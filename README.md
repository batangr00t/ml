# ml
machine learning LAB

## prepare environment

This is tested in Ubuntu 17.04
1. install anaconda
2. install tenforflow 
3. validate the installed tensorflow environment
4. setup eclipse

### 1. install anaconda
- homepage : http://www.continuum.io/
- remove the installed anaconda if you want : ```$ rm -rf ~/anaconda3```
- download anaconda 4.4.0 for python3.6 : https://www.continuum.io/downloads
- install it : ```$ bash Anaconda3-4.4.0-Linux-x86_64.sh```
- change PATH in .profile : ```PATH="$HOME/anaconda3/bin:$PATH"```
- logout ( not terminal but Desktop environment ) and login again

### 2. install tenforflow 
- homepage : https://www.tensorflow.org/install/install_linux
- Determine which TensorFlow to install : TensorFlow with CPU support only
- create conda environment : ```$ conda create --name tensorflow python=3.6```
- remove a conda environment if you want : ```$ conda remove --name tensorflow```
- activate tensorflow environment : ```$ source activate tensorflow```
- install tensorflow 
```bash
(tensorflow) $ pip install --ignore-installed https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.2.1-cp36-cp36m-linux_x86_64.whl
```

### 3. validate the installed tensorflow environment
- run a short python program
```python
# python
import os
os.environ['TF_CPP_MIN_LOG_LEVEL']='2'
import tensorflow as tf
hello = tf.constant('Hello, TensorFlow!')
sess = tf.Session()
print(sess.run(hello))
```

### 4. setup eclipse
- install PyDev : http://www.pydev.org/manual_101_install.html
- setup eclipse
```
Windows->Preferences->PyDev->Python Interpreters
   click [New...]
   Interpreter Name : tensorflow
   Interpreter Executable : /home/cho/anaconda3/envs/tensorflow/bin/python
```
   

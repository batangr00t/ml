# ml
machine learning LAB

## prepare environment

This is tested in Ubuntu 17.04
1. install tensorflow from source
2. install anaconda
3. make a conda environment for tensorflow

## 1. install tenforflow from source
- homepage : https://www.tensorflow.org/install/install_sources
- Determine which TensorFlow to install : TensorFlow with CPU support only
- clone tensorflow sources
```bash
$ cd
$ git clone https://github.com/tensorflow/tensorflow 
```
- install build tool bazel
```bash
$ echo "deb [arch=amd64] http://storage.googleapis.com/bazel-apt stable jdk1.8" | sudo tee /etc/apt/sources.list.d/bazel.list
$ curl https://bazel.build/bazel-release.pub.gpg | sudo apt-key add -
$ sudo apt-get update
$ sudo apt-get install bazel
```
- check and install following python3 packages : numpy, dev, pip, wheel
```bash
$ sudo apt-get install python3-numpy python3-dev python3-pip python3-wheel
```
- compile
- make pip package

### 2. install anaconda
- homepage : http://www.continuum.io/
- remove the installed anaconda if you want : ```$ rm -rf ~/anaconda3```
- download anaconda 4.4.0 for python3.6 : https://www.continuum.io/downloads
- install it : ```$ bash Anaconda3-4.4.0-Linux-x86_64.sh```
- change PATH in .profile : ```PATH="$HOME/anaconda3/bin:$PATH"```
- logout ( not terminal but Desktop environment ) and login again

### 3. make a conda environment for tensorflow
- create conda envionment : ```$ conda create --name tensorflow python=3.6```
- activate tensorflow environment : ```$ source activate tensorflow```

# using tensorflow

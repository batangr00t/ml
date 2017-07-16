# ml
machine learning LAB

## prepare environment

This is tested in Ubuntu 17.04
1. install anaconda
2. install tensorflow from source
3. make a conda environment for tensorflow

### 1. install anaconda
- homepage : http://www.continuum.io/
- remove the installed anaconda if you want : ```$ rm -rf ~/anaconda3```
- download anaconda 4.4.0 for python3.6 : https://www.continuum.io/downloads
- install it : ```$ bash Anaconda3-4.4.0-Linux-x86_64.sh```
- change PATH in .profile : ```PATH="$HOME/anaconda3/bin:$PATH"```
- logout ( not terminal but Desktop environment ) and login again

### 2. install tenforflow from source
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
- donwload sources : ```$ git clone https://github.com/tensorflow/tensorflow```
- copy mklml lib
```bash
$ mkdir /opt/intel/mklml
$ cd tensorflow/third_party/mkl/mklml_lnx_2018.0.20170425
$ cp -R lib /opt/intel/mklml/
$ chmod -x /opt/intel/mklml/lib/libmklml_intel.so
```
- configure
```bash
$ cd tensorflow
$ ./configure
You have bazel 0.5.2 installed.
Please specify the location of python. [Default is /home/cho/anaconda3/bin/python]: 
Found possible Python library paths:
  /home/cho/anaconda3/lib/python3.6/site-packages
Please input the desired Python library path to use.  Default is [/home/cho/anaconda3/lib/python3.6/site-packages]

Using python library path: /home/cho/anaconda3/lib/python3.6/site-packages
Do you wish to build TensorFlow with MKL support? [y/N] y
MKL support will be enabled for TensorFlow
Do you wish to download MKL LIB from the web? [Y/n] n
Please specify the location where MKL is installed. [Default is /opt/intel/mklml]: 
Please specify optimization flags to use during compilation when bazel option "--config=opt" is specified [Default is -march=native]: 
Do you wish to use jemalloc as the malloc implementation? [Y/n] 
jemalloc enabled
Do you wish to build TensorFlow with Google Cloud Platform support? [y/N] 
No Google Cloud Platform support will be enabled for TensorFlow
Do you wish to build TensorFlow with Hadoop File System support? [y/N] 
No Hadoop File System support will be enabled for TensorFlow
Do you wish to build TensorFlow with the XLA just-in-time compiler (experimental)? [y/N] 
No XLA support will be enabled for TensorFlow
Do you wish to build TensorFlow with VERBS support? [y/N] 
No VERBS support will be enabled for TensorFlow
Do you wish to build TensorFlow with OpenCL support? [y/N] 
No OpenCL support will be enabled for TensorFlow
Do you wish to build TensorFlow with CUDA support? [y/N] 
No CUDA support will be enabled for TensorFlow
Do you wish to build TensorFlow with MPI support? [y/N] 
MPI support will not be enabled for TensorFlow
Configuration finished

```
- compile and builds a script named build_pip_package
```bash
$ bazel build --config=opt //tensorflow/tools/pip_package:build_pip_package
...
INFO: Elapsed time: 1459.126s, Critical Path: 55.06s
$ head bazel-bin/tensorflow/tools/pip_package/build_pip_package
#!/usr/bin/env bash
# Copyright 2015 The TensorFlow Authors. All Rights Reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
```
- make pip package
```bash
$ bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg
$ ls -lh /tmp/tensorflow_pkg/
합계 39M
-rw-r--r-- 1 cho cho 39M  7월 16 22:08 tensorflow-1.2.1-cp36-cp36m-linux_x86_64.whl
```

### 3. make a conda environment for tensorflow
- create conda envionment : ```$ conda create --name tensorflow python=3.6```
- activate tensorflow environment : ```$ source activate tensorflow```
- install tensorflow 
```bash
(tensorflow) $ pip install /tmp/tensorflow_pkg/tensorflow-1.2.1-cp36-cp36m-linux_x86_64.whl
(tensorflow) $ conda list
# packages in environment at /home/cho/anaconda3/envs/tensorflow:
#
bleach                    1.5.0                     <pip>
html5lib                  0.9999999                 <pip>
Markdown                  2.6.8                     <pip>
numpy                     1.13.1                    <pip>
openssl                   1.0.2l                        0  
pip                       9.0.1                    py36_1  
protobuf                  3.3.0                     <pip>
python                    3.6.1                         2  
readline                  6.2                           2  
setuptools                27.2.0                   py36_0  
six                       1.10.0                    <pip>
sqlite                    3.13.0                        0  
tensorflow                1.2.1                     <pip>
tensorflow-tensorboard    1.3.1                     <pip>
tk                        8.5.18                        0  
Werkzeug                  0.12.2                    <pip>
wheel                     0.29.0                   py36_0  
xz                        5.2.2                         1  
zlib                      1.2.8                         3
```

# using tensorflow

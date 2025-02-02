# DPRNet : Deep 3D Point based Residual Network for Semantic Segmentation and Classification of 3D Point Clouds

## Usage

This code is tested in Ubuntu 16.04 LTS with CUDA 8.0 and Tensorflow-gpu==1.4.
First of all you need to compile convolutional operators as follow:
```bash
cd tf_ops/conv3p/

chmod 777 tf_conv3p_compile.sh

./tf_conv3p_compile.sh -a
```

if you are using tensorflow-gpu==1.4 or above then you might want to try compiling with `tf_conv3p_compile_tf14.sh` instead. It fixes some include paths due to `nsync_cv.h`, and set the flag `_GLIBCXX_USE_CXX11_ABI=0` to make it compatible to libraries compiled with GCC version earlier than 5.1. 

After successfully compiling the convolution operators you can start DPRNet training as follow:

To train object classification, execute

```bash
python train_modelnet40.py [epoch]
```

To evaluate, execute

```bash
python eval_modelnet40.py [epoch]
```

Similar procedure is required for scene segmentation task. By default 'epoch' is 0. You can resume the training by passing epoch number in the above command.

## Training Data

Data folder contains links of the datasets for both classification and semantic segmentation task.


## Dependencies

This code includes the following third party libraries and data:

- Scaled exponential linear units (SeLU) for self-normalization in neural network.

- ModelNet40 data from PointNet

- Some other utility code from Pointwise CNN

- h5py

## Acknowledgemets
The code for convolution operators, Training and evaluation borrowed from [<a href="https://github.com/scenenn/pointwise">Pointwise CNN</a>] 

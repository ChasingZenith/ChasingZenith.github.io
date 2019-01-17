---
layout: post
title:  "Anaconda GPU"
date:   2019-1-15 20:13:16 +0800
categories: Anaconda GPU
---

# conda 配置GPU环境

## Conclusion

使用 *conda* 进行安装的时候，会连带的安装一些驱动文件（可能会覆盖掉外部安装的驱动的设置），但与显卡驱动可能不匹配，cuda的版本号与驱动的版本号不对应很可能就会出现问题。

1. conda install时，和驱动相关的依赖关系它可能无法检测出来，安装前最好也要看清楚版本号
2. conda search conda show 可查看依赖关系

## 错误描述

GPUs: 两个  NVIDIA 1080Ti
显卡驱动： 390.86 CUDA 9.0 cuDNN 经过mnist测试TEST PASS
不使用conda环境，使用pip install tensorflow-gpu 一切正常
使用 conda install tensorflow-gpu 后出现问题

```shell
2019-01-15 09:58:35.670043: E tensorflow/stream_executor/cuda/cuda_dnn.cc:373] Could not create cudnn handle: CUDNN_STATUS_NOT_INITIALIZED
2019-01-15 09:58:35.670168: E tensorflow/stream_executor/cuda/cuda_dnn.cc:381] Possibly insufficient driver version: 390.87.0
2019-01-15 09:58:35.670199: E tensorflow/stream_executor/cuda/cuda_dnn.cc:373] Could not create cudnn handle: CUDNN_STATUS_NOT_INITIALIZED
2019-01-15 09:58:35.670248: E tensorflow/stream_executor/cuda/cuda_dnn.cc:381] Possibly insufficient driver version: 390.87.0
```

## 问题所在

使用conda 安装的时候没有对应安装正确版本的cuda

```bash
_tflow_select             2.1.0                       gpu    https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
absl-py                   0.4.1                    py35_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
astor                     0.7.1                    py35_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
blas                      1.0                         mkl    https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
ca-certificates           2018.03.07                    0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
certifi                   2018.8.24                py35_1    https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
cudatoolkit               9.2                           0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
cudnn                     7.2.1                 cuda9.2_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
cupti                     9.2.148                       0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
gast                      0.2.0                    py35_0    https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
```

## 解决方法

使用以下命令可以正好安装上正确的驱动

使用以下命令在源中查找正确版本

```bash
$ conda search cudnn

Loading channels: done
# Name                  Version           Build  Channel             
cudnn                       5.1               0  anaconda/pkgs/free  
cudnn                       5.1               0  pkgs/free           
cudnn                    5.1.10       cuda7.5_0  anaconda/pkgs/free  
cudnn                    5.1.10       cuda7.5_0  pkgs/free           
cudnn                    5.1.10       cuda8.0_0  anaconda/pkgs/free  
cudnn                    5.1.10       cuda8.0_0  pkgs/free           
cudnn                       6.0               0  anaconda/pkgs/free  
cudnn                       6.0               0  pkgs/free           
cudnn                    6.0.21       cuda7.5_0  anaconda/pkgs/free  
cudnn                    6.0.21       cuda7.5_0  pkgs/free           
cudnn                    6.0.21       cuda8.0_0  anaconda/pkgs/free  
cudnn                    6.0.21       cuda8.0_0  pkgs/free           
cudnn                     7.0.5       cuda8.0_0  pkgs/main           
cudnn                     7.0.5       cuda8.0_0  anaconda/pkgs/main  
cudnn                     7.1.2       cuda9.0_0  pkgs/main           
cudnn                     7.1.2       cuda9.0_0  anaconda/pkgs/main  
cudnn                     7.1.3       cuda8.0_0  pkgs/main           
cudnn                     7.1.3       cuda8.0_0  anaconda/pkgs/main  
cudnn                     7.2.1       cuda9.2_0  pkgs/main           
cudnn                     7.2.1       cuda9.2_0  anaconda/pkgs/main  

```

安装正确版本的cudnn,则其他的依赖都会正常

```bash
conda install tensorflow-gpu cudnn=7.1.2
# Multi GPUs
# conda install nccl
```

```bash
# create a conda environment DIRECTLY
conda create -n tfgpu tensorflow-gpu cudnn=7.1.2
```

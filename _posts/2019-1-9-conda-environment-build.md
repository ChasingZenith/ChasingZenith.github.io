---
layout: post
title:  "Set up a conda environment"
date:   2019-1-9 20:13:16 +0800
categories: Python Conda
---

# 搭建conda环境

## [设置更新源](https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/)

## create

conda create -n tf36 python=3.6

tensorflow 现在暂时（2018-01-09）还不支持3.7

## activate

conda activate tf36

## remove

conda env remove -n tf36

> Reference
>
> [Docs » Command reference » conda env remove](https://conda.io/docs/commands/env/conda-env-remove.html)


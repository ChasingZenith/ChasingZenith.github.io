---
layout: post
title:  "Dairy-to-remind-me-what-I-have-done"
date:   2019-3-5 10:51:20 +0800
categories: Linear Algebra
---

# 主要目的

1. 记录学习生活，提高学习效率
2. 留下参考资料，参考网站，以便以后查找。
3. 建立自己的知识库
4. 方便建立阶段性总结
5. 留下美好回忆

## Mar 3th, 2019

1. 多维正态分布---Jessca Hwang Introduction to Probability
   1. todo: 还是不明白其$p(x)=\frac{1}{(2\pi)^{N/2}\det^{1/2}{C}}\exp(-\frac{1}{2}(\boldsymbol{x}-\boldsymbol{\mu})^TC^{-1}(\boldsymbol{x}-\boldsymbol{\mu}))$是怎么来的

## Mar 4th, 2019

1. 行列式求导---参考2019-3-4-Derivative of Determinant
2. Kay Appendix 3C Derivation of General Gaussian CRLB 的难点进行了突破，总体思路弄明白

## Mar 5th, 2019

1. Antonio 的课 Network Theory and Analytics
   1. [x] 奇异值 $A=U\Sigma V^T,$
   2. [x] 奇异值分解
   3. [ ] PageRank
   4. [x] 矩阵指数
   5. [ ] 转移矩阵
   6. [ ] 矩阵级数
   7. [ ] 变换后的矩阵的特征值和特征向量
   8. [ ] 特征向量的迭代算法
   9. [ ] 相似与合同

2. Appendix 3C Derivation of General Gaussian CRLB 难点进行了总结
3. 白噪声与bandlimit白噪声---Simon haykin   Communication Systems
4. 发现Simon haykin的Communication Systems 很能补充现在我不懂的地方
5. 看完Kay Chap3 开始做作业
   1. [ ] SNR
   2. [ ] mean squre bandwidth
   3. [ ] Fourier Transform Definition Properties
   4. [ ] P56 about sin
   5. [ ] Autoregressive model
   6. [ ] z transform
   7. [ ] Fourier transform $F(2\pi f)$的共轭$F^*(2\pi f)$的时域序列
   8. [ ] Fourier transform $A(f)=A^*(-f)$
   9. [ ] P61 $r_{xx}[k-l]$ and inverse Fourier Transform of Power Spectrum Density $P_{xx}(f;\theta)$
   10. [ ] high order moment
   11. [ ] PSD
   12. [ ] Fourier transform of Gaussian Function
   13. [ ] $\boldsymbol{E}\{x_ix_jx_mx_m\}=\boldsymbol{E}(x_ix_j)\boldsymbol{E}(x_mx_n)+\boldsymbol{E}(x_ix_m)\boldsymbol{E}(x_jx_n)+\boldsymbol{E}(x_ix_n)\boldsymbol{E}(x_jx_m)=R_{ij}R_{mn}+R_{im}R{jn}+R_{in}R_{jm}$

# Mar 6th

1. 读完Chap3 开始做作业
   1. Problem3.16 WSS的均值不变， $\frac{\partial\mu(\theta)}{\partial\theta}$
   2. nyquist rate
   3. P54 $k\Delta=k/(2B)$correspond to the zeros of the ACF of $w(t)$
2. Kay Apendix1 关于Power Spectrum， Gaussian Random Processing的部分，尚不是很清晰。

# Mar 7th

1. Kay P54 证明nyquist rate 下 sample $w[n]$是$r_{xx}[k] = 0 \,\text{if} \,  k \neq0$ 则可使用$(3.14)$?

## Mar 8th

1. Antonio的课
2. 安装flow环境

## Mar 10th

1. 高斯变量可加性诀窍：配方法$u=x-s/2$
2. 依概率收敛
3. 又开始想 regularity condition 和sufficient statistic的关系，sufficient statistics有一副图，上面显示了关于A的导数为0
4. 毕设：运行flow的tutorial01 发现conda 的虚拟环境下使用 *Jupyter notebook* 一定需要重新```pip install jupyter```

## Mar 11th

1. locua 的智能交通程序配置
2. 学习奇异值分解
3. 哄开心
4. 凸优化

## Mar 12th

1. psudoinverse
2. locus的智能交通程序

## Mar 13th

1. 关于样本方差$S_n=\frac{1}{n-1}\sum_{j=1}^{n}(X_j-\bar{X}_n)$中$n-1$的理解:$\bar{X}_n$与$X_j$不独立，由于$\bar{X}_n$会随着$n$个i.i.d.的样本的上浮和下浮产生同方向偏离$E(\bar{X})=\text{Var}(\bar{X}_n)=\sigma^2/n$，所以和$\sum(X_j-\mu)$相比方差要小。Jessica Hwang P254
2. [ ] 极坐标转直角坐标积分
3. Moment generate function the MGF of $X=\mu+\sigma Z - N(\mu, \sigma^2)$ is $M_X(t)=e^{\mu t+\frac{1}{2}\sigma^2t^2}$
4. 早上上了凸优化的课 LP QP SOCP SDP
5. FSSP 3.14
# Feasibility of Learning

## 大数定律

$$P(|Q_n(A)-\theta| \gt \epsilon) \rightarrow 0$$

## Hoeffding's Inequality

In a big sample (large m), v is probably close to

$$P(|v - \mu|) \leq 2\exp(-2\epsilon^2m) \text{for any } \epsilon > 0$$

$$P(|E_{in}(g) - E_{out}(g)|) \leq 2\exp(-2\epsilon^2m) \text{for any } \epsilon > 0$$

$$E_{in} \rightarrow E_{out}$$

指的是泛化性能

## Real learning - Finite Learning Model

empirical risk

expected risk

$$|\Bbb{N}|=|\Bbb{Z}|=|\Bbb{Q}|\lt|\Bbb{R}|$$

集合的基？

$$ \Bbb{P}[|E_{in}(g)-E_{out}(g)|\gt\epsilon]\leq 2|H|e^{-2\epsilon^2m} $$

## efficiency of an optimization algorithm

 (local) convergence rate 主要精度提高都在于收敛接近收尾最后的时候的速度

 complexity analysis(worst-case complexity)
  $\epsilon$-optimality

computational cost per iteration

hassen n-dimention o(n^2)for hessen 而且要求逆

批梯度?

## Interpretation of Gradient Descent

Gradient descent

Taylor 展开

$x^{k+1}\Leftarrow x^k-\alpha \Delta J(x^k)$

n 个一元二次函数

二次函数的最优值

$f(y)\approx f(x)+\Delta f(x)^T(y-x)+1/(2\alpha)||y-x||^2$

当前用一个线性函数近似

Quadratic approximation replacing usual $\Delta^2f(x)$ by $1/\alpha I$

### Starting point

convex problem : global
nonconvex problem: local

### Stepsize/ Learning Rate

if step size too large

### backtracking line search回溯

away to adaptively choose the step size

$f(x-\alpha \varDelta f(x))>f(x)$

充分下降条件

sufficient decrease condition

线搜索 Amijo backtracking line search

keep in mind that steepest may not be wise

 gradient descent may be shortsighted

为什么扁 由于曲率,二阶信息

### Convergence analysis

Assume that $f:\Bbb{R}^n\rightarrow\Bbb{R}$ is conve and differentiable,  and additionally Lipschitz continuous with constant $L>0$

when $\alpha \leq 1/L$
$$ f(x^k)-f(x^*) \leq \frac{||x^0-x^*||^2}{2\alpha k} $$

和初始值估计的精准程度有关
与stepsize$\alpha$有关

最小二乘的Lipscchitz的L是多少,最大的特征值??

### Convergence analysis for backtracking

$$ f(x^k)-f(x^*) \leq \frac{||x^0-x^*||^2}{2\alpha_{min} k} $$
with $\alpha_{min}=\min\{1, \gamma/L\}$
$\gamma$ 是backtracking 缩小的倍数

### Linear Convergence for Strongly COnvex Cases

不太陡也不太平才好

$(\frac{L/\mu-1}{L/\mu+1})^{2k}\frac{L}{2}||x^0-x^*||^2$

按照比例缩小 线性收敛

$L$ the largest eigenvalue

$\mu$ the smallest eigenvalue

$L\over \mu$ condition number. If condition number is $1$, i.e. $L = \mu$, 等高线是同心圆

## Strong Convexity Implies PL Inequality

considering  a linear problem $Ax=b$

1. 接近欠定的时候条件数特别大,
2. ill-posed 多解

在处理的时候,用的方法使用正则化的技术

梯度很小的时候,离最优非常近了

$$

\nabla^2 f(x) \rVert \leq \sqrt{2d\epsilon}
\Rightarrow
f(x)-f(x^*)
\leq \epsilon

$$

即便不连续,使用梯度下降法,跑到不连续的点的几率为$0$测度为0的点.

## Acceleration

Nesterou reserch of first-order acceleration

Nesterou's Acceleratioin

$$
f(\omega^k)-f^*
\leq
\left(  1-\sqrt{\frac{\mu}{L}}  \right)^k
\lvert{  f(\omega^0)-f^*  }\rvert
$$

stepsize and 海森矩阵尽量相同

再过来的方向上

## Lecture 6 Error and Noise

the latter part of Chapter 1

最大似然估计
对应了一种噪音的模型
在学习条件概率

### Maximum likelihood Estimation

找一个分布,最可能是从这个分布上面得到的

Suppose distribution is known, but unknown  parameter
采样然后
一批样本就是由这个分布产生的可能性有多大

$L_m(\theta; x_1, x_2, ..., x_m)$由参数和样本共同组成

为什么极大化$L_m$

$\ln$是保序的

极大化似然到极大化loglikelihood

对loglikelihood求一次,二导,一阶到为零,二阶导为正

poisson $E(X)=\lambda$

#### MLE v.s LS(Linear Regrassion model)

$$ y=x^T\theta+\epsilon $$

We assume that $epsilon_i$ are i.i.d. with $\epsilon^i\sim\mathcal{N}(0,\sigma^2)$
Then the conditional distribution of $Y_i$ given that $X^i=x^i$ is

$$ Pr(Y \vert \mathrm{x}^i) \sim \mathcal{N}({\mathrm{x}^i}^T\theta, \sigma^2) $$

feature vector $\mathrm{x}$ is constant

The log likelihoode estimation is given by

法方程

linear model Gaussian noise

最小二乘 对应于概率模型高斯分布

数学史上,先有最小二乘后有高斯分布

#### Effects of MSE

sensitive outliers

如果有很大的偏离点,平方的话会有很大的误差

$\frac{}{}$

$x ^{a}$
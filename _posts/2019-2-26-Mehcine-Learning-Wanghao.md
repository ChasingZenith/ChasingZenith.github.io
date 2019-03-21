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
# Feasibility of Learning

## 大数定律

$P(|Q_n(A)-\theta| \gt \epsilon) \rightarrow 0$

## Hoeffding's Inequality

In a big sample (large m), v is probably close to

$P(|v - \mu|) \leq 2\exp(-2\epsilon^2m) \text{for any } \epsilon > 0$

$P(|E_{in}(g) - E_{out}(g)|) \leq 2\exp(-2\epsilon^2m) \text{for any } \epsilon > 0$

$E_{in} \rightarrow E_{out}$

指的是泛化性能

## Real learning - Finite Learning Model

empirical risk

expected risk

$|\Bbb{N}|=|\Bbb{Z}|=|\Bbb{Q}|\lt|\Bbb{R}|$

集合的基？

$$ 

\Bbb{P}[|E_{in}(g)-E_{out}(g)|\gt\epsilon]\leq 2|H|e^{-2\epsilon^2m} $$
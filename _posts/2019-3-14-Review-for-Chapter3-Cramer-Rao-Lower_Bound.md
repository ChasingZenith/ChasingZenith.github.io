---
layout: post
title:  "Review for Chapter 3 Cramer-Rao Lower Bound"
date:   2019-3-14 21:01:20 +0800
categories: Signal_Processing CRLB
---

#

## 3.1 Introduction

At best, it allows us to assert that an estimator is the MVU estimator. At worst, it provides a bnchmark against which we can compare the performance of any unbiased estimator.

## From Geommetry Aspect and Intuition

Figure3.1

Intuitively, the "sharpness" of the likelihood function determines how accurately we can estimate the unknown parameter. To quantify this notion observe that the sharpness is effectively measureed by the negative of the second derivative, i.e. the curvature, of the log-likelihood funcion at its peak.

## 3.4 Cramer-Rao Lower Bound

### Theorem 3.1 (Cramer-Rao Lower Bound - Scalar Parameter)

It is assumed that the PDF $p(x;\theta)$ satisfies the "regularity" condition

$$ E[\frac{\partial \ln p(\textbf{x};\theta)}{\partial\theta}]=0 \quad \textrm{for all } \theta \tag{3.6}$$

where the expectation is taken with respect to $p(\textbf{x};\theta)$.
The expectation above is expicitly given by

$$ E[\frac{\partial^2 \ln p(\mathbf{x};\theta)}{\partial\theta^2}]=\int\frac{\partial^2 \ln p(\mathbf{x};\theta)}{\partial\theta^2} p(\mathbf{x};\theta) \, \mathrm{d}x $$

since the second derivation is a random variable deandent on $\mathbf{x}$
Then, the variance of any unbiased estimator $\hat{\theta}$ must satisfy

$$ \textrm{var} \ge \frac{1}{-E\left[\frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial\theta^2}\right]} $$

where the derivative is evaluated at the true value of $\theta$ and the expectation is taken with respect to $p(\mathbf{x}; \theta$. Furthermore, an unbiased estimator may be found that attains the bound for all $\theta$ if and only if

$$ \frac{\partial\ln p(\mathbf{x};\theta)}{\partial\theta}=I(\theta)(g(\mathbf{x}-\theta)) $$

for some functions $g$ and $I$. That estimator, which is the MVU estimator, is $\hat{\theta}=g(\mathbf{x})$, and the minimum variance is $1/I(\theta)$

**The bound will depend on $\theta$ in general.**

### Expressed in a different form

Although $(3.6)$ is usually more vonvenient for evaluation, the alternative form is sometimes useful for the theoretical work.

$$ E\left[\left(\frac{\partial\ln p(\mathbf{x};\theta)}{\partial \theta}\right)^2 \right] = -E\left[\frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial \theta^2} \right] \tag{3.11}$$

### Fisher Information

The denominator in $(3.6)$ is referred to as the Fisher information $I(\theta)$ for the datea $\mathbf{x}$ or

$$ I(\theta)=-E\left[\frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial \theta^2} \right]$$

It has the essential properties of an information measure in that it is

1. nonnegative due to $(3.11)$.
2. additive for independent observations.

## 3.5 General CRLB for Signals in White Gaussian Noise

Assume that a deterministic signal with an unknown parameter $\theta$ is ovserved in WGN as

$$ x[n] = s[n; \theta] + w[n] \qquad n=0,1, ..., N-1.$$

The depandence of the signal on $\theta$ is explicitly noted.

We will have

$$ \textsf{var}(\hat{\theta})\ge\frac{\sigma^2}{\sum_{n=0}^{N-1}(\frac{\partial s[n;\theta]}{\partial \theta})^2} $$

The form of the bound demonstrates the importance of the signal dependence of $\theta$. Signals that change rapidly as the unknown parameter changes result in accurate estimators.

## Transformation of Parameters

If it is desired to estimate $\alpha=g(\theta)$, then the CRLB is

$$ var(\hat{\alpha}) \ge \frac{(\frac{\partial g}{\partial\theta})^2}{-E\left[\frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial \theta^2}\right]} $$

The efficiency of an estimator is **destroyed by a nonlinear transormation**. Although efficiency is preserved only over linear transformations, it is *approximately* maintained over nonlinear transformations if the data record is large enough. Intuitively, this situation occurs due to the statistical linearity of the transormation.

## 3.7 Extension to a Vector Parameter

### Theorem 3.2 (Cramer-Rao Lower Bound - Vector Parameter)

It is assumed that the PDF $p(\mathbf{x};\mathbf{\theta})$ satisfies the "regularity" condition

$$ E[\frac{\partial \ln p(\textbf{x};\mathbf{\theta})}{\partial\mathbf{\theta}}]=0 \quad \textrm{for all } \mathbf{\mathbf{\theta}} $$

where the expectation is taken with respect to $p(\textbf{x};\mathbf{\theta})$.
The expectation above is expicitly given by

$$ E[\frac{\partial^2 \ln p(\mathbf{x};\mathbf{\theta})}{\partial\mathbf{\theta}^2}]=\int\frac{\partial^2 \ln p(\mathbf{x};\mathbf{\theta})}{\partial\mathbf{\theta}^2} p(\mathbf{x};\mathbf{\theta}) \, \mathrm{d}x $$

since the second derivation is a random variable deandent on $\mathbf{x}$
Then, the **co-variance matrix** of any unbiased estimator $\hat{\mathbf{\theta}}$ must satisfy

$$ \mathbf{C}_{\hat{\mathbf{\theta}}} - \mathbf{I}^{-1}(\mathbf{\theta}) \ge \mathbf{0} \tag{3.24} $$

where $ge \mathbf{0}$ is interpreted as meaning that the matrix is positive semidefinite. The Fisher Information matrix $\mathbf{I}(\mathbf{\theta})$ is given as

$$ [I(\mathbf{\theta})]_{ij}=-E\left[\frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial \theta_i \partial\theta_j}\right] $$

where the derivative is evaluated at the true value of $\mathbf{\theta}$ and the expectation is taken with respect to $p(\mathbf{x}; \mathbf{\theta}$. Furthermore, an unbiased estimator may be found that attains the bound in that $\mathbf{C}_{\hat{\mathbf{\theta}}}=\mathbf{I}^{-1}(\mathbf{\theta})$ for all $\mathbf{\theta}$ if and only if

$$ \frac{\partial\ln p(\mathbf{x};\mathbf{\theta})}{\partial\mathbf{\theta}}=I(\mathbf{\theta})(\mathbf{g}(\mathbf{x}-\mathbf{\theta})) \tag{3.25} $$

for some functions $p$-dimension function $\mathbf{g}$ and some $p\times p$ matrix $I$. That estimator, which is the MVU estimator, is $\hat{\mathbf{\theta}}=\mathbf{g}(\mathbf{x})$, and the minimum covariance matrix is $1/I(\mathbf{\theta})$

By noting that for a postive semidefinite matrix the diagonal elements are nonnegative. Hence,

$$ [\mathbf{C}_{\mathbf{\theta}}] - \mathbf{I}^{-1}(\mathbf{\theta})]_{ii} \ge 0 $$

and therefore

$$ \textnormal{var}(\mathbf{\theta})=[\mathbf{C}_{\mathbf{\hat{\theta}}}]_{ii} \ge [\mathbf{I}^{-1}(\mathbf{\theta})]_{ii} $$

If the equality conditions hold, the reader may ask whether we can be assured that $\mathbf{\hat{\theta}}$ is unbiased. Because the regularity conditions

$$ E[\frac{\partial \ln p(\textbf{x};\mathbf{\theta})}{\partial\mathbf{\theta}}]=0 \quad \textrm{for all } \mathbf{\mathbf{\theta}} $$

are always assumed to hold, we can apply them to $(3.25)$. This then yields $E[\mathbf{g(x)}=E[\mathbf{\hat{\theta}}]=\mathbf{\theta}$.

**The bound will depend on $\mathbf{\theta}$ in general.**

## Vector Parameter CRLB for Transformations

Assume that it is desired to estimate $\mathbf{\alpha}= \mathbf{g(\theta)}$ for $\mathbf{g}$, an $r$-dimension function. Then

$$ \mathbf{C_{\hat{\alpha}}} - \frac{\partial\mathbf{g(\theta)}}{\partial\mathbf{\theta}}\mathbf{I}^{-1}(\mathbf{\theta}){\frac{\partial\mathbf{g(\theta)}}{\partial\theta}}^T \ge \mathbf{0} \tag{3.30}$$

where, $\ge \mathbf{0}$ is to be interreted as positive semidefinite. In $(3.30)$, $\partial\mathbf{g(\theta)}/\partial\mathbf{\theta}$ is the $r\times p$ **Jacobian matrix** defined as

$$ \left[\frac{\partial\mathbf{g(\theta)}}{\partial\mathbf{\theta}}\right]_{ij} = \frac{\partial g_i(\mathbf{\theta})}{\partial\theta_j} $$


## 3.9 CRLB for the General Gaussian Case

Assume that

$$\mathbf{x} \sim \mathcal{N}(\mathbf{\mu(\theta), \mathbf{C(\theta)}}$$


## Chapter 5 General Minimum Variance Unbiased Estimation

## mainly

1. Definition of **Sufficient Statistic**
2. Find (single) Sufficient Statistic (Neymann Fisher factorization)
3. check if sufficient statistic is complete(RBLS tell us a complete sufficient statistic can lead to a MVU estimater) by using $\int_{-\infty}^{\infty}v(T)p(T;\theta)\text{d}y$
4. RBLS tell us we can find better(best for a sufficient estimator $T(\textbf{x})$ that is complete) estimator by $\hat{\theta}=E(\check{\theta}|T(\textbf{x}))$


## 5.2

Sufficient statistic as one which summarizes the data in the sense that if we are given the suffcient statistic, the PDF of the data no longer dependent on the unknown parameter.

## 5.5 Using Sufficiency to Find the MVU Estimator(RBLS Rao-Blackwell-Lehmann-Scheffe)

if $T(x)$ is complete, there is but **one** function of $T$ that is an unbiased estimator. Hence, $\hat{\theta}$ is **unique**, independent of the $\check{\theta}$ we choose from the class shown in Figure 5.2. Every $\check{\theta}$ maps into the same estimator $\hat{\theta}$. Becasuse the variance of $\hat{\theta}$ must be less than **any** $\check{\theta}$ within the class (unbiased), we conclude that $\hat{\theta}$ must be thte MVU estimator.

### Two Ways to Find the Unbiased Estimator

Find a single sufficient statistic for $\theta$, that is $T(\textbf{x})$, byusing the Neyman-FIsher factorization theorem.

### Method 1

Find *any* unbiased estimator of $\theta$, say $\check{\theta}$ is an unbiased estimator of $\theta$, and determine 

$$ \hat{\theta}=E(\check{\theta}|T(\textbf{x}))=\int \check{\theta}p\big(\check{\theta}|T(\textbf{x})\big)d\check{\theta}=g(T(\textbf{x})). $$

$E(\check{\theta}|T(\textbf{x})$ is solely a function of the sufficient statistic $T(\textbf{x})$.

### Method 2

Find some function $g$ so that $\hat{\theta}=g(T)$ is an unbiased estimator of $A$.


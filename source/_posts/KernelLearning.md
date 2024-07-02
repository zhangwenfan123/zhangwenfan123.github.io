---
title: Incomplete-view oriented kernel learning method with generalization error bound
date: 2022-06-08
tags: Kernel_Learning
category: Artificial Intelligence
excerpt: Multi-view learning (MVL) is a promising direction and most MVL methods work under the assumption that data are complete in all views. However, this assumption is often violated in practice due to the difficulties of high cost, equipment failure, and so on. Besides, the amount of data with missing views is particularly huge. Therefore, it is challenging yet valuable to fully leverage the large-scale incomplete-view data. 
author: Zhang Wenfan
authorURL: 
url: 
copyrightText: 
mathjax: true
---

$\underline{\text{-01. Questions}}$

>1. What's the difference between [*Multimodal Machine Learning*](https://arxiv.org/abs/1705.09406) and [Multi-view Learning](https://arxiv.org/abs/1304.5634)? How to define the specific concept? Are the two terms refer to the same thing?

>2. Is the the RPSVM-2V solution just linear Integration of RSVM and PSVM-2V? According to the data completeness, jump to the certain branch by "IF"?


$\underline{\text{00. Key Concepts and Definitions}}$

- 0.1 **KL(Kernel Methods)**
    - *Support Vector Machines (SVM)*
    - *Radial Basis Function (RBF)*
    - *Linear Discriminate Analysis (LDA)*

>Kernels or kernel methods (also called Kernel functions) are sets of different types of algorithms that are being used for pattern analysis. They are used to solve a non-linear problem by using a linear classifier. Kernels Methods are employed in SVM (Support Vector Machines) which are used in classification and regression problems.

*Support Vector Machines (SVM)*

>In machine learning, support-vector machines (SVMs, also support-vector networks) are supervised learning models with associated learning algorithms that analyze data for classification and regression analysis.

最优参数的SVM决策函数：

$$
f(x)=\text{sgn}(w^Tx+b^*)
$$

$$
f(x)=\text{sgn}(w^{*T}x+b^*)=\text{sgn}(\sum_{n=1}^N \lambda_n^*y^n(x^n)^Tx+b^*)
$$

在一个变换后的特征空间中，SVM的决策函数：

$$
f(x) = sgn(w^T\phi(x)+b^*) = sgn(\sum_{n=1}^N \lambda_n^*y^nK(x^n,x)x+b^*)
$$

其中核函数（Kernel）为：

$$
K(x,z)=\phi(x)^T\phi(z)
$$


*Radial Basis Function (RBF)*

>A radial basis function (RBF) is a real-valued function φ whose value depends only on the distance between the input and some fixed point, either the origin, so that φ(𝐱)=φ(|𝐱|), or some other fixed point 𝐜, called a center, so that φ(𝐱)=φ(|𝐱-𝐜|). Any function φ that satisfies the property φ(𝐱)=φ(|𝐱|) is a radial function. The distance is usually Euclidean distance, although other metrics are sometimes used.

*Linear Discriminate Analysis (LDA)*

>Linear discriminant analysis (LDA), normal discriminant analysis (NDA), or discriminant function analysis is a generalization of Fisher's linear discriminant, a method used in statistics and other fields, to find a linear combination of features that characterizes or separates two or more classes of objects or events. The resulting combination may be used as a linear classifier, or, more commonly, for dimensionality reduction before later classification.

- 0.2 MKL(Multiple Kernel Learning)
    - *Supervised learning*
        - Fixed rules approaches
        - Heuristic approaches
        - Optimization approaches
        - Bayesian approaches
        - Boosting approaches
    - *Semi-Supervised learning*
    - *UnSupervised learning*

>Multiple kernel learning refers to a set of machine learning methods that use a predefined set of kernels and learn an optimal linear or non-linear combination of kernels as part of the algorithm. Reasons to use multiple kernel learning include a) the ability to select for an optimal kernel and parameters from a larger set of kernels, reducing bias due to kernel selection while allowing for more automated machine learning methods, and b combining data from different sources that have different notions of similarity and thus require different kernels. Instead of creating a new kernel, multiple kernel algorithms can be used to combine kernels already established for each individual data source.

Multiple kernel learning (MKL) algorithms aim to find the best convex combination of a set of kernels to form the best classifier. Many algorithms have been presented in recent years and they form two classes.

_**Supervised learning**_

Fixed rules approaches

$$
k((x_{1i},x_{1j}),(x_{2i},x_{2j}))=k(x_{1i},x_{2i})k(x_{1j},x_{2j})+k(x_{1i},x_{2j})k(x_{1j},x_{2i}).
$$

Heuristic approaches

These algorithms use a combination function that is parameterized. we can define
$$
\beta_m=\frac{\pi_m - \delta} {\sum_{i=0}^N(\pi_h-\delta)}
$$

Other approaches use a definition of kernel similarity, such as
$$
{\displaystyle A(K_{1},K_{2})={\frac {\langle K_{1},K_{2}\rangle }{\sqrt {\langle K_{1},K_{1}\rangle \langle K_{2},K_{2}\rangle }}}}
$$

Optimization approaches

>These approaches solve an optimization problem to determine parameters for the kernel combination function. This has been done with similarity measures and structural risk minimization approaches. For similarity measures such as the one defined above, the problem can be formulated as follows:[9]

$$
\max_{\beta,\operatorname {tr}(K'_{tra})=1,K'\geq 0}A(K'_{tra},YY^{T}).
$$

Bayesian approaches

>Bayesian approaches put priors on the kernel parameters and learn the parameter values from the priors and the base algorithm. For example, the decision function can be written as

$$
f(x)=\sum_{i=0}^{n}\alpha_{i}\sum_{m=1}^{p}\eta_{m}K_{m}(x_{i}^{m},x^{m})
$$

Boosting approaches

>Boosting approaches add new kernels iteratively until some stopping criteria that is a function of performance is reached. An example of this is the MARK model developed by Bennett et al. (2002) [14]

$$
f(x)=\sum_{i=1}^{N}\sum_{m=1}^{P}\alpha_{i}^{m}K_{m}(x_{i}^{m},x^{m})+b
$$

_**Semi-Supervised learning**_

Let $L={(x_{i},y_{i})}$ be the labeled data, and let $U={x_{i}}$ be the set of unlabeled data. Then, we can write the decision function as follows.
$$
f(x)=\alpha_{0}+\sum_{i=1}^{|L|}\alpha_{i}K_{i}(x)
$$

The problem can be written as

$$
\min_{f}L(f)+\lambda R(f)+\gamma \Theta (f)
$$

where $L$ is the loss function (weighted negative log-likelihood in this case), $R$ is the regularization parameter (Group LASSO in this case), and $\Theta$ is the conditional expectation consensus (CEC) penalty on unlabeled data. The CEC penalty is defined as follows. Let the marginal kernel density for all the data be

$$
g_m^\pi(x)=(\phi_m^\pi,\varphi_m(x))
$$
where $\psi_{m}(x)=[K_{m}(x_{1},x),\ldots ,K_{m}(x_{L},x)]^{T}$(the kernel distance between the labeled data and all of the labeled and unlabeled data) and $\phi_{m}^{\pi } $ is a non-negative random vector with a 2-norm of 1. The value of $\Pi $ is the number of times each kernel is projected. Expectation regularization is then performed on the MKD, resulting in a reference expectation $q_{m}^{pi}(y|g_{m}^{\pi }(x))$ and model expectation $p_{m}^{\pi }(f(x)|g_{m}^{\pi }(x))$. Then, we define

$$
\Theta ={\frac {1} {\Pi}}\sum_{\pi =1}^{\Pi }\sum_{m=1}^{M}D(q_{m}^{pi}(y|g_{m}^{{\pi}}(x))||p_{m}^{\pi}(f(x)|g_{m}^{\pi}(x)))
$$

where $D(Q||P)=\sum_{i}Q(i)\ln {\frac {Q(i)}{P(i)}} $ is the Kullback-Leibler divergence. The combined minimization problem is optimized using a modified block gradient descent algorithm. For more information, see Wang et al.[15]


_**UnSupervised learning**_

Combining these terms, we can write the minimization problem as follows.

$$
\min_{\beta ,B}\sum_{i=1}^{n}\left\Vert x_{i}-\sum_{x_{j}\in B_{i}}K(x_{i},x_{j})x_{j}\right\Vert^{2}+\gamma_{1}\sum_{i=1}^{n}\sum_{x_{j}\in B_{i}}K(x_{i},x_{j})\left\Vert x_{i}-x_{j}\right\Vert^{2}+\gamma_{2}\sum_{i}|B_{i}|
$$
where . One formulation of this is defined as follows. Let $D\in {0,1}^{n\times n}$ be a matrix such that $D_{ij}=1$ means that $x_{i}$ and $x_{j}$ are neighbors. Then, $B_{i}=x_{j}:D_{ij}=1.$. Note that these groups must be learned as well. Zhuang et al. solve this problem by an alternating minimization method for $K$ and the group $B_{i}$. For more information, see Zhuang et al.[16]



+ 0.3 MVL(Multi-view Learning)

>Data in reality often exhibit in multi-modal forms, called multi-view data. Each view distributed in distinct feature spaces
describes different attributes of the same object with high dimension, strong heterogeneity and rich description. The performance of multi-view learning models compares more favorably than that of single-view learning models. The existing MVL
approaches either comply with the consensus principle or the complementary principle. Here we mainly review SVM-based
MVL classification methods.



$\underline{\text{01. Background and Key Problems}}$

- 1.1 Multi-view data and learning

> The simplest way is to train the model on the concatenated view. However, this approach ignores the correlation and interaction among views, which may cause overfitting and dimension disasters [3,4]. In this case, multi-view learning (MVL) has emerged and achieved great success in classification [5], clustering[6,7], feature selection [8,9], etc.

> With the help of different kinds sensor equipment, data tracking from different aspects is much easier. In most of the cases, multi modal data gives a better view of a certain event, characterising the specific object in comprehensive way, by providing more information.

- 1.2 Incomplete multi-view data

>In real-world applications, we often confront an obstacle that only partial views are available, due to the difficulties of high
cost, equipment failure, and so on [13]. Thus, learning with multiple incomplete views is a challenging yet valuable work.

> Unfortunately, the aforementioned strategies may either lose important information or introduce some errors, especially for the case where the amount of incomplete multi-view data is particularly large. In contrast, learning from massive complete-view data without view-missing is also complicated and time-consuming.

$\underline{\text{02. Solution Approach }}$

- reduced support vector machine (RSVM)
- multi-view privileged support vector machine (PSVM-2V)
- mix solution RPSVM-2V(Integration with RSVM and PSVM-2V)

_**RSVM**_

The RSVM can be expressed as follows:
$$
\mathop{min}\limits_{\overline{v},\gamma,\xi} 
\enspace \enspace \enspace \enspace
\frac{1} {2}(\overline{v'} \overline{v}+\gamma^2)+\frac{C} {2} \xi' \xi
$$

$$
s.t. \enspace \enspace D(K(A,\overline{A'})\overline{v}-e\gamma)+\xi\ge e, \xi\ge 0.
$$

_**PSVM-2V**_

To begin with, we can directly reformulate PSVM-2V (1) for incomplete-view learning, as shown below.

$$
\mathop{min}\limits_{W_{A_1},W_{A_1},\xi^{A_1},\xi^{A_2},\eta} 
\enspace \enspace \enspace \enspace
\frac{1} {2}(\left\Vert W_{A_1} \right\Vert^2+\mu\left\Vert W_{A_2} \right\Vert^2)+C_{A_1}(e'\xi^{A_1})+C_{A_2}(e'\xi^{A_2})+C(e'\eta)
$$

$$
s.t.  \enspace \enspace \enspace \enspace |[[<W_{A_1},\Phi_{A_1}>]]_l^r-[[<w_{A_2}>,\Phi_{A_2}]]_l^r |\le \eta+e\epsilon,
$$

$$
D_1<W_{A_1},\Phi_{A_1}>+\xi^{A_1} \ge e,
$$

$$
D_2<W_{A_2},\Phi_{A_2}>+\xi^{A_2} \ge e,
$$

$$
[[\xi^{A_1}]]_l^r \ge [[D_2<W_{A_2,\Phi_{A_2}}>]]_l^r,
$$

$$
[[\xi^{A_2}]]_l^r \ge [[D_1<W_{A_1,\Phi_{A_1}}>]]_l^r,
$$
$$
\xi^{A_1},\xi^{A_2},\eta \ge 0,
$$
According to the represent theorem [43], the solution of the optimization problem (3) can be formulated as 
$$ W_{A_k} = \sum_{n=1}^N v_{A_k}^{j} \phi_{k} (X_{j}^{A_k}) $$.
Then problem (3) can be rewritten as follows.

$$
\mathop{min}\limits_{v_{A_1},v_{A_2},\xi^{A_1},\xi^{A_2},\eta} 
\enspace \enspace \enspace \enspace
\frac{1} {2}(\sum_{i=1}^{m_1}\sum_{j=1}^{m_1} v_{A_1}^i v_{A_1}^j K_{A_1}(X_{i}^{A_1},X_{j}^{A_1})+\mu \sum_{i-1}^{m_2}\sum_{j-1}^{m_2} v_{A_2}^i v_{A_2}^j K_{A_2}(X_i^{A_2},X_j^{A_2}))+C_{A_1}(e'\xi^{A_1})+C_{A_2}(e'\xi^{A_2})+C(e'\eta)
$$

$$
s.t. 
\enspace \enspace \enspace \enspace
|[[K_{A_1}(A_1,A_1')v_{A_1}]]_l^r-[[K_{A_2}(A_2,\overline{A_2'}v_{A_2})]]| \le \eta + e \epsilon
$$

$$
D_1 K_{A_1}(A_1,A_1')v_{A_1}+\xi^{A_1} \ge e,
$$
$$
D_2 K_{A_2}(A_2,A_2')v_{A_2}+\xi^{A_2} \ge e,
$$

$$
[[\xi^{A_1}]]_l^r \ge [[D_2(K_{A2,A_2'}v_{A_2})]]_l^r
$$

$$
[[\xi^{A_2}]]_l^r \ge [[D_1(K_{A1,A_1'}v_{A_1})]]_l^r
$$

$$
\xi^{A_1},\xi^{A_2},\eta \ge 0.
$$

_**RPSVM-2V**_(*****)

Formally, RPSVM-2V can be built as follows.

$$
\mathop{min}\limits_{v_{A_1},v_{A_2},\xi^{A_1},\xi^{A_2},\eta} 
\enspace \enspace \enspace \enspace
\frac{1} {2}(\widetilde{v_{A_1}'}\widetilde{v_{A_1}}+\mu\widetilde{v_{A_2}'}\widetilde{v_{A_2}})+C_{A_1}(e'\xi^{A_1})+C_{A_2}+C(e'\eta)
$$

$$
D_1 \widetilde{K_{A_1}}(A_1,\overline{A_1}')\widetilde{v_{A_1}}+\xi^{A_1} \ge e,
$$
$$
D_2 \widetilde{K_{A_2}}(A_2,\overline{A_2}')\widetilde{v_{A_2}}+\xi^{A_2} \ge e,
$$

$$
[[\xi^{A_1}]]_l^r \ge [[D_2 \widetilde{K_{A_2}}(A_2,\overline{A_2'})\widetilde{v_{A_2}}]]_l^r
$$

$$
[[\xi^{A_2}]]_l^r \ge [[D_1 \widetilde{K_{A_1}}(A_1,\overline{A_1'})\widetilde{v_{A_1}}]]_l^r
$$
$$
\xi^{A_1},\xi^{A_2},\eta \ge 0.
$$

$\underline{\text{03. Theoretical analysis }}$

- generalization error bound
- Generalized performance
- parameter study

In this section, proof and algorithm are stated in detial for the final expriment output.


$\underline{\text{03. Exprimental Conclusions }}$

In this paper, we propose a new model RPSVM-2V by integrating RSVM with PSVM-2V in incomplete- and complete-view
scenarios. RPSVM-2V can not only fully leverage all available information for the incomplete views case, but also achieve
comparable performance with less computation and storage cost in the complete-view setting. 

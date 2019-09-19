-   [Operation Research](#operation-research)
    -   [Linear programming](#linear-programming)
        -   [Extreme point and Basic feasible solution](#extreme-point-and-basic-feasible-solution)
            -   [Convex set](#convex-set)
            -   [Convex function](#convex-function)
            -   [Linear programming](#linear-programming)
                -   [Extreme point](#extreme-point)
                -   [Basic feasible solution](#basic-feasible-solution)
        -   [Simplex method](#simplex-method)
            -   [Relationship between Basic feasible solution and Optimal solution](#relationship-between-basic-feasible-solution-and-optimal-solution)
            -   [Simplex method](#simplex-method)
            -   [Simplex tableau](#simplex-tableau)
            -   [Degeneration](#degeneration)
            -   [Proof of simplex method](#proof-of-simplex-method)
        -   [Initial basic feasible solution](#initial-basic-feasible-solution)
            -   [Add Slack variables](#add-slack-variables)
            -   [Big M method](#big-m-method)
            -   [Two-phase method](#two-phase-method)
        -   [Dual problem](#dual-problem)
            -   [Introduction to Dual problem](#introduction-to-dual-problem)
            -   [Dual problem](#dual-problem)
            -   [Properties of Dual problem](#properties-of-dual-problem)
                -   [Symmetry](#symmetry)
                -   [Weak duality](#weak-duality)
                -   [Optimality](#optimality)
                -   [Unbounded](#unbounded)
                -   [Strong duality](#strong-duality)
                -   [Complementary slackness](#complementary-slackness)
            -   [Dual simplex method](#dual-simplex-method)
        -   [Primal-dual method](#primal-dual-method)
            -   [Primal-dual method](#primal-dual-method)
                -   [Finding a Dual feasible solution](#finding-a-dual-feasible-solution)
                -   [Restricted Problem (RP) and Dual Restricted Problem (DRP)](#restricted-problem-rp-and-dual-restricted-problem-drp)
                -   [Improve Dual feasible solution](#improve-dual-feasible-solution)
                -   [Time complexity](#time-complexity)
            -   [Application: Shortest-path problem](#application-shortest-path-problem)
                -   [Linear programming](#linear-programming)
                -   [Dual problem and Dual Restricted Problem of Shortest-path problem](#dual-problem-and-dual-restricted-problem-of-shortest-path-problem)
    -   [Combinatorial Optimization](#combinatorial-optimization)
        -   [Linear integer programming, Cutting plane method, and Branch and bound](#linear-integer-programming-cutting-plane-method-and-branch-and-bound)
            -   [Linear integer programming](#linear-integer-programming)
                -   [0-1 Knapsack problem](#0-1-knapsack-problem)
                -   [Minimum Spanning Tree](#minimum-spanning-tree)
                -   [Bin packing problem](#bin-packing-problem)
                -   [Matching problem](#matching-problem)
            -   [Gomory cutting-plane method](#gomory-cutting-plane-method)
            -   [Branch and bound](#branch-and-bound)
        -   [Greedy solution for 1-class problem](#greedy-solution-for-1-class-problem)
            -   [Independent system](#independent-system)
                -   [Independent system](#independent-system)
                -   [Independent set and dependent set](#independent-set-and-dependent-set)
                -   [基与圈](#基与圈)
                -   [秩商](#秩商)
            -   [1-class maximization (minimization) problem](#1-class-maximization-minimization-problem)
            -   [Matroid](#matroid)
            -   [2-class greedy algorithm](#2-class-greedy-algorithm)
        -   [Approximation - 1](#approximation---1)
            -   [Vertex Cover](#vertex-cover)
                -   [Approximation algorithm 1](#approximation-algorithm-1)
                -   [Approximation algorithm 2](#approximation-algorithm-2)
                -   [Approximation algorithm 3](#approximation-algorithm-3)
            -   [Unrelated Parallel Machine Scheduling (UPMS)](#unrelated-parallel-machine-scheduling-upms)
        -   [Approximation - 2](#approximation---2)
            -   [均摊体积](#均摊体积)
            -   [Proof](#proof)
                -   [第一步：证明均摊体积不超过 1.7](#第一步证明均摊体积不超过-17)
                -   [第二步：证明除两个 bin 以外，其它 bin 权值均值至少为 1](#第二步证明除两个-bin-以外其它-bin-权值均值至少为-1)
        -   [Approximation - 3](#approximation---3)
            -   [Configuration LP](#configuration-lp)
            -   [Approximation algorithm](#approximation-algorithm)
            -   [Iterative algorithm](#iterative-algorithm)
                -   [第一步](#第一步)
                -   [第二步](#第二步)
                -   [第三步](#第三步)
                -   [回顾一下](#回顾一下)
        -   [Approximation - 4](#approximation---4)
            -   [Planar Steiner Tree](#planar-steiner-tree)
            -   [满足三角不等式的完全图上的斯坦纳树](#满足三角不等式的完全图上的斯坦纳树)
            -   [旅行商问题的近似比](#旅行商问题的近似比)
            -   [满足三角不等式的完全图的旅行商问题](#满足三角不等式的完全图的旅行商问题)
            -   [满足三角不等式的完全图的最短哈密尔顿路](#满足三角不等式的完全图的最短哈密尔顿路)
                -   [$k = 0$](#k--0)
                -   [$k = 1$](#k--1)
                -   [$k = 2$](#k--2)

# Operation Research

## Linear programming

### Extreme point and Basic feasible solution

#### Convex set

对于集合 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S)，若任意两元素 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x,%20y%20\in%20S)，且对于任意 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%200%20\le%20\theta%20\le%201) 有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\theta%20x%20+%20(1-\theta)y%20\in%20S)，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 是凸集（convex set，形象地想象就是凸的图形）。

可以推广：若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 为凸集，那么对任意 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n%20\ge%202) 个元素 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1,%20x_2,%20\dots,%20x_n%20\in%20S) 以及任意 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\sum_{i=1}^n%20\theta_i%20=%201)，都有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\sum_{i=1}^n%20\theta_ix_i%20\in%20S)。

利用归纳法证明：

1.  对于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n%20=%202)，根据凸集的定义，结论成立。
2.  若对于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n%20=%20k) 结论成立，即对任意 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1,%20x_2,%20\dots,%20x_k%20\in%20S) 以及任意 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\sum_{i=1}^k%20\theta_i%20=%201)，有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\sum_{i=1}^k%20\theta_ix_i%20\in%20S)。那么对于任意 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y_1,%20y_2,%20\dots,%20y_{k+1}%20\in%20S) 以及任意 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\sum_{i=1}^{k+1}%20\lambda_i%20=%201)，有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\sum_{i=1}^k%20\lambda_i%20=%201%20-%20\lambda_{k+1})，即 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\sum_{i=1}^k%20\lambda_i%20/%20(1%20-%20\lambda_{k+1})%20=%201)，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20t_{k+1}%20=%20\sum_{i=1}^k%20\lambda_iy_i%20/%20(1%20-%20\lambda_{k+1})%20\in%20S)，根据凸集的定义，自然有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\sum_{i=1}^{k+1}%20\lambda_iy_i%20=%20(1%20-%20\lambda_{k+1})t_{k+1}%20+%20\lambda_{k+1}y_{k+1}%20\in%20S)，结论成立。

凸集的交仍然是凸集，容易通过定义证明。

#### Convex function

对于定义在凸集 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 上的函数 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20f(x))，若对于任意 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%200%20\le%20\theta%20\le%201) 有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20f(\theta%20x%20+%20(1-\theta)%20y)%20\le%20\theta%20f(x)%20+%20(1-\theta)%20f(y))，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20f(x)) 是凸函数（convex function）。

可以推广为延森不等式（Jensen's inequality，原来一直念琴生不等式，被老师吐槽了一通...）：若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20f(x)) 是凸函数，那么对于任意 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\sum_{i=1}^n%20\theta_i%20=%201)，有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20f(\sum_{i=1}^n%20\theta_ix_i)%20\le%20\sum_{i=1}^n%20\theta_i%20f(x_i))。

若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20-f(x)) 是凸函数，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20f(x)) 是凹函数（concave function）；根据定义，仿射函数（affine function）即是凸函数又是凹函数。

凸函数美妙的性质是：局部最优就是全局最优。利用反证法证明：

若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2) 满足 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20|x_1-x_2|%20<%20\epsilon)，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2) 在对方的邻域内。假设 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\hat{x}) 是局部最优点而不是全局最优点，设 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x^*) 为全局最优点，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20f(\hat{x})%20>%20f(x^*))。由于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20f(x)) 为凸函数，那么对于它们凸组合出来的一点 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20=%20\theta%20\hat{x}%20+%20(1-\theta)x^*) 有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20f(x)%20\le%20\theta%20f(\hat{x})%20+%20(1-\theta)%20f(x^*)%20<%20f(\hat{x}))。只要取 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\theta%20=%201%20-%20\epsilon/(2|\hat{x}-x^*|))，就有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20|x%20-%20\hat{x}|%20=%20\epsilon/2%20<%20\epsilon)，说明 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 在 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\hat{x}) 的邻域内，而且比它优，与我们开始的假设不相符。

#### Linear programming

线性规划（linear programming，LP）问题指的是如下形式的优化问题：
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\min_{x} \quad c^Tx + d \\ \text{s.t.} \quad Ax \le b \\ Px = q
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
简单来说，就是目标函数和约束函数都是仿射函数的优化问题。

由于仿射函数既是凸函数又是凹函数，所以优化问题是 min 还是 max 问题不大；由于常数 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20d) 对优化问题的解没有影响，一般也可以去掉。课堂上讨论的 LP 问题是如下形式的问题
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\max_{x} \quad c^Tx \\ \text{s.t.} \quad Ax \le b \\ Px = q \\ x \ge 0
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
其实，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20Ax%20\le%20b) 这个约束，可以通过给每个不等式增加一个松弛变量进行松弛：对于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_1x_1%20+%20a_2x_2%20+%20\dots%20+%20a_nx_n%20\le%20b) 这个约束，我们添加 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_{n+1})，把问题变为![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_1x_1%20+%20a_2x_2%20+%20\dots%20+%20a_nx_n%20+%20x_{n+1}%20=%20b)。注意到原来的约束取的是小等于号，所以 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_{n+1}%20\ge%200) 这个条件是满足的。

这样，我们就把 LP 问题特化为
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\max_{x} \quad c^Tx \\ \text{s.t.} \quad Ax = b \\ x \ge 0
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)

为了发掘 LP 问题的一些性质，我们进行一些定义。

##### Extreme point

设 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 为凸集，若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20\in%20S) 无法表示为其它两个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 内元素的凸组合，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 是极点。

LP 问题的可行域实际上是很多超平面的交，最后组成的应该是一个超多面体。在这个超多面体有界的情况下，极点就是这些超多面体的顶点。对于 LP 问题而言，在超多面体有界的情况下，最优解一定可以在极点取到，且极点的数量是有限的（不过不知道怎么证明- -但是感性地想一想好像还是很有道理的，和函数的极值什么的有点像...）

##### Basic feasible solution

我们讨论 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20Ax%20=%20b) 有解且行满秩的情况（如果 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20Ax%20=%20b) 没有解那这个问题也没得做了，如果行不满秩，那么我们去掉线性相关的限制条件即可）。设 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 是一个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20m%20\times%20n) 的矩阵，根据线性代数的知识，我们可以从 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 中选出最多 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20m) 列线性无关的列向量，其它列向量都和它们线性相关。我们把这 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20m) 个列向量调整到前面去，把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 分成两部分：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A%20=%20\begin{bmatrix}%20A_B%20&%20A_N%20\end{bmatrix})，其中 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_B) 就是那 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20m) 个线性无关的列向量。我们容易构造出 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20Ax%20=%20b) 的一个解：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)x = \begin{bmatrix} A_B^{-1}b \\ 0 \end{bmatrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 称这种解为基可行解。显然，基可行解**至多**有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20C_n^m) 种。

接下来我们要证明一个厉害的定理：**每个极点都对应着一个基可行解，且每个基可行解都对应着一个极点**。有了这个定理，再结合可行域有解情况下最优解一定可以在极点取到，我们只要枚举基可行解，就能找到最优解了（至于如何优雅地枚举下节课再说- -）。

首先证明一个引理：**若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20=%20\begin{bmatrix}%20x_1%20&%20x_2%20&%20\dots%20&%20x_k%20&%200%20&%200%20&%20\dots%20\end{bmatrix}) 不是基可行解，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 中非 0 元素对应的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 中的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 列是线性相关的**。如果 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k%20>%20m) 显然这 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 列线性相关；如果 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k%20\le%20m) 但这 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 列线性无关，那么我们就可以把这 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 列当作 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_B)（如果 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k%20<%20m) 就再选几个线性无关的列，凑成 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20m) 个），![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 就成为了一个基可行解。所以这 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 列一定是线性相关的。

首先我们用反证法证明：若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 为极点，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 也是基可行解。假设 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 并不是基可行解，我们把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 里的非 0 元素（假设有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 个）都调整到前面去（相应地，也要把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 中这 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 个非 0 元素对应的列调到前面去），那么我们可以把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 写为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20=%20\begin{bmatrix}%20x_1%20&%20x_2%20&%20\dots%20&%20x_k%20&%200%20&%200%20&%20\dots%20\end{bmatrix})。根据引理，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 中对应的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 列是线性相关的。

记线性相关的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 列为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20p_1,%20p_2,%20\dots,%20p_k)，我们就有不全为 0 的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\lambda_i)，使得 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\sum_{i=1}^k%20\lambda_i%20p_i%20=%200)。记辅助向量 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20v%20=%20\begin{bmatrix}%20\lambda_1%20&%20\lambda_2%20&%20\dots%20&%20\lambda_k%20&%200%20&%200%20&%20\dots%20\end{bmatrix}^T)，令 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x'%20=%20x%20+%20\epsilon%20v)，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x''%20=%20x%20-%20\epsilon%20v)，显然我们有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20=%20(x'%20+%20x'')%20/%202)。由于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 至 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_k) 均大于 0，当 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\epsilon) 充分小时，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x'%20\ne%20x'')，且 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x'%20\ge%200) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x''%20\ge%200) 的性质也能得到保证。另外，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20Ax'%20=%20A(x%20+%20\epsilon%20v)%20=%20Ax%20=%20b)，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20Ax''%20=%20A(x%20-%20\epsilon%20v)%20=%20Ax%20=%20b)，说明 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x') 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x'') 都是可行解。这就是说，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 可以表示为可行域内其它两点的凸组合，与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 是极点的假设矛盾，反证法结束。

我们继续用反证法证明：若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 为基可行解，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 为极点。假设 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 不是极点，那么有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20=%20(x'%20+%20x'')%20/%202)，而且 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x'%20\ne%20x'')，以及 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x'%20\ge%200) 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x''%20\ge%200)。设 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_i%20=%200)，注意到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x') 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x'') 元素非负，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x'_i%20=%20x''_i%20=%200)。设 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 中有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 个非 0 元素，根据基可行解的定义，这些元素所对应的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 的列向量是线性无关的，那么想从这些列向量得到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20b)，线性组合的方式也是唯一的。这就说明了 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20=%20x'%20=%20x'')，则 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 是极点，反证法结束。

这次课上还遇到了一个有趣的转换。给定 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20m%20\times%20n) 的矩阵 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20m) 维向量 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20b)，考虑以下优化问题：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\max_{x} \min_{j} \quad \sum_{i=1}^m b_ix_i - \sum_{i=1}^m a_{i,j}x_i \\ \text{s.t.} \quad x \le q \\ x \ge 0![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 这个问题第一眼看上去并不像一个线性规划，因为这是一个 max 再套 min 的问题。我们把它改写一下：
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\max_{x} \quad \sum_{i=1}^m b_ix_i - (\max_{j} \quad \sum_{i=1}^m a_{i,j}x_i) \\ \text{s.t.} \quad x \le q \\ x \ge 0
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
注意到第二个 max 针对的变量 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 的取值是有限的（只有 1 到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n)），我们就可以把它提出来，变成下面的问题：
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\max_{x,y} \quad \sum_{i=1}^m b_ix_i - y \\ \text{s.t.} \quad x \le q \\ x \ge 0 \\ y \ge \sum_{i=1}^m a_{i,j}x_i \quad \forall j = 1, 2, \dots, n
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
一下子就变成了线性规划问题，感觉这个操作非常厉害...

### Simplex method

#### Relationship between Basic feasible solution and Optimal solution

接上一次课，首先是用反证法，证明一下最优解一定可以在基可行解处取到：

假设没有基可行解是最优解，设最优解为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20=%20\begin{bmatrix}%20x_1%20&%20x_2%20&%20\dots%20&%20x_k%20&%200%20&%200%20&%20\dots%20&%200%20\end{bmatrix}^T) 不是基可行解，由上一次课的一个引理，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_k) 对应的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 中 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 列 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20p_1,%20p_2,%20\dots,%20p_k) 是线性相关的。那么有不全为 0 的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\lambda)，使得 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\sum_{i=1}^k%20\lambda_i%20p_i%20=%200)。

记辅助向量 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20v%20=%20\begin{bmatrix}%20\lambda_1%20&%20\lambda_2%20&%20\dots%20&%20\lambda_k%20&%200%20&%200%20&%20\dots%20&%200%20\end{bmatrix}^T)，我们仍然构造 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x'%20=%20x%20+%20\epsilon%20v) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x''%20=%20x%20-%20\epsilon%20v)（熟悉的套路...）。显然有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20=%20\frac{x'+x''}{2})，由于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 是最优解，当然 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x') 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x'') 也是最优解。如果存在 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\lambda_i%20<%200)，那么我们取 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\epsilon%20=%20\min\limits_{\lambda_i%20<%200}%20-\frac{x_i}{\lambda_i})，就能把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x') 中 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_k) 的某一个变成 0；如果不存在 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\lambda_i%20<%200)，那么我们取 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\epsilon%20=%20\min%20\frac{x_i}{\lambda_i})，就能把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x'') 中 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_k) 的某一个变成 0。也就是说，非 0 元素少了一个。这样一直构造下去，我们就能不断减少非 0 元素，直到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_k) 在 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 中对应的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 列线性无关，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 就变成了一个基可行解。而且在构造过程中，最优性没有改变，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 还是最优解。

#### Simplex method

接下来介绍用单纯形法（simplex method）求解线性规划问题的方式。单纯形法的每一步都在引入一个非基变量取代某一基变量，找出目标函数值更优的另一基本可行解，这样一步一步调整到最优解。

来看一个例题：
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\begin{matrix} & \max\limits_{x} \quad 3x_1 + 2x_2 \\ \text{s.t.} & 2x_1 + x_2 \le 12 \\ & x_1 + 2x_2 \le 9 \\ & x_1, x_2 \ge 0 \end{matrix}
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
引入松弛变量，将原问题变为 
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\begin{matrix} & \max\limits_{x} \quad z = 3x_1 + 2x_2 \\ \text{s.t.} & 2x_1 + x_2 + x_3 = 12 \\ & x_1 + 2x_2 + x_4 = 9 \\ & x_1, x_2, x_3, x_4 \ge 0 \end{matrix}
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
首先，我们有一个可行解：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20=%20\begin{bmatrix}%200%20&%200%20&%2012%20&%209%20\end{bmatrix}^T)，当前目标函数值为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20z%20=%200)。我们把各个变量用非基变量进行表示，有
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
x_3 = 12 - 2x_1 - x_2 \\ x_4 = 9 - x_1 - 2x_2 \\ z = 3x_1 + 2x_2
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
看起来 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 对 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20z) 的贡献比 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2) 来的大（![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 的系数比较大，这个系数称为“检验数”），我们考虑把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 变成基变量。要注意，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_3%20\ge%200) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_4%20\ge%200) 的条件仍然需要成立。根据 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_3) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_4) 之间的表达式不难看出，当 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20=%206) 时，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_3) 最先变成 0，我们把它从基变量中去除。

现在，可行解变为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20=%20\begin{bmatrix}6%20&%200%20&%200%20&%203\end{bmatrix}^T)，当前目标函数值为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20z%20=%2018)。继续把各个变量用非基变量进行表示，有
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
x_1 = 6 - x_2/2 - x_3/2 \\ x_4 = 3 - 3x_2/2 + x_3/2 \\ z = 18 + x_2/2 - 3x_3/2
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
从系数可以看出，只有增加 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2) 才能对目标函数值的增大有所贡献，考虑把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2) 变成基变量。从 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2) 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_4) 的关系式中也不难发现，当 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2%20=%202) 时，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_4) 最先变成 0，我们把它从基变量中去除。

现在，可行解变为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20=%20\begin{bmatrix}%205%20&%202%20&%200%20&%200%20\end{bmatrix}^T)，当前目标函数值为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20z%20=%2019)。继续把各个变量用非基变量进行表示，有 
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
x_1 = 5 - 2x_3/3 + x_4/3 \\ x_2 = 2 + x_3/3 - 2x_4/3 \\ z = 19 - 4x_3/3 - x_4/3
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
可以发现，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_3) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_4) 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20z) 相关的系数都是负值，那么无论把哪个变量加入基变量，都只能让目标函数值变小了。所以此时我们就得到了线性规划问题的最优解：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20=%20\begin{bmatrix}%205%20&%202%20&%200%20&%200%20\end{bmatrix}^T)，目标函数值为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20z%20=%2019)。

当然，完全有可能出现某一个变量可以无限增大，求不出最优解的情况。考虑以下线性规划问题：
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\begin{matrix} & \max\limits_{x} \quad 2x_1 + x_2 \\ \text{s.t.} & -3x_1 + x_2 \le 3 \\ & -4x_1 + x_2 \le 5 \\ & x_1, x_2 \ge 0 \end{matrix}
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
加入松弛变量后有
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\begin{matrix} & \max\limits_{x} \quad 2x_1 + x_2 \\ \text{s.t.} & -3x_1 + x_2 + x_3 = 3 \\ & -4x_1 + x_2 + x_4 = 5 \\ & x_1, x_2, x_3, x_4 \ge 0 \end{matrix}
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
有初始可行解 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20=%20\begin{bmatrix}%200%20&%200%20&%203%20&%205%20\end{bmatrix}^T)，仍然用非基变量表示其它变量，有
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
x_3 = 3 + 3x_1 - x_2 \\ x_4 = 5 + 4x_1 - x_2 \\ z = 2x_1 + x_2
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
从 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_3) 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_4) 的关系式中可以看出，不管 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 如何增大，两个基变量都不会小于 0，而且 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 的检验数也是正数，那么这个优化问题没有最优解。

归纳起来，单纯形法的基本步骤如下（来自 wiki）：

1.  把线性规划问题的约束方程组表达成典范型方程组，找出基本可行解作为初始基可行解。
2.  若基本可行解不存在，即约束条件有矛盾，则问题无解。
3.  若基本可行解存在，从初始基可行解作为起点，根据最优性条件和可行性条件，引入非基变量取代某一基变量，找出目标函数值更优的另一基本可行解。
4.  按步骤3进行迭代，直到对应检验数满足最优性条件（这时目标函数值不能再改善），即得到问题的最优解。
5.  若迭代过程中发现问题的目标函数值无界，则终止迭代。

#### Simplex tableau

可以用矩阵的形式，把各个变量用非基变量进行表示。

设要优化的线性规划问题（标准形式）为
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\begin{matrix} & \max\limits_{x} \quad z = c^Tx \\ \text{s.t.} & Ax \le b \\ & x \ge 0 \end{matrix}
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
我们可以把各个矩阵或向量根据基变量和非基变量分为两部分：令 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c^T%20=%20\begin{bmatrix}%20c_B^T%20&%20c_N^T%20\end{bmatrix})，令 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A%20=%20\begin{bmatrix}%20A_B%20&%20A_N%20\end{bmatrix})，令 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20=%20\begin{bmatrix}%20x_B^T%20&%20x_N^T%20\end{bmatrix}^T)，显然我们有
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
A_Bx_B + A_Nx_N = b \\ z = c_B^Tx_B + c_N^Tx_N
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
通过移项就能用 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_N) 表示其它变量：
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
x_B = A_B^{-1}b - A_B^{-1}A_Nx_N \\ z = c_B^TA_B^{-1}b + (c_N^T - c_B^TA_B^{-1}A_N)x_N
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
当然啦，由于基可行解中 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_N%20=%200)，我们有
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
x_B = A_B^{-1}b \\ z = c_B^TA_B^{-1}b
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
单纯形表可以帮助我们利用矩阵形式，通过列表的方式求解线性规划问题，也利于编程实现。

首先画一张这样的表：
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\begin{array}{c|cc|c} & c_B^T & c_N^T & 0 \\ \hline x_B & A_B & A_N & b\end{array}
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
利用行变换将 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_B) 变为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I)，根据线性代数的知识，这相当于左乘了一个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_B^{-1})，那么表会变成这样：
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\begin{array}{c|cc|c} & c_B^T & c_N^T & 0 \\ \hline x_B & I & A_B^{-1}A_N & A_B^{-1}b\end{array}
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
然后再把下面一行乘上 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_B^T)，用上面一行减一减，得到
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\begin{array}{c|cc|c} & 0 & c_N^T-c_B^TA_B^{-1}A_N & -c_B^TA_B^{-1}b \\ \hline x_B & I & A_B^{-1}A_N & A_B^{-1}b\end{array}
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
这是一张非常神奇的表：第一行第二列（![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_B) 那一列我们不看）就是检验数，第一行第三列就是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20-z)，而基变量和非基变量之间的系数也可以通过第二行的第二、三两列求出，计算起来非常方便。表格每这样计算一次，就是单纯形法里的一次迭代。

虽然这个表格看起来有点麻烦（比如，看起来每次迭代好像都要重新写上 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_B) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_N) 什么的，从头开始变化？），但实际操作起来是非常简便的，每次迭代的变化不会很多。看一个例子就知道了：

![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\begin{matrix} & \max\limits_{x} \quad 3x_1 + 2x_2 \\ \text{s.t.} & 2x_1 + x_2 \le 12 \\ & x_1 + 2x_2 \le 9 \\ & x_1, x_2 \ge 0 \end{matrix}
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
这个例子和上一节的例子是一样的。仍然加入松弛变量变化为标准形式：
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\begin{matrix} & \max\limits_{x} \quad z = 3x_1 + 2x_2 \\ \text{s.t.} & 2x_1 + x_2 + x_3 = 12 \\ & x_1 + 2x_2 + x_4 = 9 \\ & x_1, x_2, x_3, x_4 \ge 0 \end{matrix}
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
初始的基可行解是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20=%20\begin{bmatrix}%200%20&%200%20&%2012%20&%209\end{bmatrix}^T)，绘制初始的单纯形表：
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\begin{array}{c|cccc|c} & 3 & 2 & 0 & 0 & 0 \\ \hline x_3 & 2 & 1 & 1 & 0 & 12 \\ x_4 & 1 & 2 & 0 & 1 & 9 \end{array}
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
由于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_B%20=%20\begin{bmatrix}%20x_3%20&%20x_4%20\end{bmatrix}%20^%20T)，所以此时的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_B) 由第二行和第三行的三、四两列组成，而且恰好是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I)；![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_B^T) 由第一行的第三、四两列组成，而且恰好是 0，我们直接来到了最后一步。

根据单纯形法，我们选择检验数中较大的那个（3，对应 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1)）。由于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%2012/2%20=%206%20<%209/1%20=%209)，所以 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 成为基变量，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_3) 被移出基变量。修改表格为
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\begin{array}{c|cccc|c} & 3 & 2 & 0 & 0 & 0 \\ \hline x_1 & 2 & 1 & 1 & 0 & 12 \\ x_4 & 1 & 2 & 0 & 1 & 9 \end{array}
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
由于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_B%20=%20\begin{bmatrix}%20x_1%20&%20x_4%20\end{bmatrix}%20^%20T)，所以此时的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_B) 由第二行和第三行的一、四两列组成（有人可能会问：为什么不用原问题里的矩阵 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 呢？因为矩阵进行行变化之后，不改变方程的解，而且每次都用修改后的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A)，只要更改一列就可以把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_B) 变成 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I)，较为方便）。我们发现，只要把第一列改成单位向量即可，通过行变换，变化后的表格为
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\begin{array}{c|cccc|c} & 3 & 2 & 0 & 0 & 0 \\ \hline x_1 & 1 & 1/2 & 1/2 & 0 & 6 \\ x_4 & 0 & 3/2 & -1/2 & 1 & 3 \end{array}
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
接下来我们把下面的几列乘以 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_B^T)，注意此时 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_B^T) 是由第一行第一、四列组成的，所以我们要计算的是
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\begin{bmatrix}3 & 0\end{bmatrix}\begin{bmatrix} 1 & 1/2 & 1/2 & 0 & 6 \\ 0 & 3/2 & -1/2 & 1 & 3 \end{bmatrix}
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
把第一行减去矩阵计算的结果，我们就有了第二次迭代后的单纯形表：
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\begin{array}{c|cccc|c} & 0 & 1/2 & -3/2 & 0 & -18 \\ \hline x_1 & 1 & 1/2 & 1/2 & 0 & 6 \\ x_4 & 0 & 3/2 & -1/2 & 1 & 3 \end{array}
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
依然选择最大的检验数（![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%201/2)，对应 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2)），由于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%203/(3/2)%20=%202%20<%206/(1/2)%20=%2012)，所以 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2) 成为基变量，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_4) 被移出基变量。进行和上面类似的过程。
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\begin{array}{c|cccc|c} & 3 & 2 & 0 & 0 & 0 \\ \hline x_1 & 1 & 1/2 & 1/2 & 0 & 6 \\ x_2 & 0 & 3/2 & -1/2 & 1 & 3 \end{array}
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)

![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\begin{array}{c|cccc|c} & 3 & 2 & 0 & 0 & 0 \\ \hline x_1 & 1 & 0 & 2/3 & -1/3 & 5 \\ x_2 & 0 & 1 & -1/3 & 2/3 & 2 \end{array}
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)

第三次迭代后的单纯形表为：
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
\begin{array}{c|cccc|c} & 0 & 0 & -4/3 & -1/3 & -19 \\ \hline x_1 & 1 & 0 & 2/3 & -1/3 & 5 \\ x_2 & 0 & 1 & -1/3 & 2/3 & 2 \end{array}
![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)
此时所有检验数都为非正数，那么单纯形法结束。单纯形表右上角的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20-z) 就是最优目标函数的相反数，所以最优目标函数为 19。表格最右一列的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_B^{-1}b) 就是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_B) 的取值，所以最优解为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20=%205)，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2%20=%202)。

#### Degeneration

退化是指一个基可行解中，存在至少一个基变量为 0 的情况。也就是说，这个基变量可以和另一个非基变量任意互换，而不影响结果（反正两个变量在这个解里取值都是 0）。

退化会给单纯形法的求解带来一些麻烦：它可能会让单纯形法陷入循环，可能无法找到最优解。[这个页面](https://people.orie.cornell.edu/miketodd/or630/SimplexCyclingExample.pdf)里提供了一个让单纯形法无限循环的例子。

不过，我们可以使用如下法则让单纯形法一定不会陷入循环（也就是一定能找到最优解）：在有多个可以入基的变量时，选择下标最小的一个；在有多个可以出基的变量时，也选择下标最小的一个。不过我不会证明...

#### Proof of simplex method

接下来证明单纯形法在非退化的情况下为什么可以取到最优解，以及为什么可以停止。

首先证明：**若检验数向量 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\hat{c}%20=%20c_N%20-%20c_B^TA_B^{-1}A_N) 的每一维都小等于 0，那么此时基可行解 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 是最优解**。

反证：假设有一个更优的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y) 才是最优解。令 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20d%20=%20x%20-%20y)，我们有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)Ax - Ay = b - b = 0 \\ = Ad = A_Bd_B + A_Nd_N![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)d_B = -A_B^{-1}A_Nd_N![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 则 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)c^Td = c_B^Td_B + c_N^Td_N \\ = (c_N^T-c_B^TA_B^{-1}A_N)d_N = \hat{c}d_N![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 要注意，这里的 B（基变量）和 N（非基变量）都是对于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 而言的。

显然根据基可行解的定义 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_N%20=%200)，又 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y%20\ge%200)，所以 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20d_N%20\ge%200)；又 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\hat{c}%20\le%200)，所以 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c^Td%20=%20\hat{c}d_N%20\le%200)，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c^Ty%20=%20c^Tx%20+%20c^Td%20\le%20c^Tx)，说明 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y) 并没有比 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 更优，矛盾。这就说明了为什么在检验数均小等于 0 时停止算法，就能得到最优解。

类似地，我们可以说明**若基可行解 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 是非退化的最优解，那么检验数向量的每一维都小等于 0**。否则由于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 是非退化的最优解，如果有一个检验数大于 0，它对应的非基变量一定有增加的空间（而不会像退化的解一样，增加的空间为 0），那么就能构造一个更优的解。这就说明了，在非退化的情况下，肯定有解满足算法停止的情况。

最后简单说明**非退化情况下的单纯形法一定可以停止**。因为非退化的单纯形法的每一次迭代都会让答案更优一点，所以它访问的基可行解都是不会重复的。而基可行解的数量是有限的（根据上一节课，至多 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20C_n^m) 个），其中又存在着让算法停止的最优解，所以算法一定可以停止。单纯形法的最差复杂度是指数级的（这个最差情况由 Klee 和 Minty 提出，是一个高维立方体，详见[维基百科](https://en.wikipedia.org/wiki/Klee–Minty_cube)），不过在大多数问题下，它的运行效率都还是比较快的。

### Initial basic feasible solution

#### Add Slack variables

松弛变量总是那么好用...考虑原问题为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix}\max\limits_{x} & z = c^Tx \\ \text{s.t.} & Ax = b \\ & x \ge 0\end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 我们加入松弛变量 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{x})，把问题转化为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix}\max\limits_{x} & z = c^Tx \\ \text{s.t.} & Ax + \bar{x} = b \\ & x, \bar{x} \ge 0\end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) （这里我们要求 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20b%20\ge%200)，一般的带不等式约束的线性规划问题，都能通过移项、加/减松弛变量等方法凑出 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20b%20\ge%200) 的只含等式约束的线性规划问题标准形式）

这样，我们就有了一个天然的初始可行解 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20=%200,%20\bar{x}%20=%20b)。

但还存在一个问题：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{x}) 是我们添加进去的变量，我们希望最后的最优解里，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{x}) 能全部出基（这样 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{x}%20=%200)），只留下 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 中的变量作为基变量，这样我们才能在不改变原问题的情况下，获得原问题的解。

#### Big M method

一个很自然的想法，就是对不为 0 的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{x}) 进行“惩罚”。我们可以将目标函数改为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)z = c^Tx - M\sum_{i=1}^m\bar{x}_i![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 如果 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20M) 是一个足够大的正数，那么如果原问题存在可行解，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{x}) 就会在 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20-M) 这个“严厉的惩罚”之下变成 0。

可是这个方法有一个很大的缺陷：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20M) 的值到底该取多少呢？如果 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20M) 的值取得太小导致 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{x}) 最后还是非 0，到底是因为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20M) 太小了，还是因为问题本来就没有可行解呢；如果 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20M) 的值取得太大，可能会带来计算上的误差。所以这个方法貌似不太常用...

#### Two-phase method

我们只是想要找到线性规划问题的一个初始可行解，并不一定要同时获得原问题的最优解，所以我们完全可以另外设计一个只由松弛变量组成的优化问题，解决了这个优化问题，就找到了原问题的一个可行解。我们设计优化问题如下 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix}\min\limits_{\bar{x}} & \sum_{i=1}^m\bar{x}_i \\ \text{s.t.} & Ax + \bar{x} = b \\ & x, \bar{x} \ge 0\end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) （如果觉得看 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\max) 比较习惯的话也可以写成 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\max\limits_{x}%20\quad%20-\sum\limits_{i=1}^m\bar{x}_i)）

对于这个优化问题，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{x}%20=%20b) 就是一个可行解，所以就不用费心再去找初始可行解了。

容易发现，如果这个优化问题的最优解的目标函数值不为 0，那么原问题无可行解；如果最优解让目标函数值为 0，就说明了存在一种 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 的取值满足约束，且 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{x}%20=%200)，这样就找到了原问题的一个可行解。我们再以这个可行解为起点，利用单纯形法求出原问题的最优解即可。

来举一个例子，考虑以下线性规划问题 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} & \max\limits_{x} \quad 4x_1-x_2+x_3 \\ \text{s.t.} & x_1+2x_2+3x_3=1 \\ & 2x_1+3x_2+2x_3 = 2 \\ & x \ge 0\end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 加入松弛变量，转化为两阶段法的优化问题 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} & \max\limits_{x} \quad -x_4-x_5 \\ \text{s.t.} & x_1+2x_2+3x_3+x_4 = 1 \\ & 2x_1+3x_2+2x_3+x_5 = 2 \\ & x \ge 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 利用单纯形表求解，第一次迭代：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{array}{c|ccccc|c} & 3 & 5 & 5 & 0 & 0 & 3 \\ \hline x_4 & 1 & 2 & 3 & 1 & 0 & 1 \\ x_5 & 2 & 3 & 2 & 0 & 1 & 2\end{array}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 为了展示一个特殊情况，我们不按常规选择检验数最大的入基，而是选择 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 入基，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_4) 出基，第二次迭代：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{array}{c|ccccc|c} & 0 & -1 & -4 & -3 & 0 & 0 \\ \hline x_1 & 1 & 2 & 3 & 1 & 0 & 1 \\ x_5 & 0 & -1 & -4 & -2 & 1 & 0 \end{array}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 我们发现，目标函数值已经是 0 了，但是基变量里有一个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_5)，还是没有把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{x}) 完全从基变量里弄出去。不过没关系，这是一个退化情况，我们有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2%20=%20x_3%20=%20x_5%20=%200)。我们此时可以让 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2) 入基，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_5) 出基，就能把基变量变为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2)。同时也求出了原问题的一个可行解：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20=%201,%20x_2%20=%20x_3%20=%200)，基变量是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2)。

接下来继续利用单纯形表求解原问题。第一次迭代：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{array}{c|ccc|c} & 0 & 0 & 25 & -4 \\ \hline x_1 & 1 & 0 & -5 & 1 \\ x_2 & 0 & 1 & 4 & 0 \end{array}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 是一个退化情况，不过我们还是继续计算。让 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_3) 入基，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2) 出基，第二次迭代：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{array}{c|ccc|c} & 0 & -25/4 & 0 & -4 \\ \hline x_1 & 1 & 5/4 & 0 & 1 \\ x_3 & 0 & 1/4 & 1 & 0 \end{array}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 所有检验数都非正，迭代结束。我们获得了原问题的最优解：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20=%201,%20x_2%20=%20x_3%20=%200)，此时目标函数值为 4。

### Dual problem

#### Introduction to Dual problem

考虑一个线性规划问题：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix}\max\limits_x & 4x_1 + 3x_2 \\ \text{s.t.} & 2x_1 + 3x_2 \le 24 \\ & 5x_1 + 2x_2 \le 26 \\ & x \ge 0\end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 我们可以把这个问题看作一个生产模型：一份产品 A 可以获利 4 单位价格，生产一份需要 2 单位原料 C 和 5 单位原料 D；一份产品 B 可以获利 3 单位价格，生产一份需要 3 单位原料 C 和 2 单位原料 D。现有 24 单位原料 C，26 单位原料 D，问如何分配生产方式才能让获利最大。

但假如现在我们不生产产品，而是要把原料都卖掉。设 1 单位原料 C 的价格为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y_1)，1 单位原料 D 的价格为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y_2)，每种原料制定怎样的价格才合理呢？

首先，原料的价格应该不低于产出的产品价格（不然还不如自己生产...），所以我们有如下限制：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)2y_1 + 5y_2 \ge 4 \\ 3y_1 + 2y_2 \ge 3![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 当然也不能漫天要价（也要保护消费者利益嘛- -），所以我们制定如下目标函数：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\min_y \quad 24y_1 + 26y_2![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 合起来就是下面这个线性规划问题：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \min\limits_y & 24y_1 + 26y_2 \\ \text{s.t.} & 2y_1 + 5y_2 \ge 4 \\ & 3y_1 + 2y_2 \ge 3 \\ & y \ge 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 这个问题就是原问题的对偶问题。

#### Dual problem

对于一个线性规划问题（称为原问题，primal，记为 P） ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \max\limits_x & c^Tx \\ \text{s.t.} & Ax \le b \\ & x \ge 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 我们定义它的对偶问题（dual，记为 D）为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \min\limits_x & b^Ty \\ \text{s.t.} & A^Ty \ge c \\ & y \ge 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 这里的对偶变量 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y)，可以看作是对原问题的每个限制，都用一个变量来表示。

原问题限制条件的不等号，和对偶问题限制条件的不等号，是相互关联的。假设原问题是一个最大化问题，设 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_i^T) 表示 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 中的第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 行，我们有以下结论：

1.  若限制条件为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_i^Tx%20\le%20b_i)，那么对偶问题中有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y_i%20\ge%200)

证明略，根据对偶问题的定义即可获得。

2.  若限制条件为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_i^Tx%20\ge%20b_i)，那么对偶问题中有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y_i%20\le%200)

把不等式转换为标准形式显然有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20-a_i^Tx%20\le%20-b_i)。令 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{y}_i%20=%20-y_i)，用 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{y}_i) 表示原问题的第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 个限制，令 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y'%20=%20\begin{bmatrix}%20y_1%20&%20\dots%20&%20y_{i-1}%20&%20\bar{y}_i%20&%20y_{i+1}%20&%20\dots%20&%20y_m%20\end{bmatrix}^T)，那么对偶问题可以写为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \min\limits_{y'} & \begin{bmatrix} b_1 & \dots & b_{i-1} & -b_i & b_{i+1} & \dots & b_m \end{bmatrix} y' \\ \text{s.t.} & \begin{bmatrix} a_1 & \dots & a_{i-1} & -a_i & a_{i+1} & \dots & a_m \end{bmatrix} y' \ge c \\ & y' \ge 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 将 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y_i%20=%20-\bar{y}_i) 代回式中即可获得。

3.  若限制条件为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_i^Tx%20=%20b_i)，那么对偶问题中对 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y_i) 无限制

![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_i^Tx%20=%20b_i) 可以看作 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_i^Tx%20\ge%20b_i) 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_i^Tx%20\le%20b_i)，用 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{y}_i) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\tilde{y}_i) 表示这两个限制，并令 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y'%20=%20\begin{bmatrix}%20y_1%20&%20\dots%20&%20\bar{y}_i%20&%20\tilde{y}_i%20&%20\dots%20&%20y_m%20\end{bmatrix}^T)，那么对偶问题可以写为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \min\limits_{y'} & \begin{bmatrix} b_1 & \dots & b_i & -b_i & \dots & b_m \end{bmatrix} y' \\ \text{s.t.} & \begin{bmatrix} a_1 & \dots & a_i & -a_i & \dots & a_m \end{bmatrix} y' \ge c \\ & y' \ge 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 令 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y_i%20=%20\bar{y}_i%20-%20\tilde{y}_i)，代回上面的式子中即可获得原来的对偶问题的形式。容易看出 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y_i) 是可正可负的，没有限制。

4.  若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_i%20\ge%200)，那么对偶问题中有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_i^Ty%20\ge%20c_i) 
5.  若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_i%20\le%200)，那么对偶问题中有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_i^Ty%20\le%20c_i) 
6.  若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_i) 无限制，那么对偶问题中有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_i^Ty%20=%20c_i)

这三条的推导和前三条类似，这里不再赘述。

#### Properties of Dual problem

这一部分讲解线性规划中对偶问题的若干性质。

##### Symmetry

P 的对偶是 D，那么 D 的对偶也是 P。如果我们把对偶问题变成标准形式，有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \max\limits_y & y^T(-b) \\ \text{s.t.} & (-A^T)y \le -c \\ & y \ge 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 它的对偶问题是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \min\limits_x & -c^Tx \\ \text{s.t.} & -Ax \ge -b \\ & x \ge 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 把目标函数和限制都乘以 -1 之后就是原问题。

##### Weak duality

设 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y) 分别是原问题和对偶问题的可行解，我们有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c^Tx%20\le%20b^Ty)。这是因为，由 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y) 的可行性我们有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A^Ty%20\ge%20c)，即 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y^TA%20\ge%20c^T)，两边同乘以 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y^TAx%20\ge%20c^Tx)；由 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 的可行性我们还有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20Ax%20\le%20b)，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y^TAx%20\le%20y^Tb)，合起来就是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c^Tx%20\le%20b^Ty)。

由弱对偶定理我们马上获得以下两条性质。

##### Optimality

若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y) 分别是原问题和对偶问题的可行解，而且 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c^Tx%20=%20b^Ty)，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y) 分别是原问题和对偶问题的最优解。

##### Unbounded

若原问题有可行解无最优解（就是目标函数值可以取无穷大），那么对偶问题无可行解；若对偶问题有可行解无最优解，那么原问题无可行解。

当然啦，也有两个问题都无解的情况发生，比如下面这个线性规划 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \max\limits_x & x_1 + x_2 \\ \text{s.t.} & x_1 - x_2 \le 1 \\ & -x_1 + x_2 \le -2 \\ & x \ge 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 它的对偶问题是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \min\limits_y & y_1 - 2y_2 \\ \text{s.t.} & y_1 - y_2 \ge 1 \\ & -y_1 + y_2 \ge 1 \\ & y \ge 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)

##### Strong duality

若原问题（或对偶问题）有有限最优解，那么对偶问题（或原问题）也有有限最优解，且二者最优解相等。

可以通过单纯形法的计算过程来辅助证明。

假设引入松弛变量之后，原问题变为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \max\limits_x & c^Tx \\ \text{s.t.} & \bar{A}x = b \\ & x \ge 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 画出初始的单纯形表 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{array}{c|cc|c} & c^T & 0 & 0 \\ \hline x^*_B & A & I & b \end{array}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 最终的单纯形表为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{array}{c|cc|c} & c^T - c^T_B\bar{A}_B^{-1}A & -c^T_B\bar{A}_B^{-1} & -c^T_B\bar{A}_B^{-1}b \\ \hline x^*_B & \bar{A}_B^{-1}A & \bar{A}_B^{-1} & \bar{A}_B^{-1}b \end{array}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 由于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x^*_B) 是原问题最优的基变量组合，那么检验数均非正，即 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)c^T \le c^T_B\bar{A}_B^{-1}A \\ -c^T_B\bar{A}_B^{-1} \le 0![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 不妨取 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y^{*T}%20=%20c^T_B\bar{A}_B^{-1})，根据上面两个式子，我们有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A^Ty^*%20\ge%20c) 以及 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y^*%20\ge%200)，即 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y^*) 是一个可行解。根据单纯形法，我们知道 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x^*_B%20=%20\bar{A}_B^{-1}b)，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x^*_N%20=%200)，那么对偶问题的目标函数值为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20b^Ty^*%20=%20y^{*T}b%20=%20c^T_B\bar{A}_B^{-1}b%20=%20c^T_Bx^*_B%20=%20c^Tx^*)，即我们找到了一对可行的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y)，使得原问题和对偶问题的目标函数值相等，那么根据弱对偶定理，这两个可行解分别是原问题和对偶问题的最优解。

##### Complementary slackness

若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x^*) 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y^*) 分别是原问题和对偶问题的可行解，那么以下两点等价：

\1. ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x^*) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y^*) 分别是原问题和对偶问题的最优解；

\2. ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(y^{*T}A%20-%20c^T)x^*%20=%200) 且 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y^{*T}(Ax^*-b)%20=%200)。

由 2 推出 1 很简单，把括号都打开后有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y^{*T}b%20=%20y^{*T}Ax^*%20=%20c^Tx^*)，根据弱对偶定理得 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x^*) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y^*) 分别是原问题和对偶问题的最优解。

由 1 推出 2 也不难，根据弱对偶定理中的推导，我们有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y^{*T}b%20\ge%20y^{*T}Ax^*%20\ge%20c^Tx^*)。而 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x^*) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y^*) 分别是原问题和对偶问题的最优解，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y^{*T}b%20=%20c^Tx^*)，不等式就会全部取等，即  ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y^{*T}b%20=%20y^{*T}Ax^*%20=%20c^Tx^*)，加上括号就行了。

这个定理揭示了原始问题的最优解和对偶问题的最优解之间的关系，它们对限制条件的满足是“一紧一松”的。

#### Dual simplex method

利用强对偶定理，我们可以为单纯形法作出另一种解释。

我们知道，单纯形法的停止条件是所有检验数非正（如果是 min 问题就是所有检验数非负）。而从强对偶定理的推导中我们可以看到，所有检验数非正时，我们就能构造一个对偶问题的可行解，使得原问题和对偶问题的目标函数值相等，那么它们分别是原问题和对偶问题的最优解。也就是说，单纯形法是在保证原问题可行解的情况下，尝试构造对偶问题的可行解（这个可行解让目标函数值与原问题相同），如果构造成功，那么两个都是最优解。这种单纯形法又称为原始单纯形法。

相应地，我们可以设计对偶单纯形法：在保证对偶问题可行解（所有检验数非正，如果是 min 问题就是所有检验数非负）的情况下，尝试构造原始问题的可行解（这个可行解让目标函数值与对偶问题相同），如果构造成功，那么两个都是最优解。

下面以 min 问题为例，简要说明对偶单纯形法的计算步骤：

1.  找到一组基，使得所有检验数非负；
2.  如果单纯形表中 b 的那一列出现负数，说明当前基不可行（因为有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20\ge%200) 的限制），选择负数中 b 的绝对值最大的那一行（设为第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 行），对应的变量 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_i) 作为出基变量（要把该变量从负数调到 0）；
3.  假设第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 行中，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_j) 的系数为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_j)，检验数为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20d_j)，那么在所有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_j%20<%200) 的变量中，选择 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20d_j/a_j) 绝对值最小的那一列，对应的变量 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_k) 作为入基变量，回到 2。如果所有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_j%20\ge%200)，那么原问题无可行解；
4.  如果单纯形表中 b 的那一列均非负，说明构造出了一个原问题的可行解，算法结束。

为什么要选择 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_k%20<%200) 的变量呢？我们写出出基变量和非基变量之间的关系式 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\sum_{j \in N} a_jx_j + x_i = b_i![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 如果 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_k%20>%200)，那么为了把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_i) 从负数调到 0，又要保证等式成立，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_k) 只能从 0 变成负数，就不能入基了；相反，如果 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_k%20<%200)，那么为了让等式成立，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_k) 会从 0 变成正数，就可以入基，向原始问题的可行解靠近一步。

为什么要选择 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20d_j/a_j) 绝对值最小的变量呢？我们写出 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_k) 和其它变量的关系式，以及目标函数和检验数的关系式 ：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)x_k = \frac{b_i - x_i}{a_k} - \sum_{j \in N, j \ne k} \frac{a_j}{a_k}x_j \\ z = v + \sum_{j \in N}d_jx_j = \sum_{j \in N, j \ne k}(d_j - \frac{d_k}{a_k}a_j)x_j - \frac{d_k}{a_k}x_i + (v+ \frac{d_k}{a_k}b_i)![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 为了保持对偶问题的可行解，我们需要保证变量替换之后，检验数仍然非负，即 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)-\frac{d_k}{a_k} \ge 0 \\ d_j-\frac{d_k}{a_k}a_j \ge 0![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 第一个式子显然满足，因为原检验数 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20d_k%20\ge%200)，且 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_k%20<%200)。第二个式子在 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_j) 为正数时显然满足，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_j) 为负数时，需要 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{d_j}{a_j}%20\le%20\frac{d_k}{a_k}) 才能满足，这就是选择 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20d_j/a_j) 绝对值最小的变量的原因。

举一个例子 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix}\min\limits_{x} & 9x_1 + 5x_2 + 3x_3 \\ \text{s.t.} & 3x_1 + 2x_2 - 3x_3 \ge 3 \\ & 2x_1 + x_3 \ge 5 \\ & x \ge 0\end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 加入松弛变量后，问题转化为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix}\min\limits_{x} & 9x_1 + 5x_2 + 3x_3 \\ \text{s.t.} & 3x_1 + 2x_2 - 3x_3 - x_4 = 3 \\ & 2x_1 + x_3 - x_5 = 5 \\ & x \ge 0\end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 绘制单纯形表，第一次迭代：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{array}{c|ccccc|c} & 9 & 5 & 3 & 0 & 0 & 0 \\ \hline x_4 & -3 & -2 & 3 & 1 & 0 & -3 \\ x_5 & -2 & 0 & -1 & 0 & 1 & -5 \end{array}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 选择 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_5) 出基. 由于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%203/1%20<%209/2)，选择 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_3) 入基，第二次迭代：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{array}{c|ccccc|c} & 3 & 5 & 0 & 0 & 3 & -15 \\ \hline x_4 & -9 & -2 & 0 & 1 & 3 & -18 \\ x_3 & 2 & 0 & 1 & 0 & -1 & 5 \end{array}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 选择 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_4) 出基. 由于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%203/9%20<%205/2)，选择 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1) 入基，第三次迭代：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{array}{c|ccccc|c} & 0 & 13/3 & 0 & 1/3 & 4 & -21 \\ \hline x_1 & 1 & 2/9 & 0 & -1/9 & -1/3 & 2 \\ x_3 & 0 & -4/9 & 1 & 2/9 & -1/3 & 1 \end{array}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 此时最后一列第二、三行均非负，迭代结束。原问题的最优解为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20=%202,%20x_2%20=%200,%20x_3%20=%201)，目标函数值为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%2021)。

### Primal-dual method

#### Primal-dual method

原始对偶方法利用的就是上一节课中讲到的互补松弛定理。我们首先找到对偶问题的一个可行解 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y)，并尝试找到一个原问题的可行解 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x)，使得 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y) 满足互补松弛定理。如果我们找到了这样的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x)，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y) 就分别是原问题和对偶问题的最优解；否则我们就需要调整 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y)，让它变得更好，继续尝试，直到找到最优解为止。

##### Finding a Dual feasible solution

考虑以下线性规划问题作为原问题 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \min\limits_x & c^Tx \\ \text{s.t.} & Ax = b \ge 0 \\ & x \ge 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 它的对偶问题为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \max\limits_x & b^Ty \\ \text{s.t.} & A^Ty \le c \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 我们首先需要获得一个对偶问题的可行解。如果 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c%20\ge%200)，显然 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y%20=%200) 就是对偶问题的一个可行解，否则我们可以使用如下方法寻找可行解。

给原问题增加一个变量与一条约束 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20+%20x_2%20+%20\dots%20+%20x_n%20+%20x_{n+1}%20=%20b_{m+1})，其中 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20b_{m+1}) 需要足够大，至少要大等于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20+%20x_2%20+%20\dots%20+%20x_n) 可能的最大值。这样的约束就不会改变原问题。

加入新约束后，我们写出新的对偶问题 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \max\limits_y & b^Ty + b_{m+1}y_{m+1} \\ \text{s.t.} & A^Ty + y_{m+1}\begin{bmatrix} 1 & 1 & \dots & 1 \end{bmatrix}^T \le c \\ & y_{m+1} \le 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 我们很容易看出这个新对偶问题的可行解为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y_i%20=%200%20\quad%20\forall%20i%20\in%20\{1,%202,%20\dots,%20m\}) 以及 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y_{m+1}%20=%20\min\limits_i%20\quad%20c_i)。

##### Restricted Problem (RP) and Dual Restricted Problem (DRP)

假设我们找到了对偶问题的可行解 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y)，现在我们需要寻找一个原问题的可行解 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 满足互补松弛定理。

设 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_j) 表示矩阵 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 的第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 列，定义 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20J%20=%20\{%20j%20|%20A_j^Ty%20=%20c_j%20\})（称 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20J) 为允许指标集，简单来说 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20J) 就是以 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y) 作为对偶可行解时，对偶问题中较紧的那些限制的编号）。根据原问题的定义和互补松弛定理，我们有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)Ax = b \\ x_j = 0 \quad \forall j \not\in J \\ x_j \ge 0 \quad \forall j \in J![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 如果我们能找到一个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 满足上面三个条件，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y) 就能满足互补松弛定理。

为了获得一个可行的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x)，我们使用一个类似于两阶段法的思想（虽然两阶段法和原始对偶方法可能没啥联系- -），构造一个优化问题，称为限制的原问题（restricted primal，RP）![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \max\limits_x & \sum\limits_{i=1}^m \bar{x}_i \\ \text{s.t.} & \sum\limits_{j\in J} a_{i,j}x_j + \bar{x}_i = b_i \\ & x_j \ge 0, \bar{x}_i \ge 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 很显然，若目标函数值取 0，那么我们就找到了满足互补松弛定理的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x)。

我们再来写出 RP 的对偶问题，称为限制的对偶问题（DRP）![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \max\limits_x & b^Ty \\ \text{s.t.} & A^T_jy \le 0 & \forall j \in J \\ & y_i \le 1 & \forall i \in \{1, 2, \dots, m\} \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 设 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{y}) 为 DRP 的最优解，根据强对偶定理，若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20b^T\bar{y}%20=%200) 则 RP 的目标函数值也可以取到 0，那么当前对偶可行的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y) 就是对偶问题的最优解；否则我们有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20b^T\bar{y}%20\ge%200)，因为至少 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{y}%20=%200) 是 DRP 的可行解。

一开始要求原问题的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20b%20\ge%200) 可能是为了保证 RP 问题有可行解（如果 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20b%20\ge%200) 那么 RP 问题至少有可行解 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20=%200) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{x}%20=%20b)）。不过这可能也不是很有必要，如果发现 RP 问题无可行解，或者 DRP 问题无有限最优解，那就说明了原问题无可行解。

##### Improve Dual feasible solution

如果 DRP 的最优解让 DRP 的目标函数值超过 0，说明当前的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y) 还不是最优的。我们来想办法用 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{y}) 改进 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y)。我们让新的对偶可行解 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\hat{y}%20=%20y%20+%20\theta\bar{y})（其中 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\theta%20\ge%200)），显然有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20b^T\hat{y}%20=%20b^Ty%20+%20\theta%20b^T\bar{y}%20>%20b^Ty)，说明对偶问题的目标函数值的确改进了。但别忘了，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\hat{y}) 仍然需要是对偶可行的，也就是说，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A^T\hat{y}%20=%20A^Ty%20+%20\theta%20A^T\hat{y}%20\le%20c) 仍要满足。

我们来考虑 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\theta) 的取值范围。对于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j%20\in%20J)，因为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A^T_j\bar{y}%20\le%200)，无论 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\theta) 取多大，都不会超过 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c) 的限制，所以这些项不会限制 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\theta) 的取值；对于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j%20\not\in%20J)，我们选择 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\theta = \min_{j \not\in J, A^T_j\bar{y} > 0} \quad \frac{c_j - A^T_jy}{A^T_j\bar{y}}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 这样就会让 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j%20\not\in%20J) 中的一条限制变紧，其它限制则不会超过，仍然是对偶可行的。当然啦，如果 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\theta) 可以无限增大，说明对偶问题没有有限最优解，那么原问题无可行解。

将 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y) 调整为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\hat{y}) 之后，就进入下一轮迭代继续调整（当然我们不需要再从原问题开始，慢慢写出 RP 和 DRP 了，直接确定新的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20J) 和新的 DRP 即可），直到 DRP 的最优解让目标函数值为 0，此时的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y) 就是对偶问题的最优解。

##### Time complexity

事实上，原始对偶问题就是通过枚举 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20J) 来获得对偶问题的最优解。由于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20J) 至多有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%202^n) 个，所以这个方法是一定会终止的。当然，这个方法的最差复杂度也是指数级的。如果限制条件在进入 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20J) 后不会出来，那么算法就能在线性步数内结束。

这个方法看起来比单纯形法麻烦多了。单纯形法只要解一个优化问题就能得到最优解，这个方法一下子变出来四个优化问题。但是这个方法对特定问题是非常有效的，对于一些特定问题来说，我们可以一下子看出（或者在很短的时间内方便地算出）DRP 的最优解。下面就来举例说明原始对偶方法的应用。

#### Application: Shortest-path problem

##### Linear programming

我们来考虑有向图上的最短路问题，起点为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20s)，终点为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20t)。对有向图定义点 - 弧关联矩阵，这个矩阵中每列对应一条边，每行对应一个顶点。若一条边是一个顶点的出边，那么矩阵对应元素为 1；若一条边是一个顶点的入边，那么矩阵对应元素为 -1。设 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w_i) 表示第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 条边的长度，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_i) 表示第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 条边是否在最短路上，那么最短路问题就是解如下线性规划问题 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \min\limits_x & w^Tx \\ \text{s.t.} & Ax = v \\ & x \ge 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 其中 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)v_i = \begin{cases} 1 & i = s \\ -1 & i = t \\ 0 & \text{otherwise} \end{cases}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 虽然这个问题是一个线性规划问题，但是最优解中每个变量的值不是 0 就是 1（最短路问题中不会有半条边在最短路上吧- -）。最优解中每个变量的取值范围在 0~1 之间还好理解（如果有一个变量大于 1，就必须有变量取负值，这样不满足 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20\ge%200) 的条件），为什么每个变量的取值还是整数呢？

我们使用单纯形法求解时，得到的解是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_B%20=%20A_B^{-1}b)。如果 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_B^{-1}) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20b) 的元素都是整数，得到的解自然是整数。我们引入全幺模矩阵（total unimodular matrix）的定义：一个整数矩阵 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 称为全幺模矩阵，如果 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 的任何一个子方阵的行列式取值为 0，1 或 -1。如果我们能证明有向图的点 - 弧关联矩阵是全幺模矩阵，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_B) 的行列式取值就为 0，1 或 -1。由于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_B^{-1}%20=%20A_B^*%20/%20|A_B|)，而由于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_B) 的元素均为整数，伴随矩阵 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_B^*) 的元素也为整数，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A_B^{-1}) 的元素自然也都是整数了。

 

以下对方阵的边长 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 使用数学归纳法，证明任意一个有向图的点 - 弧关联矩阵的子方阵行列式取值为 0，1 或 -1。

**起始步骤：**对于任意有向图 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n%20=%201) 的子方阵，根据点 - 弧关联矩阵的定义，子方阵的行列式取值为 0，1 或 -1。

**推递步骤：**假设对于任意有向图 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n%20\le%20k) 的子方阵，都有行列式取值为 0，1 或 -1。

对于任意有向图 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n%20=%20k%20+%201) 的子方阵，根据点 - 弧关联矩阵的定义，每一列至多有两个非 0 元素，且这些元素中至多一个为 1，至多一个为 -1。

如果该子方阵存在一列没有非 0 元素，那么该子方阵的行列式取值为 0；

如果该子方阵存在一列只有一个非 0 元素，由于该元素为 1 或 -1，那么该子方阵行列式的绝对值等于该元素余子式的绝对值。将原有向图去掉该元素对应的点和边后，这个余子阵可以看作是新有向图的子方阵. 根据归纳法假设，该元素余子式的绝对值为 0 或 1，那么该子方阵的行列式取值为 0，1 或 -1；

如果该子方阵的每一列都有两个非 0 元素，那么根据点 - 弧关联矩阵的定义，对该子方阵的每一行求和，将会得到一个元素都是 0 的行向量，所以该子方阵的行列式取值为 0。

综上所述，对于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n%20=%20k%20+%201) 的子方阵，其行列式的取值仍为 0，1 或 -1。

根据上述数学归纳法，有向图的点 - 弧关联矩阵是全幺模矩阵。

##### Dual problem and Dual Restricted Problem of Shortest-path problem

根据点 - 弧关联矩阵的定义很容易发现，把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 的每一行加起来，最后会获得都是 0 的一行，也就是说 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 中的行向量是线性相关的。那么不妨从 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 中去掉代表终点 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20t) 的那一行，得到新矩阵 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{A})。这样，最短路问题就变为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \min\limits_x & w^Tx \\ \text{s.t.} & \bar{A}x = v \\ & x \ge 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 其中 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)v_i = \begin{cases} 1 & i = s \\ 0 & \text{otherwise} \end{cases}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 我们写出这个问题的对偶问题 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \max\limits_{\pi} & \pi_s \\ \text{s.t.} & \pi_i - \pi_j \le w_e & \forall e = (i, j) \in E \\ & \pi_t = 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 其中 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(i,%20j)) 代表一条从 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 连到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 的边，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E) 是有向图的边集。这个对偶问题的可行解很容易得到，只要令![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\pi%20=%200) 即可。另外，虽然 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{A}) 矩阵比 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 矩阵少了代表 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20t) 的那一行，但是只要我们定义 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\pi_t%20=%200)，就又能把对偶问题写成上面的形式了。这个形式就是差分约束系统，以前做算法竞赛的时候一直不能理解为什么差分约束求最大值反而要跑一个最短路，现在终于明白了，原来差分约束是最短路问题的对偶问题...

我们再来写出最短路问题的 DRP ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \max\limits_{\pi} & \pi_s \\ \text{s.t.} & \pi_i - \pi_j \le 0 & \forall (i, j) \in J \\ & \pi_i \le 1 \\ & \pi_t = 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 这个 DRP 问题的解是非常容易看出的。如果从点 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20s) 到某个点 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20p) 的最短路已经算出来了，而边 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 就在这条最短路上，根据最短路的三角不等式，这条边一定在 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 中。我们把所有已知最短路的点构成的连通块称为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20C)，为了让 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\pi_s) 的取值最大并满足 DRP 的限制条件，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20C) 中所有点的变量值都必须和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\pi_s) 相同。显然，若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20t%20\not\in%20C)，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\pi_s%20=%201)；若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20t%20\in%20C)，那么由于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\pi_t%20=%200) 的条件，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\pi_s%20=%200)，说明我们找到了从 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20s) 到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20t) 的最短路。

我们用一张有向图来模拟一下最短路的原始对偶算法。

 ![最短路例图](https://images.cnblogs.com/cnblogs_com/tsreaper/1112059/o_aop5.graph.png)

![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{array}{c|cccccc} \text{iter}. & \pi_s & \pi_{v2} & \pi_{v3} & \pi_{v4} & \pi_{v5} & \pi_t \\ \hline 0 & 0 & 0 & 0 & 0 & 0 & 0 \\ 1 & 1 & 0 & 0 & 0 & 0 & 0 \\ 2 & 2 & 0 & 1 & 0 & 0 & 0 \\ 3 & 4 & 2 & 3 & 0 & 2 & 0 \\ 4 & 6 & 5 & 4 & 2 & 4 & 0 \end{array}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 其实这就是我们熟悉的 Dijkstra 算法的过程。

## Combinatorial Optimization

### Linear integer programming, Cutting plane method, and Branch and bound

#### Linear integer programming

先从最简单的线性整数规划开始。线性整数规划其实就是线性规划加上解必须为整数的限制，其基本形式为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \max\limits_x & c^Tx \\ \text{s.t.} & Ax \le b \\ & x \in \mathbb{N} \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 我们之前见过的很多算法问题都能写成线性整数规划的形式，特别是能写成整数规划的一种特殊形式：0-1 规划。

##### 0-1 Knapsack problem

设共有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 件物品，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20v_i) 表示第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 件物品的价值，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w_i) 表示第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 件物品的重量，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c) 表示背包的最大承重，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_i%20\in%20\{0,%201\}) 表示是否选择第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 件物品。那么 0-1 背包问题可以写为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \max\limits_x & \sum\limits_{i=1}^n v_ix_i \\ \text{s.t.} & \sum\limits_{i=1}^n w_ix_i \le c \\ & x_i \in \{0, 1\} \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)

##### Minimum Spanning Tree

设共有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 个点，点集为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20V)，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(i,%20j)%20\in%20E) 表示从第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 个点连到第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 个点的一条有向边（一条无向边就相当于两条有向边），![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w_{i,%20j}) 表示边权，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_{i,%20j}%20\in%20\{0,%201\}) 表示这一条边是否在最小生成树内。那么最小生成树问题可以写为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \min\limits_x & \sum\limits_{(i, j) \in E} w_{i, j}x_{i, j} \\ \text{s.t.} & \sum\limits_{(i, j) \in E} x_{i, j} = n-1 \\ & \sum\limits_{i \in S, j \not\in S} x_{i, j} \ge 1 & \forall S \;\unicode{x2acb}\; V \\ & x_{i, j} \in \{0, 1\} \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 第一项限制保证了生成树中有且仅有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n-1) 条边，第二项限制保证了生成树的连通性。因为树是无向图，所以每条边都会被算两次，最后答案除以 2 即可。

虽然这个表述使用了指数级的限制，但我们知道，最小生成树是有多项式算法的。也可以用椭球法在多项式时间内解最小生成树问题。

##### Bin packing problem

设共有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 个物品，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w_i) 表示第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 个物品的重量，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c) 表示每个箱子的承重，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_{i,%20j}%20\in%20\{0,%201\}) 表示是否将第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 个物品放入第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 个箱子，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y_i) 表示是否使用第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 个箱子。那么装箱问题可以写为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \min\limits_{x, y} & \sum\limits_{i=1}^n y_i \\ \text{s.t.} & \sum\limits_{i=1}^n w_ix_{i, j} \le cy_j & \forall j \in \{1, 2, \dots, n\} \\ & \sum\limits_{j=1}^n x_{i, j} = 1 & \forall i \in \{1, 2, \dots, n\} \\ & x_{i, j} \in \{0, 1\} \\ & y_{i, j} \in \{0, 1\} \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 第一项限制保证了每个箱子装的物品不会超过承重，第二项限制保证了每个物品一定会被装入箱子，且每个物品只装入一个箱子。

##### Matching problem

设图的点集为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20V)，边集为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E)。设 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(i,%20j)%20\in%20E) 表示从第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 个点连到第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 个点的一条有向边，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_{i,%20j}) 表示这条边是否为匹配边。那么一般无向图的最大匹配问题可以写为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \max\limits_x & \sum\limits_{(i, j) \in E} x_{i, j} \\ \text{s.t.} & \sum\limits_{(i, j) \in E} x_{i, j} \le 1 & \forall i \in V \\ & \sum\limits_{(i, j) \in E} x_{i, j} \le 1 & \forall j \in V \\ & x_{i, j} \in \{0, 1\} \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 我们也可以用图的点 - 边关联矩阵来描述匹配问题。设图中有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 个顶点，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20m) 条边，那么图的点 - 边关联矩阵是一个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n%20\times%20m) 的矩阵。该矩阵每列对应一条边，每行对应一个顶点。若第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 个顶点是第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 条边的端点，那么矩阵第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 行第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 列为 1，否则为 0（可以看出，这个矩阵描绘的是无向边）。

用图的点 - 边关联矩阵将一般无向图的最大匹配问题写为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \max\limits_{(i, j) \in E} & x_{i, j} \\ \text{s.t.} & Ax \le b \\ & x_{i, j} \in \{0, 1\} \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 其中 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 为图的点 - 边关联矩阵，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y) 是一个全为 1 的向量。

 

匹配问题中，二分图的最大匹配最为特殊。如果把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_{i,%20j}%20\in%20\{0,%201\}) 这项条件改成 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20\ge%200)，用线性规划求解二分图的最大匹配问题，最优解仍然非 0 即 1。和[上一节课](http://www.cnblogs.com/tsreaper/p/aop5.html)讲解的最短路问题一样，这也是因为二分图的点 - 边关联矩阵是全幺模矩阵。

以下对方阵的边长 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 使用数学归纳法，证明任意一个无向二分图的点 - 边关联矩阵的子方阵行列式取值为 0，1 或 -1。

**起始步骤**：对于任意二分图 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n%20=%201) 的子方阵，根据点 - 边关联矩阵的定义，子方阵的行列式取值为 0 或 1。

**推递步骤**：假设对于任意二分图 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n%20\le%20k) 的子方阵，都有行列式取值为 0，1 或 -1。

对于任意二分图 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n%20=%20k%20+%201) 的子方阵，根据点 - 边关联矩阵的定义，每一列至多有两个非 0 元素，且这些元素均为 1。

如果该子方阵存在一列没有非 0 元素，那么该子方阵的行列式取值为 0；

如果该子方阵存在一列只有一个非 0 元素，由于该元素为 1，那么该子方阵行列式的绝对值等于该元素余子式的绝对值。将原二分图去掉该元素对应的点和边后，这个余子阵可以看作是新二分图的子方阵（因为二分图的子图仍然是二分图）。根据归纳法假设，该元素余子式的绝对值为 0 或 1，那么该子方阵的行列式取值为 0，1 或 -1。

如果该子方阵的每一列都有两个非 0 元素，设二分图可以被分为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B) 两个集合，根据点 - 边关联矩阵的定义与二分图的定义，将集合 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 中的点对应的行相加，再减去集合 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B) 中的点对应的行，将会得到一个元素都是 0 的行向量，所以该子方阵的行列式取值为 0。

综上所述，对于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n%20=%20k%20+%201) 的子方阵，其行列式的取值仍为 0，1 或 -1。

根据上述数学归纳法，无向二分图的点 - 边关联矩阵是全幺模矩阵。

 

将二分图的最大匹配问题放松成线性规划后，写出它的对偶问题 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \min\limits_y & \sum\limits_{i=1}^n y_i \\ \text{s.t.} & y_i + y_j \ge 1 & (i, j) \in E \\ & y \ge 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 由于全幺模矩阵的转置也是全幺模矩阵，所以这个问题也可以加上 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y%20\in%20\{0,%201\}) 的限制而答案不变。

如果我们把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20y_i) 看作是否选择第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 个点，这就是二分图的最小覆盖问题。这就是二分图的最大匹配和最小覆盖可以互相转化的原因。而一般图的最大匹配问题将 0-1 限制放松后最优解会改变，所以无法这样转化。

#### Gomory cutting-plane method

接下来介绍两种解线性整数规划问题的方法，首先介绍 Gomory 割平面法。

Gomory 割平面法的思想就是一直去除非整数的最优解，直到某一次求得的最优解为整数。考虑一个线性规划问题，假设我们使用单纯形表求解后获得的不是整数解，我们选择一个非整数的变量 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_i)，根据单纯形表有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)x_i + \sum\limits_{j=m+1}^n \bar{a_{i,j}}x_j = \bar{b_i} \qquad \qquad \text{①} ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 既然 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_i) 不是整数，说明 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{b_i}) 一定不是整数，当然 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\bar{a_{i,j}}) 也可能不是整数。

将式 ① 调整一下，变为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)x_i + \sum\limits_{j=m+1}^n \left\lfloor \bar{a_{i,j}} \right\rfloor x_j \le \bar{b_i} \qquad \qquad \text{②} ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 显然，式 ① 的解一定是式 ② 的解。

再次调整式 ②，变为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)x_i + \sum\limits_{j=m+1}^n \left\lfloor \bar{a_{i,j}} \right\rfloor x_j \le \left\lfloor\bar{b_i}\right\rfloor \qquad \qquad \text{③}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 容易看出，式 ② 的整数解一定符合式 ③，而原来用单纯形表求出的非整数解就不符合式 ③ 了（因为原来求出的非整数解中，有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_i%20=%20\bar{b_i}%20>%20\left\lfloor%20\bar{b_i%20}%20\right\rfloor) 以及 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_j%20=%200)）。我们只要把式 ③ 加入原来的线性规划问题，重新求解多出一个限制的线性规划问题。如果求出来的是整数解就停止，否则继续加入限制并求解，直到获得整数解为止。

顺便一提，大部分参考资料不会直接加入式 ③，而是加入 ① - ③，即 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\sum\limits_{j=m+1}^n(\bar{a_{i,j}} - \left\lfloor \bar{a_{i,j}} \right\rfloor) x_j \ge \bar{b_i} - \left\lfloor \bar{b_i} \right\rfloor![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 当然效果是一样的。

 

来举个例子，考虑以下线性整数规划问题 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \max\limits_x & 3x_1 + 2x_2 \\ \text{s.t.} & 2x_1 + 3x_2 + x_3 = 14 \\ & 2x_1 + x_2 + x_4 = 9 \\ & x \ge 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 用单纯形表解该问题，结果为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{array}{c|cccc|c} & 0 & 0 & -1/4 & -5/4 & -59/4 \\ \hline x_2 & 0 & 1 & 1/2 & -1/2 & 5/2 \\ x_1 & 1 & 0 & -1/4 & 3/4 & 13/4 \end{array}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 选择 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2)，加入限制：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2%20-%20x_4%20\le%202)，即 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2%20-%20x_4%20+%20x_5%20=%202)。用单纯形表求解加入限制后的问题，结果为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{array}{c|ccccc|c} & 0 & 0 & 0 & -1 & -1/2 & -29/2 \\ \hline x_3 & 0 & 0 & 1 & 1 & -2 & 1 \\ x_1 & 1 & 0 & 0 & 1 & -1/2 & 7/2 \\ x_2 & 0 & 1 & 0 & -1 & 1 & 2 \end{array}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 选择 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1)，加入限制：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20+%20x_4%20-%20x_5%20\le%203)，即 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20+%20x_4%20-%20x_5%20+%20x_6%20=%203). 用单纯形表求解加入限制后的问题，结果为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{array}{c|cccccc|c} & 0 & 0 & 0 & -1 & 0 & -1 & -14 \\ \hline x_3 & 0 & 0 & 1 & 1 & 0 & -4 & 3 \\ x_1 & 1 & 0 & 0 & 1 & 0 & -1 & 4 \\ x_5 & 0 & 0 & 0 & 0 & 1 & -2 & 1 \\ x_2 & 0 & 1 & 0 & -1 & 0 & 2 & 1 \end{array}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 所以原问题的最优解为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20=%204,%20x_2%20=%201)，目标函数值为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%2014)。

#### Branch and bound

（其实我觉得应该写作分支定界法，不过上课的老师坚持认为是分枝- -）

分枝定界法的思想和最优性剪枝或者 min-max 搜索树什么的差不多。我们先将原问题放松成线性规划问题，解这个线性规划，就得到了整数规划最优解的上界。假设最优解中 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20N%20<%20x_i%20<%20N+1) 不是整数，就会有两种可能：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_i%20\le%20N) 或 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_i%20\ge%20N+1)，对两种情况分别进行搜索。如果在某一枝内算出了一个整数解，我们就得到了原整数规划最优解的下界；如果另一枝内线性规划问题的解还没有这个下界来得优，那么那一枝就可以直接不考虑了（因为线性规划问题的解是那一枝能找到的最优解的上界）。总而言之就是带着最优性剪枝的暴搜。

 

用一张 youtube 视频里的图作为例子

![分枝定界法](https://images.cnblogs.com/cnblogs_com/tsreaper/1112059/o_aop6.branch-and-bound.png)

对于放松后的线性规划问题，最优解为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20=%208,%20x_2%20=%202.25)，目标函数值为 35.25；

首先考虑 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2%20\le%202)，也就是 node1A，算得该情况下最优解为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20=%208,%20x_2%20=%202)，目标函数值为 34。这是一个整数解，记录并回溯；

考虑 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2%20\ge%203)，也就是 node1B，算得该情况下的最优解为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20=%206.5,%20x_2%20=%203)，目标函数值为 34.5。它还优于我们已知的下界 34，继续搜索；

考虑 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20\le%206)，也就是 node2C，算得该情况下的最优解为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20=%206,%20x_2%20=%203.25)，目标函数值为 34.25。它还优于我们已知的下界 34，继续搜索；

考虑 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2%20\le%203)，也就是 node3E，算得该情况下的最优解为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20=%206,%20x_2%20=%203)，目标函数值为 33。它劣于我们已知的下界 34，回溯；

考虑 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2%20\ge%204)，也就是 node3F，算得该情况下的目标函数值为 33.5。它劣于我们已知的下界 34，回溯；

考虑 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20\ge%207)，也就是 node2D，该情况下无可行解，回溯；

搜索得最优解为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20=%208,%20x_2%20=%202)，目标函数值为 34。

（事实上我觉得这个例子不太好，其实在 node1B就可以直接回溯了。因为 node1B 那一枝的上界是 34.5，那么最优整数解最多只有 34 了。）

 

再试一试 Gomory 单纯形法的那个例子。将原问题松弛为线性规划问题后，得到的最优解为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2%20=%205/2,%20x_1%20=%2013/4)，目标函数值为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%2059/4)。

先探索 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_2%20\le%202) 的情况，用单纯形表求解得 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{array}{c|ccccc|c} & 0 & 0 & 0 & -1 & -1/2 & -29/2 \\ \hline x_3 & 0 & 0 & 1 & 1 & -2 & 1 \\ x_1 & 1 & 0 & 0 & 1 & -1/2 & 7/2 \\ x_2 & 0 & 1 & 0 & -1 & 1 & 2 \end{array}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 探索 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20\le%203) 的情况，用单纯形表求解得 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{array}{c|cccccc|c} & 0 & 0 & 0 & 0 & -2 & -3 & -13 \\ \hline x_3 & 0 & 0 & 1 & 0 & 0 & -2 & 2 \\ x_4 & 0 & 0 & 0 & 1 & 0 & -2 & 1 \\ x_2 & 0 & 1 & 0 & 0 & 1 & 0 & 2 \\ x_1 & 1 & 0 & 0 & 0 & 0 & 1 & 3 \end{array}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 得到候选的解 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20=%203,%20x_2%20=%202)，目标函数值为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%2013)。

接下来探索 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20\ge%204)，用单纯形表解得 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{array}{c|ccccc|c} & 0 & 0 & 0 & -2 & -1 & -14 \\ \hline x_1 & 1 & 0 & 0 & 0 & -1 & 4 \\ x_3 & 0 & 0 & 1 & -2 & -4 & 3 \\ x_2 & 0 & 1 & 0 & 1 & 2 & 1 \\ x_5 & 0 & 0 & 0 & 0 & 1 & 1 \end{array}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 得到候选的解 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20=%204,%20x_2%20=%201)，目标函数值为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%2014)。

注意到原问题目标函数值的上界为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%2059/4)，而 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%2014%20<%2059/4%20<%2015)，所以目标函数值的整数上界为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%2014)，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20=%204,%20x_2%20=%201) 必然为整数最优解. 所以原问题的最优解为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_1%20=%204,%20x_2%20=%201)，目标函数值为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%2014)。

### Greedy solution for 1-class problem

#### Independent system

考虑一个有限元素集合 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E)，给 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E) 中的每个元素 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20e) 定义一个非负的费用 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c(e))。再考虑 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\mathcal{F}%20\in%202^E)，那么对于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F%20\in%20\mathcal{F})，我们定义 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F) 的费用 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c(F)%20=%20\sum\limits_{e%20\in%20F}%20c(e))。现在我们要找出一个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F)，使得 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c(F)) 最大（或最小）。这就是这节课我们需要考虑的一类问题。

##### Independent system

从这类问题中，我们引入独立系统的概念。对于一个二元组 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(E,%20\mathcal{F}))，若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\forall%20Y%20\in%20\mathcal{F})，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20X%20\subseteq%20Y%20\to%20X%20\in%20\mathcal{F})，那么我们称 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(E,%20\mathcal{F})) 为独立系统。由这个定义我们马上推出，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\emptyset%20\in%20\mathcal{F})。

##### Independent set and dependent set

在独立系统 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(E,%20\mathcal{F})) 中，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\mathcal{F}) 中的元素称为独立集，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E%20-%20\mathcal{F}) 中的元素称为相关集。

##### 基与圈

我们将 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\mathcal{F}) 中的极大独立集称为基，将 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E%20-%20\mathcal{F}) 中的极小相关集称为圈。

对于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20X%20\subseteq%20E)，定义 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20X) 上的基为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20X) 中的极大独立集。

##### 秩商

对于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20X%20\subseteq%20E)，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20X) 中的基大小可能不同。我们定义 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20X) 的秩 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20r(X)) 为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20X) 中最大的基的大小，类似地定义 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20X) 的下秩 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\rho(X)) 为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20X) 中最小的基的大小。

由此定义独立系统的秩商 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20q(E,%20\mathcal{F})%20=%20\min\limits_{x%20\subseteq%20E}%20\quad%20\frac{\rho(X)}{r(X)})。秩商是一类问题中贪心解法近似比的下界，下面会进行说明。

#### 1-class maximization (minimization) problem

根据独立系统的定义，我们引出一类最大（小）化问题。

**最大化问题**：给出一个独立系统 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(E,%20\mathcal{F}))，找出一个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F%20\in%20\mathcal{F})，使得 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c(F)) 最大。

很显然，由于每个元素的费用都是非负的，所以 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20|F|) 越大，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c(F)) 也越大。所以最优的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F) 一定是基。

**最小化问题**：给出一个独立系统 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(E,%20\mathcal{F}))，找出一个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F%20\in%20\mathcal{F})，使得 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F) 是基，且 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c(F)) 最小。

（如果不要求 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F) 是基，那么取 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F%20=%20\emptyset) 就会让代价最小，没什么意义...）

 

最大化问题的实例有很多。

0-1 背包问题：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E) 中的元素是每个物品，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\mathcal{F}) 中的元素是所有可以放进背包的物品集合，费用就是物品的价值。

最大权独立集：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E) 中的元素是点，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\mathcal{F}) 中的元素是独立集，费用就是每个点的权值。

最长简单路径：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E) 中的元素是边，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\mathcal{F}) 中的元素是所有从起点到终点的简单路径以及其子集，费用就是每条边的距离。

最大权森林：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E) 中的元素是边，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\mathcal{F}) 中的元素是所有不含圈的边集，费用就是每条边的权值。

 

最小化问题也有很多实例。

最小生成树：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E) 中的元素是边，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\mathcal{F}) 中的元素是所有不含圈的边集，费用就是每条边的权值。

最短路：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E) 中的元素是边，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\mathcal{F}) 中的元素是所有从起点到终点的简单路径以及其子集，费用就是每条边的距离。

旅行商问题（TSP）：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E) 中的元素是边，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\mathcal{F}) 中的元素是哈密尔顿回路及其子集，费用就是每条边的距离。

#### Matroid

拟阵（matroid）是一个特殊的独立系统。一个独立系统需要满足以下三个条件中的一个才被称为是拟阵（事实上以下三个条件等价）：

(1) 若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20X,%20Y%20\in%20\mathcal{F})，且 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20|X|%20>%20|Y|)，则 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\exists%20e%20\in%20X%20-%20Y)，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20Y%20\cup%20\{e\}%20\in%20\mathcal{F})；

(2) 若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20X,%20Y%20\in%20\mathcal{F})，且 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20|X|%20=%20|Y|%20+%201)，则 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\exists%20e%20\in%20X%20-%20Y)，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20Y%20\cup%20\{e\}%20\in%20\mathcal{F})；
(3) ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\forall%20X%20\subseteq%20E)，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20X) 的所有基大小相同。

 

接下来说明这三个条件等价。

(1) 推出 (2) 是显然的，(2) 推出 (1) 使用归纳法即可。

(1) → (3)：假设存在 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20X,%20Y%20\in%20\mathcal{F})，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20X) 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20Y) 都是基，且 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20|X|%20>%20|Y|)。那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\exists%20e%20\in%20X%20-%20Y)，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20Y%20\cup%20\{e\}%20\in%20\mathcal{F})，说明 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20Y) 不是基。矛盾。
(3) → (1)：假设存在 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20X,%20Y%20\in%20\mathcal{F})，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20|X|%20>%20|Y|)，且 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\forall%20e%20\in%20X%20-%20Y)，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20Y%20\cup%20\{e\}%20\not\in%20\mathcal{F})，那么说明 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20Y) 是基。由于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20X) 是独立集，存在一个基 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20Z) 使得 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20|Z|%20\ge%20|X|%20>%20|Y|)，那么有两个基 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20Y) 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20Z) 大小不同。矛盾。

 

我们另外定义 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\mathcal{F}^*%20=%20\{F%20\subseteq%20E%20\quad%20|%20\quad%20\exists%20(E,%20\mathcal{F})%20\text{%20的基%20}%20B,%20F%20\cap%20B%20=%20\emptyset\})。

很容易发现，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(E,%20\mathcal{F}^*)) 也是独立系统。我们称 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(E,%20\mathcal{F})) 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(E,%20\mathcal{F}^*)) 互为对偶。

 

下面证明 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F%20\in%20\mathcal{F}^{**}%20\to%20F%20\in%20\mathcal{F})：

首先，由 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F%20\in%20\mathcal{F}^{**}) 可以推出 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\exists%20(E,%20\mathcal{F^*})%20\text{%20的基%20}%20B_1,%20F%20\cap%20B_1%20=%20\emptyset)。

又可以推出 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\exists%20(E,%20\mathcal{F})%20\text{%20的基%20}%20B_2,%20B_1%20\cap%20B_2%20=%20\emptyset)。

注意到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B_1%20\cup%20B_2%20=%20E)，否则我们可以从 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E%20-%20(B_1%20\cup%20B_2)) 中选出一个元素加入 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B_1)，仍有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B_1%20\cap%20B_2%20=%20\emptyset)，那 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B_1) 就不是基了。

既然 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B_1%20\cup%20B_2%20=%20E)，且 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F%20\cap%20B_1%20=%20\emptyset)，那么只能有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F%20\subseteq%20B_2)。根据独立系统的定义，有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F%20\in%20\mathcal{F})。

反过来也是成立的，证明类似就略去。

#### 2-class greedy algorithm

下面介绍两类贪心算法，分别用于独立系统的最大化和最小化问题。

**Best in**：将 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E) 中所有元素按费用从大到小排序，使得 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c(e_1)%20\ge%20c(e_2)%20\ge%20...%20\ge%20c(e_n))。一开始令 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F%20=%20\emptyset)，按 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20e_1,%20e_2%20\dots,%20e_n) 的顺序考虑，若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20e_i) 加入 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F) 后 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F) 仍是独立集那就加入。这个贪心算法用于解决最大化问题。

**Worst out**：将 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E) 中所有元素按费用从大到小排序，使得 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c(e_1)%20\ge%20c(e_2)%20\ge%20...%20\ge%20c(e_n))。一开始令 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F%20=%20E)，按 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20e_1,%20e_2%20\dots,%20e_n) 的顺序考虑，若把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20e_i) 从 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F) 中去掉后 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20F) 还含有至少一个基那就去掉。这个贪心算法用于解决最小化问题。

 

接下来介绍重要的 Best in 定理：设 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20G(E,%20\mathcal{F})) 表示 best in 贪心得到的解，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\text{OPT}(E,%20\mathcal{F})) 表示最优解，则 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)q(E, \mathcal{F}) \le \frac{G(E, \mathcal{F})}{\text{OPT}(E, \mathcal{F})} \le 1![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 从这个定理可以看出，如果一个独立系统是拟阵，那么用 best in 得到的最大化问题的解一定是最优解。

 

下面证明 Best in 定理：

首先定义 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E_j%20=%20\{e_1,%20e_2,%20\dots,%20e_n\})，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20G_n) 是 best in 贪心选中元素的集合，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20O_n) 是最优解选中元素的集合。令 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20G_j%20=%20E_j%20\cap%20G_n) 表示 best in 贪心在考虑 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20e_j) 之后选择了哪些元素，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20O_j%20=%20E_j%20\cap%20O_n) 表示最优解在考虑 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20e_j) 之后选择了哪些元素。记 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20d_j%20=%20c(e_j)%20-%20c(e_{j+1})) 以及 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20d_n%20=%20c(e_n))，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} c(G_n) & = & \sum\limits_{j=1}^n(|G_j| - |G_{j-1}|)c(e_j) \\ & = & \sum\limits_{j=1}^n|G_j|d_j \\ & \ge & \sum_{j=1}^n \rho(E_j)d_j & \text{（因为容易证明 } G_j \text{ 是 } E_j \text{ 的一个极大独立集）} \\ & \ge & q(E, \mathcal{F})\sum\limits_{j=1}^n r(E_j)d_j & \text{（根据秩商的定义）} \\ & \ge & q(E, \mathcal{F})\sum\limits_{j=1}^n |O_j|d_j \\ & = & q(E, \mathcal{F})c(O_n) \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 这就证明了 Best in 定理。

可以举一个例子说明 Best in 定理的下界是紧的：根据秩商的定义，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\exists%20X%20\subset%20E)，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20X) 的基 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B_1) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B_2) 满足 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{|B_1|}{|B_2|}%20=%20q(E,%20\mathcal{F}))。我们定义 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)c(e) = \begin{cases} 1 & e \in X \\ 0 & e \not\in X \end{cases}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 然后把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B_1) 中的元素排在前面形成 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20e_1,%20e_2,%20\dots,%20e_{|B_1|})，后面随便排。如果使用 best in 贪心，就会把前面 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20|B_1|) 个元素选走，然而最优解可以选 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20|B_2|) 个元素。

 

另外还有两个奇怪的定理，上课提了一下...

Worst out 定理：使用 worst out 贪心得到的解满足 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)1 \le \frac{G(E, \mathcal{F})}{\text{OPT}(E, \mathcal{F})} \le \max\limits_{F \subseteq E} \quad \frac{|F| - \rho^*(F)}{|F| - r^*(F)}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 其中 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\rho^*(F)) 表示对偶独立系统中的下秩，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20r^*(F)) 表示对偶独立系统中的秩。

![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 个拟阵的交：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 个拟阵的交，用贪心得到的解近似比为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{1}{n})。

### Approximation - 1

#### Vertex Cover

来看一些 vertex cover 的近似算法。

##### Approximation algorithm 1

**算法描述**：将度数最大的点 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20u) 选入答案集合，并将 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20u) 与端点包含 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20u) 的边都删去。重复这个过程，直到所有边都被删去为止。

这是一个思路非常自然的贪心算法，但是它的近似比非常差。我们来看下面这张图：

![vertex cover 例图](https://images.cnblogs.com/cnblogs_com/tsreaper/1112059/o_aop8.vertex-cover-example.png)

设第一列共有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 个点，那么这张图一共有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n%20+%20n(1%20+%20\frac{1}{2}%20+%20\frac{1}{3}%20+%20\dots%20+%20\frac{1}{n})%20=%20n%20+%20n\ln%20n) 个点。

显然，只要将第一列的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 个点加入答案集合中，就能获得最小的 vertex cover。虽然第一列的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 个点度数均为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n)，可是最后一列的点度数也为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n)。如果我们按照上述的贪心算法选择了最后一列的点，第一列的点度数就会减小至 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n-1)。可是倒数第二列的点度数也为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n-1)，如果我们选择了倒数第二列的点，那么... 这样下去，我们会把从第二列到最后一列的所有点都选入答案集合，才能获得一个 vertex cover。所以，近似算法 1 的近似比至少为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{n\ln%20n}{n}%20=%20\ln%20n)，是一个比较差的算法。

##### Approximation algorithm 2

**算法描述**：随机选择图中的一条边 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(u,%20v))，将 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20u) 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20v) 都加入答案集合，并删去 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20u)、![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20v) 以及所有端点包含 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20u) 或 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20v) 的边。重复这个过程，直到所有边都被删去为止。

这是一个听起来很不自然的算法- -然而该算法的近似比为 2：假设该算法选中了 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 条边，那么这 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 条边是原图中的一个匹配（因为这 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 条边没有相同的端点）。为了覆盖这 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 条边形成的匹配，每条边至少要有一个端点被选中。也就是说，最优解至少为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k/2)，那么近似比为 2。

##### Approximation algorithm 3

近似算法 2 对于无权的 vertex cover 问题近似比为 2，而带权的 vertex cover 问题需要使用下面这个算法。

设共有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 个点。用 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_i) 表示第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 个点是否在答案集合中，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w_i) 表示第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 个点的权重。用 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E) 表示边集，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(u,%20v)) 表示连接点 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20u) 与点 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20v) 的一条边。写出 vertex cover 要优化的模型。![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \min\limits_x & \sum\limits_{i=1}^n w_ix_i \\ \text{s.t.} & x_i + x_j \ge 1 & \forall (i, j) \in E \\ & x \in \{0, 1\} \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 这是一个整数规划问题，设该问题的最优目标函数值为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\text{OPT})。

对该问题进行 LP 松弛，将 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20\in%20\{0,%201\}) 改为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20\ge%200)。设松弛后的线性规划问题最优解为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x^*)，最优目标函数值为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\text{OPT}_{LP})，显然有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\text{OPT}_{LP}%20\le%20\text{OPT})。

我们构造原问题的可行解 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x) 如下：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)x_i = \begin{cases} 1 & x^*_i \ge 0.5 \\ 0 & x^*_i < 0.5 \end{cases}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 由于对于每条边 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(i,%20j)) 存在 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x^*_i%20+%20x^*_j%20\ge%201) 的限制，则 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\max(x^*_i,%20x^*_j)%20\ge%200.5)，所以 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_i%20+%20x_j%20\ge%201) 仍然成立。我们构造的解是可行的。

容易看出，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_i%20\le%202x^*_i)。将我们构造的解代入目标函数，有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\sum\limits_{i=1}^n w_ix_i \le 2\sum\limits_{i=1}^n w_ix^*_i \\ \le 2\text{OPT}_{LP} \le 2\text{OPT}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 这就证明了算法的近似比为 2。

这种“四舍五入”的构造方法在两个东西加起来至少为 1 的限制下似乎挺好用的，可以证明很多近似算法的近似比为 2。

#### Unrelated Parallel Machine Scheduling (UPMS)

UPMS 问题是说：有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20m) 台机器和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 件物品，每件物品都要在一台机器上加工，第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 台机器加工第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 件物品的时间为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_{i,%20j})。求一种把物品分配给机器的方案，使得加工总时长最长的机器，加工总时长最短。

我们很容易写出该问题的优化模型：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \min\limits_{x, t} & t \\ \text{s.t.} & \sum\limits_{i=1}^m x_{i, j} = 1 & \forall j \in \{1, 2, \dots, n\} \\ & \sum\limits_{j=1}^n a_{i, j}x_{i, j} \le t & \forall i \in \{1, 2, \dots, m\} \\ & x_{i, j} \in \{0, 1\} \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)

对这个模型进行 LP 松弛不是一个好主意。假设只有一件物品需要加工，而且该物品在所有机器上的加工时间都为 1。那么原问题的最优目标函数值显然为 1，然而 LP 松弛后的最优目标函数值为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%201/m)（LP 松弛求出的最优解为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_{i,%201}%20=%201/m)），下界太松了，很难进行近似比分析。

 

但是聪明的数学家们对优化模型进行了一个改动：先二分 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20t) 的值，如果 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_{i,%20j}%20>%20t)，那么加上 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_{i,%20j}%20=%200) 的限制（或者直接把这个变量从 LP 中拿走）。很显然，让改动后的 LP 问题存在可行解的最小的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20t)，就是原问题最优目标函数值的下界（用两阶段法的第一阶段判断是否存在可行解即可）。

现在我们通过二分找到了这个最小的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20t)，设改动后的 LP 问题最优解为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x^*)。对于第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 件物品，若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\exists%20i,%20x^*_{i,%20j}%20=%201) 那么称该物品为“整数物品”，设共有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n_1) 个“整数物品”；否则称该物品为“分数物品”，设共有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n_2) 个“分数物品”。显然有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n_1%20+%20n_2%20=%20n)

容易发现，若第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 件物品为“分数物品”，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_{i,%20j}) 中至少有两个非零值。由于原问题有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n+m) 条限制，根据单纯形法，非零的变量至多有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n+m) 个，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n_1%20+%202n_2%20\le%20n%20+%20m)，得到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n_2%20\le%20m)。

下面我们给每台机器分配物品，使得每台机器的加工总时长都不超过 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%202t)，以此设计一个近似比为 2 的算法。

先进行两个定义：若连通图中边数小等于点数，那么称该连通图为**伪树**；若一张图的所有连通块都是伪树，那么称该图为**伪森林**。

构造一张二分图：左边有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20m) 个点，每个点表示一台机器；右边有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 个点，每个点表示一件物品。若 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_{i,%20j}%20>%200) 则连接第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 台机器和第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 件物品。如果这个二分图不连通，那么对每个连通块分别求解，最后把解合并起来就是答案，所以我们假设该二分图连通。由于非零变量至多有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n+m) 个，所以该连通图的边数不超过点数，是一个伪树。

首先考虑“整数物品”。很显然，每个“整数物品” ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 都只和一台机器 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 有连边 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(i,%20j))，那就把“整数物品” ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 放在机器 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 中加工，并去掉物品 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 和边 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(i,%20j))。由于每次恰好去除一个点和一条边，这张图仍然是伪树。显然，此时每台机器的加工总时长至多为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20t)（不然 LP 的最优目标函数值就不只有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20t) 了）。

这样，图中就只剩机器和“分数物品”了。我们来考虑所有度数为 1 的机器 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i)。假设唯一连接机器 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 的边是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(i,%20j))，那么我们把“分数物品” ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 放在机器 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 中加工，并去掉机器 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i)、物品 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 和物品 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 的所有连边。由于每件“分数物品”都有至少两条连边（度数至少为 2），所以我们每次都会去掉两个点以及至少两条边，容易说明剩下的图是伪森林。

反复考虑度数为 1 的机器并进行删除操作，直到最后不存在度数为 1 的机器为止。由于剩下的图是伪森林也是二分图，那么剩下的图中只能包含若干偶环。在偶环上随便给每台机器分配一件物品即可。

这样，每台机器至多分配到一个“分数物品”（别忘了一件物品的加工时间至多为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20t)），再加上原来分配给它的“整数物品”，每台机器的总加工时长至多为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%202t)，这就是一个近似比为 2 的算法。

### Approximation - 2

#### 均摊体积

如果有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 个物品，每个物品的体积都是 0.51，我们可以分析出最优目标函数值的下界至少约为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n/2)。可是这个下界太松了（事实上最优目标函数值就是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n)），只能用来证明近似比为 2。怎样才能证明渐进比为 1.7 呢？

聪明的数学家们不知怎么就想到了“均摊体积”的方法。设第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 件物品体积为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20a_i)，定义权重 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w(a_i)) 如下：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)w(a_i) = \frac{6}{5}a_i + v(a_i)![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 称 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20v) 为 bonus，定义为：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)v(a_i) = \begin{cases} 0 & a_i \le \frac{1}{6} \\ \frac{3}{5}(a_i - \frac{1}{6}) & \frac{1}{6} < a_i \le \frac{1}{3} \\ \frac{1}{10} & \frac{1}{3} < a_i \le \frac{1}{2} \\ \frac{2}{5} & a_i > \frac{1}{2} \end{cases}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)

#### Proof

记 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w(I)) 为 bin packing 的一个实例 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I) 的权重总和，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\text{FF}(I)) 表示对实例 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I) 运用 first fit 算法得到的目标函数值，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\text{OPT}(I)) 表示实例 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I) 的最优目标函数值。

再记 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B) 为 first fit 算法得到的方案，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B^*) 为最优方案，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c(B_j)) 表示第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 个 bin 中物品的体积总和，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w(B_j)) 表示第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20j) 个 bin 中物品的权重总和。

我们容易得到以下等式 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)w(I) = \sum\limits_{i=1}^n w(a_i) = \sum\limits_{j=1}^{\text{FF}(I)}w(B_j) = \sum\limits_{j=1}^{\text{OPT}(I)}w(B^*_j)![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)

如果我们能证明 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\forall%20c(B^*_j)%20\le%201,%20w(B^*_j)%20\le%201.7)，根据 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w(I)%20=%20\sum\limits_{j=1}^{\text{OPT}(I)}w(B^*_j))，我们就能得到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w(I)%20\le%201.7\text{OPT}(I))；如果我们还能证明所有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w(B_j)) 的均值都至少为  1，那么根据 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w(I)%20=%20\sum\limits_{j=1}^{\text{FF}(I)}w(B_j))，我们就能证明 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\text{FF}(I)%20\le%20w(I)%20\le%201.7\text{OPT}(I))。不过我们这里要证明一个弱一点的结论：除了两个 bin 以外，其它 bin ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w(B_j)) 的均值都至少为  1。后面我们会看到，这个结论将会推导出 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\text{FF}(I)%20\le%20w(I)%20+%200.8%20\le%201.7\text{OPT}(I)%20+%200.8)，就能证明 first fit 算法 1.7 的近似比。

 

##### 第一步：证明均摊体积不超过 1.7

第一步的证明比较容易，根据权重的定义可以直接推导出来。对于一个 bin，分以下情况讨论。

1.  如果所有物品体积 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c) 均有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c%20\le%20\frac{1}{6})

这个情况下，bin 的权重就是 bin 中物品体积总和的 1.2 倍，不会超过 1.7。

2.  如果存在物品体积 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c) 有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{1}{6}%20<%20c%20\le%20\frac{1}{2})

很显然，这种物品在一个 bin 内至多有 5 个，那么 bonus 不会超过 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{1}{10}%20\times%205%20=%20\frac{1}{2})，权重也不会超过 1.7。

3.  如果存在两个物品体积 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_1) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_2) 有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_1%20>%20\frac{1}{2}) 且 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{1}{3}%20<%20c_2%20\le%20\frac{1}{2})

很显然，其它物品的体积都不会超过 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{1}{6})，没有 bonus；![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_1) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_2) 带来的 bonus 恰为 0.5，权重不会超过 1.7。

4.  如果存在三个物品体积 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_1)，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_2) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_3) 有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_1%20>%20\frac{1}{2})，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{1}{6}%20<%20c_2,%20c_3%20\le%20\frac{1}{3}) 且 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_2%20+%20c_3%20<%20\frac{1}{2})

很显然，其它物品的体积都不会超过 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{1}{6})，没有 bonus；![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_2) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_3) 带来的 bonus 为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{3}{5}(c_2%20-%20\frac{1}{6})%20+%20\frac{3}{5}(c_3%20-%20\frac{1}{6})%20<%200.1)，再加上 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_1) 带来的 bonus 0.4，权重不会超过 1.7。

 

##### 第二步：证明除两个 bin 以外，其它 bin 权值均值至少为 1

我们首先去掉权值至少为 1 的 bin，考虑那些权值不足 1 的 bin。容易证明，权值不足 1 的 bin 有以下性质：

1.  不含体积至少为 0.5 的物品；
2.  一个 bin 内不会包含两个体积至少为 1/3 的物品；
3.  bin 的体积之和小于 5/6。

据此容易推出：

1.  除了最后一个 bin，其它 bin 中至少有两个物品；
2.  除了最后两个 bin，其它 bin 的体积之和都大于 2/3（如果有一个 bin 的体积之和不超过 2/3，由于是 first fit 算法，后面 bin 里的物品体积肯定至少为 1/3 但不足 1/2；而后面至少还有两个 bin，这就违反了“一个 bin 内不会包含两个体积至少为 1/3 的物品”的性质）。

 

下面证明一个引理：如果两个 bin ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B_1) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B_2) 满足 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B_1) 在 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B_2) 前面、![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w(B_1),%20w(B_2)%20<%201)、![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c(B_1)%20\ge%20\frac{2}{3}) 以及 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B_2) 有至少两个物品，则 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{6}{5}c(B_1)%20+%20v(B_2)%20\ge%201)。

引理的证明，只需要分类讨论 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B_2) 里体积最小的物品的体积 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c') 即可：

首先，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c'%20\ge%20\frac{1}{6})，不然 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B_1) 将会与“bin 的体积之和小于 5/6”的性质矛盾；

其次，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c'%20<%20\frac{1}{3})，不然 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B_2) 将会与“一个 bin 内不会包含两个体积至少为 1/3 的物品”的性质矛盾；

另外，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c'%20>%201%20-%20c(B_1))，不然 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c') 就会放进 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B_1) 里。

那么只可能有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{1}{6}%20\le%20c'%20<%20\frac{1}{3})，则 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} & \frac{6}{5}c(B_1) + v(B_2) \\ \ge & \frac{6}{5}c(B_1) + 2 \times v(c') \\ > & \frac{6}{5}c(B_1) + \frac{6}{5}(1 - c(B_1) - \frac{1}{6}) \\ = & 1\end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)

 

假设 first fit 得到的方案中，权重之和小于 1 的 bin 按先后顺序为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B_1,%20B_2,%20\dots,%20B_k)，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} & w(B_1) + w(B_2) + \dots + w(B_{k-2}) + w(B_{k-1}) + w(B_k) \\ = & v(B_1) + (\frac{6}{5}c(B_1) + v(B_2)) + \dots + (\frac{6}{5}c(B_{k-2}) + v(B_{k-1})) + (\frac{6}{5}c(B_{k-1}) + \frac{6}{5}c(B_k)) + v(B_k) \\ \ge & (k-2) + \frac{6}{5} \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 也就是说，除了最后两个 bin，其它的 bin 权值均值都至少为 1。再补个 0.8，再加上权值本来就至少为 1 的 bin，那么所有的 bin 权值均值就都至少为 1 了。这就完成了渐进比为 1.7 的证明。

### Approximation - 3

#### Configuration LP

我们将 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 个物品按体积分类，设共有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 种不同的体积，记为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_1,%20c_2,%20\dots,%20c_k)，每种体积有物品 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20b_1,%20b_2,%20\dots,%20b_k) 个。

对于一个 bin，我们枚举体积为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_1) 的物品放几个，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_2) 的放几个，...，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_k) 的放几个。

假设一共有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20N) 种不同的方案（又称为 pattern），记 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20t_{i,%20j}) 表示第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 种方案中，体积为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_j) 的物品放了几个。我们设 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_i) 表示对一个 bin packing 问题得到的答案中，第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 种方案的 bin 用了几个。

那么，我们能写出 bin packing 的线性规划问题：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} \min\limits_x & \sum\limits_{i=1}^N x_i \\ \text{s.t.} & \sum\limits_{i=1}^N t_{i, j}x_i \ge b_j & \forall j \in \{1, 2, \dots, k\} \\ & x \ge 0 \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)

这个线性规划看起来变量很多，但是可以通过某种神奇的方法在比较好的多项式时间内求解。

#### Approximation algorithm

下面将提出一种渐进比为 1 的近似算法。记 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20N(I)) 表示该算法对 bin packing 的实例 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I) 算出来的答案，我们将要证明 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20N(I)%20\le%20\text{OPT}_{LP}(I)%20+%20O(\log^2\text{OPT}_{LP}(I)))。算法步骤如下：

1.  记 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c(I)) 表示实例 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I) 中物品的体积总和，先将体积小于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{1}{c(I)}) 的物品拿走。等其它物品用迭代算法分配完后，再把小的物品用 first fit 安排进去。
2.  使用迭代算法分配剩下的物品。

 

为什么最后分配“小”的物品不影响结论呢？下面先证明一个引理。

**引理**：设 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I) 为 bin packing 问题的实例，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20g) 是一个 0~1 之间的实数。我们称体积至少为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{g}{2}) 的物品为“大”物品，其它物品是“小”物品。我们首先分配大物品，设一共用了 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 个 bin。此时再用 first fit 把小物品也分配进去，则总共使用的 bin 数至多为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\max(A,%20(1+g)c(I)+1))。

**证明**：设总共使用的 bin 数量为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B)。如果最后的 first fit 没有再开新的 bin，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B%20=%20A)；否则至多有一个 bin 体积小于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%201%20-%20\frac{g}{2})，那么我们可以推出 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c(I)%20\ge%20(1%20-%20\frac{g}{2})(B-1))，再结合 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%200%20\le%20g%20\le%201)，就有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20B%20\le%20\frac{2}{2-g}c(I)%20+%201%20\le%20(1+g)c(I)+1)。

回到我们的算法，算法的第 1 步其实就是让 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{1}{c(I)}%20=%20\frac{g}{2})，即 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c(I)%20=%20\frac{2}{g})。只要有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c(I)%20\ge%202)（![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c(I)%20<%202) 用 first fit 就行了，反正要证的是渐进比嘛...），那么用 first fit 分配小物品后，使用的总 bin 数就是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20(1%20+%20\frac{2}{c(I)})c(I)%20+%201%20=%20c(I)%20+%203)（然后和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 取个 max），不改变我们渐进比为 1 的结论。下面我们只要证明 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20A) 也符合结论就行了。

#### Iterative algorithm

下面说明要用到的迭代算法，并证明算法的结果仍然符合渐进比为 1 的结论。每一次迭代考虑当前的实例 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I)，进行以下步骤：

##### 第一步

求出 configuration LP 的解。设第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 个 pattern 用了 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x_i) 次，由于 LP 只有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 个限制，那么非零量至多只有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k) 个（所以不用担心因为非零量太多直接变成指数级算法）。

##### 第二步

把实例 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I) 拆成两部分，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I_1) 包含了解的整数部分（即 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\left\lfloor%20x%20\right\rfloor)），![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I_2) 包含了解的小数部分（即 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x%20-%20\left\lfloor%20x%20\right\rfloor)）。由于我们使用的 pattern 种数至多为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k)，那么小数部分物品的体积总和不超过 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k)。

很容易发现，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I_1) 的最优解就是恰好放满 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\text{OPT}_{LP}(I_1)) 个 bin，那么容易有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\text{OPT}_{LP}(I_1)%20+%20\text{OPT}_{LP}(I_2)%20=%20\text{OPT}_{LP}(I))。

举个例子：

假如有 2 种物品 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_1,%20c_2) 和 2 种 pattern。

第 1 个 pattern 有 3 个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_1) 与 1 个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_2)；

第 2 个 pattern 有 1 个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_1) 与 3 个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_2)。

Configuration LP 的解为 2.5 个 pattern 1 与 1.5 个 pattern 2。

那么我们把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I) 拆成两个部分，

![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I_1) 里有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%203%20\times%202%20+%201%20\times%201%20=%207) 个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_1) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%201%20\times%202%20+%203%20\times%201%20=%205) 个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_2)，

![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I_2) 里有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%203%20\times%200.5%20+%201%20\times%200.5%20=%202) 个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_1) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%201%20\times%200.5%20+%203%20\times%200.5%20=%202) 个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20c_2)。

##### 第三步

把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I_2) 中的所有物品按体积总大到小排序，设为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20d_1%20\ge%20d_2%20\ge%20\dots)。

我们把这些物品分堆：首先找到最小的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n_1)，把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20d_1) 到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20d_{n_1}) 分成第一堆，且堆内物品体积总和至少为 2；再找到最小的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n_2)，把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20d_{n_1+1}) 到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20d_{n_2}) 分成第二堆，且堆内体积总和至少为 2；...这样分成 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20p) 堆，显然只有最后一堆的体积总和可能小于 2。

由于每个物品的体积都至多为 1，每一堆的体积总和肯定小于 3。还容易发现，由于物品是按体积从大到小排序的，有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n_1%20\le%20n_2%20\le%20\dots%20\le%20n_{p-1})。

 

接下来，我们去掉第一堆和第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20p) 堆。在第 2 到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20p-1) 堆中，对于第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 堆，我们只留下最大的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n_{i-1}) 个物品（去掉剩下的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n_i%20-%20n_{i-1}) 个物品），并且把这些物品的体积都放大到第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 堆里最大的体积。将我们留下来的物品构成实例 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I')。

不难注意到，如果我们把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I') 也进行分堆，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I') 里第一堆的物品数和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I_2) 里第一堆的物品数相同，但体积都没有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I_2) 第一堆的大，其它堆也是如此。所以我们有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\text{OPT}(I')%20\le%20\text{OPT}(I_2))。我们只要把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I') 作为新一轮迭代的实例进行迭代即可。

不过，我们要迭代多少轮呢？注意到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I_2) 分堆后，每一堆的体积至少为 2，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I') 中体积不同的物品种数至多为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{c(I_2)}{2})。别忘了我们在第二步中发现的结论：小数部分物品的体积总和不超过体积不同的物品种数。所以每一轮 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I_2) 的体积都会折半，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\log%20c(I)) 轮之后迭代就会结束。

 

最后我们再来看看被我们去掉的物品总体积是多少。

首先，我们去掉了第一堆和第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20p) 堆，这两堆的体积之和至多为 6。

再来看第 2 堆到第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20p-1) 堆。对于第 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20i) 堆，我们去掉了 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n_i%20-%20n_{i-1}) 个物品，它们的体积均值不会超过 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{3}{n_i})（只考虑小的值，均值会变小）。我们来求个和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)\begin{matrix} & 6 + \sum\limits_{i=2}^{p-1}(n_i-n_{i-1})\frac{3}{n_i} \\ = & 6 + 3\sum\limits_{i=2}^{p-1}(\frac{1}{n_i} + \frac{1}{n_i} + \dots + \frac{1}{n_i}) \\ \le & 6 + 3\sum\limits_{i=2}^{p-1}(\frac{1}{n_{i-1}+1} + \frac{1}{n_{i-1}+2} + \dots + \frac{1}{n_i}) \\ \le & 6 + 3\sum\limits_{i=1}^{n_{p-1}} \frac{1}{i} \end{matrix}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 别忘了我们一开始就把体积小于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{1}{c(I)}) 的物品拿走了，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n_{p-1}%20\le%203%20\div%20\frac{1}{c(I)}%20=%203c(I))，那么去掉的物品总体积就是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20O(\log%20c(I))) 的了。

我们最后再把这些去掉的物品 first fit 一下就好了。我们知道 first fit 近似比是 1.7 的，不会改变大 O 的结论。

##### 回顾一下

每次迭代都会把当前实例 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I) 分成 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I_1) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I_2)。![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I_1) 里的物品由于恰好装满箱子，肯定是最优解的一部分，那么比最优解差的部分就来自于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I_2) 中被去掉的物品。而 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20I_2) 中被去掉的物品总体积为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20O(\log%20c(I)))，迭代最多进行 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\log%20c(I)) 次，所以算法的结果就是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\text{OPT}_{LP}(I)%20+%20O(\log^2%20C(I))%20\le%20\text{OPT}_{LP}(I)%20+%20O(\log^2\text{OPT}_{LP}(I)))，这就完成了证明。

### Approximation - 4

#### Planar Steiner Tree

平面上的斯坦纳树指的是这样的问题：平面上有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 个点，要用总长尽量少的线段把它们连通起来。要注意，线段不一定要在给定的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 个点相交（不然跑个最小生成树就没了），完全可以在平面上的其它点相交。最优解中，线段在平面上除了给定点外的交点称为斯坦纳点。

![平面斯坦纳树（n = 3）](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3f/Steiner_3_points.svg/330px-Steiner_3_points.svg.png)![平面斯坦纳树（n = 4）](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e4/Steiner_4_points.svg/330px-Steiner_4_points.svg.png)

可以从上图看出 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n%20=%203) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n%20=%204) 的情况，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S)、![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S_1) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S_2) 是斯坦纳点。![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n%20=%203) 时，斯坦纳点就是三角形的费马点。

平面上的斯坦纳树是一个 NP-Hard 问题。

#### 满足三角不等式的完全图上的斯坦纳树

满足三角不等式的完全图上的斯坦纳树指的是这样的问题：给定一张满足三角不等式（对于任意两两有连边的三点 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20x,%20y,%20z)，有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w(x,%20y)%20\le%20w(x,%20z)%20+%20w(z,%20y))，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w) 表示边权）的完全图 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20G%20=%20(V,%20E)) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S%20\subseteq%20V)，求 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20G) 的连通子图 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20G')，使得 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 中的所有点都在 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20G') 中，且 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20G') 边权之和最小。

即使有了这么多的限制条件，这个问题仍然是一个 NP-Hard 问题（[证明见此](https://www.cise.ufl.edu/~mythai/courses/2009/cis6930/Notes/HardnessOfVertexCoverandSteinerTree.pdf)）。下面我们提出它的一个 2- 近似算法：其实很简单，只要算出 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 的最小生成树即可（别忘了是完全图，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 肯定是连通的）。

**算法近似比证明**：

假设最优的斯坦纳树边权之和为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\text{OPT})，最小生成树的边权之和为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\text{MST})。我们把最优斯坦纳树中的每条边复制一次，得到一张有欧拉回路的图，它的边权总和为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%202\text{OPT})。

我们在欧拉图中任选一个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 中的点出发，找到一条欧拉回路 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20L)。我们只走 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 中的点，且每个点只走一次，如果不能沿着 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20L) 走到下一个点就直接“跳到”那个点（别忘了是完全图，这种“跳跃”称为 short-cutting）。

![斯坦纳树近似算法](https://images.cnblogs.com/cnblogs_com/tsreaper/1112059/o_aop11.steiner.2approx.png)

举个例子，例如上图是我们找到的欧拉回路的一部分，红色点是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 中的点。由于不能从第一个 a 沿着 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20L) 走到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20b)，我们要跳过去；由于 a 已经走过了，所以不能走 c → a → d，而是要从 c 直接跳到 d。

由于完全图符合三角不等式，直接跳过去肯定不比沿着 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20L) 走过去来得长。这样，我们就找到了 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 的一个连通图，而且这个连通图的边权之和至多为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%202\text{OPT})。

别忘了，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 的任何连通图，边权之和都不比最小生成树小。所以我们有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\text{MST}%20\le%202\text{OPT})。这就证明了算法的近似比是 2。

![斯坦纳树近似比的例子](https://images.cnblogs.com/cnblogs_com/tsreaper/1112059/o_aop11.steiner.2approx.example.png)

用上图的例子说明这个近似比对于这个算法是紧的。图中没有画出来的边权值都是 2。令 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S%20=%20\{1,%202,%20\dots,%20n\})，显然最优解为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n)（利用中间的 0 作为斯坦纳点），但用上面的算法会得到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%202(n-1)) 的结果，在 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 足够大的时候近似比趋近于 2。

#### 旅行商问题的近似比

大家都知道，完全图上的 TSP 是 NP-Hard。然而，完全图上的 TSP 甚至没有很好的近似比。下面证明完全图上的 TSP 不存在近似比为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20O(2^{\text{poly}(n)})) 的多项式算法，其中 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\text{poly}(n)) 表示 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 的多项式。

我们利用哈密尔顿回路问题进行证明。对于普通无向图 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20G%20=%20(V,%20E)) 上的哈密尔顿回路问题，我们构造完全图 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20G'%20=%20(V,%20E'))，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20E') 中一条边 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20e') 的边权 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w(e')) 定义如下：![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20)w(e') = \begin{cases} 1 & e' \in E \\ 2^{\text{poly}(n)}n & e' \not\in E \end{cases}![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20) 这张完全图的输入规模仍然是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n) 的多项式。

如果 TSP 存在近似比为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20O(2^{\text{poly}(n)})) 的算法，那么对于上面的完全图，算法就绝对不能选 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20e'%20\not\in%20E) 的边。但如果算法只用 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20e'%20\in%20E) 的边构造出了一个解，那就同时找到了 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20G) 中的哈密尔顿回路。我们知道，找哈密尔顿回路本身就是 NPC 的，这就完成了证明。

#### 满足三角不等式的完全图的旅行商问题

既然普通完全图上的旅行商问题这么难，我们给它加一点限制。在满足三角不等式的完全图上，TSP 就有很好的近似比。

首先容易证明这个问题近似比上界为 2：先跑个最小生成树（边权和肯定小等于最优哈密尔顿回路），把树上每条边重复一次变成欧拉图，在欧拉图上进行和斯坦纳树类似的 short-cutting 即可。

不过我们可以证明一个更紧的上界。不一定要把树上每条边都重复一次才能得到欧拉图嘛，如果我们把树上度数为奇数的点（下面简称奇点）进行配对（一张图的奇点肯定有偶数个，不用担心有一个匹配不上），每一对之间连一条边，那么构成的图就都是偶点，也就是一张欧拉图了。这种配对工作非常容易，只要用带花树什么的求一个最小权完美匹配即可。下面证明这种算法的近似比为 1.5。

![TSP 1.5 近似算法](https://images.cnblogs.com/cnblogs_com/tsreaper/1112059/o_aop11.tsp.approx.png)

假设最优的哈密尔顿回路如上图，白色的点是最小生成树上的奇点。我们将奇点按顺序进行 short-cutting，就能得到两个不相交匹配（1 - 2, 3 - 4, ..., 2k-1 - 2k 以及 2 - 3, 4 - 5, ..., 2k - 1）。由于满足三角不等式，这两个匹配的权值之和肯定不大于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\text{OPT})，那么两个匹配中较小的那个权值肯定不大于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%200.5\text{OPT})。别忘了，我们在算法中求出来的可是最小完美匹配，那么最小完美匹配的权值肯定也不大于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%200.5\text{OPT})。最小生成树 + 最小权完美匹配就证明了 1.5 的近似比。

![TSP 1.5 近似比的例子](https://images.cnblogs.com/cnblogs_com/tsreaper/1112059/o_aop11.tsp.approx.example.png)

上面的例子可以说明 1.5 对这个算法是紧的，没有画出来的边权值都是 2。右边实线是算法可能获得的最小生成树，虚线是算法可能算出的最小权完美匹配。显然最优解为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n)，而算法可能得出的解是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20n%20+%20\frac{n}{2})。只要“梯形”上面的点足够多，那么近似比就是 1.5。

#### 满足三角不等式的完全图的最短哈密尔顿路

下面来考虑一个有些不一样的问题：在满足三角不等式的完全图中，给定 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k%20=%20\{0,%201,%202\}) 个固定点（即指定起点或者终点，或者都指定，或者都不指定），求满足固定点的最短哈密尔顿路。

这个问题可以通过以下近似算法解决：

1.  首先求个最小生成树 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20T)；
2.  令点集 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 包含两类点：在最小生成树上是偶点的固定点（因为要把固定点变奇点，才好找以它们开头的欧拉路），以及在最小生成树上是奇点的非固定点；
3.  类似于 TSP 问题，求个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 的最小权匹配 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20M)，要求有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%202-k) 个非固定点不匹配（只要加入 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%202-k) 个辅助点，与非固定点连权值为 0 的辅助边即可）。容易发现，这样会恰有 2 个点成为奇点，并且固定点一定在这 2 个点里；
4.  这样 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20T%20\cup%20M) 就是一张有欧拉路的图，用 short-cutting 的方法把欧拉路变成哈密尔顿路即可。

 

这个算法在 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k%20\in%20\{0,%201\}) 时是 1.5 近似算法。下面进行证明。

##### ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k%20=%200)

证明思想与 TSP 类似。假设最优解上有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%202t) 个奇点，那么可以拆成两个匹配：1 - 2, 3 - 4, ..., (2t-3) - (2t-2)（2t-1 和 2t 没有匹配） 与 2 - 3, 4 - 5, 6 - 7, ..., (2t-2) - (2t-1)（1 和 2t 没有匹配），就可以证明 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20M) 的权值之和至多为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%200.5\text{OPT})。

##### ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k%20=%201)

不妨设起点（设为 s）是固定点。

如果起点是奇点比较好办，假设最优解上有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%202t+1) 个奇点（不含起点），那么可以拆成两个匹配：1 - 2, 3 - 4, ..., (2t-1) - 2t（2t+1 没有匹配）与 2 - 3, 4 - 5, ..., 2t - (2t+1)（1 没有匹配）；

如果起点是偶点就比较麻烦了。假设最优解上有 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%202t) 个奇点，因为起点必须被匹配，我们没法把最优解拆成两个匹配符合要求的匹配。不过我们可以先把最优解拆成两个匹配 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20M_1)：s - 1, 2 - 3, ..., (2t-2) - (2t-1)（2t 没有匹配），以及 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20M_2)：1 - 2, 3 - 4, ..., (2t-1) - 2t（s 没有匹配）。

记 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w(M)) 表示匹配 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20M) 的权重之和。如果 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w(M_1)%20<%20w(M_2)) 那把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20M_1) 并入 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20T) 答案就已经出来了，否则我们用 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20T%20\cup%20M_2) 得到一张欧拉图，找出一条哈密尔顿回路，再去掉连接 s 的一条边，获得以 s 为起点的哈密尔顿路。由于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20w(M_2)%20\le%20w(M_1))，而我们加进图的是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20M_2)，所以仍然有 1.5 的近似比。

 

##### ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k%20=%202)

![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20k%20=%202) 的情况稍有不同，这个算法在同时给定起点与终点的情况下，近似比为 5/3。这次我们要把 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20T%20\cup%20\text{OPT}) 拆成 3 个匹配来完成证明。下面以起点（记为 s）与终点（记为 t）均为偶点为例进行证明，其它情况类似。

不难发现，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20T%20-%20\{s,%20t\}) 中有偶数个点，那么 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 中也有偶数个点。设最优路径依次经过 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20s,%20v_1,%20v_2,%20\dots,%20v_{2k},%20t)，其中 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20v_i) 是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20T) 上的奇度点。

记 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20u%20-%20v) 表示仅通过最优路径中的边从点 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20u) 走到点 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20v)，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20u%20\sim%20v) 表示仅通过 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20T) 中的边从点 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20u) 走到点 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20v)。我们尝试将 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20T%20\cup%20\text{OPT}) 拆成这样三个部分（不一定是匹配），且每条边至多使用一次：

1.  ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20s%20-%20v_1,%20v_2%20-%20v_3,%20\dots,%20v_{2k-2}%20-%20v_{2k-1},%20v_{2k}%20-%20t)；
2.  ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20v_1%20-%20v_2,%20v_3%20-%20v_4,%20\dots,%20v_{2k-1}%20-%20v_{2k},%20s%20\sim%20t)；
3.  找到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20s,%20t,%20v_1,%20v_2,%20\dots,%20v_{2k}) 的一个排列 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20u_1,%20u_2,%20\dots,%20u_{2k+2})，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20u_1%20\sim%20u_2,%20u_3%20\sim%20u_4,%20\dots,%20u_{2k+1}%20\sim%20u_{2k+2})。

由于三角不等式，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20u%20\sim%20v) 所使用的边的权值总和，一定大等于直接连接 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20u) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20v) 的边的权值。如果我们能找到以上拆分，且每条边至多使用一次，那么我们就找到了 3 个 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 的完美匹配，其权值总和不超过 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%202\text{OPT})。这样，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 的最小权完美匹配权值就不会超过 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{2}{3}\text{OPT})，就能证明 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{5}{3}) 的近似比。

 

![哈密尔顿路 k=2 例](https://images.cnblogs.com/cnblogs_com/tsreaper/1112059/o_aop11.hamilton.k=2.png)

举个例子。左图中，实线是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20T) 的边，虚线是 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\text{OPT}) 中的边；红边是部分 1 中的边，蓝边是部分 2 中的边，绿边是部分 3 中的边。

再看右图。虽然所有绿色边不能构成一个匹配，但是橙色边却可以构成一个匹配，而且权值之和一定不大于绿色边的权值之和。

 

很显然，部分 1 与部分 2 中除开 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20s%20\sim%20t) 之外的边，就组成了最优路径。我们通过以下算法，在 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20T) 上找到部分 3 以及部分 2 中 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20s%20\sim%20t) 中的边：

1.  在 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20T) 中找到从 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20s) 到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20t) 的路径作为 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20s%20\sim%20t)，去掉使用过的边；
2.  对于每个连通块，选择任意一个奇度点 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20u)，在 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20T) 中找到通往另一个奇度点 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20v) 的路径，且路径上不含其它奇度点。去掉使用过的边；
3.  重复步骤 2，直到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 中的点都在步骤 2 中找到了对应的点。

根据算法描述容易看出，如果算法成功退出，我们就找到了需要的拆分。接下来说明 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 中的每个点都能在步骤 2 中找到对应的点，即算法可以成功退出。

注意到 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20s) 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20t) 均为偶度点。步骤 1 结束后，由于 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20s) 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20t) 是路径端点，去掉路径上的边后，![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20s) 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20t) 都变成了奇度点；而路径上的其它点在去掉路径上的边后，奇偶性不变。

步骤 2 中，由于每个连通块一定有偶数个奇度点，所以一定可以找到符合要求的 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20u) 和 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20v)。由于路径中间不含其它奇度点，所以其它点的奇偶性不变，不影响算法的后续运行；而 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20u) 与 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20v) 作为路径端点，在去掉路径中的边后都变成了偶度点，不会再次被选中，也不影响算法的后续运行。

因此，我们一定可以将 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20T%20\cup%20\text{OPT}) 拆成 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20S) 的 3 个完美匹配，即可证明算法的近似比不超过 ![Image](http://chart.googleapis.com/chart?cht=tx&chl=\Large%20\frac{5}{3})。


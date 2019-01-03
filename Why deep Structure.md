---
typora-copy-images-to: img
---

### Why Deep Structure?

#### 1、Can shallow network fit any function? 

 **Given a shallow network structure with one hidden layer with ReLU activation and linear output**

![1-1](https://github.com/haoyuheng/MLDS_notebook/blob/master/img/1-1.png)

**Given a L-Lipschitz function **$f^*$

Lipschitz（利普希茨）连续定义： 
有函数$f(x)$，如果存在一个常量L，使得对$f(x)$定义域上（可为实数也可以为复数）的任意两个值满足如下条件： 
<a href="https://www.codecogs.com/eqnedit.php?latex=|f(x_1)-f(x_2)|\leq&space;L*|x_1-x_2|" target="_blank"><img src="https://latex.codecogs.com/gif.latex?|f(x_1)-f(x_2)|\leq&space;L*|x_1-x_2|" title="|f(x_1)-f(x_2)|\leq L*|x_1-x_2|" /></a>
那么称函数$f(x)$满足Lipschitz连续条件，并称L为$f(x)$的Lipschitz常数。 

Lipschitz连续比一致连续要强。它限制了函数的局部变动幅度不能超过某常量。

**How many neurons are needed to approximate$f^*$?** 

Given a small number $\varepsilon > 0$
$$
\exists  f\epsilon N(K) \max_{0\leq x \leq 1}|f(x)-f^*(x)|\leq \varepsilon
$$
$f\epsilon N(K)$：The function space defined by the network with K neurons.

The difference between$f(x)$ and $𝑓
^∗( 𝑥)$ is smaller than $\varepsilon$

![1-2](https://github.com/haoyuheng/MLDS_notebook/blob/master/img/1-2.png)

**So $2L/\varepsilon$ Relu neurons shallow network can fit any  L-Lipschitz function.**

#### 2、Potential of Deep



#### 3、Is Deep better than Shallow?

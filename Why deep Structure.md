---
typora-copy-images-to: img
---

### 1	Why Deep Structure?

#### 1.1		Can shallow network fit any function? 

 **Given a shallow network structure with one hidden layer with ReLU activation and linear output**

![1-1](https://github.com/haoyuheng/MLDS_notebook/blob/master/img/1-1.png?raw=true)

**Given a L-Lipschitz function $f^*$**

Lipschitz（利普希茨）连续定义： 
有函数$f(x)$，如果存在一个常量L，使得对$f(x)$定义域上（可为实数也可以为复数）的任意两个值满足如下条件： 
$$
|f（x_1）-f(x_2)|\leq L*|x_1-x_2|
$$
那么称函数$f(x)$满足Lipschitz连续条件，并称L为$f(x)$的Lipschitz常数。 

Lipschitz连续比一致连续要强。它限制了函数的局部变动幅度不能超过某常量。

**How many neurons are needed to approximate$f^*$?** 

Given a small number $\varepsilon > 0$
$$
\exists  f\epsilon N(K) \max_{0\leq x \leq 1}|f(x)-f^*(x)|\leq \varepsilon
$$
$f\epsilon N(K)$：The function space defined by the network with K neurons.

The difference between$f(x)​$ and $𝑓
^∗( 𝑥)​$ is smaller than $\varepsilon​$

![1-2](https://github.com/haoyuheng/MLDS_notebook/blob/master/img/1-2.png?raw=true)

**So $2L/\varepsilon$ Relu neurons shallow network can fit any  L-Lipschitz function.**

#### 1.2		Potential of Deep

![1-5](https://github.com/haoyuheng/MLDS_notebook/blob/master/img/1-5.png?raw=true)

![1-4](https://github.com/haoyuheng/MLDS_notebook/blob/master/img/1-4.png?raw=true)

**If K is width, H is depth . We can have at least $K^H $pieces**

Depth has much larger influence than width.

也就是说当NN的layer的层数为H，每一层有K个Neural的时候，NN可以表示一个有$K^H $pieces的分段函数。

所以Depth的对NN表示能力的影响要大于Width。

#### 1.3		Is Deep better than Shallow?

![1-3](https://github.com/haoyuheng/MLDS_notebook/blob/master/img/1-3.png?raw=true)
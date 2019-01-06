## 4	Computational Graph

#### 4.1 	Computational Graph and Backpropagation

[*Calculus on Computational Graphs: Backpropagation*](https://colah.github.io/posts/2015-08-Backprop/)

##### 4.1.1 	Computational Graphs

Computational Graphs: A “language” describing a function

• Node: variable (scalar, vector, tensor ……)

• Edge: operation (simple function) 

For example, consider the expression e=(a+b)∗(b+1).

![tree-def](https://github.com/haoyuheng/MLDS_notebook/raw/master/assets/tree-def.png?raw=true)

##### 4.1.2	Derivatives on Computational Graphs

Sum rule: $\frac{\partial}{\partial a}(a+b) = \frac{\partial a}{\partial a} + \frac{\partial b}{\partial a} = 1$

Product rule:$\frac{\partial}{\partial u}uv = u\frac{\partial v}{\partial u} + v\frac{\partial u}{\partial u} = v$

Chain rule:![4-1](https://github.com/haoyuheng/MLDS_notebook/raw/master/assets/4-1.png?raw=true)

##### 4.1.3	Factoring Paths

![img](https://github.com/haoyuheng/MLDS_notebook/raw/master/assets/chain-def-greek.png?raw=true)

In the above diagram, there are three paths from X to Y, and a further three paths from Y to Z. If we want to get the derivative$\frac{\partial Z}{\partial X}$ by summing over all paths, we need to sum over 3∗3=9 paths:
$$
\frac{\partial Z}{\partial X} = \alpha\delta + \alpha\epsilon + \alpha\zeta + \beta\delta + \beta\epsilon + \beta\zeta + \gamma\delta + \gamma\epsilon + \gamma\zeta
$$
Instead of just naively summing over the paths, it would be much better to factor them:
$$
\frac{\partial Z}{\partial X} = (\alpha + \beta + \gamma)(\delta + \epsilon + \zeta)
$$
This is where “forward-mode differentiation” and “reverse-mode differentiation” come in.
**Forward-mode differentiation** starts at an input to the graph and moves towards the end.  At every node, it sums all the paths feeding in.

![img](https://github.com/haoyuheng/MLDS_notebook/raw/master/assets/chain-forward-greek.png?raw=true)

**Reverse-mode differentiation**, on the other hand, starts at an output of the graph and moves towards the beginning.  At each node, it merges all paths which originated at that node.

![img](https://github.com/haoyuheng/MLDS_notebook/raw/master/assets/chain-backward-greek.png?raw=true)

> **Forward-mode differentiation tracks how one input affects every node. Reverse-mode differentiation tracks how every node affects one output. That is, forward-mode differentiation applies the operator $\frac{\partial}{\partial X}$ to every node, while reverse mode differentiation applies the operator $\frac{\partial}{\partial X}$to every node( This might feel a bit like [dynamic programming](https://en.wikipedia.org/wiki/Dynamic_programming). That’s because it is!).**

##### 4.1.4	Computational Victories

 Imagine a function with a million inputs and one output. Forward-mode differentiation would require us to go through the graph a million times to get the derivatives. Reverse-mode differentiation can get them all in one fell swoop! A speed up of a factor of a million is pretty nice!

So, reverse-mode differentiation, called **Backpropagation** in the context of neural networks, gives us a massive speed up!

*If one has a function with lots of outputs, forward-mode differentiation can be much, much, much faster*

#### 4.2		 Computational Graph for Feedforward Network

**Feedforward Network** and **Loss Function of Feedforward Network**

![4-2](https://github.com/haoyuheng/MLDS_notebook/raw/master/assets/4-2.png?raw=true)

![4-3](https://github.com/haoyuheng/MLDS_notebook/raw/master/assets/4-3.png?raw=true)

**Gradient of Cost Function**

![4-4](https://github.com/haoyuheng/MLDS_notebook/raw/master/assets/4-4.png?raw=true)

#### 4.3 	Computational Graph for Recurrent Network

Recurrent Network** and **Loss Function of Recurrent Network**

![4-6](https://github.com/haoyuheng/MLDS_notebook/raw/master/assets/4-6.png?raw=true)

![4-5](https://github.com/haoyuheng/MLDS_notebook/raw/master/assets/4-5.png?raw=true)

**Gradient of Cost Function**

![4-7](https://github.com/haoyuheng/MLDS_notebook/raw/master/assets/4-7.png?raw=true)
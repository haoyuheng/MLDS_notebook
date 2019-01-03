## Deep Learning 

### Optimization

#### 1、When Gradient is Zero?

Critical Point包括: Local minima / Local maxima / Saddle Point（**鞍点**）

![5](https://github.com/haoyuheng/MLDS_notebook/blob/master/img/5.png)

Hessian Matrix的特征值其实就是对应的二阶导数，在特定的方向d的二阶导数我们可以写成 dtHd（因为H是一个实对称矩阵）。

![6](https://github.com/haoyuheng/MLDS_notebook/blob/master/img/6.png)

通过检测Hessian的特征值来判断该临界点是一个Local minima / Local maxima / Saddle Point（**鞍点**）。

当Hessian矩阵是正定的（所有特征值都为正），得到的是Local minima。因为Hessian在任意方向都是正的，参考单变量的二阶导数测试就能得到该结果。

同样的，当Hessian矩阵是负定的，这个点就是Local maxima。

如下图所示：

![](https://github.com/haoyuheng/MLDS_notebook/blob/master/img/7.png)

如果Hessian的特征值中至少一个是正的，一个是负的，那么x是f某个横截面的局部极大值，又是另一个横截面的局部极小值，则这个可能就是Saddle Point （鞍点）了。

当所有非0特征值是同号的且至少有一个特征值是0时，这个检测就是不确定的。



#### 2、Deep Linear Network

**线性多层网络**的所有局部极小值(local minima)是全局最小(global minimum)，也就说所有局部极小值的目标函数值是一样的

[Deep Learning without Poor Local Minima](https://arxiv.org/abs/1605.07110), NIPS, 2016

[Deep linear neural networks with arbitrary loss: All local minima are global](https://arxiv.org/abs/1712.01473), arXiv, 2017



#### 3、Non-linear  Deep Network ： Does it have Local Minima?

The Relu Network has local minima.

*"Blind Spot" of Relu: 所有的neural的output都是0, always be local minima*

#### 4、Conjecture about Deep Learning——Geometry of Loss Surfaces

*Almost all local minimum have very similar loss to the global optimum, and hence finding a local minimum is good enough.*

![1](https://github.com/haoyuheng/MLDS_notebook/blob/master/img/1.png)

#### 5、Empirical about Deep Learning——Geometry of Loss Surfaces

Training Processing: Different initialization / different strategies usually lead to similar loss (there are some exceptions). ![2](https://github.com/haoyuheng/MLDS_notebook/blob/master/img/2.png)

Batch Normalization![3](https://github.com/haoyuheng/MLDS_notebook/blob/master/img/3.png)

Skip Connection

![4](https://github.com/haoyuheng/MLDS_notebook/blob/master/img/4.png)

[Geometry of Neural Network Loss Surfaces via Random Matrix Theory](https://ai.google/research/pubs/pub46120)

### Conclusion

Deep linear network is not convex, but all the local minima are global minima.

​	• There are saddle points which are hard to escape

 Deep network has local minima.

​	• We need more theory in the future

 Conjecture:

​	• When training a larger network, it is rare to meet local minima.
​	• All local minima are almost as good as global

We can try to understand the error surface by visualization.

​	• The error surface is not as complexed as imagined.


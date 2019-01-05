## 3	Generalization（泛化）

### 3.1		Generalization Ability

**Generalization Gap**:  difference between training error and testing error

**Capacity of model**: "size" of the your model, 也可以理解为model的parameter的规模，可以使用VC维来度量

一般来说，capacity 越大，会存在overfit的现象，导致Generalization Gap增大；但是对deep learning来说，一般来说并不容易overfit（有时也会）。如：

1、圆圈的面积单表params的规模，面积越大，params越多，可以看出往往是params越多的network往往表现的更好。[AN ANALYSIS OF DEEP NEURAL NETWORK MODELS FOR PRACTICAL APPLICATIONS](https://arxiv.org/pdf/1605.07678.pdf)

![3-1](https://github.com/haoyuheng/MLDS_notebook/blob/master/assets/3-1.png?raw=true)

2、对fully connected network来说，layer越多，params越多，但由下图可知层数增加时并未存在overfit的情况。[Towards Understanding Generalization of Deep Learning: Perspective of Loss Landscapes](https://arxiv.org/pdf/1706.10239.pdf)

![3-2](https://github.com/haoyuheng/MLDS_notebook/blob/master/assets/3-2.png?raw=true)

3、Google Brain的文章，从下图可以看出，Number of weights增大的时候gap的最小值并不会降低。[SENSITIVITY AND GENERALIZATION IN NEURAL NETWORKS: AN EMPIRICAL STUDY](https://arxiv.org/pdf/1802.08760.pdf)

![3-3](https://github.com/haoyuheng/MLDS_notebook/blob/master/assets/3-3.png?raw=true)

**Concluding Remarks**

• The capacity of deep model is large.

• However, it does not overfit!

• The reason is not clear yet.

### 3.2		Indicator of Generalization

#### Sensitivity

**Definition**: Given a network 𝑓, the sensitivity of a data point x is the Frobenius norm of the Jacobian.

![3-4](https://github.com/haoyuheng/MLDS_notebook/blob/master/assets/3-4.png?raw=true)

Sensitivity of x is：![3-5](https://github.com/haoyuheng/MLDS_notebook/blob/master/assets/3-5.png?raw=true)

It is not surprise that sensitivity is related to generalization.

Sensitivity 直观上是x变化对y的变化的影响，Sensitivity越大，𝑓在x点陡峭，y的变化越大；反之，Sensitivity越小，𝑓在x点平滑，y的变化越小。

**Regularization** is kind of minimizing sensitivity.

Regularization可以平滑𝑓。

对一个训练好的model，在training data附近的Sensitivity会比较小，反之在training data没有出现的地方Sensitivity较小。（还是参照Google Brain关于Sensitivity的文章）

1、如下图，黑色代表一个随机的椭圆函数，并不经过任何training data，Sensitivity在每个点都较高。而红色椭圆在经过了training data的三个点，Sensitivity较低。

![3-6](https://github.com/haoyuheng/MLDS_notebook/blob/master/assets/3-6.png?raw=true)

2、比较了training前后，model的Sensitivity分布，可见在有training data的位置，训练后model的Sensitivity较小，model比较平滑。图中色块的大小可以理解为Relu 网络piecewise的长度，色块越大，越平滑。

![3-7](https://github.com/haoyuheng/MLDS_notebook/blob/master/assets/3-7.png?raw=true)

**A strong relationship between the Jacobian norm and generalization**.

从下图可以看到一般情况下， Jacobian norm 越小，Generalization gap越小。

![3-8](https://github.com/haoyuheng/MLDS_notebook/blob/master/assets/3-8.png?raw=true)

#### Sharpness

我们把minima分为Flat Minima和Sharp Minima，从下图可以直观的看出，Flat Minima处具有好的Generalization（Training Loss和Testing Loss的Gap较小），而Sharp Minima对应与bad Generalization.

![3-9](https://github.com/haoyuheng/MLDS_notebook/blob/master/assets/3-9.png?raw=true)

那么如何定义一个点的Sharpness呢？

**Definition of Sharpness**

![3-10](https://github.com/haoyuheng/MLDS_notebook/blob/master/assets/3-10.png?raw=true)

**Batch Size**

一般来说，Batch Size 越小，Generalization效果越好。

![3-11](https://github.com/haoyuheng/MLDS_notebook/blob/master/assets/3-11.png?raw=true)

**Batch Size v.s. Sharpness**

可以看出，随着batch size增大，Sharpness也会增大，而Generalization的效果变差。

![3-12](https://github.com/haoyuheng/MLDS_notebook/blob/master/assets/3-12.png?raw=true)

**Concluding Remarks**

• Good generalization are associated with sensitivity

• Good generalization are associated with flatness (?)

• Understanding the indicator for generalization helps us develop algorithm in the future
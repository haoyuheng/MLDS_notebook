## Generalization（泛化）

### Generalization Ability

**Generalization Gap**:  difference between training error and testing error

**Capacity of model**: "size" of the your model, 也可以理解为model的parameter的规模，可以使用VC维来度量

一般来说，capacity 越大，会存在overfit的现象，导致Generalization Gap增大；但是对deep learning来说，一般来说并不容易overfit（有时也会）。如：

1、圆圈的面积单表params的规模，面积越大，params越多，可以看出往往是params越多的network往往表现的更好。[AN ANALYSIS OF DEEP NEURAL NETWORK MODELS FOR PRACTICAL APPLICATIONS](https://arxiv.org/pdf/1605.07678.pdf)

![3-1](/home/MLDS_notebook/assets/3-1.png)

2、对fully connected network来说，layer越多，params越多，但由下图可知层数增加时并未存在overfit的情况。[Towards Understanding Generalization of Deep Learning: Perspective of Loss Landscapes](https://arxiv.org/pdf/1706.10239.pdf)

![3-2](/home/MLDS_notebook/assets/3-2.png)

3、Google Brain的文章，从下图可以看出，Number of weights增大的时候gap的最小值并不会降低。[SENSITIVITY AND GENERALIZATION IN NEURAL NETWORKS: AN EMPIRICAL STUDY](https://arxiv.org/pdf/1802.08760.pdf)

![3-3](/home/MLDS_notebook/assets/3-3.png)

**Concluding Remarks**

• The capacity of deep model is large.
• However, it does not overfit!
• The reason is not clear yet.

### Indicator of Generalization

#### Sensitivity

**Definition**: Given a network 𝑓, the sensitivity of a data point x is the Frobenius norm of the Jacobian.

![3-4](/home/MLDS_notebook/assets/3-4.png)

Sensitivity of x =![3-5](/home/MLDS_notebook/assets/3-5.png)

#### Sharpness

**Concluding Remarks**

• Good generalization are associated with sensitivity
• Good generalization are associated with flatness (?)
• Understanding the indicator for generalization helps us develop algorithm in the future
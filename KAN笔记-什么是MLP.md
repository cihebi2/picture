![neuronalen Netzes ](https://cdn-images-1.medium.com/max/800/0*aBzfwk6V8U2kJqGd)

我所理解的深度学习网络如同这张图片，输入一个数组，表示为Input Layer，经过一系列的数值运算，表示为Hidden Layer，最后输出想要的结果，表示为Output Layer。

![局部神经元](https://cdn-images-1.medium.com/max/800/1*U6tiIuizR8PMkrOuqyH5vg.png)

其中的细节如上图，每一个圆圈，称之为神经元，两个神经元之间的每个连接都由一个数值表示，我们称之为权重。

两个神经元之间的每个连接都是通过不同的权重 $w$ 实现的。这些权重中的每一个$w$都有两个下标，下表的第一位数字表示连接来源的层中的神经元标签，下标的第二个数字表示连接所指向的层中的神经元标签。

![权重矩阵](https://cdn-images-1.medium.com/max/800/0*ebwG9bWKzhgZ0OLW)

神经网络中两层之间的所有权重都可以由称为神经网络的矩阵确定。称为权重矩阵，而所谓的训练就是找到合适的权重矩阵。

![前向传播](https://cdn-images-1.medium.com/max/800/0*TyR7iGDsl3AuEmq6)

对于给定的输入向量 $\vec{x}$，神经网络计算输出或预测向量，这里将其称为 $\vec{h}$，

![前向传播方程](https://cdn-images-1.medium.com/max/800/0*LYoM4KMv_Y46Ko2c)

这里计算输出的步骤也称为向前传播。为此，需要计算输入向量 $\vec{x}$ 和连接两个神经元层的权重矩阵 $W$ 之间的乘积。

这里最终输出或预测向量 $\vec{h}$ 是通过对向量 $\vec{z}$ 应用所谓的激活函数来获得的。这里激活函数由字母 $\sigma$ 表示。激活函数只是一个非线性函数，它执行从 $\vec{z}$ 到 $\vec{h}$， $\sigma ： z \mapsto h$ 的非线性映射。

深度学习中使用了 3 个激活函数。它们是：tanh、Sigmoid 和 ReLu。

比如ReLU就可以如下表示。小于0就是0，大于0就保持原样，所用用了ReLU有些权重就直接pass，也方便模型训练。

非线性的激活函数带给模型非线性的表示，可以学习到一些更有趣且隐藏了的表示。

![ReLu函数](https://miro.medium.com/max/651/1*j-9JXINdtfwKdudGoJ8rxw.png)

![神经网络](https://miro.medium.com/max/875/0*AONVmd3v4wO_dWr6)

将许多的神经元连接起来，计算输入 $\vec{x}$ 和第一个权重矩阵 $W_1$ 之间的乘积，并对结果向量应用激活函数以获得向量 $\vec{h}_1$。$\vec{h}_1$ 再表示为第一个隐藏层中神经元的值，并作为下一个隐藏层的输入。重复上述过程，直到我们从网格中得到最终输出 $\vec{y}$

![正向传播方程](https://cdn-images-1.medium.com/max/800/0*LrkPxaZxvdyOp9OY)

再通过损失函数计算最终输出 $\vec{y}$和真实标签的差距，用优化器调节权重的大小，不断重复，这一过程称为反向传播，最后得到一个较好的权重矩阵，就是我们所说的模型。



当然，这样的说法过于粗糙，实际上的需要考虑的问题有很多。比如输入的 $\vec{x}$ 是一段文字或图片或音频，就需要特征工程，表示为模型可以理解的数值形式。模型的架构也有很多的变体，如常用于图片的卷积神经网络，用于文字的循环神经网络。根据最后的输出，可以有预测真假的二分类问题，或多分类问题，预测某一连续数值的回归问题，还有生成模型、扩散模型等等。

现有的模型大都是建立在Multilayer Perceptron (MLP)之上，又被称为多层感知机。以前选择这个模型有部分是因为它的架构比较简单，可以不断堆叠，适合那时候不太发达的硬件。

而现在有了一个新的网络架构--KAN(Kolmogorov-Arnold Networks)，一个还很粗糙，效率低下，但很有潜力的新范式。

资料来源：

[什么是深度学习？ - AI教程 (artemoppermann.com)](https://artemoppermann.com/de/was-ist-deep-learning/)

[[2404.19756\] KAN：Kolmogorov-Arnold 网络 (arxiv.org)](https://arxiv.org/abs/2404.19756)

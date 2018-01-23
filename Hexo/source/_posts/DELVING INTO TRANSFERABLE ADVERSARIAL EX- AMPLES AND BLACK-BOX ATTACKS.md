title: DELVING INTO TRANSFERABLE ADVERSARIAL EX- AMPLES AND BLACK-BOX ATTACKS

tags: 
- 对抗样本

categories:
- 论文

------
## 贡献

研究目标和非目标攻击，转移性在非目标攻击时更容易发生
用已有的方法进行目标攻击时，几乎没有转移性
提出基于集成的方法生成对抗样本，这样在进行目标攻击时可提高攻击成功率。

<!--more-->
此前转移性只在小的数据集，如MNIST (LeCun et al. (1998)) and CIFAR-10 (Krizhevsky & Hinton (2009))中进行试验，本论文在在大规模数据集，ImageNet (Russakovsky et al. (2015))进行试验

不同模型的梯度方向是正交的，决策边界是对齐的

攻击了Clarifai.com, a commercial com- pany providing state-of-the-art image classification services


转移性的研究：（1）在同样数据集的不同模型间 （2）相同模型在不相交的数据集上 （3）不同模型在不同数据集上

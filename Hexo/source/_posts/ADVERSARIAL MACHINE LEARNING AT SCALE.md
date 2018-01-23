
title: ADVERSARIAL MACHINE LEARNING AT SCALE

tags:

- 论文集
- 对抗样本

categories:

- 论文


------
## 摘要

<!--more-->
## 贡献
比较了多种攻击方式构造的对抗样本在更大的数据集（imageNET ）上的实验结果，

单步攻击方法比多步攻击方法更具转移性
 
解决标签泄露问题

focusing on the question of how well adversarial examples transfer between different types of models, while we focus on defenses and studying howwell different types of adversarial example generation procedures transfer between relatively similar models

标签泄露是指如果分类器正确分类了由使用正确标签构造的对抗样本但是错分了相应的没有使用标签构造的对抗样本，这就说明有了标签泄露。
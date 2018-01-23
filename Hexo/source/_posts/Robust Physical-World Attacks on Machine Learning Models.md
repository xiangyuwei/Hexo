
title: Robust Physical-World Attacks on Machine Learning Models

tags:
- 对抗样本

categories:
- 论文
------

最近的研究中，许多对抗样本构造方法在真实自然世界效果不好。已有的对抗攻击研究在现实世界中，往往不能使分类模型误分类，或者只在非常有限的情况比如复杂原始图像经修改后打印出来才能达到对抗攻击的目的。
<!--more-->
 本论文要点如下：
1. 提出Robust Physical Perturbations(RP2)算法，能产生鲁棒且自然有效的对抗扰动。
2. 使用RP2算法用两种方式构造对抗攻击：
-- subtle perturbations：对整个标志进行微小的、很难探测到的改动。把整个受到攻击后的图片打印后覆盖到原标志上面，尺寸和原图一样。
-- camouflage perturbations：以涂鸦或艺术画的形式对原图进行可见的改变。攻击者直接将扰动攻击打印出来，然后贴到已经存在的标志上面。
3. 因为目前缺乏衡量自然界对抗攻击效果的标准方法，因此论文提出了一种评估方法。

数据集：LISA数据集，包含47种不同的路标图片，在本实验中重设尺寸为32×32

https://www.zybuluo.com/wuxin1994/note/839621
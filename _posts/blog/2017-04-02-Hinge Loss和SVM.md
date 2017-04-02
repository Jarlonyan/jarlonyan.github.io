---
layout: post
title: Hinge Loss和SVM
categories: 机器学习
description: 
keywords: Loss和SVM
---


# 1. Hinge Loss
在PRML中，$hinge \, loss$常常用在 $SVM$ 中。数据的真实标签 $y=\pm 1$ 和分类器的分数$f(x)$ . $hinge \, loss$定义如下：
$$\ell(y,f(x))=max \big(0,1-y\cdot f(x) \big)      \tag{1}
$$

$f(x)$是分类器决策函数的原始输出值，而不是类标。
$$f(x)=wx+b    \tag{2}
$$
可以看出，当$y$和$f(x)$有相同的符号时，意味着$f(x)$预测出正确的分类，这时$\left| f(x) \right| \geq 1 $

+ SVM得到的模型是：
$$f(x)=\sum_{i=1}^m{\alpha_i \cdot y_i \cdot x_i^T \cdot x + b}     \tag{3}
$$

+ SVM预测

$$\begin{cases}
        f(x)\geq 0, 正类 \\
        f(x)< 0, 负类
\end{cases}   \tag{4}$$


# 2. SVM、软间隔和正则化

+ loss function

$$\ell(y,f(x))=max(0,1-y\cdot f(x))     \tag{5}
$$

+ SVM总的损失：
$$
\sum_{i=1}^m{max \big\{ {0, 1-y_i(wx_i+b)}  \big\} }     \tag{6}
$$

+ SVM优化目标：

$$
\frac{1}{2} \lVert w \rVert ^2 + C \cdot \sum_{i=1}^m{max \big\{ {0, 1-y_i(wx_i+b)}  \big\} }    \tag{7}
$$

+ 引入松弛变量:
引入松弛变量$\epsilon_i$，重写上面式子，
$$\min \limits_{w,b,\epsilon} \big\{ { \frac{1}{2} \lVert w \rVert ^2 + C \cdot \sum_{i=1}^m{ \epsilon_i }} \big\} \\
s.t. \quad y_i(w^T x_i +b) \geq 1- \epsilon_i \\
\epsilon \geq 0      \tag{8}
$$




<br><br><br><br><br><br><br>
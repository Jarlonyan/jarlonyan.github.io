---
layout: post
title: Logistic Regression推导
categories: 机器学习
description: 
keywords: Logistic Regression
---


# 1.已知
+ 假设样本 $x$ 是正样本的概率：
$$p(y=1|x) = \frac{1}{1+e^{-(wx+b)}}
\tag{1}$$

+ 将上面这个 $sigmoid$ 函数看做是 $f(x)$ 
这个$f(x)$特点:
  
$$f^{'}(x)=f(x)\cdot \big( 1-f(x) \big)
\tag{2}$$

+ $loss \, function$:
$$\ell(y, p(y|x))=-\log{p(y|x)}
\tag{3} $$ 

# 2. 推导过程

+ 上面的 $loss \, function$ 等价于
$$\ell(y, p(y|x))=\begin{cases}
            -\log{p(y=1 \big| x)}, \qquad y=1 \\
            -\log{\left[ 1-p(y=1\big| x) \right] }, y=0
            \end{cases}
\tag{4}$$

+ 将上面的式子写成一个式子
  
$$\ell(y, p(y|x))=-y\cdot{\log{p(y=1\big| x)}}-(1-y)\cdot{\log{\left[ 1-p(y=1\big| x)\right]}}
\tag{5}$$

+ 训练集的总的代价：

$$\begin{alignat}{2}
J(w)&=\sum_{i=1}^m {\ell(y_i,p(y_i\big| x_i))}  \\
&=\sum_{i=1}^m {-y_i\cdot{\log{p(y_i=1\big| x_i)}}-(1-y_i)\cdot  \log{\left[ 1-p(y_i=1\big| x_i)\right]}}\\
\end{alignat}
\tag{6}$$

+ 为了简单起见，公式中的 $x$ ，$w$ 用增广向量表示，用 $f(wx)$ 来表示 $p(y=1|x)$ 。那么：
  
$$J(w)=\sum_{i=1}^m{-y_i\cdot \log{f(w \cdot x_i)}-(1-y_i)\cdot  \log{\left[ 1-f(w \cdot x_i)\right]}}
\tag{7}$$

+ 对式子关于$w$求导：

$$\begin{align*}
\frac{ \partial J(w)}{ 
\partial w} & =\frac{ \partial\left\{ { \sum_{i=1}^m{-y_i\cdot \log{f(w \cdot x_i)}-(1-y_i)\cdot  \log{\left[ 1-f(w \cdot x_i)\right]}} } \right\}}{ \partial w}	\tag{8} \\
&	=\sum_{i=1}^m {-y_i\cdot {(1-f(w \cdot x_i))}\cdot x_i -(1-y_i)\cdot (-1) \cdot f(w \cdot x_i) \cdot x_i }	\tag{9} \\
&	=-\sum_{i=1}^m { x_i \big\{ { y_i \cdot (1-f(w \cdot x_i))-(1-y_i \cdot f(w \cdot x_i) }) \big\} } \tag{10} \\
&	=-\sum_{i=1}^m { x_i \big\{ { y_i-f(w \cdot x_i) } \big\} } 
\tag{11}	
\end{align*}$$


# 3. 求解方法

## 3.1 梯度下降法

$$w=w-\eta \cdot \frac{\partial J(w)}{\partial w}
\tag{12}$$

## 3.2 牛顿法

$$w=w-\eta \cdot \frac{ J^{'}(w)}{ J^{''}(w)}=w-\eta \cdot \frac{\partial ^ 2 J(w)}{ \partial w \cdot \partial w^{T}  }  \tag{13}
$$


<br><br><br><br><br><br><br>






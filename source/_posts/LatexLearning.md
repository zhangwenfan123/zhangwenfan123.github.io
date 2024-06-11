---
title: Latex for Hexo Markdown Engine
date: 2020-05-13
tags: Latex_Learning
category: Software Engineering
excerpt: 本文主要对Latex在Markdown中的渲染语法进行学习和熟悉,包含基础得希腊字母及其变体、公式得上下标处理、分式和根式表达、数学运算符、大型运算符、函数/方程及矩阵得表达等。
author: Zhang Wenfan
authorURL: 
url: 
copyrightText: 
comment: true
---

### 本文主要对Latex在Markdown中的渲染语法进行学习和熟悉

+ **第一部分:希腊字母基础表达**

```latex
$$
\delta, \lambda\\
\Delta, \Lambda\\
\alpha, \beta\\
\phi,\varphi--正常phi和变体phi \\
\epsilon,\varepsilon\\
\pi,\Pi--首字母大写，对应希腊字母也大写\\
$$
```
**实际渲染效果如下**
$$
\delta, \lambda\\
$$

$$
\Delta, \Lambda\\
$$

$$
\alpha, \beta\\
$$

$$
\phi, \varphi--正常phi和变体phi\\
$$

$$
\epsilon, \varepsilon--正常epsilon和变体epsilon\\
$$

$$
\pi, \Pi--首字母大写，对应希腊字母也大写\\
$$

+ **第二部分：公式上下标处理**
```latex
$$
a^2,a_1,\\
x^{y+z},p_{ij}\\--用大括号包裹多项式\\
$$
$$
x_i,x_{\rm i},x_{\text i}--下标是斜体还是直立体的i\\
$$
$$
\text{A B},\rm{A B}--text和rm的区别\\
$$
$$
\text A B,\rm A B--text和rm对后面的作用域区别
$$
$$
{\rm A} B--注意LaTeX里面是用大括号而不是小括号作为作用域的\\
$$
$$
\text{e},\text{i}--常量e,i建议用直立体的字母\\
$$

```

$$
a^2,a_1,\\
x^{y+z},p_{ij}\\--用大括号包裹多项式\\
$$
$$
x_i,x_{\rm i},x_{\text i}--下标是斜体还是直立体的i\\
$$
$$
\text{A B},\rm{A B}--text和rm的区别\\
$$
$$
\text A B,\rm A B--text和rm对后面的作用域区别
$$
$$
{\rm A} B--注意LaTeX里面是用大括号而不是小括号作为作用域的\\
$$
$$
\text{e},\text{i}--常量e,i建议用直立体的字母\\
$$

+ **第三部分：分式和根式的表达**

```latex
$$
分式：\\
--语法为  \frac{分子} {分母}
\frac{1} {2}, \frac1 2 \\
\frac{1} {x+y} \\
\frac{\frac1 x + 1} {y+1}--嵌套分式\\
\frac{\dfrac1 x + 1} {y+1}\\
--分子中的1/x较小，改为dfrac(display-style)调整格式\\
----------------------\\
根式:\\
--语法为  \sqrt[根指数-开n次方根]{根底数}
\sqrt 2,\sqrt{x+y}\\
\sqrt[n]{2}---n次方根
$$
```
$$
分式：\\
--语法为  \frac{分子} {分母} 
$$
$$
\frac{1} {2}, \frac1 2 \\
\frac{1} {x+y} \\
$$
$$
\frac{\frac{1} x + 1} {y+1}--嵌套分式\\
$$
$$
\frac{\dfrac1 x + 1} {y+1}\\
--分子中的1/x较小，改为dfrac(display-style)调整格式\\
$$
$$
根式:\\--语法为  
\sqrt[根指数-开n次方根]{根底数}  
$$
$$
\sqrt 2,\sqrt{x+y}\\
$$
$$
\sqrt[n]{2}---n次方根
$$

+ **第四部分：数学运算符**

```latex
$$
+,-,\times,\cdot,\div,\pm,\mp,\\
$$
$$
\ge,\le,\gg,\ll,\ne,\approx,\equiv,>,<
$$
$$
\cap,\cup,\in,\notin,\subseteq,\subsetneq,\subsetneqq,\varnothing\\
$$
$$
\forall,\exists,\nexists,\because,\therefore\\
$$
$$
\mathbb R,\mathbb N,\mathbb Z \\
$$
$$
\mathcal F,\mathscr F\\
$$
```
$$
+,-,\times,\cdot,\div,\pm,\mp,\\
$$
$$
\ge,\le,\gg,\ll,\ne,\approx,\equiv,>,<
$$
$$
\cap,\cup,\in,\notin,\subseteq,\subsetneq,\subsetneqq,\varnothing\\
$$
$$
\forall,\exists,\nexists,\because,\therefore\\
$$
$$
\mathbb R,\mathbb N,\mathbb Z \\
$$
$$
\mathcal F,\mathscr F\\
$$

+ **第五部分：特殊运算符和函数**

```latex
$$
\cdots,\vdots,\ddots\\
\infty,\partial,\nabla,\propto,\degree\\
---------------\\
\sin x,\sec x,\cosh x\\
\log_2 x,\ln x,\lg x\\
---------------\\
\lim_{x \to 0} \frac {sinx} {x}\\
\lim\limits_{x \to 0} \frac {sinx} {x}\\
加入limits，则x \to0的角标在lim的下方
$$
```

$$
\cdots,\vdots,\ddots\\
$$
$$
\infty,\partial,\nabla,\propto,\degree\\
$$
$$
\sin x,\sec x,\cosh x\\
$$
$$
\log_2 x,\ln x,\lg x\\
$$
$$
\lim_{x \to 0} \frac {sinx} {x}\\
$$
$$
\lim\limits_{x \to 0} \frac {sinx} {x}\\
加入limits，则x \to0的角标在lim的下方
$$

+ **第六部分：大型运算符**

```latex
$$
\sum,\prod\\
\sum_{i=0}^N,\prod_{i=0}^N\\
\frac{\sum_{i=0}^N} {\prod_{i=0}^N}\\
这里上下限均现实在求和求积的右侧的，如果想显示在上下侧需要加入limits限定如下\\
\frac{\sum\limits_{i=0}^N} {\prod\limits_{i=0}^N}\\
----------------------\\
\int,\iint,\iiint\\
\oint,\oiint\\
\int_{-\infty}^0 f(x)dx\\
但在严谨场合dx中的d为直立体，且与被积函数应该拉开一段小间隔)\\
\int_{-\infty}^0 f(x) \, \text dx\\
$$
```
$$
\sum,\prod\\
$$
$$
\sum_{i=0}^N,\prod_{i=0}^N\\
$$
$$
\frac{\sum_{i=0}^N} {\prod_{i=0}^N}\\
$$
$$
这里上下限均现实在求和求积的右侧的，如果想显示在上下侧需要加入limits限定如下\\
$$
$$
\frac{\sum\limits_{i=0}^N} {\prod\limits_{i=0}^N}\\
$$
$$
\int,\iint,\iiint\\
\oint, 
此处二重围道积分无法正确渲染，问题待解决
\oiint\\
$$
$$
\int_{-\infty}^0 f(x)dx\\
但在严谨场合dx中的d为直立体，且与被积函数应该拉开一段小间隔)\\
$$
$$
\int_{-\infty}^0 f(x) \, \text dx\\
$$

+ **第六部分：标注符号、箭头、定界符**

```latex
$$
标注符号：\\
\vec x,\overrightarrow x,\overrightarrow {AB}  --上面一个右箭头\\
\bar x,\overline x,\overline {AB} --上面一个横线\\
---------------\\
箭头：\\
\leftarrow,\rightarrow--单箭头\\
\Leftarrow,\Rightarrow--双箭头\\
\Leftrightarrow,\longleftarrow\\
---------------\\
括号和定界符：\\
(),[],\{\} \\
大括号的左右括号要加转义\\
\lceil,\rceil,\lfloor,\rfloor,||\\
(0,\frac 1 a] \\
高度自适应的括号：\\
\left(0,\frac 1 a \right]\\
为了自适应竖线，构造了虚拟的左括号：\\
\left.\frac {\partial f} {\partial x}\right|_{x=0}\\
$$
```

$$
标注符号：\\
\vec x,\overrightarrow x,\overrightarrow {AB}  --上面一个右箭头\\
$$
$$
\bar x,\overline x,\overline {AB} --上面一个横线\\
$$
$$
箭头：\\
\leftarrow,\rightarrow--单箭头\\
$$
$$
\Leftarrow,\Rightarrow--双箭头\\
$$
$$
\Leftrightarrow,\longleftarrow\\
$$
$$
括号和定界符：\\
(),[],\{\} \\
$$
$$
大括号的左右括号要加转义\\
\lceil,\rceil,\lfloor,\rfloor,||\\
(0,\frac 1 a] \\
$$
$$
高度自适应的括号：\\
\left(0,\frac 1 a \right]\\
$$
$$
为了自适应竖线，构造了虚拟的左括号：\\
\left.\frac {\partial f} {\partial x}\right|_{x=0}\\
$$

+ **第七部分：多行公式和矩阵**

```latex
$$
f(x)=
\begin{cases}
\sin x,-\pi\le x \le \pi\\
0,\text{其他}
\end{cases}
$$
$$
\begin {matrix}
a & b & \cdots & c\\
\vdots & \vdots & \ddots & \vdots\\
e & f & \cdots & g\\
\end {matrix}
$$
$$
\begin {bmatrix}
a & b & \cdots & c\\
\vdots & \vdots & \ddots & \vdots\\
e & f & \cdots & g\\
\end {bmatrix}
$$
$$
\begin {pmatrix}
a & b & \cdots & c\\
\vdots & \vdots & \ddots & \vdots\\
e & f & \cdots & g\\
\end {pmatrix}
$$
$$
\begin {vmatrix}
a & b & \cdots & c\\
\vdots & \vdots & \ddots & \vdots\\
e & f & \cdots & g\\
\end {vmatrix}
$$
```

$$
f(x)=
\begin{cases}
\sin x,-\pi\le x \le \pi\\
0,\text{其他}
\end{cases}
$$

$$
\begin {matrix}
a & b & \cdots & c\\
\vdots & \vdots & \ddots & \vdots\\
e & f & \cdots & g\\
\end {matrix}
$$

$$
\begin {bmatrix}
a & b & \cdots & c\\
\vdots & \vdots & \ddots & \vdots\\
e & f & \cdots & g\\
\end {bmatrix}
$$

$$
\begin {pmatrix}
a & b & \cdots & c\\
\vdots & \vdots & \ddots & \vdots\\
e & f & \cdots & g\\
\end {pmatrix}
$$

$$
\begin {vmatrix}
a & b & \cdots & c\\
\vdots & \vdots & \ddots & \vdots\\
e & f & \cdots & g\\
\end {vmatrix}
$$

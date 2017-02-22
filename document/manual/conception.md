---
title: 相关概念
layout: page
---
## 数字图像处理基本概念

* ### 图像概念
数字图像处理中所指的图像，确切地说叫光栅图，是点阵构成的，所以也称之为点阵图或位图（bit map），它的大小又深度和尺寸决定。

* ### 尺寸
构成图像的点阵的行数和列数，这决定了图像对空间细节的表现能力，所以也称之为分辨率。

* ### 格式，深度
每个点阵的数据类型，如每个点是一个[0,255]的整数，是一个小数...每种数据类型在计算机中占特定的位，我们称单个像素所占的位称为图像的深度，这决定了单个点的信息描述能力，因此有些时候深度也称之为色彩分辨率。

* ### 通道
对于一些图像（比如彩色图像），包含了多个尺寸相同的点阵，我们称每个单一层为一个通道，这些通道各自描述了图像的某个维度的信息，只有合成之后，才是完整的。

* ### 存储格式
位图是一个一个的点数据，因此占据大量的存储空间，因而存储时可以对其进行压缩，由不同的原理得到的各种算法，就形成了存储格式，常见的有 Bmp(未压缩), jpg, png, tif等，不同与位图，他们的存储大小除了尺寸，还取决与像素的内容，不过无论采用什么压缩格式，在进行数字图像处理时，往往要先解压缩，在内存中形成位图。
**注：与像素数据格式是两个概念**

## ImagePy 用到的一些概念
* ### 图像栈
一些有相同尺寸，相同格式的图像构成的图像序列，称之为图像栈。ImagePy 中图像栈分为连续栈和列表栈，其中列表栈支持随时动态添加，删除图像，连续栈则不可以。但一些三维滤波器则必须在连续栈上才能运行。二者可以转换。

* ### 索引色
对于灰度图像，有时会通过特定的映射关系，把它映射成彩色。这的确增强了图像的肉眼可判读性，但并没有增加其包含的信息量，因而有时也称之为假彩色。
![](http://home.imagepy.org/manual/idxcolor.png "index color")

* ### 选区
顾名思义，它只是用于指定图像的一块区域，自身并没有什么作用，只是为其他的操作指明目标。在 ImagePy 里，选区是指一个叠加在图像上的矢量图形，可以是点，线，面，镂空多边形。
![](http://home.imagepy.org/manual/roisim.png "selection")

* ### 掩膜
一个与图像大小一样，全部像素由 0-1 构成的一张位图。类似与选区，但掩膜更直接地指明某个像素是否处于被选中状态，这有助于一些相关操作。（掩膜可以由选区填充而得到）

* ### 标记
是一个叠加在图像上的可绘制的一个层，可以是适量图形，位图，文字等，标记不对图像产生任何作用和影响，仅仅用于提示人。
---
layout: post
title:  "[project][title]"
date:   2021-04-25
categories: Git 
tags: git linux
excerpt:  
mermaid: true
author: Huaixu
---
* content
{:toc}


# 重构之如何学
# 重构之如何整理

> 重构（refactoring）
> 百度百科定义为：通过调整代码，改善代码质量、性能，使其程序的设计模式和架构更趋合理化，提高软件的扩展  
> 从字面来看，这是从代码的角度来看，但如果扩充到其他的，似乎有一定的内连，于此，从我的角度重新定义  
> ：通过调整知识🕸️,改善知识的网络、  ，使其架构更紧凑，更趋合理化，提高扩展。  
>

## 思路的起源
### 1.最大的数
《从一到无穷大》书中讲述了一个原始部落的故事：两个酋长要比一比谁说的数字大，一个酋长想了想，先说了“3”，第二个酋长想了半天，说你赢了。  
因为在原始部落，物资机器缺乏，很少超过3，他们就称之为“许多”或者叫不清楚。
### 2.不同文字系统记录信息的能力是等价的
这里所说的文字系统包括但不限于 汉字，英语，数字。**恩对，包括数字**。
### 3.文字系统的体量不会随文化的发展一直增加
最早刻有埃及象形文字的文物的年代大约是公元前32世纪，那个时期的象形文字数量大约只有500个，但是到了公元前5-7世纪（主要是“希腊-罗马时代”），埃及象形文字的数量增加到了5000个左右，与中国常用汉字数量相当。然而随着文明的进步，信息量的增加，埃及的象形文字数量便不再随着文明的发展而增加了，因为没有人能够学会和记住那么多的文字。于是，概念的第一次概括和归类就开始了。在中国的象形文字中，“日”本意是太阳，但它同时又是太阳从东升起到落山再到升起的时间周期，也就是我们讲的一天。
### 4.至简至恒
文字出现在远古“信息爆炸”导致人们的头脑装不下这些信息的时候；数字出现在人们的财产多到需要数一数才搞清楚有多少的时候。  
从原先的一，二，三分别代表1，2，3，这是萌芽，再到后来的进制的出现，这是革新，也是必经之路（从有限，散乱到无限有规律的变革）  
十进制，来源于我们的双手指数，但我想这不是巧然，更像是必然。就像人人熟耳的九九乘法表，但是如果是20进制，那便有19×19表，那显然不太愉快，（玛雅文明使用的是20进制，也很发达且影响深远，但是不易爆发，或许就是因为入门的门槛提升了。对于初中才能勉强会背九九乘法表的我，若是我们使用的是19×19乘法表，那我想我的学业生涯也就停止在初中了。）  

### 5.记忆的遗忘
填鸭式教育带来一定记忆的锻炼，使得我们在18岁的年纪，记住了天文，知晓了数理。但随着时间的流逝，它们也在渐隐，是我们的记忆在退化吗？我想答案是否定的。  
比如，此刻你能说出几种白色的物体？比如，雪，牛奶。。。  
但如果询问如何堆雪人呢？  
这两个问题除了字面的差别，有一层差别在于，前者答案是点，后者答案是线。

## 基向量+万物皆对象
> 这是我思考出来的重构的具体思路，大致为两点：  
> 基向量：一个系统的基础、框架，命名来源于欧几里得空间（三维坐标空间）的xyz基向量。比如拉丁语系中的a-z，阿拉伯数字中的0-9等等都算作其体系中的基向量。  
> 万物皆对象：把具体的，不同的事物，抽象成统一的对象。命名来源于面向对象编程，那是把其他的都抽象成对象，来操作一个对象就好了，比如把文件抽象成对象，这样知道了如何操作对象之后，同样的把设备抽象成对象之后便能旁通。比如linux的一切皆文件，把鼠标，键盘等一切抽象为文件，操作相应的文件进行修改就能模拟指定的动作，这样需要学的只是对文件的操作，便能解决其他。而不需要鼠标学一次，键盘学一次。

## 基向量
> 百度百科定义:在线性代数中，基(basis)（也称为基底）是描述、刻画向量空间的基本工具。向量空间的基是它的一个特殊的子集，基的元素称为基向量。  
> 个人定义：在一门知识体系中，其最小构成单位或最基本公理，例如：三维空间中的基向量、力学中的牛顿三定理、英语的26个字母等等。  

### 性质
  *  稳定性  
     基底的选择首先必须是稳定，比如0-9数字的，无限的始于此，假如这个存在问题，那么影响的将会是整个人类的文明。所以选择的首要便是稳定，公理。
  *  简单
     至简至恒。

### 如何寻找基向量
  * 抽象分层
    假如说，你面向的是数学，这个庞大而笼统的词汇，那么毋庸置疑，它的基向量是数字。（我们最最开始接触的数字）；但如果你想要细分到数学中的特定领域，比如高等代数，那么你面向的对象改变了，基向量自然也变成了矩阵。  
    正似计算机网络的OSI七层，每一层对其上一层提供接口。  

## 万物皆对象
> 定义：参考java一切皆对象的理念,和linux一切皆文件的理念。  
> 个人定义:没有定义，说说我对linux一切皆文件的感触。

### 性质
 * 抽象
     每门知识大抵相同，抽象成what why how  
 * 互通
     

### 如何寻找对象
 * 封装

## 应用（apply）
  * 高数
    - 基向量：函数
    - 万物皆对象
        - 属性：连续、极限、导、微分、积分
        - 方法：求是否连续，某点极限。。。。。

  * 数据结构
    - 基向量：数据(每一种结构是一种数据集)
    - 万物皆对象
       - 属性：逻辑结构、物理结构、数据运算
       - 方法：遍历数据集，排序数据集，查找数据集中的数据。。。。。

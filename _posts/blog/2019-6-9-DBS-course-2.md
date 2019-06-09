---
layout: post
title: 数据库系统-第二章：关系型数据库
categories: 数据库系统
description: 数据库系统课程笔记
keywords: DBS，课程笔记
---
# 第二章：关系数据库

## 2.1 关系数据结构及形式化定义
1. 关系的定义：D1 * D2 * ... * Dn的子集叫做在域D1，D2，...，Dn上的关系。
2. 一些基本概念
  + 域：一组具有相同数据结构的值的集合
  + 笛卡儿积：所有域的所有取值的一个组合
  + 元组：一行
  + 分量：一行中的一个属性
  + 基数：笛卡儿积的元素的个数
3. 码
  + 候选码（Candidate key）：唯一标识一个元组
  + 全码 (All-key)：所有属性组为候选码，成为全码
  + 主码（Parmary key）：多个候选码中的一个
  + 主属性（Prime attribute）：候选码中的所有属性
  + 非主属性（Non-Prime attribute）：不包含候选码中的所有属性的属性
4. 关系中的三种类型
  + 基本关系：实际存在的表
  + 查询表：查询结构对应的表
  + 视图表：虚表
5. 基本关系的6组性质
  + 列是同质的（Homogeneous）
  + 不同的列可出自同一个域
  + 列的顺序无所谓,，列的次序可以任意交换
  + 任意两个元组的候选码不能相同
  + 行的顺序无所谓，行的次序可以任意交换
  + 分量必须取原子值 **！不能表中嵌表**
6. 关系模式是型，关系是值
7. 关系模式的形式化表示：R（U，D，DOM，F），其中：
  + R       	     关系名
  +	U       	     组成该关系的属性名集合
  +	D       	     U中属性所来自的域
  +	DOM  	     属性向域的映像集合
  +	F        	     属性间数据的依赖关系的集合
8. 关系数据库：所有关系的集合

## 2.2 关系操作
1. 5种基本操作：选择、投影、并、差、笛卡儿积
2. 关系数据库语言的分类
  + 关系代数语言：关系的运算
  + 关系演算语言：谓词逻辑
    + 元组关系演算语言：谓词变元的基本对象是元组
    + 域关系演算语言：谓词变元的基本对象是域  

## 2.3 关系的完整性
1. 分类：实体完整性、参照完整性、用户定义的完整性
2. 实体完整性：主码不能为NULL
3. 参照完整性：
  + **外码（foreign key）** 约束：或者取空值；或者等于S中的某个元组的主码值。

## 2.4 关系代数
1. 分类
  + 传统的集合运算符：并、差、交、笛卡儿积
  + 专门的关系运算符：选择、投影、连接、除
2. 引入的记号
  + 元组的连接：列的连接
  + 象集：某一列的特定值的所拥有的另一列的值，比如学号为XXX的同学所选择的课程。
2. 选择：选择满足条件的若干元组（行）  **！详细例子请见书中例子**
3. 投影：选择若干列 **！详细例子请见书中例子**
4. 连接：不是一个基本运算，可以用笛卡儿积和比较运算结合而成。
  + 等值连接：两个关系的笛卡儿积比较两个属性组相等的若干元组
  + 自然连接：同名的属性组 在结果中去掉重复的列
  + 悬浮元组：在自然元组中被舍弃的元组
  + 外连接：保留悬浮元组在结果中，把缺失属性标记为NULL。
  + 左（右）外连接：只保留左边（右边）关系的悬浮元组
5. 除：元组在 X 上分量值 x 的象集 Yx 包含 S 在 Y 上投影的集合。  
  元组在X 上分量值 x x 的象集Y x 包含S 在Y 上投影的集合，记为：
><a href="https://www.codecogs.com/eqnedit.php?latex=R\div&space;S&space;=&space;\begin{Bmatrix}&space;t_{r}[X]|&space;t_{r}\in&space;R\wedge&space;\prod_{Y}\bigl(\begin{smallmatrix}&space;S&space;\end{smallmatrix}\bigr)&space;\subseteq&space;Y_{X}&space;\end{Bmatrix}{}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?R\div&space;S&space;=&space;\begin{Bmatrix}&space;t_{r}[X]|&space;t_{r}\in&space;R\wedge&space;\prod_{Y}\bigl(\begin{smallmatrix}&space;S&space;\end{smallmatrix}\bigr)&space;\subseteq&space;Y_{X}&space;\end{Bmatrix}{}" title="R\div S = \begin{Bmatrix} t_{r}[X]| t_{r}\in R\wedge \prod_{Y}\bigl(\begin{smallmatrix} S \end{smallmatrix}\bigr) \subseteq Y_{X} \end{Bmatrix}{}" /></a>

  其中<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;Y_{X}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\inline&space;Y_{X}" title="Y_{X}" /></a>为 x 在 R 中的象集， <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;x&space;=&space;t_{r}\begin{bmatrix}&space;X&space;\end{bmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\inline&space;x&space;=&space;t_{r}\begin{bmatrix}&space;X&space;\end{bmatrix}" title="x = t_{r}\begin{bmatrix} X \end{bmatrix}" /></a>。  

## 2.5\*关系演算
  略

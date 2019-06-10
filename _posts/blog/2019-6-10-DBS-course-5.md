---
layout: post
title: 数据库系统-第五章：数据库完整性
categories: 数据库系统
description: 数据库系统课程笔记
keywords: DBS，课程笔记
---
# 第五章：数据库完整性

## 0. 数据的完整性和安全性的联系与区别
+ 防范对象不同
	+ 完整性：不合语义的、不正确的数据
	+ 安全性：非法用户和非法操作

## 1. 实体完整性
+ 主码的约束：唯一且非空

## 2. 参照完整性
+ 外码的约束：被参照表的主码或NULL
+ 违约处理：

| 被参照表 | 参照表 | 违约处理 |
| --- | --- | --- |
| 可能破坏参照完整性 | 插入元组 | 拒绝 |
| 可能破坏参照完整性 | 修改外码值 | 拒绝 |
| 删除元组 | 可能破坏参照完整性 | 拒绝/级联删除/设置为NULL |
| 修改主码值 | 可能破坏参照完整性 | 拒绝/级联删除/设置为NULL |

+ SQL语言：
	+ ON DELETE CASCADE
	+ ON DELETE NO ACTION

## 3. 用户定义的完整性
+ 用户针对 **某一具体应用** 的数据必须满足的语义要求
+ 完整性约束命名子句
	+ CONSTRAINT < 完整性约束条件名>< 完整性约束条件 >
	+ < 完整性约束条件> 包括NOT NULL 、UNIQUE、PRIMARY KEY 短语、FOREIGN KEY 短语、CHECK短语等

## 4. 断言
+ 触发时机：任何对断言中所涉及的关系的操作
+ 语句格式
```
CREATE ASSERTION< 断言名><CHECK子句>
```
+ **例子**：限制数据库课程最多60名学生选修
```
CREATE ASSERTION ASSE_SC_DB_NUM
CHECK (60 >= (select count(*)
/* 此断言的谓词涉及聚集操作count 的SQL 语句*/
From Course,SC
Where SC.Cno=Course.Cno and
Course.Cname =' 数据库')
);
```

## 5. 触发器
+ 触发器（Trigger）是用户定义在关系表上的一类由 **事件驱动** 的特殊过程。
+ 触发器又叫做事件- 条件- 动作（event-condition-action）规则。
	+ 当特定的系统事件发生时，对规则的条件进行检查，如果条件成立则执行规则中的动作，否则不执行该动作。规则中的动作体可以很复杂，通常是一段SQL存储过程。
+ 语法格式
```
CREATE TRIGGER < 触发器名>
{BEFORE | AFTER} < 触发事件> ON < 表名>
REFERENCING NEW|OLD ROW AS< 变量>
FOR EACH {ROW | STATEMENT}
[WHEN < 触发条件>]<触发动作体>
```

+ **例子** ：当对表SC 的Grade 属性进行修改时，若分数增加了10%，则将此次操作记录到下面表中：SC_U （Sno,Cno,Oldgrade,Newgrade）
```
CREATE TRIGGER SC_T
AFTER UPDATE OF Grade ON SC
REFERENCING
OLD row AS OldTuple,
NEW row AS NewTuple
FOR EACH ROW
WHEN (NewTuple.Grade >= 1.1*OldTuple.Grade)
INSERT INTO SC_U(Sno,Cno,OldGrade,NewGrade)
VALUES(OldTuple.Sno,OldTuple.Cno,OldTuple.Grade,NewTuple.Grade)
```

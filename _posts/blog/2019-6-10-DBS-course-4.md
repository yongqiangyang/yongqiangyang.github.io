---
layout: post
title: 数据库系统-第四章：数据库安全性
categories: 数据库系统
description: 数据库系统课程笔记
keywords: DBS，课程笔记
---
# 第四章：数据库安全性

## 1. 数据库安全性概述
+ 数据共享带来数据泄露、更改或破坏
+ 数据库的不安全因素：
  1. 非授权用户对数据库的恶意存取和破坏
  2. 数据库中重要或敏感的数据被泄露
  3. 安全环境的脆弱性
+ 安全标准
  ![text](https://github.com/yongqiangyang/DBS_course/blob/master/picture/%E5%AE%89%E5%85%A8%E6%A0%87%E5%87%86%E7%AE%80%E4%BB%8B.png?raw=true)
  1. TCSEC：美国国防部《可信计算机系统评估准则》
    + 安全级别划分：A1，B3，B2，B1，C2，C1，D七个等级
  2. CC（Common Criteria）通用准则  
    + 分为：EAL1，EAL2，EAL3，EAL4，EAL5，EAL6，EAL7七个准则

## 2. 数据库安全性控制方法
+ 计算机系统的安全模型
![text](https://github.com/yongqiangyang/DBS_course/blob/master/picture/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%B3%BB%E7%BB%9F%E5%AE%89%E5%85%A8%E6%A8%A1%E5%9E%8B.png?raw=true)

+ 数据库管理系统安全性控制模型
![text](https://github.com/yongqiangyang/DBS_course/blob/master/picture/%E6%95%B0%E6%8D%AE%E5%BA%93%E7%B3%BB%E7%BB%9F%E5%AE%89%E5%85%A8%E6%8E%A7%E5%88%B6%E6%A8%A1%E5%9E%8B.png?raw=true)

+ **安全性控制的常用方法**
  1. 用户标识和鉴定
    + 方法：静态口令鉴别、动态口令鉴别、生物特征鉴别、智能卡鉴别
  2. 存取控制
    + 方法：
      1. 自主存取控制（Discretionary Access Control，简称DAC）
      2. 强制存取控制（Mandatory Access Control，简称MAC）
  3. 视图
  4. 审计
  5. 数据加密
+ 自主存取控制方法
  + SQL的GRANT语句和REVOKE语句
  + 数据库角色
+ 强制存取控制方法
  + 引入原因：自主存取控制仅仅通过对数据的存取权限来进行安全控制，而 **数据本身并无安全性标记**
  + 相关概念：
    + 主体：系统中的活动实体，比如 **实际的用户**。
    + 客体：系统中的被动实体，受主体操纵。比如 **文件、基本表、索引、视图**
  + 敏感度标记：绝密（TS）>=机密（S）>=可信（C）>=公开（P）
  + 强制存取控制规则
    1. 仅当主体的许可证级别 **大于或等于** 客体的密级时，该主体才能 **读** 相应的客体。
    2. 仅当主体的许可证级别 **小于或等于** 客体的密级时，该主体才能 **写** 相应的客体。

## 3. 视图
+ 把要保密的数据对无权存取这些数据的用户隐藏起来，对数据提供一定程度的安全保护

## 4. 审计
+ 启用一个审计日志，来监控数据库中的各种行为，找出非法存取数据的操作和人。
+ SQL语句：AUDIT和NOAUDIT语句

## 5. 数据加密
+ 加密方法：存储加密、传输加密

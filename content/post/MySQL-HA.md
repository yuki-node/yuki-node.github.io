---
title: 'MySQL 高可用架构'
date: '2024-11-17T22:58:24+08:00'
draft: false
tags: ['MySQL', '数据库']
keywords: []
author: "Cookie"
---

# 还在看的文章：
- https://developer.aliyun.com/article/1323573
- https://blog.csdn.net/crazymakercircle/article/details/120521986
- https://zhuanlan.zhihu.com/p/679494969
- 

# 前言
PXC：Percona XtraDB Cluster

PXC 特性：
- 同步复制，强一致性、无同步延迟
- 多主复制，任一节点可读可写
- 并行复制，基于行的并行复制
- 强一致性，每个节点都包含完整的数据副本
- 自动添加节点，新节点自动同步全量数据

PXC 限制
- 只支持 INNODB 表
- 不允许大事务的产生
- 写性能取决于最差的节点
- 不能解决热点更新问题


# 架构原理
至少使用 3节点，每个节点都是一个 MySQL Server

# 备份
备份使用

# 还原

# PITR

# Binlog 快速恢复

# 数据库巡检
巡检：主机/OS级别巡检 -> MySQL 巡检 -> 人工/智能分析
## 主机/OS级别巡检
### 主机硬件配置
### CPU/内存/磁盘使用率
### I/O使用情况

## MySQL 巡检
### 备份情况
### 配置
### 用户权限
### Top10 SQL

## 人工智能分析
### 慢 SQL 语句获取
### 优化建议

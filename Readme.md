# MySQL
Begin in 2022/1/23

## 基础篇大纲
1. 数据库概述与MySQL安装篇
   * [第01章：数据库概述](Basic/src/main/sql/数据库概述与MySQL安装/第1章数据库概述/第1章数据库概述.md)
   * [第02章：MySQL环境搭建](Basic/src/main/sql/数据库概述与MySQL安装/第2章MySQL环境搭建/第2章MySQL环境搭建.md)
2. SQL之SELECT使用篇
   * [第03章：基本的SELECT语句](Basic/src/main/sql/SQL之SELECT使用篇/第3章基本的SELECT语句/第3章基本的SELECT语句.md)
   * [第04章：运算符](Basic/src/main/sql/SQL之SELECT使用篇/第4章运算符/第4章运算符.md)
   * [第05章：排序与分页](Basic/src/main/sql/SQL之SELECT使用篇/第5章排序与分页/第5章排序与分页.md)
   * [第06章：多表查询](Basic/src/main/sql/SQL之SELECT使用篇/第6章多表查询/第6章多表查询.md)
   * [第07章：单行函数](Basic/src/main/sql/SQL之SELECT使用篇/第7章单行函数/第7章单行函数.md)
   * [第08章：聚合函数](Basic/src/main/sql/SQL之SELECT使用篇/第8章聚合函数/第8章聚合函数.md)
   * [第09章：子查询](Basic/src/main/sql/SQL之SELECT使用篇/第9章子查询/第9章子查询.md)
3. SQL之DDL、DML、DCL使用篇
   * [第10章：创建和管理表](Basic/src/main/sql/SQL之DDL_DML_DCL使用篇/第10章创建和管理表/第10章创建和管理表.md)
   * 第11章：数据处理之增删改
   * 第12章：MySQL数据类型精讲
   * 第13章：约束
4. 其它数据库对象篇
   * 第14章：视图
   * 第15章：存储过程与函数
   * 第16章：变量、流程控制与游标
   * 第17章：触发器
5. MySQL8 新特性篇
   * 第18章：MySQL8其它新特性

## 高级篇大纲
1. MySQL架构篇
   * 第01章：Linux下MySQL的安装与使用
   * 第02章：MySQL的数据目录
   * 第03章：用户与权限管理
   * 第04章：逻辑架构
   * 第05章：存储引擎
   * 第06章：InnoDB数据页结构
2. 索引及调优篇
   * 第07章：索引
   * 第08章：性能分析工具的使用
   * 第09章：索引优化与SQL优化
   * 第10章：数据库的设计规范
   * 第11章：数据库其他调优策略
3. 事务篇
   * 第12章：事务基础知识
   * 第13章：MySQL事务日志
   * 第14章：锁
   * 第15章：多版本并发控制(MVCC)
4. 日志与备份篇
   * 第16章：其它数据库日志
   * 第17章：主从复制
   * 第18章：数据库备份与恢复

## SQL的分类

DDL:数据定义语言：CREATE \ ALTER \ DROP \ RENAME \ TRUNCATE


DML:数据操作语言：INSERT \ DELETE \ UPDATE \ SELECT （重中之重）


DCL:数据控制语言：COMMIT \ ROLLBACK \ SAVEPOINT \ GRANT \ REVOKE
   
## SQL语句执行顺序

|        语句组        | 执行次序 |
|:-----------------:|:----:|
|    select 查询列表    |  7   |
|    from 表1 别名     |  1   |
|   连接类型 join 表2    |  2   |
|      on 连接条件      |  3   |
|     where 筛选      |  4   |
|   group by 分组列表   |  5   |
|     having 筛选     |  6   |
|   order by排序列表    |  8   |
| limit 起始条目索引，条目数; |  9   |

## [SQL关键字](Other/src/main/sql/SQL关键字/SQL关键字.md)

## [问题与拓展](Other/src/main/sql/SQL问题与拓展/问题与拓展.md)
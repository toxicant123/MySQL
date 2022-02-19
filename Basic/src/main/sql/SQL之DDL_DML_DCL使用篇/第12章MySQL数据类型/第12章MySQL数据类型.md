# 第12章 MySQL数据类型

## 1. MySQL中的数据类型

|    类型    |                                                  类型举例                                                   |
|:--------:|:-------------------------------------------------------------------------------------------------------:|
|   整数类型   |                             TINYINT、SMALLINT、MEDIUMINT、INT(或INTEGER)、BIGINT                             |
|   浮点类型   |                                              FLOAT、DOUBLE                                               |
|  定点数类型   |                                                 DECIMAL                                                 |
|   位类型    |                                                   BIT                                                   |
|  日期时间类型  |                                    YEAR、TIME、DATE、DATETIME、TIMESTAMP                                    |
| 文本字符串类型  |                             CHAR、VARCHAR、TINYTEXT、TEXT、MEDIUMTEXT、LONGTEXT                              |
|   枚举类型   |                                                  ENUM                                                   |
|   集合类型   |                                                   SET                                                   |
| 二进制字符串类型 |                           BINARY、VARBINARY、TINYBLOB、BLOB、MEDIUMBLOB、LONGBLOB                            |
|  JSON类型  |                                              JSON对象、JSON数组                                              |
|  空间数据类型  | 单值：GEOMETRY、POINT、LINESTRING、POLYGON；<br/>集合：MULTIPOINT、MULTILINESTRING、MULTIPOLYGON、GEOMETRYCOLLECTION |

常见数据类型的属性（约束），如下：

|      MySQL关键字      |      含义       |
|:------------------:|:-------------:|
|        NULL        |  数据列可包含NULL值  |
|      NOT NULL      | 数据列不允许包含NULL值 |
|      DEFAULT       |      默认值      |
|    PRIMARY KEY     |      主键       |
|   AUTO_INCREMENT   | 自动递增，适用于整数类型  |
|      UNSIGNED      |      无符号      |
| CHARACTER SET name |    指定一个字符集    |


可以使用`character set name`来指定字符集

```sql
#创建数据库时指名字符集
CREATE DATABASE IF NOT EXISTS dbtest12 CHARACTER SET 'utf8';

#创建表的时候，指名表的字符集
CREATE TABLE temp(
    id INT
) CHARACTER SET 'utf8';

#创建表，指名表中的字段时，可以指定字段的字符集
CREATE TABLE temp1
(
    id   INT,
    NAME VARCHAR(15) CHARACTER SET 'gbk'
);
```

## 2. 整数类型

### 2.1 类型介绍

整数类型一共有 5 种，包括 TINYINT、SMALLINT、MEDIUMINT、INT（INTEGER）和 BIGINT。

它们的区别如下表所示：

|     整数类型     |  字节  |                 有符号数取值范围                  |        无符号数取值范围         |
|:------------:|:----:|:-----------------------------------------:|:-----------------------:|
|   TINYINT    |  1   |                 -128~127                  |          0~255          |
|   SMALLINT   |  2   |               -32768~32767                |         0~65535         |
|  MEDIUMINT   |  3   |             -8388608~8388607              |       0~16777215        |
| INT、INTEGER  |  4   |          -2147483648~2147483647           |      0~4294967295       |
|    BIGINT    |  8   | -9223372036854775808~9223372036854775807  | 0~18446744073709551615  |




















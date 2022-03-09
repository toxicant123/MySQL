# 如何统计去重后的数据个数

使用如下语句：

```sql
select count(distinct 需要统计去重后的字段) from ...
```
# 两表join后数据增多

这是由于 on 的条件在任意表中不是唯一的

举例：

```sql
create table a(
    id   int comment '身份id',
    name varchar(20)
);

create table b(
    id      int comment '身份id',
    address varchar(20)
);

insert into a
    value (1, 'Tom'),
    (2, 'Jerry');

insert into b
    value (1, 'home'),
    (1, 'house'),
    (2, 'bed');
```

表1存储了所有人的id和姓名，表二存储了所有人的id和住址，如果这个时候想查询姓名和住址的关系，若如下编写：

```sql
select name,address
from a
         join b on a.id = b.id;
```

结果为：

```
+-------+---------+
| name  | address |
+-------+---------+
| Tom   | home    |
| Tom   | house   |
| Jerry | bed     |
+-------+---------+
3 rows in set (0.00 sec)
```

可以发现name为"Tom"的记录有两条，这是由于on的条件在b表不唯一的原因造成的。
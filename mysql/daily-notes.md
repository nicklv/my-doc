# errors

## 1175

禁止批量更新错误

此时需要执行 SET SQL_SAFE_UPDATES = 0;
再执行语句

## 1093

update表不能出现在子查询的from中

此时可改为使用inner join，如：
update TEST_NOIDX b  inner join  ( select a.ID,a.CREATETIME from TEST_NOIDX a where a.VNAME='Aa') c on b.ID=c.ID set b.CREATETIME=now();  


# explain

type显示的是访问类型，是较为重要的一个指标，结果值从好到坏依次是：
system > const > eq_ref > ref > fulltext > ref_or_null > index_merge > unique_subquery > index_subquery > range > index > ALL
一般来说，得保证查询至少达到range级别，最好能达到ref。

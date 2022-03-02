# DataFrame basic options

## Option1 : 与  pd.info()等效操作

```
#data
+-------+----------+----+
|session|timestamp1| id2|
+-------+----------+----+
|      1|         1|null|
|      1|         2| 5.0|
|      1|         3| NaN|
|      1|         4|null|
|      1|         5|10.0|
|      1|         6| NaN|
|      1|         6| NaN|
+-------+----------+----+
```

1. ##### 计算每一列的空值情况

   ```python
   #option1
   df.select([count(when(isnan(c) | col(c).isNull(), c)).alias(c) for c in df.columns]).show() #
   +-------+----------+---+
   |session|timestamp1|id2|
   +-------+----------+---+
   |      0|         0|  5|
   +-------+----------+---+
   ```

   ```python
   #option2
   df.select([count(when(isnan(c), c)).alias(c) for c in df.columns]).show() #
   +-------+----------+---+
   |session|timestamp1|id2|
   +-------+----------+---+
   |      0|         0|  3|
   +-------+----------+---+
   ```

2. ##### 计算每一列数据分布情况

   ```python
   df.describe().show()
   +-------+-------+------------------+---+
   |summary|session|        timestamp1|id2|
   +-------+-------+------------------+---+
   |  count|      7|                 7|  5|
   |   mean|    1.0| 3.857142857142857|NaN|
   | stddev|    0.0|1.9518001458970664|NaN|
   |    min|      1|                 1|5.0|
   |    max|      1|                 6|NaN|
   +-------+-------+------------------+---+
   ```

3. ##### 计算每一列数据类型

   ```python
   df.dtypes 
   [('session', 'bigint'), ('timestamp1', 'bigint'), ('id2', 'double')]
   ```


## Option2 : collect()

PySpark的collect()操作是用来将所有结点中的数据**收集到驱动结点上**(PySpark基于分布式架构)。因此collect()操作一般用于小型数据及上，在大型数据及上使用可能会导致内存不足。
 

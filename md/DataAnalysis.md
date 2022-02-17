### 数据分析起手式

```python
import pandas as pd
import numpy as np

dt = pd.read_csv(r"",sep)
dt.info()
```

#### 不放回抽取

```python
np.random.seed(1234)
index = np.random.choice(np.arange(number1),number2,replace=False)
np.ramdom.seed(1234)
inde = np.ramdom.permutation(np.arange())
```

#### pandas去重

```python
DataFrame.Drop_duplicates（subset=None,keep="first",inplace=False,ignore_index=False）

sunset=["column_name1","column_name2"] #去重的依赖子集，默认全部列重复才去
keep =“first” #默认去重保留第一个重复数据，也可以设为“last”

```

#### Pandas 离散数据类型排序

```python
#df["columns1"]是离散数据类型
list_sort = ['','','','','']
df["columns1"] = df["columns1"].astype("category".cat.set_categories(list_sorted))
df_sorts = df.sort_values(by=["columns1"],asending=Ture)

#------------------------sort参数：na_postion =“False”#default    可替换为first
```

#### 统计长度操作

```python
df["data_len"] = df["columns1"].apply(len)
print(data["data_len"].describe())
```

#### 重新索引

```python
df.reset_index()#有正常索引的再列出一列索引，concat会自动重置索引，groupby最适合用这个
```

#### 空值处理

```python
print(df[df.isnull().T.any()])
df.dropna(axis=0, how='any', thresh=None, subset=None, inplace=False)
#inplace 是否在原数据上操作
#how =“any”|"all",只要有缺失值就删除该行或该列|所有的值缺失才删除
#thresh 有多少个空值才删除
```

#### 哑变量处理

```python
pd.get_dummies(dataframe)
#返回一个哑变量的矩阵，需要修改表头
```

#### pandas存进去是列表格式，都出来是字符串

```python
df["data"] = df["data"].apply(lambda x:eval(x))
```

#### apply多输入多输出处理

```python
df = pd.DataFrame(......)
def func(row):
  a = row["..."]
  b = row["..."]
  ...
  return A,B
df[["",""]] = df.apply(func,axis=1,result_type = "expend")
```

#### Mysql数据库操作

```sql
#终端操作
mysql -uroot -p #登录mysql
show databases 
use database
show tables
```

#### 

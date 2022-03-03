## DataFrame Basic Option

## apply 函数应用

- ### option1  : apply  多值输入

```python
df = pd.DataFrame(......)
def func(row):
  a = row["..."]
  b = row["..."]
  ...
  return A,B
df[["",""]] = df.apply(func,axis=1,result_type = "expend")  #expend参数
```

## 重复值处理

- ### option1 : df.deduplicate

`duplicated`函数用于标记`Series`中的值、`DataFrame`中的记录行是否是重复，重复为`True`，不重复为`False`。

```python
df.duplicated(self, subset=None, keep='first')#默认所有列，第一次出现外，其余相同的被标记为重复 
df.duplicated(['col1','col2'],keep='last')#所有相同的都被标记为重复
              keep='first'  #除了第一次出现外，其余相同的被标记为重复 
              keep='last'   #除了最后一次出现外，其余相同的被标记为重复

return: 返回bool值
重复的row ： df[df.duplicated(self, subset=None, keep='first')]
去重后的df ：df[~df.duplicated(self, subset=None, keep='first')]
```

- ### option2 : df.drop_duplicates

```python
df.drop_duplicates(self, subset=None, keep='first',inplace=False)inplace为True直接修改原DF
```

## 展示

- ### option1:  pd.set_option

```python
pd.set_option('max_colwidth',100) #设置value的显示长度为100，默认为50
pd.set_option('display.max_rows', None) #显示所有行
pd.set_option('display.max_columns', None)   #显示所有列
```

## 空值处理

- ### option1  : 

## 存进去是列表，读出来是字符串

- ### solution1  value()

  ```python
  df["data"] = df["data"].apply(lambda x:eval(x))
  ```

  

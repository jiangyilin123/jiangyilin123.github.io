---
title: "First"
date: 2021-12-21T18:32:31-06:00
draft: true
---
# Json Format 
### 快速找到key
#数据处理 
-[[Python#Zip实现快速转字典，存入数据库]]
```python
d = response.json()
a = d.keys()
b = list(a)
print(b[0])
````

上面的代码把API 内得到的response变成了json
之后又把json的key 放到变量a里面
之后再打印出第一个key

### 字典增加object
使用data.update({"name":"value"})


# 时间戳
### 时间戳转换时区
#数据处理 
如果一个timestamp并没有任何声明,他是没有任何时区的: 我们需要让他知道time zone. 这里一般直接使用pandas内置的tz_localize这个function,它的用法在[pandas.Series.tz_localize — pandas 1.3.5 documentation (pydata.org)](https://pandas.pydata.org/docs/reference/api/pandas.Series.tz_localize.html)
```python
s = pd.Series([1],index=pd.DatetimeIndex(['2018-09-15 01:30:00']))
s.tz_localize('CET')
````
*另外时间戳转换在线软件: [[好用的网页#时间转换]]*

### epoch 快速变成utc 时间
使用datetime的库，其中有专门的utc时间
```python
dataframe['dt'] = dataframe['dt'].apply(lambda x: datetime.utcfromtimestamp(x))
````

# 配置文件
#后端
### 多个配置文件
- 第一种想到的方案： [如何使用Python ConfigParser的多个配置文件？ - 问答 - 云+社区 - 腾讯云 (tencent.com)](https://cloud.tencent.com/developer/ask/53708)
- 第二种想到的方案

```ad-note
也许这里可以去考虑多个配置文件串联
````

# Zip实现快速转字典，存入数据库
如果你有两个numpy或者list， 快速使用zip变成dictionary，从而方便进入数据库。
[python - zip to dictioanry- Stack Overflow](https://stackoverflow.com/questions/14302248/dictionary-update-sequence-element-0-has-length-3-2-is-required)

# List
### 一个命令快速搞定2d list的展开
```python
sum([[1, 2, 3], [4, 5, 6], [7], [8, 9]],[])
# [1, 2, 3, 4, 5, 6, 7, 8,9]
````
**注意**： 这里使用的是`sum(list,[])`
参考： [python - How to make a flat list out of a list of lists - Stack Overflow](https://stackoverflow.com/questions/952914/how-to-make-a-flat-list-out-of-a-list-of-lists)

### list 与map结合，快速转换
```python
map(lambda x: True if x % 2 == 0 else False, range(1, 11))
````
参考：[pandas - Map an if statement in Python - Stack Overflow](https://stackoverflow.com/questions/29247718/map-an-if-statement-in-python)

### 通过value定位到list的具体位置


# Lambda运用
一个快速的小模块，让你不用for loop
例一：
```python
dataframe['dt'] = dataframe['dt'].apply(lambda x: datetime.utcfromtimestamp(x))
````
这里例子里面还有知识点 [[Python#epoch 快速变成utc 时间]]


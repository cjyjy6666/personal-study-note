# strings
长字符串：①括号，隐式连接②反斜杠，显式连接③三引号，保留格式

`str.replace()`

`string2=string1.replace("origin","to replace")`

We have to use string2 to store it, and string1 won't change.

f-strings:

`print(f"value of a is{a:.2f}")`

`str="sep".join([str1,str2,str3])`

`str.upper()``str.lower()``str.title()`

`str.strip()`去除字符串两端的空白字符

`list=str.split("sep")`return一个字符串列表，sep缺省默认空格

连用多个函数，左→右结合

# numbers
**the division of ints produces float!!!**

整除`//`模`%`乘方`**`

```python
from decimal import Decimal#Decimal类用于创建高精度十进制数
from_str = Decimal("0.1") #从字符串创建无精度误差
from_float = Decimal(0.1)   #从浮点数创建有精度误差
```

# conditionals
支持bool型变量True and False

`bool(0)=False` `bool(1)=True`list/dictionary:False when empty.

`1 <= 2 <= 3`is acceptable.

与或非写作`and,or,not`

```python
if condition1:
    ...
elif condition2:
    ...
else:...
```

# lists
`a_list=[]`

`len()`用于获取数据结构中元素数量，适用于任何可迭代对象，如字符串、列表、元组、字典、集合等数据结构

list可以是多维的

list中的值可以用`del`删去

`del`的用法：删除变量、列表中元素（通过索引或切片）、字典中键值对（指定key即可）、对象属性、整个列表或字典

`if "sth" in a_list:`check the presence of sth in a list.



**列表可变性**：

引用问题  将列表赋值给另一个变量，实际是创建一个新的引用

对原变量的修改会影响另一个变量！

Python中变量名是对对象的**引用**，与C/C++的指针有相同之处

创建列表独立副本：

方式一：`modified=list(original)`

方式二：`modified=original.copy()`

🔺still shallow copy!

元素为可变对象，仍然共享引用

方式三：first`import copy`,then`modified=copy.deepcopy(original)`

Deep Copy! 创建完全独立副本



**一些列表操作函数**

`list.append()`

`list.remove()`(better to check first(using "in"))

sorting:

`list.sort()`sorts the list in place

`slist=sorted(list)`returns a new list

排序参数：

①`key`指定一个函数，应用于列表每一项，返回值作为排序依据

②`reverse`指定顺序。默认`False`升序，`True`降序

`firstlist.extend(secondlist)`with secondlist unchanged ,but copied and appended to first list

same as:`firstlist+=secondlist`

`list.reverse()`

# dictionaries
key-value pairs 键唯一、不可变  值可重复、可变

因此key不能是list,dict等immutable types

```python
dict1 = {"value1": 1.6, "value2": 10, "name": "John Doe"}
dict2 = dict(value1=1.6, value2=10, name="John Doe")
```

`dict.keys()``dict.values()``dict.items()`返回动态变化的视图对象



Accessing and setting values:

using`dict["key"]`注意保持单双引号风格一致

also`value=dict.get('key','default_value')`default value默认为None



`del dict["key"]`



与list一样具可变性(mutable)



`a_value=dict.pop("key","default_value")`

pop:从数据结构中移除并返回一个元素的操作



`dict.setdefault()`基本同get()，但是default_value被返回的同时会被加进dict



`dict1.update(dict2)`

# for-loops
```python
for item in my_list:
    print(item)
```



```python
for idx, val in enumerate(my_list):
    print(f"idx: {idx}, value: {val}")
```

enumerate(iterable, start=0)

iterable：要遍历的序列（可迭代对象）

start：遍历的起始位置，默认为0

返回值：返回一个枚举对象(enumerate object)，每次迭代生成一个元组，再解包成idx和val

解包(unpacking):将可迭代对象中元素直接赋值给多个变量

部分解包:*捕获剩余元素，如first,second,*rest

忽略元素:_,_=1,2,下划线作为占位符

```python
my_dict = {"hacker": True, "age": 72, "name": "John Doe"}
for val in my_dict:
    print(val)
#直接遍历dictionary，默认key迭代
#不可直接说指定起始位置

for key, val in my_dict.items():
    print(f"{key}={val}")
```



`range(0, 10, 2)`

`r=range(10)``print(list(r[1:9:2]))`

range对象是不可变序列，但支持索引和切片操作。

迭代时按需生成数字，不占内存。






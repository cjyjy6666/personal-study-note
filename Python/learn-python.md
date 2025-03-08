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

`r=range(10)` `print(list(r[1:9:2]))`

range对象是不可变序列，但支持索引和切片操作。

迭代时按需生成数字，不占内存。

# functions
`positional arguments`：参数按定义顺序传递，数量匹配

`keyword arguments`:we can mix the order
    混合使用时，不能以keyword arguments开头

`default arguments`:set default value in function definition
`None`can be used as a default argument
mutable objects are not allowed as default arguments!But we can use `None` as default value and initialize the mutable object in the function body.

`Docstrings`:for example`"""A description of the function."""`is written in a function,and we can use `help(function_name)`to get the docstring.推荐格式：功能说明+参数+返回值

`pass`占位符does nothing,can be used as a placeholder for future code,like
```python
def to_be_writen_function():
    pass
```
# file I/O
## working with paths
使用标准库`pathlib`进行路径操作
①面向对象②自动处理操作系统路径差异
**accessing the path of current file**:
```python
from pathlib import Path
file_path=Path("filename").resolve()
#In .py files,we can get the path of the current file by using:
Path(__file__)
```
其中`resolve()`函数：
①基于当前工作目录，将相对路径转换为绝对路径
②符号链接解析
③路径规范化
而`absolute()`函数依赖于工作目录且无法实现符号链接解析和路径规范化
**目录操作**
获取当前工作目录：`current_dir=Path.cwd()`
获取父目录：`current_dir=current_file.parent`
获取文件名：`current_file.name`
获取文件扩展名：`current_file.suffix`
获取文件名（不含扩展名）：`current_file.stem`
路径拼接操作符`/`
例如`data_dir = current_dir.parent / "data"`
**checking if path exists**
`path.exists()`检查路径是否存在
`path.is_dir()`检查路径是否为目录
`path.is_file()`检查路径是否为文件
**Symbolic links符号链接**
数据指针，记录目标路径
```bash
#创建符号链接(windows需要管理员权限)
ln -s originial_path link_path
```
In python:
```python
from pathlib import Path

src = Path("data/important.csv")
link = Path("shortcut.csv")

if not link.exists():
    link.symlink_to(src)  # 类似 ln -s
link.unlink()#删除符号链接
```
use`.issymlink()`to check if a path is a symbolic link.
use`.resolve()`to get the target(original) path of a symbolic link.
## reading files
Using `with` statement to obtain a context manager is preferred.
>context manager：用于资源管理，通过with语句自动化资源管理，处理成对出现的操作，如打开文件、获取锁、连接数据库等，保证退出context时自动释放资源。
```python
file_path=data_dir/"example_file.txt"
with open(file_path,"r") as example_file:
    for line in example:
        print(line.strip())
#用with语句自动实现文件关闭，当然也可以用file.close()
```
文件打开模式：
- `"r"` 只读（默认） 文件不存在时抛出异常
- `"r+"` 读写 文件不存在时抛出异常
- `"w"` 只写（清空原内容） 文件不存在时创建
- `"a"` 追加（保留原内容） 文件不存在时创建
- `"x"` 只写（清空原内容） 文件不存在时创建，文件已存在时抛出异常
- `"b"` 二进制模式（用于非文本文件）
- `"t"` 文本模式（默认）
读取方法：
- `for line in file:`逐行读取文件内容
- `file.read()`读取整个文件内容（小文件）
- `file.readline()`逐行读取文件内容
- `file.readlines()`逐行读取文件内容，返回一个列表
- `file.read(n)`读取n个字符（二进制文件分块读取可用）
## writing files
```python
new_file_path=data_dir/"new_file.txt"

with open(new_file_path,"w") as new_file:
    new_file.write("Content")
```
Also we can delete the file by:
```python
if new_file_path.exists():
    new_file_path.unlink()
```
注意`unlink`的效果：
- 路径指向普通文件，删除文件
- 符号链接，删除符号链接，不影响目标文件

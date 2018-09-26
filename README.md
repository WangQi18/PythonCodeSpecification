# Python代码规范和命名规范

## 1、编码
如无特殊情况, 文件一律使用 UTF-8 
编码如无特殊情况, 文件头部必须加入#-*-coding:utf-8-*-标识

## 2、代码格式
### 2.1、缩进
统一使用 4 个空格进行缩进
### 2.2、行宽
每行代码尽量不超过 80 个字符(在特殊情况下可以略微超过 80 ，但最长不得超过 120)
理由：
    方便diff
    方便在控制台下查看代码
    太长可能是设计有缺陷
### 2.3、空行
模块级函数和类定义之间空一行；
类成员函数之间空一行；
```
class A:  

    def __init__(self):
        pass
        
    def hello(self):  
        pass
        
    def main():  
        pass  
```
可以使用多个空行分隔多组相关的函数
函数中可以使用空行分隔出逻辑相关的代码

## 3、空格
在二元运算符两边各空一格[=,-,+=,==,>,in,is not, and]:
```
i = i + 1
submitted += 1
x = x * 2 - 1 
hypot2 = x * x + y * y 
c = (a + b) * (a - b)
```
函数的参数列表中，','之后要有空格
```
# 正确的写法
def complex(real, imag):
    pass 
    
# 不推荐的写法
def complex(real,imag):
    pass
```

函数的参数列表中，默认值等号两边不要添加空格
```
# 正确的写法
def complex(real, imag=0.0):
    pass 
    
# 不推荐的写法
def complex(real, imag = 0.0):   
    pass
```
左括号之后，右括号之前不要加多余的空格
```
# 正确的写法
spam(ham[1], {eggs: 2}) 

# 不推荐的写法
spam( ham[1], { eggs : 2 } )
```
字典对象的左括号之前不要多余的空格
```
# 正确的写法
dict['key'] = list[index] 

# 不推荐的写法
dict ['key'] = list [index]
```
不要为对齐赋值语句而使用的额外空格
```
# 正确的写法
x = 1
y = 2
long_variable = 3 
# 不推荐的写法
x             = 1
y             = 2
long_variable = 3
```

## 4、换行
Python 支持括号内的换行。这时有两种情况。
1) 第二行缩进到括号的起始处
```
foo = long_function_name(var_one, var_two,                         
                         var_three, var_four)
```
2) 第二行缩进 4 个空格，适用于起始括号就换行的情形
```
def long_function_name(        
        var_one, var_two, var_three,
        var_four):
    print(var_one)
```
使用反斜杠\换行，二元运算符+ .等应出现在行末；长字符串也可以用此法换行
```
session.query(MyTable).\ 
        filter_by(id=1).\        
        one() 
        
print 'Hello, '\
       '%s %s!' %\
       ('Harry', 'Potter')
```
禁止复合语句，即一行中包含多个语句：
```
# 正确的写法
do_first()
do_second()
do_third() 

# 不推荐的写法
do_first();do_second();do_third();
```
if/for/while一定要换行：
```
# 正确的写法
if foo == 'blah':    
    do_blah_thing() 
    
# 不推荐的写法
if foo == 'blah':
    do_blash_thing()
```

6、docstring
docstring 的规范中最其本的两点：
所有的公共模块、函数、类、方法，都应该写 docstring 。私有方法不一定需要，但应该在 def 后提供一个块注释来说明。docstring 的结束"""应该独占一行，除非此 docstring 只有一行。"""Return a foobarOptional plotz says to frobnicate the bizbaz first.""" """Oneline docstring"""

# 二、注释

## 1、注释
### 1.1、块注释
“#”号后空一格，段落件用空行分开（同样需要“#”号）
```
# 块注释
# 块注释
#
# 块注释
# 块注释
```
### 1.2、行注释
至少使用两个空格和语句分开，注意不要使用无意义的注释
```
# 正确的写法
x = x + 1  # 边框加粗一个像素 

# 不推荐的写法(无意义的注释)
x = x + 1 # x加1
```
### 1.3 函数注释
对自定义函数，表明函数功能和参数及返回描述
```
def func(arg1, arg2): 
    """
    在这里写函数的一句话总结(如: 计算平均值). 
    :param arg1:参数1
    :param arg2: 参数2
    :return: 返回int
"""
```
### 1.4、建议

在代码的关键部分(或比较复杂的地方), 能写注释的要尽量写注释
比较重要的注释段, 使用多个等号隔开, 可以更加醒目, 突出重要性
```
app = create_app(name, options) 

# =====================================
# 请勿在此处添加 get post等app路由行为 !!!
# ===================================== 

if __name__ == '__main__':
    app.run()
```
# 三、命名规范
## 1、类名
类名使用驼峰(CamelCase)命名风格，首字母大写，私有类可用一个下划线开头
```
class Farm():   
    pass class

AnimalFarm(Farm): 
    pass 
    
class _PrivateFarm(Farm):
    pass
```
将相关的类和顶级函数放在同一个模块里. 不像Java, 没必要限制一个类一个模块.
## 2、函数
函数名一律小写，如有多个单词，用下划线隔开
```
def run():   
    pass 

def run_with_env():
    pass
```
私有函数在函数前加一个下划线_
```
class Person():    

    def _private_func():
        pass
 ```
## 3、变量名
变量名尽量小写, 如有多个单词，用下划线隔开
```
if __name__ == '__main__':
    count = 0    
    school_name = ''
```
常量采用全大写，如有多个单词，使用下划线隔开
```
MAX_CLIENT = 100
MAX_CONNECTION = 1000
CONNECTION_TIMEOUT = 600
```

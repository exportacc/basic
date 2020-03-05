---
layout:     post
title:      [basic]class
subtitle:   class 入門
date:       2020-02-26
author:     GEo
catalog: true
tags:
    - Python
    - Class
---

> 這是為我以後開發類別程式,為后面的人看懂我的程式結構以節省更多時間。

> 文件中内容與一些程式碼皆在以下書中找到 。 

> 此文件只作爲教學用途使用,非商業用途 。

> book : Introducing Python , Bill Lubanovic Copyright 2015 Bill Lubanovic , 978-1-449-35936-2   

可使用下述程式碼把markdown格式轉成word
```
pandoc -o output.docx -f markdown -t docx input.md
```

## OOP

> Object Oriented Programming 

> 面向對象編程

## 簡單物件與類別

簡單的class資料結構

```
class Person():
    pass

someone = Person()
```

Python 需要定義簡單的初始化資訊才是好的定義Class方法

承接之前的例子,添加初始化條件

```
class Person():
    def __init__(self,name): # 初始化條件
        self.name = name

hunter = Person('Elmer Fudd!!')

```

$__init__()$ 特殊的Python名稱(類別),代表一個方法,用來定義初始化單一物件

它第一個參數必須是self。

self 不是Python保留字,而是一種慣例 , 方便後來維護的人員知道這是它參考至自己本身這個物件 。 

Step :

    1. 查看Person類別的定義
    2. 在記憶體中建立一個新物件
    3. 呼叫 __init__ , 傳遞這個物件給 self , 另一個引數('Elmer Fudd!!')給 name 。
    4. 在物件中儲存name的值
    5. return 
    6. 將名稱 hunter 指定給物件 。

之後我們物件會被當作是屬性與物件一起存儲,可以直接讀取或寫入 。 

當我們建立一個實際新物件,要使用回傳給變數的名稱,以上述例子而言

```
print('{}'.format(hunter.name))
```

更多的表達方式

```
class ComplexN():
    def __init__(self,r=0,i=0):
        self.real = r
        self.imag = i

    def get(self):
        print('{}+{}j'.format(self.real,self.imag))

ComplexN().get() # 使用預設的初始值 0,0
ComplexN(1,2).get() # r=1 , i=2
```

## 繼承 Inheritance

> 原本的類別稱爲 父系(parent) , 超類別 (superclass) 或 基礎類別 (base class) 

> 新的類別稱爲 子系 (child) , 子類別 (subclass) 或 衍生類別 (derived class)

```
class Car():
    def exclaim(self):
        print('I'm a car!')

class Yugo(Car):
    def exclaim(self):
        print('I\'m a car! but more Yugo-ish')

    def need_a_push(self): # 添加新方法
        pass

Yugo = Yugo() # 不好命名方式 , 會覆蓋原本定義的 class

GiveYugo = Yugo()

>> GiveYugo.exclaim()

'I'm a car! but more Yugo-ish'

```

#### 父系

```
class Person():
    def __init__(self,name):
        self.name = name

class EmailPerson(Person):
    def __init__(self,name,email):
        super().__init__(name) # 繼承Person的初始化資訊
        self.name = email # 新增初始化資訊

bob = EmailPerson('Bob Frapples','bob@frapples.com')

super().__init__(name) is equivalent to
Person.__init__(self,name)

class EmailPerson(Person):
    def __init__(self,name,email):
        self.name = name # 繼承Person的初始化資訊
        self.name = email
```

上述寫法也沒有錯,不過是浪費繼承的使用方法 。

## Multiple Inheritance  雙重繼承

兩種形態

### 一對一的雙重繼承

```
class Base:
    pass

class Derived1(Base):
    pass

class Derived2(Derived1):
    pass
```

### 多對一的雙重繼承

```
class Base1:
    pass

class Base2:
    pass

class MultiDerived(Base1, Base2):
    pass
```

## 使用特性來取得屬性值與設定它 Property

Python 不需要 getter 與 setter , 因爲有 Python 的風格 —— 使用特性(Property)

> 也就是作爲裝飾器 ```@```

```
@property # 在getter方法之前

@name.setter # 在setter方法之前
```

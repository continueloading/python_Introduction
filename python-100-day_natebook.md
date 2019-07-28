# python-100-day学习笔记
这是关于在git-hub上的一个python的学习笔记（[python-100-day](https://github.com/jackfrued/Python-100-Days)），记录一些新学习到的东西.
## 1. 编写规范
记录关于一些私人、团队编写代码时的一些代码编写规则，让代码可读性更高
### 1.1 PEP 8要求
* 用小写字母拼写，多个单词用下划线连接。
* 受保护的实例属性用单个下划线开头。<font color='red'>（后面会讲）</font>
* 私有的实例属性用两个下划线开头。<font color='red'>（后面会讲）</font>

### 1.2 必要元素
#### 1.2.1 自定义模块的引用
一般我们可以使用import来引用一些我们写在其他'.py'文件中（模块）的函数或者变量，这些模块中有时会有一些执行代码，一般我们是不想让其运行的，所以要将执行代码放入以下的条件中，可以使除非是我们直接用编译器打开执行，否则都会跳过不执行。

	# __name__是Python中一个隐含的变量它代表了模块的名字
	# 只有被Python解释器直接执行的模块的名字才是__main__
	if __name__ == '__main__':
		执行代码

	###############################################
	# 标准写法
	def main():
    # Todo: Add your code here
    	pass


	if __name__ == '__main__':
    	main()
	###############################################
## 2. 编写技巧
记录一些在学习过程中看见的方便实用的代码编辑方法
### 2.1 比对大小并交换
	(x, y) = (y, x) if x > y else (x, y)
	#可以使用后面的if来对x，y的值进行大小判断，判断为真则取前面，判断为小取后
### 2.2 字符型转数值
使用字符型转到数字型时要注意字符型本身的数字是什么类型的变量，如果是浮点型的数字使用转换时只能先将其转换为浮点型再转为整型，而整型的字符可以直接转换为浮点型。即int()只能用来转换整型的字符，float()没有限制

	a = '9'
	print(int(a))	#True
	print(float(a))	#True

	a = '9.3'
	print(int(a))	#False
	print(float(a))	#True

## 3. 基础学习
记录一些有关python的一些函数的使用方法以及基础学习
### 3.1 字符串
这里字符串的学习大都都是没有学过的

#### 3.1.1 基础操作
		str1 = 'hello, world!'

	    # 通过len函数计算字符串的长度
	    print(len(str1))  # 13

	    # 获得字符串首字母大写的拷贝
	    print(str1.capitalize())  # Hello, world!

	    # 获得字符串变大写后的拷贝
	    print(str1.upper())  # HELLO, WORLD!

	    # 从字符串中查找子串所在位置
	    print(str1.find('or'))  # 8
	    print(str1.find('shit'))  # -1

    	# 与find类似但找不到子串时会引发异常
    	# print(str1.index('or'))
    	# print(str1.index('shit'))

    	# 检查字符串是否以指定的字符串开头
	    print(str1.startswith('He'))  # False
	    print(str1.startswith('hel'))  # True

	    # 检查字符串是否以指定的字符串结尾
	    print(str1.endswith('!'))  # True

	    # 将字符串以指定的宽度居中并在两侧填充指定的字符
	    print(str1.center(50, '*'))

	    # 将字符串以指定的宽度靠右放置左侧填充指定的字符
	    print(str1.rjust(50, ' '))
	    str2 = 'abc123456'

	    # 从字符串中取出指定位置的字符(下标运算)
	    print(str2[2])  # c

	    # 字符串切片(从指定的开始索引到指定的结束索引)
	    print(str2[2:5])  # c12
	    print(str2[2:])  # c123456
	    print(str2[2::2])  # c246
	    print(str2[::2])  # ac246
	    print(str2[::-1])  # 654321cba
	    print(str2[-3:-1])  # 45

	    # 检查字符串是否由数字构成
	    print(str2.isdigit())  # False

	    # 检查字符串是否以字母构成
	    print(str2.isalpha())  # False

	    # 检查字符串是否以数字和字母构成
	    print(str2.isalnum())  # True

	    str3 = '  jackfrued@126.com '
	    print(str3)

	    # 获得字符串修剪左右两侧空格的拷贝
	    print(str3.strip())


### 3.2 列表
#### 3.2.1 基础操作

	    list1 = [1, 3, 5, 7, 100]
	    print(list1)
	    list2 = ['hello'] * 5
	    print(list2)

	    # 计算列表长度(元素个数)
	    print(len(list1))

	    # 下标(索引)运算
	    print(list1[0])
	    print(list1[4])
	    # print(list1[5])  # IndexError: list index out of range
	    print(list1[-1])
	    print(list1[-3])
	    list1[2] = 300
	    print(list1)

	    # 添加元素
	    list1.append(200)
	    list1.insert(1, 400)
	    list1 += [1000, 2000]
	    print(list1)
	    print(len(list1))

	    # 删除元素	
	    list1.remove(3)		#删除同名元素
	    if 1234 in list1:
	        list1.remove(1234)

	    del list1[0]	#删除相应下标元素
	    print(list1)

	    # 清空列表元素
	    list1.clear()
	    print(list1)

#### 3.2.2 切片操作

		fruits = ['grape', 'apple', 'strawberry', 'waxberry']
	    fruits += ['pitaya', 'pear', 'mango']

	    # 循环遍历列表元素
	    for fruit in fruits:
	        print(fruit.title(), end=' ')
	    print()

	    # 列表切片
	    fruits2 = fruits[1:4]
	    print(fruits2)
	    # fruit3 = fruits  # 没有复制列表只创建了新的引用

	    # 可以通过完整切片操作来复制列表
	    fruits3 = fruits[:]
	    print(fruits3)
	    fruits4 = fruits[-3:-1]
	    print(fruits4)

	    # 可以通过反向切片操作来获得倒转后的列表的拷贝
	    fruits5 = fruits[::-1]
	    print(fruits5)

#### 3.2.3 排序操作

		list1 = ['orange', 'apple', 'zoo', 'internationalization', 'blueberry']
	    list2 = sorted(list1)
	    # sorted函数返回列表排序后的拷贝不会修改传入的列表
	    # 函数的设计就应该像sorted函数一样尽可能不产生副作用
	    list3 = sorted(list1, reverse=True)

	    # 通过key关键字参数指定根据字符串长度进行排序而不是默认的字母表顺序
	    list4 = sorted(list1, key=len)

	    print(list1)
	    print(list2)
	    print(list3)
	    print(list4)

	    # 给列表对象发出排序消息直接在列表对象上进行排序
	    list1.sort(reverse=True)
	    print(list1)

#### 3.2.3 生成列表

		f = [x for x in range(1, 10)]
	    print(f)
	    f = [x + y for x in 'ABCDE' for y in '1234567']
	    print(f)
	    # 用列表的生成表达式语法创建列表容器
	    # 用这种语法创建列表之后元素已经准备就绪所以需要耗费较多的内存空间
	    f = [x ** 2 for x in range(1, 1000)]
	    print(sys.getsizeof(f))  # 查看对象占用内存的字节数
	    print(f)

	    # 请注意下面的代码创建的不是一个列表而是一个生成器对象
	    # 通过生成器可以获取到数据但它不占用额外的空间存储数据
	    # 每次需要数据的时候就通过内部的运算得到数据(需要花费额外的时间)
	    f = (x ** 2 for x in range(1, 1000))
	    print(sys.getsizeof(f))  # 相比生成式生成器不占用存储数据的空间
	    print(f)
	    for val in f:
	        print(val)

		# yield关键字将一个普通函数改造成生成器函数
		def fib(n):
		    a, b = 0, 1
		    for _ in range(n):
		        a, b = b, a + b
		        yield a

### 3.3 元组
Python 的元组与列表类似，不同之处在于元组的元素不能修改。

相较于列表元组有以下优点：

+ 元素固定不可更改，对于一些例如多线程等可以降低程序出错。
+ 对于储存空间以及创建时间来说相对于列表都少。

	    # 定义元组
	    t = ('骆昊', 38, True, '四川成都')
	    print(t)

	    # 获取元组中的元素
	    print(t[0])
	    print(t[3])

	    # 遍历元组中的值
	    for member in t:
	        print(member)

	    # 重新给元组赋值
	    # t[0] = '王大锤'  # TypeError
	    # 变量t重新引用了新的元组原来的元组将被垃圾回收
	    t = ('王大锤', 20, True, '云南昆明')
	    print(t)

	    # 将元组转换成列表
	    person = list(t)
	    print(person)

	    # 列表是可以修改它的元素的
	    person[0] = '李小龙'
	    person[1] = 25
	    print(person)

	    # 将列表转换成元组
	    fruits_list = ['apple', 'banana', 'orange']
	    fruits_tuple = tuple(fruits_list)
	    print(fruits_tuple)

### 3.4 集合
这里的集合定义与数学中的集合定义是相同的。集合内元素不能重复，集合间可以有交集、并集、合集。
<center>
<img src="https://raw.githubusercontent.com/jackfrued/Python-100-Days/master/Day01-15/res/python-set.png" width=450 height=330 />
图3.4.1 集合运算
</center>

		set1 = {1, 2, 3, 3, 3, 2}
	    print(set1)

	    print('Length =', len(set1))

	    set2 = set(range(1, 10))
	    print(set2)

	    set1.add(4)
	    set1.add(5)
	    set2.update([11, 12])
	    print(set1)
	    print(set2)

	    set2.discard(5)
	    # remove的元素如果不存在会引发KeyError
	    if 4 in set2:
	        set2.remove(4)
	    print(set2)

	    # 遍历集合容器
	    for elem in set2:
	        print(elem ** 2, end=' ')
	    print()

	    # 将元组转换成集合
	    set3 = set((1, 2, 3, 3, 2, 1))
	    print(set3.pop())
	    print(set3)

	    # 集合的交集、并集、差集、对称差运算
	    print(set1 & set2)
	    # print(set1.intersection(set2))
	    print(set1 | set2)
	    # print(set1.union(set2))
	    print(set1 - set2)
	    # print(set1.difference(set2))
	    print(set1 ^ set2)
	    # print(set1.symmetric_difference(set2))

	    # 判断子集和超集
	    print(set2 <= set1)
	    # print(set2.issubset(set1))
	    print(set3 <= set1)
	    # print(set3.issubset(set1))
	    print(set1 >= set2)
	    # print(set1.issuperset(set2))
	    print(set1 >= set3)
	    # print(set1.issuperset(set3))

### 3.5 字典
字典是另一种可变容器模型，类似于我们生活中使用的字典，它可以存储任意类型对象，与列表、集合不同的是，字典的每个元素都是由一个键和一个值组成的“键值对”，键和值通过冒号分开。下面的代码演示了如何定义和使用字典。

		scores = {'骆昊': 95, '白元芳': 78, '狄仁杰': 82}
	    # 通过键可以获取字典中对应的值
	    print(scores['骆昊'])
	    print(scores['狄仁杰'])

	    # 对字典进行遍历(遍历的其实是键再通过键取对应的值)
	    for elem in scores:
	        print('%s\t--->\t%d' % (elem, scores[elem]))

	    # 更新字典中的元素
	    scores['白元芳'] = 65
	    scores['诸葛王朗'] = 71
	    scores.update(冷面=67, 方启鹤=85)
	    print(scores)
	    if '武则天' in scores:
	        print(scores['武则天'])
	    print(scores.get('武则天'))

	    # get方法也是通过键获取对应的值但是可以设置默认值
	    print(scores.get('武则天', 60))

	    # 删除字典中的元素
	    print(scores.popitem())
	    print(scores.popitem())
	    print(scores.pop('骆昊', 100))

	    # 清空字典
	    scores.clear()
	    print(scores)

### 3.6 类和对象
简单的说，类是对象的蓝图和模板，而对象是类的实例。

 > 使用class关键字定义类，写在类中的函数，我们通常称之为（对象的）方法，这些方法就是对象可以接收的消息。虚拟对象的关键字为self。
 
	#	定义
	class Student(object):
	    # __init__是一个特殊方法用于在创建对象时进行初始化操作
	    # 通过这个方法我们可以为学生对象绑定name和age两个属性
	    def __init__(self, name, age):
	        self.name = name
	        self.age = age
	
	    def study(self, course_name):
	        print('%s正在学习%s.' % (self.name, course_name))
	
	    # PEP 8要求标识符的名字用全小写多个单词用下划线连接
	    # 但是部分程序员和公司更倾向于使用驼峰命名法(驼峰标识)
	    def watch_movie(self):
	        if self.age < 18:
	            print('%s只能观看《熊出没》.' % self.name)
	        else:
	            print('%s正在观看岛国爱情大电影.' % self.name)

	#	创建和使用
	def main():
    # 创建学生对象并指定姓名和年龄
    stu1 = Student('骆昊', 38)
    # 给对象发study消息
    stu1.study('Python程序设计')
    # 给对象发watch_av消息
    stu1.watch_movie()
    stu2 = Student('王大锤', 15)
    stu2.study('思想品德')
    stu2.watch_movie()


	if __name__ == '__main__':
    	main()

#### 3.6.1 访问可见性问题
对象的属性设置为私有的（private）或受保护的（protected），简单的说就是不允许外界访问，而对象的方法通常都是公开的（public）。在Python中，属性和方法的访问权限只有两种，也就是公开的和私有的，如果希望属性是私有的，在给属性命名时可以用两个下划线作为开头。

>双下划线开头的是私有的是不允许访问的
>单下划线开头的是暗示受保护的，是不建议直接访问的

	class Test:
	    def __init__(self, foo):
	        self.__foo = foo
	
	    def __bar(self):
	        print(self.__foo)
	        print('__bar')
		
	def main():
	    test = Test('hello')
	    # AttributeError: 'Test' object has no attribute '__bar'
	    test.__bar()
	    # AttributeError: 'Test' object has no attribute '__foo'
	    print(test.__foo)
	
	if __name__ == "__main__":
	    main()

其实Python的语法中并没有这样区分，只是对有两个下划线的变量进行来换名处理。如下：

	class Test:
	    def __init__(self, foo):
	        self.__foo = foo
	
	    def __bar(self):
	        print(self.__foo)
	        print('__bar')
	
	def main():
	    test = Test('hello')
	    test._Test__bar()
	    print(test._Test__foo)
	
	
	if __name__ == "__main__":
	    main()

#### 3.6.2 面向对象的支柱
面向对象有三大支柱：封装、继承和多态。

> 封装:隐藏复杂操作，提供简单接口，在创建类的过程中已经将数据以及数据的操作封装起来，用户只要知道输入参数和调用方法就可以使用这个类里的代码。


#### 3.6.3 <font color='red'>@property装饰器</font>
一般单下划线开头是暗示保护的，是不建议直接访问的，想访问属性可以通过属性的getter（访问器）和setter（修改器）方法进行对应的操作。如果要做到这点，就可以考虑使用@property包装器来包装getter和setter方法，使得对属性的访问既安全又方便，代码如下所示。

	class Person(object):
	    def __init__(self, name, age):
	        self._name = name
	        self._age = age
	
	    # 访问器 - getter方法			这种定义决定可以访问
	    @property
	    def name(self):
	        return self._name
	
	    # 访问器 - getter方法
	    @property
	    def age(self):
	        return self._age
	
	    # 修改器 - setter方法			这种定义决定考研修改
	    @age.setter
	    def age(self, age):
	        self._age = age
	
	    def play(self):
	        if self._age <= 16:
	            print('%s正在玩飞行棋.' % self._name)
	        else:
	            print('%s正在玩斗地主.' % self._name)
	
	def main():
	    person = Person('王大锤', 12)
	    person.play()
	    person.age = 22
	    person.play()
	    # person.name = '白元芳'  # AttributeError: can't set attribute
	
	if __name__ == '__main__':
	    main()

>说明：@的使用
>
>   def funcA(A):
> 	   print("function A")
> 	
> 	def funcB(B):
> 	    print(B(2))
> 	    print("function B")
> 	
> 	@funcA
> 	@funcB
> 	def func(c):
> 	    print("function C")
> 	    return c**2
> 	================================Result==========================
> 	function C
> 	4
> 	function B
> 	function A
> 	则整个程序的执行过程就是funA(funB(funC))

#### 3.6.4 __ slots__魔法
Python是一门动态语言。通常动态语言允许我们在程序运行时给对象绑定新的属性或方法，当然也可以对已经绑定的属性和方法进行解绑定。可以通过在类中定义__ slots__ 变量来进行限定。需要注意的是__ slots__的限定只对当前类的对象生效，对子类并不起任何作用。
	class Person(object):
	
	    # 限定Person对象只能绑定_name, _age和_gender属性
	    __slots__ = ('_name', '_age', '_gender')
	
	    def __init__(self, name, age):
	        self._name = name
	        self._age = age
	
	    @property
	    def name(self):
	        return self._name
	
	    @property
	    def age(self):
	        return self._age
	
	    @age.setter
	    def age(self, age):
	        self._age = age
	
	    def play(self):
	        if self._age <= 16:
	            print('%s正在玩飞行棋.' % self._name)
	        else:
	            print('%s正在玩斗地主.' % self._name)
	
	
	def main():
	    person = Person('王大锤', 22)
	    person.play()
	    person._gender = '男'
	    # AttributeError: 'Person' object has no attribute '_is_gay'若无__slots__下面的语句将被允许
	    # person._is_gay = True


#### 3.6.5 静态方法和类方法
我们在类中定义的方法都是对象方法，也就是说这些方法都是发送给对象的消息。需要对类的输入参数进行先步判读时，可以使用静态方法和类方法。静方法如下（判断输入三角形三边是否符合要求）：

	from math import sqrt
	
	
	class Triangle(object):
	
	    def __init__(self, a, b, c):
	        self._a = a
	        self._b = b
	        self._c = c
	
	    @staticmethod
	    def is_valid(a, b, c):
	        return a + b > c and b + c > a and a + c > b
	
	    def perimeter(self):
	        return self._a + self._b + self._c
	
	    def area(self):
	        half = self.perimeter() / 2
	        return sqrt(half * (half - self._a) *
	                    (half - self._b) * (half - self._c))
	
	
	def main():
	    a, b, c = 3, 4, 5
	    # 静态方法和类方法都是通过给类发消息来调用的
	    if Triangle.is_valid(a, b, c):
	        t = Triangle(a, b, c)
	        print(t.perimeter())
	        # 也可以通过给类发消息来调用对象方法但是要传入接收消息的对象作为参数
	        # print(Triangle.perimeter(t))
	        print(t.area())
	        # print(Triangle.area(t))
	    else:
	        print('无法构成三角形.')
	
	
	if __name__ == '__main__':
	    main()


和静态方法比较类似，Python还可以在类中定义类方法，类方法的__第一个参数__约定名为__cls__，它代表的是当前类相关的信息的对象（类本身也是一个对象，有的地方也称之为类的元数据对象），通过这个参数我们可以获取和类相关的信息并且可以创建出类的对象，代码如下所示。


'''Python
from time import time, localtime, sleep


class Clock(object):
    """数字时钟"""

    def __init__(self, hour=0, minute=0, second=0):
        self._hour = hour
        self._minute = minute
        self._second = second

    @classmethod
    def now(cls):
        ctime = localtime(time())
        return cls(ctime.tm_hour, ctime.tm_min, ctime.tm_sec)

    def run(self):
        """走字"""
        self._second += 1
        if self._second == 60:
            self._second = 0
            self._minute += 1
            if self._minute == 60:
                self._minute = 0
                self._hour += 1
                if self._hour == 24:
                    self._hour = 0

    def show(self):
        """显示时间"""
        return '%02d:%02d:%02d' % \
               (self._hour, self._minute, self._second)


def main():
    # 通过类方法创建对象并获取系统时间
    clock = Clock.now()
    while True:
        print(clock.show())
        sleep(1)
        clock.run()

if __name__ == '__main__':
    main()
'''

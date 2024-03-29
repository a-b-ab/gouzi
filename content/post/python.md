+++
title = 'python'
date = 2024-03-17T13:35:01+08:00
draft = false
+++
*这是我在学习蛇书时的学习笔记，写这篇博客一是为了自己以后复盘，二是顺便分享一下，本人写这篇文章时才大二，写的不是很好，但是我就是不改，嘿嘿~~*
*白金镇楼*
![](https://raw.githubusercontent.com/a-b-ab/picture/main/Picgo202403182039941.jpg)

# Python和markdown使用方法
## markdown基础使用方法
标题前面加井号  

回车不能换行，只是将文字加个空格，想要换行需要在上一行后面加两个空格再回车  

想要在新起一段，则打两个回车

ctrl+i ：斜体
ctrl+b ：加粗

列表:
* 鸡翅
 
1.汉堡
2.可乐

插入图片： ctrl+alt+v

数学公式：以“\”起始
行内展示数学公式：ctrl+m
另起一段展示数学公式，上面连按两下

表格：第一行是表头以“|”分列，第二行是对齐方式，“-”表示默认即左对齐，在“—”左侧加“：”为左对齐，两边加为居中对齐,冒号一定要用英文
alt+shift+f可格式话文本编排

链接：复制链接直接cv
直接黏贴则直接生成可点击的链接
选中文字黏贴则生成可点击的文字按钮链接，选中文字黏贴则生成可点击的文字按钮链接

代码块:
```
int a 
a = 100
```
指定语言可高亮

```C
int a 
a = 100
```

分割线
在所需添加分割线的文本下新起一行输入三个减号“---”
阿巴阿巴阿巴阿巴

---

引用
在引用的2文字前加上大于号“>”
>聪明的愚者


流程图（略）

md文件导出为其他文件

##Python编程：从入门到实践

###字符串
name.title()
name.upper()
name.lower()

f字符串
```Python
first_name = "ada"
last_name = "lovelace"
fulll_name = f"{first_name} {last_name}"
message = f"Hello,{full_name.title()}!"
```

删除空白
❶ >>> favorite_language = ' python '
❷ >>> favorite_language.rstrip()
 ' python'
❸ >>> favorite_language.lstrip()
 'python '
❹ >>> favorite_language.strip()
 'python'

 删除前缀
>>> nostarch_url = 'https://nostarch.com'
>>> nostarch_url.removeprefix('https://')
'nostarch.com'


常量
常量（constant）是在程序的整个⽣命周期内都保持不变的变量。Python 没
有内置的常量类型，但 Python 程序员会使⽤全⼤写字⺟来指出应将某个变
量视为常量，其值应始终不变

列表
append追加
insert插入
del
pop()弹栈，可加索引
remove()根据值删除元素
sort()对列表永久排序
car.sort(reverse=True)
sorted()临时排序
reverse()
len()

使用range()创建数值列表
numbers = list(range(1,6))

列表推导式
squares = [value**2 for value in range(1,11)]

切片
players[0:3]

![](2024-03-10-16-58-41.png)

复制列表
players[:]

元组
列表⾮常适合⽤于存储在程序运⾏期间可能变化的数据集。列表是可以修
改的，这对于处理⽹站的⽤户列表或游戏中的⾓⾊列表⾄关重要。然⽽，
你有时候需要创建⼀系列不可修改的元素，元组可满⾜这种需求。Python
将不能修改的值称为不可变的，⽽不可变的列表称为元组（tuple）。

```Python
requested_toppings = []
if requested_toppings:
    for requested_topping in requested_toppings:
        print(f"Adding {requested_topping}.")
        print("\nFinished making your pizza!")
else:
 print("Are you sure you want a plain pizza?")
```

使用多个列表
```Python
available_toppings = ['mushrooms', 'olives', 'green peppers','pepperoni', 'pineapple', 'extra cheese'] 
requested_toppings = ['mushrooms', 'french fries', 'extra cheese']
for requested_topping in requested_toppings:
    if requested_topping in available_toppings:
        print(f"Adding {requested_topping}.")
    else:
        print(f"Sorry, we don't have {requested_topping}.")
print("\nFinished making your pizza!")
```

一个简单的字典
```Python
alien_0 = {'color'：'green','point':5}
print(alien_0['color'])
print(alien_0['points'])
#添加键值对
alien_0['x_position'] = 0
alien_0['y_position'] = 25
#删除键值对
del
```

由类似的对象组成的字典
```Python
favorite_languages = {
 'jen': 'python',
 'sarah': 'c',
 'edward': 'rust',
 'phil': 'python',
 }
```

可使⽤ get() ⽅法在指定的键不存在时返回⼀个默认值。get() ⽅
法的第⼀个参数⽤于指定键，是必不可少的；第⼆个参数为当指定的键不
存在时要返回的值，是可选的：

遍历字典的所有键值对
```Python
user_0 = {
    'username': 'efermi',
    'first': 'enrico',
    'last': 'fermi',
}

for key,value in user_0.items():
    print(f"\nKey:{key})
    print(f"value:{value}")
```

遍历字典中的所有键
keys()
```Python
favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'rust',
    'phil': 'python',
 }
for name in favorite_languages.keys():
    print(name.title())
```

遍历字典时，默认遍历所有的键

遍历字典中的所有值，values()
```python
for language in set(favorite_languages.values()):
```
用set剔除重复项

嵌套
```python
alien_0 = {'color': 'green', 'points': 5}
alien_1 = {'color': 'yellow', 'points': 10}
alien_2 = {'color': 'red', 'points': 15}
aliens = [alien_0, alien_1, alien_2]
for alien in aliens:
    print(alien)
```

字典列表
```python
# 创建⼀个⽤于存储外星⼈的空列表
 aliens = []
# 创建 30 个绿⾊的外星⼈
for alien_number in range(30):
    new_alien = {'color': 'green', 'points': 5, 'speed': 'slow'}
    aliens.append(new_alien)
# 显⽰前 5 个外星⼈
for alien in aliens[:5]:
    print(alien)
print("...")
# 显⽰创建了多少个外星⼈
print(f"Total number of aliens: {len(aliens)}")
```

在字典中存储列表
```python
# 存储顾客所点⽐萨的信息
pizza = {
    'crust': 'thick',
    'toppings': ['mushrooms', 'extra cheese'],
 }
# 概述顾客点的⽐萨
print(f"You ordered a {pizza['crust']}-crust pizza " "with the following toppings:")
for topping in pizza['toppings']:
    print(f"\t{topping}")
```

在字典中存储字典

input()解读为字符串
int()获取数值输入


for 循环是⼀种遍历列表的有效⽅式，但不应该在 for 循环中修改列表，
否则将导致 Python 难以跟踪其中的元素。要在遍历列表的同时修改它，可
使⽤ while 循环。通过将 while 循环与列表和字典结合起来使⽤，可收
集、存储并组织⼤量的输⼊，供以后查看和使⽤。

```python
# ⾸先，创建⼀个待验证⽤户列表
# 和⼀个⽤于存储已验证⽤户的空列表
unconfirmed_users = ['alice', 'brian', 'candace']
confirmed_users = []
# 验证每个⽤户，直到没有未验证⽤户为⽌
# 将每个经过验证的⽤户都移到已验证⽤户列表中
while unconfirmed_users:
    current_user = unconfirmed_users.pop()
    print(f"Verifying user: {current_user.title()}")
    confirmed_users.append(current_user)
# 显⽰所有的已验证⽤户
print("\nThe following users have been confirmed:")
for confirmed_user in confirmed_users:
    print(confirmed_user.title())
```

删除为特定值的所有列表元素
```python
pets = ['dog', 'cat', 'dog', 'goldfish', 'cat', 'rabbit', 'cat']
print(pets)
while 'cat' in pets:
    pets.remove('cat')
print(pets)
```

使用用户输入填充字典
```python
responses = {}
# 设置⼀个标志，指出调查是否继续
polling_active = True
while polling_active:
# 提⽰输⼊被调查者的名字和回答
    name = input("\nWhat is your name? ")
    response = input("Which mountain would you like to climb someday?")
# 将回答存储在字典中
    responses[name] = response
# 看看是否还有⼈要参与调查
    repeat = input("Would you like to let another person respond?(yes/no) ")
    if repeat == 'no':
        polling_active = False
# 调查结束，显⽰结果
print("\n--- Poll Results ---")
for name, response in responses.items():
    print(f"{name} would like to climb {response}.")
```

函数
"""文档字符串"""
位置实参

关键字实参
```python
def describe_pet(animal_type, pet_name):
    """显⽰宠物的信息"""
    print(f"\nI have a {animal_type}.")
    print(f"My {animal_type}'s name is {pet_name.title()}.")

describe_pet(animal_type='hamster', pet_name='harry')
```
默认值

让实参变成可选的
为让中间名变成可选的，可给形参 middle_name 指
定默认值（空字符串），在⽤户不提供中间名时不使⽤这个形参。为了让
get_formatted_name() 在没有提供中间名时依然正确运⾏，可给形参
middle_name 指定默认值（空字符串），并将其移到形参列表的末尾
middle_name=''

返回字典

传递列表
```python
def greet_users(names):
"""向列表中的每个⽤户发出简单的问候"""
    for name in names:
        msg = f"Hello, {name.title()}!"
        print(msg)

usernames = ['hannah', 'ty', 'margot']
greet_users(usernames)
```

传递任意数量的实参
```python
def make_pizza(*toppings):
"""打印顾客点的所有配料"""
    print(toppings)

make_pizza('pepperoni')
make_pizza('mushrooms', 'green peppers', 'extra cheese')
```
形参名 *toppings 中的星号让 Python 创建⼀个名为 toppings 的元组，
该元组包含函数收到的所有值。函数体内的函数调⽤ print() ⽣成的输出
证明，Python 既能处理使⽤⼀个值调⽤函数的情形，也能处理使⽤三个值
调⽤函数的情形。它以类似的⽅式处理不同的调⽤。注意，Python 会将实
参封装到⼀个元组中，即便函数只收到⼀个值也是如此

使⽤任意数量的关键字实参
```python
def build_profile(first, last, **user_info):
"""创建⼀个字典，其中包含我们知道的有关⽤户的⼀切"""
    user_info['first_name'] = first
    user_info['last_name'] = last
    return user_info
user_profile = build_profile('albert', 'einstein',location='princeton',field='physics')
print(user_profile)
```
build_profile() 函数的定义要求提供名和姓，同时允许根据需要提供
任意数量的名值对。形参 **user_info 中的两个星号让 Python 创建⼀个
名为 user_info 的字典，该字典包含函数收到的其他所有名值对。在这
个函数中，可以像访问其他字典那样访问 user_info 中的名值对。

将函数存储在模块中
使⽤函数的优点之⼀是可将代码块与主程序分离。通过给函数指定描述性
名称，能让程序容易理解得多。你还可以更进⼀步，将函数存储在称为模
块的独⽴⽂件中，再将模块导⼊（import）主程序。import 语句可让你在
当前运⾏的程序⽂件中使⽤模块中的代码。

导⼊特定的函数

使⽤ as 给函数指定别名

函数编写指南
在编写函数时，需要牢记⼏个细节。应给函数指定描述性名称，且只使⽤
⼩写字⺟和下划线。描述性名称可帮助你和别⼈明⽩代码想要做什么。在
给模块命名时也应遵循上述约定。
在给形参指定默认值时，等号两边不要有空格

面向对象编程：类

创建Dog类
```python
class Dog:
    """⼀次模拟⼩狗的简单尝试"""
    def __init__(self, name, age):
    """初始化属性 name 和 age"""
        self.name = name
        self.age = age
    def sit(self):
    """模拟⼩狗收到命令时坐下"""
        print(f"{self.name} is now sitting.")
    def roll_over(self):
    """模拟⼩狗收到命令时打滚"""
    print(f"{self.name} rolled over!")
```

__init__() ⽅法:是⼀个特殊⽅法，每当你根据 Dog 类创建新实例时，Python 都会⾃动运⾏
它。在这个⽅法的名称中，开头和末尾各有两个下划线，这是⼀种约定，
旨在避免 Python 默认⽅法与普通⽅法发⽣名称冲突。务必确保
__init__() 的两边都有两个下划线，否则当你使⽤类来创建实例时，将
不会⾃动调⽤这个⽅法，进⽽引发难以发现的错误。
我们将 __init__() ⽅法定义成包含三个形参：self、name 和 age。在
这个⽅法的定义中，形参 self 必不可少，⽽且必须位于其他形参的前
⾯。为何必须在⽅法定义中包含形参 self 呢？因为当 Python 调⽤这个⽅
法来创建 Dog 实例时，将⾃动传⼊实参 self。每个与实例相关联的⽅法
调⽤都会⾃动传递实参 self，该实参是⼀个指向实例本⾝的引⽤，让实例
能够访问类中的属性和⽅法。
在 __init__() ⽅法内定义的两个变量都有前缀 self（⻅❸）。以self
为前缀的变量可供类中的所有⽅法使⽤，可以通过类的任意实例来访问。
self.name = name 获取与形参 name 相关联的值，并将其赋给变量
name，然后该变量被关联到当前创建的实例。self.age = age 的作⽤
与此类似。像这样可通过实例访问的变量称为属性（attribute）。

根据类创建实例
```python
my_dog = Dog('Willie', 6)
print(f"My dog's name is {my_dog.name}.")
print(f"My dog is {my_dog.age} years old.")
```

给属性指定默认值
有些属性⽆须通过形参来定义，可以在 __init__() ⽅法中为其指定默认
值。
下⾯来添加⼀个名为 odometer_reading 的属性，其初始值总是为 0。我
们还添加了⼀个名为 read_odometer() 的⽅法，⽤于读取汽⻋的⾥程
表
```python
class Car:
    def __init__(self, make, model, year):
    """初始化描述汽⻋的属性"""
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0
    def get_descriptive_name(self):
        --snip--
❷   def read_odometer(self):
    """打印⼀条指出汽⻋⾏驶⾥程的消息"""
        print(f"This car has {self.odometer_reading} miles on it.")
 my_new_car = Car('audi', 'a4', 2024)
 print(my_new_car.get_descriptive_name())
 my_new_car.read_odometer()
```

修改属性的值

1.直接修改属性的值
2.通过方法修改属性的值
3.通过方法让属性的值递增

继承
当⼀个类继承另⼀个类时，将⾃动获
得后者的所有属性和⽅法。原有的类称为⽗类（parent class），⽽新类称为
⼦类（child class）。⼦类不仅继承了⽗类的所有属性和⽅法，还可定义⾃
⼰的属性和⽅法

子类的_init_()方法
在既有的类的基础上编写新类，通常要调⽤⽗类的 __init__() ⽅法。这
将初始化在⽗类的 __init__() ⽅法中定义的所有属性，从⽽让⼦类也可
以使⽤这些属性。

```python
class Car:
 """⼀次模拟汽⻋的简单尝试"""
    def __init__(self, make, model, year):
    """初始化描述汽⻋的属性"""
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0
    def get_descriptive_name(self):
    """返回格式规范的描述性名称"""
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name.title()
    def read_odometer(self):
    """打印⼀个句⼦，指出汽⻋的⾏驶⾥程"""
        print(f"This car has {self.odometer_reading} miles on it.")
    def update_odometer(self, mileage):
    """将⾥程表读数设置为给定的值"""
        if mileage >= self.odometer_reading:
            self.odometer_reading = mileage
        else:
            print("You can't roll back an odometer!")
    def increment_odometer(self, miles):
    """让⾥程表读数增加给定的量"""
        self.odometer_reading += miles
class ElectricCar(Car):
 """电动汽⻋的独特之处"""
    def __init__(self, make, model, year):
    """初始化⽗类的属性"""
        super().__init__(make, model, year)
my_leaf = ElectricCar('nissan', 'leaf', 2024)
print(my_leaf.get_descriptive_name())
```

⾸先是 Car 类的代码（⻅❶）。在创建⼦类时，⽗类必须包含在当前⽂件
中，且位于⼦类前⾯。接下来，定义⼦类 ElectricCar（⻅❷）。在定义
⼦类时，必须在括号内指定⽗类的名称。__init__() ⽅法接受创建 Car
实例所需的信息（⻅❸）。
super() 是⼀个特殊的函数，让你能够调⽤⽗类的⽅法（⻅❹）。这⾏代
码让 Python 调⽤ Car 类的 __init__() ⽅法，从⽽让 ElectricCar 实
例包含这个⽅法定义的所有属性。⽗类也称为超类（superclass），函数名
super 由此得名。
为了测试继承能够正确地发挥作⽤，我们尝试创建⼀辆电动汽⻋，但提供
的信息与创建燃油汽⻋时相同。在❺处，创建 ElectricCar 类的⼀个实
例，并将其赋给变量 my_leaf。这⾏代码调⽤ ElectricCar 类中定义的
__init__() ⽅法，后者让 Python 调⽤⽗类 Car 中定义的 __init__()
⽅法。我们提供了实参 'nissan'、'leaf' 和 2024

给子类定义属性和方法
让⼀个类继承另⼀个类后，就可以添加区分⼦类和⽗类所需的新属性和新
⽅法了。
下⾯添加⼀个电动汽⻋特有的属性（电池），以及⼀个描述该属性的⽅
法。我们将存储电池容量，并编写⼀个⽅法打印对电池的描述

重写父类中的方法

将实例用作属性
在使⽤代码模拟实物时，你可能会发现⾃⼰给类添加了太多细节：属性和
⽅法越来越多，⽂件越来越⻓。在这种情况下，可能需要将类的⼀部分提
取出来，作为⼀个独⽴的类。将⼤型类拆分成多个协同⼯作的⼩类，这种
⽅法称为组合（composition）。

```python
class Car:
--snip--
class Battery:
"""⼀次模拟电动汽⻋电池的简单尝试"""
    def __init__(self, battery_size=40):
    """初始化电池的属性"""
        self.battery_size = battery_size
    def describe_battery(self):
    """打印⼀条描述电池容量的消息"""
        print(f"This car has a {self.battery_size}-kWh battery.")
class ElectricCar(Car):
"""电动汽⻋的独特之处"""
    def __init__(self, make, model, year):
"""
先初始化⽗类的属性，再初始化电动汽⻋特有的属性
"""
    super().__init__(make, model, year)
    self.battery = Battery()
 
 my_leaf = ElectricCar('nissan', 'leaf', 2024)
 print(my_leaf.get_descriptive_name())
 my_leaf.battery.describe_battery()
```

模拟实物
这让你进⼊了程序员的另⼀个境界：在解决上述问题时，从较⾼的逻辑层
⾯（⽽不是语法层⾯）思考。你考虑的不是 Python，⽽是如何使⽤代码来
表⽰实际事物。达到这种境界后，你会经常发现，对现实世界的建模⽅法
没有对错之分。有些⽅法的效率更⾼，但要找出效率最⾼的表⽰法，需要
⼀定的实践。只要代码能够像你希望的那样运⾏，就说明你已经做得很好
了！即便发现⾃⼰不得不多次尝试使⽤不同的⽅法来重写类，也不必⽓
馁。要编写出⾼效、准确的代码，这是必经之路

导入类
模块级⽂档字符串，对该模块的内容做了简要的描述。你应该
为⾃⼰创建的每个模块编写⽂档字符串。

导⼊类是⼀种⾼效的编程⽅式。如果这个程序包含整个 Class 类，它该有
多⻓啊！通过将这个类移到⼀个模块中并导⼊该模块，依然可使⽤其所有
功能，但主程序⽂件变得整洁易读了。这还让你能够将⼤部分逻辑存储在
独⽴的⽂件中。在确定类能像你希望的那样⼯作后，就可以不管这些⽂
件，专注于主程序的⾼级逻辑了

在一个模块中存储多个类

从一个模块中导入多个类

导入整个模块
先导⼊整个模块，再使⽤点号访问需要的类

导入模块中的所有类

使用别名

找到合适的工作流程
⼀开始应让代码结构尽量简单。⾸先尝试在⼀个⽂件中完成所有的⼯作，
确定⼀切都能正确运⾏后，再将类移到独⽴的模块中。如果你喜欢模块和
⽂件的交互⽅式，可在项⽬开始时就尝试将类存储到模块中。先找出让你
能够编写出可⾏代码的⽅式，再尝试让代码更加整洁

python标准库
randint()它将两个整数作为参数，
并随机返回⼀个位于这两个整数之间（含）的整数。下⾯演⽰了如何⽣成
⼀个位于 1 和 6 之间的随机整数

```python
from random import randint
randint(1, 6)
3
```

choice()它将⼀个列表或
元组作为参数，并随机返回其中的⼀个元素：

```python
from random import choice
players = ['charles', 'martina', 'michael', 'florence', 'eli']
first_up = choice(players)
first_up
'florence
```

在创建与安全相关的应⽤程序时，不要使⽤模块 random，但它能⽤来创建
众多有趣的项⽬。

类的编程风格
类名应采⽤驼峰命名法，即将类名中的每个单词的⾸字⺟都⼤写，并且不
使⽤下划线。实例名和模块名都采⽤全⼩写格式，并在单词之间加上下划
线。

可以使⽤空⾏来组织代码，但不宜过多。在类中，可以使⽤⼀个空⾏来分
隔⽅法；⽽在模块中，可以使⽤两个空⾏来分隔类。
当需要同时导⼊标准库中的模块和你编写的模块时，先编写导⼊标准库模
块的 import 语句，再添加⼀个空⾏，然后编写导⼊你⾃⼰编写的模块的
import 语句。在包含多条 import 语句的程序中，这种做法让⼈更容易
明⽩程序使⽤的各个模块来⾃哪⾥。

文件和异常

要使⽤⽂件的内容，需要将其路径告知 Python。路径（path）指的是⽂件或
⽂件夹在系统中的准确位置。Python 提供了 pathlib 模块，让你能够更轻
松地在各种操作系统中处理⽂件和⽬录。提供特定功能的模块通常称为库
（library）。这就是这个模块被命名为 pathlib 的原因所在
这⾥⾸先从 pathlib 模块导⼊ Path 类。Path 对象指向⼀个⽂件，可⽤
来做很多事情。例如，让你在使⽤⽂件前核实它是否存在，读取⽂件的内
容，以及将新数据写⼊⽂件。这⾥创建了⼀个表⽰⽂件 pi_digits.txt 的
Path 对象，并将其赋给了变量 path（⻅❶）。由于这个⽂件与当前编写
的 .py ⽂件位于同⼀个⽬录中，因此 Path 只需要知道其⽂件名就能访问
它。

```python
from pathlib import Path

path = Path('pi_digits.txt')
contents = path.read_text()
print(contents)
```
read_text() 将该⽂件的全部内容作为⼀个字符串返回,read_text() 在到达⽂件末尾时会返回⼀个空字符串，⽽这个空字符串会被显⽰为⼀个空⾏。

方法链式调用
这⾏代码先让 Python 对当前处理的⽂件调⽤ read_text() ⽅法，再对
read_text() 返回的字符串调⽤ rstrip() ⽅法，然后将整理好的字符
串赋给变量 contents。
```python
contents = path.read_text().rstrip()
```

相对文件路径和绝对文件路径

访问文件中的各行
使⽤ splitlines() ⽅法将冗⻓的字符串转换为⼀系列⾏，再使⽤
for 循环以每次⼀⾏的⽅式检查⽂件中的各⾏：
```python
from pathlib import Path
 
path = Path('pi_digits.txt')
contents = path.read_text()
lines = contents.splitlines()
for line in lines:
    print(line)
```
splitlines() ⽅法返回⼀个列
表，其中包含⽂件中所有的⾏，⽽我们将这个列表赋给了变量 lines

使用文件的内容
注意：在读取⽂本⽂件时，Python 将其中的所有⽂本都解释为字符
串。如果读取的是数，并且要将其作为数值使⽤，就必须使⽤ int()
函数将其转换为整数，或者使⽤ float() 函数将其转换为浮点数。

写入文件

写入一行
定义⼀个⽂件的路径后，就可使⽤ write_text() 将数据写⼊该⽂件了

注意：Python 只能将字符串写⼊⽂本⽂件。如果要将数值数据存储到
⽂本⽂件中，必须先使⽤函数 str() 将其转换为字符串格式。

写入多行
write_text() ⽅法会在幕后完成⼏项⼯作。⾸先，如果 path 变量对应
的路径指向的⽂件不存在，就创建它。其次，将字符串写⼊⽂件后，它会
确保⽂件得以妥善地关闭。如果没有妥善地关闭⽂件，可能会导致数据丢
失或受损。
```python
from pathlib import Path

contents = "I love programming.\n"
contents += "I love creating new games.\n"
contents += "I also love working with data.\n"
path = Path('programming.txt')
path.write_text(contents)
```
注意：在对 path 对象调⽤ write_text() ⽅法时，务必谨慎。如果
指定的⽂件已存在， write_text() 将删除其内容，并将指定的内容
写⼊其中。

异常
Python 使⽤称为异常（exception）的特殊对象来管理程序执⾏期间发⽣的
错误。每当发⽣让 Python 不知所措的错误时，它都会创建⼀个异常对象。
如果你编写了处理该异常的代码，程序将继续运⾏；如果你未对异常进⾏
处理，程序将停⽌，并显⽰⼀个 traceback，其中包含有关异常的报告。

使用try-except代码块
```python
try:
    print(5/0)
except ZeroDivisionError:
    print("You can't divide by zero!")
```

else代码块
这个⽰例还包含⼀个 else 代码块，只有 try
代码块成功执⾏才需要继续执⾏的代码，都应放到 else 代码块中
```python
 --snip--
while True:
 --snip--
    if second_number == 'q':
        break
    try:
        answer = int(first_number) / int(second_number)
    except ZeroDivisionError:
        print("You can't divide by 0!")
    else:
        print(answer)
```
依赖 try 代码块成功执⾏的代码都被放在else 代码块中

只有可能引发异常的代码才需要放在 try 语句中。有时候，有⼀些仅在
try 代码块成功执⾏时才需要运⾏的代码，这些代码应放在 else 代码块
中。except 代码块告诉 Python，如果在尝试运⾏ try 代码块中的代码时
引发了指定的异常该怎么办

分析文本
使⽤ split() ⽅法，它默认以空⽩为分隔符将字符串分拆成多个部分
```python
from pathlib import Path
path = Path('alice.txt')
try:
    contents = path.read_text(encoding='utf-8')
except FileNotFoundError:
    print(f"Sorry, the file {path} does not exist.")
else:
    #计算⽂件⼤致包含多少个单词
    words = contents.split()
    num_words = len(words)
print(f"The file {path} has about {num_words} words.")
```

使用多个文件
```python
from pathlib import Path

def count_words(filename):
 --snip--
    filenames = ['alice.txt', 'siddhartha.txt', 'moby_dick.txt', 'little_women.txt']
    for filename in filenames:
        path = Path(filename)
        count_words(path)
```

静默失败
但并⾮每次捕获异常都需要告诉⽤户，你有时候希望程序在发⽣异常时保持静默，就像什么都
没有发⽣⼀样继续运⾏。

```python
def count_words(path):
 """计算⼀个⽂件⼤致包含多少个单词"""
    try:
 --snip--
    except FileNotFoundError:
        pass
    else:
 --snip--
```

存储数据
json.dumps() 函数接受⼀个实参，即要转换为 JSON 格式的数据。这个函数返回⼀个字符串
```python
from pathlib import Path
import json
 
numbers = [2,3,5,7,11,13]
path = Path('numbers.json')
contents = json.dumps(numbers)
path.write_text(contents)
```

使⽤ json.loads() 将这个列表读取到内存中
```python
from pathlib import Path
import json

path = Path('numbers.json')
contents = path.read_text()
numbers = json.loads(contents)

print(numbers)
```

Path 类提供了很多很有⽤的⽅法。如果指定的⽂件或⽂件夹存在，
exists() ⽅法返回 True，否则返回 False。这⾥使⽤
path.exists() 来确定是否存储了⽤户名（⻅❶）。如果⽂件
username.json 存在，就加载其中的⽤户名，并向⽤户发出个性化问候。

测试代码
学习如何使⽤ pytest 来测试代码。pytest 库是⼀组⼯
具，不仅能帮助你快速⽽轻松地编写测试，⽽且能持续⽀持随项⽬增⼤⽽
变得复杂的测试。Python 默认不包含 pytest，因此你将学习如何安装外
部库

测试函数
所幸 pytest 提供了⼀种⾃动测试函数输出的⾼效⽅式

单元测试和测试用例
断言
```python
from name_function import get_formatted_name

def test_first_last_name():
"""能够正确地处理像 Janis Joplin 这样的姓名吗？"""
    formatted_name = get_formatted_name('janis', 'joplin')
    assert formatted_name == 'Janis Joplin'
```
测试⽂件的名称很重要，必须以test_打头。当你让 pytest 运⾏测试时，它将查找以 test_打头的⽂件，并运⾏其中的所有测试

运行测试
如果直接运⾏⽂件 test_name_function.py，将不会有任何输出，因为我们没
有调⽤这个测试函数。相反，应该让 pytest 替我们运⾏这个测试⽂件。
为此，打开⼀个终端窗⼝，并切换到这个测试⽂件所在的⽂件夹。如果你
使⽤的是 VS Code，可打开测试⽂件所在的⽂件夹，并使⽤该编辑器内嵌
的终端。在终端窗⼝中执⾏命令 pytest

通过


     $ pytest
        ========================= test session starts
        =========================
        ❶ platform darwin -- Python 3.x.x, pytest-7.x.x, pluggy-1.x.x
        ❷ rootdir: /.../python_work/chapter_11
        ❸ collected 1 item
        ❹ test_name_function.py . 
        [100%]
        ========================== 1 passed in 0.00s
        ==========================

不通过

 
        $ pytest
        ========================= test session starts
        =========================
        --snip--
        ❶ test_name_function.py F 
        [100%]
        ❷ ============================== FAILURES
        ===============================
        ❸ ________________________ test_first_last_name
        _________________________
        def test_first_last_name():
        """能够正确地处理像 Janis Joplin 这样的姓名吗?"""
        ❹ > formatted_name = get_formatted_name('janis', 'joplin')
        ❺ E TypeError: get_formatted_name() missing 1 required positional
        argument: 'last'
        test_name_function.py:5: TypeError
        ======================= short test summary info
        =======================
        FAILED test_name_function.py::test_first_last_name - TypeError:
        get_formatted_name() missing 1 required positional argument:
        'last'
        ========================== 1 failed in 0.04s
        ==========================

测试类
断言
![](2024-03-11-09-06-48.png)

使用夹具
在测试中，夹具（fixture）可帮助我们搭建测试环境。这通常意味着创建供
多个测试使⽤的资源。在 pytest 中，要创建夹具，可编写⼀个使⽤装饰
器 @pytest.fixture 装饰的函数。装饰器（decorator）是放在函数定义
前⾯的指令。在运⾏函数前，Python 将该指令应⽤于函数，以修改函数代
码的⾏为。这听起来很复杂，但是不⽤担⼼：即便没有学习如何编写装饰
器，也可使⽤第三⽅包中的装饰器
```python
import pytest
from survey import AnonymousSurvey

@pytest.fixture
def language_survey():
"""⼀个可供所有测试函数使⽤的 AnonymousSurvey 实例"""
    question = "What language did you first learn to speak?"
    language_survey = AnonymousSurvey(question)
    return language_survey
def test_store_single_response(language_survey):
"""测试单个答案会被妥善地存储"""
    language_survey.store_response('English')
    assert 'English' in language_survey.responses
def test_store_three_responses(language_survey):
"""测试三个答案会被妥善地存储"""
    responses = ['English', 'Spanish', 'Mandarin']
    for response in responses:
        language_survey.store_response(response)
    for response in responses:
        assert response in language_survey.responses
```
现在需要导⼊ pytest，因为我们使⽤了其中定义的⼀个装饰器。我们将装
饰器 @pytest.fixture（⻅❶）应⽤于新函数language_survey()
（⻅❷）。这个函数创建并返回⼀个AnonymousSurvey 对象
请注意，两个测试函数的定义都变了（⻅❸和❺）：都有⼀个名为
language_survey 的形参。当测试函数的⼀个形参与应⽤了装饰器
@pytest.fixture 的函数（夹具）同名时，将⾃动运⾏夹具，并将夹具
返回的值传递给测试函数。在这个⽰例中，language_survey() 函数向
test_store_single_response() 和test_store_three_responses() 提供了⼀个 language_survey 实例。

##使用Git进行版本控制

安装Git

配置Git

创建项目
我们来创建⼀个要进⾏版本控制的项⽬。在系统中创建⼀个⽂件夹，并将
其命名为 git_practice。

忽略文件
扩展名为 .pyc 的⽂件是根据 .py ⽂件⾃动⽣成的，因此⽆须让 Git 跟踪它
们。这些⽂件存储在⽬录 __pycache__ 中。为了让 Git 忽略这个⽬录，创建
⼀个名为 .gitignore 的特殊⽂件（这个⽂件名以句点打头，且没有扩展
名），并在其中添加如下⼀⾏内容
![](2024-03-11-13-34-48.png)

这会让 Git 忽略⽬录 __pycache__ 中的所有⽂件。使⽤⽂件 .gitignore 可避
免混乱，让项⽬开发起来更容易。
你可能需要修改⽂件浏览器的设置，使其显⽰隐藏的⽂件（名称以句点打
头的⽂件）：在 Windows 资源管理器中，选择菜单“查看”中的复选框“隐藏
的项⽬”；在 macOS 系统中，按组合键 Command + Shift + .（句点）；在
Linux 系统中，查找并选择设置 Show Hidden Files（显⽰隐藏的⽂件）

初始化仓库
前⾯创建了⼀个⽬录，其中包含⼀个 Python ⽂件和⼀个 .gitignore ⽂件，现
在可以初始化⼀个 Git 仓库了。为此，打开⼀个终端窗⼝，切换到⽂件夹
git_practice，并执⾏如下命令：


        git_practice$ git init
        Initialized empty Git repository in git_practice/.git/
        git_practice$

输出表明 Git 在 git_practice 中初始化了⼀个空仓库。仓库（repository）是
程序中被 Git 主动跟踪的⼀组⽂件。Git ⽤来管理仓库的⽂件都存储在隐藏
的⽬录 .git 中。虽然你根本不需要与这个⽬录打交道，但千万不要删除它，
否则将丢失项⽬的所有历史记录。

检查状态

            git_practice$ git status
            ❶ On branch main
            No commits yet
            ❷ Untracked files:
            (use "git add <file>..." to include in what will be committed)
            .gitignore
            hello_git.py
            ❸ nothing added to commit but untracked files present (use "git add" to
            track)
            git_practice$

在 Git 中，分⽀（branch）是项⽬的⼀个版本。从这⾥的输出可知，我们位
于分⽀ main 上（⻅❶）。每当查看项⽬的状态时，输出都将指出位于分⽀
main 上。接下来的输出表明，还未执⾏任何提交。提交（commit）是项⽬
在特定时间点的快照
Git 指出了项⽬中未被跟踪的⽂件（⻅❷），因为还没有告诉它要跟踪哪些
⽂件。接下来，Git 告诉我们没有将任何东⻄添加到当前的提交中，并且指
出了可能需要加⼊仓库的未跟踪⽂件（⻅❸）

将文件加入仓库


        ❶ git_practice$ git add .
        ❷ git_practice$ git status
        On branch main
        No commits yet
        Changes to be committed:
        (use "git rm --cached <file>..." to unstage)
        ❸ new file: .gitignore
        new file: hello_git.py
        git_practice$

命令 git add . 将项⽬中未被跟踪的所有⽂件（条件是没有在 .gitignore
中列出）都加⼊仓库（⻅❶）。它不提交这些⽂件，只是让 Git 关注它们。
现在检查项⽬的状态，会发现 Git 找出了⼀些需要提交的修改（⻅❷）。
new file 意味着这些⽂件是新添加到仓库中的（⻅❸）。

执行提交

        ❶ git_practice$ git commit -m "Started project."
        ❷ [main (root-commit) cea13dd] Started project.
        ❸ 2 files changed, 5 insertions(+)
        create mode 100644 .gitignore
        create mode 100644 hello_git.py
        ❹ git_practice$ git status
        On branch main
        nothing to commit, working tree clean
        git_practice$

我们执⾏命令 git commit -m "message"（⻅❶）创建项⽬的快照。
标志 -m 让 Git 将接下来的消息（Started project.）记录到项⽬的历
史记录中。输出表明我们位于分⽀ main 上（⻅❷）且有两个⽂件被修改了
（⻅❸）。
现在检查状态，将发现我们位于分⽀ main 上且⼯作树是⼲净的（⻅❹）。
这是在每次提交项⽬的可⾏状态时都应该看到的消息。如果显⽰的消息不
是这样的，请仔细阅读，很可能是你在提交前忘记了添加⽂件

查看提交历史
git log

每次提交时，Git 都会⽣成⼀个独⼀⽆⼆的引⽤ ID，⻓度为 40 个字符。它
记录提交是谁执⾏的，提交的时间，以及提交时指定的消息。并⾮在任何
情况下都需要所有这些信息，因此 Git 提供了⼀个选项，让你能够打印提交
历史条⽬的简单版本

git log --pretty=oneline
标志 --pretty=oneline 指定显⽰两项最重要的信息：提交的引⽤ ID，
以及为提交记录的消息

放弃修改
下⾯来看看如何放弃所做的修改，恢复到上⼀个可⾏状态
Git 注意到我们修改了 hello_git.py（⻅❶）。如果愿意，可以提交所做的修
改，但这次我们不提交所做的修改，⽽是恢复到最后⼀个提交（我们知
道，那次提交时项⽬能够正常地运⾏）。为此，我们不对 hello_git.py 执⾏
任何操作（既不删除刚添加的代码⾏，也不使⽤⽂本编辑器的撤销功
能），⽽是在终端会话中执⾏如下命令
git_practice$ git restore 
git_practice$ git status

在这个简单的项⽬中，恢复到之前某个状态的能⼒看似微不⾜道，但如果
开发的是⼤型项⽬，其中数⼗个⽂件都被修改了，那么通过恢复到上⼀个
状态，将撤销最后⼀次提交后对这些⽂件所做的所有修改。这个功能很有
⽤：在实现新功能时，可根据需要做任意数量的修改；如果这些修改不可
⾏，可撤销它们，⽽不会影响项⽬。你⽆须记住做了哪些修改并⼿动撤销
所做的修改，Git 会替你完成所有这些⼯作

检出以前的提交
要检出提交历史中的任何提交，可使⽤命令 checkout，并指定该提交的
引⽤ ID 的前 6 个字符。检出并检查以前的提交后，既可以返回最后⼀次提
交，也可以放弃最近所做的⼯作并选择以前的提交
检出以前的提交后，将离开分⽀ main，并进⼊ Git 所说的分离头指针
（detached HEAD）状态（⻅❶）。HEAD 表⽰当前提交的项⽬状态。之所
以说处于分离状态（detached），是因为离开了⼀个具名分⽀（这⾥是
main）。
要回到分⽀ main，可按建议（⻅❷）所说的那样撤销上⼀个操作
这样就回到分⽀ main 了。除⾮要使⽤ Git 的⾼级功能，否则在检出以前的
提交后，最好不要对项⽬做任何修改。然⽽，如果参与项⽬开发的⼈只有
你⾃⼰，⽽你⼜想放弃最近的所有提交并恢复到以前的状态，也可将项⽬
重置到以前的提交。

删除仓库
有时候，仓库的历史记录被弄乱了，⽽你⼜不知道如何恢复。在这种情况
下，⾸先应考虑使⽤附录 C 介绍的⽅法寻求帮助。如果⽆法恢复且参与项
⽬开发的只有你⼀个⼈，可继续使⽤这些⽂件，但将项⽬的历史记录删除
——删除⽬录 .git。这不会影响任何⽂件的当前状态，只会删除所有的提
交，因此将⽆法检出项⽬的其他任何状态。
为此，既可以打开⼀个⽂件浏览器并将⽬录 .git 删除，也可以通过命令⾏将
其删除。之后，需要重新创建⼀个仓库，以便重新对修改进⾏跟踪。

##项目
外星人入侵
规划项⽬
这个游戏由 run_game() ⽅法控制。该⽅法包含⼀个不断运⾏的 while
循环（⻅❸），⽽这个循环包含⼀个事件循环以及管理屏幕更新的代码。
事件是⽤户玩游戏时执⾏的操作，如按键或移动⿏标。为了让程序能够响
应事件，可编写⼀个事件循环，以侦听事件并根据发⽣的事件类型执⾏适
当的任务

我们使⽤ pygame.event.get() 函数来访问 Pygame 检测到的事件。这
个函数返回⼀个列表，其中包含它在上⼀次调⽤后发⽣的所有事件。所有
键盘和⿏标事件都将导致这个 for 循环运⾏。在这个循环中，我们将编写
⼀系列 if 语句来检测并响应特定的事件。例如，当玩家单击游戏窗⼝的关
闭按钮时，将检测到 pygame.QUIT 事件，进⽽调⽤ sys.exit() 来退出
游戏

处调⽤了pygame.display.flip()，命令 Pygame 让最近绘制的屏幕
可⻅。这⾥，它在每次执⾏ while 循环时都绘制⼀个空屏幕，并擦去旧屏
幕，使得只有新的空屏幕可⻅。我们在移动游戏元素时，
pygame.display.flip() 将不断更新屏幕，以显⽰新位置上的元素并隐
藏原来位置上的元素，从⽽营造平滑移动的效果

在这个⽂件末尾，创建⼀个游戏实例并调⽤ run_game()。这些代码被放
在⼀个 if 代码块中，仅当直接运⾏该⽂件时，它们才会执⾏。如果此时运
⾏ alien_invasion.py，将看到⼀个空的 Pygame 窗⼝

理想情况下，游戏在所有的系统中都应以相同的速度（帧率）运⾏。对于
可在多种系统中运⾏的游戏，控制帧率是个复杂的问题，好在 Pygame 提供
了⼀种相对简单的⽅式来达成这个⽬标。我们将创建⼀个时钟（clock），
并确保它在主循环每次通过后都进⾏计时（tick）。当这个循环的通过速度
超过我们定义的帧率时，Pygame 会计算需要暂停多⻓时间，以便游戏的运
⾏速度保持⼀致

tick() ⽅法接受⼀个参数：游戏的帧率。这⾥使⽤的值为 60， Pygame 将
尽可能确保这个循环每秒恰好运⾏ 60 次。

需要先加载⼀幅图像，再使⽤ Pygame blit() ⽅法绘制它。
最安全、成本最低的⽅式是使⽤ OpenGameArt 等⽹站提供的免费图形，这些素材⽆须授权许可即可使⽤和修改

在游戏中，可以使⽤⼏乎任意类型的图像⽂件，但使⽤位图（.bmp）⽂件
最为简单，因为 Pygame 默认加载位图。虽然可配置 Pygame 以使⽤其他⽂
件类型，但有些⽂件类型要求你在计算机上安装相应的图像库。⽹上的⼤
多数图像是 .jpg 和 .png 格式的，不过可以使⽤ Photoshop、GIMP 和 Paint等⼯具将其转换为位图。

pygame 之所以⾼效，是因为它让你能够把所有的游戏元素当作矩形（rect
对象）来处理，即便它们的形状并⾮矩形也⼀样。⽽把游戏元素当作矩形
来处理之所以⾼效，是因为矩形是简单的⼏何形状。例如，通过将游戏元
素视为矩形，Pygame 能够更快地判断出它们是否发⽣了碰撞。这种做法的
效果通常很好，游戏玩家⼏乎注意不到我们处理的不是游戏元素的实际形
状。在这个类中，我们将把⻜船和屏幕作为矩形进⾏处理

在处理 rect 对象时，可使⽤矩形的四个⾓及中⼼的 x 坐标和 y 坐标，通过
设置这些值来指定矩形的位置。如果要将游戏元素居中，可设置相应 rect
对象的属性 center、centerx 或 centery；要让游戏元素与屏幕边缘对
⻬，可设置属性 top、bottom、left 或 right。除此之外，还有⼀些组
合属性，如 midbottom、midtop、midleft 和 midright。要调整游戏
元素的⽔平或垂直位置，可使⽤属性 x 和 y，它们分别是相应矩形左上⾓
的 x 坐标和 y 坐标。这些属性让你⽆须去做游戏开发⼈员原本需要⼿动完
成的计算，因此很常⽤

在 Pygame 中，原点(0, 0)位于屏幕的左上⾓，当⼀个点向右下
⽅移动时，它的坐标值将增⼤。在 1200×800 的屏幕上，原点位于左上
⾓，右下⾓的坐标为(1200, 800)。这些坐标对应的是游戏窗⼝，⽽不是
物理屏幕。

##重构：_check_events() ⽅法和_update_screen() ⽅法
在⼤型项⽬中，经常需要在添加新代码前重构既有的代码。重构旨在简化
既有代码的结构，使其更容易扩展。本节将把越来越⻓的 run_game() ⽅
法拆分成两个辅助⽅法。辅助⽅法（helper method）⼀般只在类中调⽤，不
会在类外调⽤。在 Python 中，辅助⽅法的名称以单下划线打头


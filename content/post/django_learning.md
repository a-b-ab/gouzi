+++
title = 'Django'
date = 2024-04-21T13:28:01+08:00
draft = false
+++
<img src="https://raw.githubusercontent.com/a-b-ab/picture/main/Picgo202404221612743.jpg"/>

# Django

*基于蛇书的django项目*

## 建立项目

### 制定规范

### 建立虚拟环境
虚拟环境是系统的⼀个位置，你可在其中安装包，并将这些包与其他 Python 包隔离开来。将项⽬的
库与其他项⽬分离是有益的，为了部署到服务器，这也是必须的

    python -m venv ll_env

### 激活虚拟环境

    Linux:source ll_env/bin/activate
    Window:ll_env\Scripts\activate

### 安装Django

    pip install --upgrade pip
    pip install django
    安装特定版本： pip install django==4.1.*

### 在Django中创建项目

    django_admin startproject ll_project . 
    ls (在 Windows 系统上为 dir)
    ls ll_project

Django 新建了⼀个名为 ll_project 的⽬录。它还创建了⽂件 manage.py，这是⼀个简单的程序，接受命令并将其交给 Django 的相关部分。我们将使⽤这些命令来管理使⽤数据库和运⾏服务器等任务

⽬录 ll_project 包含 4 个⽂件，其中最重要的是 settings.py、urls.py和 wsgi.py。⽂件 settings.py 指定 Django 如何与系统交互以及如何管理项⽬。在开发项⽬的过程中，我们将修改其中的⼀些设置，并添加⼀些设置。⽂件 urls.py 告诉 Django，应创建哪些⽹⻚来响应浏览器请求。⽂件
wsgi.py 帮助 Django 提供它创建的⽂件，名称是 web server gateway interface（Web 服务器⽹关接⼝）的⾸字⺟缩写

### 创建数据库

    python manage.py migrate

    dir

SQLite 是⼀种使⽤单个⽂件的数据库，是编写简单应⽤程序的理想选择，因为它让你不⽤太关注数据库的管理问题

### 查看项目

    python manage.py runserver

Django 启动⼀个服务器（development server），让你能够查看系统中的项⽬，了解它的⼯作情况。如果你在浏览器中输⼊ URL 以请求⽹⻚，那么该Django 服务器将进⾏响应：⽣成合适的⽹⻚，并将其发送给浏览器。

## 创建应用程序
Django 项⽬（project）由⼀系列应⽤程序组成，它们协同⼯作让项⽬成为⼀个整体

    source ll_env/bin/activate
    python manage.py startapp learning_logs
    ls
    ls learning_logs/

### 定义模型
模型告诉 Django 如何处理应⽤程序中存储的数据。模型就是⼀个类，就像前⾯讨论的每个类⼀样，包含属性和⽅法。

### 激活模型

    python manage.py makemigrations learning_logs
    python manage.py migrate

每当需要修改“学习笔记”管理的数据时，都采取如下三个步骤：修改models.py，对 learning_logs 调⽤ makemigrations，以及让 Django迁移项⽬

### Django管理网站
Django 提供的管理⽹站（admin site）让你能够轻松地处理模型。Django 管理⽹站仅供⽹站的管理员使⽤，普通⽤户不能使⽤。本节将建⽴管理⽹站，并通过它使⽤模型 Topic 来添加⼀些主题

#### 创建超级用户
Django 允许创建具备所有权限的⽤户，即超级⽤户（superuser）。权限决定了⽤户可执⾏的操作。最严格的权限设置只允许⽤户阅读⽹站的公开信息。注册⽤户通常可阅读⾃⼰的私有数据，还可查看⼀些只有会员才能查看的信息。为了有效地管理项⽬，⽹站所有者通常需要访问⽹站存储的所有信息。优秀的管理员会⼩⼼地对待⽤户的敏感信息，因为⽤户对其访问的应⽤程序有极⼤的信任。

    python manage.py createsuperuser

#### 向管理网站注册模型
Django ⾃动在管理⽹站中添加了⼀些模型，如 User 和 Group，如果要添加我们创建的模型，则必须⼿动注册

#### 添加主题

### 定义模型Entry

### 迁移模型Entry

### Django shell
输⼊⼀些数据后，就可以通过交互式终端会话以编程的⽅式查看这些数据了。这种交互式环境称为 Django shell，是测试项⽬和排除故障的理想之地

    python manage.py shell
    from learning_logs.models import Topic
    Topic.objects.all()
    topics = Topic.objects.all()
    for topic in topics:
        print(topic.id, topic)
    t = Topic.objects.get(id=1)
    t.text
    t.date_added
    t.entry_set.all()

每次修改模型后，都需要重启 shell，以便看到修改的效果。要退出 shell 会话，可按 Ctr + D。如果你使⽤的是 Windows 系统，应先按 Ctr + Z，再按回⻋键

## 创建网页：学习笔记主页
使⽤ Django 创建⽹⻚的过程分为三个阶段：定义 URL，编写视图，以及编写模板。按什么顺序完成这三个阶段⽆关紧要，但在本项⽬中，总是先定义 URL 模式。URL 模式描述了 URL 的构成，让 Django 知道如何将浏览器请求与⽹站 URL 匹配，以确定返回哪个⽹⻚

每个 URL 都被映射到特定的视图。视图函数获取并处理⽹⻚所需的数据。视图函数通常使⽤模板来渲染⽹⻚，⽽模板定义⽹⻚的总体结构。为了明⽩其中的⼯作原理，我们来创建学习笔记的主⻚。这包括定义该主⻚的URL，编写其视图函数，以及创建⼀个简单的模板

### 映射URL
⽤户通过在浏览器中输⼊ URL 和单击链接来请求⽹⻚，因此需要确定项⽬需要哪些 URL。主⻚的 URL 最重要，它是⽤户⽤来访问项⽬的基础URL。当前，基础 URL（http://localhost:8000/）返回默认的 Django ⽹站，让我们知道正确地建⽴了项⽬

### 编写视图
视图函数接受请求中的信息，准备好⽣成⽹⻚所需的数据，再将这些数据发送给浏览器。这通常是使⽤定义⽹⻚外观的模板实现的。
*learning_logs 中的⽂件 views.py 是执⾏命令 python manage.pystartapp 时⾃动⽣成的*

###  编写模板
模板定义⽹⻚的外观，⽽每当⽹⻚被请求时，Django 都将填⼊相关的数据。模板让你能够访问视图提供的任何数据。我们的主⻚视图没有提供任何数据，因此相应的模板⾮常简单

### 模板继承
在创建⽹站时，⼀些通⽤元素会出现在所有⽹⻚中。在这种情况下，可编写⼀个包含通⽤元素的⽗模板，并让每个⽹⻚都继承⽗模板，⽽不是在每个⽹⻚中重复定义这些通⽤元素。这种⽅法不仅能够让你专注于开发每个⽹⻚的独特⽅⾯，还使得修改项⽬的整体外观容易得多。

#### 父模板

#### 子模版

### 显示所有主题的页面

#### URL模式
⾸先，定义显⽰所有主题的⻚⾯的 URL。通常，使⽤⼀个简单的 URL⽚段来指出⽹⻚显⽰的信息；这⾥将使⽤单词 topics，因此 URL http://localhost:8000/topics/ 将返回显⽰所有主题的⻚⾯。

#### 视图

#### 模板

### 显示特定主题的页面

#### URL模式

#### 视图

#### 模板

#### 将显示所有主题的页面中的每个主题都设置为链接

# 用户账户
Web 应⽤程序的核⼼是让任何地⽅的任何⽤户都能够注册账户并使⽤它。本章将创建⼀些表单，让⽤户能够添加主题和条⽬并编辑既有的条⽬。你将了解到，Django 能够防范对基于表单的⽹⻚发起的常⻅攻
击，让你⽆须花⼤量时间考虑应⽤程序的安全问题。

## 让用户能够输入数据

### 添加新主题

#### 用于添加主题的表单

#### URL模式new_topic

#### 视图函数new_topic

#### GET请求和POST请求

#### 模板new_topic

#### 链接到页面new_topic

### 添加新条目

#### 用于添加新条目的表单

#### URL模式new_entry

#### 视图函数new_entry()

#### 模板new_entry

#### 链接到页面new_entry

### 编辑条目

#### URL模式edit_entry

#### 视图函数edit_entry()

#### 模板edit_entry

#### 链接到页面edit_entry

## 创建用户账户
本节将建⽴⽤户注册和⾝份验证系统，让⽤户能够注册账户、登录和注销。为此，我们将新建⼀个应⽤程序，其中包含与处理⽤户账户相关的所有功能。这个应⽤程序将尽可能使⽤ Django ⾃带的⽤户⾝份验证系统来完成⼯作。

### 应用程序accounts

    python manage.py startapp accounts
    ls
    ls accounts

### 将应用程序accounts添加到settings.py中

### 包含应用程序accounts的URL

### 登录页面

#### 模板login.html

#### 设置LOGIN_REDIRECT_URL

#### 链接到登录页面

#### 使用登录页面

### 注销

#### 在base.html中添加注销表单

#### 设置LOGOUT_REDIRECT_URL

### 注册页面

#### 注册页面的URL模式

#### 视图函数register()

#### 注册模板

#### 链接到注册页面

## 让用户拥有自己的数据

### 使用@login_required限制访问
Django 提供了装饰器 @login_required，有助于轻松地限制对某些⻚⾯的访问。第 11 章介绍过，装饰器（decorator）是放在函数定义前⾯的指令，⽤于改变函数的⾏为

### 全面限制对项目“学习笔记”的访问

### 将数据关联到用户
现在，需要将数据关联到提交它们的⽤户。只需将最⾼层的数据关联到⽤户，低层的数据也将⾃动关联到该⽤户。在项⽬“学习笔记”中，应⽤程序的最⾼层数据是主题，所有条⽬都与特定的主题相关联。只要每个主题都归属于特定的⽤户，就能确定数据库中每个条⽬的所有者。

#### 修改模型Topic

#### 确认当前有哪些用户

    python manage.py shell
    from django.contrib.auth.models import User
    User.objects.all()
    for user in User.objects.all():
        print(user.username, user.id)

#### 迁移数据库
知道⽤户 ID 后，就可迁移数据库了。在这样做时，Python 将询问是要暂时将模型 Topic 关联到特定的⽤户，还是在⽂件 models.py 中指定默认⽤户。

    python manage.py makemigrations learning_logs
    1
    1
    python manage.py migrate

### 只允许用户访问自己的主题

### 保护用户的主题

### 保护页面edit_entry

### 将新主题关联到当前用户

## 设置应用程序的样式并部署

## 设置项目"学习笔记"的样式

### 应用程序django-bootstrap5 

    pip install django-bootstrap5

### 使用Bootstarp设置项目"学习笔记"的样式

### 修改base.html

#### 定义HTML头部

#### 定义导航栏

#### 添加用户账户链接

#### 在导航栏中添加注销表单

#### 定义页面的主要部分

#### 使用jumbotron设置主页的样式

#### 设置登录页面的样式

### 设置页面topics的样式

### 设置页面topic中条目的样式

## 部署"学习笔记"

### 注册Platform.sh账户

### 安装Platform.sh CLI
要将项⽬部署到 Platform.sh 服务器上并对其进⾏管理，需要使⽤Platform.sh CLI（command lineinterface，命令⾏界⾯）中的⼯具。要安装该CLI 的最新版本

### 安装platformshconfig
还需安装⼀个名为 platformshconfig 的包。这个包可帮助我们监测项⽬运⾏在本地系统还是 Platform.sh 服务器上。为了安装这个包，可在活动的虚拟环境中执⾏如下命令

     pip install platformshconfig

### 创建文件requirements.txt
远程服务器需要知道项⽬“学习笔记”依赖于哪些包，因此我们将使⽤ pip ⽣成⼀个⽂件，在其中列出这些包。

    pip freeze > requirements.txt

### 其他部署要求

### 添加配置文件

#### 显示隐藏的文件

#### 配置文件 .platform.app.yaml

#### 配置文件routes.yaml
路由（route）指的是请求在被服务器处理的过程中经过的路径。Platform.sh 需要知道应将收到的请求发送到哪⾥

#### 配置文件services.yaml

### 为部署到Platform.sh而修改settings.py

### 使用Git跟踪项目文件

#### 安装Git

#### 配置Git

#### 忽略文件

#### 提交项目

#### 在Platform.sh上创建项目

    platform login
    Y
    platform create
    ll_project
    us-3.platform.sh

#### 推送到Platform.sh

    platform push

### 查看线上项目

    platform url

### 改进Platform.sh部署

#### 在Platform.sh上创建超级用户

    platform environment:ssh
    ls
    python manage.py createsuperuser
    ll_admin_live

#### 确保线上项目的安全

#### 提交并推送修改

    git commit -am "Set DEBUG False on live
    git status
    platform push


### 创建定制错误页面

#### 创建定制模板

#### 将修改推送到Platform.sh

    git add .
    git commit -am "Added custom 404 and 500 error pages."
    platform push

#### 继续开发
将项⽬“学习笔记”推送到远程服务器上之后，你可能想进⼀步开发它或开发要部署的其他项⽬。更新项⽬的过程⼏乎完全相同，如下所⽰。⾸先，对本地项⽬做必要的修改。如果在修改过程中创建了新⽂件，使⽤命令 git add .（千万别忘记末尾的句点）将它们加⼊ Git 仓库。如果有修改要求迁移数据库，也需要执⾏这个命令，因为每次迁移都将⽣成新的迁移⽂件。然后，使⽤命令 git commit -am "commit message" 将修改提交到仓库，再使⽤命令 platform push 将修改推送到 Platform.sh 上。然后，访问线上的项⽬，确认期望看到的修改已⽣效。

### 将项目从Platform.sh删除
要删除项⽬，可使⽤ Platform.sh CLI：

    platform project:delete

命令 platform create 还在本地 Git 仓库中添加了⼀个引⽤，它指向位于 Platform.sh 服务器上的远程仓库。可在命令⾏中删除这个远程仓库

    git remote
    git remote remove platform

还可以删除项⽬的资源。⾸先登录 Platform.sh ⽹站，并访问你的仪表盘（dashboard）。这个⻚⾯列出了你的所有活动项⽬。单击项⽬框中的三个点，再单击 Edit Plan。这将打开项⽬的计价⻚⾯（pricing page），单击该⻚⾯底部的 Delete Project 按钮，将出现⼀个确认⻚⾯，然后就可以按其中的说明完成项⽬的删除了。即便你选择使⽤ CLI 删除项⽬，也应该熟悉托管提供商提供的仪表盘。
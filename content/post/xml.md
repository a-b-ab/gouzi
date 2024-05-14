+++
title = 'xml'
date = 2024-05-10T13:28:01+08:00
draft = false
+++
# 是什么
XML(Extensible Markup Language) 扩展性标识语言。文件后缀名为：.xml。就像HTML的作用是显示数据，XML的作用是传输和存储数据。
*据说，java是一门专业操作XML的语言*

# 是干啥用的
为了便于不同应用，不同平台之间的数据共享和通信

具体点的作用为：
1.可作为一种简单的数据库，存储并检索数据
2.传输约定格式的文件
3.做软件的配置文件
*配置文件：保存软件设置的文件*

**XML的出生是为了完善HTML的缺陷和局限性**

# XML的闺蜜--JSON
JSON javascript Object Notation ,js对象表示法。作用也是存储和交换文本信息

JSON更小，跟快，更易解析
JSON适用于简单的传值，XML适用于更广阔的范围

.xml文件中的代码

    <?xml version="1.0" encoding="UTF-8"?>
    <email xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="email.xsd">
    <to>liuwei8809@163.com</to>
    <form>hellokitty@163.com</form>
    <title>about loving</title>
    <body>I love you forever!</body>
    <date>2008-11-12</date>
    </email>
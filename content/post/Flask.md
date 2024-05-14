+++
title = 'Flask'
date = 2024-04-30T13:28:01+08:00
draft = false
+++
# 一个最小的应用
![](https://raw.githubusercontent.com/a-b-ab/picture/main/Picgo202405142258566.jpg)
```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello,World!'
```
那么，这些代码是什么意思呢？

- 首先我们导入了 Flask 类。 该类的实例将会成为我们的 WSGI 应用。

- 接着我们创建一个该类的实例。第一个参数是应用模块或者包的名称。如果你使用 一个单一模块（就像本例），那么应当使用 __name__ ，因为名称会根据这个 模块是按应用方式使用还是作为一个模块导入而发生变化（可能是 ‘__main__’ ， 也可能是实际导入的名称）。这个参数是必需的，这样 Flask 才能知道在哪里可以 找到模板和静态文件等东西。更多内容详见 Flask 文档。

- 然后我们使用 route() 装饰器来告诉 Flask 触发函数的 URL 。

- 函数名称被用于生成相关联的 URL 。函数最后返回需要在用户浏览器中显示的信息。

把它保存为 hello.py 或其他类似名称。请不要使用 flask.py 作为应用名称，这会与 Flask 本身发生冲突。

外部可见的服务器
运行服务器后，会发现只有你自己的电脑可以使用服务，而网络中的其他电脑却 不行。缺省设置就是这样的，因为在调试模式下该应用的用户可以执行你电脑中 的任意 Python 代码。

如果你关闭了调试器或信任你网络中的用户，那么可以让服务器被公开访问。 只要在命令行上简单的加上 --host=0.0.0.0 即可:

$ flask run --host=0.0.0.0
这行代码告诉你的操作系统监听所有公开的 IP 。

## 调试模式

虽然 flask 命令可以方便地启动一个本地开发服务器，但是每次应用代码 修改之后都需要手动重启服务器。这样不是很方便， Flask 可以做得更好。如果你打开 调试模式，那么服务器会在修改应用代码之后自动重启，并且当应用出错时还会提供一个 有用的调试器。

如果需要打开所有开发功能（包括调试模式），那么要在运行服务器之前导出 FLASK_ENV 环境变量并把其设置为 development:

    $ export FLASK_ENV=development
    $ flask run

（在 Windows 下需要使用 set 来代替 export 。）

这样可以实现以下功能：

- 激活调试器。

- 激活自动重载。

- 打开 Flask 应用的调试模式。

还可以通过导出 FLASK_DEBUG=1 来单独控制调试模式的开关。

Attention
虽然交互调试器不能在分布环境下工作（这使得它基本不可能用于生产环境），但是 它允许执行任意代码，这样会成为一个重大安全隐患。因此， 绝对不能在生产环境 中使用调试器 。

## 路由
现代 web 应用都使用有意义的 URL ，这样有助于用户记忆，网页会更得到用户的青睐， 提高回头率。

使用 route() 装饰器来把函数绑定到 URL:
```python
@app.route('/')
def index():
    return 'Index Page'

@app.route('/hello')
def hello():
    return 'Hello, World'
```

## 变量规则
通过把 URL 的一部分标记为 <variable_name> 就可以在 URL 中添加变量。标记的 部分会作为关键字参数传递给函数。通过使用 <converter:variable_name> ，可以 选择性的加上一个转换器，为变量指定规则。请看下面的例子:

```python
@app.route('/user/<username>')
def show_user_profile(username):
    # show the user profile for that user
    return 'User %s' % escape(username)

@app.route('/post/<int:post_id>')
def show_post(post_id):
    # show the post with the given id, the id is an integer
    return 'Post %d' % post_id

@app.route('/path/<path:subpath>')
def show_subpath(subpath):
    # show the subpath after /path/
    return 'Subpath %s' % escape(subpath)
```

## 唯一的 URL / 重定向行为
projects 的 URL 是中规中矩的，尾部有一个斜杠，看起来就如同一个文件夹。 访问一个没有斜杠结尾的 URL 时 Flask 会自动进行重定向，帮你在尾部加上一个斜杠。

about 的 URL 没有尾部斜杠，因此其行为表现与一个文件类似。如果访问这个 URL 时添加了尾部斜杠就会得到一个 404 错误。这样可以保持 URL 唯一，并帮助 搜索引擎避免重复索引同一页面。

## URL 构建
url_for() 函数用于构建指定函数的 URL。它把函数名称作为第一个 参数。它可以接受任意个关键字参数，每个关键字参数对应 URL 中的变量。未知变量 将添加到 URL 中作为查询参数

## HTTP 方法
Web 应用使用不同的 HTTP 方法处理 URL 。当你使用 Flask 时，应当熟悉 HTTP 方法。 缺省情况下，一个路由只回应 GET 请求。 可以使用 route() 装饰器的 methods 参数来处理不同的 HTTP 方法

## 静态文件
动态的 web 应用也需要静态文件，一般是 CSS 和 JavaScript 文件。理想情况下你的 服务器已经配置好了为你的提供静态文件的服务。但是在开发过程中， Flask 也能做好 这项工作。只要在你的包或模块旁边创建一个名为 static 的文件夹就行了。 静态文件位于应用的 /static 中。

    url_for('static', filename='style.css')

这个静态文件在文件系统中的位置应该是 static/style.css 。

## 渲染模板
在 Python 内部生成 HTML 不好玩，且相当笨拙。因为你必须自己负责 HTML 转义， 以确保应用的安全。因此， Flask 自动为你配置 Jinja2 模板引擎。

使用 render_template() 方法可以渲染模板，你只要提供模板名称和需要 作为参数传递给模板的变量就行了。下面是一个简单的模板渲染例子:

```python
from flask import render_template

@app.route('/hello/')
@app.route('/hello/<name>')
def hello(name=None):
    return render_template('hello.html', name=name)
```

Flask 会在 templates 文件夹内寻找模板。因此，如果你的应用是一个模块， 那么模板文件夹应该在模块旁边；如果是一个包，那么就应该在包里面：

## 操作请求数据
对于 web 应用来说对客户端向服务器发送的数据作出响应很重要。在 Flask 中由全局 对象 request 来提供请求信息。如果你有一些 Python 基础，那么 可能 会奇怪：既然这个对象是全局的，怎么还能保持线程安全？答案是本地环境：

## 请求对象
请求对象在 API 一节中有详细说明这里不细谈（参见 Request ）。 这里简略地谈一下最常见的操作。首先，你必须从 flask 模块导入请求对象:
    from flask import request

通过使用 method 属性可以操作当前请求方法，通过使用 form 属性处理表单数据（在 POST 或者 PUT 请求 中传输的数据）。以下是使用上述两个属性的例子
```python
@app.route('/login', methods=['POST', 'GET'])
def login():
    error = None
    if request.method == 'POST':
        if valid_login(request.form['username'],
                       request.form['password']):
            return log_the_user_in(request.form['username'])
        else:
            error = 'Invalid username/password'
    # the code below is executed if the request method
    # was GET or the credentials were invalid
    return render_template('login.html', error=error)
```
当 form 属性中不存在这个键时会发生什么？会引发一个 KeyError 。 如果你不像捕捉一个标准错误一样捕捉 KeyError ，那么会显示一个 HTTP 400 Bad Request 错误页面。因此，多数情况下你不必处理这个问题。

要操作 URL （如 ?key=value ）中提交的参数可以使用 args 属性:

    searchword = request.args.get('key', '')

## 文件上传
用 Flask 处理文件上传很容易，只要确保不要忘记在你的 HTML 表单中设置 enctype="multipart/form-data" 属性就可以了。否则浏览器将不会传送你的文件。

已上传的文件被储存在内存或文件系统的临时位置。你可以通过请求对象 files 属性来访问上传的文件。每个上传的文件都储存在这个 字典型属性中。这个属性基本和标准 Python file 对象一样，另外多出一个 用于把上传文件保存到服务器的文件系统中的 save() 方法

```python
from flask import request

@app.route('/upload', methods=['GET', 'POST'])
def upload_file():
    if request.method == 'POST':
        f = request.files['the_file']
        f.save('/var/www/uploads/uploaded_file.txt')
    ...
```

## Cookles
要访问 cookies ，可以使用 cookies 属性。可以使用响应 对象 的 set_cookie 方法来设置 cookies 。请求对象的 cookies 属性是一个包含了客户端传输的所有 cookies 的字典。在 Flask 中，如果使用会话 ，那么就不要直接使用 cookies ，因为 会话 比较安全一些。

读取 cookies:
```python
from flask import request

@app.route('/')
def index():
    username = request.cookies.get('username')
    # use cookies.get(key) instead of cookies[key] to not get a
    # KeyError if the cookie is missing.
```

储存 cookies:
```python
from flask import make_response

@app.route('/')
def index():
    resp = make_response(render_template(...))
    resp.set_cookie('username', 'the username')
    return resp
```

注意， cookies 设置在响应对象上。通常只是从视图函数返回字符串， Flask 会把它们 转换为响应对象。如果你想显式地转换，那么可以使用 make_response() 函数，然后再修改它。

## 重定向和错误
使用 redirect() 函数可以重定向。使用 abort() 可以 更早退出请求，并返回错误代码:
```python
from flask import abort, redirect, url_for

@app.route('/')
def index():
    return redirect(url_for('login'))

@app.route('/login')
def login():
    abort(401)
    this_is_never_executed()
```

缺省情况下每种出错代码都会对应显示一个黑白的出错页面。使用 errorhandler() 装饰器可以定制出错页面:
```python
from flask import render_template

@app.errorhandler(404)
def page_not_found(error):
    return render_template('page_not_found.html'), 404
```

注意 render_template() 后面的 404 ，这表示页面对就的出错 代码是 404 ，即页面不存在。缺省情况下 200 表示：一切正常。

## 关于响应
视图函数的返回值会自动转换为一个响应对象。如果返回值是一个字符串，那么会被 转换为一个包含作为响应体的字符串、一个 200 OK 出错代码 和一个 text/html 类型的响应对象。如果返回值是一个字典，那么会调用 jsonify() 来产生一个响应。以下是转换的规则：

- 如果视图返回的是一个响应对象，那么就直接返回它。

- 如果返回的是一个字符串，那么根据这个字符串和缺省参数生成一个用于返回的 响应对象。

- 如果返回的是一个字典，那么调用 jsonify 创建一个响应对象。

- 如果返回的是一个元组，那么元组中的项目可以提供额外的信息。元组中必须至少 包含一个项目，且项目应当由 (response, status) 、 (response, headers) 或者 (response, status, headers) 组成。 status 的值会重载状态代码， headers 是一个由额外头部值组成的列表 或字典。

如果以上都不是，那么 Flask 会假定返回值是一个有效的 WSGI 应用并把它转换为 一个响应对象。

如果想要在视图内部掌控响应对象的结果，那么可以使用 make_response() 函数。

可以使用 make_response() 包裹返回表达式，获得响应对象，并对该对象 进行修改，然后再返回:

## JSON格式的API
JSON 格式的响应是常见的，用 Flask 写这样的 API 是很容易上手的。如果从视图 返回一个 dict ，那么它会被转换为一个 JSON 响应。
```python
@app.route("/me")
def me_api():
    user = get_current_user()
    return {
        "username": user.username,
        "theme": user.theme,
        "image": url_for("user_image", filename=user.image),
    }
```

如果 dict 还不能满足需求，还需要创建其他类型的 JSON 格式响应，可以使用 jsonify() 函数。该函数会序列化任何支持的 JSON 数据类型。 也可以研究研究 Flask 社区扩展，以支持更复杂的应用。

```python
@app.route("/users")
def users_api():
    users = get_all_users()
    return jsonify([user.to_json() for user in users])
```

## 会话
除了请求对象之外还有一种称为 session 的对象，允许你在不同请求 之间储存信息。这个对象相当于用密钥签名加密的 cookie ，即用户可以查看你的 cookie ，但是如果没有密钥就无法修改它

使用会话之前你必须设置一个密钥。举例说明:
```python
from flask import Flask, session, redirect, url_for, escape, request

app = Flask(__name__)

# Set the secret key to some random bytes. Keep this really secret!
app.secret_key = b'_5#y2L"F4Q8z\n\xec]/'

@app.route('/')
def index():
    if 'username' in session:
        return 'Logged in as %s' % escape(session['username'])
    return 'You are not logged in'

@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        session['username'] = request.form['username']
        return redirect(url_for('index'))
    return '''
        <form method="post">
            <p><input type=text name=username>
            <p><input type=submit value=Login>
        </form>
    '''

@app.route('/logout')
def logout():
    # remove the username from the session if it's there
    session.pop('username', None)
    return redirect(url_for('index'))
```

如何生成一个好的密钥
生成随机数的关键在于一个好的随机种子，因此一个好的密钥应当有足够的随机性。 操作系统可以有多种方式基于密码随机生成器来生成随机数据。使用下面的命令 可以快捷的为 Flask.secret_key （ 或者 SECRET_KEY ）生成值:

$ python -c 'import os; print(os.urandom(16))'
b'_5#y2L"F4Q8z\n\xec]/'

## 消息闪现
一个好的应用和用户接口都有良好的反馈，否则到后来用户就会讨厌这个应用。 Flask 通过闪现系统来提供了一个易用的反馈方式。闪现系统的基本工作原理是在请求结束时 记录一个消息，提供且只提供给下一个请求使用。通常通过一个布局模板来展现闪现的 消息。

flash() 用于闪现一个消息。在模板中，使用 get_flashed_messages() 来操作消息。完整的例子参见 消息闪现 。

## 日志
有时候可能会遇到数据出错需要纠正的情况。例如因为用户篡改了数据或客户端代码出错 而导致一个客户端代码向服务器发送了明显错误的 HTTP 请求。多数时候在类似情况下 返回 400 Bad Request 就没事了，但也有不会返回的时候，而代码还得继续运行 下去。

这时候就需要使用日志来记录这些不正常的东西了。自从 Flask 0.3 后就已经为你配置好 了一个日志工具。

以下是一些日志调用示例:
app.logger.debug('A value for debugging')
app.logger.warning('A warning occurred (%d apples)', 42)
app.logger.error('An error occurred')

## 集成 WSGI 中间件
如果想要在应用中添加一个 WSGI 中间件，那么可以包装内部的 WSGI 应用。假设为了 解决 lighttpd 的错误，你要使用一个来自 Werkzeug 包的中间件，那么可以这样做:

    from werkzeug.contrib.fixers import LighttpdCGIRootFix
    app.wsgi_app = LighttpdCGIRootFix(app.wsgi_app)

## 使用 Flask 扩展
扩展是帮助完成公共任务的包。例如 Flask-SQLAlchemy 为在 Flask 中轻松使用 SQLAlchemy 提供支持。

## 部署到网络服务器
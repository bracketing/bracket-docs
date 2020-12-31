# Learn Bracket

## Introduction

**Bracket** is an Elegant static site generator. It encapsulates **[Jinja2](https://github.com/pallets/jinja)**. Its biggest highlight is to render the static pages in the form of **view function**, and support real-time **debugging**. It can also support **CSS framework**, **international routing** and more functions through ecological extension.

[https://github.com/bracketing/bracket](https://github.com/bracketing/bracket)

## Installation

Your computer needs the following environment:

* `Python 3.6` and above


Install and update using [pip](pypi.org):

``` bash
$ pip install bracket
```

You can also download the development version from [GitHub](https://github.com/bracketing/bracket):

``` bash
$ git clone https://github.com/bracketing/bracket
$ cd bracket
$ python setup.py install
```


## A Simple Example

``` python
from bracket import WebSite
from jinja2 import Template

app = WebSite(__name__)

@app.pages("/")
def helloworld(context):
    return context({
    "title":"Welcome to Bracket",
    "content":Template('''
        <h1>{{ messages }}</h1>
        <img src="{{ bracket.res('/logo.png')}}">
    '''),
    "resources":{
        "messages":"Welcome to Bracket"
    }
})

app.dispatch("/")
```

* `#4` Creating `app` through `WebSite(__name__)`
* `#6` Create `helloworld` interface through `app.pages()`
* `#8` Send `jinja2` content with rendering through `context` object
    * `title` Title of HTML
    * `context` `jinja2.Template`
    * `resources` Template parameters passed
* `#19` Rendering interface

``` html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="generator" content="Bracket & Jinja2 ">
    
    <title>Welcome to Bracket</title>
</head>
<body>
    <div id="bracketapp">
    
        <h1>Welcome to Bracket</h1>
        <img src="/static/logo.png">
        
    </div>
</body>
</html>
```
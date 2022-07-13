# 一. jQuery介绍

## 1 什么是jQuery

> jQuery是一个JavaScript函数库

在早期的时候, 浏览器有很多不同的版本, 如果要做各种浏览器兼容是很头疼的事. 

jQuery的出现解决了这个问题, 处理了兼容问题, 并提供了一系列**简洁的**, **统一的**操作DOM的方式

> jQuery的口号是"write less, do more"

## 2 jQuery包含哪些功能

jQuery库包含以下功能：

- HTML 元素选取
- HTML 元素操作
- CSS 操作
- HTML 事件函数
- JavaScript 特效和动画
- HTML DOM 遍历和修改
- AJAX

除此之外, 还提供了大量的插件. 

虽然现在3大框架的出现在一定程度上影响了jQuery的市场份额. 但是jQuery对于学习DOM编程还是非常有帮助的. 同时也不排除jQuery依然活跃于大型项目中

# 二. jQuery快速上手

## 1 jQuery的安装

jQuery的安装只需要引入jQuery的js文件即可, 常用的获取jquery.js文件的方式:

- 从 [jquery.com](http://jquery.com/download/) 下载 jQuery 库
- 从 CDN 中载入 jQuery, 如从 jsDelivr 中加载 jQuery

这里, 更推荐大家使用CDN的方式引入

> 推荐的CDN公共资源网站

[jsDelivr](https://www.jsdelivr.com/)

```html
<script src="https://cdn.bootcdn.net/ajax/libs/jquery/3.6.0/jquery.js"></script>
```

[bootCDN](https://www.bootcdn.cn/)

```html
<script src="https://cdn.jsdelivr.net/npm/jquery@3.6.0/dist/jquery.min.js"></script>
```

更多公共资源CDN可以参考: [菜鸟驿站-jQuery安装](https://www.runoob.com/jquery/jquery-install.html)

> 扩展

许多用户在访问其他站点时，已经从百度、又拍云、新浪、谷歌或微软加载过 jQuery。所以结果是，当他们访问您的站点时，会从缓存中加载  jQuery，这样可以减少加载时间。同时，大多数 CDN  都可以确保当用户向其请求文件时，会从离用户最近的服务器上返回响应，这样也可以提高加载速度

## 2 jQuery语法

jQuery最主要的作用就是操作DOM

步骤:

1. 选择DOM元素
2. 执行操作(事件, 属性, 效果...)

> 语法

```
$('选择器').action
```

> 示例

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <!-- 1. 引入jQuery -->
    <script src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.min.js"></script>
  </head>
  <body>
    <div>慢慢就看不见我了!!!</div>
    <script>
      // 选择div元素, 在3s内隐藏
      $('div').hide(3000)
    </script>
  </body>
</html>
```

## 3 入口函数

当DOM元素加载完成后执行. 不用等所有内容(包括图片, css)加载完成

> 示例

```js
$(function(){
    // 执行代码
})
```

> 示例

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <!-- 1. 引入jQuery -->
    <script src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.min.js"></script>
  </head>
  <body>
    <script>
      $('div').hide(3000)
    </script>
    <div>慢慢就看不见我了!!!</div>
  </body>
</html>
```

没有起效果.

如果我们希望jQuery的代码生效, 可以考虑将代码放在入口函数中

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <!-- 1. 引入jQuery -->
    <script src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.min.js"></script>
  </head>
  <body>
    <script>
      $(function () {
        $('div').hide(3000)
      })
    </script>
    <div>慢慢就看不见我了!!!</div>
  </body>
</html>
```

## 4 DOM对象与jQuery对象

DOM对象是通过原生的DOM API得到的对象

jQuery对象是通过$()得到的对象

两者可以使用方法不一样

> 示例

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <!-- 1. 引入jQuery -->
    <script src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.min.js"></script>
  </head>
  <body>
    <div>box</div>

    <script>
      var div = document.querySelector('div')
      div.onclick = function () {
        alert(123)
      }

      var jqObj = $('div')
      // jqObj 并没有onclick方法, 不会生效
      jqObj.onclick = function () {
        console.log(123)
      }
    </script>
  </body>
</html>
```

DOM对象和jQuery对象是可以相互转换的

- 通过$()得到的对象是jq对象, 通过下标得到dom对象
- 通过dom API得到dom对象, 通过$()转换为jq对象

> 示例

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <!-- 1. 引入jQuery -->
    <script src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.min.js"></script>
  </head>
  <body>
    <div>box1</div>
    <div>box2</div>
    <div>box3</div>

    <script>
      // 通过$()得到的对象是jq对象, 通过下标得到dom对象
      var jqObj = $('div')
      console.dir(jqObj)
      console.dir(jqObj[0])

      // 通过dom API得到dom对象, 通过$()转换为jq对象
      var divs = document.querySelectorAll('div')
      console.log(divs)
      console.log($(divs))
    </script>
  </body>
</html>
```

# 三. jQuery选择器

类似于CSS选择器, jQuery提供丰富的选择器, 可以快速准确的选出DOM元素.

这里, 我们也只是给出常用的选择器, 更多组合大家自行探索

| 名称               | 用法                    | 描述                                |
| ------------------ | ----------------------- | ----------------------------------- |
| ID选择器           | $('#id')                | 获取指定ID的元素                    |
| 类选择器           | $('.class')             | 获取一类class的元素                 |
| 标签选择器         | $('div')                | 获取所有div元素                     |
| 后代选择器         | $('ul li')              | 获取ul下所有的li元素                |
| :first             | $('li:first')           | 获取第一个li元素                    |
| eq(index)          | $('li:eq(2)')           | 获取索引号为2的元素, 从0开始        |
| find(selector)     | $('ul').find('li')      | 在ul下找所有的li元素                |
| eq(index)          | $('li').eq(2)           | 相当于$('li:eq(2)')                 |
| siblings(selector) | $(this).siblings()      | 选择自己的兄弟元素, 不包括自己      |
| 属性选择器         | $("a[target='_blank']") | target 属性值等于 "_blank" 的 a元素 |

# 四. jQuery事件

## 1 什么是事件

当用户浏览网页时, 网页上一些可以交互的元素(按钮)对用户操作的反应就是事件.

比如

- 用户点击登录按钮
- 看小说, 漫画时按键盘的左右键进行翻页

这些都是事件

## 2 常见的事件

常见的事件可以分为

- 鼠标事件
- 键盘事件
- 表单事件
- 窗口事件

![image-20201214092143897](http://image.brojie.cn/images/image-20201214092143897.png)

## 3 jQuery如何处理事件

> 语法

```js
$("选择器").事件名(function(){
    // 事件处理函数
});
```

> 示例

```js
$("btn").click(function(){
    alert('我被点击了')
});
```

# 五. jQuery CSS操作

通过jQuery可以快速的添加CSS样式

## 1 CSS操作

> 语法

```js
// 设置单个属性
$("选择器").css('属性名', '属性值')
// 设置多个属性
$("选择器").css({
  属性名1: 属性值1,
  属性名2: 属性值2
})
```

> 示例

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <!-- 1. 引入jQuery -->
    <script src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.min.js"></script>
  </head>
  <body>
    <div id="box">box</div>

    <script>
      // 对于-, 改成驼峰命名
      // 设置单个属性
      $('#box').css('backgroundColor', 'skyblue')

      // 设置多个属性
      $('#box').css({
        width: '400px',
        height: '400px',
        color: '#fff',
        fontSize: '32px',
      })
    </script>
  </body>
</html>

```

## 2 类操作

更多的时候, 我们使用类操作

- 添加一个类样式: addClass
- 删除一个类样式: removeClass
- 切换类样式: toggleClass

> 示例

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <!-- 1. 引入jQuery -->
    <script src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.min.js"></script>
    <style>
      div {
        width: 150px;
        height: 150px;
        background-color: skyblue;
      }

      .current {
        background-color: greenyellow;
      }
    </style>
  </head>
  <body>
    <div>box</div>
    <button id="btnAdd">点击添加颜色</button>
    <button id="btnRemove">点击删除颜色</button>
    <button id="btnToggle">点击切换颜色</button>

    <script>
      $('#btnAdd').click(function () {
        // 添加颜色
        $('div').addClass('current')
      })

      $('#btnRemove').click(function () {
        // 删除颜色
        $('div').removeClass('current')
      })

      $('#btnToggle').click(function () {
        // 切换颜色
        $('div').toggleClass('current')
      })
    </script>
  </body>
</html>

```

> 综合练习: 仿京东Tab栏切换

实现如下效果:

![tab](http://image.brojie.cn/images/tab.gif)

思路:

1. 点击上部的li，当前li 添加current类，其余兄弟移除类。
2. 点击的同时，得到当前li 的索引号
3. 让下部里面相应索引号的item显示，其余的item隐藏

> 答案

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <!-- 1. 引入jQuery -->
    <script src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.min.js"></script>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      li {
        list-style: none;
      }
      .tab {
        width: 800px;
        height: 300px;
        margin: 100px auto;
      }
      .tab-title {
        height: 36px;
        background-color: #f1f1f1;
        border: 1px solid #ccc;
      }
      .tab-title ul li {
        float: left;
        padding: 0 20px;
        height: 36px;
        line-height: 36px;
        text-align: center;
        cursor: pointer;
      }
      .active {
        background-color: #c81623;
        color: #fff;
      }
      .item {
        display: none;
      }
    </style>
  </head>
  <body>
    <div class="tab">
      <div class="tab-title">
        <ul>
          <li class="active">商品介绍</li>
          <li>规格与包装</li>
          <li>售后保障</li>
          <li>商品评价(50000)</li>
          <li>手机社区</li>
        </ul>
      </div>
      <div class="tab-item">
        <div class="item" style="display: block">商品介绍</div>
        <div class="item">规格与包装</div>
        <div class="item">售后保障</div>
        <div class="item">商品评价</div>
        <div class="item">手机社区</div>
      </div>
    </div>

    <script>
      $('.tab-title li').click(function () {
        var i = $(this).index()
        $(this).addClass('active').siblings().removeClass('active')
        $('.item').eq(i).show().siblings().hide()
      })
    </script>
  </body>
</html>

```

- 这里使用到了链式操作
- $(this): 表示当前选中的li元素
- 通过index(): 获取当前选中的li元素的下标

总的思路是:

给当前选中的添加样式

给兄弟移除样式

# 六. jQuery效果

## 1 显示与隐藏

三个方法

- show()
- hide()
- toggle()

> 语法

```js
// 不带参数, 直接显示
$('选择器').show()

// 带一个参数, 在time(毫秒)内显示
$('选择器').show(time)

// 带二个参数, 在time(毫秒)内显示, 显示完后执行回调
$('选择器').show(time, callback)
```

> 示例

```js
$("button").click(function() {
  $("div").show(1000, function() {
    alert(1);
  });
})
```

## 2 滑入滑出

三个方法

- slideDown() 
- slideUp() 
- slideToggle()

语法跟show()一样

## 3 淡入淡出

自学淡入淡出函数

综合案例: 带下拉效果的导航条

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <script src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.min.js"></script>
    <!-- 2. 样式 -->
    <style>
      /* reset */
      * {
        margin: 0;
        padding: 0;
      }
      li {
        list-style: none;
      }
      a {
        text-decoration: none;
      }
      /* 布局 */
      .nav {
        width: 400px;
        margin: 50px auto;
      }
      .nav .nav-item {
        float: left;
        position: relative;
      }
      .nav .nav-item .nav-title {
        display: block;
        width: 80px;
        height: 40px;
        line-height: 40px;
        text-align: center;
        color: #333;
        /* background-color: #eee; */
      }
      .nav .nav-item .nav-title:hover {
        background-color: #edeef0;
        color: #ff8400;
      }
      .nav .nav-menu {
        display: none;
        position: absolute;
        color: #333;
        border-left: 1px solid #fecc5b;
        border-right: 1px solid #fecc5b;
      }
      .nav .nav-menu li {
        line-height: 40px;
        padding: 0 20px;
        white-space: nowrap;
        border-bottom: 1px solid #fecc5b;
      }
      .nav .nav-menu li:hover {
        background-color: #fff5da;
        color: #e67902;
      }
    </style>
  </head>
  <body>
    <!-- 1. 结构 -->
    <nav class="nav">
      <ul>
        <li class="nav-item">
          <a href="#" class="nav-title">微博</a>
          <ul class="nav-menu">
            <li>私信</li>
            <li>评论</li>
            <li>@我</li>
          </ul>
        </li>
        <li class="nav-item">
          <a href="#" class="nav-title">博客</a>
          <ul class="nav-menu">
            <li>博客评论</li>
            <li>未读提醒</li>
          </ul>
        </li>
        <li class="nav-item">
          <a href="#" class="nav-title">邮箱</a>
          <ul class="nav-menu">
            <li>免费邮箱</li>
            <li>VIP邮箱</li>
            <li>企业邮箱</li>
            <li>新浪企业邮箱客户端</li>
          </ul>
        </li>
      </ul>
    </nav>
    <script>
      // $('.nav-item').mouseenter(function () {
      //   $(this).children('.nav-menu').slideDown(200)
      // })
      // $('.nav-item').mouseleave(function () {
      //   $(this).children('.nav-menu').slideUp(200)
      // })
      // $('.nav-item').hover(
      //   function () {
      //     $(this).children('.nav-menu').slideDown(200)
      //   },
      //   function () {
      //     $(this).children('.nav-menu').slideUp(200)
      //   }
      // )

      $('.nav-item').hover(function () {
        $(this).children('.nav-menu').slideToggle(200)
      })
    </script>
  </body>
</html>
```

## 4 停止动画

stop()

如果不停止动画就会出现上面的情况. 我们可以使用stop停止动画

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <script src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.min.js"></script>
    <!-- 2. 样式 -->
    <style>
      /* reset */
      * {
        margin: 0;
        padding: 0;
      }
      li {
        list-style: none;
      }
      a {
        text-decoration: none;
      }
      /* 布局 */
      .nav {
        width: 400px;
        margin: 50px auto;
      }
      .nav .nav-item {
        float: left;
        position: relative;
      }
      .nav .nav-item .nav-title {
        display: block;
        width: 80px;
        height: 40px;
        line-height: 40px;
        text-align: center;
        color: #333;
        /* background-color: #eee; */
      }
      .nav .nav-item .nav-title:hover {
        background-color: #edeef0;
        color: #ff8400;
      }
      .nav .nav-menu {
        display: none;
        position: absolute;
        color: #333;
        border-left: 1px solid #fecc5b;
        border-right: 1px solid #fecc5b;
      }
      .nav .nav-menu li {
        line-height: 40px;
        padding: 0 20px;
        white-space: nowrap;
        border-bottom: 1px solid #fecc5b;
      }
      .nav .nav-menu li:hover {
        background-color: #fff5da;
        color: #e67902;
      }
    </style>
  </head>
  <body>
    <!-- 1. 结构 -->
    <nav class="nav">
      <ul>
        <li class="nav-item">
          <a href="#" class="nav-title">微博</a>
          <ul class="nav-menu">
            <li>私信</li>
            <li>评论</li>
            <li>@我</li>
          </ul>
        </li>
        <li class="nav-item">
          <a href="#" class="nav-title">博客</a>
          <ul class="nav-menu">
            <li>博客评论</li>
            <li>未读提醒</li>
          </ul>
        </li>
        <li class="nav-item">
          <a href="#" class="nav-title">邮箱</a>
          <ul class="nav-menu">
            <li>免费邮箱</li>
            <li>VIP邮箱</li>
            <li>企业邮箱</li>
            <li>新浪企业邮箱客户端</li>
          </ul>
        </li>
      </ul>
    </nav>
    <script>
      $('.nav-item').hover(function () {
        $(this).children('.nav-menu').stop().slideToggle(200)
      })
    </script>
  </body>
</html>
```

# 七. jQuery属性操作

## 1 jQuery元素属性操作

这里主要是两个方法

- prop()
- attr()

虽然attrubite和property都有属性的意思, 但是

- prop() -- 操作js对象的属性
- attr() -- 操作html属性节点

prop更适用于表单属性, 如：disabled / checked / selected 等

> 示例

prop示例

```js
$('button').on('click',function(){
  if ($('input').prop('checked')) {
    $('input').prop('checked',false);
  }else{
    $('input').prop('checked',true);
  }
})
```

 attr示例

```html
<a href="http://www.baidu.com" title="baidu">百度</a>
<button id="btn">点击</button>
<script>
  $('#btn').click(function () {
    console.log($('a').attr('title'))
    $('a').attr('title', '百度')
  })
</script>
```

## 2 jQuery文本操作

主要涉及两个方法

- html()
- text()
- val()

html相当于原生的innerHTML

text相当于原生的innerText

val相当于原生的value

> 语法

```js
// 不带参数, 获取值
$('选择器').html()

// 带参数, 设置值
$('选择器').html('值')
```

> 示例

```html
<div id="test1">1</div>
<div id="test2">2</div>
<input type="text" id="test3" />

<div>
  <button id="btn1">1</button>
  <button id="btn2">2</button>
  <button id="btn3">3</button>
</div>

<script>
  $('#btn1').click(function () {
    // html标签不会被解析, 原样输出
    $('#test1').text('<b>Hello world!</b>')
  })
  $('#btn2').click(function () {
    // html标签会被解析
    $('#test2').html('<b>Hello world!</b>')
  })
  $('#btn3').click(function () {
    // 修改test3中的值
    $('#test3').val('用户名')
  })
</script>
```

## 3 jQuery元素操作

### 1) 添加元素

有4个方法

- append() - 在被选元素的内部插入子元素, 在最后
- prepend() - 在被选元素的内部插入子元素, 在最前
- after() - 在被选元素的外部插入兄弟元素, 在后面
- before() - 在被选元素的外部插入兄弟元素, 在前面

### 2) 删除元素

如需删除元素和内容，一般可使用以下两个方法：

- remove() - 删除被选元素（及其子元素）
- empty() - 从被选元素中删除子元素

> 案例: Todolist

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <script src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.min.js"></script>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      li {
        list-style: none;
      }
      a {
        text-decoration: none;
      }
      .todo {
        width: 400px;
        margin: 50px auto;
      }
      .todo .header {
        padding: 0 20px;
        /* height: 40px; */
        line-height: 40px;
        color: #fff;
        background-color: skyblue;
      }
      .todo .header input {
        height: 30px;
        padding-left: 10px;
        color: #333;
        border: none;
        outline: none;
      }
      .todo .list {
        min-height: 100px;
        margin-top: 20px;
        border: 1px solid #ccc;
      }

      .todo .list li {
        margin: 10px 0;
        padding: 5px 20px;
        background-color: #eee;
      }
      .todo .list p {
        display: inline-block;
        width: 200px;
      }
      .todo .list a {
        float: right;
      }
    </style>
  </head>
  <body>
    <div class="todo">
      <div class="header">
        添加待办: <input id="add" type="text" placeholder="按回车添加待办" />
      </div>
      <div class="list">
        <ul></ul>
      </div>
    </div>

    <script>
      // 添加操作
      $('#add').keyup(function (e) {
        if (e.keyCode == '13') {
          // 得到add的值
          var todo = $('#add').val()

          if (!todo) return

          // 创建元素
          $('.list')
            .find('ul')
            .prepend(`<li><p>${todo}</p><a href="#">删除</a></li>`)

          $('#add').val('')
        }
      })

      // 修改操作
      $('ul').on('click', 'p', function () {
        var p = $(this)
        var todo = p.text()
        var input = $(`<input type="text" value="${todo}"/> `)

        p.html(input)

        input.click(function () {
          input.focus()
          return false
        })

        input.blur(function () {
          var newTxt = $(this).val()
          p.html(newTxt)
        })
        input.keyup(function (e) {
          if (e.keyCode == '13') {
            var newTxt = $(this).val()
            p.html(newTxt)
          }
        })
      })

      // 删除操作
      $('ul').on('click', 'a', function () {
        $(this).parent().remove()
      })
    </script>
  </body>
</html>
```




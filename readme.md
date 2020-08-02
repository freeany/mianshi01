## 1. 基础知识

1. 原型 原型链
2. 作用域 闭包
3. 异步 单线程

## 2. API

1. DOM BOM
2. Ajax跨域
3. 事件存储

## 3. 开发环境

1. 版本管理
2. 调试抓包
3. 打包构建

## 4. 运行环境

1. 页面渲染
2. 性能优化
3. web安全

## 5. 思考

1. 拿到一个面试题，你第一时间看到的是什么
   - 拿到一个面试，第一时间看到的是  -> 考点
2. 如何看到网上搜出来的永远做不完的题海
   - 不变应万变，题可变，考点不变
3. 如何对待接下来遇到的面试题
   - 题目到知识点， 再到题目。当拿到一个题目要有能力知道考点是什么，再到题目



```js
1. typeof 能判断哪些类型
	考点：js变量类型
2. 何时使用 ===  何时使用 == 
    考点：强制类型转换
3. windo.onload 和 window.DOMContentLoaded 的区别
	考点：页面加载过程
4. js手写10个 a标签， 点击的时候弹出对应的序号
	考点：js作用域
5. 手写节流 throttle、防抖debounce
	考点：性能、体验优化
6. promise解决了什么问题
	考点：异步(解决了异步的什么问题，异步的场景是什么)
```

## 6. 前端知识体系

- 什么是知识体系

  - 高效学习三部曲： 找准(注意是找准)知识体系， 刻意训练，及时反馈
  - 知识体系：结构化的知识范围
    - 涵盖所有的知识点：结构化、有组织、易扩展   把知识形成树状

- 从哪些方面梳理

  - w3c **标准**         应用的标准
  - ecma 262**标准**      语法的标准（变量的定义，if else， 函数的定义，原型的方式，闭包的方式 es6等）
  - 开发环境  写代码（代码版本的管理，怎么调试代码，怎么打包上线等）
  - 运行环境  （安全、优化等）

- 知识体系目录 （这里需要整理思维导图）

  - js基础语法
    - 变量类型和计算
      - 值类型和引用类型
      - 类型判断
      - 逻辑运算
    - 原型和原型链
      - class
      - 继承
      - 原型
      - 原型链
      - instanceof
    - 作用域和闭包
      - 作用域
      - 自由变量
      - 闭包
      - this
    - 异步
      - 单线程
      - callback
      - 应用场景
      - promise
    - 模块化
      - es6 module

  - js-web-api
    - DOM
      - 树形结构
      - 节点操作
      - 属性
      - 树结构操作
      - 性能
    - BOM 
      - navigator
      - screen
      - location
      - history
    - 事件
      - 绑定
      - 冒泡
      - 代理
    - ajax
      - XMLHttpRequest
      - 状态码
      - 跨域
    - 存储
      - cookie
      - localStorage
      - sessionStorage
  - 开发环境
    - git
    - 调试
    - webpack 和 babel
    - liunx命令
  - 运行环境
    - 页面加载
      - 加载
      - 渲染
    - 性能优化
      - 加载资源优化
      - 渲染优化
    - 安全
      - xss
      - csrf

## **js基础语法**

1. 栈是key value 的结构，内存中一块存储变量的空间
2. 堆是存放引用类型的空间，key value结构
3. 简单数据类型：number，string， boolean
4. 引用数据类型： 对象，数组，null(特殊引用类型， 指针指向空地址)、
5. 函数： 特殊引用类型，但不用于存储数据，所有没有拷贝、复制函数一说

### typeof 运算符

- 识别所有值类型  undefined string number boolean symbol
- 识别函数   function 
- 判断是否是引用类型，(不可再细分)  object (null, array., object)

### 变量计算 - 类型转换

- 字符串拼接
- == （会发生类型转化）
  - 100 == '100'
  - 0 == ''  0 == false  false == '' 
  - null == undefined
  - 全部用三等
- if语句和逻辑运算
  - if 语句中会 !!变量



## 原型与原型链

1. class和继承
2. 类型判断 instanceof
3. 原型和原型链

### class

- 本质上类似一个模板 对象

- 通过constructor构建一个模板 对象

- 有属性和 方法

- extends继承

- class是原型继承的语法糖 

### 原型

  ```js
  class Student {} 
  typeof Student // function
  const xialuo = new Student()
  // 隐式原型和显式原型
  console.log( xialuo.__proto__ )
  console.log( Student.prototype )
  console.log( xialuo.__proto__ === Student.prototype ) // true
  ```

- 每个class都有显式原型prototype

- 每个实例都有隐式原型 \_\_proto\_\_

- 实例的\_\_proto\_\_ 指向对应class的prototype

#### 基于原型的执行规则

- 获取属性 xialuo.name 或 执行方法 xialuo.sayhi()  时
- 现在自身属性 和 方法寻找
- 如果找不到就自动去 \-\-proto\-\-上去找

### 原型链

- `console.log( Student.prototype.__proto__ )`

- `console.log( People.prototype)`

- `console.log( People.prototype === Student.prototype.__proto__) // true`

- 可以理解为  `Student.prototype.__proto__ 是 new People() 这个对象`
- 原型链的尽头是 Object， Object的`__proto__` 是null

![1596337595976](G:\慕课vip-project\双越js面试\原型链.png)



## 二

知识点： 

- 作用域和自由变量

  - 全局作用域

  - 函数作用域

  - 块级作用域 (ES6新增)

  - 自由变量

    1. 一个变量在当前作用域没有定义，但被使用了, 这就是自由变量

    2. 向上级作用域，一层一层依次查找，知道找到为止
    3. 如果全局作用域都没有找到，则报错 xx is not defined

- 闭包

  - 作用域应用的特殊情况，有两种表现
    - 函数作为参数被传递
    - 函数作为返回值被返回
  - 所有(包括闭包函数)自由变量的查找规则， 是在函数定义的地方，向上级作用域查找， 不是在执行的地方。

- this         (this在各种场景中取什么值不是在函数定义的时候决定的，而是在 执行的时候定义的!!! )

  - 调用方式
    - 作为普通函数
    - 使用call apply  bind 
    - 作为对象方法被调用
    - 在class方法中被调用
    - 箭头函数

- 闭包的在实际开发的应用
  - 闭包隐藏数据，只提供api， 封装的思想

    ```js
    // 闭包隐藏数据，对数据的修改只提供 我暴露的api
    function createCache() {
        const data = {} // 闭包中的数据，被隐藏，不被外界访问
    
        return {
            get: function(key) {
                return data[key]
            },
            set: function(key, value) {
                data[key] = value
            }
        }
    }
    
    const obj = createCache()
    obj.set('a', 100)
    console.log(obj.get('a'))
    ```

    

## 三

- 同步和异步的区别是什么
- 手写用promise 加载一张图片
- 前端使用异步的场景有哪些

### 知识点

- 单线程和异步
  - js是单线程，只能同时做一件事情
  - 浏览器和nodejs 已支持js启动 进程， 如web worker
  - js 和 dom 渲染共用同一个线程， 因为js 可修改 dom结构
  - 遇到等待（网络请求、定时任务）不能卡住
  - 需要异步
  - 回调callback形式调用
  - 异步不会阻塞代码执行
  - 同步会阻塞代码执行
- 应用场景
  - 网络请求，如ajax图片加载
  - 定时任务，如setTimeout
- callback hell 和 promise



## API 介绍

- js 基础知识， 规定语法
- js webapi， 网页操作的api 

- 前者是后者的基础，两者结合才能真正实际应用

### js web api

DOM、 BOM、 事件绑定，ajax、存储

- vue 和 react 框架应用广泛，封装了dom的操作
- 但是dom操作一直都是前端工程师的基础、必备知识

#### 题目

- dom是哪种数据结构
  - 树（DOM树）
- dom操作的常用api
- attr 和 property 的区别
  - property： 修改对象属性， 不会体现到html结构中
  - attribute： 修改html属性， 会改变html(该标签)结构
  - 两种都有可能会引起dom的重新渲染

#### 知识点

- dom本质 dom节点操作 dom结构操作 dom性能
- dom的本质是从html文件 解析出来的一棵树
- 获取dom节点   nodeName nodeType 
- 新增和插入节点
  - createElement appendChild
- 获取父元素和子元素
  - dom.parentNode 和 dom.childNodes(NodeList)

- 删除元素

  - dom.removeChild(dom)

- dom性能

  - dom操作非常昂贵， 避免频繁的dom操作
  - 对dom查询做缓存
  - 将频繁操作改为一次性操作

  ```js
   const list = document.getElementById('list')
  
   // 创建一个文档片段(临时区)， 此时还没有插入到dom结构中
   const frag = document.createDocumentFragment()
  
   for(let i =0;i<10; i++) {
       const li = document.createElement('li')
       li.innerHTML = `List item ${i}`
  
       // 先插入到文档片段中
       frag.appendChild(li)
   }
  // 统一插入到dom结构中
  list.appendChild(frag)
  ```



### bom操作

- 如何识别浏览器的类型
- 分析拆解 url 各个部分

知识点： 

	1. navigator
 	2. screen
 	3. location
 	4. history

### 事件 

- 编写一个通用的事件监听函数  事件绑定
- 描述事件冒泡的流程   事件冒泡
- 无线下拉的图片列表，如何监听每个图片的点击？  事件代理



### webapi - ajax

- XMLHttpRequest

  ```js
   // get 请求
  const xhr = new XMLHttpRequest()
  // 定义请求， true 代表这是异步的请求
  xhr.open('GET', '/data/data.json', true)
  xhr.onreadystatechange = function() {
  
      if(xhr.readyState === 4) {
          if(xhr.status === 200) {
              alert(xhr.responseText)
          }
      }
  }
  
  // 发送请求
  xhr.send(null)
  
  xhr.readyState
  0 - 未初始化——还没有调用send方法
  1 - 载入 -- 已调用send方法， 正在发送请求
  2 - 载入完成 -- send() 方法执行完成，已经接收到全部响应内容
  3 - 交互 -- 正在解析响应内容
  4- 完成 响应 -- 内容解析完成，可以在客户端调用
  
  xhr.status
  2xx - 表示成功处理请求 ，
  3xx - 需要重定向，浏览器直接跳转  如301永久重定向 302临时重定向，下一次不会再跳转了 304资源没有被改变，用浏览器缓存
  4xx - 客户端请求错误， 如404 403
  5xx - 服务器错误
  ```

  

- 状态码

- 跨域： 同源策略， 跨域解决方案

- 同源策略

  - ajax请求时， 浏览器要求当前网页 和 server必须同源（安全）
  - 同源：协议，域名，端口，三者必须一致
  - 加载图片 css js 可无视**浏览器**同源策略
    - `<img src=跨域的图片地址 />`
    - `<link href=跨域的css地址 />`
    - `<script src=跨域的地址 />`
  - 所有的跨域， 都必须经过server端允许和配合
  - 未经server端允许就实现跨域，说明浏览器有漏洞。



### 存储

- cookie
  - 本身时用于浏览器和server通讯

  - 以前蛮荒时期被"借用"到本地存储来

  - 此网站的每个请求都会带上此网站的cookie

  - 客户端通过document.cookie 来操作cookie 

    ```js
    document.cookie = "a=100;b=200"
    同key被覆盖， 不同key时追加
    ```

  - cookie的缺点

    - 存储大小只有4kb
    - http请求时需要发送到服务端， 增加请求数据量
    - 只能用 document.cookie = '...' 来修改， 太过于简陋

- localstorage 和 sessionStorage

  - h5专门未存储而设计的，最大可存5M
  - API简单易用 
  - 不会随着http请求被发送出去

- 描述 cookie localStorage sessionStorage 的区别
  - 容量
  - api 易用性
  - 是否跟随http 请求发送出去





### 移动端h5页面抓包   fiddler

- 手机和电脑同连一个局域网
- 将手机代理到电脑上
- 查看网络请求
- 网络代理
- https



## 运行环境

- 从输入url到渲染出整个页面的过程
- window.onload 和 DOMContentLoaded的区别
  - load事件 是页面的全部资源加载完才会执行，包括图片、视频等
  - DOMContentLoaded事件  是dom渲染完即可执行，此时图片、视频可能还没有加载完成

- 加载页面的形式
  - html代码
  - 媒体文件，图片或视频
  - js css
- 加载资源的过程
  - dns 解析:  域名 -> ip地址 (一些大的网站，可能域名相同，但是ip可能被分区了)
  - 浏览器根据ip地址向服务器发起http请求
  - 服务器处理http请求，并返回给浏览器
- 渲染页面的过程
  - 根据html代码生成dom tree
  - 根据css 代码生成 cssom css object model
  - 将dom tree 和 css dom 整合形成renderer tree
  - 根据renderer tree 渲染页面
  - 遇到script 则暂停渲染， 优先加载并执行js代码， 完成后再继续, js线程和渲染线程是一个线程，因为js可能会改变渲染树
  - 直至renderer tree 渲染完成

- 为什么要把css 放在head中
  - dom和css 同时进行，render tree 形成之后再执行js。
- js为什么放在底部

- 性能优化
  - 性能优化原则
    - 多使用内存、缓存或其他方法
    - 减少cpu计算量，减少网络加载耗时
    - 这就是空间换时间
  - 从何入手
    - 让加载更快
      - 减少资源体积，压缩代码
      - 减少访问次数：合并代码，ssr服务端渲染，缓存
      - 使用更快的网络：CDN
    - 让渲染更快
      - css放在head，js放在body下面
      - 尽早开始执行js，用DOMContentLoaded触发
      - 懒加载 （图片懒加载）
      - 对dom查询进行缓存
      - 频繁dom操作：合并到一起插入dom结构中
      - 节流和防抖



## 安全

- 常见的web前端攻击方式有哪些

- xss 跨站请求攻击

  - 一个博客网站，我发表一篇文章，其中嵌入到script脚本
  - 脚本内容: 获取cookie， 发送到我们的服务器（服务端配合跨域）
  - 发布这篇博客，有人查看他， 我就能轻松获取该用户的cookie

  - xss 预防
    - 替换特殊字符，如< 变为 \&lt; > 变为\&gt;
    - \<script\> 变为\&lt; script\&gt; , 直接显示， 而不会作为脚本执行
    - 前端要替换，后端也要替换，都做总不会有错

- xsrf 跨站请求伪造

  - 你正在购物， 看中了每个商品， 商品id是100
  - 付费接口时xxx.com/pay?id=100,  但是没有验证
  - 我是攻击者，我看中了一个商品， id时200
  - 我向你发送一封电子邮件，邮件标题很吸引人
  - 但邮件正文隐藏着< img src="xxx.com/pay?id=200" />
  - 你查看邮件，就帮我购买了id是200的商品
  - xsrf 预防
    - 使用post接口
    - 增加验证，例如密码，短信验证码，指纹等。




































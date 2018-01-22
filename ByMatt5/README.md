[饥人谷](https://jirengu.com/)  
[伯乐在线 题](http://web.jobbole.com/88041/)

https://www.cnblogs.com/bhan/p/6802644.html  
https://www.zhihu.com/question/41466747?sort=created  
https://www.zhihu.com/question/19568008

# Fragment Knowledge

## If you don't know these things, Do not have an interview!!!
- Http statecode  
100  
200, 201, 202, 203, 204, 206  
300, 301, 302, 304  
400, 401, 403, 404, 405  
500, 501, 503  

- Answer  
1xx - 表示临时响应并需要请求者继续执行操作的状态代码  
100 - continue  
3xx - 表示要完成请求，需要进一步操作。 通常，这些状态代码用来重定向  


## CSS 优先级
> !important > id > class > element

## How many types in JS
- 7, answer from YDKJS
```
string
number
null
undefined
boolean
object
symbol
``` 

`typeof null //object`  
`typeof function(){} //function`  
function被看做是object基本数据类型的一种特殊对象

## How many typeof in JS
- `Symbol('instance')`
```
object
string
number
undefined
boolean
function
symbol
```
## array.pop(2) shift(1) unshift(0)
```js
var array = ['a', 'b', 'c']
array.pop() //'c'
array.shift() //'a'
array.unshift('d') //2
console.log(array) //['d','b']
```

## js事件委托
> stopPropagation

## 阻止事件冒泡
```js
if (event && event.stopPropagation)
    event.stopPropagation()
else
    window.event.cancelBubble = true
```

## 简要介绍你理解的闭包
```js
for(var i=0;i<2;i++){
      (function(i){
             setTimeout(function(){
              console.log(i);
        },0)
    })(i);
}
```
- 隔离作用域
- 闭包就是能够读取其他函数内部变量的函数
- 介绍一下闭包和闭包常用场景  
    闭包是指有权访问另一个函数作用域中的变量的函数.   
    创建闭包常见方式,就是在一个函数内部创建另一个函数.  
    应用场景 设置私有变量和方法  
    不适合场景：返回闭包的函数是个非常大的函数  
    闭包的缺点就是常驻内存，会增大内存使用量，使用不当很容易造成内存泄露。

## js添加 删除 替换 插入到某个接点的方法???
insertBefore

## 实现js继承
- 原型继承、构造函数继承、call aplly继承

```js
//1
function A(name){
    this.name = name;
    this.sayHello = function(){alert(this.name+” say Hello!”);};
}
function B(name,id){
    this.temp = A;
    this.temp(name);        //相当于new A();
    delete this.temp;       
     this.id = id;   
    this.checkId = function(ID){alert(this.id==ID)};
}

//2
class A {
  constructor(){
    this.test1 = 'test1'
  }
}
class B extends A {
//constructor(){super()}
}
new B().test1

//3 by babel
'use strict';

function _possibleConstructorReturn(self, call) { if (!self) { throw new ReferenceError("this hasn't been initialised - super() hasn't been called"); } return call && (typeof call === "object" || typeof call === "function") ? call : self; }

function _inherits(subClass, superClass) { if (typeof superClass !== "function" && superClass !== null) { throw new TypeError("Super expression must either be null or a function, not " + typeof superClass); } subClass.prototype = Object.create(superClass && superClass.prototype, { constructor: { value: subClass, enumerable: false, writable: true, configurable: true } }); if (superClass) Object.setPrototypeOf ? Object.setPrototypeOf(subClass, superClass) : subClass.__proto__ = superClass; }

function _classCallCheck(instance, Constructor) { if (!(instance instanceof Constructor)) { throw new TypeError("Cannot call a class as a function"); } }

var A = function A() {
  _classCallCheck(this, A);

  this.test1 = 'test1';
};

var B = function (_A) {
  _inherits(B, _A);

  function B() {
    _classCallCheck(this, B);

    return _possibleConstructorReturn(this, (B.__proto__ || Object.getPrototypeOf(B)).call(this));
  }

  return B;
}(A);

new B().test1;

//4
var Super = function(name){
  this.name = name;
}
Super.prototype.func1 = function() { console.log('func1'); }
var Sub = function(name,age) {
  Super.call(this, name);
  this.age = age;
}
Sub.prototype = new Super();
```

## nodejs使用场景
非阻塞 异步回调  
IO 密集而非计算密集的情景；高并发微数据（比如账号系统）的情景。特别是高并发，Node.js 的性能随并发数量的提高而衰减的现象相比其他 server 都有很明显的优势
## nodejs优点缺点
(优点)
因为Node是基于事件驱动和无阻塞的，所以非常适合处理并发请求，
因此构建在Node上的代理服务器相比其他技术实现（如Ruby）的服务器表现要好得多。
此外，与Node代理服务器交互的客户端代码是由javascript语言编写的，
因此客户端和服务器端都用同一种语言编写，这是非常美妙的事情。  
(缺点)
Node是一个相对新的开源项目，所以不太稳定，它总是一直在变，
而且缺少足够多的第三方库支持。看起来，就像是Ruby/Rails当年的样子
## gulp and grunt

## 性能优化 前端优化 yslow yahoo23/35条
1、使用css sprites，可以有效的减少http请求数    
2、使用缓存    
3、压缩js，css文件，减小文件体积   
4、使用cdn，减小服务器负担    
5、懒加载图片    
6、预加载css，js文件    
7、避免dom结构的深层次嵌套   
8、给DOM元素添加样式时，把样式放到类中，直接给元素添加类，减少重构，回流



## 一个页面从输入 URL 到页面加载显示完成，这个过程中都发生了什么
https://www.cnblogs.com/jesse131/p/6215961.html  
查找浏览器缓存  
DNS解析、查找该域名对应的IP地址、重定向（301）、发出第二个GET请求  
进行HTTP协议会话  
客户端发送报头(请求报头)  
文档开始下载  
文档树建立，根据标记请求所需指定MIME类型的文件  
文件显示  
浏览器这边做的工作大致分为以下几步：  
加载：根据请求的URL进行域名解析，向服务器发起请求，接收文件（HTML、JS、CSS、图象等）。
解析：对加载到的资源（HTML、JS、CSS等）进行语法解析，建议相应的内部数据结构（比如HTML的DOM树，JS的（对象）属性表，CSS的样式规则等等）
## 介绍下你的项目 并说一下在做这个项目中运用的技术以及遇到的难题是如何解决的

## js
```js
function fun(n,o) {
  console.log(o)
  return {
    fun:function(m){
      return fun(m,n);
    }
  };
}
var a = fun(0);  a.fun(1);  a.fun(2);  a.fun(3);
var b = fun(0).fun(1).fun(2).fun(3);
var c = fun(0).fun(1);  c.fun(2);  c.fun(3);

//scope
var name = 'World!';
(function () {
    if (typeof name === 'undefined') {
        var name = 'Jack';
        console.log('Goodbye ' + name);
    } else {
        console.log('Hello ' + name);
    }
})();

//prototype
function fn() {
    this.a = 0;
    this.b = function() {
        alert(this.a)
    }
}
fn.prototype = {
    b: function() {
        this.a = 20;
        alert(this.a);
    },
    c: function() {
        this.a = 30;
        alert(this.a);
    }
}
var myfn = new fn();
myfn.b();
myfn.c();

//once
function test () {console.log('test')}
 
var once = function (fn) {
  var isFirst = true;
  return function () {
    if (isFirst) {
      isFirst = !isFirst;
      fn();
    }
  };
};
 
var b = once(test);
b(); // 'test'
b(); // nothing
```

## What's REST
http://www.infoq.com/cn/articles/understanding-restful-style/
- REST架构风格最重要的架构约束有6个  
    客户-服务器（Client-Server）
    通信只能由客户端单方面发起，表现为请求-响应的形式。
    
    无状态（Stateless）
    通信的会话状态（Session State）应该全部由客户端负责维护。
    
    缓存（Cache）
    响应内容可以在通信链的某处被缓存，以改善网络效率。
    
    统一接口（Uniform Interface）
    通信链的组件之间通过统一的接口相互通信，以提高交互的可见性。
    
    分层系统（Layered System）
    通过限制组件的行为（即，每个组件只能“看到”与其交互的紧邻层），将架构分解为若干等级的层。
    
    按需代码（Code-On-Demand，可选）
    支持通过下载并执行一些代码（例如JavaApplet、Flash或JavaScript），对客户端的功能进行扩展

- REST是HTTP/1.1协议等Web规范的设计指导原则，HTTP/1.1协议正是为实现REST风格的架构而设计的

- 理解REST的五个关键词  
    资源（Resource）  
    资源的表述（Representation）  
    状态转移（State Transfer）  
    统一接口（Uniform Interface）  
    超文本驱动（Hypertext Driven）


- 7个HTTP方法：GET/POST/PUT/DELETE/PATCH/HEAD/OPTIONS
- 符合REST设计标准的API，即RESTful API。REST架构设计，遵循的各项标准和准则，就是HTTP协议的表现，换句话说，HTTP协议就是属于REST架构的设计模式


## Web service, web api, How to define oneui framework, what's the type?
- Web service的发展趋势  
    1. 在使用方式上，RPC和soap的使用在减少，Restful架构占到了主导地位。  
    2. 在数据格式上，XML格式的使用在减少，json等轻量级格式的使用在增多。  
    3. 在设计架构上，越来越多的第三方软件让用户在客户端（即浏览器），直接与云端对话，不再使用第三方的服务器进行中转或处理数据

- OneUI isn't a web service, it's hosted in IIS, it's just a website


## Write a raw xhr, post and get

```js
var xmlHttp = new XMLHttpRequest();
 
xmlHttp.open('GET','demo.php','true');

xmlHttp.send()

xmlHttp.onreadystatechange = function(){

  if(xmlHttp.readyState === 4 & xmlHttp.status === 200){

  }

}
  
//Promise
function getJSON(url) { 
    return new Promise(function(resolve, reject) { 
        var XHR = new XMLHttpRequest(); 
        XHR.open('GET', url, true); 
        XHR.send(); 
   
        XHR.onreadystatechange = function() { 
            if (XHR.readyState == 4) { 
                if (XHR.status == 200) { 
                    try { 
                        var response = JSON.parse(XHR.responseText); 
                        resolve(response); 
                    } catch (e) { 
                        reject(e); 
                    } 
                } else { 
                    reject(new Error(XHR.statusText)); 
                } 
            } 
        } 
    }) 
} 
   
getJSON(url).then(res => console.log(res));
```

- 当前状态readystate  
0 代表未初始化。 还没有调用 open 方法  
1 代表正在加载。 open 方法已被调用，但 send 方法还没有被调用  
2 代表已加载完毕。send 已被调用。请求已经开始  
3 代表交互中。服务器正在发送响应  
4 代表完成。响应发送完毕  

## post和get的区别
get是从服务器上获取数据，post是向服务器传送数据

get请求可以将查询字符串参数追加到url的末尾; post请求应该把数据作为请求的主体提交.

get请求数据有大小限制；post没有

post比get安全性更高

## cookie and session
cookie数据存放在客户的浏览器上，session数据放在服务器上。

session比cookie更安全

单个cookie保存的数据不能超过4K，很多浏览器都限制一个站点最多保存20个cookie。

一般用cookie来存储sessionid

## call()和apply()的区别, 别忘了bind()
apply => array

## prototype `.__proto__` `.protoype`, extend, instanceof
https://segmentfault.com/a/1190000006146779

## this
## ES6 await async
## [] + {} and {} + []
## 同源策略
## 跨域的方式
http://www.cnblogs.com/rainman/archive/2011/02/20/1959325.html

## why多个dsn处理数据
同一个域名 并发请求有限制，chrome最多6个

## 证书 Certification https
## content-type包含哪些内容
## 强缓存和协商缓存
https://www.cnblogs.com/etoah/p/5579622.html  

- 服务器返回Expires, ETag/Last-Modify  
- 客户端发送If-None-Match/If-Modify-Since 
- 强缓存是利用http的返回头中的Expires或者Cache-Control两个字段来控制的  
1. Expires http1.0中的标准GMT时间 服务器时间， Cache-Control http1.1中的标准max-age  
2. ETag/If-None-Match Last-Modify/If-Modify-Since  
Last-modified: 表明请求的资源上次的修改时间。  
If-Modified-Since：客户端保留的资源上次的修改时间。  
Etag：资源的内容标识。（不唯一，通常为文件的md5或者一段hash值，只要保证写入和验证时的方法一致即可）  
If-None-Match： 客户端保留的资源内容标识。  
⚠️：  
1） 分布式系统尽量关闭Etag，因为每台机器生成的Etag都不一样。  
2）分布式系统里多台机器间文件的Last-Modified必须一致，以免负载均衡不同导致对比失败

- Why Etag  
Last-Modified标注的最后修改只能精确到秒级，如果某些文件在1秒钟以内，被修改多次的话，它将不能准确标注文件的修改时间  
如果某些文件会被定期生成，当有时内容并没有任何变化，但Last-Modified却改变了，导致文件没法使用缓存  
有可能存在服务器没有准确获取文件修改时间，或者与代理服务器时间不一致等情形  

## What's the difference between ready and onload
$(document).ready(), window.onload = function (){}

## FP Function Programming, Currying and Uncurrying
https://zhuanlan.zhihu.com/p/22094473  
对于相同的输入，永远会得到相同的输出，而且没有任何可观察的副作用，也不依赖外部环境的状态

1. no side effect
2. immutable
3. function first  
4. 
没有并发编程的问题，是多线程安全的

- 引用透明（Referential transparency）
- 没有副作用（No Side Effect）
## 时间复杂度
## Closure

## Vuejs如何实现双向数据绑定 AngularJS dirty check
## AMD and CMD and ES6 import export
## css3 box-sizing: content-box and border-box
http://blog.csdn.net/practicer2015/article/details/46454921  
- 实现三个DIV等分排布在一行（考察border-box）
- 为什么看起来content-box更合理，但是还是经常使用border-box  
content-box 是W3C的标准盒模型 元素宽度=内容宽度+padding+border  
border-box 是ie的怪异盒模型  他的元素宽度等于内容宽度  内容宽度包含了padding和border

## bootstrap的栅格系统如何实现的
box-sizing: border-box;  
container row column设置百分比

## JavaScript的内存回收机制

## 数防抖和函数节流

```js
//函数防抖
var timer = false
document.getElementById("debounce").onScroll = function() {
        clearTimeout(timer)  
        timer = setTimeout(function(){
                console.log(‘函数防抖’) 
  }, 300)     
}
//函数节流
var canScroll = true;
document.getElementById('throttle').onScroll = function() {
               if (!canScroll) {
                return;
               }
                canScroll = false;
                setTimeout(function(){
                   console.log('函数节流');
                   canScroll = true;
                },300)       
}
```

## What's BFC: Block formatting context/块级格式化上下文
http://web.jobbole.com/84808/  
http://web.jobbole.com/83274/  
https://segmentfault.com/a/1190000006740129

- BFC就是隔离子元素 成一个独立的行政区域，之间互不影响
- BFC包含创建该上下文元素的所有子元素，但不包括创建了新BFC的子元素的内部元素
- 一个元素不能同时存在于两个BFC中

- 简单归纳一下：
    1. 内部的盒会在垂直方向一个接一个排列（可以看作BFC中有一个的常规流）；
    2. 处于同一个BFC中的元素相互影响，可能会发生margin collapse；  
    即使不是bfc中也会重叠啊！！！错误理解，其实都在root bfc下  
    解读：设置不同的bfc可以防止重叠(额外添加bfc)
    
    3. 每个元素的margin box的左边，与容器块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此；
    4. BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素，反之亦然；
    5. 计算BFC的高度时，考虑BFC所包含的所有元素，连浮动元素也参与计算；  
    解读：非bfc的容器不会将float元素的高度计算在内
    
    6. BFC的区域不会与float的元素区域重叠/浮动盒区域不叠加到BFC上

- 总的解读：  
    因为BFC内部的元素和外部的元素绝对不会互相影响，因此， 当BFC外部存在浮动时，它不应该影响BFC内部Box的布局，BFC会通过变窄，而不与浮动有重叠。同样的，当BFC内部有浮动时，为了不影响外部元素的布局，BFC计算高度时会包括浮动的高度。避免margin重叠也是这样的一个道理。

- Why  
http://en.jsrun.net/FfqKp/edit  
div.right>div.little为什么会换行，既然float已经按照bfc来定位，为什么还受到了非bfc的parent right的影响

- 满足下列CSS声明之一的元素便会生成BFC，最常见的就是overflow:hidden、float:left/right、position:absolute
    1. 根元素
    2. float属性不为none
    3. overflow不为visible
    4. display为inline-block, table-cell, table-caption //弹性盒 flex boxes: flex, inline-flex
    5. position为absolute或fixed

## float
- 当先有div时 float元素在下面
- 当先有float时 div会覆盖在左上角

## margin collapse
- 避免外边距折叠
    1. float
    2. parent bfc(overflow: hidden)
    3. inline-block/not block element


## h5的新特性
https://www.zhihu.com/question/41466747?sort=created
## css盒模型 写一个layout

## 多个页面之间如何进行通信????????????????????????????
使用cookie，使用web worker，使用localeStorage和sessionStorage

## webSocket如何兼容低浏览器

## 浏览器的渲染过程
1. Html/xhtml/svg => dom tree  
DOM 树的构建过程是一个深度遍历过程：当前节点的所有子节点都构建好后才会去构建当前节点的下一个兄弟节点
2. css => css rule tree
3. dom tree, cssom tree => render tree

- Reflow回流， Repaint重绘
    1. Reflow（回流）：浏览器要花时间去渲染，当它发现了某个部分发生了变化影响了布局，那就需要倒回去重新渲染。 
    2. Repaint（重绘）：如果只是改变了某个元素的背景颜色，文字颜色等，不影响元素周围或内部布局的属性，将只会引起浏览器的repaint，重画某一部分。 
    Reflow要比Repaint更花费时间，也就更影响性能。所以在写代码的时候，要尽量避免过多的Reflow

- reflow的原因  
（1）页面初始化的时候；   
（2）操作DOM时；   
（3）某些元素的尺寸变了；   
（4）如果 CSS 的属性发生变化了

- 减少reflow/repaint  
（1）不要一条一条地修改 DOM 的样式。与其这样，还不如预先定义好 css 的 class，然后修改 DOM 的 className。   
（2）不要把 DOM 结点的属性值放在一个循环里当成循环里的变量。   
（3）为动画的 HTML 元件使用 fixed 或 absoult 的 position，那么修改他们的 CSS 是不会 reflow 的。   
（4）千万不要使用 table 布局。因为可能很小的一个小改动会造成整个 table 的重新布局。

- HTML页面加载和解析流程 
    1. 用户输入网址（假设是个html页面，并且是第一次访问），浏览器向服务器发出请求，服务器返回html文件； 
    2. 浏览器开始载入html代码，发现＜head＞标签内有一个＜link＞标签引用外部CSS文件； 
    3. 浏览器又发出CSS文件的请求，服务器返回这个CSS文件； 
    4. 浏览器继续载入html中＜body＞部分的代码，并且CSS文件已经拿到手了，可以开始渲染页面了； 
    5. 浏览器在代码中发现一个＜img＞标签引用了一张图片，向服务器发出请求。此时浏览器不会等到图片下载完，而是继续渲染后面的代码； 
    6. 服务器返回图片文件，由于图片占用了一定面积，影响了后面段落的排布，因此浏览器需要回过头来重新渲染这部分代码； 
    7. 浏览器发现了一个包含一行Javascript代码的＜script＞标签，赶快运行它； 
    8. Javascript脚本执行了这条语句，它命令浏览器隐藏掉代码中的某个＜div＞ （style.display=”none”）。突然少了这么一个元素，浏览器不得不重新渲染这部分代码； 
    9. 终于等到了＜/html＞的到来，浏览器泪流满面…… 
    10. 等等，还没完，用户点了一下界面中的“换肤”按钮，Javascript让浏览器换了一下＜link＞标签的CSS路径； 
    11. 浏览器召集了在座的各位＜div＞＜span＞＜ul＞＜li＞们，“大伙儿收拾收拾行李，咱得重新来过……”，浏览器向服务器请求了新的CSS文件，重新渲染页面

- js为什么阻塞dom渲染  
    执行时会阻塞页面后续的内容（包括页面的渲染、其它资源的下载）。原因：因为浏览器需要一个稳定的DOM树结构，而JS中很有可能有 代码直接改变了DOM树结构，比如使用 document.write 或 appendChild,甚至是直接使用的location.href进行跳转，浏览器为了防止出现JS修 改DOM树，需要重新构建DOM树的情况，所以 就会阻塞其他的下载和呈现

- 重构、回流  
    浏览器的重构指的是改变每个元素外观时所触发的浏览器行为，比如颜色，背景等样式发生了改变而进行的重新构造新外观的过程。重构不会引发页面的重新布局，不一定伴随着回流，回流指的是浏览器为了重新渲染页面的需要而进行的重新计算元素的几何大小和位置的，他的开销是非常大的，回流可以理解为渲染树需要重新进行计算，一般最好触发元素的重构，避免元素的回流；比如通过通过添加类来添加css样式，而不是直接在DOM上设置，当需要操作某一块元素时候，最好使其脱离文档流，这样就不会引起回流了，比如设置position：absolute或者fixed，或者display：none，等操作结束后在显示


## new 操作符到底做了什么

## 导入css的link和@import有什么区别

## iframe的优点和缺点
https://www.zhihu.com/question/20653055  

iframe会阻塞主页面的Onload事件；  
iframe和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。  
使用iframe之前需要考虑这两个缺点。如果需要使用iframe，最好是通过javascript动态给iframe添加src属性值，这样可以可以绕开以上两个问题。

## webSocket如何兼容低浏览器？(阿里)
## line-height
## css3 弹性布局 flex box
## 实现JS轮播插件原理
## ajax原理
## sass和less区别




























## 跨域通信有哪些方案
## 多页面通信有哪些方案
## XSS和CSRF攻击
http://blog.csdn.net/ghsau/article/details/17027893  
http://www.cnblogs.com/hyddd/archive/2009/04/09/1432744.html  
防范：验证码 token 来源检测
## 严格模式
严格模式对Javascript的语法和行为，都做了一些改变。

全局变量必须显式声明。

对象不能有重名的属性

函数必须声明在顶层

消除Javascript语法的一些不合理、不严谨之处，减少一些怪异行为;  
消除代码运行的一些不安全之处，保证代码运行的安全；  
提高编译器效率，增加运行速度；  
为未来新版本的Javascript做好铺垫。







## Others======================================>
## 二叉树面试题
## 排序问题
- 快速排序

```js
var quickSort = function (arr){
        if(arr.lenght <= 1) {
           return arr;
          }
 
       var left = [];
       var right = [];
       var mid = arr.splice(Math.floor(arr.length/2), 1);
 
       for(var i=0;i<arr.length;i++){
             if(arr[i]<mid) {
                 left.push(arr[i]);
            }
             if(arr[i]>mid) {
                 right.push(arr[i]);
            }
          return quickSort(left).concat(mid, quickSort(right));
     }  
}
```
## css移动
jquery的animate方法  
css3的transition

## 深拷贝
```js
var clone = function(v) {
  var o = v.constructor === Array ? [] : {};
  for (var i in v) {
    o[i] = typeof v[i] === "Object" ? clone(v[i]) : v[i];
  }
  return o;
}
```

## Determine array
```js
a instanceof Array
a.constructor == Array
Object.prototype.toString.call(a) == [Object Array]
```

## refresh for cachce
f5 304， ajax 200 from cache
f5浏览器行为，跳过强缓存200 from cache

## memory cache and disk cache
https://www.zhihu.com/question/64201378  

## 图片预加载 懒加载
## 关于nginx
## MVVM MVC
mvc的界面和逻辑关联紧密，数据直接从数据库读取，必须通过Controller来承上启下，通信都是单向的。  
mvvm的View 和 ViewModel可以互相通信，界面数据从viewmodel中获取。

## 浏览器兼容问题
## 正则表达式?????????????????????????????????

## CSS Position

position | description
---|---
absolute | 生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定
fixed | 生成绝对定位的元素，相对于浏览器窗口进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。
relative | 生成相对定位的元素，相对于其正常位置进行定位。因此，"left:20" 会向元素的 LEFT 位置添加 20 像素。
static | 默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right 或者 z-index 声明）。inherit	规定应该从父元素继承 position 属性的值。 

## position:absolute和float属性的异同
## 伪类和伪元素
https://www.cnblogs.com/ghost-xyx/p/3763669.html

## ajax无法后退的问题
HTML5里引入了新的API，即：history.pushState, history.replaceState

可以通过pushState和replaceState接口操作浏览器历史，并且改变当前页面的URL。

onpopstate监听后退

## 页面的加载顺序
html顺序加载，其中js会阻塞后续dom和资源的加载，css不会阻塞dom和资源的加载但是会阻塞js的加载。

浏览器会使用prefetch对引用的资源提前下载

1.没有 defer 或 async，浏览器会立即加载并执行指定的脚本

2.有 async，加载和渲染后续文档元素的过程将和 script.js 的加载与执行并行进行(下载异步，执行同步，加载完就执行)。

3.有 defer，加载后续文档元素的过程将和 script.js 的加载并行进行（异步），但是 script.js 的执行要在所有元素解析完成之后，DOMContentLoaded 事件触发之前完成。

## websocket和ajax轮询




## ES6 Knowledge====================>

## Vuejs Angular Reactjs Knowledge
## vuejs生命周期 事件
beforecreated：el 和 data 并未初始化  
created:完成了 data 数据的初始化，el没有  
beforeMount：完成了 el 和 data 初始化   
mounted ：完成挂载　　updated；destroyed 





## Review Knowledge====================>
## `parseInt('c2')`




## youdao OpenAPI====================>
http://note.youdao.com/open/download/apidoc_1.1.0.pdf  
http://note.youdao.com/open/apidoc.html
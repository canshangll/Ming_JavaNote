# JavaWeb学习笔记

### JavaScript

```javascript
浏览器支持就可以使用得语言
//语法
<script type="text/javascript" src="1.js">
	....//编写逻辑代码   //如果src 已经引用则只会用 1.js里面的逻辑代码
</script>
```

#### JS变量

```javascript
JavaScript的变量类型:
	数值类型:number
    字符串类型:string
    对象类型:object
    布尔类型:boolean
    函数类型:function
JavaScript里特殊的值:
	undefined:未定义,所有js变量未赋于初始值的时候，默认值都是undefined
	null:空值
    NAN:全称是:Not a Number.非数字，非数值。

JavaScript定义变量
	var 变量名;
    var 变量名=值;
```

#### 关系(比较)运算符-常用

```javascript
等于: == 等于是简单的做字面值的比较
全等于: === 除了做字面值的比较之外,还会比较两个变量的数据类型
```

#### 逻辑运算符

```javascript
且运算:&&
或运算:||
取反运算:!
在JavaScript语言中,所有的变量,都可以做为一个boolean类型的变量去使用.
0、null、undefined、""(空串) 都认为是false
    
&&且运算: (有两种情况)
第一种:当表达式全为真的时候。返回最后一个表达式的值。
第二种:当表达式中,有一个为假的时候.返回第一个为假的表达式的值
||或运算
第一种情况:当表达式全为假时,返回最后一个表达式的值
第二种情况:只要有一个表达式为真.就会把回第一个为真的表达式的值
//并且&&与运算 和 ||或运算 有短路
短路就是说,当这个&&或||运算有结果之后。后面的表达式不在执行
```

#### 数组

```javascript
JavaScript数组的定义:
	var 数组名 = [];//空数组
	var 数组名 = [1,'abc',true];//定义数组同时赋值元素
```

#### 函数

```javascript
函数有两种定义方式
//第一种,可以使用function关键字来定义函数
语法：
	function 函数名(形参列表){
        函数体
    }
//第二种
语法：
	var 函数名 = function (形参列表){
        函数体
    }
//注：在Java中允许函数重载。但在JavaScript中函数的重载会直接覆盖掉上一次的定义.
    
//隐形参数arguments(只在function函数内)
在function函数中不需要定义,但却可以直接用来获取所以参数的变量，叫隐形参数。
隐形参数特别像java基础的可变长参数一样。
public void fun(Object ...args);
可变长参数其实是一个数组
JavaScript中的隐形参数也跟java的可变参数一样。操作类似数组
```

#### 自定义对象

```javascript
//Object形式的自定义对象
对象的定义:
	var 变量名 = new Object();	//对象实例(空对象)
	变量名.属性名 = 值	//定义一个属性
	变量名.函数名 = function(){}	//定义一个函数
对象的访问:
	变量名.属性 / 函数名();

//花括号形式自定义对象
对象的定义:
	var 变量名 = {	//空对象
        属性名 : 值,	//定义一个属性
        属性名 : 值,	//定义一个属性
        函数名 : function(){}	//定义一个函数
    };	
对象的访问:
	变量名.属性 / 函数名();
```

#### 事件

```javascript
//常用的事件:
onload加载完成事件:	页面加载完成之后,常用于做页面js代码初始化操作
onclick单击事件:	常用于按钮的点击响应操作
onblur失去焦点事件:	常用用于输入框失去焦点后验证其输入内容是否合法
onchange内容改变事件:	常用于下拉列表和输入框内容发送改变后操作
onsubmit表单提交事件:	常用于表单提交前,验证所有表单项是否合法

//事件的注册(静态注册和动态注册)
静态注册事件:通过HTML标签的事件属性直接赋于事件响应后的代码,这种方式叫静态事件
动态注册事件:是指先通过js代码得到标签的dom对象,然后再通过dom对象.事件名 = function(){} 这种形式赋于事件响应后的代码,叫动态注册
	动态注册基本步骤:
		1、获取标签对象
        2、标签对象.事件名 = function(){}
```

#### DOM模型

```javascript
DOM 全称 Document Object Model 文档对象模型
把文档中的标签，属性，文本，转换成对象来管理
//Document对象的理解:
1、Document它管理了所有的Html的文档内容
2、document它是一种树结构的文档。有层级关系
3、它让我们把所有的标签都对象化
4、我们可以通过document访问所有的标签对象
```

```javascript
<body>
    <div id="div01">
        div01
    </div>
</body>
模拟对象化，相当于
class Dom{
	private String id; //id属性
    private String tagName; //表示标签名
    private Dom parentNode; //父亲
    private List<Dom> children; //孩子结点
	private String innerHTML; //起始标签和结束标签中间的内容
}
```

```javascript
//Document对象中的方法介绍
document.getElementById(elementId)
通过标签的id属性查找标签dom对象,elementId是标签的id属性值
document.getElementsByName(elementName)
通过标签的name属性查找标签dom对象,elementName 标签的name属性值
document.getElementsByTagName(tagname)
通过标签名查找标签dom对象.tagname是标签名
document.createElement(tagName)
通过给定的标签名,创建一个标签对象.tagName是要创建的标签名
//注：
document 对象的三个查询方法，如果有id属性，优先使用getElementById方法来进行查询
如果没有id属性，则优先使用 getElementsByName方法来进行查询
如果id属性和name属性都没有最后再按标签名查询getElementsByTagName
以上三个方法，一定要在页面加载完成之后执行，才能查询到标签对象
//属性
childNodes属性,获取当前节点的所有子节点
firstChild属性,获取当前节点的第一个子节点
lastChild属性,获取当前节点的最后一个子节点
parentNode属性,获取当前节点的父节点
nextSibling属性,获取当前节点的下一个节点
previousSibling属性,获取当前节点的上一个节点
className属性,用于获取当前节点的上一个节点
innerHTML属性,表示获取/设置起始标签和结束标签中的内容
innerText属性,表示获取/设置起始标签和结束标签中的文本
```

### JQuery

#### JQueryFAQ

```javascript
1、使用jQuery一定要引入jQuery库
2、jQuery中的 $ 是一个函数
3、给按钮添加点击事件：使用jQuery查询到标签对象，使用标签对象.click(function(){});
```

```javascript
    <script type="text/javascript" src="../script/jquery-1.7.2.js"></script>
    <script type="text/javascript">
        // window.onload = function () {
        //     var btnObj = document.getElementById("btnId");
        //     // alert(btnObj);//[object HTMLButtonElement] ===>> dom对象
        //     btnObj.onclick=function () {
        //         alert("js 原生的单击事件");
        //     }
        // }
        $(function () { //表示页面加载完成之后 相当于 window.onload = function(){}
            var $btnObj = $("#btnId");//表示按id查询标签对象
            $btnObj.click(function () {
                alert("jQuery 的单击事件")
            })
        });
```

#### JQuery核心函数

```javascript
1、传入参数为[函数]时:表示页面加载完成之后，相当于 window.onload = function(){}
2、传入参数为[HTML 字符串]时:会对我们创建这个html标签对象
3、传入参数为[选择器字符串]时:
	$("#id属性值"):id选择器,根据id查询标签对象
	$("标签名"):标签名选择器,根据指定的标签名查询标签对象
	$(".class属性值"):类型选择器,可以根据class属性查询标签对象
4、传入参数为[DOM对象]时:会把这个dom对象转换为JQuery对象
```

#### JQuery对象和Dom对象

  ```javascript
  //Dom对象
  1、通过getElementById()查询出来的标签对象是Dom对象
  2、通过getElementByName()查询出来的标签对象是Dom对象
  3、通过getElementByTagName()查询出来的标签对象是Dom对象
  4、通过createElement()方法创建的对象,是Dom对象
  //JQuery对象
  5、通过JQuery提供的API创建的对象,是JQuery对象
  6、通过JQuery包装的Dom对象,也是JQuery对象
  7、通过JQuery提供的API查询到的对象,是Jquery对象
  
  DOM对象Alert出来的效果是: [object HTML 标签名 Element]
  JQuery对象Alert出来的效果是: [object Object]
  
  //JQuery对象是dom对象的数组 + Jquery提供的一些列功能函数。
  //JQuery对象和Dom对象使用区别
  JQuery对象不能使用DOM对象的属性和方法
  DOM对象也不能使用JQuery对象的属性和方法
  //DOM对象和JQuery对象互转
  1、dom对象转化为JQuery对象：1.现有DOM对象 2.$(DOM对象)就可以转换成为JQuery对象
  2、JQuery对象转为dom对象：1.先有JQuery对象 2.JQuery对象[下标]取出相应的DOM对象
  ```

```sequence
Dom对象->JQuery对象: dom对象转换成为jQuery对象
JQuery对象->Dom对象: jQuery对象转换成为dom对象 var dom = $obj[下标]
```

#### JQuery选择器

```js
//基本选择器
#ID 	 选择器：根据 id 查找标签对象 
.class   选择器：根据 class 查找标签对象 
element  选择器：根据标签名查找标签对象
*  		 选择器：表示任意的，所有的元素 
selector1，selector2 组合选择器：合并选择器 1，选择器 2 的结果并返回
// p.myClass 表示标签名必须是 p 标签，而且 class 类型还要是 myClass

//层级选择器
ancestor descendant 后代选择器 ：在给定的祖先元素下匹配所有的后代元素 
parent > child 子元素选择器：在给定的父元素下匹配所有的子元素 
prev + next 相邻元素选择器：匹配所有紧接在 prev 元素后的 next 元素 
prev ~ sibings 之后的兄弟元素选择器：匹配 prev 元素之后的所有 siblings 元素

//基本过滤器
:first 获取第一个元素 
:last 获取最后个元素 
:not(selector) 去除所有与给定选择器匹配的元素 
:even 匹配所有索引值为偶数的元素，从 0 开始计数 
:odd 匹配所有索引值为奇数的元素，从 0 开始计数 
:eq(index) 匹配一个给定索引值的元素 :gt(index) 匹配所有大于给定索引值的元素 :lt(index) 匹配所有小于给定索引值的元素 :header 匹配如 h1, h2, h3 之类的标题元素 :animated 匹配所有正在执行动画效果的元素

//内容过滤器
:contains(text) 匹配包含给定文本的元素 
:empty 匹配所有不包含子元素或者文本的空元素 
:parent 匹配含有子元素或者文本的元素 
:has(selector) 匹配含有选择器所匹配的元素的元素

//属性过滤器
[attribute] 匹配包含给定属性的元素。 
[attribute=value] 匹配给定的属性是某个特定值的元素 
[attribute!=value] 匹配所有不含有指定的属性，或者属性不等于特定值的元素。 [attribute^=value] 匹配给定的属性是以某些值开始的元素 
[attribute$=value] 匹配给定的属性是以某些值结尾的元素 
[attribute*=value] 匹配给定的属性是以包含某些值的元素 
[attrSel1][attrSel2][attrSelN] 复合属性选择器，需要同时满足多个条件时使用。

//表单过滤器
:input 匹配所有 input, textarea, select 和 button 元素 :text 匹配所有 文本输入框 :password 匹配所有的密码输入框 
:radio 匹配所有的单选框 :checkbox 匹配所有的复选框 
:submit 匹配所有提交按钮 
:image 匹配所有 img 标签 
:reset 匹配所有重置按钮 
:button 匹配所有 input type=button <button>按钮 
:file 匹配所有 input type=file 文件上传 
:hidden 匹配所有不可见元素 display:none 或 input type=hidden

:enabled 匹配所有可用元素 
:disabled 匹配所有不可用元素 
:checked 匹配所有选中的单选，复选，和下拉列表中选中的 option 标签对象 
:selected 匹配所有选中的 option
```

#### JQuery元素筛选

```js
eq() 获取给定索引的元素 功能跟 :eq() 一样 
first() 获取第一个元素 功能跟 :first 一样 
last() 获取最后一个元素 功能跟 :last 一样 
filter(exp) 留下匹配的元素 
is(exp) 判断是否匹配给定的选择器，只要有一个匹配就返回，true has(exp) 返回包含有匹配选择器的元素的元素 功能跟 :has 一样 
not(exp) 删除匹配选择器的元素 功能跟 :not 一样 
children(exp) 返回匹配给定选择器的子元素 功能跟 parent>child 一样 
find(exp) 返回匹配给定选择器的后代元素 功能跟 ancestor descendant 一样
next() 返回当前元素的下一个兄弟元素 功能跟 prev + next 功能一样 
nextAll() 返回当前元素后面所有的兄弟元素 功能跟 prev ~ siblings 功能一样
nextUntil() 返回当前元素到指定匹配的元素为止的后面元素
parent() 返回父元素 
prev(exp) 返回当前元素的上一个兄弟元素
prevAll() 返回当前元素前面所有的兄弟元素
prevUnit(exp) 返回当前元素到指定匹配的元素为止的前面元素 
siblings(exp) 返回所有兄弟元素 
add() 把 add 匹配的选择器的元素添加到当前 jquery 对象中
```

#### JQuery属性操作

```js
html() 它可以设置和获取起始标签和结束标签中的内容。 跟 dom 属性 innerHTML 一样。 text() 它可以设置和获取起始标签和结束标签中的文本。 跟 dom 属性 innerText 一样。 val() 它可以设置和获取表单项的 value 属性值。 跟 dom 属性 value 一样
attr() 可以设置和获取属性的值，不推荐操作 checked、readOnly、selected、disabled 等等 attr 方法还可以操作非标准的属性。比如自定义属性：abc,bbj 
prop() 可以设置和获取属性的值,只推荐操作 checked、readOnly、selected、disabled 等等
```

#### DOM的增删改

```js
//内部插入： 
appendTo() a.appendTo(b) 把 a 插入到 b 子元素末尾，成为最后一个子元素
prependTo() a.prependTo(b) 把 a 插到 b 所有子元素前面，成为第一个子元素 
//外部插入： 
insertAfter() a.insertAfter(b) 得到 ba 
insertBefore() a.insertBefore(b) 得到 ab 
//替换: 
replaceWith() a.replaceWith(b) 用 b 替换掉 a 
replaceAll() a.replaceAll(b) 用 a 替换掉所有 b 
//删除：
remove() a.remove(); 删除 a 标签 
empty() a.empty(); 清空 a 标签里的内容
```

#### css样式操作

```js
addClass() 添加样式 
removeClass() 删除样式 
toggleClass() 有就删除，没有就添加样式。 
offset() 获取和设置元素的坐标。
```

#### JQuery动画

```js
//基本动画 
show() 将隐藏的元素显示 
hide() 将可见的元素隐藏。 
toggle() 可见就隐藏，不可见就显示。 
	以上动画方法都可以添加参数。 
		1、第一个参数是动画 执行的时长，以毫秒为单位 
		2、第二个参数是动画的回调函数 (动画完成后自动调用的函数) 
//淡入淡出动画
fadeIn() 淡入（慢慢可见） 
fadeOut() 淡出（慢慢消失）
fadeTo() 在指定时长内慢慢的将透明度修改到指定的值。0 透明，1 完成可见，0.5 半透明 fadeToggle() 淡入/淡出 切换
```

#### JQuery事件操作

```js
$( function(){} ); 
和
window.onload = function(){} 的区别？ 
他们分别是在什么时候触发？ 
1、jQuery 的页面加载完成之后是浏览器的内核解析完页面的标签创建好 DOM 对象之后就会马上执行。 
2、原生 js 的页面加载完成之后，除了要等浏览器内核解析完标签创建好 DOM 对象，还要等标签显示时需要的内容加载 完成。
```

##### JQuery中其他的事件处理方法

```js
click() 它可以绑定单击事件，以及触发单击事件 
mouseover() 鼠标移入事件 
mouseout() 鼠标移出事件 
bind() 可以给元素一次性绑定一个或多个事件。
one() 使用上跟 bind 一样。但是 one 方法绑定的事件只会响应一次。 
unbind() 跟 bind 方法相反的操作，解除事件的绑定
live() 也是用来绑定事件。它可以用来绑定选择器匹配的所有元素的事件。哪怕这个元素是后面动态创建出 来的也有效
```

##### 事件的冒泡

```js
//什么是事件的冒泡？ 
事件的冒泡是指，父子元素同时监听同一个事件。当触发子元素的事件的时候，同一个事件也被传递到了父元素的事件里去 响应。 
//那么如何阻止事件冒泡呢？
在子元素事件函数体内，return false; 可以阻止事件的冒泡传递。
```

##### JavaScript事件对象

```js
事件对象，是封装有触发的事件信息的一个 javascript 对象。 我们重点关心的是怎么拿到这个 javascript 的事件对象。以及使用。 
如何获取呢 javascript 事件对象呢？
在给元素绑定事件的时候，在事件的 function( event ) 参数列表中添加一个参数，这个参数名，我们习惯取名为 event。 这个 event 就是 javascript 传递参事件处理函数的事件对象。
```

### XML

 [hamcrest-core-1.3.jar](..\资料\资料\05-XML & Tomcat\代码\05_xml\lib\hamcrest-core-1.3.jar) 

 [junit-4.12.jar](..\资料\资料\05-XML & Tomcat\代码\05_xml\lib\junit-4.12.jar) 

#### xml的作用

```xml
xml 的主要作用有： 
1、用来保存数据，而且这些数据具有自我描述性 
2、它还可以做为项目或者模块的配置文件 
3、还可以做为网络传输数据的格式（现在 JSON 为主）。
```

#### xml语法

```xml
1. 文档声明。 2. 元素（标签） 3. xml 属性 4. xml 注释 5. 文本区域（CDATA 区）
```

#### **xml** **注释** 

```xml
html 和 XML 注释 一样 : <!-- html 注释 -->
```

#### xml命名规则

```xml
1.名称可以含字母、数字以及其他的字符
2.名称不能以数字或者标点符号开始
3.名称不能包含空格
4.xml 中的元素（标签）也 分成 单标签和双标签：
单标签 格式： <标签名 属性=”值” 属性=”值” ...... /> 
双标签 格式：< 标签名 属性=”值” 属性=”值” ......>文本数据或子标签</标签名>
```

#### xml属性

```xml
xml 的标签属性和 html 的标签属性是非常类似的，属性可以提供元素的额外信息 
在标签上可以书写属性：
一个标签上可以书写多个属性。每个属性的值必须使用 引号 引起来。 的规则和标签的书写规则一致。
```

#### xml语法规则

```xml
1.所有 XML 元素都须有关闭标签（也就是闭合）
2.XML 标签对大小写敏感
3.XML 必须正确地嵌套
4.XML 文档必须有根元素
5.XML 的属性值须加引号
6.XML 中的特殊字符
7.文本区域（CDATA 区）
```

#### xml解析🔺

```xml
xml 可扩展的标记语言。 
不管是 html 文件还是 xml 文件它们都是标记型文档，都可以使用 w3c 组织制定的 dom 技术来解析。
document 对象表示的是整个文档（可以是 html 文档，也可以是 xml 文档）
```

```xml
早期JDK为我们提供了两种xml解析技术DOM和Sax简介（已经过时，但我们需要知道这两种技术）
第三方的解析： 
jdom 在 dom 基础上进行了封装;
dom4j 又对 jdom 进行了封装;
pull 主要用在 Android 手机开发，是在跟 sax 非常类似都是事件机制解析 xml 文件。

<-注：这个 Dom4j 它是第三方的解析技术。我们需要使用第三方给我们提供好的类库才可以解析 xml 文件。
```

#### **dom4j**解析技术🔺

```xml
由于 dom4j 它不是 sun 公司的技术，而属于第三方公司的技术，我们需要使用 dom4j 就需要到 dom4j 官网下载 dom4j 的 jar 包。
```

 [dom4j-1.6.1.jar](..\资料\资料\05-XML & Tomcat\代码\05_xml\lib\dom4j-1.6.1.jar) 

##### 使用：

先编写需要解析 xml文件：books.xml

```xml
<?xml version="1.0" encoding="utf-8" ?>
<books>
    <book sn="SN12144">
        <name>时间简史</name>
        <author>霍金</author>
        <price>75</price>
    </book>
    <book sn="SN12144123123">
        <name>时间简史2</name>
        <author>霍金1</author>
        <price>75</price>
    </book>
</books>
```

编写Book类：（简要）

```java
    public Book(String sn, String name, BigDecimal price, String author) {
        this.sn = sn;
        this.name = name;
        this.price = price;
        this.author = author;
    }
```

读取books.xml 文件生成Book类

```java
    @Test
    public void  Test2() throws Exception{
        //1、读取books.xml文件
        SAXReader reader = new SAXReader();
        //在 Junit测试中，相对路径是从模块名开始算
        Document document = reader.read("src/books.xml");
        //2、通过Document对象获取根元素
        Element rootElement = document.getRootElement();
        //3、通过根元素获取book标签对象
        //element()和elements() 都是通过标签名查找子元素
        List<Element> books = rootElement.elements("book");
        //4、遍历，处理每个book标签转换为Book类
        for (Element book : books) {
            Element nameElement = book.element("name");
            // asXMl() 把标签对象。转换为标签字符串
            //getText() 可以获取标签中的文本内容
            String text = nameElement.getText();
            String price = book.elementText("price");
            String author = book.elementText("author");
            String sn = book.attributeValue("sn");
            System.out.println(new Book(sn,text,BigDecimal.valueOf(Double.parseDouble(price)),author));
        }
输出：
Book{sn='SN12144', name='时间简史', price=75.0, author='霍金'}
Book{sn='SN12144123123', name='时间简史2', price=88.0, author='霍金1'}       
```

### JavaWeb概念

```java
//什么是 JavaWeb 
JavaWeb 是指，所有通过 Java 语言编写可以通过浏览器访问的程序的总称，叫 JavaWeb。 JavaWeb 是基于请求和响应来开发的。
//什么是请求
请求是指客户端给服务器发送数据，叫请求 Request。
//什么是响应  
响应是指服务器给客户端回传数据，叫响应 Response。    
//请求和响应的关系    
请求和响应是成对出现的，有请求就有响应。
```

```sequence
客户端(浏览器)->服务器(Tomcat): 客户端给服务器发数据叫请求(Request)
服务器(Tomcat)->客户端(浏览器): 服务器给客户端回传数据叫响应(Response)
```

#### Web资源的分类

```java
web 资源按实现的技术和呈现的效果的不同，又分为静态资源和动态资源两种。
静态资源： html、css、js、txt、mp4 视频 , jpg 图片 
动态资源： jsp 页面、Servlet 程序
```

#### 常用的Web服务器

```java
Tomcat：由 Apache 组织提供的一种 Web 服务器，提供对 jsp 和 Servlet 的支持。它是一种轻量级的 javaWeb 容器（服务 器），也是当前应用最广的 JavaWeb 服务器（免费）。
    
Jboss：是一个遵从 JavaEE 规范的、开放源代码的、纯 Java 的 EJB 服务器，它支持所有的 JavaEE 规范（免费）。
    
GlassFish： 由 Oracle 公司开发的一款 JavaWeb 服务器，是一款强健的商业服务器，达到产品级质量（应用很少）。
    
Resin：是 CAUCHO 公司的产品，是一个非常流行的服务器，对 servlet 和 JSP 提供了良好的支持， 性能也比较优良，resin 自身采用 JAVA 语言开发（收费，应用比较多）。 
    
WebLogic：是 Oracle 公司的产品，是目前应用最广泛的 Web 服务器，支持 JavaEE 规范， 而且不断的完善以适应新的开发要求，适合大型项目（收费，用的不多，适合大公司）。
```

### Tomacat

安装：找到你需要用的 Tomcat 版本对应的 zip 压缩包，解压到需要安装的目录即可。

#### 目录介绍

```java
bin 专门用来存放 Tomcat 服务器的可执行程序 
conf 专门用来存放 Tocmat 服务器的配置文件 
lib 专门用来存放 Tomcat 服务器的 jar 包 
logs 专门用来存放 Tomcat 服务器运行时输出的日记信息 
temp 专门用来存放 Tomcdat 运行时产生的临时数据 
webapps 专门用来存放部署的 Web 工程。 
work 是 Tomcat 工作时的目录，用来存放 Tomcat 运行时 jsp 翻译为 Servlet 的源码，和 Session 钝化的目录。
```

#### 启动与停止

```java
找到 Tomcat 目录下的 bin 目录下的 startup.bat 文件，双击，就可以启动 Tomcat 服务器。
测试
打开浏览器，在浏览器地址栏中输入以下地址测试： 
1、http://localhost:8080 
2、http://127.0.0.1:8080 
3、http://真实 ip:8080

1、点击 tomcat 服务器窗口的 x 关闭按钮 
2、把 Tomcat 服务器窗口置为当前窗口，然后按快捷键 Ctrl+C 
3、找到 Tomcat 的 bin 目录下的 shutdown.bat 双击，就可以停止 Tomcat 服务器
```

#### 部署web过程到Tomcat

##### 第一种：

```java
把 web 工程的目录拷贝到 Tomcat 的 webapps 目录下 即可。
在浏览器中输入访问地址格式如下： http://ip:port/工程名/目录下/文件名
```

##### 第二种：

```java
找到 Tomcat 下的 conf 目录\Catalina\localhost\ 下,创建如下的配置文件：如 abc.xml
配置文件内容：
    <!-- Context 表示一个工程上下文 path 表示工程的访问路径:/abc docBase 表示你的工程目录在哪里 --> <Context path="/abc" docBase="E:\book" />
访问这个工程的路径如下:http://ip:port/abc/ 就表示访问 E:\book 目录
```

##### **ROOT** 的工程的访问

```java
当我们在浏览器地址栏中输入访问地址如下： http://ip:port/ ====>>>> 没有工程名的时候，默认访问的是 ROOT 工程。 
当我们在浏览器地址栏中输入的访问地址如下： http://ip:port/工程名/ ====>>>> 没有资源名，默认访问 index.html 页面
```

### Servlet🔺

```java
//什么是 Servlet 
    1、Servlet 是 JavaEE 规范之一。规范就是接口 
    2、Servlet 就 JavaWeb 三大组件之一。三大组件分别是：Servlet 程序、Filter 过滤器、Listener 监听器。 
    3、Servlet 是运行在服务器上的一个 java 小程序，它可以接收客户端发送过来的请求，并响应数据给客户端。 
//手动实现 Servlet 程序 
    1、编写一个类去实现 Servlet 接口
    2、实现 service 方法，处理请求，并响应数据
    3、到web.xml 中去配置 servlet 程序的访问地址
	public class HelloServlet implements Servlet { //实现接口 }
```

```xml
<!--    servlet标签给Tomcat配置Servlet程序-->
    <servlet>
<!--        servlet-name标签 Servlet程序起一个别名(一般是类名)-->
        <servlet-name>HelloServlet</servlet-name>
<!--        servlet-class是Servlet程序的全类名-->
        <servlet-class>com.atguigu.servlet.HelloServlet</servlet-class>
    </servlet>
<!--        servlet-mapping标签给servlet程序配置访问地址-->
    <servlet-mapping>
<!--  servlet-name标签的作用是告诉服务器，我当前配置的地址给哪个Servlet程序使用-->
        <servlet-name>HelloServlet</servlet-name>
<!--        url-pattern标签配置访问地址
            / 斜杠在服务器解析的时候，表示地址为:http://ip:post/过程路径 <br/>
            /hello 表示地址为：   http://ip:post/过程路径/hello      <br/> -->
        <url-pattern>/hello</url-pattern>
    </servlet-mapping>
```

#### 常见错误

```java
常见的错误 1：url-pattern 中配置的路径没有以斜杠打头。
// Invalid <url-pattern> hello in servlet mapping
常见错误 2：servlet-name 配置的值不存在：    
// Servlet mapping specifies an unknown servlet name HelloServlet1
常见错误 3：servlet-class 标签的全类名配置错误：
// com.atguigu.servlt.HelloServlet    
```

#### **url** **地址到** **Servlet** 程序的访问

![url地址到Servlet程序的访问](E:\java\javaweb\笔记\images\url地址到Servlet程序的访问.png)

#### **Servlet** 的生命周期

```java
1、执行 Servlet 构造器方法 
2、执行 init 初始化方法 第一、二步，是在第一次访问，的时候创建 Servlet 程序会调用。 
3、执行 service 方法 第三步，每次访问都会调用。
4、执行 destroy 销毁方法 第四步，在 web 工程停止的时候调用。
```

#### **GET** **和** **POST** **请求的分发处理** 

```java
/*** service 方法是专门用来处理请求和响应的 */ 
@Override 
public void service(ServletRequest servletRequest, ServletResponse servletResponse) throws ServletException, IOException {
    System.out.println("3 service === Hello Servlet 被访问了"); 
 	// 类型转换（因为它有 getMethod()方法） 
	HttpServletRequest httpServletRequest = (HttpServletRequest) 	servletRequest; 
 	// 获取请求的方式 
	String method = httpServletRequest.getMethod(); 
	if ("GET".equals(method)) { 
    	doGet(); 
	} else if ("POST".equals(method)) { 
    	doPost(); 
	} 
}

/*** 做 get 请求的操作 */ 
public void doGet(){ 
    System.out.println("get 请求");
}
/*** 做 post 请求的操作 */ 
public void doPost(){ 
    System.out.println("post 请求"); 
}
```

#### 通过继承HttpServlet 实现Servlet程序

一般在实际项目开发中，都是使用继承 HttpServlet 类的方式去实现 Servlet 程序。 

1、编写一个类去继承 HttpServlet 类 

2、根据业务需要重写 doGet 或 doPost 方法 

3、到 web.xml 中的配置 Servlet 程序的访问地址

HelloServlet2.java

```java
public class HelloServlet2 extends HttpServlet {
    @Override 
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
        System.out.println("HelloServlet2 的 doGet 方法"); 
    }
	@Override 
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
        System.out.println("HelloServlet2 的 doPost 方法"); 
    } 
}    
```

web.xml

```xml
<servlet>
    <servlet-name>HelloServlet2</servlet-name> 
    <servlet-class>com.atguigu.servlet.HelloServlet2</servlet-class> </servlet>
<servlet-mapping>
    <servlet-name>HelloServlet2</servlet-name> 
    <url-pattern>/hello2</url-pattern>
</servlet-mapping>
```

#### Servlet类的继承体系

![Servlet类的继承体系](E:\java\javaweb\笔记\images\Servlet类的继承体系.png)

#### ServletConfig类🔺

```java
ServletConfig 类从类名上来看，就知道是 Servlet 程序的配置信息类。 
Servlet 程序和 ServletConfig 对象都是由 Tomcat 负责创建，我们负责使用。 
Servlet 程序默认是第一次访问的时候创建，ServletConfig 是每个 Servlet 程序创建时，就创建一个对应的 ServletConfig 对 象。
```

##### **ServletConfig** **类的三大作用** 

1、可以获取 Servlet 程序的别名 servlet-name 的值 

2、获取初始化参数 init-param 

3、获取 ServletContext 对象

web.xml:

```xml
    <servlet>
        <servlet-name>HelloServlet</servlet-name>
        <servlet-class>com.atguigu.servlet.HelloServlet</servlet-class>
        <init-param>
            <param-name>username</param-name>
            <param-value>root</param-value>
        </init-param>
        <init-param>
            <param-name>url</param-name>
            <param-value>jdbc:mysql://localhost:3306/test</param-value>
        </init-param>
    </servlet>
    <servlet-mapping>
        <servlet-name>HelloServlet</servlet-name>
        <url-pattern>/hello</url-pattern>
    </servlet-mapping>
```

Servlet代码

```java
@Override 
public void init(ServletConfig config) throws ServletException { 
    super.init(config) //注意：重写init方法里面一定要调用父类的init(ServletConfig)操作
    System.out.println("2 init 初始化方法"); 
	// 1、可以获取 Servlet 程序的别名 servlet-name 的值 
	System.out.println("HelloServlet 程序的别名是:" + 		config.getServletName());
	// 2、获取初始化参数 init-param 
	System.out.println("初始化参数 username 的值是;" + 	config.getInitParameter("username")); 
	System.out.println("初始化参数 url 的值是;" + config.getInitParameter("url")); 
	// 3、获取 ServletContext 对象 
	System.out.println(config.getServletContext()); 
}
```

#### ServletContext类🔺

```java
1、ServletContext 是一个接口，它表示 Servlet 上下文对象 
2、一个 web 工程，只有一个 ServletContext 对象实例。 
3、ServletContext 对象是一个域对象。 
4、ServletContext 是在 web 工程部署启动的时候创建。在 web 工程停止的时候销毁。 
什么是域对象? 
域对象，是可以像 Map 一样存取数据的对象，叫域对象。 这里的域指的是存取数据的操作范围，整个 web 工程。 
		存数据 		 取数据 			删除数据 
Map 	put() 			get() 			remove() 
域对象 setAttribute() 	getAttribute()  removeAttribute();
```

##### ServletContext类的四个作用

```java
1、获取 web.xml 中配置的上下文参数 context-param 
2、获取当前的工程路径，格式: /工程路径 
3、获取工程部署后在服务器硬盘上的绝对路径 
4、像 Map 一样存取数据
```

ServletContext.java

```java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //1.获取web.xml 中配置的上下文参数context-paaram
        ServletContext servletContext = getServletConfig().getServletContext();
        String username = servletContext.getInitParameter("username");
        System.out.println("context-param参数username的值是：" + username);
        System.out.println("context-param参数password的值是：" + servletContext.getInitParameter("password"));
        System.out.println("init-paraam参数url的值是：" + servletContext.getInitParameter("url"));
        //2.获取当前的过程路径，格式：/工程路径
        System.out.println("当前工程路径" + servletContext.getContextPath());
        //3.获取工程部署后在服务器硬盘上的绝对路径
        /**
         * / 斜杠被服务器解析地址为：http://ip:post/工程名/  映射到IDEA代码的web目录		  */
        System.out.println("过程部署的路径是："+servletContext.getRealPath("/"));
        System.out.println("工程下css目录的绝对路径是：："+servletContext.getRealPath("/css"));
        System.out.println("工程下imgs目录1/jpg的绝对路径是：："+servletContext.getRealPath("/imgs/1.jpg"));
    }
```

web.xml:

```xml
<context-param>
	<param-name>username</param-name>
    <param-value>context</param-value>
</context-param>
<context-param>
    <param-name>password</param-name>
	<param-value>root</param-value>
</context-param>
```

##### ServletContext 像 Map 一样存取数据： 

ContextServlet1.java:

```java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
    //获取ServletContext对象
	ServletContext servletContext = getServletContext();
    System.out.println(servletContext);
    System.out.println("保存之前：Context1 获取 key1的值是："+servletContext.getAttribute("key1"));
    servletContext.setAttribute("key1","value1");
    System.out.println("Context1 中获取域数据key1的值是："+servletContext.getAttribute("key1"));
}
```

ContextServlet2.java:

```java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
	ServletContext servletContext = getServletContext();
    System.out.println(servletContext);
    System.out.println("Context2 中获取域数据key1的值是：" + servletContext.getAttribute("key1"));
}
```

#### HTTP协议

```java
//什么是 HTTP 协议 
//什么是协议? 
    协议是指双方，或多方，相互约定好，大家都需要遵守的规则，叫协议。 
    所谓 HTTP 协议，就是指，客户端和服务器之间通信时，发送的数据，需要遵守的规则，叫 HTTP 协议。 HTTP 协议中的数据又叫报文。
//请求的 HTTP 协议格式
    客户端给服务器发送数据叫请求。 
    服务器给客户端回传数据叫响应。 
    请求又分为 GET 请求，和 POST 请求两种
```

##### GET请求

```java
1、请求行 
    (1) 请求的方式 GET 
    (2) 请求的资源路径[+?+请求参数] 
    (3) 请求的协议的版本号 HTTP/1.1 
2、请求头 
    key : value 组成 不同的键值对，表示不同的含义。
```

![Get请求](E:\java\javaweb\笔记\images\Get请求.png)

##### Post请求

```java
1、请求行
    (1) 请求的方式 POST 
    (2) 请求的资源路径[+?+请求参数] 
    (3) 请求的协议的版本号 HTTP/1.1 
2、请求头
    1) key : value 不同的请求头，有不同的含义 
        空行 
3、请求体 ===>>> 就是发送给服务器的数据
```

![Post请求](E:\java\javaweb\笔记\images\Post请求.png)

##### **常用请求头的说明** 

```java
Accept: 表示客户端可以接收的数据类型 
Accpet-Languege: 表示客户端可以接收的语言类型 
User-Agent: 表示客户端浏览器的信息 
Host： 表示请求时的服务器 ip 和端口号
```

##### 哪些是GET请求和POST请求

```java
GET 请求有哪些： 
    1、form 标签 method=get 
    2、a 标签 
    3、link 标签引入 css 
    4、Script 标签引入 js 文件 
    5、img 标签引入图片 
    6、iframe 引入 html 页面 
    7、在浏览器地址栏中输入地址后敲回车 
POST 请求有哪些： 
    8、form 标签 method=post
```

##### **响应的** **HTTP** **协议格式** 

```java
1、响应行
    (1) 响应的协议和版本号 
    (2) 响应状态码 
    (3) 响应状态描述符 
2、响应头 
    (1) key : value 不同的响应头，有其不同含义 
    空行 
3、响应体 ---->>> 就是回传给客户端的数据
```

![响应的HTTP协议格式](E:\java\javaweb\笔记\images\响应的HTTP协议格式.png)

##### **常用的响应码说明**

```java
200 表示请求成功 
302 表示请求重定向（明天讲） 
404 表示请求服务器已经收到了，但是你要的数据不存在（请求地址错误）
500 表示服务器已经收到请求，但是服务器内部错误（代码错误）
```

##### MIME类型说明

```java
MIME 是 HTTP 协议中数据类型。 
MIME 的英文全称是"Multipurpose Internet Mail Extensions" 多功能 Internet 邮件扩充服务。MIME 类型的格式是“大类型/小 类型”，并与某一种文件的扩展名相对应。
```

常见的 MIME 类型：

| 文件               | MIME类型                             |
| ------------------ | ------------------------------------ |
| 超文本标记语言文本 | .html , .htm     text/html           |
| 普通文本           | .txt   text/plain                    |
| RTF 文本           | .rtf   application/rtf               |
| GIF 图形           | .gif   image/gif                     |
| JPEG 图形          | jpeg,.jpg    image/jpeg              |
| au 声音文件        | .au    audio/basic                   |
| MIDI 音乐文件      | mid,.midi    audio/midi,audio/x-midi |
| RealAudio 音乐文件 | .ra, .ram   audio/x-pn-realaudio     |
| MPEG 文件          | .mpg,.mpeg    video/mpeg             |
| AVI 文件           | .avi     video/x-msvideo             |
| GZIP 文件          | .gz      application/x-gzip          |
| TAR 文件           | .tar     application/x-tar           |

#### HttpServletRequest类🔺

```java
//HttpServletRequest 类有什么作用：
每次只要有请求进入 Tomcat 服务器，Tomcat 服务器就会把请求过来的 HTTP 协议信息解析好封装到 Request 对象中。 然后传递到 service 方法（doGet 和 doPost）中给我们使用。我们可以通过 HttpServletRequest 对象，获取到所有请求的 信息。
```

##### **HttpServletRequest** 类的常用方法

| getRequestURI()          | 获取请求的资源路径                   |
| ------------------------ | ------------------------------------ |
| getRequestURL()          | 获取请求的统一资源定位符（绝对路径） |
| getRemoteHost()          | 获取客户端的 ip 地址                 |
| getHeader()              | 获取请求头                           |
| getParameter()           | 获取请求的参数                       |
| getParameterValues()     | 获取请求的参数（多个值的时候使用）   |
| getMethod()              | 获取请求的方式 GET 或 POST           |
| setAttribute(key, value) | 设置域数据                           |
| getAttribute(key)        | 获取域数据                           |
| getRequestDispatcher()   | 获取请求转发对象                     |

##### 获取请求参数

表单：

```xml
<body> 
    <form action="http://localhost:8080/07_servlet/parameterServlet" method="get">
        用户名：<input type="text" name="username"><br/>
        密码：<input type="password" name="password"><br/> 
        兴趣爱好：<input type="checkbox" name="hobby" value="cpp">C++ 
        <input type="checkbox" name="hobby" value="java">Java
        <input type="checkbox" name="hobby" value="js">JavaScript<br/>
        <input type="submit"> 
    </form> 
</body>
```

java代码

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //设置请求字体的字符编码，解决post请求的中文乱码
        req.setCharacterEncoding("UTF-8");
        //获取请求的参数
        String username = req.getParameter("username");
        String password = req.getParameter("password");
        String[] hobby = req.getParameterValues("hobby");

        System.out.println("用户名：" + username);
        System.out.println("密码：" + password);
        System.out.println("兴趣爱好：" + Arrays.asList(hobby));
    }
```

##### 请求的转发

```java
//什么是请求的转发? 
请求转发是指，服务器收到请求后，从一次资源跳转到另一个资源的操作叫请求转发。
```

![请求转发](E:\java\javaweb\笔记\images\请求转发.png)

Servlet代码：

```java
public class Servlet1 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("=======doGet=======");
        //获取请求的参数(办事的材料)查看
        String username = req.getParameter("username");
        System.out.println("在Servlet1(柜台1)中查看参数(材料)：" + username);
        //给材料 盖一个章，并传递到Servlet2(柜台2)去查看
        req.setAttribute("key","柜台1的章");
        //问路:Servlet2(柜台2) 怎么走
        /**
         * 请求转发必须要以斜杠打头，/ 斜杠表示地址为：http://ip:port/工程名/ ，映射到IDEA代码的web目录
         */
        RequestDispatcher requestDispatcher = req.getRequestDispatcher("/form.html");
        //走向 Servlet2 （柜台2）
        requestDispatcher.forward(req,resp);
    }
}
```

Servlet2代码

```java
public class Servlet2 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //获取请求的参数(办事的材料)查看
        String username = req.getParameter("username");
        System.out.println("在Servlet2(柜台2)中查看参数(材料)：" + username);
        //查看 是否有柜台1 的盖章
        Object key = req.getAttribute("key");
        System.out.println("柜台1是否有章：" + key);
        //处理自己的业务
        System.out.println("Servlet2 处理自己的业务");
    }
}
```

##### base标签的作用

```html
base标签可以设置当前页面中所有相对路径工作时，参照哪个路径来进行跳转
<!--base 标签设置页面相对路径工作时参照的地址 href 属性就是参数的地址值 -->
<base href="http://localhost:8080/07_servlet/a/b/">
```

##### web中 / 斜杠的不同意义

```java
在 web 中 / 斜杠 是一种绝对路径。 
/ 斜杠 如果被浏览器解析，得到的地址是：http://ip:port/ 
	<a href="/">斜杠</a> 
/ 斜杠 如果被服务器解析，得到的地址是：http://ip:port/工程路径 
	1、<url-pattern>/servlet1</url-pattern> 
    2、servletContext.getRealPath(“/”); 
	3、request.getRequestDispatcher(“/”); 
特殊情况： response.sendRediect(“/”); 把斜杠发送给浏览器解析。得到 http://ip:port/
```

#### HttpServletResponse类🔺

```java
//HttpServletResponse 类的作用
	HttpServletResponse 类和 HttpServletRequest 类一样。每次请求进来，Tomcat 服务器都会创建一个 Response 对象传 递给 Servlet 程序去使用。HttpServletRequest 表示请求过来的信息，HttpServletResponse 表示所有响应的信息， 
    我们如果需要设置返回给客户端的信息，都可以通过 HttpServletResponse 对象来进行设置
```

```java
//两个输出流的说明
字节流 getOutputStream(); 常用于下载（传递二进制数据） 
字符流 getWriter(); 常用于回传字符串（常用） 
两个流同时只能使用一个。 
使用了字节流，就不能再使用字符流，反之亦然，否则就会报错。
//同时使用报错： getOutputStream() has already been called for this response
```

##### **往客户端回传数据** 

```java
public class ResponseIOServlet extends HttpServlet { 
    @Override 
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
        // 要求 ： 往客户端回传 字符串 数据。 
        PrintWriter writer = resp.getWriter(); 
        writer.write("response's content!!!"); 
    } 
}
```

##### **响应的乱码解决** 

```java
//解决响应中文乱码方案一(不推荐使用):
	// 设置服务器字符集为 
	UTF-8 resp.setCharacterEncoding("UTF-8"); 
	// 通过响应头，设置浏览器也使用 UTF-8 字符集 
	resp.setHeader("Content-Type", "text/html; charset=UTF-8");
//解决响应中文乱码方案二(推荐)
	// 它会同时设置服务器和客户端都使用 UTF-8 字符集，还设置了响应头 
	// 此方法一定要在获取流对象之前调用才有效 
	resp.setContentType("text/html; charset=UTF-8");
```

##### 请求重定向

```java
	请求重定向，是指客户端给服务器发请求，然后服务器告诉客户端说。我给你一些地址。你去新地址访问。叫请求 重定向（因为之前的地址可能已经被废弃）。
```

![请求重定向](E:\java\javaweb\笔记\images\请求重定向.png)

```java
请求重定向的第一种方案： 
    // 设置响应状态码 302 ，表示重定向，（已搬迁） 
    resp.setStatus(302); 
	// 设置响应头，说明 新的地址在哪里 
	resp.setHeader("Location", "http://localhost:8080"); 

请求重定向的第二种方案（推荐使用）： 
    resp.sendRedirect("http://localhost:8080");
```

### JSP

```java
//什么是 jsp，它有什么用?
jsp 的全换是 java server pages。Java 的服务器页面。 
jsp 的主要作用是代替 Servlet 程序回传 html 页面的数据。 
因为 Servlet 程序回传 html 页面数据是一件非常繁锁的事情。开发成本和维护成本都极高。
```

#### Jsp如何访问

```java
jsp 页面和 html 页面一样，都是存放在 web 目录下。访问也跟访问 html 页面一样。
在 web 目录下有如下的文件： 
web 目录
    a.html 页面 访问地址是 =======>>>>>> http://ip:port/工程路径/a.html 
	b.jsp 页面 访问地址是 =======>>>>>> http://ip:port/工程路径/b.jsp
```

#### jsp的本质是什么

```java
//jsp 页面本质上是一个 Servlet 程序。 
当我们第一次访问 jsp 页面的时候。Tomcat 服务器会帮我们把 jsp 页面翻译成为一个 java 源文件。并且对它进行编译成 为.class 字节码程序。
打开java 源文件：
    跟踪原代码发现，HttpJspBase 类。它直接地继承了 HttpServlet 类。也就是说。jsp 翻译出来的 java 类，它间接了继 承了 HttpServlet 类。也就是说，翻译出来的是一个 Servlet 程序
//总结：通过翻译的 java 源代码我们就可以得到结果：jsp 就是 Servlet 程序。 
    大家也可以去观察翻译出来的 Servlet 程序的源代码，不难发现。其底层实现，也是通过输出流。把 html 页面数据回传 给客户端。
```

#### jsp的三种语法

##### **jsp** **头部的** **page** **指令** 

```jsp
jsp 的 page 指令可以修改 jsp 页面中一些重要的属性，或者行为。
<%@ page contentType="text/html;charset=UTF-8" language="java" %>    
i. language 属性 表示 jsp 翻译后是什么语言文件。暂时只支持 java。 
ii. contentType 属性 表示 jsp 返回的数据类型是什么。也是源码中 response.setContentType()参数值 
iii. pageEncoding 属性 表示当前 jsp 页面文件本身的字符集。 
iv. import 属性 跟 java 源代码中一样。用于导包，导类。 
======两个属性是给 out 输出流使用=======
v. autoFlush 属性 设置当 out 输出流缓冲区满了之后，是否自动刷新冲级区。默认值是 true。 vi. buffer 属性 设置 out 缓冲区的大小。默认是 8kb
vii. errorPage 属性 设置当 jsp 页面运行时出错，自动跳转去的错误页面路径。
viii. isErrorPage 属性 设置当前 jsp 页面是否是错误信息页面。默认是 false。如果是 true 可以 获取异常信息。 
ix. session 属性 设置访问当前 jsp 页面，是否会创建 HttpSession 对象。默认是 true。 x. extends 属性 设置 jsp 翻译出来的 java 类默认继承谁。
```

##### **jsp** **中的常用脚本** 

###### 1、声明脚本(极少使用)

```jsp
声明脚本的格式是： <%! 声明 java 代码 %> 
作用：可以给 jsp 翻译出来的 java 类定义属性和方法甚至是静态代码块。内部类等。
```

###### 2、表达式脚本(常用)

```jsp
表达式脚本的格式是：<%=表达式%> 
表达式脚本的作用是：的 jsp 页面上输出数据。 
表达式脚本的特点： 
	1、所有的表达式脚本都会被翻译到_jspService() 方法中 
	2、表达式脚本都会被翻译成为 out.print()输出到页面上 
	3、由于表达式脚本翻译的内容都在_jspService() 方法中,所以_jspService()方法中的对象都可以直接使用。 
	4、表达式脚本中的表达式不能以分号结束。
```

###### 3、代码脚本

```jsp
代码脚本的格式是： 
	<% java 语句 %> 
代码脚本的作用是：可以在 jsp 页面中，编写我们自己需要的功能（写的是 java 语句）。 
代码脚本的特点是： 
	1、代码脚本翻译之后都在_jspService 方法中 
	2、代码脚本由于翻译到_jspService()方法中，所以在_jspService()方法中的现有对象都可以直接使用。 
	3、还可以由多个代码脚本块组合完成一个完整的 java 语句。 
	4、代码脚本还可以和表达式脚本一起组合使用，在 jsp 页面上输出数据
```

#### jsp中的三种注释

```jsp
i. html 注释 
	<!-- 这是 html 注释 -->
	html 注释会被翻译到 java 源代码中。在_jspService 方法里，以 out.writer 输出到客户端。 
ii. java 注释 
	<% // 单行 java 注释 /* 多行 java 注释 */ %> 
	java 注释会被翻译到 java 源代码中。 
iii. jsp 注释 
	<%-- 这是 jsp 注释 --%> 
	jsp 注释可以注掉，jsp 页面中所有代码。
```

#### Jsp九大内置对象

```jsp
jsp 中的内置对象，是指 Tomcat 在翻译 jsp 页面成为 Servlet 源代码后，内部提供的九大对象，叫内置对象。
< request	请求对象>
< response	响应对象>
< pageContext	jsp的上下文对象>
< session	会话对象>
< application	ServletContext对象>
< config	ServletConfig对象>
< out	jsp输出流对象>
< page	指向当前jsp的对象>
< exception	异常对象>
```

#### jsp四大域对象

```jsp
四个域对象分别是： 
<	pageContext (PageContextImpl 类) 当前 jsp 页面范围内有效 
<	request (HttpServletRequest 类)、 一次请求内有效 
<	session (HttpSession 类)、 一个会话范围内有效（打开浏览器访问服务器，直到关闭浏览器） 
<	application (ServletContext 类) 整个 web 工程范围内都有效（只要 web 工程不停止，数据都在） 
域对象是可以像 Map 一样存取数据的对象。四个域对象功能一样。不同的是它们对数据的存取范围。 虽然四个域对象都可以存取数据。在使用上它们是有优先顺序的。 
四个域在使用的时候，优先顺序分别是，他们从小到大的范围的顺序。
	pageContext ====>>> request ====>>> session ====>>> application
```

scope.jsp页面

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
    <%
        pageContext.setAttribute("key","pageContent");
        request.setAttribute("key","request");
        session.setAttribute("key","session");
        application.setAttribute("key","application");
    %>
    pageContext域是否有值：<%=pageContext.getAttribute("key")%><br>
    request域是否有值：<%=request.getAttribute("key")%><br>
    session域是否有值：<%=session.getAttribute("key")%><br>
    application域是否有值：<%=application.getAttribute("key")%><br>
    <%
        request.getRequestDispatcher("/scope1.jsp").forward(request,response);
    %>
</body>
</html>
```

scope1.jsp

```jsp
<body>
    <h1>scope2.jsp页面</h1>
    pageContext域是否有值：<%=pageContext.getAttribute("key")%><br>
    request域是否有值：<%=request.getAttribute("key")%><br>
    session域是否有值：<%=session.getAttribute("key")%><br>
    application域是否有值：<%=application.getAttribute("key")%><br>
</body>
```

#### jsp中的out输出和response.getWriter输出的区别

```jsp
response 中表示响应，我们经常用于设置返回给客户端的内容（输出） 
out 也是给用户做输出使用的。
```

![Jsp中out输出和response输出](E:\java\javaweb\笔记\images\Jsp中out输出和response输出.png)

```java
由于 jsp 翻译之后，底层源代码都是使用 out 来进行输出，所以一般情况下。我们在 jsp 页面中统一使用 out 来进行输出。避免打乱页面输出内容的顺序。 
    out.write() 输出字符串没有问题 
    out.print() 输出任意数据都没有问题（都转换成为字符串后调用的 write 输出） 
//深入源码，浅出结论：在 jsp 页面中，可以统一使用 out.print()来进行输出
```

#### jsp常用标签

##### jsp静态包含

```jsp
<%--
    <%@ include file=""%> 就是静态包含 
		file 属性指定你要包含的 jsp 页面的路径 
		地址中第一个斜杠 / 表示为 http://ip:port/工程路径/ 映射到代码的 web 目录
静态包含的特点： 
	1、静态包含不会翻译被包含的 jsp 页面。 
	2、静态包含其实是把被包含的 jsp 页面的代码拷贝到包含的位置执行输出。
--%> 
<%@ include file="/include/footer.jsp"%>
```

##### jsp动态包含

```jsp
<%--
    <jsp:include page=""></jsp:include> 这是动态包含 
    page 属性是指定你要包含的 jsp 页面的路径 
    动态包含也可以像静态包含一样。把被包含的内容执行输出到包含位置 
    动态包含的特点： 
        1、动态包含会把包含的 jsp 页面也翻译成为 java 代码 
        2、动态包含底层代码使用如下代码去调用被包含的 jsp 页面执行输出。 JspRuntimeLibrary.include(request, response, "/include/footer.jsp", out, false); 
		3、动态包含，还可以传递参数 
--%> 
<jsp:include page="/include/footer.jsp">
    <jsp:param name="username" value="bbj"/> 
    <jsp:param name="password" value="root"/> 
</jsp:include>
```

##### jsp标签-转发

```jsp
<%--
    <jsp:forward page=""></jsp:forward> 是请求转发标签，它的功能就是请求转发 page 属性设置请求转发的路径 
--%> 
<jsp:forward page="/scope2.jsp"></jsp:forward>
```

#### **Listener** **监听器**

```java
ServletContextListener 它可以监听 ServletContext 对象的创建和销毁。 ServletContext 对象在 web 工程启动的时候创建，在 web 工程停止的时候销毁。 
    监听到创建和销毁之后都会分别调用 ServletContextListener 监听器的方法反馈。 
```

两个方法分别是：

```java
public interface ServletContextListener extends EventListener { 
    /*** 在 ServletContext 对象创建之后马上调用，做初始化 */ 
    public void contextInitialized(ServletContextEvent sce); 
    /*** 在 ServletContext 对象销毁之后调用 */ 
    public void contextDestroyed(ServletContextEvent sce); }
```

使用 ServletContextListener 监听器监听 ServletContext 对象。 

```java
使用步骤如下： 
1、编写一个类去实现 ServletContextListener 
2、实现其两个回调方法 
3、到 web.xml 中去配置监听器
```

监听实现类：

```java
public class MyServletContextListenerImpl implements ServletContextListener { 
    @Override 
    public void contextInitialized(ServletContextEvent sce) { 
        System.out.println("ServletContext 对象被创建了"); 
    }
    @Override
    public void contextDestroyed(ServletContextEvent sce) { 
        System.out.println("ServletContext 对象被销毁了"); 
    } 
}
```

web.xml配置：

```xml
<!--配置监听器-->
<listener> 
    <listener-class>com.atguigu.listener.MyServletContextListenerImpl</listener-class></listener>
```

### EL表达式

```java
//什么是 EL 表达式，EL 表达式的作用?
EL 表达式的全称是：Expression Language。是表达式语言。 
EL 表达式的什么作用：EL 表达式主要是代替 jsp 页面中的表达式脚本在 jsp 页面中进行数据的输出。 
因为 EL 表达式在输出数据的时候，要比 jsp 的表达式脚本要简洁很多。
```

```jsp
<body> 
    <% 
    	request.setAttribute("key","值"); 
    %>
    表达式脚本输出 key 的值是： 	<%=request.getAttribute("key1")==null?"":request.getAttribute("key1")%><br/> EL 表达式输出 key 的值是：${key1} 
</body>
EL 表达式的格式是：${表达式} 
EL 表达式在输出 null 值的时候，输出的是空串。jsp 表达式脚本输出 null 值的时候，输出的是 null
```

#### **EL** **表达式搜索域数据的顺序**

```java
EL 表达式主要是在 jsp 页面中输出数据。 
主要是输出域对象中的数据。 
当四个域中都有相同的 key 的数据的时候，EL 表达式会按照四个域的从小到大的顺序去进行搜索，找到就输出。
```

```jsp
<body> 
    <% 
    //往四个域中都保存了相同的 key 的数据。 request.setAttribute("key", "request");
session.setAttribute("key", "session"); application.setAttribute("key", "application"); pageContext.setAttribute("key", "pageContext");
    %>${ key } 
</body>
```

**EL** **表达式输出** **Bean** **的普通属性，数组属性。****List** **集** 

**合属性，****map** **集合属性** 

```jsp
<body>
    <%
        Person person = new Person();
        person.setName("男孩女孩");
        person.setPhones(new String[]{"123141","11414","124141"});
        List<String> cities = new ArrayList<String>();
        cities.add("北京");
        cities.add("上海");
        cities.add("深圳");
        person.setCities(cities);
        Map<String,Object> map = new HashMap<>();
        map.put("key1","value1");
        map.put("key2","value2");
        map.put("key3","value3");
        person.setMap(map);
        pageContext.setAttribute("p",person);
    %>
    输出Person: ${ p }<br/>
    输出Person的name属性: ${ p.name }<br/>
    输出Person的phones数组属性值: ${ p.phones[1] }<br/>
    输出Person的cities集合中的元素值: ${ p.cities }<br/>
    输出Person的List集合中个别元素值: ${ p.cities[1] }<br/>
    输出Person的Map集合: ${ p.map }<br/>
    输出Person的Map集合中某个key的值: ${ p.map.key3 }<br/>
    输出Person的age属组: ${ p.age }<br/>
</body>
```

#### **EL** **表达式——运算**

```java
语法：${ 运算表达式 } ， EL 表达式支持如下运算符：
//关系运算符，逻辑运算符，算数运算符
//empty运算：
	empty 运算可以判断一个数据是否为空，如果为空，则输出 true,不为空输出 false。 
	以下几种情况为空： 
		1、值为 null 值的时候，为空 
		2、值为空串的时候，为空 
		3、值是 Object 类型数组，长度为零的时候 
		4、list 集合，元素个数为零 5、map 集合，元素个数为零
//三元运算 
   	表达式 1？表达式 2：表达式 3 
   	如果表达式 1 的值为真，返回表达式 2 的值，如果表达式 1 的值为假，返回表达式 3 的值。 
    ${ 12 != 12 ? "国哥帅呆":"国哥又骗人啦" }
//“.”点运算 和 [] 中括号运算符 
    .点运算，可以输出 Bean 对象中某个属性的值。 
    []中括号运算，可以输出有序集合中某个元素的值。 
    并且[]中括号运算，还可以输出 map 集合中 key 里含有特殊字符的 key 的值。
```

#### **EL** **表达式的** **11** **个隐含对象** 

```java
//EL 获取四个特定域中的属性
pageScope ====== pageContext 域 
requestScope ====== Request 域 
sessionScope ====== Session 域 
applicationScope ====== ServletContext 域
```

```java
//pageContext 对象的使用
1.协议： ${ req.scheme }<br> 
2.服务器 ip：${ pageContext.request.serverName }<br> 
3.服务器端口：${ pageContext.request.serverPort }<br> 
4.获取工程路径：${ pageContext.request.contextPath }<br> 
5.获取请求方法：${ pageContext.request.method }<br> 
6.获取客户端 ip 地址：${ pageContext.request.remoteHost }<br> 
7.获取会话的 id 编号：${ pageContext.session.id }<br>
```

```java
//EL 表达式其他隐含对象的使用
param Map<String,String> 它可以获取请求参数的值 paramValues Map<String,String[]> 它也可以获取请求参数的值，获取多个值的时候使用。
请求地址： 
http://localhost:8080/09_EL_JSTL/other_el_obj.jsp?username=wzg168&password=666666&hobby=java&hobby=cpp
```

```java
header Map<String,String> 它可以获取请求头的信息 headerValues Map<String,String[]> 它可以获取请求头的信息，它可以获取多个值的情况
输出请求头【User-Agent】的值：${ header['User-Agent'] } <br> 
输出请求头【Connection】的值：${ header.Connection } <br> 
输出请求头【User-Agent】的值：${ headerValues['User-Agent'][0] } <br>
```

```java
cookie Map<String,Cookie> 它可以获取当前请求的 Cookie 信息
获取 Cookie 的名称：${ cookie.JSESSIONID.name } <br> 
获取 Cookie 的值：${ cookie.JSESSIONID.value } <br>    
```

```xml
initParam Map<String,String> 它可以获取在 web.xml 中配置的<context-param>上下文参数
<context-param> 
    <param-name>username</param-name> 
    <param-value>root</param-value> 
    </context-param> 
<context-param> 
    <param-name>url</param-name> 
    <param-value>jdbc:mysql:///test</param-value> 
</context-param>    
    
输出&lt;Context-param&gt;username 的值：${ initParam.username } <br> 
输出&lt;Context-param&gt;url 的值：${ initParam.url } <br>    
```


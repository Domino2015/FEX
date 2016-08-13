

> 本任务完成的功能为：用户可以在输入框中输入任何内容，点击“确认填写”按钮后，用户输入的内容会显示在“您输入的值是”文字的右边

## 函数封装

```javascript
var $ =function (id) {
  return document.getElementById(id);
}
```

## isNaN()函数

如果把 NaN 与任何值（包括其自身）相比得到的结果均是 false，所以要判断某个值是否是 NaN，不能使用 == 或 === 运算符。   

 x 是特殊的非数字值 NaN（或者能被转换为这样的值），返回的值就是 true。如果 x 是其他值,则返回 false。

## parseInt()函数

parseInt()函数将给定的字符串以指定基数（radix/base）解析成为整数.

> parseInt(string,radix)；

string
  要被解析的值，如果参数不是一个字符串，则试图把他转换为一个字符串。字符串开头的空白符将会被忽略。
radix
  一个2到36之间的整数值，用于指定转换中采用的基数。 *总是指定该参数*提高代码可读性。

#### 描述

  `parseInt`函数将第一个参数（字符串）解析并试图返回一个整数或者NaN（Not a Number）。如果结果不是NaN，那么返回值是把第一个参数看作是radix参数指定的进制下的数，然后把它转换成十进制的整数。  

  如果 parseInt 遇到了不属于radix参数所指定的基数中的字符那么该字符和其后的字符都将被忽略。接着返回已经解析的整数部分。parseInt 将截取整数部分。开头和结尾的空白符允许存在，会被忽略。   

  如果第一个字符不能被转换成数字，parseInt返回NaN。   

  算术上， NaN 不是任何一个进制下的数。 你可以调用 `isNaN` 来判断 parseInt 是否返回 `NaN`。NaN 参与的数学运算其结果总是 NaN。  

  将整型数值以特定基数转换成它的字符串值可以使用 `intValue.toString(radix)`.

#### 更加严格的解析函数

```javascript
  filterInt = function (value) {
   if(/^(\-|\+)?([0-9]+|Infinity)$/.test(value))
    return Number(value);
  return NaN;
  }
```
## 同理 parseFloat()函数

parseFloat()方法将参数中指定的字符串解析成为一个*浮点数字*并返回.

> parseFloat(string);

#### 描述

parseFloat将它的字符串参数解析成为浮点数并返回.如果在解析过程中遇到了正负号(+或-),数字(0-9),小数点,或者科学记数法中的指数(e或E)以外的字符,则它会忽略该字符以及之后的所有字符,返回当前已经解析到的浮点数.同时参数字符串首位的空白符会被忽略.

#### 更加严格的解析函数

```javascript
 var filterFloat = function (value) {
    if(/^(\-|\+)?([0-9]+(\.[0-9]+)?|Infinity)$/
      .test(value))
      return Number(value);
  return NaN;
}
```


## onkeyup 属性

onketyup 属性 在当前元素上释放键盘按键时会触发keyup事件

```javascrpt
$("api-input").onkeyup =function (event){
  if(event.keyCode === 13){
    handler();
  }
}
```
## event.keyCode

得到键盘按下键的unicode值
代码如上面显示的。注意**===**

## Even对象

事件是一种一步编程的实现方式，本质上是和程序的各个部分之间的通讯。DOM支持大量的事件。

### EventTarget接口

Dom的事件操作（监听和触发）,都定义在`EventTarget`接口。Eement节点，document节点和window对象，都部署在这个接口。XMLHttpRequest，AudioNode,Audiocontext等浏览器内置对象，都在这个接口上。   
该接口有三种方法
1. addEventListener 用于绑定监听函数
2. removeEventListener 移除监听函数
3. dispatchEvent 用于触发事件

#### addEventListener()

addEventListener 方法   在当前节点或者对象上，定义一个特定事件的监听函数
```javascript
  target.addEventListener(type,listener,useCapture);

  window.addEventListener('load',function(){...},false);
```
addEventListener方法接受三个参数.
1. type:事件名称.
2. listener：监听函数，表示发生时，会调用该监听函数。
3. useCapture：布尔值。表示监听函数是否在捕获阶段（capture）触发。默认为false（监听函数只在冒泡阶段被触发）。为保持兼容性，建议总是写上该参数。

```javascript
  var $ = function (id){
    return document.getElementById('id');
  }
  function hello(){
  console.log("hello world");
  }
  $('btn').addEventListener('click',hello,false);
```

监听函数`hello`只在冒泡阶段触发   
addEventListener方法可以为当前对象的同一个事件，添加多个监听函数，按添加顺序执行。同一事件多次添加到同一个监听函数，该函数只会执行一次。

如果希望向监听函数传递参数，可以用匿名函数包装一下监听函数。
```javacript
  function print(x){
    console.log(x);
  }
  var el = document.getElementById('div1');
  el.addEventListener('click',function(){print('hello');},false);
```

#### removeEventListener()

```javascript
  div.addEventListener('click',listener,false);
  div.removeEventListener('click',listener,false);
```

移除`addEventListener`方法添加的事件监听函数
removeEventListener方法必须与对应的`addEventListener`方法的参数一致,而且必须在同一元素节点.

#### dispatchEvent()

在当前节点上触发指定事件,从而触发监听函数的执行。该方法返回一个布尔值，只要有监听函数调用了`Event.preventDefault`,则返回值为false，否则为true。

```javascript
<script type="text/javascript">
var $ = function (id) {
    return document.getElementById(id);
}

function hello(){
  console.log("hello word!");
}

$('p').addEventListener('click', hello,false);
var event = new Event('click');
$('p').dispatchEvent(event); 
</script>

```
### 监听函数
监听函数（listener）是事件发生时，程序所要执行的函数。他是事件驱动编程模式的主要编程方式。

DOM提供三种方法，可以用来为事件绑定监听函数。
#### HTML标签的`on-`属性
HTML允许在标签中，直接定义某些事件的监听代码。

```javascript
  <body onload="doSomething()"></body>
  <div onclick="console.log('触发一些事件')"></div>
```
这个方法指定的监听函数，只会在冒泡阶段触发。
**on-属性的值是将会执行的代码（on-属性的值是原样传入javascript引擎执行），而不是‘监听’函数**，因此执行函数需要加上一对括号。    
Element节点的setAttribute方法，其实设置的也是这种效果。   
`el.setAttribute('onclick','doSomething()');`   

违反了HTML与JavaScript代码相分离的原则.

#### Element节点的事件属性

```
<script type="text/javascript">
  window.onload = doSomething;
  div.onclick = function(event){
    console.log('触发事件');
  };
</script>
```

监听函数，只会在冒泡阶段触发。  

同一个事件只能定义一个监听函数，也就是说，如果定义两次onclick属性，后一次定义会覆盖前一次。

#### addEventLIstener()
'window.addEventListener('load',doSomething,false);'

1. 同一个事件，添加多个监听函数。

2. 能指定阶段（捕获阶段还是冒泡阶段）触发回监听函数。

3. 除了DOM节点，还可以部署在window、XMLHttpRequest等对象上面，等于统一了整个JavaScript的监听函数接口。
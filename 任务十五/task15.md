> 接触一下JavaScript中的高级选择器
学习JavaScript中的数组对象遍历、读写、排序等操作
学习简单的字符串处理操作

## js获取许多`<li>`标签中的内容并将其存为数组

```HTML
 <ul id="source">
    <li>1313</li>
    <li>31231</li>
    <li>312</li>
    <li>312</li>
    <li>31232</li>
</ul>
<script>
    (function(){
        var text = document.getElementsByTagName('li');
        var temp=[];
        var textlen=text.length;
        console.log(text);
        for(var i=0;i<textlen;i++){
            temp.push(text[i].innerHTML);
        }
        console.log(temp);
    })();
</script>
```

text得到的只是`li`标签的集合并不是内容的集合。


## push()方法

可向数组的末尾添加多个元素，并返回新的数组长度

> arrayObject.push(newelement1,newelement2,....,newelementX)

参数       |     描述
          -|-
newelement1|必需。要添加到数组的第一个元素。
newelement2|可选。要添加到数组的第二个元素。

要想数组的`开头`添加一个或多个元素，请使用 unshift() 方法


## split()

split()方法用于把**一个字符串分割成字符串数组**

> stringObject.split(separator,howmany)

参数       |     描述
          -|-
separator  |必需。字符串或正则表达式，从该参数指定的地方分割 stringObject。
howmany    |可选。该参数可指定返回的数组的最大长度。如果设置了该参数，返回的子串不会多于这个参数指定的数组。如果没有设置该参数，整个字符串都会被分割，不考虑它的长度。

#### 返回值

一个字符串数组，该数组是通过在 separator 指定的边界处将字符串 stringObject 分割成子串创建的。返回的数组中的字串不包括 separator 自身。

#### 如果把空字符串 ("") 用作 separator，那么 stringObject 中的每个字符之间都会被分割。

```HTML
<ul id="source">
        <li>北京空气质量：<b>90</b></li>
        <li>上海空气质量：<b>70</b></li>
        <li>天津空气质量：<b>80</b></li>
        <li>广州空气质量：<b>50</b></li>
        <li>深圳空气质量：<b>40</b></li>
        <li>福州空气质量：<b>32</b></li>
        <li>成都空气质量：<b>90</b></li>
</ul>
<script type="text/javascript">
         (function (){
        var ul = document.getElementById('source');
        var value =[];
        for(var i = 0;i < ul.childElementCount;i++){
          var li = ul.children[i];
          var strCity = li.innerHTML.split('空气质量：'.1);
          /*
          因为是返回的数组split（)把字符串分割成了有两项的数组，如果自是取城市的名字就索引第一项，如果想要数字索引第二项.
          或者写成 var strCity = li.innerHTML.split('空气质量：')[0]
           */
          value.push(strCity);
        }
        document.write(value);
      })()
</script>
```

## ParentNode.childElementCount属性(面临淘汰)

**其作用基本可以被element.children.length所取代,所以在未来版本的Gecko中,该属性可能会被删除**

返回当前元素的`子元素个数`， 只有当一个节点的nodeType属性为1(Node.ELEMENT_NODE==1)时,它才是元素节点 .文本节点和注释节点不属于元素节点.

> var elCount =elementNODE.childElenmentCount;

```HTML
<ul id="source">
    <li>assd</li>
    <li>asdd</li>
    <li>assd</li>
    <li>adsda</li>
    <li>dasasd</li>
</ul>
<script type="text/javascript">
    var ul = document.getElementById('source');
    for(var i =0;i<ul.childElementCount;i++){
        //.....
    }
    /*
    或者写成 for(var i = 0;i<ul.getElementByTagName('li').length;i++){

    }
     */
</script>
```

## join()方法

用于把数组中的所有元素放入一个字符串。元素是通过指定的分割符进行分割的。

> arrayObject.join('separator')

参数 | 描述
---- | ----
separator | 可选。指定要使用的分隔符。如果省略该参数，则使用逗号作为分隔符。

#### 返回值
返回一个字符串该字符串是通过把 arrayObject 的每个元素转换为字符串，然后把这些字符串连接起来，在两个元素之间插入 separator 字符串而生成的。

```
<script>
var arr = new Array();
      arr[1]='hahah';
      arr[2]='xixixi';
      arr[3]='heheh';
      document.write(arr.join('-'));
</script>
```

## document.getElementById('id').children[i]

可以返回组成子节点的数组

```HTML
<ul id="source">
    <li>assd</li>
    <li>asdd</li>
    <li>assd</li>
    <li>adsda</li>
    <li>dasasd</li>
</ul>
<script type="text/javascript">
    var ul = document.getElementById('source');
    var li=ul.children[i]
</script>
```

## Number()

Number()函数把对象转化为数字

> NUmber(Object)

#### 返回值

如果对象是Date对象，Number（）返回从 1970 年 1 月 1 日至今的毫秒数。
如果对象的值无法转换为数字，那么 Number() 函数返回 `NaN`。










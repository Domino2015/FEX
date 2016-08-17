> 页面加载后，将提供的空气质量数据数组，按照某种逻辑（比如空气质量大于60）进行过滤筛选，最后将符合条件的数据按照一定的格式要求显示在网页上

## sort

语法
> arr.sort([compareFunction])    

compareFunction   
可选，用来指定按照某种顺序进行排列的函数。

#### 描述
如果没有指明 compareFunction ，那么元素会被转换为字符串并按照万国码位点顺序排序。例如 "Cherry" 会被排列到 "banana" 之前。当对数字进行排序的时候， 9 会出现在 80 之前，因为他们会先被转换为字符串，而 "80" 比 "9" 要靠前。

按照数值的大小对数字进行排序，要实现这一点，就必须使用一个排序函数：
```

arr.sort(sortNumber);
//从大到小
function sortNumber(a,b){
  return a-b;
}
//从小到大
function sortNumber(a,b){
  return b-a;
}
```

#### 使用映射改善排序

compareFunction可能需要对元素做多次映射以实现排序，尤其是当compareFunction较为复杂，且元素较多的时候，某些comparefunction可能会导致很高的负载。使用 map 辅助排序。基本思想是首先将数组中的每个元素比较的实际值取出来，排序后再将数组恢

```javascript

//需要被排序的数组
var list =['heheh','alpha','wjdws','hjanc'];

//对需要排序的数字和位置的临时储存
var mapped = list.map(function(el,i)){
  return {index:i,value:el.toLowerCase() };
}

// 按照多个值排序数组
mapped.sort(function(a, b) {
  return +(a.value > b.value) || +(a.value === b.value) - 1;
});

// 根据索引得到排序的结果
var result = mapped.map(function(el){
  return list[el.index];
});

```

## appendChild()方法

向节点`添加最后一个子节点`。
如果需要创建包含文本的新段落，请记得添加到文本节点，然后向文档添加该段落。

```javascript
<ul id="myList">
  <li>coffee</li>
  <li>tea</li>
</ul>
<button id="btn">点击我</button>

<script type="text/javascript">
//第一种
function myFunction(){
  var node = document.createElement('li');
  var textnode = document.createTextNode('water');
  node.appendChild(textnode);
  document.getElementById("myList").appendChild(node);
}
document.getElementById('btn').addEventListener('click',myFunction,false);
//第二种
function myFunction(){
  var node = document.createElement('li');
  var textnode = document.createTextNode('water');
  node.appendChild(textnode);
  document.getElementById("myList").appendChild(node);
}
document.getElementById('btn').addEventListener('click',myFunction,false);
</script>

```    

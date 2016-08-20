---
title: 前端笔记四
date: 2016年8月20日09:45:07
categories: [WEB]
tags: [WEB]
---

## trim（）

trim() 方法会删除一个字符串两端的空白字符。在这个字符串里的空格包括所有的空格字符 (space, tab, no-break space 等)以及所有的行结束符（如 LF，CR）

> trim() 方法并不影响原字符串本身，它返回的是一个新的字符串。

## target 事件属性

target 事件属性可返回事件的目标节点（触发该事件的节点），如生成事件的元素、文档或窗口。

> event.target

```HTML
<script type="text/javascript">
        function getEvent(event){
            x= event.target;
            alert(x.id);
        }
</script>

<p id="p1" onmousedown="getEvent(event)">haha</p>

```

## element.dataset.camelCasedName

自定义的数据属性

> string = element.dataset.camelCasedName;
element.dataset.camelCasedName = string;

```HTML
<div id="day2-meal-expense"
  data-drink="coffee"
  data-food="sushi"
  data-meal="lunch">¥20.12
  </div>
<script type="text/javascript">
var expenseday2 = document.getElementById('day2-meal-expense');
var typeOfDrink = expenseday2.dataset.drink;
</script>
```

如果你想删掉一个data属性，可以这么做：

`delete expenseday2.dataset.meal;`
如果你想给元素添加一个属性，可以这么做：

`expenseday2.dataset.dessert = 'icecream';`

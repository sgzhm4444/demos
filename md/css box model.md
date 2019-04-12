## CSS basic box model

**如何显示HTML中各div的box model** 
```
$$('*').forEach(e => {
	e.style.border='1px solid';
})
```

**每个盒子都由4部分组成：** 
* content
* padding
* margin
* border

**盒子模型分为三种：**
* content box:
```
	width = width;
	height = height;
``` 
* border box:
```
	width=width+border+padding;
	height=height+border+padding
```
* padding box: 已废弃

**定位规则**
* 普通文档流中，盒子会依次放置
* 在block formatting context中，盒子在垂直方向依次排列
* 在inline formatting context中，盒子在水平方向依次排列
* 浮动：当一个盒子的float不为none，且position为relative或static时，该盒子为浮动定位
* float: left, float: right会将盒子定位到当前行盒子的左侧或右侧
* 绝对定位：若盒子的position为absolute或fixed，该盒子为绝对定位，会从当前的文档流中移除
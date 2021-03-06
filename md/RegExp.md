#### RegExp

1. 定义方法
```
var reg = new RegExp("a");
var reg = /a/;
```

2. 常用变量含义

| var | 含义 |
| ------ | ------ |
| \s | 空格 |
| \S | 非空格 |
| \d | 数字 |
| \D | 非数字 |
| \w | 字符 ( 字母 ，数字，下划线_ ) |
| \W | 非字符例子：是否有不是数字的字符 |
| i | 忽略大小写 |
| g | 全局 |
| () | 分组符 |
| [] | []中内容的任意一个 |
| ^ | 在[]中是“非”的意思，在正则表达式开始处代表“起始”的意思 |
| $ | 在正则表达式的最后位置 ,代表结束的意思 |
| . | 任意字符 |
| \\. | 真正的. |
| \b | 独立的部分 （ 起始，结束，空格 ） |
| \B | 非独立的部分 |
| \n | 重复的第n个子项，如“\1 重复的第一个子项” |
| {n,m} | 量词，至少出现n次，最多m次 |
| {n,} | 量词，至少n次 |
| * | 量词，任意次 相当于{0,} |
| ？ | 量词，零次或一次 相当于{0,1} |
| + | 量词，一次或任意次相当于 {1,} |
| {n} | 量词，正好n次 |


3. 常用api

| API | 作用 | 用法 |
| ------ | ------ |
| test() | 在字符串中查找符合正则的内容，若查找到返回true,反之返回false | 正则.test(字符串) |
| search() | 在字符串搜索符合正则的内容，搜索到就返回出现的位置（从0开始，如果匹配的不只是一个字母，那只会返回第一个字母的位置）， 如果搜索失败就返回 -1  | 字符串.search(正则) |
| match() | 在字符串中搜索复合规则的内容，搜索成功就返回内容，格式为数组，失败就返回null | 字符串.match(正则) |
| replace() | 查找符合正则的字符串，就替换成对应的字符串。返回替换后的内容 | 字符串.replace(正则,新的字符串/回调函数) |

4. 贪婪匹配与非贪婪匹配

* 在RegExp后边加上?，可由贪婪匹配转为非贪婪匹配
	
```
var str = "...abc...123...abc...123...";
var reg1 = /abc(.*)123/g;
var reg2 = /abc(.*?)123/g;
str.match(reg1);	//"abc...123...abc...123"
str.match(reg2);	//["abc...123", "abc...123"]
```

5. 捕获型匹配与非捕获型匹配

正常用()型捕获会暂存捕获的结果，例子如下：

```
var reg = /(\d{4})-(\d{2})-(\d{2})/;
var str = "2019-09-18";
reg.test(str);	//RegExp.$1=2019, RegExp.$2 = 09, RegExp.$3 = 18
```

有时，我们不需要捕获结果，则可以用(?:)，例子如下：

```
var reg = /(?:\d{4})-(\d{2})-(\d{2})/;
var str = "2019-09-18";
reg.test(str);	//RegExp.$1 = 09, RegExp.$2 = 18
```

6. 前瞻型匹配

前瞻型匹配分为正向前瞻型(?=)和反向前瞻型(?!)，两个都为非捕获型，例子如下：

```
var regP = /this is (?=positive)/;
var regN = /this is (?!positive)/;
var str = "this is positive";
regP.test(str);		//true
regN.test(str);		//false
```

7. 例子

(1) 找到重复项最多的字符个数
```
var str = 'assssjdssskssalsssdkjsssdss';

var arr = str.split(''); //把字符串转换为数组
str = arr.sort().join(''); //首先进行排序，这样结果会把相同的字符放在一起，然后再转换为字符串

var value = '';
var index = 0; 
var reg = /(\w)\1+/g;   //匹配字符，且重复这个字符，重复次数至少一次。
str.replace(reg,function($0,$1){ 
    console.log($0);   //代表每次匹配成功的结果 : aa dd jj kk l sssssssssssssssss
    console.log($1);   //代表每次匹配成功的第一个子项，也就是\w:  a d j k l S 
　　
    if(index<$0.length){  //如果index保存的值小于$0的长度就进行下面的操作
        index = $0.length;  // 这样index一直保存的就在最大的长度
        value = $1;  //value保存的是出现最多的这个字符
    }

}); 
```

(2) 判断是不是QQ号
```
//首先QQ号的规则，首位不能是0，必须是 5-12位的数字
   
var qqStr = '45648798';
var reg = /^[1-9]\d{4,11}$/;

//123456abc为了防止出现这样的情况，所以必须限制最后
//首位是1-9，接着是4-11位的数字类型。

if(reg.test(qqStr)){
	console.log('是QQ号');
}else{
	console.log('不是QQ号');
}

```

(3) 去掉字符串前后的空格
```
var str = '  hello  ';
function trim(str){
   var reg = /^\s+|\s+$/g;   // |代表或者   \s代表空格  +至少一个    前面有至少一个空格 或者后面有至少一个空格 且全局匹配
   return str.replace(reg,'');   //把空格替换成空
} 
```

(4) 常用的一些表单校验
```
匹配中文：/[\u4e00-\u9fa5]/   //中文ACALL码的范围
Email：/^\w+@[a-z0-9]+(\.[a-z]+){1,3}$/   //起始至少为一个字符(\w字母，数字或者下划线)，然后匹配@,接着为任意个字母或者数字，\.代表真正的点，.后面为至少一个的字符（a-z）,同时这个(比如.com)整体为一个子项作为结束，可以出现1-3次。因为有的邮箱是这样的.cn.net。（xxxx.@qq.com xxxx.@163.com xxxx.@16.cn.net ）
网址：/[a-zA-z]+://[^\s]*/   // http://......，匹配不分大小写的任意字母，接着是//,后面是非空格的任意字符
邮政编码：/\d{6}/   //起始数字不能为0，然后是5个数字
身份证：/[1-9]\d{14}|[1-9]\d{17}|[1-9]\d{16}x/

```
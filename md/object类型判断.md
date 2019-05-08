#### Object类型判断

我们知道在判断类型的时候可以通过 Object.prototype.toString.call 来获取对应对象返回的字符串，比如：
```
let isString = obj => Object.prototype.toString.call( obj ) === '[object String]';

let isArray = obj => Object.prototype.toString.call( obj ) === '[object Array]';

let isNumber = obj => Object.prototype.toString.call( obj ) === '[object Number]';
```

抽象成判断类型的方法：

```
let isType = type => obj => {
  return Object.prototype.toString.call( obj ) === '[object ' + type + ']';
}

isType('String')('123');        // true
isType('Array')([1, 2, 3]);    // true
isType('Number')(123);            // true
```
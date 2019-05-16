### 函数curry化

curry化是把接受多个参数的函数变换成接受一个单一参数（最初函数的第一个参数）的函数，并且返回接受余下的参数而且返回结果的新函数的技术。

* 单参数n元curry实现（一次传一个参数）

```
function currying(fn, ...args) {
    if (args.length >= fn.length) {
        return fn(...args)
    }
    return function (...args2) {
        return currying(fn, ...args, ...args2)
    }
}
var add = function (arg1, arg2){
	return arg1 + arg2;
}
var sum = currying(add)(4);
sum(1);
```

* 多参数curry实现（一次传若干个参数）

```
function currying(fn, ...args) {
    return (..._arg2) => {
        return fn(...args, ..._arg2);
    }
}
var add = function (arg1, arg2){
	return arg1 + arg2;
}
var sum = currying(add,4,5);
sum(6);
```
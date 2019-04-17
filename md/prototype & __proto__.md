### 首先，Object.prototype和Function.prototype的关系

```
Object.prototype.__proto__ === null                   // true

Function.prototype.__proto__ === Object.prototype     // true
```

### 然后，Object和Function都是可以作为构造函数的，但是二者还是有区别

* 使用对象字面量创建的对象，其 [[Prototype]] 值是 Object.prototype。
* 使用数组字面量创建的对象，其 [[Prototype]] 值是 Array.prototype。
* 使用 function f(){} 函数创建的对象，其 [[Prototype]] 值是 Function.prototype。
* 使用 new fun() 创建的对象，其中 fun 是由 JavaScript 提供的内建构造器函数之一(Object, Function, Array, Boolean, Date, Number, String 等等），其 [[Prototype]] 值是 fun.prototype。
* 使用其他 JavaScript 构造器函数创建的对象，其 [[Prototype]] 值就是该构造器函数的 prototype 属性。

```
let o = {a: 1};
// 原型链:    o ---> Object.prototype ---> null

let a = ["yo", "whadup", "?"];
// 原型链:    a ---> Array.prototype ---> Object.prototype ---> null

function f(){
  return 2;
}
// 原型链:    f ---> Function.prototype ---> Object.prototype ---> null

var fun = new Function();
// 原型链:    fun ---> Function.prototype ---> Object.prototype ---> null

function Foo() {
  return {};
}
let foo = new Foo();
// 原型链:    foo ---> Foo.prototype ---> Object.prototype ---> null
```

### 最后，Object和Function的关系如下

```
// Object instanceof Function     即
Object.__proto__ === Function.prototype               // true

// Function instanceof Function 即    
Function.__proto__ === Function.prototype            // true

// Object instanceof Object         即           
Object.__proto__.__proto__ === Object.prototype      // true

// Function instanceof Object     即
Function.__proto__.__proto__ === Object.prototype    // true
```

### 这个图挺好的
![prototype](/resources/prototype.jpg)
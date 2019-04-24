### ES6 Arrow function

#### 箭头函数具有一下特点：
* 函数体内的this对象就是定义时所在对象，不是执行时的对象，这一点与传统的函数不同
* 箭头函数不能作为构造函数
* 不可以使用arguments对象，该对象在函数体内不存在
* 不可以使用yield命令，即箭头函数不能作为Generator函数
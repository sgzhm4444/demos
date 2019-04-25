### for in & for of

#### 1.	for in 语句以任意顺序遍历一个对象自有的、继承的、可枚举的、非Symbol的属性。对于每个不同的属性，语句都会被执行。
* for in遍历的是key值，最好用于object，不要用于array

```
	var obj = {a:1, b:2, c:3};
	for (var prop in obj) {
		console.log("obj." + prop + " = " + obj[prop]);
	}

	// Output:
	// "obj.a = 1"
	// "obj.b = 2"
	// "obj.c = 3"
```

#### 2.	for of 语句在可迭代对象（包括 Array，Map，Set，String，TypedArray，arguments 对象等等）上创建一个迭代循环，调用自定义迭代钩子，并为每个不同属性的值执行语句。
* for of遍历的是value值

```
	//迭代Array
	let iterable = [10, 20, 30];
	for (const value of iterable) {
		console.log(value);
	}
	// 10
	// 20
	// 30
```

```
	//迭代String
	let iterable = "boo";
	for (let value of iterable) {
		console.log(value);
	}
	// "b"
	// "o"
	// "o"
```

```
	//迭代Map
	let iterable = new Map([["a", 1], ["b", 2], ["c", 3]]);
	for (let entry of iterable) {
	  console.log(entry);
	}
	// ["a", 1]
	// ["b", 2]
	// ["c", 3]

	for (let [key, value] of iterable) {
	  console.log(value);
	}
	// 1
	// 2
	// 3
```
```
	//迭代Set
	let iterable = new Set([1, 1, 2, 2, 3, 3]);
	for (let value of iterable) {
	  console.log(value);
	}
	// 1
	// 2
	// 3
```
```
	//迭代arguments
	(function() {
	  for (let argument of arguments) {
		console.log(argument);
	  }
	})(1, 2, 3);
	// 1
	// 2
	// 3
```

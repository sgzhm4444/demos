### 闭包

写一点关于closure的理解

直接上代码

```
	var f1 = function (x) { 
		return function () {    
			return x++; 
		};  
	};  
	var y = f1(0);    
	y();   //0
	y();   //1
	y();   //2
	...
```

closure就是指函数f1中返回另一个函数f2，且f2中引用了f1中定义的变量x，
最后把f1赋值给变量y，则调用y时，由于f2中引用了f1中的变量x，因此f1的作用域一直存在，
每次调用y，修改f1中变量x的值，相当于x的值通过f2的调用而修改了。
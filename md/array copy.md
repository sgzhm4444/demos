### 复制一个数组，不影响原数组
#### 由于js中数组是引用类型，直接赋值复制的话会导致两个数组指向一个引用，操作新数组会影响原数组：

```
	var arr1 = [1,2,3];
	var arr2 = arr1;
	arr2.reverse();
	console.log(arr2);	//[3,2,1]
	console.log(arr1);	//[3,2,1]
```

#### 解决办法是复制数组时创建一个新的数组，切断与原数组的引用关系：

```
	var arr1 = [1,2,3];
	
	var arr2 = [...arr1].reverse();
	var arr2 = [].concat(arr1).reverse();  
	var arr2 = Object.assign([],arr1).reverse();
	var arr2 = arr1.slice().reverse();
	
	console.log(arr2);	//[3,2,1]
	console.log(arr1);	//[1,2,3]
```
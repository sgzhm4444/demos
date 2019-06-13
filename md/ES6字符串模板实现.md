#### ES6字符串模板实现方法
	
```
function sprintf(template, obj) {
	 return template.replace(/\$\{([^}]+)\}/g,function(matched,childItem){
	 	//console.log(matched);
	 	//console.log(childItem);
        return obj[childItem];
    })
}

const template = "My name is ${name}, I'm from ${city}";
const result = sprintf(template, {
	name: "zhanghaomiao",
	city: "beijing"
});
console.log(result);

```

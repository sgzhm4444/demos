#### 实现 (5).add(3).minus(2) 功能

```
let myFun = {
    add(number) {
        if (typeof number !== 'number') {
            throw new Error('请输入数字')
    	}
    	return this + number
    },
    minus(number) {
        if (typeof number !== 'number') {
            throw new Error('请输入数字')
    	}
    	return this - number
    }
}

// 挂载到原型上
Object.assign(Number.prototype, myFun);

(5).add(3).minus(2)
```
```
//throttle
function throttle(func, wait){
	let canRun = true;
	return function(){
		if(!canRun){
			return
		}
		canRun = false;
		setTimeout(function(){
			canRun = true;
			func.apply(this,arguments);
		},wait)
	}
}
```
```
//debounce
function debounce(func, wait) {
	let timer,result;
	return function() {
		if(timer){
			clearTimeout(timer);
		}

		timer = setTimeout(function(){
			result = func.apply(this,arguments);
		},wait);

		return result;
	}
}
```
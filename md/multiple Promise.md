#### 10 个 Ajax 同时发起请求，全部返回展示结果，并且至多允许三次失败，说出设计思路
```
let errorCount = 0;
let p1 = new Promise((resolve, reject) => {
  let xhr = new XMLHttpRequest();
  xhr.open("GET", url);
  xhr.onload = () => {
    if (this.status == 200) {
      resolve(xhr.responseText);
    } else {
      errorCount++;
      if (errorCount > 3) {
        // 失败次数大于3次就应该报错了
        reject(xhr.responseText);
      } else {
        resolve(xhr.responseText);
      }
    }
  }
  xhr.send();
})
let p10 = new Promise((resolve, reject) => {
  let xhr = new XMLHttpRequest();
  xhr.open("GET", url);
  xhr.onload = () => {
    if (this.status == 200) {
      resolve(xhr.responseText);
    } else {
      errorCount++;
      if (errorCount > 3) {
        // 失败次数大于3次就应该报错了
        reject(xhr.responseText);
      } else {
        resolve(xhr.responseText);
      }
    }
  }
  xhr.send();
})
Promise.all([p1, p10]).then(res => {
  console.log(res);
});
```

####3 个 Ajax 同时发起请求，等全部返回结果后（无论成功or失败），再执行下一步
```
let p1 = new Promise((resolve, reject) => {
  let xhr = new XMLHttpRequest();
  xhr.open("GET", url);
  xhr.onload = () => {
    resolve(xhr.responseText);
  }
  xhr.send();
})
let p3 = new Promise((resolve, reject) => {
  let xhr = new XMLHttpRequest();
  xhr.open("GET", url);
  xhr.onload = () => {
    resolve(xhr.responseText);
  }
  xhr.send();
})
Promise.all([p1, p10]).then(res => {
  console.log(res);
});
```
或
```
let p1 = new Promise((resolve, reject) => {
  let xhr = new XMLHttpRequest();
  xhr.open("GET", url);
  xhr.onload = () => {
    if (this.status == 200) {
      resolve(xhr.responseText);
    } else {
      reject(xhr.responseText);
    }
  }
  xhr.send();
})
let p10 = new Promise((resolve, reject) => {
  let xhr = new XMLHttpRequest();
  xhr.open("GET", url);
  xhr.onload = () => {
    if (this.status == 200) {
      resolve(xhr.responseText);
    } else {
      reject(xhr.responseText);
    }
  }
  xhr.send();
})
Promise.allSettled([p1, p10]).then(res => {
  console.log(res);
});
```
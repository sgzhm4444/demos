```
function travel(node) {
  if (node.tagName) {
    console.log(node.tagName);
  }
  var length = node.childNodes.length;
  for (var i = 0; i < length; i++) {
    travel(node.childNodes[i]); 
  }
}
travel(document);
```
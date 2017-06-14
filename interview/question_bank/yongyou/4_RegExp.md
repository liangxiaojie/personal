# `var str = 'hello<img src="haha.png" alt="哈哈" />world';` // 正则匹配输出 'hello[哈哈]world'

```javascript
var str = 'hello<img src="haha.png" alt="哈哈" />world';
var result = str.replace(/<.*?>/, '[哈哈]');
console.log(result);
```

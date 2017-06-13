# 在 String 对象上定义一个 repeatify 函数，这个函数接受一个整数参数，来明确字符串需要重复几次。这个函数要求字符串重复指定的次数。比如：'abc'.repeatify(3); // abcabcabc

```javascript
String.prototype.repeatify = String.prototype.repeatify || function(count) {
  if (!String.prototype.repeat) {
    var str = '' + this;
    count = Math.floor(count);
    var rpt = '';
    for (var i = 0; i < count; i++) {
      rpt += str;
    }
    return rpt;
  } else {
    return this.repeat(count);
  }
}
```

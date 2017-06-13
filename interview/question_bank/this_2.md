# 请写出以下代码运行结果

```javascript
var name = 'window';
var Tom = {
  name: 'Tom',
  show: function() {
    console.log(this.name);
  },
  wait: function() {
    var fun = this.show;
    fun();
  }
};
Tom.wait();
```

```
window
```

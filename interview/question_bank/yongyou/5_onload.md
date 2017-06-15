# JavaScript window.onload 事件和 jQuery ready 函数有何不同？

1. 执行先后顺序不同（最大区别）：

原生 JavaScript 的 window.onload 必须等到包括图片视频脚本等所有页面元素完全加载完毕后才会执行。

jQuery 的 $(document).ready() 是在DOM树渲染完成后就立刻执行。

2. 可以执行的次数不同

原生 JavaScript 的 window.onload 不能同时编写多个，如果有多个 window.onload 方法只会执行最后一个(后面会覆盖前面的)。

jQuery 的 $(document).ready() 可以同时编写多个，会分别执行对应的事件函数，每个事件函数都可以正常执行(不存在覆盖的问题)。

3. 书写的方式不同

原生 JavaScript 的 window.onload 只有一种写法，没有简化写法。

jQuery 的 $(document).ready() 可以简写成 $(function(){})。
PS: 可以用 HTML5 的 DOMContentLoaded 事件代替。在 HTML5 之前可用 document.onreadystatechange 事件并手动判断 document.readyState == 'complete' 来代替。

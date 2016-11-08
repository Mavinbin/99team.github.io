title: 如何写兼容浏览器和Node.js环境的Javascript代码
categories: Web开发
---

如果有打开过jQuery的源码（从1.11及以后），或者Vue.js、React.js的源码，都会在文件的前面看见这样一段代码：

```javascript
( function( global, factory ) {

	"use strict";

	if ( typeof module === "object" && typeof module.exports === "object" ) {

		// For CommonJS and CommonJS-like environments where a proper `window`
		// is present, execute the factory and get jQuery.
		// For environments that do not have a `window` with a `document`
		// (such as Node.js), expose a factory as module.exports.
		// This accentuates the need for the creation of a real `window`.
		// e.g. var jQuery = require("jquery")(window);
		// See ticket #14549 for more info.
		module.exports = global.document ?
			factory( global, true ) :
			function( w ) {
				if ( !w.document ) {
					throw new Error( "jQuery requires a window with a document" );
				}
				return factory( w );
			};
	} else {
		factory( global );
	}

// Pass this if window is not defined yet
} )( typeof window !== "undefined" ? window : this, function( window, noGlobal ) {
  //...
```

以上是jQuery V3.1.0的一段代码。如果自己平时写的都是在浏览器上运行的js代码，又没有接触过Node.js的，可能就不知道 ‘module.exports’ 是什么，为什么要加以判断了。如果有接触过Node，就知道 ‘module.exports’ 其实就是一个js文件的出口，相当于ES6的export。

现在。从头介绍如何写一个兼容浏览器和Node环境的js代码。假设这个js文件名为export.js。

首页，为了避免污染全局作用域，立即执行函数是必须的。这个函数的参数，就像上面的代码那样，也传入一个函数吧。

export.js代码如下：

```javascript
(function(factory) {
  //判断宿主环境
}(function() {
  //代码的核心
}));
```

接下来，就是判断宿主环境。在浏览器环境下，window这个变量是无需创建，自动生成的；在Node环境下，module同理。export.js代码如下：

```javascript
(function(factory) {
  if (typeof module !== 'undefined') {
    module.exports = factory();
  } else {
    factory();
  }
}(function() {
  var vue = 30;
  //...
}));
```

判断了宿主环境后，现在我们需要获得已经定义了的变量vue。在浏览器环境下，用形如

```javascript
window.vue = vue;
```

这样的语句让vue这个变量变成全局的；而在node环境下，export.js用

```javascript
return vue;
```

而需要用到这个变量的文件加上这么一句：

```javascript
var vue = require('./export.js');
```

这样的语句获得vue这个变量。export.js代码如下：

```javascript
(function(factory) {
  if (typeof module !== 'undefined') {
    module.exports = factory();
  } else {
    factory();
  }
}(function() {
  var vue = 30;
  if (typeof window !== 'undefined') {
    window.vue = vue;
  } else {
    return vue;
  }
}));
```

其实，在看了Vue.js的这部分代码后，发现了一个更便捷的方式，就是把vue这个全局变量放在function(factory)里面，这样，下面只要写一个return vue; 就可以了。export.js代码如下：

```javascript
(function(factory) {
  if (typeof module !== 'undefined') {
    module.exports = factory();
  } else {
    window.vue = factory();
  }
}(function() {
  var vue = 30;
  return vue;
}));
```

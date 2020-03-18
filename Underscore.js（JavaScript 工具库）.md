网址：https://underscorejs.bootcss.com/
测试套件地址：https://underscorejs.bootcss.com/test/
最新版本：1.7.0 — August 26, 2014 
最老版本：0.1.0 — October 28, 2009 — Docs

Underscore是一个Jascript工具库，它提供了一整套函数式编程的实用功能，但是没有扩展任何Jascript内置对象。
它弥补了jQueryA没有实现的功能，同时又是Backbone必不可少的部分。

Underscore提供了100多个函数，包括常用的：map、filter、invoke,当然还有很多更专业的辅助函数，
如函数绑定、Jascript模板功能、创建快速索引、强类型相等测试等等。

集合函数（数组或对象）
注意：集合函数能在数组、对象、和类数组对象，比如argument是，NodeList和类似的数组类型上正常工作。但是它通过鸭子类型工作，
所以要避免传递一个不固定length属性的对象（注：对象和数组的长度（length）属性要固定的）。每个循环不能被破坏或者打破，使用_find代替时也要很好的注意。

each   _each(list,iteratee,[context])  别名：forEach
遍历list中所有元素，按顺序用遍历输出每个元素。如果传递了context参数，则把iteratee绑定到context对象上。每次调用iteratee都会传递三个参数：（element,index,list）。如果list是个Javascript对象，iteratee的参数是（value,key,list）。返回list以方便链式调用。
（注：如果存在原生的ForEach方法，Underscore就使用它代替。）
_each([1,2,3],alert);
=> alerts each number in turn...
_each({one：1，two:2,three:3},alert);
=> alert each number value in turn...

map _map(list,iteratee,[context])   别名：

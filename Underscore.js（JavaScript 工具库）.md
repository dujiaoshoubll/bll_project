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

each   _.each(list,iteratee,[context])  别名：forEach
遍历list中所有元素，按顺序用遍历输出每个元素。如果传递了context参数，则把iteratee绑定到context对象上。每次调用iteratee都会传递三个参数：（element,index,list）。如果list是个Javascript对象，iteratee的参数是（value,key,list）。返回list以方便链式调用。
（注：如果存在原生的ForEach方法，Underscore就使用它代替。）
_.each([1,2,3],alert);
=> alerts each number in turn...
_.each({one：1，two:2,three:3},alert);
=> alert each number value in turn...

map  _.map(list,iteratee,[context])   别名：collect
通过变换函数（itetatee迭代器）把list中的每个值映射到一个新的数组中（注：产生一个新的数组）。如果存在原生的map方法，就用原生map方法代替。
如果list是个JavaScript对象，iteratee的参数是（value,key,list）。
_.map([1,2,3],function(num){return num*3;});
=> [3,6,9]
_.map({one:1,two:2,three:3},function(num,key){return num*3;});
=> [3,6,9]

reduce  _.reduce(list,iteratee,[memo],[context])   别名:inject,foldl
reduce方法把list中元素归结为一个单独的数值。Memo是reduce函数的初始值，reduce的每一步都需要由iteratee返回。
这个迭代传递4个参数:memo,value和迭代的index(或者key)和最后一个引用的整个list.

如果没有memo传递给reduce的初始调用，iteratee不会被列表中的第一个元素调用。第一个元素将取代传递给列表中的下一个元素调用iteratee的momo参数。
var sum=_.reduce([1,2,3],function(memo,num){return memo+num;},0);
=> 6

find _.find(list,predicate,[context])  别名：detect
在list中逐项查找，返回第一个通过predicate迭代函数真值检测的元素值，如果没有值传递给测试迭代器将返回underfined。
如果找到匹配的元素，函数将立即返回，不会遍历整个list。
var even=_.find([1,2,3,4,5,6],function(num){return num % 2==0;});
=> 2

filter  _.filter(list,predicate,[context])  别名：select
遍历list中的每个值，返回包含所有通过predicate真值检测的元素值。（注：如果存在原生filter方法，则用原生的filter方法。）
var evens=_filter([1,2,3,4,5,6],function(num){return num % 2==0;});
=> [2,4,6]

reject  _.reject(list,predicate,[context])
返回list中没有通过predicate真值检测的元素集合，与filter相反。
var odds=_.reject([1,2,3,4,5,6],function(num){return num % 2 ==0;});
=> [1,3,5]

contains  _.contains(list,value)   别名：include
如果list包含指定的value则返回true（注：使用===检测）。如果list是数组，内部使用indexof判断。
_.contains([1,2,3],3);
=> true

max  _.max(list,[iteratee],[context])
返回list中的最大值。如果传递iteratee参数，iteratee将作为list中的每个值的排序依据。如果list为空，将返回-infinity，
所以你可能需要事先用isEmpty检测list。
var stooges = [{name:'moe',age:40},{name:'larry',age:50},{name:'curly',age:60}];
_max.(stooges,function(stooge){return stooge.age;});
=> {name:'curly',age:60};

min  _.min(list,[iteratee],[context])
返回list中的最小值。如果传递iteratee参数，iteratee将作为list中每个值的排序依据。如果list为空，将返回-infinity,
所以你可能需要实先用isEmpty检查list。
var numbers=[10,5,100,2,1000];
_.min(numbers);
=> 2

数组函数（Array Functions）
注：arguments(参数)对象将在所有数组函数中工作，然而，Underscore函数的设计并不只是针对稀疏（"sparse"）数组的。

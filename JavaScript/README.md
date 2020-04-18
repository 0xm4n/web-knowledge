### 1 -  闭包

概念：闭包函数能够在函数外部作用域读取函数内部的变量。

作用：1、能够读取函数内部的变量(封装私有变量) 2、让变量的值始终保持在内存。





### 2 -  手写防抖

概念：触发高频事件后n	秒内函数只会执行一次，如果n秒内高频事件再次被触发，则重新计算时间

思路：每次触发事件时都取消之前的延时调用方法

应用场景：搜索联想，用户在不断输入值时，用防抖来节约请求资源。

``` javascript
function debounce(fn) {
    let timeout = null; 
    return function () {
      clearTimeout(timeout); 
      timeout = setTimeout(() => { 
        fn.apply(this, arguments);
      }, 500);
    };
  }
  function sayHi() {
    console.log('防抖成功');
  }

  var inp = document.getElementById('inp');
  inp.addEventListener('input', debounce(sayHi)); 
```





### 3 -  手写节流

概念：高频事件触发，但在n秒内只会执行一次，所以节流会稀释函数的执行频率

思路：每次触发事件时都判断当前是否有等待执行的延时函数

应用场景：客户连续频繁地触发事件，监听滚动事件，是否滑到底部自动加载

``` javascript
function throttle(fn) {
  let canRun = true; 
  return function () {
    if (!canRun) return; 
    canRun = false; 
    setTimeout(() => {
      fn.apply(this, arguments);
      canRun = true;
    }, 500);
  };
}
function sayHi(e) {
  console.log(e.target.innerWidth, e.target.innerHeight);
}
window.addEventListener("resize", throttle(sayHi));
```





### 4 -  手写计数器

``` javascript
var counter = function () {
  var counter = 1;
  return function () {
    return counter++;
  };
};
```





### 5 -  JavaScript数据类型

6种数据类型：数字number、字符串string、布尔值Boolean、undefined、null、对象Object





### 6 -  变量提升

变量和函数的声明在编译阶段被放入内存中。JavaScript仅提升声明，而不提升初始化。





### 7 -   JavaScript类型转换，比如 object 和 string 做加法运算；JavaScript里面 1+‘1’=？  1+null=？





### 8 -  变量声明var、let 和 const 区别

var：在任何语句执行前都已完成声明和初始化，即变量提升且值为undefined

function： 声明、初始化、赋值一开始就全部完成，所以函数的变量提升优先级更高

let：解析器进入一个块级作用域，发现let关键字，变量只完成声明，并没有初始化。此时如果在此作用域提前访问，则报错xx is not defined，这就是暂时性死区的由来。等到解析到有let那一行的时候，才会进入初始化阶段。如果let的那一行是赋值操作，则初始化和赋值同时进行

区别：

a)  var声明变量存在变量提升，let和const不存在变量提升

b)   let和const声明形成块作用域，而var不存在此作用域

c)   同一作用域下let和const不能声明同名变量，而var可以

d)   let、const存在暂存死区





### 9 -  正则表达式，正则表达式中*和+的区别

? 问号表示某个模式出现0次或1次
 \* 星号表示某个模式出现0次或多次

\+ 加号表示某个模式出现1次或多次

^ 表示字符串的开始位置

$ 表示字符串的结束位置

竖线符号（|）在正则表达式中表示“或关系”（OR）





### 10 -  this的指向 

this就是函数运行时所在的环境对象





### 11-  如何改变this的指向

apply、call、bind 





### 12  -  bind、apply、call的区别

apply方法的作用与call方法类似，也是改变this指向，然后再调用该函数。唯一的区别就是，它接收一个数组作为函数执行时的参数，使用格式如下。

通过bind改变this作用域会返回一个新的函数，这个函数不会马上执行。





### 13 - 手写一个bind()





### 14 -  箭头函数的概念，箭头函数和function区别

箭头函数是普通函数的简写，和普通函数有以下几点差异：

1、函数体内的 this 对象，就是定义时所在的对象，而不是使用时所在的对象。

2、函数体内不存在arguments 对象。如果要用，可以用 rest 参数代替。

3、不可以使用 new 命令，因为：没有自己的 this，无法调用 call，apply。没有 prototype 属性 





### 15 -  箭头函数的优点是什么？ 

a) 箭头函数写代码拥有更加简洁的语法；

b) 不会绑定this。





### 16 -  手写instanceof

instanceof 运算符用于检测构造函数的 prototype 属性是否出现在某个实例对象的原型链上。





### 17-  new做了什么

1. 首先创建一个空对象

var o = new Object();

2. 将空对象的原型赋值为构造器函数的原型

o.__proto__ = A.prototype;

3. 更改构造器函数内部this，将其指向新创建的空对象

A.call(o);





### 18 -  手写new

```javascript
function _new(fn, ...arg) {
  const obj = Object.create(fn.prototype);
  const ret = fn.apply(obj, arg);
  return ret instanceof Object ? ret : obj;
}
```





### 19 -  函数柯里化





### 20 -  JavaScript原型链

每个实例对象（ object ）都有一个私有属性（称之为 __proto__ ）指向它的构造函数的原型对象（prototype ）。该原型对象也有一个自己的原型对象( __proto__ ) ，层层向上直到一个对象的原型对象为 null。根据定义，null 没有原型，并作为这个原型链中的最后一个环节。





### 21 -  Event loop

同步任务执行完了，引擎就会去检查那些挂起来的异步任务，是不是可以进入主线程了。这种循环检查的机制，就叫做事件循环





### 22 -  promise有几种状态？分别是什么？

a)   异步操作未完成（pending）

b)   异步操作成功（fulfilled）

c)   异步操作失败（rejected）





### 23 -  promise.then返回的是什么？





### 24 -  手写封装promise超时





### 25 -  ES5的继承与ES6的继承 





### 26 -  ES6新特性 



\1. 需要三个请求全部完成，用什么？(Promise.all)

\2.  

 

\3. ES5继承，ES6继承 

\4. 继承方案（优缺点）

\5. ES6新特性 

 

\6. Map Set weakMap weakSet

\7. for in 和for of 的区别

https://juejin.im/post/5a2e5f0851882575d42f5609

https://segmentfault.com/a/1190000013756012

\8. class关键字

\9. JS的垃圾回收机制

扩展运算符 
# 现代 JavaScript 速查

<a id="modern-javascript-cheatsheet"></a>

![Modern JavaScript cheatsheet](https://i.imgur.com/aexPxMb.png)
<small>Image Credits: [Ahmad Awais ⚡️](https://github.com/ahmadawais)</small>

## 简介

### 初心

本文档是一份 JavaScript 速查表，你在现代项目中会经常遇到，以及最新的代码示例。

本指南不是为了教你从头开始学习 JavaScript ，而是为了帮助那些可能不熟悉当前代码库（例如 React）所用到 JavaScript 概念的开发人员。

此外，我有时还会提供一些个人的建议，这些建议可能是有争议的，但我也会注意到，当我这么做的时候，这是我个人的建议。

> **注意：** 这里介绍的大多数概念来自于最新的 JavaScript 语言（ ES2015，通常称为 ES6）。你可以在 [这里](http://es6-features.org) 找到新增的特性，网站做得很棒。

### 补充资源

当您努力了解一个新概念时，我建议你在以下资源网站上寻找相关的答案：

- [MDN (Mozilla Developer Network)](https://developer.mozilla.org/fr/search?q=)
- [你所不知道的JS (书)](https://github.com/getify/You-Dont-Know-JS)
- [ES6 新特性和例子](http://es6-features.org)
- [WesBos 的博客 (ES6)](http://wesbos.com/category/es6/)
- [Reddit (JavaScript)](https://www.reddit.com/r/javascript/)
- 用 [Google](https://www.google.com/) 来查找特定的博客和资源
- [StackOverflow](https://stackoverflow.com/questions/tagged/javascript)


## 目录

- [现代 JavaScript 速查](#modern-javascript-cheatsheet)
  * [简介](#introduction)
    + [初心](#motivation)
    + [参考资料](#complementary-resources)
  * [目录](#table-of-contents)
  * [概念](#notions)
    + [变量声明: var, const, let](#variable-declaration-var-const-let)
      - [简单说明](#short-explanation)
      - [简单的示例](#sample-code)
      - [详细说明](#detailed-explanation)
      - [扩展阅读](#external-resource)
    + [箭头函数](#-arrow-function)
      - [简单的示例](#sample-code-1)
      - [详细说明](#detailed-explanation-1)
        * [简洁性](#concision)
        * [*this* 引用](#this-reference)
      - [有用的资源](#useful-resources)
    + [函数参数默认值](#function-default-parameter-value)
      - [扩展阅读](#external-resource-1)
    + [解构对象和数组](#destructuring-objects-and-arrays)
      - [用示例代码说明](#explanation-with-sample-code)
      - [有用的资源](#useful-resources-1)
    + [数组方法 - map / filter / reduce](#array-methods---map--filter--reduce)
      - [简单的示例](#sample-code-2)
      - [说明](#explanation)
        * [Array.prototype.map()](#arrayprototypemap)
        * [Array.prototype.filter()](#arrayprototypefilter)
        * [Array.prototype.reduce()](#arrayprototypereduce)
      - [扩展阅读](#external-resource-2)
    + [展开操作符 "..."](#spread-operator-)
      - [简单的代码示例](#sample-code-3)
      - [说明](#explanation-1)
        * [应用于迭代 (如数组)](#in-iterables-like-arrays)
        * [函数剩余参数](#function-rest-parameter)
        * [对象属性展开](#object-properties-spreading)
      - [扩展阅读](#external-resources)
    + [对象属性简写](#object-property-shorthand)
      - [说明](#explanation-2)
      - [扩展阅读](#external-resources-1)
    + [Promises](#promises)
      - [简单的代码示例](#sample-code-4)
      - [说明](#explanation-3)
        * [创建 promise](#create-the-promise)
        * [Promise 处理器的用法](#promise-handlers-usage)
      - [扩展阅读](#external-resources-2)
    + [模板字符串](#template-literals)
      - [简单的代码示例](#sample-code-5)
      - [扩展阅读](#external-resources-3)
    + [带标签(tag)的模板字符串](#tagged-template-literals)
      - [扩展阅读](#external-resources-4)
    + [ES6 模块的导入 / 导出 (imports / exports)](#imports--exports)
      - [用示例代码说明](#explanation-with-sample-code-1)
        * [命名导出](#named-exports)
        * [默认导入 / 导出 (imports / exports)](#default-import--export)
      - [扩展阅读](#external-resources-5)
    + [JavaScript 中的 *this*](#-javascript-this)
      - [扩展阅读](#external-resources-6)
    + [类(Class)](#class)
      - [简单的示例](#samples)
      - [扩展阅读](#external-resources-7)
    + [`Extends` 和 `super` 关键字](#extends-and-super-keywords)
      - [简单的代码示例](#sample-code-6)
      - [扩展阅读](#external-resources-8)
    + [异步和等待(Async Await)](#async-await)
      - [简单的代码示例](#sample-code-7)
      - [用示例代码说明](#explanation-with-sample-code-2)
      - [错误处理](#error-handling)
      - [扩展阅读](#external-resources-9)
    + [真值/假值(Truthy / Falsy)](#truthy--falsy)
      - [扩展阅读](#external-resources-10)
    + [静态方法](#static-methods)
      - [简单说明](#short-explanation-1)
      - [简单的代码示例](#sample-code-8)
      - [详细说明](#detailed-explanation-2)
        * [在静态方法调用另一个静态方法](#calling-other-static-methods-from-a-static-method)
        * [在非静态方法调用静态方法](#calling-static-methods-from-non-static-methods)
      - [扩展阅读](#external-resources-11)
  * [词汇表](#glossary)
    + [作用域(Scope)](#-scope)
    + [变量的可变性](#-variable-mutation)

<div id="notions"></div>

## 概念

<div id="variable-declaration-var-const-let"></div>

### 变量声明: var, const, let

在 JavaScript 中，有 3 个关键字可用于声明一个变量，他们之间有些差异。那些是 `var` ，`let` 和 `const`。

<div id="short-explanation"></div>

#### 简单说明

使用 `const` 关键字声明的变量无法重新分配，而 `let` 和 `var` 可以。

我建议总是默认使用 `const` 来声明你的变量，如果你需要改变它，或者稍后需要重新分配，那么实用 `let` 。

<table>
  <tr>
    <th></th>
    <th>作用域</th>
    <th>可否重新分配</th>
    <th>可变性</th>
   <th><a href="#tdz_sample">暂时性死区</a></th>
  </tr>
  <tr>
    <th>const</th>
    <td>Block</td>
    <td>No</td>
    <td><a href="#const_mutable_sample">Yes</a></td>
    <td>Yes</td>
  </tr>
  <tr>
    <th>let</th>
    <td>Block</td>
    <td>Yes</td>
    <td>Yes</td>
    <td>Yes</td>
  </tr>
   <tr>
    <th>var</th>
    <td>Function</td>
    <td>Yes</td>
    <td>Yes</td>
    <td>No</td>
  </tr>
</table>

<div id="sample-code"></div>

#### 简单的示例

```js
const person = "Nick";
person = "John" // 将会引起错误，person 不能重新分配
```

```js
let person = "Nick";
person = "John";
console.log(person) // "John", 使用 let 允许重新分配
```
<div id="detailed-explanation"></div>

#### 详细说明

变量的 [*作用域*](#scope_def) 大致意思是“在哪里可以访问这个变量”。 

##### var

`var` 声明的变量是 *函数作用域* ，这意味着当在函数中创建变量时，该函数中的所有内容都可以访问该变量。
此外，函数中创建的 *函数作用域* 变量无法在此函数外访问。

我建议你把它看作一个 *X 作用域* 变量，意味着这个变量是 X 的属性。

```js
function myFunction() {
  var myVar = "Nick";
  console.log(myVar); // "Nick" - 在这个函数中 myVar 可被访问到
}
console.log(myVar); // 抛出错误 ReferenceError, 在函数之外 myVar 则无法访问
```

继续关注变量的作用域，这里是一个更微妙的例子：

```js
function myFunction() {
  var myVar = "Nick";
  if (true) {
    var myVar = "John";
    console.log(myVar); // "John"
    // 实际上，myVar是函数作用域，我们只是将之前 myVar 的值 "Nick" 抹去，重新声明为 "John"
  }
  console.log(myVar); // "John" - 看看 if 语句块中的指令是如何影响这个值的 
}
console.log(myVar); // 抛出错误 ReferenceError, 在函数之外 myVar 则无法访问
```

此外，在执行过程中，*var*声明的变量被移动到范围的顶部。这就是我们所说的[变量声明提升（var hoisting)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var#var_hoisting)。

这部分的代码：

```js
console.log(myVar) // undefined -- 不会报错
var myVar = 2;
```

在执行时，被解析为：

```js
var myVar;
console.log(myVar) // undefined -- 不会报错
myVar = 2;
```

愚人码头注：变量提升和函数声明提升可以查看：<a href="http://www.css88.com/archives/7924" target="_blank">JavaScript 中的 Hoisting (变量提升和函数声明提升)</a>

##### let

`var` 和 `let` 大致相同，但是用 `let` 声明的变量时有以下几个特性：

- *块级作用域*（ block scoped )
- 在被分配之前， **无法** 访问使用
- 在同一个作用域之下，不能重新声明


我们来看看我们前面的例子，采用块级作用域（ block scoping ）后的效果：

```js
function myFunction() {
  let myVar = "Nick";
  if (true) {
    let myVar = "John";
    console.log(myVar); // "John"
    // 实际上 myVar 在块级作用域中，（在 if 语句块中）我们只是创建了一个新变量 myVar。
    // 此变量在 if 语句块之外不可访问，
    // 完全独立于创建的第一个 myVar 变量！
  }
  console.log(myVar); // "Nick", 可以看到 if 语句块中的指令不会影响这个值
}
console.log(myVar); // 抛出错误 ReferenceError，myVar 无法在函数外部被访问。
```

<a name="tdz_sample"></a>现在，我们来看看 *let*（和 *const*）变量在被赋值之前不可访问是什么意思：

```js
console.log(myVar) // 抛出一个引用错误 ReferenceError !
let myVar = 2;
```

与 *var* 变量不同的是，如果你在 *let* 或者 *const* 变量被赋值之前读写，那么将会出现错误。这种现象通常被称为暂存死区（[*Temporal dead zone*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let#Temporal_Dead_Zone_and_errors_with_let)）或者 *TDZ*。

> **注意：** 从技术上讲，*let* 和 *const* 变量声明时也存在提升，但并不代表它们的赋值也会被提升。但由于它被设计成了赋值之前无法使用，所以我们直观感觉上它没有被提升，但其实是存在提升的。如果想了解更多细节，请看[这篇文章](http://jsrocks.org/2015/01/temporal-dead-zone-tdz-demystified)。

此外，您不能重新声明一个 *let* 变量：

```js
let myVar = 2;
let myVar = 3; // 抛出语法错误 SyntaxError
```

##### const

`const` 声明的变量很像 *let* ，但它不能被重新赋值。

总结一下 *const* 变量：

- *块级作用域*
- 分配之前无法访问
- 在同一个作用域内部，不能重新声明
- 不能被重新分配

```js
const myVar = "Nick";
myVar = "John" // 抛出一个错误， 不允许重新分配
```

```js
const myVar = "Nick";
const myVar = "John" // 抛出一个错误， 不允许重新声明
```

<a name="const_mutable_sample"></a> 但这里有一个小细节：`const` 变量并不是[**不可变**](#mutation_def)，具体来说，如果 `const` 声明的变量是 *object* 和 *array* 类型的值，那它是 **可变的** 。

对于对象：
```js
const person = {
  name: 'Nick'
};
person.name = 'John' // 这是有效的！person 变量并非完全重新分配，只是值被改变
console.log(person.name) // "John"
person = "Sandra" // 抛出一个错误， 因为用 const 声明的变量不能被重新分配
```

对于数组：
```js
const person = [];
person.push('John'); // 这是有效的！person 变量并非完全重新分配，只是值被改变
console.log(person[0]) // "John"
person = ["Nick"] // 抛出一个错误， 因为用 const 声明的变量不能被重新分配
```

<a id="external-resource"></a>

#### 扩展阅读

- [How let and const are scoped in JavaScript - WesBos](http://wesbos.com/javascript-scoping/)
- [Temporal Dead Zone (TDZ) Demystified](http://jsrocks.org/2015/01/temporal-dead-zone-tdz-demystified)

<a id="-arrow-function"></a>

### <a name="arrow_func_concept"></a> 箭头函数

ES6 JavaScript 更新引入了 *箭头函数* ，这是另一种声明和使用函数的方法。以下是他们带来的好处： 

- 更简洁 
- *this* 的值继承自外围的作用域 
- 隐式返回

<a id="sample-code-1"></a>

#### 简单的示例

- 简洁性和隐式返回

```js
function double(x) { return x * 2; } // 传统的方法
console.log(double(2)) // 4
```

```js
const double = x => x * 2; // 相同的函数写成带有隐式返回的箭头函数
console.log(double(2)) // 4
```

- *this* 的引用

在箭头函数中， *this* 意味着封闭执行上下文的 *this* 值。基本上，使用箭头函数，在函数中调用函数之前，您不需要执行 "that = this" 这样的的技巧。

```js
function myFunc() {
  this.myVar = 0;
  setTimeout(() => {
    this.myVar++;
    console.log(this.myVar) // 1
  }, 0);
}
```

<a id="detailed-explanation-1"></a>

#### 详细说明

<a id="concision"></a>

##### 简洁性

箭头函数在许多方面比传统函数更简洁。让我们来看看所有可能的情况：

- 隐式 VS 显式返回

**显式返回 (explicit return)** 是指在函数体中明确的使用 *return* 这个关键字。

```js
  function double(x) {
    return x * 2; // 这个函数显示返回 x * 2, 并且使用了 *return* 关键字
  }
```

在函数传统的写法中，返回总是显式的。但是如果是使用箭头函数，你可以执行 *隐式返回(implicit return)*，这表示你不需要使用关键字 *return* 来返回一个值。

要做隐式回传，代码必须用一行语句写完。

```js
  const double = (x) => {
    return x * 2; // 这里是显式返回
  }
```

由于这里只有一个返回值，我们可以做一个隐式的返回。

```js
  const double = (x) => x * 2;
```

这样做，我们只需要 **移除括号** 以及 **return** 关键字。这就是为什么它会被称为 *隐式* 返回，*return* 关键字不在了，但是这个函数确实会返回 `x * 2`。

> **注意：** 如果你的函数没有回传一个值 (这种作法有 *副作用*)，那么它将不会做显式或隐式返回。

另外，如果你想隐式地返回一个 *对象(object)*，你**必须用括号包裹**，否则它将与块大括号冲突：

```js
const getPerson = () => ({ name: "Nick", age: 24 })
console.log(getPerson()) // { name: "Nick", age: 24 } -- 箭头函数隐式地返回一个对象
```

- 只有一个参数

如果你的函数只接受一个参数，你可以省略包裹它的括号。如果我们拿上述的 *double* 代码做为举例：

```js
  const double = (x) => x * 2; // 这个箭头函数只接受一个参数
```

包裹参数的括号是可以被省略：

```js
  const double = x => x * 2; // 这个箭头函数只接受一个参数
```

- 没有参数

当没有为箭头函数提供任何参数时，你就必须加上括号，否则将会抛出语法错误。

```js
  () => { // 提供括号，一切都能正常运行
    const x = 2;
    return x;
  }
```

```js
  => { // 没有括号，这不能正常运行！
    const x = 2;
    return x;
  }
```

<a id="this-reference"></a>

##### *this* 引用

要理解箭头函数的精妙之处，你就必须知道 [this](#this_def) 在 JavaScript 中是如何运作的。

在一个箭头函数中，*this* 等同于封闭执行上下文的 *this* 值。这意味着，一个箭头函数并不会创造一个新的 *this*，而是从它的外围作用域中抓取的。

如果没有箭头函数，你想在一个函数内部的函数中通过 *this* 访问变量，你就只能使用 *that = this* 或者是 *self = this* 这样的技巧。

举例来说，你在 myFunc 中使用 setTimeout 函数：

```js
function myFunc() {
  this.myVar = 0;
  var that = this; // that = this 技巧
  setTimeout(
    function() { // 在这个函数作用域中，一个新的 *this* 被创建
      that.myVar++;
      console.log(that.myVar) // 1

      console.log(this.myVar) // undefined -- 见上诉函数声明
    },
    0
  );
}
```

但是如果你使用箭头函数，*this* 是从它的外围作用域中抓取的：

```js
function myFunc() {
  this.myVar = 0;
  setTimeout(
    () => { // this 值来自它的外围作用域, 在这个示例中，也就是 myFunc 函數
      this.myVar++;
      console.log(this.myVar) // 1
    },
    0
  );
}
```

<a id="useful-resources"></a>

#### 有用的资源

- [Arrow functions introduction - WesBos](http://wesbos.com/arrow-functions/)
- [JavaScript arrow function - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
- [Arrow function and lexical *this*](https://hackernoon.com/javascript-es6-arrow-functions-and-lexical-this-f2a3e2a5e8c4)

<a id="function-default-parameter-value"></a>

### 函数参数默认值

从 ES2015 JavaScript 更新之后开始，你可以通过下列的语法为函数的参数设定默认值：

```js
function myFunc(x = 10) {
  return x;
}
console.log(myFunc()) // 10 -- 没有提供任何值，所以在 myFunc 中 10 做为默认值分配给 x
console.log(myFunc(5)) // 5 -- 有提供一个参数值，所以在 myFunc 中 x 等于 5 

console.log(myFunc(undefined)) // 10 -- 提供 undefined 值，所以默认值被分配给 x 
console.log(myFunc(null)) // null -- 提供一个值 (null)，详细资料请见下文 
```

默认参数应用于两种且仅两种情况：

- 没有提供参数
- 提供 *undefined* 未定义参数

换句话说，如果您传入 *null* ，则**不会应用**默认参数。

> **注意：** 默认值分配也可以与解构参数一起使用（参见下一个概念以查看示例）。

<a id="external-resource-1"></a>

#### 扩展阅读

- [Default parameter value - ES6 Features](http://es6-features.org/#DefaultParameterValues)
- [Default parameters - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters)

<a id="destructuring-objects-and-arrays"></a>

### 解构对象和数组

*解构 (destructuring)* 是通过从存储在对象或数组中的数据中提取一些值来创建新变量的简便方法。

举个简单的实例，*destructuring* 可以被用来解构函数中的参数，或者像是 React 项目中 *this.props* 这样的用法。

<a id="explanation-with-sample-code"></a>

#### 用示例代码说明

- Object

我们考虑一下以下对象的所有属性：

```js
const person = {
  firstName: "Nick",
  lastName: "Anderson",
  age: 35,
  sex: "M"
}
```

不使用解构：

```js
const first = person.firstName;
const age = person.age;
const city = person.city || "Paris";
```

使用解构，只需要 1 行代码：

```js
const { firstName: first, age, city = "Paris" } = person; // 就是这么简单！

console.log(age) // 35 -- 一个新变量 age 被创建，并且其值等同于 person.age
console.log(first) // "Nick" -- 一个新变量 first 被创建，并且其值等同于 person.firstName A new variable first is created and is equal to person.firstName
console.log(firstName) // Undefined -- person.firstName 虽然存在，但是新变量名为 first
console.log(city) // "Paris" -- 一个新变量 city 被创建，并且因为 person.city 为 undefined(未定义) ，所以 city 将等同于默认值也就是 "Paris"。
```

**注意：** 在 `const { age } = person;` 中, *const* 关键字后的括号不是用于声明对象或代码块，而是 *解构(structuring)* 语法。

- 函数参数

*解构(structuring)* 经常被用来解构函数中的对象参数。

不使用解构：

```js
function joinFirstLastName(person) {
  const firstName = person.firstName;
  const lastName = person.lastName;
  return firstName + '-' + lastName;
}

joinFirstLastName(person); // "Nick-Anderson"
```

在解构对象参数 *person* 这个参数时，我们可以得到一个更简洁的函数：

```js
function joinFirstLastName({ firstName, lastName }) { // 通过解构 person 参数，我们分别创建了 firstName 和 lastName 这两个变数
  return firstName + '-' + lastName;
}

joinFirstLastName(person); // "Nick-Anderson"
```
[箭头函数](#arrow_func_concept)中使用解构，使得开发过程更加愉快：

```js
const joinFirstLastName = ({ firstName, lastName }) => firstName + '-' + lastName;

joinFirstLastName(person); // "Nick-Anderson"
```

- Array

我们考虑一下以下数组：

```js
const myArray = ["a", "b", "c"];
```

不使用解构：

```js
const x = myArray[0];
const y = myArray[1];
```

使用解构：

```js
const [x, y] = myArray; // 就是这么简单！

console.log(x) // "a"
console.log(y) // "b"
```

<a id="useful-resources-1"></a>

#### 有用的资源

- [ES6 Features - Destructuring Assignment](http://es6-features.org/#ArrayMatching)
- [Destructuring Objects - WesBos](http://wesbos.com/destructuring-objects/)
- [ExploringJS - Destructuring](http://exploringjs.com/es6/ch_destructuring.html)

<a id="array-methods---map--filter--reduce"></a>

### 数组方法 - map / filter / reduce

*map*，*filter* 和 *reduce* 都是数组提供的方法，它们源自于 [*函数式编程*](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0) 。

总结一下：

- **Array.prototype.map()** 接受一组数组，在其元素上执行某些操作，并返回具有转换后的元素数组。
- **Array.prototype.filter()** 接受一组数组，依照元素本身决定是否保留，并返回一个仅包含保留元素的数组。
- **Array.prototype.reduce()** 接受一组数组，将这些元素合并成单个值（并返回）。

我建议尽可能地使用它们来遵循函数式编程 (functional programming) 的原则，因为它们是可组合的，简洁的且优雅的。

通过这三种方法，您可以避免在大多数情况下使用 *for* 和 *forEach* 。当你试图做一个 *for* 循环时，尝试用 *map*，*filter* 和 *reduce* 来组合试试。起初你可能很难做到这一点，因为它需要你学习一种新的思维方式，但一旦你得到它，事情会变得更容易。

愚人码头注：JavaScript 函数式编程建议看看以下几篇文章
<ul>
<li><a href="http://www.css88.com/archives/7781" target="_blank">JavaScript 中的 Currying(柯里化) 和 Partial Application(偏函数应用)</a></li>
<li><a href="http://www.css88.com/archives/7794" target="_blank">一步一步教你 JavaScript 函数式编程（第一部分）</a></li>
<li><a href="http://www.css88.com/archives/7822" target="_blank">一步一步教你 JavaScript 函数式编程（第二部分）</a></li>
<li><a href="http://www.css88.com/archives/7829" target="_blank">一步一步教你 JavaScript 函数式编程（第三部分）</a></li>
<li><a href="http://www.css88.com/archives/7833" target="_blank">JavaScript 函数式编程术语大全</a></li>
</ul>

<a id="sample-code-2"></a>

#### 简单的示例

```js
const numbers = [0, 1, 2, 3, 4, 5, 6];
const doubledNumbers = numbers.map(n => n * 2); // [0, 2, 4, 6, 8, 10, 12]
const evenNumbers = numbers.filter(n => n % 2 === 0); // [0, 2, 4, 6]
const sum = numbers.reduce((prev, next) => prev + next, 0); // 21
```

通过组合 map，filter 和 reduce 来计算 10 分以上的学生成绩总和 sum ：

```js
const students = [
  { name: "Nick", grade: 10 },
  { name: "John", grade: 15 },
  { name: "Julia", grade: 19 },
  { name: "Nathalie", grade: 9 },
];

const aboveTenSum = students
  .map(student => student.grade) // 我们将学生数组映射到他们成绩的数组中
  .filter(grade => grade >= 10) // 我们过滤成绩数组以保持10分以上的元素
  .reduce((prev, next) => prev + next, 0); // 我们将合计所有10分以上的成绩

console.log(aboveTenSum) // 44 -- 10 (Nick) + 15 (John) + 19 (Julia), 低于10的 Nathalie 被忽略 
```

<a id="explanation"></a>

#### 说明

让我们考虑一下下列数组：

```js
const numbers = [0, 1, 2, 3, 4, 5, 6];
```

<a id="arrayprototypemap"></a>

##### Array.prototype.map()

```js
const doubledNumbers = numbers.map(function(n) {
  return n * 2;
});
console.log(doubledNumbers); // [0, 2, 4, 6, 8, 10, 12]
```

这里发生了什么？我们在 *numbers* 这个数组中使用 .map 方法，map 将会迭代数组的每个元素，并传递给我们的函数。该函数的目标是生成并返回一个新的值，以便 map 可以替换掉原本的数组。

我们来解释一下这个函数，使之更清楚一点：

```js
const doubleN = function(n) { return n * 2; };
const doubledNumbers = numbers.map(doubleN);
console.log(doubledNumbers); // [0, 2, 4, 6, 8, 10, 12]
```

`numbers.map(doubleN)` 将会产生 `[doubleN(0), doubleN(1), doubleN(2), doubleN(3), doubleN(4), doubleN(5), doubleN(6)]` 而它们分别等同于 `[0, 2, 4, 6, 8, 10, 12]`。

> **注意：** 如果你不需要返回一个新的数组， 且只想执行一个带有副作用的循环，使用 for / forEach 循环会更为符合你的需求。

<a id="arrayprototypefilter"></a>

##### Array.prototype.filter()

```js
const evenNumbers = numbers.filter(function(n) {
  return n % 2 === 0; // 如果 "n" 符合条件返回 true , 如果 "n" 不符合条件则 false 。
});
console.log(evenNumbers); // [0, 2, 4, 6]
```

我们在 *numbers* 数组中使用 .filter  方法，过滤器遍历数组中的每个元素，并将其传递给我们的函数。函数的目标是返回一个布尔值，它将确定当前值是否被保留。过滤之后返回的数组将只包含保留值。

<a id="arrayprototypereduce"></a>

##### Array.prototype.reduce()

reduce 方法的目标是将迭代数组中的所有元素，*减少* 到只留下单一值。如何聚合这些元素取决于你。

```js
const sum = numbers.reduce(
  function(acc, n) {
    return acc + n;
  },
  0 // 累加器迭代变量的初始值
);

console.log(sum) //21
```

就像 .map 和 .filter 方法一样， .reduce 方法被应用在数组上并接收一个函数做为第一个参数。

下面是一些差异：

- .reduce 接受两个参数

第一个参数是一个函数，将在每个迭代步骤中被调用。

第二个参数是在第一个迭代步骤（读取下一个用的）的累加器变量的值（此处是 *acc*）。

- 函数参数

作为 .reduce 的第一个参数传递的函数需要两个参数。第一个（此处是 *acc*）是累加器变量，而第二个参数（*n*）则是当前元素。

累加器变量的值等于 **上一次** 迭代步骤中函数的返回值。在迭代过程的第一步，*acc* 等于你做为 .reduce 时第二个参数所传递的值（愚人码头注：也就是累加器初始值）。

###### 进行第一次迭代

`acc = 0` 因为我们把 0 做为 reduce 的第二个参数

`n = 0` *number* 数组的第一个元素

函数返回 *acc* + *n* --> 0 + 0 --> 0

###### 进行第二次迭代

`acc = 0` 因为它是上次迭代所返回的值

`n = 1` *number* 数组的第二个元素

函数返回 *acc* + *n* --> 0 + 1 --> 1

###### 进行第三次迭代

`acc = 1` 因为它是上次迭代所返回的值

`n = 2` *number* 数组的第三个元素

函数返回 *acc* + *n* --> 1 + 2 --> 3

###### 进行第四次迭代

`acc = 3` 因为它是上次迭代所返回的值

`n = 3` *number* 数组的第四个元素

函数返回 *acc* + *n* --> 3 + 3 --> 6

###### [...] 进行最后一次迭代

`acc = 15` 因为它是上次迭代所返回的值

`n = 6` *number* 数组的最后一个元素

函数返回 *acc* + *n* --> 15 + 6 --> 21

因为它是最后一个迭代步骤了， **.reduce** 将返回 21 。

<a id="external-resource-2"></a>

#### 扩展阅读

- [Understanding map / filter / reduce in JS](https://hackernoon.com/understanding-map-filter-and-reduce-in-javascript-5df1c7eee464)

<a id="spread-operator-"></a>

### 展开操作符 "..."

ES2015 已经引入了展开操作符 `...` ，可以将可迭代多个元素（如数组）展开到适合的位置。

<a id="sample-code-3"></a>

#### 简单的代码示例

```js
const arr1 = ["a", "b", "c"];
const arr2 = [...arr1, "d", "e", "f"]; // ["a", "b", "c", "d", "e", "f"]
```

```js
function myFunc(x, y, ...params) {
  console.log(x);
  console.log(y);
  console.log(params)
}

myFunc("a", "b", "c", "d", "e", "f")
// "a"
// "b"
// ["c", "d", "e", "f"]
```

```js
const { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 };
console.log(x); // 1
console.log(y); // 2
console.log(z); // { a: 3, b: 4 }

const n = { x, y, ...z };
console.log(n); // { x: 1, y: 2, a: 3, b: 4 }
```

<a id="explanation-1"></a>

#### 说明

<a id="in-iterables-like-arrays"></a>

##### 应用于迭代 (如数组)

如果我们有以下两个数组:

```js
const arr1 = ["a", "b", "c"];
const arr2 = [arr1, "d", "e", "f"]; // [["a", "b", "c"], "d", "e", "f"]
```

*arr2* 的第一个元素是一个数组 ，因为 *arr1* 是被注入到 *arr2* 之中的。但我们真正想要得到的 *arr2* 是一个纯字母的数组。为了做到这点，我们可以将 *arr1* *展开(spread)* 到 *arr2*。

通过展开操作符：

```js
const arr1 = ["a", "b", "c"];
const arr2 = [...arr1, "d", "e", "f"]; // ["a", "b", "c", "d", "e", "f"]
```

<a id="function-rest-parameter"></a>

##### 函数剩余参数

在函数参数中，我们可以使用 rest 操作符将参数注入到我们可以循环的数组中。这里已经有一个 **argument** 对象绑定到每个函数上，等同于把数组中的所有参数都传递给函数。

```js
function myFunc() {
  for (var i = 0; i < arguments.length; i++) {
    console.log(arguments[i]);
  }
}

myFunc("Nick", "Anderson", 10, 12, 6);
// "Nick"
// "Anderson"
// 10
// 12
// 6
```

但是如果说，我们希望创造的是一个包含各科成绩和平均成绩的新学生。将前两个参数提取为两个单独的变量，并把剩下的元素生成一个可迭代的数组是不是更加方便呢？

这正是 rest 操作符允许我们做的事情！

```js
function createStudent(firstName, lastName, ...grades) {
  // firstName = "Nick"
  // lastName = "Anderson"
  // [10, 12, 6] -- "..." 将传递所有剩余参数，并创建一个包含它们的 "grades" 数组变量

  const avgGrade = grades.reduce((acc, curr) => acc + curr, 0) / grades.length; // 根据 grade 计算平均成绩

  return {
    firstName: firstName,
    lastName: lastName,
    grades: grades,
    avgGrade: avgGrade
  }
}

const student = createStudent("Nick", "Anderson", 10, 12, 6);
console.log(student);
// {
//   firstName: "Nick",
//   lastName: "Anderson",
//   grades: [10, 12, 6],
//   avgGrade: 9.333333333333334
// }
```

> **注意：** 在这个示例中， createStudent 函数其实并不太好，因为我们并没有去检查 grades.length 是否存在又或者它等于 0 的情况。但是这个例子现在这样写，能够更好的帮助我们理解剩余参数的运作，所以我没有处理上述的这种情况。

<a id="object-properties-spreading"></a>

##### 对象属性展开

对于这一点，我建议你阅读有关 rest 操作符以前的有关迭代和函数参数的相关说明。

```js
const myObj = { x: 1, y: 2, a: 3, b: 4 };
const { x, y, ...z } = myObj; // 这里是对象被解构
console.log(x); // 1
console.log(y); // 2
console.log(z); // { a: 3, b: 4 }

// z是对象解构后的剩余部分：myObj 对象除去 x 和 y 属性后剩余部分被解构

const n = { x, y, ...z };
console.log(n); // { x: 1, y: 2, a: 3, b: 4 }

// 这里 z 对象的属性展开到 n 中
```

<a id="external-resources"></a>

#### 扩展资源

- [TC39 - Object rest/spread](https://github.com/tc39/proposal-object-rest-spread)
- [Spread operator introduction - WesBos](https://github.com/wesbos/es6-articles/blob/master/28%20-%20Spread%20Operator%20Introduction.md)
- [JavaScript & the spread operator](https://codeburst.io/javascript-the-spread-operator-a867a71668ca)
- [6 Great uses of the spread operator](https://davidwalsh.name/spread-operator)

<a id="object-property-shorthand"></a>

### 对象属性简写

将变量分配给一个对象属性时，如果变量名称和属性名称相同，你可以执行以下操作：

```js
const x = 10;
const myObj = { x };
console.log(myObj.x) // 10
```

<a id="explanation-2"></a>

#### 说明

通常（ES2015之前）当你声明一个新的 *对象字面量* 并且想要使用变量作为对象属性值时，你会写这样类似的代码：

```js
const x = 10;
const y = 20;

const myObj = {
  x: x, // 将 x 分配给 myObj.x
  y: y // 将 y 变量给 myObj.y
};

console.log(myObj.x) // 10
console.log(myObj.y) // 20
```

如您所见，这样的作法其实相当重复，因为 myObj 的属性名称与要分配给这些属性的变量名相同。

使用ES2015，当变量名与属性名称相同时，您可以进行以下简写：

```js
const x = 10;
const y = 20;

const myObj = {
  x,
  y
};

console.log(myObj.x) // 10
console.log(myObj.y) // 20
```

<a id="external-resources-1"></a>

#### 扩展资源

- [Property shorthand - ES6 Features](http://es6-features.org/#PropertyShorthand)

<a id="promises"></a>

### Promises

Promises 是一个可以从异步函数 ([参考](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261#3cd0)) 同步返回的对象。

可以使用 Promises 来避免 [回调地狱 (callback hell)](http://callbackhell.com/) ，而且它们在现代 JavaScript 项目中越来越频繁地遇到。

<a id="sample-code-4"></a>

#### 简单的代码示例

```js
const fetchingPosts = new Promise((res, rej) => {
  $.get("/posts")
    .done(posts => res(posts))
    .fail(err => rej(err));
});

fetchingPosts
  .then(posts => console.log(posts))
  .catch(err => console.log(err));
```

<a id="explanation-3"></a>

#### 说明

当你在执行 *Ajax 请求* 时，响应不是同步的，因为资源请求需要时间。如果你要的资源由于某些原因 (404) 不可用，甚至可能永远都不会请求到。

为了处理这类情况，ES2015 为我们提供了 *promises*。 Promises 可以有三种不同的状态：

- 等待中 (Pending)
- 达成 (Fulfilled)
- 拒绝 (Rejected)

假设我们希望使用 promises 去进行 Ajax 请求以获取 X 资源。

<a id="create-the-promise"></a>

##### 创建 promise

我们首先要创建一个 promise。我们将会使用 jQuery 的 get 方法对 X 资源执行 Ajax 请求。

```js
const xFetcherPromise = new Promise( // 使用 "new" 关键字创建promise，并把它保存至一个变量
  function(resolve, reject) { // Promise 构造函数需要一个带有着 resolve 和 reject 这两个参数的函数作为参数
    $.get("X") // 执行 Ajax 请求
      .done(function(X) { // 一旦请求完成...
        resolve(X); // ... 把 X 值做为参数去 resolve promise
      })
      .fail(function(error) { // 如果请求失败...
        reject(error); // ... 把 error 做为参数去 reject promise
      });
  }
)
```

如上示例所示，Promise 对象需要一个带有两个参数 ( **resolve** 和 **reject** ) 的执行函数。这两个参数会把 *pending* 状态的 promise 分别进行 *fulfilled* 和 *rejected* 的处理。

Promise 在实例创建后处于待处理状态，并且它的执行器函数立即执行。一旦在执行函数中调用了 *resolve* 或 *reject* 函数，Promise 将调用相关的处理程序。

<a id="promise-handlers-usage"></a>

##### Promise 处理器的用法

为了获得 promise 结果（或错误），我们必须通过执行以下操作来附加处理程序：

```js
xFetcherPromise
  .then(function(X) {
    console.log(X);
  })
  .catch(function(err) {
    console.log(err)
  })
```


如果 promise 成功，则执行 *resolve* ，并执行 `.then` 参数所传递的函数。

如果失败，则执行 *reject* ，并执行 `.catch` 参数所传递的函数。

> **注意：** 如果 promise 在相应的处理程序附加时已经 *fulfilled* 或 *rejected*，处理程序将被调用，
因此在异步操作完成和其处理程序被附加之间没有竞争条件。 [(参考： MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#Description)（MDN）。

<a id="external-resources-2"></a>

#### 扩展阅读

- [JavaScript Promises for dummies - Jecelyn Yeen](https://scotch.io/tutorials/javascript-promises-for-dummies)
- [JavaScript Promise API - David Walsh](https://davidwalsh.name/promises)
- [Using promises - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)
- [What is a promise - Eric Elliott](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261)
- [JavaScript Promises: an Introduction - Jake Archibald](https://developers.google.com/web/fundamentals/getting-started/primers/promises)
- [Promise documentation - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

<a id="template-literals"></a>

### 模板字符串

模板字符串是一种单行和多行字符串的 [*表达式插值 (expression interpolation)*](https://en.wikipedia.org/wiki/String_interpolation)。

换句话说，它是一种新的字符串语法，你可以更方便地在 JavaScript 表达式中使用 (例如变量)。

<a id="sample-code-5"></a>

#### 简单的代码示例

```js
const name = "Nick";
`Hello ${name}, the following expression is equal to four : ${2+2}`;

// Hello Nick, the following expression is equal to four: 4
```

<a id="external-resources-3"></a>

#### 扩展阅读

- [String interpolation - ES6 Features](http://es6-features.org/#StringInterpolation)
- [ES6 Template Strings - Addy Osmani](https://developers.google.com/web/updates/2015/01/ES6-Template-Strings)

<a id="tagged-template-literals"></a>

### 带标签(tag)的模板字符串

模板标签是*可以作为[模板字符串(template literal)](#template-literals)的前缀函数*。当一个函数被这钟方式调用时，第一个参数是出现在模板插值变量之间的字符串数组，并且随后的参数是插值变量的值。可以使用展开运算符 `...` 捕获所有这些参数。  [(参考: MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#Tagged_template_literals)。

> **注意：** 名为[styled-components](https://www.styled-components.com/)的著名库很大程度上依赖于此功能。

以下是他们工作的玩具示例。

```js
function highlight(strings, ...values) {
  // 愚人码头注：为了更好的理解函数的参数，我增加了这样两行代码，特殊说明见示例代码下面的说明；
  console.log(strings);//(3) ["I like ", " on ", ".", raw: Array(3)]
  console.log(values);//(2) ["jam", "toast"]

  const interpolation = strings.reduce((prev, current) => {
    return prev + current + (values.length ? "<mark>" + values.shift() + "</mark>" : "");
  }, "");

  return interpolation;
}

const condiment = "jam";
const meal = "toast";

highlight`I like ${condiment} on ${meal}.`;
// "I like <mark>jam</mark> on <mark>toast</mark>."
```

-------愚人码头注开始-------

#### 愚人码头注，关于第一个参数：

标签函数的第一个参数是一个包含了字符串字面值的数组（在本例中分别为"I like "," on "和"."）。如果我们这样调用 **highlight\`I like ${condiment} on ${meal}\`** (注意最后面没".")，那么第一个参数还是一个 3 个元素的数组：["I like ", " on ", ""]，特别注意最后一个元素是的空字符串""；

##### 字符串的 raw 属性

`strings` 确实是一个数组，但是它还有一个 `raw` 属性。其属性值 `strings.raw` 也是一个数组，其元素分别表示 `strings`  中对应的，经过转义之前在 模板字符串(Template literals) 中由用户输入的字符串。我们来看一个例子：

```js
const myTag = (strs, ...exprs) => {
    console.log(strs);                  //(3) ["x", "\y", "", raw: Array(3)]
    console.log(strs.raw);              //(3) ["x", "\\y", ""
    console.log(exprs);                 //[1, 2]
};

const obj = { a: 1, b: 2 };
const result = myTag`x${obj.a}\\y${obj.b}`;
```

上例中 `"\y"` 未转义之前对应的字符串为 `"\\y"` ，显然这两个字符串长度是不同的。

`String.raw` 是ES2015，内置对象 `String` 的一个静态方法，把它作为Tag，可以做到只替换嵌入表达式而不转义字符。

```js
const raw = String.raw`1\\2\\${1+2}`;

console.log(raw);           //1\\2\\3
console.log(raw.length);    //7

const x = `1\\2\\${1+2}`;
console.log(x);             //1\2\3
console.log(x.length);      //5
```

###### 规避问题 

Template literals遵从字符串的转义规则：

（1）以 `\u` 开头，后跟4个16进制数字，例如，`\u00B1`表示`±`
（2）以 `\u` 开头，使用大括号括起来的16进制数字，例如，`\u{2F804}` 表示 `你`
（3）以 `\x` 开头，后跟2个16进制数字，例如，`\xB1` 表示 `±`
（4）以 `\` 开头，后跟10进制数字，用来表示八进制字面量（注：strict mode下不支持）

解释器遇到 `\u` 和 `\x` ，如果发现后面的字符不满足以上条件，就会报语法错。例如，

```js
> latex`\unicode`
> Uncaught SyntaxError: Invalid Unicode escape sequence
```

不再展开，具体参考:[Template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#Tagged_template_literals)。


#### 愚人码头注，关于后面的剩余参数：

在第一个参数后的每一个参数，都是已经求值后的替换表达式。 看下面这个例子：

```js
var a = 5;
var b = 10;
function tag(strings, ...values) {
  console.log(values[0]);      // 15
  console.log(values[1]);      // 50

  return values[0]+values[1];  //65
}

tag`Hello ${ a + b } world ${ a * b}`;
```

上例中，剩余的2个参数值分别是 `15` 和 `50`;

-------愚人码头注结束-------

一个更有趣的例子：

```js
function comma(strings, ...values) {
  return strings.reduce((prev, next) => {
    let value = values.shift() || [];
    value = value.join(", ");
    return prev + next + value;
  }, "");
}

const snacks = ['apples', 'bananas', 'cherries'];
comma`I like ${snacks} to snack on.`;
// "I like apples, bananas, cherries to snack on."
```

<a id="external-resources-4"></a>

#### 扩展阅读

- [Wes Bos on Tagged Template Literals](http://wesbos.com/tagged-template-literals/)
- [Library of common template tags](https://github.com/declandewet/common-tags)

<a id="imports--exports"></a>

### ES6 模块的导入 / 导出 (imports / exports)

ES6模块用于访问模块中显式导出的模块中的变量或函数。

我强烈建议您查看 MDN 上有关 import/export（请参阅下面的扩展阅读资源），它们写的既简洁又完整。

<a id="explanation-with-sample-code-1"></a>

#### 用示例代码说明

<a id="named-exports"></a>

##### 命名导出

命名导出用于从一个模块导出多个值。

> **注意：** 您命名导出的变量是[一等公民(first-class citizens)](https://en.wikipedia.org/wiki/First-class_citizen)。

```js
// mathConstants.js
export const pi = 3.14;
export const exp = 2.7;
export const alpha = 0.35;

// -------------

// myFile.js
import { pi, exp } from './mathConstants.js'; // 命名导入 -- 类似于解构语法
console.log(pi) // 3.14
console.log(exp) // 2.7

// -------------

// mySecondFile.js
import * as constants from './mathConstants.js'; // 将所有导出的值注入到 constants 变量中
console.log(constants.pi) // 3.14
console.log(constants.exp) // 2.7
```

虽然命名导入看起来像是 *解构(destructuring)*，但它们具有不同的语法，并且不一样。 他们不支持默认值，也不支持深层次的解构。

此外，您可以使用别名，但语法不同于解构中使用的语法：

```js
import { foo as bar } from 'myFile.js'; // foo 被导入并注入到一个新的 bar 变量中
```

<a id="default-import--export"></a>

##### 默认导入 / 导出 (imports / exports)

关于默认导出，每个模块只能有一个默认导出。默认导出可以是函数，类，对象或其他任何东西。这个值被认为是“主要”的导出值，因为它将是最简单的导入。 [参考： MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export#Description)。

```js
// coolNumber.js
const ultimateNumber = 42;
export default ultimateNumber;

// ------------

// myFile.js
import number from './coolNumber.js';
// 默认导出，将独立于其名称，自动注入到 number 这个变量; 
console.log(number) // 42
```

函数导出：

```js
// sum.js
export default function sum(x, y) {
  return x + y;
}
// -------------

// myFile.js
import sum from './sum.js';
const result = sum(1, 2);
console.log(result) // 3
```

<a id="external-resources-5"></a>

#### 扩展阅读

- [ECMAScript 6 Modules(模块)系统及语法详解](http://www.css88.com/archives/6974)
- [ES6 Modules in bulletpoints](https://ponyfoo.com/articles/es6#modules)
- [Export - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export)
- [Import - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)
- [Understanding ES6 Modules](https://www.sitepoint.com/understanding-es6-modules/)
- [Destructuring special case - import statements](https://ponyfoo.com/articles/es6-destructuring-in-depth#special-case-import-statements)
- [Misunderstanding ES6 Modules - Kent C. Dodds](https://medium.com/@kentcdodds/misunderstanding-es6-modules-upgrading-babel-tears-and-a-solution-ad2d5ab93ce0)
- [Modules in JavaScript](http://exploringjs.com/es6/ch_modules.html#sec_modules-in-javascript)

<a id="-javascript-this"></a>

### <a name="this_def"></a> JavaScript 中的 *this*

*this* 操作符的行为与其他语言不同，在大多数情况之下是由函数的调用方式决定。 ([参考： MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this))。

*this* 概念有很多细节，并不是那么容易理解，我强烈建议你深入了解下面的扩展阅读。因此，我会提供我个人对于 *this* 的一点理解和想法。我是从 [Yehuda Katz 写的这篇文章](http://yehudakatz.com/2011/08/11/understanding-javascript-function-invocation-and-this/) 学到了这个提示。

```js
function myFunc() {
  ...
}

// 在每个述句后面，你都可以在 myFunc 中找到 this 的值

myFunc.call("myString", "hello") // "myString" -- 首先， .call的参数值被注入到 *this*

// 在非严格模式下（non-strict-mode）
myFunc("hello") // window -- myFunc() 是 myFunc.call(window, "hello") 的语法糖

// 在严格模式下（strict-mode）
myFunc("hello") // undefined -- myFunc() 是 myFunc.call(undefined, "hello") 的语法糖
```

```js
var person = {
  myFunc: function() { ... }
}

person.myFunc.call(person, "test") // person 对象 -- 首先， .call的参数值被注入到 *this*
person.myFunc("test") // person 对象 -- person.myFunc() 是  person.myFunc.call(person, "test") 的语法糖

var myBoundFunc = person.myFunc.bind("hello") // 创造了一个函数，并且把 "hello" 注入到 *this* 
person.myFunc("test") // person 对象 -- bind 方法对原有方法并无造成影响
myBoundFunc("test") // "hello" -- myBoundFunc 是把带有 "hello" 的 person.myFunc 绑定到 *this*
```
<a id="external-resources-6"></a>

#### 扩展阅读

- [Understanding JavaScript Function Invocation and "this" - Yehuda Katz](http://yehudakatz.com/2011/08/11/understanding-javascript-function-invocation-and-this/)
- [JavaScript this - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)

<a id="class"></a>

### 类(Class)

JavaScript 是一个[基于原型](https://en.wikipedia.org/wiki/Prototype-based_programming) 的语言(然而Java 是[基于类别](https://en.wikipedia.org/wiki/Class-based_programming ) 的语言)。 ES6 引入了 JavaScript 类，它们是用于基于原型的继承的语法糖，而 **不是** 一种新的基于类继承的模型([参考](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)).

如果您熟悉其他语言的类，那么 *类 (class)* 这个词的确容易理解出错。 如果真的有此困扰，请避免在这样的认知下思考 JavaScript 类的行为，并将其视为完全不同的新概念。

由于本文档不是从根本上教你 JavaScript 语言，我会相信你知道什么是原型，以及它们的行为。 如果没有，请参阅示例代码下面列出的扩展阅读，以方便你去理解这些概念：

- [Understanding Prototypes in JS - Yehuda Katz](http://yehudakatz.com/2011/08/12/understanding-prototypes-in-javascript/)
- [A plain English guide to JS prototypes - Sebastian Porto](http://sporto.github.io/blog/2013/02/22/a-plain-english-guide-to-javascript-prototypes/)
- [Inheritance and the prototype chain - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

<a id="samples"></a>

#### 简单的示例

ES6 之前，原型語法:

```js
var Person = function(name, age) {
  this.name = name;
  this.age = age;
}
Person.prototype.stringSentence = function() {
  return "Hello, my name is " + this.name + " and I'm " + this.age;
}
```

使用 ES6 类(class)* 语法:

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  stringSentence() {
    return "Hello, my name is " + this.name + " and I'm " + this.age;
  }
}

const myPerson = new Person("Manu", 23);
console.log(myPerson.age) // 23
console.log(myPerson.stringSentence()) // "Hello, my name is Manu and I'm 23
```

<a id="external-resources-7"></a>

#### 扩展阅读

更好的理解原型：

- [Understanding Prototypes in JS - Yehuda Katz](http://yehudakatz.com/2011/08/12/understanding-prototypes-in-javascript/)
- [A plain English guide to JS prototypes - Sebastian Porto](http://sporto.github.io/blog/2013/02/22/a-plain-english-guide-to-javascript-prototypes/)
- [Inheritance and the prototype chain - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

更好的理解类：

- [ES6 Classes in Depth - Nicolas Bevacqua](https://ponyfoo.com/articles/es6-classes-in-depth)
- [ES6 Features - Classes](http://es6-features.org/#ClassDefinition)
- [JavaScript Classes - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

<a id="extends-and-super-keywords"></a>

### `Extends` 和 `super` 关键字

`extends` 关键字用于类声明或类表达式中，以创建一个类，该类是另一个类的子类([参考: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/extends))。 子类继承超类的所有属性，另外可以添加新属性或修改继承的属性。

`super` 关键字用于调用对象的父对象的函数，包括其构造函数。

- `super` 关键字必须在构造函数中使用 `this` 关键字之前使用。
- 调用 `super()` 调用父类构造函数。 如果要将类的构造函数中的一些参数传递给其父构造函数，则可以使用 `super(arguments)` 来调用它。
- 如果父类有一个 `X` 的方法（甚至静态），可以使用 `super.X()` 在子类中调用。

<a id="sample-code-6"></a>

#### 简单的代码示例

```js
class Polygon {
  constructor(height, width) {
    this.name = 'Polygon';
    this.height = height;
    this.width = width;
  }

  getHelloPhrase() {
    return `Hi, I am a ${this.name}`;
  }
}

class Square extends Polygon {
  constructor(length) {
    // 这里，它调用父类的构造函数的 length, 
    // 提供给 Polygon 的 width 和 height。
    super(length, length);
    // 注意: 在派生的类中, 在你可以使用 'this' 之前, 必须先调用 super() 。
    // 忽略这个, 这将导致引用错误。
    this.name = 'Square';
    this.length = length;
  }

  getCustomHelloPhrase() {
    const polygonPhrase = super.getHelloPhrase(); // 通过 super.X() 语法访问父级方法
    return `${polygonPhrase} with a length of ${this.length}`;
  }

  get area() {
    return this.height * this.width;
  }
}

const mySquare = new Square(10);
console.log(mySquare.area) // 100
console.log(mySquare.getHelloPhrase()) // 'Hi, I am a Square' -- Square 继承自 Polygon 并可以访问其方法
console.log(mySquare.getCustomHelloPhrase()) // 'Hi, I am a Square with a length of 10'
```

**注意 :** 如果我们在 Square 类中调用 `super()` 之前尝试使用 `this`，将引发一个引用错误：

```js
class Square extends Polygon {
  constructor(length) {
    this.height; // 引用错误,  必须首先调用 super() !

    // 这里，它调用父类的构造函数的 length, 
    // 提供给 Polygon 的 width 和 height。
    super(length, length);

    // 注意: 在派生的类中, 在你可以使用 'this' 之前, 必须先调用 super() 。
    // 忽略这个, 这将导致引用错误。
    this.name = 'Square';
  }
}
```

<a id="external-resources-8"></a>

#### 扩展阅读

- [Extends - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/extends)
- [Super operator - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/super)
- [Inheritance - MDN](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Inheritance)

<a id="external"></a>

### 异步和等待(Async Await)

除 [promises](#promises) 之外，还有一种新的语法可能会遇到，那就是异步的 *async / await*。

async / await 函数的目的是简化同步使用 promise 的行为，并对一组 promises 执行一些处理。正如 promises 类似于结构化的回调，async / await 类似于组合生成器(combining generators) 和 promises。异步函数 *总是* 返回一个 Promise。 ([参考: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function))

> **注意：** 您必须了解什么是 promises 以及它们是如何工作的，然后再尝试了解 async / await ，因为它们依赖于 promises 。
> **注意2：** [*await* 必须在*async*函数中使用](https://hackernoon.com/6-reasons-why-javascripts-async-await-blows-promises-away-tutorial- c7ec10518dd9#f3f0)，这意味着你不能程式码的顶部使用 *await*，因为它并不在异步函数之内。

<a id="sample-code-7"></a>

#### 简单的代码示例

```js
async function getGithubUser(username) { // async 关键字允许在函数中使用 await ，意味着函数返回一个 promise 
  const response = await fetch(`https://api.github.com/users/${username}`); // 执行在这里暂停，直到fetch返回的 Promise 被 resolved 
  return response.json();
}

getGithubUser('mbeaudru')
  .then(user => console.log(user)) // 记录用户响应 - 不能使用 await 语法，因为此代码不在 async 函数中 
  .catch(err => console.log(err)); // 如果在我们的异步函数中抛出一个错误，我们将在这里捕获它 
```

<a id="explanation-with-sample-code-2"></a>

#### 用示例代码说明

*Async / Await* 是建立在 promises 概念之上的，但它们允许更强制的代码风格。

*async* 操作符将一个函数标记为异步，并将始终返回一个 *Promise* 。你可以在 *async* 函数中使用 *await* 操作符来暂停该行代码的执行，直到表达式中返回的 Promise resolves 或 rejects 。

```js
async function myFunc() {
  // 我们可以使用 *await* 操作符 因为这个函数是 异步(async) 的 
  return "hello world";
}

myFunc().then(msg => console.log(msg)) // "hello world" -- 由于 async 操作符，myFunc 的返回值将变成了一个 promise 
```

当异步函数运行到 *return* 语句时，将会使用返回的值来 fulfilled Promise。 如果在 async 函数中抛出错误，则 Promise 状态将转为 *rejected* 。 如果没有从 async 函数返回任何值，则在执行 async 函数完成时，仍然会返回 Promise 并 resolves 为无值。

*await*  操作符用于等待 *Promise* fulfilled ，只能在  *async* 函数体内使用。 遇到这种情况时，代码执行将暂停，直到 promise fulfilled。

> **注意：** *fetch* 是一个允许执行 AJAX 请求，返回一个 Promise 的函数。

首先，我们来看看如何通过 promises 来获取一个 github 用户：

```js
function getGithubUser(username) {
  return fetch(`https://api.github.com/users/${username}`).then(response => response.json());
}

getGithubUser('mbeaudru')
  .then(user => console.log(user))
  .catch(err => console.log(err));
```

等价于这里 *async / await* :

```js
async function getGithubUser(username) { // promise + await 关键字使用允许
  const response = await fetch(`https://api.github.com/users/${username}`); // 在此处执行停止，直到 promise 获得 fulfilled
  return response.json();
}

getGithubUser('mbeaudru')
  .then(user => console.log(user))
  .catch(err => console.log(err));
```

当你需要链接(chain)相互依赖的 promises 时，*async / await* 语法特别方便 。

例如，如果您需要获取一个令牌(token) ，以便能够在数据库上获取博客文章，然后获取作者信息：

> **注意：** *await* 表达式需要包含在括号中，这样可以在同一行上调用其 resolved 值的方法和属性。

```js
async function fetchPostById(postId) {
  const token = (await fetch('token_url')).json().token;
  const post = (await fetch(`/posts/${postId}?token=${token}`)).json();
  const author = (await fetch(`/users/${post.authorId}`)).json();

  post.author = author;
  return post;
}

fetchPostById('gzIrzeo64')
  .then(post => console.log(post))
  .catch(err => console.log(err));
```

<a id="error-handling"></a>

##### 错误处理

除非我们在 *await* 表达式外面包裹 *try / catch* 语句块，否则不会捕获异常 - 不管它们是在你的异步函数中被抛出还是在 *await* 期间被暂停 - 他们将 reject *async* 函数返回的承诺。
在 *async* 函数中使用 `throw` 语句与返回 reject 的 Promise 是相同。 [(参考: PonyFoo)](https://ponyfoo.com/articles/understanding-javascript-async-await#error-handling).

> **Note :** Promises 的行为相同的!

下面是的示例显示了 promises 是如何处理错误链的:

```js
function getUser() { // 这个 promise 将被 rejected!
  return new Promise((res, rej) => rej("User not found !"));
}

function getAvatarByUsername(userId) {
  return getUser(userId).then(user => user.avatar);
}

function getUserAvatar(username) {
  return getAvatarByUsername(username).then(avatar => ({ username, avatar }));
}

getUserAvatar('mbeaudru')
  .then(res => console.log(res))
  .catch(err => console.log(err)); // "User not found !"
```

等价于实用 *async / await* ：

```js
async function getUser() { // 这个 promise 将被 rejected!
  throw "User not found !";
}

async function getAvatarByUsername(userId) => {
  const user = await getUser(userId);
  return user.avatar;
}

async function getUserAvatar(username) {
  var avatar = await getAvatarByUsername(username);
  return { username, avatar };
}

getUserAvatar('mbeaudru')
  .then(res => console.log(res))
  .catch(err => console.log(err)); // "User not found !"
```

<a id="external-resources-9"></a>

#### 扩展阅读

- [使用 ES2017 中的 Async(异步) 函数 和 Await(等待)](http://www.css88.com/archives/7980)
- [ES2017 新特性：Async Functions (异步函数)](http://www.css88.com/archives/7731)
- [Async/Await - JavaScript.Info](https://javascript.info/async-await)
- [ES7 Async/Await](http://rossboucher.com/await/#/)
- [6 Reasons Why JavaScript’s Async/Await Blows Promises Away](https://hackernoon.com/6-reasons-why-javascripts-async-await-blows-promises-away-tutorial-c7ec10518dd9)
- [JavaScript awaits](https://dev.to/kayis/javascript-awaits)
- [Using Async Await in Express with Node 8](https://medium.com/@Abazhenov/using-async-await-in-express-with-node-8-b8af872c0016)
- [Async Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- [Await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)
- [Using async / await in express with node 8](https://medium.com/@Abazhenov/using-async-await-in-express-with-node-8-b8af872c0016)

<a id="truthy--falsy"></a>

### 真值/假值(Truthy / Falsy)

在 JavaScript 中，truthy 或 falsy 值是在布尔上下文中求值时被转换为布尔值的值。布尔上下文的一个最常见的例子是求值 `if` 条件：

每个值将被转换为`true`，除非它们等于以下值：

- `false`
- `0`
- `""` (空字符串)
- `null`
- `undefined`
- `NaN`

下面是 *布尔上下文(boolean context)* 的例子：

- `if` 条件求值

```js
if (myVar) {}
```

`myVar` 可以是任何 [一等公民(first-class citizen)](https://en.wikipedia.org/wiki/First-class_citizen) (变量, 函数, 布尔值) ，但它会被转换成一个布尔值，因为它会在布尔上下文中进行就值。

- 逻辑**非** `!` 操作符后面

如果其单独的操作数可以转换为 `true` ，则此操作符返回 `false` ; 否则返回 `true` 。

```js
!0 // true -- 0 是 falsy(假) 值，所以它返回 true
!!0 // false -- 0 是 falsy(假) 值， 所以 !0 返回 true ， 所以 !(!0) 返回 false
!!"" // false -- 空字符串是 falsy(假) 值， 所以 NOT (NOT false) 等于 false
```

- 通过 *Boolean* 对象构造函数

```js
new Boolean(0) // false
new Boolean(1) // true
```

- 在一个三元表达式求值时

```js
myVar ? "truthy" : "falsy"
```

myVar 在布尔上下文中进行求值。

<a id="external-resources-10"></a>

#### 扩展阅读

- [Truthy (MDN)](https://developer.mozilla.org/en-US/docs/Glossary/Truthy)
- [Falsy (MDN)](https://developer.mozilla.org/en-US/docs/Glossary/Falsy)
- [Truthy and Falsy values in JS - Josh Clanton](http://adripofjavascript.com/blog/drips/truthy-and-falsy-values-in-javascript.html)

<a id="static-methods"></a>

### 静态方法

<a id="short-explanation-1"></a>

#### 简单说明

`static` 关键字用于声明静态方法。静态方法是属于 class(类) 对象，而该类的任何实例都不可以访问的方法。

<a id="sample-code-8"></a>

#### 简单的代码示例

```js
class Repo{
  static getName() {
    return "Repo name is modern-js-cheatsheet"
  }
}

// 请注意，我们不必创建 Repo 类的实例 
console.log(Repo.getName()) //Repo name is modern-js-cheatsheet

let r = new Repo();
console.log(r.getName()) // 抛出一个 TypeError: repo.getName is not a function
```

<a id="detailed-explanation-2"></a>

#### 详细说明

静态方法可以通过使用 `this` 关键字在另一个静态方法中调用，这不适用于非静态方法。非静态方法无法使用 `this` 关键字直接访问静态方法。

<a id="calling-other-static-methods-from-a-static-method"></a>

##### 在静态方法调用另一个静态方法。

要在在静态方法调用另一个静态方法，可以使用 `this` 关键字 ，像这样;

```js
class Repo{
  static getName() {
    return "Repo name is modern-js-cheatsheet"
  }

  static modifyName(){
    return this.getName() + '-added-this'
  }
}

console.log(Repo.modifyName()) //Repo name is modern-js-cheatsheet-added-this
```

<a id="calling-static-methods-from-non-static-methods"></a>

##### 在非静态方法调用静态方法。

非静态方法可以通过2种方式调用静态方法;

1. ###### 使用 class(类) 名

要在非静态方法访问静态方法，我们可以使用类名，并像属性一样调用静态方法就可以了。 例如`ClassName.StaticMethodName`：

```js
class Repo{
  static getName() {
    return "Repo name is modern-js-cheatsheet"
  }

  useName(){
    return Repo.getName() + ' and it contains some really important stuff'
  }
}

// 我们需要实例化这个 class(类)，以使用非静态方法
let r = new Repo()
console.log(r.useName()) //Repo name is modern-js-cheatsheet and it contains some really important stuff
```

2. ###### 实用构造函数

静态方法可以在构造函数对象上作为属性被调用。

```js
class Repo{
  static getName() {
    return "Repo name is modern-js-cheatsheet"
  }

  useName(){
    //作为构造函数的属性来调用静态方法
    return this.constructor.getName() + ' and it contains some really important stuff'
  }
}

// 我们需要实例化这个 class(类)，以使用非静态方法 
let r = new Repo()
console.log(r.useName()) //Repo name is modern-js-cheatsheet and it contains some really important stuff
```

<a id="external-resources-11"></a>

#### 扩展阅读

- [static keyword- MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/static)
- [Static Methods- Javascript.info](https://javascript.info/class#static-methods)
- [Static Members in ES6- OdeToCode](http://odetocode.com/blogs/scott/archive/2015/02/02/static-members-in-es6.aspx)

<a id="glossary"></a>

## 词汇表

<a id="-scop"></a>

### <a name="scope_def"></a> 作用域(Scope)

在上下文之中有着 "可见的 (visible)" 值和表达式，又或者是可以被引用的。如果变量或是表达式并不在 "当前作用域中"，那么它将会是不可用的。

来源: [MDN](https://developer.mozilla.org/en-US/docs/Glossary/Scope)

<a id="-variable-mutation"></a>

### <a name="mutation_def"></a> 变量的可变性(Variable mutation)

如果变量在其初始值后发生变化时我们就称其为可变的。

```js
var myArray = [];
myArray.push("firstEl") // myArray 发生改变
```

如果一个变量不能被改变的话，我们会说这个变量是 *不可变的 (immutable)* 。

[查看 MDN Mutable 文章](https://developer.mozilla.org/en-US/docs/Glossary/Mutable) 了解更多详情。

原项目：<a href="https://github.com/mbeaudru/modern-js-cheatsheet" target="_blank">Modern JavaScript Cheatsheet </a>

## 推荐阅读最新关于 ECMAScript 的文章

<ul>
<li><a href="http://www.css88.com/archives/6200" target="_blank">ECMAScript 2015（ES6）的十大特征</a></li>
<li><a href="http://www.css88.com/archives/6533" target="_blank">JavaScript ES6（ES2015）入门-核心特性概述</a></li>
<li><a href="http://www.css88.com/archives/7240" target="_blank">ES6 新特性范例大全</a></li>
<li><a href="http://www.css88.com/archives/7291" target="_blank">现在就可以使用的5个 ES6 特性</a></li>
<li><a href="http://www.css88.com/archives/7383" target="_blank">面向对象的 JavaScript – 深入了解 ES6 类</a></li>
<li><a href="http://www.css88.com/archives/7980" target="_blank">使用 ES2017 中的 Async(异步) 函数 和 Await(等待)</a></li>
<li><a href="http://www.css88.com/archives/8189" target="_blank">JavaScript ECMAScript 2015 (ES6) 和 ECMAScript 2016 (ES7) 新特性速查表</a></li>
<li><a href="http://www.css88.com/archives/6974" target="_blank">ECMAScript 6 Modules(模块)系统及语法详解</a></li>
<li><a href="http://www.css88.com/archives/6963" target="_blank">学习 ES2015 新特性</a></li>
<li><a href="http://www.css88.com/archives/7395" target="_blank">JavaScript ES2015 中对象继承的模式</a></li>
<li><a href="http://www.css88.com/archives/7753" target="_blank">JavaScript 新书：探索 ES2016 与 ES2017</a>(包含了ES2016 与 ES2017 的最新特性)</li>
</ul>

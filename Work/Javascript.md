# A NOTE FOR JAVASCRIPT

2022/04/25  [JavaScript 基础入门_JavaScript - 蓝桥云课 (lanqiao.cn)](https://www.lanqiao.cn/courses/1238) 

## [ Javascript 基础 ]

> JavaScript，通常缩写为 JS，是一种高级的，解释执行的编程语言。JavaScript 是一门基于原型、函数先行的语言，是一门多范式的语言，它支持面向对象编程，命令式编程，以及函数式编程。它提供语法来操控文本、数组、日期以及正则表达式等，不支持 I/O，比如网络、存储和图形等，但这些都可以由它的宿主环境提供支持。它已经由 ECMA（欧洲计算机制造商协会）通过 ECMAScript 实现语言的标准化。它被世界上的绝大多数网站所使用，也被世界主流浏览器（Chrome、IE、Firefox、Safari、Opera）支持。
>
> 虽然 JavaScript 与 Java 这门语言不管是在名字上，或是在语法上都有很多相似性，但这两门编程语言从设计之初就有很大的不同，JavaScript 的语言设计主要受到了 Self（一种基于原型的编程语言）和 Scheme（一门函数式编程语言）的影响。在语法结构上它又与 C 语言有很多相似，例如 if 条件语句、while 循环、switch 语句、do-while 循环等。
>
> 在客户端，JavaScript 在传统意义上被实现为一种解释语言，但在最近，它已经可以被即时编译（JIT）执行。随着最新的 HTML5 和 CSS3 语言标准的推行，它还可用于游戏、桌面和移动应用程序的开发和在服务器端网络环境运行，如 Node.js。

**JavaScript 的组成**

- ECMAScript：JavaScript 的语法标准。
- DOM：JavaScript 操作网页上的元素的 API。
- BOM：JavaScript 操作浏览器的部分功能的 API。

**JavaScript 的特点**

- 可以使用任何文本编辑工具编写，然后使用浏览器就可以执行程序。
- 是一种解释型脚本语言：代码不进行预编译，从上往下逐行执行，不需要进行严格的变量声明。
- 主要用来向 HTML 页面添加交互行为。

### 基本规则

**变量命名规则**

- 变量名必须以字母、下划线 “_”、美元符号 “$” 开头，不能以数字开头。
- 变量可以包含字母、数字、下划线和美元符号。
- 不能使用 JavaScript 中的关键字做为变量名。
- 变量名不能有空格。
- 变量名对大小写敏感，比如：name 和 Name 就是两个完全不同的变量。

**运算符的优先级**

<img src="https://doc.shiyanlou.com/document-uid897174labid9222timestamp1547261443500.png" alt="img" style="zoom: 80%;" />

### 数组  Array 

- `length` 用来获取数组的长度。

- 通过 `split()` 方法，将字符串转换为数组。 相反的我们通过 `join()` 方法将数组转换为字符串。 

  ```javascript
  "1:2:3:4".split(":"); // returns ["1", "2", "3", "4"]
  ["1", "2", "3", "4"].join(":"); // returns "1:2:3:4"
  ```

- 在数组尾部添加一个或多个元素，使用 `push()` 方法。使用 `pop()` 方法将删除数组的最后一个元素，把数组长度减 1，并且返回它删除的元素的值。如果数组已经为空，则 `pop()` 不改变数组，然后返回 undefined 值。

  ```javascript
  var arr = ["1", "2", "3", "4"];
  arr.push("5", "6");
  arr; // returns ["1", "2", "3", "4", "5", "6"]
  arr.pop(); // returns 6
  arr; // returns ["1", "2", "3", "4", "5"]
  ```

- `unshift()` 和 `shift()` 从功能上与 `push()` 和 `pop()` 完全相同，只是它们分别作用于数组的开始，而不是结尾。 

### 字符串

**常用的转义符**

![img](https://doc.shiyanlou.com/document-uid897174labid9222timestamp1547519780285.png)

**字符串方法**

- 连接字符串 `+`

- 字符串转换：`toString()`、`Number()`

- 获取字符串的长度 `length`

- 判断是否存在切片  `indexof()`

  ```javascript
  "Blue Sky".indexOf("Sky", 0); // returns  5
  ```

   注：返回值指的是指定值第一次出现的索引，如果没有找到返回 -1。且`indexOf()` 方法区分大小写。

- `slice()`  可以提取切片

  ```javascript
  "Blue Sky".slice(0, 3); // returns "Blu"
  ```

  提取从第一个位置开始，直到但不包括最后一个位置。另外第二个参数也可以不写，不写代表某个字符之后提取字符串中的所有剩余字符。 

-  `toLowerCase()` 和 `toUpperCase()` 将所有字符分别转换为小写或大写并返回。 

-  `replace()` 方法可以将字符串中的一个子字符串替换为另一个子字符串。 

  ```javascript
  var string = "I like study";
  string.replace("study", "sleep"); // returns "I like sleep"
  // 这样只能替换第一个出现的字符串，若想替换多个可以使用全局替换方法 
  var string = "I like study study";
  string.replace(/study/g, "sleep");
  ```

### 值转换

**转换成字符串**

1. 几乎每个值都有 `toString()` 方法。数值类型的 `toString()`，可以携带一个参数，输出对应进制的值。 

2. `String()` 函数。有的值没有 `toString()` 方法，所以需要用 `String()`，比如 null 和 undefined。 

3. 使用拼接字符串。 

   ```javascript
   num.toString();
   num.toString(10);
   num2 = num1 + "";
   ```

**转换成数值类型** 

1. `Number()` 可以把任意值转换成数值，如果要转换的字符串中有一个不是数值的字符，返回 NaN（not a number）。 

2. `parseInt()` 把字符串转换成整数。如果第一个字符是数字会解析直到遇到非数字结束，只取整，不是约等于 。另外 `parseInt()` 可以传递两个参数，第一个参数是要转换的字符串，第二个参数是要转换的进制。 

3. parseFloat()` 把字符串转换成浮点数。写法和 `parseInt()` 相似，主要有以下几个不同点：

   - parseFloat 不支持第二个参数，只能解析 10 进制数。

   - 如果解析的内容里只有整数，解析成整数。

4. 执行减 0 操作。 值得注意的是，如果该字符串不是纯粹的数字字符串，那么它执行减 0 操作后，虽然变成了一个数字类型，但是返回值为 NaN。 

**转换成布尔类型** 

1. 使用 `Boolean()` 函数。 
2. 流程控制语句会把后面的值隐式转换为布尔类型。 

**Null和Undefined**

null 和 undefined 的值不等于 0，它们的值相等，但是类型不相等。undefined 表示所有没有赋值变量的默认值，而 null 则表示一个变量不再指向任何对象地址。 

## [ JavaScript 关键特性 ]

### 条件

**if...else 语句**

```javascript
if (条件) {
  // 当条件为 true 时执行的语句
} else {
  // 当条件为 false 时执行的语句
}

if(条件 1){
    // 当条件 1 为 true 时执行的代码
    }
else if(条件 2){
    // 当条件 2 为 true 时执行的代码
    }
else{
    // 当条件 1 和 条件 2 都不为 true 时执行的代码
    }
```

**switch case 语句**

```javascript
switch(k){
    case 1:
        执行代码块 1 ;
        break;
    case 2:
        执行代码块 2 ;
        break;
    default:
        默认执行（k 值没有在 case 中找到匹配时）;
}
```

**三元运算符**

```javascript
条件表达式？结果 1:结果 2
```

### 循环 

**for 循环**

```javascript
for (初始化; 条件; 增量) {
  循环代码;
  break; // 跳出循环
  continue; // 跳过当前循环去执行下一个循环
}
```

**while 语句**

```javascript
while (条件) {
  // 需要执行的代码;
}
// while 循环，先判断再执行；do while 循环先执行一次再判断
do {
  // 需要执行的代码;
} while (条件);
```

### 递归 

在程序中，递归就是函数自己直接或者间接的调用自己。 

注：一定要写临界条件，不然程序无法结束并且会报错。 

### 函数

函数是被设计为执行特定任务的代码块，可重复调用执行。 

#### 创建函数 

**函数声明创建函数**

```javascript
function functionName(parameters) {
  // 执行的代码
}
```

**函数表达式创建函数**

```javascript
var functionName = function (parameters) {
  // 执行的代码
};
```

**函数声明和函数表达式的区别**

```javascript
// 此处的代码执行没有问题，JavaScript 解析器首先会把当前作用域的函数声明提前到整个作用域的最前面。
f(2, 3);

function f(a, b) {
  console.log(a + b);
}
// 报错：f is not a function
// 这是因为函数表达式，如同定义其它基本类型的变量一样，只在执行到某一句时也会对其进行解析

f(2, 3);

var f = function (a, b) {
  console.log(a + b);
};
```

#### 函数的参数

- 形参：`function f(a, b){return a + b;} // a, b 是形参`，占位用，函数定义时形参无值。
- 实参：当我们调用上面的函数时比如 `f(2, 3);`其中 2 和 3 就是实参，会传递给 a 和 b，最后函数中执行的语句就变成了：`return 2 + 3;`。

注：在 JavaScript 中，实参个数和形参个数可以不相等。

#### Javascript中的函数

**在 JavaScript 中没有重载**

```javascript
function f(a, b) {
  return a + b;
}
function f(a, b, c) {
  return a + b + c;
}
var result = f(5, 6);
result; // returns NaN
```

**在 JavaScript 中函数的返回值**

- 如果函数中没有 `return` 语句，那么函数默认的返回值是：undefined。
- 如果函数中有 `return` 语句，那么跟着 `return` 后面的值就是函数的返回值。
- 如果函数中有 `return` 语句，但是 `return` 后面没有任何值，那么函数的返回值也是：undefined。
- 函数在执行 `return` 语句后会停止并立即退出，也就是说 `return` 语句执行之后，剩下的代码都不会再执行了。
- 当函数外部需要使用函数内部的值的时候，我们不能直接给予，需要通过 `return` 返回。

#### 匿名函数

匿名函数就是没有命名的函数，一般用在绑定事件的时候。 将匿名函数分配为变量的值，也就是我们前面所讲的函数表达式创建函数。一般来说，创建功能，我们使用函数声明来创建函数。使用匿名函数来运行负载的代码以响应事件触发（如点击按钮），使用事件处理程序。 

```javascript
function(){
    // 执行的代码
}
```

**自调用函数**

匿名函数不能通过直接调用来执行，因此可以通过匿名函数的自调用的方式来执行。比如：

```javascript
(function () {
  alert("hello");
})();
```

## [ JSON ]

对象：在 JavaScript 中对象是拥有属性和方法的数据。 

属性和方法：属性是与对象相关的值，也可以理解为特征。方法是能够在对象上执行的动作，也可以理解为行为。

> JSON（JavaScript Object Notation，JavaScript 对象表示法）是一种由道格拉斯·克罗克福特构想和设计、轻量级的数据交换语言，该语言以易于让人阅读的文字为基础，用来传输由属性值或者序列性的值组成的数据对象。尽管 JSON 是 JavaScript 的一个子集，但 JSON 是独立于语言的文本格式，并且采用了类似于 C 语言家族的一些习惯。
>
> JSON 数据格式与语言无关，脱胎于 JavaScript，但当前很多编程语言都支持 JSON 格式数据的生成和解析。JSON 的官方 MIME 类型是 application/json，文件扩展名是 .json。

特别需要注意的是：

- JSON 是一种纯数据格式,它只包含属性，没有方法。
- JSON 的属性必须通过双引号引起来。
- JSON 要求两头有 { } 来使其合法。
- 可以把 JavaScript 对象原原本本的写入 JSON 数据，比如：字符串，数字，数组，布尔还有其它的字面值对象。

### 常用内置对象 

#### Array 对象

1. Array 对象的常用属性：`length`，获取数组的长度。
2. Array 对象的常用方法：

- `concat()` 方法用于连接两个或多个数组，并返回结果。语法为：

```javascript
arrayObject.concat(arrayX, arrayX, ..., arrayX);
```

- `join()` 方法，将数组转换成字符串。（数组章节有详细介绍，这里不过多的赘述，下面的类似情况同样处理，大家看到这个方法，首先回想一下我们前面所学的知识，如有遗忘，再回去看一看加深记忆）。
- `pop()` 方法，删除并返回数组的最后一个元素。
- `push()` 方法，向数组的末尾添加一个或更多元素，并返回新的长度。
- `reverse()` 方法，颠倒数组的顺序。比如：

- `shift()` 方法，删除并返回数组的第一个元素。
- `unshift()` 方法，向数组的开头添加一个或更多元素，并返回新的长度。
- `slice()` 方法，从某个已有的数组返回选定的元素。语法为：

- `splice()` 方法，删除或替换当前数组的某些项目。语法为：

- `sort()` 方法，将数组进行排序。语法为：

#### String 对象

1. String 对象的常用属性：`length`，获取字符串的长度。
2. String 对象的常用方法：

- `charAt()` 方法，获取指定位置处字符。语法为：

- `charCodeAt()` 方法，获取指定位置处字符的 Unicode 编码。语法为：

- `concat()` 方法，连接字符串，等效于 “+”，“+” 更常用。与数组中的 `concat()` 方法相似。
- `slice()` 方法，提取字符串的片断，并在新的字符串中返回被提取的部分（字符串章节有详细介绍，这里不过多的赘述，下面的类似情况同样处理）。
- `indexOf()` 方法，检索字符串。
- `toString()` 方法，返回字符串。
- `toLowerCase()` 方法，把字符串转换为小写。
- `toUpperCase()` 方法，把字符串转换为大写。
- `replace()` 方法，替换字符串中的某部分。
- `split()` 方法，把字符串分割为字符串数组。

#### Date 对象

Date 对象方法：

- `Date()`：返回当日的日期和时间（输出的是中国标准时间）。
- `getDate()`：从 Date 对象返回一个月中的某一天 (1 ~ 31)。
- `getDay()`：从 Date 对象返回一周中的某一天 (0 ~ 6)。
- `getMonth()`：从 Date 对象返回月份 (0 ~ 11)。
- `getFullYear()`：从 Date 对象以四位数字返回年份。
- `getHours()`：返回 Date 对象的小时 (0 ~ 23)。
- `getMinutes()`：返回 Date 对象的分钟 (0 ~ 59)。
- `getSeconds()`：返回 Date 对象的秒数 (0 ~ 59)。
- `getMilliseconds()`：返回 Date 对象的毫秒(0 ~ 999)。

#### Math 对象

1. Math 对象的常用属性：

- E ：返回常数 e (2.718281828...)。
- LN2 ：返回 2 的自然对数 (ln 2)。
- LN10 ：返回 10 的自然对数 (ln 10)。
- LOG2E ：返回以 2 为底的 e 的对数 (log2e)。
- LOG10E ：返回以 10 为底的 e 的对数 (log10e)。
- PI ：返回 π（3.1415926535...)。
- SQRT1_2 ：返回 1/2 的平方根。
- SQRT2 ：返回 2 的平方根。

1. Math 对象的常用方法：

- `abs(x)` ：返回 x 的绝对值。
- `round(x)` ：返回 x 四舍五入后的值。
- `sqrt(x)` ：返回 x 的平方根。
- `ceil(x)` ：返回大于等于 x 的最小整数。
- `floor(x)` ：返回小于等于 x 的最大整数。
- `sin(x)` ：返回 x 的正弦。
- `cos(x)` ：返回 x 的余弦。
- `tan(x)` ：返回 x 的正切。
- `acos(x)` ：返回 x 的反余弦值（余弦值等于 x 的角度），用弧度表示。
- `asin(x)` ：返回 x 的反正弦值。
- `atan(x)` ：返回 x 的反正切值。
- `exp(x)` ：返回 e 的 x 次幂 (e^x)。
- `pow(n, m)` ：返回 n 的 m 次幂 (nm)。
- `log(x)` ：返回 x 的自然对数 (ln x)。
- `max(a, b)` ：返回 a, b 中较大的数。
- `min(a, b)` ：返回 a, b 中较小的数。
- `random()` ：返回大于 0 小于 1 的一个随机数。

###  创建对象和访问对 

#### 通过对象字面量来创建

```
var student = {
  name: "zhangsan",
  age: 18,
  gender: "male",
  sayHi: function () {
    console.log("hi,my name is " + this.name);
  },
};
```

#### 通过 new Object() 创建对象

```javascript
var student = new Object();
(student.name = "zhangsan"),
  (student.age = 18),
  (student.gender = "male"),
  (student.sayHi = function () {
    console.log("hi,my name is " + this.name);
  });
```

#### 通过工厂函数创建对象

```javascript
function createStudent(name, age, gender) {
  var student = new Object();
  student.name = name;
  student.age = age;
  student.gender = gender;
  student.sayHi = function () {
    console.log("hi,my name is " + this.name);
  };
  return student;
}
var s1 = createStudent("zhangsan", 18, "male");
```

#### 自定义构造函数

```javascript
function Student(name, age, gender) {
  this.name = name;
  this.age = age;
  this.gender = gender;
  this.sayHi = function () {
    console.log("hi,my name is " + this.name);
  };
}
var s1 = new Student("zhangsan", 18, "male");
```

#### new 关键字

构造函数，是一种特殊的函数。主要用来在创建对象时初始化对象，即为对象成员变量赋初始值，总与 `new` 运算符一起使用在创建对象的语句中。这里有需要特别注意的几点：

- 构造函数用于创建一类对象，首字母要大写。
- 内部使用 `this` 关键字给对象添加成员。
- 使用 `new` 关键字调用对象构造函数。

#### this 详解

在 JavaScript 中，我们经常会使用到 `this` 关键字，那么 `this` 到底指向什么呢？这里有一个口诀：谁调用 `this`，它就是谁。大家也可以从前面的例子中细细体会一下。

- 函数在定义的时候 `this` 是不确定的，只有在调用的时候才可以确定。
- 一般函数直接执行，内部 `this` 指向全局 window。比如：

```javascript
function test() {
  console.log(this);
}
test(); // window.test();
```

- 函数作为一个对象的方法，被该对象所调用，那么 `this` 指向的是该对象。
- 构造函数中的 `this`，始终是 `new` 的当前对象。

#### 遍历对象的属性

通过 `for...in` 语句用于遍历数组或者对象的属性，对数组或者对象的属性进行循环操作。比如：

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title></title>
  </head>

  <body>
    <script>
      var student = {
        name: "zhangsan",
        age: 18,
        gender: "male",
      };
      for (var key in student) {
        console.log(key);
        console.log(student[key]);
      }
    </script>
  </body>
</html>
```

注：key 是一个变量，这个变量中存储的是该对象的所有的属性的名字。

#### 删除对象的属性

使用 `delete` 删除对象的属性。比如在控制台中输入以下代码：

```javascript
var student = {
  name: "zhangsan",
  age: 18,
  gender: "male",
};
student.name; // zhangsan
delete student.name;
student.name; // undefined
```



















## [ WEB API ]

浏览器是一个封装得较为完善的软件，它给我们提供了一套操作浏览器功能和页面元素的接口——Web API。 

> API（Application Programming Interface，应用程序编程接口）："计算机操作系统"（Operating system）或"程序库"提供给应用程序调用使用的代码。其主要目的是让应用程序开发人员得以调用一组例程功能，而无须考虑其底层的源代码为何、或理解其内部工作机制的细节。API 本身是抽象的，它仅定义了一个接口，而不涉及应用程序在实际实现过程中的具体操作。

### BOM

> 浏览器对象模型（Browser Object Model (BOM)）指的是由 Web 浏览器暴露的所有对象组成的表示模型。BOM 与 DOM（Document Object Model，文档对象模型）不同，其既没有标准的实现，也没有严格的定义，所以浏览器厂商可以自由地实现 BOM。
>
> 作为显示文档的窗口，浏览器程序将其视为对象的分层集合。当浏览器分析文档时，它将创建一个对象的集合，以定义文档，并详细说明它应如何显示。浏览器创建的对象称为文档对象，它是浏览器使用的更大的对象集合的一部分。此浏览器对象集合统称为浏览器对象模型或 BOM。
>
> BOM 层次结构的顶层是窗口对象，它包含有关显示文档的窗口的信息。某些窗口对象本身就是描述文档和相关信息的对象。

#### BOM 的顶级对象 window 及其常用操作方法 

window 是浏览器的顶级对象，当调用 window 下的属性和方法时，可以省略 window。 

- **对话框**
  - `alert()`：显示带有一段消息和一个确认按钮的警告框。
  - `prompt()`：显示可提示用户输入的对话框。
  - `confirm()`：显示带有一段消息以及确认按钮和取消按钮的对话框。

- **页面加载事件**

  - `onload`
  ```javascript
  window.onload = function () {
    // 当页面加载完成执行
    // 当页面完全加载所有内容（包括图像、脚本文件、CSS 文件等）执行
  };
  ```

  - `onunload`
  ```javascript
  window.onunload = function () {
    // 当用户退出页面时执行
  };
  ```

- **浏览器尺寸**

  ```javascript
  var width = window.innerWidth;
  document.documentElement.clientWidth;
  document.body.clientWidth;

  var height = window.innerHeight;
  document.documentElement.clientHeight;
  document.body.clientHeight;
  ```

  上述代码可以获取所有浏览器的宽高（不包括工具栏/滚动条）。

- **定时器**

  - `setTimeout()`

    该方法在指定的毫秒数到达之后执行指定的函数，只执行一次。`clearTimeout()` 方法取消由 `setTimeout()` 方法设置的 `timeout`。

    ```javascript
    // 创建一个定时器，2000毫秒后执行，返回定时器的标示
    var timerId = setTimeout(function () {
    console.log("Hello shiyanlou");
    }, 2000);
  // 取消定时器的执行
    clearTimeout(timerId);
    ```
  
  - `setInterval()` 
  
    该方法设置定时调用的函数也就是可以按照给定的时间（单位毫秒）周期调用函数，`clearInterval()` 方法取消由 `setInterval()` 方法设置的 `timeout`。
  
    ```
  // 创建一个定时器，每隔 2 秒调用一次
  var timerId = setInterval(function () {
    var date = new Date();
    console.log(date.toLocaleTimeString());
  }, 2000);
  // 取消定时器的执行
    clearInterval(timerId);
    ```


BOM 的操作方法还有很多，但是一般情况下我们常用的就是上面所介绍的。

### DOM

DOM 文档对象模型（Document Object Model，简称 DOM），是 W3C 组织推荐的处理可扩展标志语言的标准编程接口。DOM 定义了访问 HTML 和 XML 文档的标准。我们这里主要学习 HTML DOM。DOM 可以把 HTML 看做是文档树，通过 DOM 提供的 API 可以对树上的节点进行操作。下面是W3C 上的 DOM 树： 

 ![img](https://doc.shiyanlou.com/document-uid897174labid9222timestamp1547429789687.png) 

#### DOM HTML 

DOM 能够操作 HTML 的内容。

- **改变 HTML 输出流**

在 JavaScript 中，使用 `document.write()` 可用于直接向 HTML 输出流写内容。

```javascript
document.write("新设置的内容<p>标签也可以生成</p>");
```

- **改变 HTML 内容**

使用 `innerHTML` 属性改变 HTML 内容。

```
 document.getElementById("p1").innerHTML = "Hello 实验楼";
```

- **改变 HTML 属性**

```javascript
document.getElementById(id).attribute = new value();
```

#### DOM CSS 

DOM 能够改变 HTML 元素的样式。语法为：

```javascript
document.getElementById(id).style.property = new style();
```

#### DOM 节点 

根据 W3C 的 HTML DOM 标准，HTML 文档中的所有内容都是节点：整个文档就是一个文档节点，而每一个 HTML 标签都是一个元素节点。HTML 标签中的文本则是文本节点，HTML 标签的属性是属性节点，一切都是节点。

![1](https://doc.shiyanlou.com/document-uid897174labid9222timestamp1547430589989.png)

#### DOM 节点的操作 

- **获取节点**

  要操作节点，首先我们要找到节点。主要有以下三种办法：

  1. 通过 ID 找到 HTML 元素：使用方法 `getElementById()` 通过元素的 ID 而选取元素，比如：
  
     ```javascript
     document.getElementById("demo"); 
     ```
  
  2. 通过标签名找到 HTML 元素：使用方法 getElementsByTagName() 来选取元素，如果有多个同类型标签，那么我们可以通过下标来确认，
  
     ```javascript
     document.getElementsByTagName("input")[0].value = "hello"; // 下标为 [0] 表示选取第 1 个 input 标签
     ```
  
  3. 通过类名来找到 HTML 元素：使用方法 `getElementsByClassName()` 通过元素的类名来选取元素。
  
     ```javascript
     document.getElementsByClassName("name"); // 返回包含 class = "name" 的所有元素的一个列表。
     ```

- **DOM 节点之间的关系**

  DOM 的节点并不是孤立的，我们从 DOM 树中也可以看出，节点与节点之间存在着相对的关系，就如同一个家族一样，有父辈，有兄弟，有儿子等等。

  | 父节点     | 兄弟节点               | 子节点            | 所有子节点 |
  | ---------- | ---------------------- | ----------------- | ---------- |
  | parentNode | nextSibling            | firstChild        | childNodes |
  |            | nextElementSibling     | firstElementChild | children   |
  |            | previousSibling        | lastChild         |            |
  |            | previousElementSibling | lastElementChild  |            |

- **DOM 节点的操作**

  1. 创建节点

     - 创建元素节点：使用 `createElement()` 方法。
  
       ```javascript
     var par = document.createElement("p");
       ```

     - 创建属性节点：使用 `createAttribute()` 方法。
  
   - 创建文本节点：使用 `createTextNode()` 方法。
  
  2. 插入子节点
  
     - `appendChild ()` 方法向节点添加最后一个子节点。
     - `insertBefore` (插入的新的子节点，指定的子节点) 方法在指定的子节点前面插入新的子节点。如果第二个参数没写或者为 null，则默认插入到后面。
  
  3. 删除节点
  
     使用 `removeChild()` 方法。写法为：
  
     ```javascript
     父节点.removeChild(子节点);
     node.parentNode.removeChild(node); // 如果不知道父节点是什么，可以这样写
     ```
  
  4. 替换子节点
  
     使用 `replaceChild()` 方法。语法为：
  
     ```javascript
     node.replaceChild(newnode, oldnode);
     ```
  
  5. 设置节点的属性：
     - 获取：`getAttribute(name)`
     - 设置：`setAttribute(name, value)`
     - 删除：`removeAttribute(name)`

#### DOM 事件 

事件的定义：在什么时候执行什么事。

事件三要素：事件由：事件源 + 事件类型 + 事件处理程序组成。
	事件源：触发事件的元素
	事件类型：事件的触发方式（比如鼠标点击或键盘点击）
	事件处理程序：事件触发后要执行的代码（函数形式，匿名函数）

- **常用的事件**

  | 事件名      | 说明                                 |
  | ----------- | ------------------------------------ |
  | onclick     | 鼠标单击                             |
  | ondblclick  | 鼠标双击                             |
  | onkeyup     | 按下并释放键盘上的一个键时触发       |
  | onchange    | 文本内容或下拉菜单中的选项发生改变   |
  | onfocus     | 获得焦点，表示文本框等获得鼠标光标。 |
  | onblur      | 失去焦点，表示文本框等失去鼠标光标。 |
  | onmouseover | 鼠标悬停，即鼠标停留在图片等的上方   |
  | onmouseout  | 鼠标移出，即离开图片等所在的区域     |
  | onload      | 网页文档加载事件                     |
  | onunload    | 关闭网页时                           |
  | onsubmit    | 表单提交事件                         |
  | onreset     | 重置表单时                           |



## [ 值类型和引用类型 ]

### 值类型

值类型又叫基本数据类型，在 JavaScript 中值类型有以下五种：

数值类型、布尔类型undefined、null、字符串

值类型存储在栈（stack）中，它们的值直接存储在变量访问的位置。

 <img src="https://doc.shiyanlou.com/document-uid897174labid9222timestamp1547607159775.png" alt="img" style="zoom: 67%;" /> 

#### 值类型的特征

- 值类型的值是不可变的，不可变是指值类型指向的空间不可变。
- 按值传递的变量之间互不影响。 
- 值类型赋值，直接将值复制一份。 
-  当参数为值类型的时候，函数内和函数外的两个变量完全不同，仅仅只是存的值一样而已，修改时互不影响。 

### 引用类型

引用类型又叫复合数据类型，在 JavaScript 中引用类型有以下三种：

对象、数组、函数

引用类型存储在堆中，也就是说存储在变量处的值是一个指针，指向存储对象的内存处。

 <img src="https://doc.shiyanlou.com/document-uid897174labid9222timestamp1547609082688.png" alt="img" style="zoom:67%;" /> 

#### 引用类型的特征

- 引用类型赋值，是将地址复制一份。

- 当参数为引用类型的时候，函数内和函数外的两个变量不同，但是共同指向同一个对象，在函数内修改对象数据时会影响外部。 

  注：其实我们可以这样理解。引用类型中的地址是一把钥匙，钥匙指向的是宝藏，复制一把钥匙后，两把钥匙能打开的是同一个宝藏。 



## [ 调试和异常处理 ]

### 调试工具的使用、设置断点

略

### 异常处理

#### 异常捕获

我们使用 `try-catch` 语句开捕获异常，语法为：

```javascript
try {
  // 这里写可能出现异常的代码
} catch (err) {
  // 在这里写，出现异常后的处理代码
}
```

需要注意以下几点：

- 语句 `try` 和 `catch` 是成对出现的。
- 如果在 `try` 中出现了错误，`try` 里面出现错误的语句后面的代码都不再执行，直接跳转到 `catch` 中，`catch` 处理错误信息，然后再执行后面的代码。
- 如果 `try` 中没有出现错误，则不会执行 `catch` 中的代码，执行完 `try` 中的代码后直接执行后面的代码。
- 通过 `try-catch` 语句进行异常捕获之后，代码将会继续执行，而不会中断。

#### throw 语句

通过 `throw` 语句，我们可以创建自定义错误。`throw` 语句常常和 `try catch` 语句一起使用。

```javascript
if (isNaN(x)) throw "您输入的不是数字";
```



##  [ 面向对象编程 ]

 JavaScript 是一门脚本语言。它支持多种编程方式，面向对象编程就是其中一种。 

**什么是对象**

ECMA-262 把对象（object）定义为“属性的无序集合，每个属性存放一个原始值、对象或函数”。我们可以从以下两个层次来理解对象到底是什么：

1. 对象是单个事物的抽象。比如一支笔，一本书，一辆车都可以是一个对象。
2. 对象是一个容器，封装了属性和方法。比如：一辆车。它的颜色，大小，重量等是它的属性，而启动，加速，减速，刹车等是它的方法。

**什么是面向对象编程**

> 面向对象程序设计（英语：Object Oriented Programming，缩写：OOP）是种具有对象概念的程序编程典范，同时也是一种程序开发的抽象方针。它可能包含数据、属性、代码与方法。对象则指的是类的实例。它将对象作为程序的基本单元，将程序和数据封装其中，以提高软件的重用性、灵活性和扩展性，对象里的程序可以访问及经常修改对象相关连的数据。在面向对象程序编程里，计算机程序会被设计成彼此相关的对象。

### 构造函数

首先，我们来复习一下创建对象的方式。

1. 通过对象字面量来创建。

   ```javascript
   var student = {
     name: "zhangsan",
     age: 18,
     gender: "male",
     sayHi: function () {
       console.log("hi,my name is " + this.name);
     },
   };
   ```

2. 通过 new Object( ) 创建对象。

   ```javascript
   var student = new Object();
     (student.name = "zhangsan"),
     (student.age = 18),
     (student.gender = "male"),
     (student.sayHi = function () {
       console.log("hi,my name is " + this.name);
     });
   ```

上面两种都是简单的创建对象的方式，但是如果有多个实例对象呢？为了降低代码冗余率，简单方式的改进是：**工厂函数**。

3. 通过工厂函数来创建对象。

```js
function createStudent(name, age, gender) {
  var student = new Object();
  student.name = name;
  student.age = age;
  student.gender = gender;
  student.sayHi = function () {
    console.log("hi,my name is " + this.name);
  };
  return student;
}
var s1 = createStudent("zhangsan", 18, "male");
var s2 = createStudent("lisi", 19, "male");
```

这样封装代码确实解决了代码冗余的问题，但是每次调用函数 `createStudent()` 都会创建新函数 `sayHi()`，也就是说每个对象都有自己的 `sayHi()` 版本，而事实上，每个对象都共享一个函数。为了解决这个问题，我们引入面向对象编程里的一个重要概念：**构造函数**。

4. 通过构造函数来创建对象。

```js
function Student(name, age, gender) {
  this.name = name;
  this.age = age;
  this.gender = gender;
  this.sayHi = function () {
    console.log("hi,my name is " + this.name);
  };
}
var s1 = new Student("zhangsan", 18, "male");
```

来看看**构造函数与工厂函数的区别**：

- 首先在构造函数内没有创建对象，而是使用 `this` 关键字，将属性和方法赋给了 `this` 对象。
- 构造函数内没有 `return` 语句，`this` 属性默认下是构造函数的返回值。
- 函数名使用的是大写的 Student。
- 用 `new` 运算符和类名 Student 创建对象。

**构造函数存在的问题** 

由于每个对象都是由 new Student 创建出来的，因此每创建一个对象，函数 `sayHi()` 都会被重新创建一次，这个时候，每个对象都拥有一个独立的但是功能完全相同的方法，这样势必会造成内存浪费。有的人可能会想，既然是一样的那我们就单独把它提出来，写一个函数，每次调用不就可以了吗？  但是这样做会导致全局变量增多，可能会引起命名冲突，代码结果混乱，维护困难。通过使用**原型**可以很好的解决这个问题。 

### 原型 prototype

 在 JavaScript 中，每一个函数都有一个 `prototype` 属性，指向另一个对象。这个对象的所有属性和方法，都会被构造函数的实例继承。我们来看看前面例子原型的写法： 

```javascript
function Student(name, age, gender) {
  this.name = name;
  this.age = age;
  this.gender = gender;
}

Student.prototype.sayHi = function () {
  console.log("hi");
};

var s1 = new Student("zhangsan", 18, "male");
s1.sayHi(); // 打印 hi
var s2 = new Student("lisi", 18, "male");
s2.sayHi(); // 打印 hi
console.log(s1.sayHi == s2.sayHi); // 结果为 true
```

**构造函数、实例、原型三者之间的关系** 

- 构造函数的 `prototype` 对象默认都有一个 `constructor` 属性，指向 `prototype` 对象所在函数。

- 通过构造函数得到的实例对象内部会包含一个指向构造函数的 `prototype` 对象的指针 `__proto__`。`__proto__` 属性最早是火狐浏览器引入的，用以通过实例对象来访问原型，这个属性在早期是非标准的属性。 


- 实例对象可以直接访问原型对象成员，所有实例都直接或间接继承了原型对象的成员。 


总结：每个构造函数都有一个原型对象，原型对象包含一个指向构造函数的指针 `constructor`，而实例都包含一个指向原型对象的内部指针`__proto__`。 

###  原型链 

我们说过所有的对象都有原型，而原型也是对象，也就是说原型也有原型，如此下去也就组成了我们的原型链。

#### 属性搜索原则

属性搜索原则，也就是属性的查找顺序，在访问对象的成员的时候，会遵循以下原则：

- 首先从对象**实例本身**开始找，如果找到了这个属性或者方法，则返回。
- 如果对象实例本身没有找到，就从它的**原型**中去找，如果找到了，则返回。
- 如果对象实例的原型中也没找到，则从它的**原型的原型**中去找，如果找到了，则返回。
- 一直按着原型链查找下去，找到就返回，如果在原型链的末端还没有找到的话，那么如果查找的是属性则返回 undefined，如果查找的是方法则返回 `xxx is not a function`。

#### 更简单的原型语法

在前面的例子中，我们是使用 `xxx.prototype.` 然后加上属性名或者方法名来写原型，但是每添加一个属性或者方法就写一次显得有点麻烦，因此我们可以用一个包含所有属性和方法的对象字面量来**重写整个原型对象**：

```js
function Student(name, age, gender) {
  this.name = name;
  this.age = age;
  this.gender = gender;
}
Student.prototype = {
  hobby: "study",
  sayHi: function () {
    console.log("hi");
  },
};

var s1 = new Student("wangwu", 18, "male");
console.log(Student.prototype.constructor === Student); // 结果为 false
```

但是这样写也有一个问题，那就是原型对象丢失了 `constructor` 成员。所以为了保持 constructor 成员的指向正确，建议的写法是：

```js
function Student(name, age, gender) {
  this.name = name;
  this.age = age;
  this.gender = gender;
}
Student.prototype = {
  constructor: Student, // 手动将 constructor 指向正确的构造函数
  hobby: "study",
  sayHi: function () {
    console.log("hi");
  },
};

var s1 = new Student("wangwu", 18, "male");
console.log(Student.prototype.constructor === Student); // 结果为 true
```

我们都听过这么一句话：子承父业。而在我们的 JavaScript 中也有继承，接下来我们会学习原型链继承。原型链继承的主要思想是利用原型让一个引用类型继承另外一个引用类型的属性和方法。

```js
function Student(name, age, gender) {
  this.name = name;
  this.age = age;
  this.gender = gender;
}
Student.prototype.sayHi = function () {
  console.log("hi");
};

var s1 = new Student("zhangsan", 18, "male");
s1.sayHi(); // 打印 hi
var s2 = new Student("lisi", 18, "male");
s2.sayHi(); // 打印 hi
```

上述例子中实例化对象 s1 和 s2 都继承了 `sayHi()` 方法。

### Object.prototype 成员介绍 

![1](https://doc.shiyanlou.com/document-uid897174labid9222timestamp1547709733167.png) 

## [ 函数进阶 ]

this的指向：谁调用 `this`，它就指向谁。 

#### call

`call()` 方法调用一个函数, 其具有一个指定的 `this` 值和分别地提供的参数（参数的列表）。语法为：

```js
fun.call(thisArg, arg1, arg2, ...)
```

注：

- `thisArg` 指的是在 `fun` 函数中指定的 `this` 的值。如果指定了 null 或者 undefined 则内部 `this` 指向 window，同时值为原始值（数字，字符串，布尔值）的 `this` 会指向该原始值的自动包装对象。是一个可选项。
- arg1, arg2, ...指定的参数列表。也是可选项。
- 使用调用者提供的 `this` 值和参数调用该函数的返回值。若该方法没有返回值，则返回 undefined。
- `call()` 允许为不同的对象分配和调用属于一个对象的函数/方法。
- `call()` 提供新的 `this` 值给当前调用的函数/方法。你可以使用 `call()` 来实现继承：写一个方法，然后让另外一个新的对象来继承它（而不是在新对象中再写一次这个方法）。

1. 使用 `call()` 方法调用函数并且指定上下文的 `this`。前面的例子可以改写成： 

2. ```js
   function foods() {}
   foods.prototype = {
     price: "￥15",
     say: function () {
       console.log("My price is " + this.price);
     },
   };
   
   var apple = new foods();
   orange = {
     price: "￥10",
   };
   apple.say.call(orange); // My price is ￥10
   ```

3. 在一个子构造函数中，你可以通过调用父构造函数的 `call()` 方法来实现继承。在控制台输入如下代码：

   ```js
   function Father(name, age) {
     this.name = name;
     this.age = age;
   }
   
   function Son(name, age) {
     Father.call(this, name, age);
     this.hobby = "study";
   }
   
   var S1 = new Son("zhangsan", 18);
   S1; // Son {name: "zhangsan", age: 18, hobby: "study"}
   ```

#### apply

`apply()` 方法与 `call()` 方法类似，唯一的区别是 `call()` 方法接受的是参数，`apply()` 方法接受的是数组。语法为：

```js
fun.apply(thisArg, [argsArray]);
```

1. 使用 `apply()` 方法将数组添加到另一个数组。

   例子：

```js
var array = ["a", "b", "c"];
var nums = [1, 2, 3];
array.push.apply(array, nums);
array; // ["a", "b", "c", 1, 2, 3]
```

> 注：concat() 方法连接数组，不会改变原数组，而是创建一个新数组。而使用 push() 是接受可变数量的参数的方式来添加元素。使用 apply() 则可以连接两个数组。

1. 使用 `apply()` 方法和内置函数。

   例子：

```js
var numbers = [7, 10, 2, 1, 11, 9];
var max = Math.max.apply(null, numbers);
max; // 11
```

> 注：直接使用 max() 方法的写法为：Math.max(7, 10, 2, 1, 11, 9);

#### bind

`bind()` 方法创建一个新的函数（称为绑定函数），在调用时设置 `this` 关键字为提供的值。并在调用新函数时，将给定参数列表作为原函数的参数序列的前若干项。语法为：

```js
fun.bind(thisArg[, arg1[, arg2[, ...]]])
```

注：参数 thisArg：当绑定函数被调用时，该参数会作为原函数运行时的 `this` 指向。当使用 `new` 操作符调用绑定函数时，该参数无效。参数：arg1，arg2，...表示当目标函数被调用时，预先添加到绑定函数的参数列表中的参数。

我们创建一个简单的绑定函数例子：

```js
var bin = function () {
  console.log(this.x);
};
var foo = {
  x: 10,
};

bin(); // undefined
var func = bin.bind(foo); // 创建一个新函数把 'this' 绑定到 foo 对象
func(); // 10
```

我们再来看一个例子：

```js
this.num = 6;
var test = {
  num: 66,
  getNum: function () {
    return this.num;
  },
};

test.getNum(); // 返回 66

var newTest = test.getNum;
newTest(); // 返回 6, 在这种情况下，"this"指向全局作用域

// 创建一个新函数，将"this"绑定到 test 对象
var bindgetNum = newTest.bind(test);
bindgetNum(); // 返回 66
var newTest = test.getNum;
newTest();

// 上面这两行代码其实相当于：
var newTest(){
    return this.num;
}
// 所以 this 指向的是全局作用域，返回 6。
```

###   作用域

#### 块级作用域

在 JavaScript 中是没有块级作用域的。

#### 函数作用域

JavaScript 的函数作用域是指在函数内声明的所有变量在函数体内始终是可见的，不涉及赋值。

#### 全局作用域

全局作用域也就是说什么地方都能够访问到。比如我们不用 `var` 关键字，直接声明变量的话，那这个变量就是全局变量，它的作用域就是全局作用域。使用 window 全局对象来声明，全局对象的属性也是全局变量。另外在所有的函数外部用 `var` 声明的变量也是全局变量，这是因为内层作用域可以访问外层作用域。

注：

- 内层作用域可以访问外层作用域，反之不行。
- 整个代码结构中只有函数可以限定作用域。
- 如果当前作用规则中有名字了，就不考虑外面的同名变量。
- 作用域规则首先使用提升规则分析。

#### 变量名提升

JavaScript 是解释型的语言，但是它并不是真的在运行的时候完完全全的逐句的往下解析执行。

 JavaScript 引擎在对 JavaScript 代码进行解释执行之前，会对 JavaScript 代码进行预解析，在预解析阶段，会将以关键字 `var` 和 `function` 开头的语句块提前进行处理。当变量和函数的声明处在作用域比较靠后的位置的时候，变量和函数的声明会被提升到作用域的开头。

### 闭包 

闭包是指函数可以使用函数之外定义的变量。

#### 简单的闭包

在 JavaScript 中，使用全局变量是一个简单的闭包实例。比如：

```js
var num = 3;
function foo() {
  console.log(num);
}
foo(); //打印 3
```

#### 复杂的闭包

```js
function f1() {
  var num1 = 6;
  function f2() {
    var num2 = 7;
  }
  console.log(num1 + num2);
}
f1();
```

在上述代码中函数 `f2` 能够访问到它外层的变量 `num1`，但是 `f1` 是不能访问 `f2` 中的变量`num2`，因此我们可以把 `num2` 作为 `f2` 的返回值，然后通过 `f2` 的返回值就可以访问到 `sum2` 了。

```js
function f1() {
  var num1 = 6;
  function f2() {
    var num2 = 7;
    return num2;
  }
  console.log(num1 + f2());
}
f1();
```

### Arguments 对象

在函数代码中，使用特殊对象 `arguments`，无需明确指出参数名，我们就能访问它们。第一个参数是 `arguments[0]`，第二个参数是 `arguments[1]`，以此类推。比如：

```js
function foo() {
  console.log(arguments[0]);
  console.log(arguments[1]);
}
foo(2, 3); // 打印 2 3
```

还可以用 `arguments` 对象检测函数的参数个数，引用属性 `arguments.length` 即可。来看一个遍历参数求和的例子：

```js
function add() {
  var sum = 0;
  for (var i = 0; i < arguments.length; i++) {
    sum += arguments[i];
  }
  return sum;
}
add(); // 0
add(1); // 1
add(1, 2); // 3
add(1, 2, 3); // 6
```

Function 对象



用 `Function()` 对象创建函数的语法如下：

```js
var function_name = new Function(arg1, arg2, ..., argN, function_body)
```

注：每个参数都必须是字符串，`function_body` 是函数主体，也就是要执行的代码。

例子：

```js
var add = new Function("a", "b", "console.log(a+b);");
add(2, 5); // 打印 7
```

再看一个例子:

```js
var add = new Function("a", "b", "console.log(a+b);");
var doAdd = add;
doAdd(2, 5); // 打印 7
add(2, 5); // 打印 7
```

在上述例子中，变量 `add` 被定义为函数，然后 `doAdd` 被声明为指向同一个函数的指针。用这两个变量都可以执行该函数的代码，并输出相同的结果。因此，函数名只是指向函数的变量，那么我们可以把函数作为参数传递给另一个函数，比如下面的例子：

```js
function addF(foo, b, c) {
  foo(b, c);
}
var add = new Function("a", "b", "console.log(a+b);");
addF(add, 2, 5); // 打印 7
```

#### Function 对象的 length 属性

函数属于引用类型，所以它们也有属性和方法。`length` 属性声明了函数期望的参数个数。

例子：

```js
var add = new Function("a", "b", "console.log(a+b);");
console.log(add.length); // 打印 2
```

#### Function 对象的方法

`Function()` 对象也有与所有对象共享的 `valueOf()` 方法和 `toString()` 方法。这两个方法返回的都是函数的源代码。

例子：

```js
var add = new Function("a", "b", "console.log(a+b);");
add.valueOf();
add.toString();
```
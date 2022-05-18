# A Note For Typescript

**什么是 TypeScript**

TypeScript 是一种由微软开发的自由和开源的编程语言。它是 JavaScript 的一个超集，而且本质上向这个语言添加了可选的静态类型和基于类的面向对象编程。它扩展了 JavaScript 的语法，所以任何现有的 JavaScript 程序可以不加改变的在 TypeScript 下工作。TypeScript 是为大型应用之开发而设计，而编译时它产生 JavaScript 以确保兼容性。 

值得一提的是，TypeScript 在开发时就能给出编译错误，而 JavaScript 错误则需要在运行时才能暴露。 

用一张表格来更清晰的观察两者的区别：

|               | JavaScript                                                   | TypeScript                                                   |
| ------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 语言          | 脚本语言                                                     | 面向对象编程语言                                             |
| 学习难度      | 灵活易学                                                     | 需要有脚本编程经验                                           |
| 类型          | 轻量级解释编程语言                                           | 强类型的面向对象编程语言                                     |
| 客户端/服务端 | 客户端服务端都有                                             | 侧重客户端                                                   |
| 拓展名        | .js                                                          | .ts 或 .tsx                                                  |
| 耗时          | 更快                                                         | 编译代码需要些时间                                           |
| 数据绑定      | 没有类型和接口的概念                                         | 使用类型和接口表示数据                                       |
| 语法          | 所有的语句都写在脚本标签内。浏览器将脚本标签内的文本识别为脚本 | 一个 TypeScript 程序由模块、方法、变量、语句、表达式和注释构成 |
| 静态类型      | JS 中没有静态类型的概念                                      | 支持静态类型                                                 |
| 模块支持      | 不支持模块                                                   | 支持模块                                                     |
| 接口          | 没有接口                                                     | 支持接口                                                     |
| 可选参数方法  | 不支持                                                       | 支持                                                         |
| 原型          | 没有这种特性                                                 | 支持原型特性                                                 |
| 参考选择      | 小型项目                                                     | TS 是一种面向对象语言，代码更简洁，可读性和复用性强。因此 TS 更适合大型项目。 |

## [ 基本数据类型 ]

数据类型有原始数据类型和非原始数据类型两种。

在 TypeScript 中声明变量，需要加上类型声明，例如 boolean 和 string 等。通过静态类型约束，在编译时执行类型检查，可以避免一些类型混用的低级错误。

### 原始数据类型

原始数据类型有以下六种：

boolean 布尔值、number 数值、string 字符串、null 空值、undefined 未定义、Symbol （ES6 中的新类型）

本节主要介绍前五种原始数据类型在 TypeScript 中的应用。

**布尔值**

布尔值是最基础的数据类型，在 TypeScript 中，使用 `boolean` 定义布尔值类型：

```ts
let isDone: boolean = false;
```

**数字**

和 JavaScript 一样，TypeScript 里的所有数字都是浮点数。 这些浮点数的类型是 `number`。 除了支持十进制和十六进制字面量，TypeScript 还支持 ECMAScript 2015 中引入的二进制和八进制字面量。

```ts
let a: number = 6;
// ES6 中的二进制表示法
let b: number = 0b1010;
// ES6 中的八进制表示法
let c: number = 0o744;
```

**字符串**

和 JavaScript 一样，可以使用双引号（ `"`）或单引号（`'`）表示字符串。

```ts
let myName: string = "xiaoming";
```

还可以使用模版字符串，它可以定义多行文本和内嵌表达式。这种字符串是被反引号包围，并且使用`$`这种形式嵌入表达式。

```ts
let myName: string = "xiaoming";
let myAge: number = 25;
let sentence: string = `Hello, my name is ${myName}.I'll be ${
  myAge + 1
} years old next month.`;
```

**空值**

JavaScript 没有空值（Void）的概念，在 TypeScript 中，可以用 `void` 表示没有任何返回值的函数：

```ts
function alertName(): void {
  alert("My name is Tom");
}
```

声明一个 `void` 类型的变量没有什么用，因为你只能将它赋值为 `undefined` 和 `null`：

```ts
let unde: void = undefined;
let nu: void = null;
```

**Null 和 Undefined**

在 TypeScript 中，可以使用 `null` 和 `undefined` 来定义这两个原始数据类型：

```ts
let un: undefined = undefined;
let nu: null = null;
```

与 `void` 的区别是，`undefined` 和 `null` 是所有类型的子类型。也就是说 `undefined` 类型的变量，可以赋值给 `number` 类型的变量：

```ts
// 这样不会报错
let num: number = undefined;
// 这样也不会报错
let un: undefined;
let num2: number = un;
```

### 非原始数据类型

非原始数据类型有以下九种：

数组、Tuple 元祖、enum 枚举、never 永不存在的值的类型、void、any 任意类型、联合类型、函数类型、对象类型

其中元组、枚举、任意值、void 类型和 never 类型是 TypeScript 有别于 JavaScript 的特有类型。

**数组**

定义数组有两种方式。

- **第一种：普通方式。**

  可以在元素类型后面接上 `[]`，表示由此类型元素组成的一个数组，数组的项中不允许出现其他的类型：

  ```javascript
  //数组表现方式 类型[]
  let arr: number[] = [1, 2, 3, 4];
  ```

- **第二种:泛型方式 `Array<元素类型>`。**

  ```javascript
  let list: Array<number> = [1, 2, 3];
  ```

**元祖**

元组类型允许表示一个已知元素数量和类型的数组，各元素的类型不必相同。比如，你可以定义一对值分别为 `string`和`number`类型的元组。

```ts
let x: [string, number];
x = ["Hello", 10];
```

**枚举**

使用枚举我们可以定义一些带名字的常量。 使用枚举可以清晰地表达意图或创建一组有区别的用例。TypeScript 支持数字的和基于字符串的枚举。

```ts
// 利用 const 关键词也可以声明一组常量，例如，声明十二生肖的排位
const rat: number = 1;
const cattle: number = 2;
const tiger: number = 3;
const rabbit: number = 4;
const dragon: number = 5;
```

上述只声明了 5 个，如果声明全排位，需要声明 12 个变量，并且注明类型，但是却多了很多重复性工作，利用数字枚举，我们可以轻松声明同样的一组常量。

- **数字枚举**

  默认情况下，从 0 开始为元素编号。 你也可以手动的指定成员的数值。

	```ts
enum ChineseZodiac {
  rat,
  cattle,
  tiger,
  rabbit,
  dragon,
}
	```

- **字符串枚举**

  在一个字符串枚举里，每个成员都必须用字符串字面量，或另外一个字符串枚举成员进行初始化。

	```ts
enum Person {
  name = "NAME",
  age = "AGE",
  love = "LOVE",
  hobby = "HOBBY",
}
console.log(Person.name); // NAME
console.log(Person.hobby); // HOBBY
	```

**never**

never 类型是任何类型的子类型，也可以赋值给任何类型，一般作为函数返回值。

```ts
// 返回never的函数必须存在无法达到的终点
function error(message: string): never {
  throw new Error(message);
}
```

**void**

void 类型像是与 any 类型相反，它表示没有任何类型。 当一个函数没有返回值时，你通常会见到其返回值类型是 void。

```ts
function warn(): void {
  console.log("This is my warning message");
}
```

**any 任意类型**

任意值（Any）用来表示允许赋值为任意类型。声明一个变量为任意值之后，对它的任何操作，返回的内容的类型都是任意值。变量如果在声明的时候，未指定其类型，那么它会被识别为任意值类型。

```ts
let notSure: any = 4;
notSure = "这是字符串";
notSure = false;
```

当你不希望类型检查器对某些值进行检查而是直接让它们通过编译阶段的检查，可以使用 any 类型来标记这些变量。

**联合类型**

联合类型（Union Types）表示取值可以为多种类型中的一种。

```ts
let num: string | number;
num = "seven";
num = 7;
```

联合类型使用 `|` 分隔每个类型。这里的 `let num: string | number` 的含义是，允许 `num` 的类型是 `string` 或者 `number`，但是不能是其他类型。

**对象类型**

object 表示非原始类型，也就是除 number，string，boolean，symbol，null 或 undefined 之外的类型。

```ts
declare function create(o: object | null): void;
create({ name: 0 }); // OK
create(null); // OK
create(2); // Error
create("字符串"); // Error
create(false); // Error
create(undefined); // Error
```

### 类型断言

类型断言可以用来手动指定一个值的类型，即允许变量从一种类型更改为另一种类型。

- 方式一：<类型>值

```ts
let someAny: any = "my name is tony";
let strLength: number = (<string>someAny).length;
```

- 方式二：值 as 类型

```ts
let someAny: any = "my name is tony";
let strLength: number = (someAny as string).length;
```

## [ 接口 ]

在 TypeScript 中，我们使用接口（Interfaces）来定义对象的类型。接口是一系列抽象方法的声明，是一些方法特征的集合，这些方法都应该是抽象的，需要由具体的类去实现，然后第三方就可以通过这组抽象方法调用，让具体的类执行具体的方法。 

**接口的作用：**

1. 对类的一部分行为进行抽象
2. 描述对象的形状

**注意：** 接口一般首字母大写，也可以在接口之前加大写 `I` ，赋值的时候，变量的形状必须和接口的形状保持一致。不允许添加未定义的属性。 

### 接口的属性

- 可选属性

  有时我们希望不要完全匹配一个形状，那么可以用可选属性。 在属性后使用 `?` 表示这个属性是可选属性，可选属性的含义是该属性可以不存在，但是仍然不允许添加未定义的属性。  

- 任意属性

  有时候我们希望一个接口允许有任意的属性， 可以使用 `[propName: string]` 定义任意属性取 `string` 类型的值。 

- 只读属性 

  有时候我们希望对象中的一些字段只能在创建的时候被赋值，那么可以用 `readonly` 定义只读属性。如果使用 `readonly` 定义的属性初始化后又被赋值了，那么就会报错了。 

```ts
interface Person {
  readonly id: number;
  name: string;
  age?: number;
  [propName: string]: any;
}

let tom: Person = {
  id: 123,
  name: "Tom",
  gender: "male",
};
```

## [ 类 ]

### 类的概念 

类（Class）**：定义了一件事物的抽象特点，包含它的属性和方法。 

**对象（Object）**：类的实例，通过 new 生成。 

**面向对象 OOP 的三大特性**

- **封装（Encapsulation）**

  将对数据的操作细节隐藏起来，只暴露对外的接口。外界调用端不需要（也不可能）知道细节，就能通过对外提供的接口来访问该对象，同时也保证了外界无法任意更改对象内部的数据。

- **继承（Inheritance）**

  子类继承父类，子类除了拥有父类的所有特性外，还有一些更具体的特性。

- **多态（Polymorphism）**

  由继承而产生了相关的不同的类，对同一个方法可以有不同的响应。比如 Cat 和 Dog 都继承自 Animal，但是分别实现了自己的 run 方法。此时针对某一个实例，我们无需了解它是 Cat 还是 Dog，就可以直接调用 run 方法，程序会自动判断出来应该如何执行 run。

**存取器（getter & setter）**：用以改变属性的读取和赋值行为。

**抽象类（Abstract Class）**：抽象类是供其他类继承的基类，抽象类不允许被实例化。抽象类中的抽象方法必须在子类中被实现。

**修饰符（Modifiers）**：修饰符是一些关键字，用于限定成员或类型的性质。比如 public 表示公有属性或方法。

**接口（Interfaces）**：不同类之间公有的属性或方法，可以抽象成一个接口。接口可以被类实现（implements）。一个类只能继承自另一个类，但是可以实现多个接口。

### 类的定义 

使用 `class` 定义类，使用 `constructor` 定义构造函数。类一般包括属性 + 方法。

```ts
class Greeter {
  greeting: string;
  constructor(message: string) {
    this.greeting = message;
  }
  greet() {
    alert("Hello, " + this.greeting);
  }
}

let greeter = new Greeter("world");
greeter.greet();
```

### 类的继承

使用 `extends` 关键字实现继承，子类中使用 `super` 关键字来调用父类的构造函数和方法。

```ts
// 父类
class Person {
  name: string;
  constructor(name: string) {
    // 构造函数，实例化类的时候触发的方法
    this.name = name;
  }
  run(): void {
    console.log(`${this.name}在运动`);
  }
}
let p = new Person("父亲");
p.run(); // 父亲在运动

// 子类继承父类
class Child extends Person {
  constructor(name: string) {
    super(name); // 初始化父类的构造函数
  }
}
let c = new Child("儿子");
c.run(); // 儿子在运动
```

### 类里面的修饰符

Typescript 里面定义属性的时候给我们提供了三种修饰符：

- public：公有，在当前类里面、子类、类外面都可以访问。
- protected：保护类型，在当前类里面、子类里面可以访问，在类外部没法访问。
- private：私有，在当前类里面可以访问，子类、类外部都没法访问。

注意：属性如果不加修饰符，默认就是公有（public）。

**public**

```ts
class Person {
  public name: string; // 公有

  constructor(name: string) {
    this.name = name;
  }

  run(): void {
    console.log(`${this.name}在运动`); // 在类里能访问
  }
}
let p = new Person("张三");
p.run();
console.log(p.name); // 在类外面能访问

class Child extends Person {
  constructor(name: string) {
    super(name);
  }

  run(): void {
    console.log(`${this.name}在运动--子类`); // 子类能访问
  }
}
let c = new Child("李四");
c.run(); // 李四在运动--子类
console.log(c.name); // 在类外面能访问
```

**protected**

```ts
class Person {
  protected name: string; // 保护

  constructor(name: string) {
    this.name = name;
  }
  run(): void {
    console.log(`${this.name}在运动`); // 在类里能访问
  }
}
let p = new Person("张三");
p.run();
// console.log(p.name); // 报错，在类外面不能访问

class Child extends Person {
  constructor(name: string) {
    super(name);
  }
  run(): void {
    console.log(`${this.name}在运动--子类`); // 子类能访问
  }
}
let c = new Child("李四");
c.run(); // 李四在运动--子类
// console.log(c.name); // 报错，在类外面不能访问
```

**private**

```ts
class Person {
  private name: string; // 私有
  constructor(name: string) {
    this.name = name;
  }
  run(): void {
    console.log(`${this.name}在运动`); // 在类里能访问
  }
}
let p = new Person("张三");
p.run();
// console.log(p.name); // 报错，在类外面不能访问

class Child extends Person {
  constructor(name: string) {
    super(name);
  }

  run(): void {
    // console.log(`${this.name}在运动--子类`); // 报错，子类不能访问
  }
}
let c = new Child("李四");
c.run(); // 李四在运动--子类
// console.log(c.name); // 报错，在类外面不能访问
```

### 静态属性和方法

使用 static 修饰符修饰的方法称为静态方法，它们不需要实例化，而是直接通过类来调用，若加上修饰符有，和其他属性和方法效果一样。

ES5 中的静态方法、静态属性：

```js
function Person() {
  this.run1 = function () {}; // 实例方法，实例化后调用
}

Person.run2 = function () {}; // 静态方法，类名直接调用
Person.name = "lucy"; // 静态属性
Person.run2(); // 静态方法的调用
```

TypeScript 中的静态方法、静态属性：

```ts
class Person {
  public name: string;
  public age: number = 20;
  static sex = "男"; // 静态属性
  constructor(name: string) {
    this.name = name;
  }
  run() {
    console.log(`${this.name}在运动`);
  }
  work() {
    console.log(`${this.name}在工作`);
  }
  static print() {
    console.log("print静态方法" + Person.sex); // 静态方法，没法直接调用类的属性
  }
}
var p = new Person("tony");
p.work();
p.run();
Person.sex; // 男
Person.print();
```

### 抽象类

`abstract` 用于定义抽象类和其中的抽象方法。

什么是抽象类？首先，抽象类是不允许被实例化的。其次，抽象类中的抽象方法必须被子类实现。 

```ts
abstract class Animal {
  public name;
  public constructor(name) {
    this.name = name;
  }
  public abstract sayHi();
}

class Cat extends Animal {
  public sayHi() {
    alert(`Meow, My name is ${this.name}`);
  }
}
let cat = new Cat("Tom");
cat.sayHi();
```

## [  函数 ]

函数是 JavaScript 应用程序的基础。 它帮助你实现抽象层，模拟类，信息隐藏和模块。在 TypeScript 里，函数仍然是主要的定义行为的地方。 TypeScript 为 JavaScript 函数添加了额外的功能，让我们可以更容易地使用。 

### 函数的定义 

和 JavaScript 一样，TypeScript 函数可以创建有名字的函数和匿名函数。 你可以随意选择适合应用程序的方式，不论是定义一系列 API 函数还是只使用一次的函数。

**ES5 函数定义**：函数声明、匿名函数、传参。

```js
// 函数声明
function fn1() {
  console.log(123);
}
fn1(); // 调用

// 匿名函数
let fn2 = function () {
  console.log(456);
};
fn2();

// 传参
function fn3(name, age) {
  console.log(`姓名：${name}，年龄：${age}`);
}
fn3("张三", 18);
```

**TypeScript 函数定义**：函数声明、匿名函数、传参。

```ts
// 函数声明
function fn1(): number {
  // number 是函数返回值类型，没有返回值为 void
  console.log("有返回值");
  return 123;
}
fn1();

// 匿名函数
let fn2 = function (): void {
  console.log(456);
};
fn2();
// 传参
function fn3(name: string, age: number): void {
  console.log(`姓名：${name}，年龄：${age}`);
}
fn3("张三", 18);
```

### 参数

- **可选参数** 

  ES5 里面方法的实参和行参可以不一样，但是 TypeScript 中必须一样，如果不一样就需要配置可选参数。

  ```ts
  function getInfo(name: string, age?: number): string {
    // age 为可选参数
    if (age) {
      return `姓名：${name}，年龄：${age}`;
    } else {
      return `姓名：${name}，年龄：保密`;
    }
  }
  console.log(getInfo("张三", 18));
  console.log(getInfo("李四"));
  ```

  注意：可选参数必须配置到参数的最后面。

- **默认参数**

  ES5 里面不能设置默认参数，ES6 和 TypeScript 中都可以设置默认参数。

  ```ts
  function getInfo(name: string, age: number = 20): string {
    // age 默认为20
    if (age) {
      return `姓名：${name}，年龄：${age}`;
    } else {
      return `姓名：${name}，年龄：保密`;
    }
  }
  console.log(getInfo("张三", 18)); // 姓名：张三，年龄：18
  console.log(getInfo("李四")); // 姓名：李四，年龄：20
  ```

- **剩余参数**

  ES6 中，可以使用 `...rest` 的方式获取函数中的剩余参数。

  事实上，`items` 是一个数组。所以我们可以用数组的类型来定义它，在 TypeScript 里，你可以把所有参数收集到一个变量里。

  ```ts
  function push(array, ...items) {
    items.forEach(function (item) {
      array.push(item);
    });
  }
  
  let a = [];
  push(a, 1, 2, 3);
  alert(a);
  ```

### 用接口定义函数的形状

我们也可以使用接口的方式来定义一个函数需要符合的形状。

```ts
interface Fn {
  (x: number, y: number): boolean;
  //左边表示函数的输入类型，右边表示输出类型
}

let fn: Fn;
fn = function (x: number, y: number) {
  return x > y;
};
```

### 函数重载 

重载指的是两个或者两个以上同名函数，但它们的参数不一样，这时会出现函数重载的情况。

**JavaScript 中方法的重载**

ES5 中出现同名方法，下面的会替换上面的方法：

```js
function getInfo(name) {}
function getInfo(name, age) {}
```

**Typescript 中的重载**

通过为同一个函数提供多个函数类型定义来实现多种功能的目的。

1. 单个参数，不同类型。

	```ts
function getInfo(name: string): string;
function getInfo(age: number): string;
function getInfo(str: any): any {
    if (typeof str === "string") {
    alert(`姓名：${str}`);
    } else {
    alert(`年龄：${str}`);
    }
}
getInfo("张三");
getInfo(18);
getInfo(true); // 错误的写法
	```

2. 多个参数，可选参数。

	```ts
function getInfo(name: string): string;
function getInfo(name: string, age: number): string;
function getInfo(name: string, age?: number): void {
    if (age) {
    alert(`姓名：${name}，年龄：${age}`);
    } else {
    alert(`姓名：${name}`);
    }
}
getInfo("张三");
getInfo(18); // 错误
getInfo("李四", 20);
	```

## [ 模块 ]

从 ECMAScript 2015 开始，JavaScript 引入了模块的概念。 TypeScript 也沿用这个概念。模块在其自身的作用域里执行，而不是在全局作用域里。这意味着定义在一个模块里的变量，函数，类等等在模块外部是不可见的，除非你使用 export 导出它们。 相反，如果想使用其它模块导出的变量，函数，类，接口等的时候，你可以通过 import 导入它们。 

### 模块的导入与导出

模块是自声明的。在 TypeScript 里，两个模块之间的关系是通过在文件级别上使用 import 和 export 建立的。下面是一个基本例子：

```ts
//a.ts
export class Animal {
  name: string;
  show(): string {
    return this.name;
  }
}
//b.ts
import { Animal } from "./a";
let dog = new Animal();
dog.name = "狗狗";
dog.show();
console.log(dog.name);
```

上面的例子里，在 `a.ts` 里声明了一个类 Animal，通过 export 导出。在 `b.ts` 里，指定相对文件路径，通过 import 导入，就可以使用 Animal 类。

执行以下命令进行编译：

```bash
$ tsc b.ts
$ node b.js
```

### 导入和导出的重命名



模块导入和导出时默认使用的内部对象的名称。TypeScript 也支持在导出前和导入后进行重命名。将上面的例子修改一下:

```ts
//a.ts
class Animal {
  name: string;
  show(): string {
    return this.name;
  }
}
export { Animal as ANI };
//b.ts
import { ANI as Animal } from "./a";
let dog = new Animal();
dog.name = "狗狗";
dog.show();
console.log("重命名-狗狗");
```

导入和导出时，通过 `as` 关键字对模块进行重命名。这个地方有一点要注意，当导出的模块重命名后，导入时重命名前的模块名要与导出重命名后的模块名保持一致，否则编译器将提示错误信息。以上面的这个例子为例，导出的模块被重命名为`ANI`，将此模块在另外一个文件 `b.ts`里导入时，`as` 关键字前面的模块名必须是 `ANI`。

如果不知道导入模块的名称，则可以用 `*` 号代替。

```ts
//b.ts
import * as animal_module from "./a";
let dog = new animal_module.ANI();
dog.name = "狗狗";
dog.show();
console.log("重命名-狗狗-*");
```

### 导出和导出多个对象

通常情况，模块里会定义多个类型对象，然后一并导出。而导入的模块里也可能会有多个。

```ts
//a.ts
enum Color {
  Red = "Red",
  Blue = "Blue",
  White = "White",
}

class Animal {
  name: string;
  color: Color;
  show(): string {
    return this.name + this.color;
  }
}

export { Animal, Color };
//b.ts
import * as animal_module from "./a";
let dog = new animal_module.Animal();
dog.name = "狗狗";
dog.color = animal_module.Color.Red;
dog.show();
console.log(dog.name + dog.color);
```

### 默认导出

对于导出内容的命名无关紧要，只要给定名称即可，但默认导出只有一个。

```ts
//a.ts
class Animal {
  name: string;
  show(): string {
    return this.name;
  }
}

export default Animal;
//b.ts
import Animal from "./a";
let dog = new Animal();
dog.name = "狗狗";
dog.show();
console.log(dog.name);
```

## [ 命名空间 ]

命名空间（之前叫做“内部模块”），一个最明确的目的就是解决重名问题。假设这样一种情况，当一个班上有两个名叫小明的学生时，为了明确区分它们，我们在使用名字之外，不得不使用一些额外的信息，比如他们的姓（王小明，李小明），或者他们父母的名字等等。

一个最明确的目的就是解决重名问题。假设这样一种情况，当一个班上有两个名叫小明的学生时，为了明确区分它们，我们在使用名字之外，不得不使用一些额外的信息，比如他们的姓（王小明，李小明），或者他们父母的名字等等。

命名空间定义了标识符的可见范围，一个标识符可在多个名字空间中定义，它在不同名字空间中的含义是互不相干的。这样，在一个新的名字空间中可定义任何标识符，它们不会与任何已有的标识符发生冲突，因为已有的定义都处于其他名字空间中。

一个文件就是一个模块， “内部模块”就是文件里面，是我们写代码的地方，为了防止可能出现命名冲突，出现了命名空间，防止程序员命名冲突，“外部模块”就是一个文件。以前 TypeScript 把命名空间写成 `module X{}` ，module 英文就是模块的意思，为了防止与 ES6 冲突特地改成命名空间（namespace）。

TypeScript 中命名空间使用 `namespace` 来定义，语法格式如下：

```ts
namespace SomeNameSpaceName {
  export interface ISomeInterfaceName {}
  export class SomeClassName {}
}
```

以上定义了一个命名空间 `SomeNameSpaceName`，如果我们需要在外部可以调用 `SomeNameSpaceName` 中的类和接口，则需要在类和接口添加 `export` 关键字。

以下实例演示了命名空间的使用，定义在不同文件中：

```ts
//a.ts
export namespace A {
  export class People {}
  export const height: number = 180;
  export function main(): void {}
}
//b.ts
import { A } from "./a";
console.log(A.People);
```

但是官方却推荐使用三斜线指令语法，其实都多文件了使用了。

```ts
//a.ts
namespace A {
  export class People {}
  export const height: number = 180;
  export function main(): void {}
}
//b.ts
/// <reference path="./a.ts" />
console.log(A);
```

程序不能立刻执行，否则会报错，因为要确保所有编译后的代码都被加载了，所以需要把所有的输入文件编译为一个输出文件，使用 `--outFile` 实现：

```bash
tsc --outFile sample.js b.ts
```

 编译成功后生成 `sample.js`，在 `index.html` 内用`script`标签引入 。

### 嵌套命名空间

可以在另一个命名空间中定义一个命名空间：

```ts
namespace namespace_name1 {
  export namespace namespace_name2 {
    export class class_name {}
  }
}
```

可以用点（.）运算符访问嵌套命名空间的成员，如下所示：

```ts
//a.ts
namespace space1 {
  export namespace addApp {
    export class add {
      public addCount(price: number) {
        return price + 10;
      }
    }
  }
}
//b.ts
/// <reference path="a.ts" />
var add = new space1.addApp.add();
console.log(add.addCount(500));
```

### 命名空间与模块

**命名空间**：将具有相似功能的代码都归一到同一个空间下进行管理，方便其他代码引用，更多的是侧重代码的复用。

**模块**：一个完整功能的封装，对外提供的是一个具有完整功能的功能包，需要显式引用。一个模块里可能会有多个命名空间。
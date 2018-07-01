# JavaSrcipt代码规范(微信小程序)

本文档参考[Google的JavaSrcipt代码规范](https://google.github.io/styleguide/jsguide.html#source-file-basics)

## 1.源文件基础

### 1.1 文件名称
文件名必须全部小写，可以包含下划线(_)或短划线(-)，但不得包含其他标点符号。遵循你的项目使用的约定。文件名的扩展名必须是`.js`。

### 1.2 文件编码：UTF-8
源文件以UTF-8编码

### 1.3 特殊字符

#### 1.3.1 空白字符
除行终止符序列外，ASCII水平空格字符（0x20）是唯一出现在源文件中任何位置的空格字符。

- 字符串文字中的所有其他空格字符都会被转义
- 制表符不用于缩进

#### 1.3.2 特殊的转义序列
对于具有特殊的转义序列（任何字符`\'`，`\"`，`\\`，`\b`，`\f`，`\n`，`\r`，`\t`，`\v`），该序列使用，而不是对应的数字逃逸（例如`\x0a`，`\u000a`或`\u{a}`）。

#### 1.3.3 非ASCII字符
对于其余的非ASCII字符，使用实际的Unicode字符（例如`∞`）或等效的十六进制或Unicode转义（例如`\u221e`），这仅取决于哪一个使得代码更易于阅读和理解。

## 2.格式化

### 2.1 大括号

#### 2.1.1 大括号用于所有控制结构
大括号都需要所有的控制结构（即`if`，`else`，`for`，`do`，`while`，以及任何其他），即使身体只包含一个声明。非空块的第一条语句必须从其自己的行开始。

非法:
```javascript
if (someVeryLongCondition())
  doSomething();

for (let i = 0; i < foo.length; i++) bar(foo[i]);
```

异常：一个简单的if语句可以完全适用于单行而没有包装（并且没有其他包装），但它可以保存在一行中，而且不会出现大括号，这样可以提高可读性。这是控制结构可以忽略大括号和换行符的唯一情况。
```javascript
if (shortCondition()) return;
```

#### 2.1.2 非空块：K＆R风格
大括号遵循Kernighan和里奇风格（[埃及方括号](https://blog.codinghorror.com/new-programming-jargon/)）为非空块和块状构造：

- 在左大括号(opening brace)之前没有换行符。
- 在左大括号(opening brace)之后换行。
- 在右大括号(closing brace)之前换行。
- 如果大括号终止语句或函数或类语句或类方法的主体，则在右大括号(closing brace)后面换行。具体而言，有没有支架后换行符如果随后`else`，`catch`，`while`，或逗号，分号，或右括号。

例：
```javascript
class InnerClass {
  constructor() {}

  /** @param {number} foo */
  method(foo) {
    if (condition(foo)) {
      try {
        // Note: this might fail.
        something();
      } catch (err) {
        recover();
      }
    }
  }
}
```

### 2.1.3 空白块：可能简洁
一个空的块或块状结构可以在其打开后立即关闭，在它们之间没有字符，空格或换行符`{}`，除非它是多块语句的一部分（直接包含多个块：`if`/`else`或`try`/`catch`/`finally`）。

例：
```javascript
function doNothing() {}
```

非法:
```javascript
if (condition) {
  // ...
} else if (otherCondition) {} else {
  // ...
}

try {
  // ...
} catch (e) {}
```

### 2.2 块缩进：+2个空格
每次打开一个新的块或块状构造时，缩进都会增加两个空格。块结束后，缩进将返回到前一个缩进级别。缩进级别适用于整个块中的代码和注释。（请参阅2.1.2非空块的示例：K＆R样式）

#### 2.2.1数组文字：可选地为“块状”
任何数组字面值可以选择性地格式化，就像它是“块状结构”一样。例如，以下全部是有效的（不是详尽的列表）：

```javascript
const a = [
  0,
  1,
  2,
];

const b =
  [0, 1, 2];

const c = [0, 1, 2];

someMethod(foo, [
  0, 1, 2,
], bar);
```

允许其他组合，特别是在强调元素之间的语义分组时，但不应仅用于减小较大阵列的垂直大小。

#### 2.2.2 对象文字：可选“块状”
任何对象文字都可以选择格式化，就好像它是一个“块状结构”。相同的例子适用于2.2.1数组文字：可选择类似块。例如，以下都是有效的（不是详尽的列表）：

```javascript
const a = [
  a: 0,
  b: 1,
  c: 2,
];

const b =
  [a: 0, b: 1, c: 2];

const c = [a: 0, b: 1, c: 2];

someMethod(foo, [
  a: 0, b: 1, c: 2,
], bar);
```

#### 2.2.3 类文字
类文字（不论是声明还是表达式）被缩进为块。不要在方法之后添加分号，也不要在类声明的右括号之后添加分号 （包含类表达式的语句（如分配）仍以分号结尾）。除非类扩展了模板化类型，否则请使用`extends`关键字，但不要使用`@extends`JSDoc注释。

例：
```javascript
class Foo {
  constructor() {
    /** @type {number} */
    this.x = 42;
  }

  /** @return {number} */
  method() {
    return this.x;
  }
}

Foo.Empty = class {};

/** @extends {Foo<string>} */
foo.Bar = class extends Foo {
  /** @override */
  method() {
    return super.method() / 2;
  }
};

/** @interface */
class Frobnicator {
  /** @param {string} message */
  frobnicate(message) {}
}
```

#### 2.2.4 函数表达式
在函数调用的参数列表中声明一个匿名函数时，函数的主体会比前面的缩进深度缩进两个空格。

例：
```javascript
prefix.something.reallyLongFunctionName('whatever', (a1, a2) => {
  // Indent the function body +2 relative to indentation depth
  // of the 'prefix' statement one line above.
  if (a1.equals(a2)) {
    someOtherLongFunctionName(a1);
  } else {
    andNowForSomethingCompletelyDifferent(a2.parrot);
  }
});

some.reallyLongFunctionCall(arg1, arg2, arg3)
    .thatsWrapped()
    .then((result) => {
      // Indent the function body +2 relative to the indentation depth
      // of the '.then()' call.
      if (result) {
        result.use();
      }
    });
```

#### 2.2.5 交换语句
与其他任何块一样，开关块的内容都是缩进+2。

切换标签后，出现一个换行符，缩进级别增加+2，就好像一个块被打开一样。如果词法作用域需要，可以使用明确的块。下面的切换标签返回到前一个缩进级别，就像块已关闭一样。

`break`与下列情况之间的空行是可选的。

```javascript
switch (animal) {
  case Animal.BANDERSNATCH:
    handleBandersnatch();
    break;

  case Animal.JABBERWOCK:
    handleJabberwock();
    break;

  default:
    throw new Error('Unknown animal');
}
```

### 2.3 声明

#### 2.3.1 每行一条语句
每条语句后跟一个换行符。

#### 2.3.2 需要使用分号
每个语句都必须以分号结尾。禁止使用自动分号插入。

### 2.4 换行

#### 2.4.1 哪里打破
换行的主要指令是：更喜欢在更高的句法层面上打破。

推荐:
```javascript
currentEstimate =
    calc(currentEstimate + x * currentEstimate) /
        2.0f;
```

不推荐:
```javascript
currentEstimate = calc(currentEstimate + x *
    currentEstimate) / 2.0f;
```

在前面的例子中，从最高到最低的语法级别如下：赋值，除法，函数调用，参数，数字常量。

- When a line is broken at an operator the break comes after the symbol.
- A method or constructor name stays attached to the open parenthesis (`(`) that follows it.
- A comma (`,`) stays attached to the token that precedes it.

注意：换行的主要目标是具有清晰的代码，不一定代码适合最小数量的行。

#### 2.4.2 缩进连续线至少+4个空格
当换行时，第一行（每个连续行）之后的每一行从原始行至少缩进+4，除非它符合块缩进的规则。

当有多条连续线时，缩进可以根据情况变化超过+4。一般而言，更深层语法级别的延续线以4的较大倍数缩进，并且两行使用相同的缩进级别当且仅当它们以语法上并行的元素开始时。

### 2.5 空白

#### 2.5.1 垂直空白
出现一个空行的地方：
- 在类或对象文字中的连续方法之间
例外：对象文本中两个连续属性定义之间的空白行（其间没有其他代码）是可选的。根据需要使用这些空白行来创建字段的逻辑分组。
- 在方法体内，谨慎地创建语句的逻辑分组。不允许在函数体的开始或结束处出现空行。
- 可选地，在类或对象字面量中的第一个或最后一个方法之前（既不鼓励也不鼓励）。

允许多个连续的空白行，但从不要求（也不鼓励）。

#### 2.5.2 水平空白
水平空白符的使用取决于位置，分为三大类：领先的（在一行的开始处），尾随的（在行的末尾）和内部的。领先的空白（即缩进）在其他地方处理。尾随空格是禁止的。

除了语言或其他样式规则的要求之外，除了文字，注释和JSDoc之外，单个内部的空格也仅出现在以下位置：

- 将任何保留字（如`if`，`for`或`catch`）与紧跟其后的开括号`(`相分离。
- 将任何保留字（如`else`或`catch`）与之前的结束大括号`}`相分离。
- 在任何打开大括号（`{`）之前，有两个例外：
- 在作为函数的第一个参数的对象字面量或数组文字中的第一个元素之前（例如`foo({a: [{c: d}]})`）。
- 在模板扩展中，因为它被语言禁止（例如`abc${1 + 2}def`）。
- 任何二进制或三元运算符的两侧。
- 用逗号（`,`）或分号（`;`）后。请注意，这些字符之前永远不允许有空格。
- 在对象文字中的冒号`:`之后。
- 在双斜线（`//`）的双方，开始行尾评论。这里允许多个空格，但不是必需的。
- 在一个打开的JSDoc注释字符和两个关闭字符之后（例如对于短格式类型的声明或强制转换：`this.foo = /** @type {number} */ (bar);`或`function(/** string */ foo) {`）。

#### 2.5.3 函数参数
倾向于将所有函数参数放在与函数名称相同的行上。如果这样做会超过80列的限制，则参数必须以可读的方式进行换行。为了节省空间，您可以尽可能地将其包装为80，或者将每个参数放在一行以增强可读性。缩进应该是四个空格。允许与括号对齐，但不鼓励。以下是自变换最常见的模式：

```javascript
// 参数从新行开始，缩进四个空格。首选的时候
// 参数不符合函数名称（或关键字）的同一行
// “function”），但完全适合第二行。与非常长的作品
// 函数名称，在没有重新加载的情况下重命名，空间不足。
doSomething(
    descriptiveArgumentOne, descriptiveArgumentTwo, descriptiveArgumentThree) {
  // ...
}

// 如果参数列表更长，则在80处换行。使用较少的垂直空间，
// 但违反了矩形规则，因此不推荐。
doSomething(veryDescriptiveArgumentNumberOne, veryDescriptiveArgumentTwo,
    tableModelEventHandlerProxy, artichokeDescriptorAdapterIterator) {
  // ...
}

// 四行，每行一个参数。使用长功能名称，
// 保留重命名，并强调每个参数。
doSomething(
    veryDescriptiveArgumentNumberOne,
    veryDescriptiveArgumentTwo,
    tableModelEventHandlerProxy,
    artichokeDescriptorAdapterIterator) {
  // ...
}
```

### 2.6 评论

#### 2.6.1 阻止评论风格
块注释缩进与周围代码相同的级别。他们可能在`/* ... */`或`//`风格。对于多行`/* ... */`注释，后续行必须以`*`与`*`前一行对齐的方式开始，以使注释显而易见且不需要额外的上下文。只要值和方法名称不能充分表达意义，“参数名称”注释就会出现在值之后。

```javascript
/*
 * This is
 * okay.
 */

// And so
// is this.

/* This is fine, too. */

someFunction(obviousParam, true /* shouldRender */, 'hello' /* name */);
```

评论不包含在用星号或其他字符绘制的框中。
不要将JSDoc（`/** ... */`）用于任何上述实现注释。

## 3.语言功能

### 3.1 局部变量声明

#### 3.1.1 使用`const`和`let`
声明所有的局部变量有两种`const`或`let`。默认情况下使用`const`，除非需要重新分配一个变量。`var`不得使用该关键字。

#### 3.1.2 每个声明一个变量
每个局部变量声明只声明一个变量。`let a = 1, b = 2;`是不合适的。

#### 3.1.3 在需要时声明，尽快初始化
局部变量不会在其包含块或块状构造的开始处习惯性地声明。相反，局部变量被声明为接近他们第一次使用的点（在合理的范围内），以最小化它们的范围。

### 3.2 数组文字

#### 3.2.1 使用尾随逗号
在最终元素和右括号之间存在换行符时，请包含尾随逗号。

例：
```javascript
const values = [
  'first value',
  'second value',
];
```

#### 3.2.2 不要使用可变参数`Array`构造函数
如果添加或删除参数，则构造函数容易出错。

非法：
```javascript
const a1 = new Array(x1, x2, x3);
const a2 = new Array(x1, x2);
const a3 = new Array(x1);
const a4 = new Array();
```

除第三种情况外，这种方式可以正常工作：如果`x1`是整数，然后`a3`是`x1`所有元素都是大小的数组`undefined`。如果`x1`是任何其他数字，则将引发异常，如果是其他数字，则它将是单元素数组。

建议：
```javascript
const a1 = [x1，x2，x3];
const a2 = [x1，x2];
const a3 = [x1];
const a4 = [];
```

`new Array(length)`在适当情况下，允许显式分配给定长度的数组。

#### 3.2.3 非数字属性
不要在数组上定义或使用非数字属性（除外`length`）。使用`Map`（或`Object`）代替。

### 3.3 对象文字

#### 3.3.1 使用尾随逗号
只要最终属性和右大括号之间存在换行符，请包含尾随逗号。

#### 3.3.2 不要使用`Object`构造函数
虽然`Object`没有`Array`与之相同的问题，但仍然不允许保持一致性。改用对象文字（`{}`或`{a: 0, b: 1, c: 2}`）。

#### 3.3.3 不要混用带引号和不带引号的键
对象文字可以表示结构（带有未加引号的键和`/`或符号）或字典（带引号和`/`或计算键）。不要将这些键类型混合在单个对象文字中。

非法：
```javascript
{
  a: 42, // struct-style unquoted key
  'b': 43, // dict-style quoted key
}
```

#### 3.3.4 方法简写
可以使用方法shorthand（`{method() { ... }}`）代替立即紧跟着一个function或一个箭头函数文字的冒号来在对象文字上定义方法。

例：
```javascript
return {
  stuff: 'candy',
  method() {
    return this.stuff;  // Returns 'candy'
  },
};
```

请注意，this在方法中，速记或function引用对象字面本身，而this在箭头函数中引用对象字面量之外的范围。

例：
```javascript
class {
  getObjectLiteral() {
    this.stuff = 'fruit';
    return {
      stuff: 'candy',
      method: () => this.stuff,  // Returns 'fruit'
    };
  }
}
```

#### 3.3.5 速记属性
对象文字允许使用简写属性。

例：
```javascript
const foo = 1;
const bar = 2;
const obj = {
  foo,
  bar,
  method() { return this.foo + this.bar; },
};
assertEquals(3, obj.method());
```

### 3.4 函数

#### 3.4.1 顶级函数
导出的函数可以直接在`exports`对象上定义，或者在本地声明并单独导出。鼓励非出口功能，不应声明`@private`。

例：
```javascript
/** @return {number} */
function helperFunction() {
  return 42;
}
/** @return {number} */
function exportedFunction() {
  return helperFunction() * 2;
}
/**
 * @param {string} arg
 * @return {number}
 */
function anotherExportedFunction(arg) {
  return helperFunction() / arg.length;
}
/** @const */
exports = {exportedFunction, anotherExportedFunction};
```

#### 3.4.2 嵌套函数和闭包
函数可能包含嵌套的函数定义。如果给函数一个名字是有用的，它应该被分配给一个本地`const`。

#### 3.4.3 参数
函数参数必须在函数定义之前的JSDoc中使用JSDoc注释进行键入，除非相同签名`@override`是s，省略所有类型。

参数类型可以在参数名称之前立即指定（如`(/** number */ foo, /** string */ bar) => foo + bar`）。内联和`@param`类型注释不得在同一个函数定义中混合使用。

##### 3.4.3.1 默认参数
使用参数列表中的等号运算符允许可选参数。可选参数必须在等号运算符的两边包含空格，完全像需要的参数（即，没有前缀`opt_`）命名，`=`在其JSDoc类型中使用后缀，在需要的参数之后，并且不使用产生可观察副作用的初始化程序。即使该值为，所有可选参数在函数声明中都必须具有默认值`undefined`。

例：
```javascript
/**
 * @param {string} required This parameter is always needed.
 * @param {string=} optional This parameter can be omitted.
 * @param {!Node=} node Another optional parameter.
 */
function maybeDoSomething(required, optional = '', node = undefined) {}
```

##### 3.4.3.2 休息参数
使用休息参数而不是访问`arguments`。Rest参数`...`在JSDoc中使用前缀进行输入。其余参数必须是列表中的最后一个参数。`...`与参数名称之间没有空格。不要命名其余参数`var_args`。永远不要命名局部变量或参数`arguments`，这会混淆内部名称。

例：
```javascript
/**
 * @param {!Array<string>} array This is an ordinary parameter.
 * @param {...number} numbers The remainder of arguments are all numbers.
 */
function variadic(array, ...numbers) {}
```

### 3.5 字符串文字

#### 3.5.1 使用单引号
普通字符串文字用单引号（`'`）分隔，而不是双引号（`"`）。
```
提示：如果某个字符串包含单引号字符，请考虑使用模板字符串以避免必须转义引号。
```
普通字符串文字不能跨越多行。

#### 3.5.2 模板字符串
使用模板字符串（用分隔\`）复杂字符串连接，特别是涉及多个字符串文字时。模板字符串可能跨越多行。
如果一个模板字符串跨越多行，它不需要遵循封闭块的缩进，尽管如果添加的空白不重要的话。

例：
```javascript
function arithmetic(a, b) {
  return `Here is a table of arithmetic operations:
${a} + ${b} = ${a + b}
${a} - ${b} = ${a - b}
${a} * ${b} = ${a * b}
${a} / ${b} = ${a / b}`;
}
```

#### 3.5.3 无续行
不要在普通模板字符串或模板字符串文字中使用换行符（即，在带有反斜杠的字符串文字中结束一行）。

非法：
```javascript
const longString = 'This is a very long string that far exceeds the 80 \
    column limit. It unfortunately contains long stretches of spaces due \
    to how the continued lines are indented.';
```

建议：
```javascript
const longString = 'This is a very long string that far exceeds the 80 ' +
    'column limit. It does not contain long stretches of spaces since ' +
    'the concatenated strings are cleaner.';
```

### 3.6 数字
数字可以用十进制，十六进制，八进制或二进制指定。使用完全相同`0x`，`0o`和`0b`(小写)前缀，分别代表十六进制，八进制和二进制。除非立即跟着`x`，`o`和`b`，否则以`0`开头 。

### 3.7 For循环
尽可能使用`for-of`结构

### 3.8 不允许的功能

#### 3.8.1 with
不要使用`with`关键字。

#### 3.8.2 动态代码评估
不要使用`eval`或`Function(...string)`构造函数（代码加载器除外）。

#### 3.8.3 自动分号插入
始终以分号终止语句（除函数和类声明外，如上所述）。

#### 3.8.4 非标准功能
不要使用非标准功能。

#### 3.8.5 原始类型的包装对象
从不使用`new`对原始对象包装（`Boolean`，`Number`，`String`，`Symbol`），也不将它们包括在类型注释。

非法：
```javascript
const /** Boolean */ x = new Boolean(false);
if (x) alert(typeof x);  // alerts 'object' - WAT?
```

这些包装可能被称为强制函数（比使用+或连接空字符串更优先）或创建符号。
例：
```javascript
const /** boolean */ x = Boolean(0);
if (!x) alert(typeof x);  // alerts 'boolean', as expected
```

## 4.命名

### 4.1 所有标识符通用的规则
标识符只使用ASCII字母和数字。
在合理的范围内尽可能描述一个名称。不必担心节省水平空间，因为让新代码立即可以让您的代码易于理解是非常重要的。不要使用项目外读者不明确或不熟悉的缩写，也不要通过删除单词中的字母来缩写。

```javascript
priceCountReader   //没有缩写。
numErrors  //“num”是一个普遍的约定。
numDnsConnections  //大多数人都知道“DNS”代表什么。
```

非法：
```javascript
n  //无意义。
nErr   //含糊不清的缩写。
nCompConns //不明确的缩写。
wgcConnections //只有你的小组知道这代表什么。
pcReader   //很多东西都可以缩写为“pc”。
cstmrId//删除内部字母。
kSecondsPerDay //不要使用匈牙利符号。
```

### 4.2 按标识符类型的规则

#### 4.2.1 方法名称
方法名称使用`lowerCamelCase`。私有方法的名称必须以尾部下划线结尾。

方法名称通常是动词或动词短语。例如，`sendMessage`或`stop_`。房产`getter`和`setter`方法从来没有被要求，但如果他们使用它们应该被命名为`getFo`（或可选`isFoo`或`hasFoo`为布尔值），或`setFoo(value)`用于制定者。

#### 4.2.2 常数名称
常量名称使用`CONSTANT_CASE`：所有大写字母，并用下划线分隔单词。没有理由使用尾部下划线来命名常量，因为私有静态属性可以被（隐式私有）模块本地代替。

#### 4.2.3 非常量字段名称
非常量字段名称（静态或其他）使用`lowerCamelCase`，私人字段的尾部下划线。

这些名称通常是名词或名词短语。例如，`computedValues`或`index_`。

#### 4.2.4 参数名称
使用`lowerCamelCase`。

#### 4.2.5 局部变量名称
使用`lowerCamelCase`。

### 4.3 使用`var`

#### 4.3.1 `var`声明不是块范围的
`var`声明的范围是最近的封闭函数，脚本或模块的开始，这可能会导致意外的行为，尤其是对于`var`在循环内引用声明的函数闭包。以下代码给出了一个例子：

```javascript
for (var i = 0; i < 3; ++i) {
  var iteration = i;
  setTimeout(function() { console.log(iteration); }, i*1000);
}

// logs 2, 2, 2 -- NOT 0, 1, 2
// because `iteration` is function-scoped, not local to the loop.
```

#### 4.3.2 声明变量尽可能接近首次使用
尽管`var`声明的范围仅限于封闭函数的开始部分`var`，但出于可读性的目的，声明应尽可能地接近它们的首次使用。但是，`var`如果该变量在块之外被引用，则不要在块内放置声明。例如：

```javascript
function sillyFunction() {
  var count = 0;
  for (var x in y) {
    // "count" could be declared here, but don't do that.
    count++;
  }
  console.log(count + ' items in y');
}
```
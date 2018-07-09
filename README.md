# Dart 语言简明教程
**翻译自 Dart 官网，[查看原文](https://www.dartlang.org/guides/language/language-tour)。**

这篇文章展示如何使用 Dart 的各个主要特性，从变量和运算符到类和库，并且假定你已经会使用其他编程语言编写代码。
要详细了解 Dart 核心库相关内容，请看官方 [A Tour of the Dart Libraries](https://www.dartlang.org/guides/libraries/library-tour)。当你想对一个语言特性了解更多，无论何时都可以查阅官方 [Dart Language Specification](https://www.dartlang.org/guides/language/spec)。

> 小提示：在 DartPad 上，你可以尝试大部分 Dart 的语言特性（[了解更多](https://www.dartlang.org/tools/dartpad)）。
>
> 转到 [DartPatd](https://dartpad.dartlang.org/)

## 目录
* [一个基本的 Dart 程序](#一个基本的-dart-程序)
* [重要概念](#重要概念)
* [关键字](#关键字)
* [变量](#变量)
  * [默认值](#默认值)
  * [Final 和 const](#final-和-const)
* [内置类型](#内置类型)
  * [数值](#数值)
  * [字符串](#字符串)
  * [布尔](#布尔)
  * [列表](#列表)
  * [映射](#映射)
  * [符文](#符文)
  * [符号](#符号)
* [函数](#函数)
  * [可选参数](#可选参数)
  * [main() 函数](#main()-函数)
  * [函数作为一等对象](#函数作为一等对象)
  * [匿名函数](#匿名函数)
  * [词法作用域](#词法作用域)
  * [词法闭包](#词法闭包)
  * [验证函数的相等性](#验证函数的相等性)
  * [返回值](#返回值)
* [运算符](#运算符)
  * [算术运算符](#算术运算符)
  * [相等和关系运算符](#相等和关系运算符)
  * [类型检测运算符](#类型检测运算符)
  * [赋值运算符](#赋值运算符)
  * [逻辑运算符](#逻辑运算符)
  * [按位和移位运算符](#按位和移位运算符)
  * [条件运算符](#条件运算符)
  * [级联符号](#级联符号)
  * [其他运算符](#其他运算符)
* [控制流程语句](#控制流程语句)
  * [If 和 else](#if-和-else)
  * [For 循环](#for-循环)
  * [While 和 do-while](#while-和-do-while)
  * [Break 和 continue](#break-和-continue)
  * [Switch 和 case](#switch-和-case)
  * [Assert](#assert)
* [异常](#异常)
  * [Throw](#throw)
  * [Catch](#catch)
  * [Finally](#finally)
* [类](#类)
  * [使用类成员](#使用类成员)
  * [使用构造函数](#使用构造函数)
  * [获取对象类型](#获取对象类型)
  * [实例变量](#实例变量)
  * [构造函数](#构造函数)
  * [方法](#方法)
  * [抽象类](#抽象类)
  * [隐式接口](#隐式接口)
  * [扩展一个类](#扩展一个类)
  * [重写类成员](#重写类成员)
  * [可枚举类型](#可枚举类型)
  * [为一个类添加特新：混入](#为一个类添加特新：混入)
  * [类变量和方法](#类变量和方法)
* [泛型](#泛型)
  * [为什么用泛型？](#为什么用泛型？)
  * [使用集合字面量](#使用集合字面量)
  * [使用带构造函数的参数化类型](#使用带构造函数的参数化类型)
  * [泛型集合和它们包含的类型](#泛型集合和它们包含的类型)
  * [限制参数化类型](#限制参数化类型)
  * [使用泛型方法](#使用泛型方法)
* [库和可见性](#库和可见性)
  * [使用库](#使用库)
  * [实现库](#实现库)
* [异步支持](#异步支持)
  * [处理 Futures](#处理-futures)
  * [声明异步函数](#声明异步函数)
  * [处理流](#处理流)
* [生成器](#生成器)
* [可调用的类](#可调用的类)
* [Isolates](#lsolates)
* [类型定义](#类型定义)
* [元数据](#元数据)
* [注释](#注释)
  * [单行注释](#单行注释)
  * [多行注释](#多行注释)
  * [文档注释](#文档注释)
* [总结](#总结)

## 一个基本的 Dart 程序
下面的代码使用了许多 Dart 的基本特性：
```Dart
// 定义函数
printInteger(int aNumber) {
  print('The number is $aNumber.'); // 打印到控制台
}

// 这里是程序开始执行的地方
main() {
  var number = 42; // 定义并初始化变量
  printInteger(number); // 调用函数
}
```
下面是这个程序使用的可适用于所有 (almost) Dart 应用的特性：

```Dart
// 这是一个单行注释
```
一个单行注释。Dart 也支持多行和文档注释。详情请看 [注释](#)。

```dart
int
```
一个类型。其他的一些 [基本类型](#) 包括**字符串**、**List** 和**布尔**。

```Dart
42
```
一个数值字面量。数值字面量是一种编译期常量。

```Dart
print()
```
一种展示输出的方便方式。

```Dart
'...' (or "...")
```
一个字符串字面量。

```Dart
$variableName (or ${expression})
```
字符串插值：插入一个变量或者表达式的字符串值到一个字符串字面量里。详情请看 [字符串](#)。

```Dart
main()
```
应用开始执行的特定的、必须的、顶级的函数。详情请看 [main() 函数](#)。

```Dart
var
```
一种声明变量但是不指定类型的方法。

> 提示：本篇文章的代码遵从 [Dart style guide](https://www.dartlang.org/guides/language/effective-dart/style) 中的公约。

## 重要概念
当你学习 Dart 语言的时候，请记住这些事实和概念：
* 所有可以放在一个变量里面的东西都是*对象*，而且所有对象都是*类*的实例。每一个数值、函数和 **null** 都是对象。所有的对象都继承自 [Object](#) 类。
* 尽管 Dart 是强类型的，但 Dart 可以推断类型所以类型声明是可选的。在上面的代码中，**number**被推断为类型  **int**。当你想要显式声明没有预期类型时，**使用特殊的 dynamic 类型**。
* Dart 支持泛型，像是 **List&lt;int&gt;**（包含整数的列表）或者 **List&lt;dynamic&gt;**（一个包含任意类型对象的列表）。
* 除了绑定在类和对象上的函数（分别为静态方法和实例方法）以外，Dart 还支持顶级函数（像是 **main()**)。你还可以在函数中创建函数（嵌套函数或局部函数）。
* 不像 Java，Dart 没有这些关键字：**pubilc**，**protected**，**private**。如果一个标识符以下划线 (\_) 开头，那么对于它的库来说是私有的。详情请看 [库和可见性](#)。
* 标识符可以以下划线 (\_) 开头，后见跟上任意字母和数字的组合。
* 有时候*表达式*和*语句*会有明显的区别，所以弄清楚它们的确切含义会很有帮助。
* Dart 相关工具会报告两种类型的问题：警告和错误。警告只是表明你的代码可能无法正常工作，但是并不会禁止你执行程序。错误可以是编译期或者运行期的。一个编译期错误完全禁止程序的执行；而运行期错误会在代码执行到这里时抛出一个 [异常](#)。

## 关键字
下面的表格列出了 Dart 语言特殊对待的关键字。

| abstract <sup>1</sup> | do | import <sup>1</sup> | super |
| ------------ | ---- | ---- | ---- |
| as <sup>1</sup> | dynamic <sup>1</sup> | in | switch |
| assert | else | interface <sup>1</sup> | sync* <sup>2</sup> |
| async <sup>2</sup> | enum | is | this |
| async* <sup>2</sup> | export <sup>1</sup> | library <sup>1</sup> | throw |
| await <sup>2</sup> | external <sup>1</sup> | mixin <sup>1</sup> | true |
| break | extends | new | try |
| case | factory <sup>1</sup> | null | typedef <sup>1</sup> |
| catch | false | operator <sup>1</sup> | var |
| class | final | part <sup>1</sup> | void |
| const | finally | rethrow | while |
| continue | for | return | with |
| covariant <sup>1</sup> | get <sup>1</sup> | set <sup>1</sup> | yield <sup>2</sup> |
| default | if | static <sup>1</sup> | yield <sup>2</sup> |
| deferred <sup>1</sup> | implements <sup>1</sup> |      |      |

<sup>1</sup> 带角标1的单词为**内置标识符**。不要使用内置标识符作为标识符。如果你使用内置标识符作为类名或者类型名，会引发一个编译期错误。

<sup>2</sup> 带角标2的单词是新的，在 Dart 的1.0版本发布之后作为**异步**支持加入的有限保留词。在以 **async**、**async\*** 或 **yield** 标识的函数体中，你不能使用 **async**、**await** 或者 **yield** 作为标识符。详情请看 [异步支持](#)。

关键词表里的其他所有单词都是**保留词**。你不能使用它们作为标识符。



## 变量

这里是创建并初始化一个变量的例子：

```Dart
var name = 'Bob';
```

变量保存的是引用。名字是 **name** 的变量包含一个指向值为 "Bob" 的**字符串**对象的引用。

名字为 **name** 的变量类型被推断为 **String**，但是你可以通过显示指定类型来改变这个行为。如果一个对象不限制为一个单一的类型，指定它为 **Object** 或 **dynamic** 类型。

```dart
dynamic name = 'Bob';
```

另一个选项是显式指定类型为它将会被推断的类型：

```dart
String name = 'Bob';
```

> 提示：对于局部变量，本篇文章遵守 [代码风格推荐](https://www.dartlang.org/guides/language/effective-dart/design#types) 使用 var，而不是类型声明。

### 默认值

未初始话的变量有一个初始值 **null**。即使是数值类型的变量初始值也是 null，因为数值——和 Dart 中其他所有类型一样——都是对象。

```dart
int lineCount;
assert(lineCount == null);
```

> 提示：代码中的**assert()**调用。在开发时，**assert(*condition*)** 会抛出一个异常，除非 *condition* 的结果是 true。详情请看 [Assert](#)。

### Final 和 const

如果你从不打算改变一个变量，使用 **final** 和 **const**，而不是 **var** 或者一个类型名。一个 final 变量只可以被设置一次；一个 const 变量是编译期常量。（Const 变量是显式 final 的。）一个 final 的顶级变量或者类变量在首次被使用时初始化。

> 提示：实例变量只可以是 final 的，不可以是 const 的。

这里是创建并设置一个 final 变量的例子：

```dart
final name = 'Bob'; // 没有类型声明
final String nickname = 'Boddy';
```

你不可以改变一个 final 变量的值：

```dart
name = 'Alice'; // 错误：一个final变量只可以被设置一次
```

对那些你想要作为**编译期常量**的变量使用 **const**。如果这个 const 变量是类级别的，使用 **static const** 标识它。在你声明的地方，设置变量的值为编译器常量比如数字或字符串字面量、另一个常量或者常量数值的算术运算结果。

```dart
const bar = 1000000; // 压力单位（达因/cm2）
const double atm = 1.01325 * bar; // 标准大气压
```

**Const** 关键字不仅可以声明常量。你还可以使用它创建常量值，也可以声明创建常量值的构造函数。任何变量都可以拥有一个常量值。

```dart
var foo = const [];
final bar = const [];
const baz = []; // 等同于 `const []`
```

你可以忽略常量声明中初始化表达式中的 **const**，像上面的 **baz** 一样。详情请看 [不要重复使用 const](https://www.dartlang.org/guides/language/effective-dart/usage#dont-use-const-redundantly)。

你可以改变一个非 final 且非 const 变量的值，即使它有一个常量值。

```dart
foo = [1, 2, 3]; // 之前是 const []
```

你不可以改变一个常量的值：

```dart
baz = [42]; // 错误：常量不可以被赋值
```

要了解更多使用 **const** 创建常量值的内容，请看 [List](#)、[Map](#) 和[类](#)。

## 内置类型

Dart 语言对以下类型有特殊的支持：

* numbers（数值）
* strings（字符串）
* booleans（布尔）
* lists（列表，也称为数组）
* maps（映射）
* runes（符文，在字符串中表示一个Unicode字符）
* symbols（符号）

你可以使用字面量初始化以上任意类型。比如，**'this is a string'** 就是一个字符串字面量，而 **true** 是一个boolean字面量。

由于 Dart 中的所有变量都是对象的引用——一个类的实例——所有你通常可以使用*构造函数*来初始化变量。某些内置类型有它们自己的构造函数。比如，你可以使用 **Map()** 构造函数创建一个 map。

### 数值

Dart 中的数值有两种类型：

#### int

小于等于64位的整数值，实际长度依赖运行平台。在 Dart 虚拟机上，可以是 -2<sup>63</sup> 到 2<sup>63</sup> 次方 -1。编译到 JavaScript 的 Dart 使用[JavaScript的数值](https://stackoverflow.com/questions/2802957/number-of-bits-in-javascript-numbers/2803010#2803010)，允许从 -2<sup>53</sup> 到 2<sup>53</sup> - 1的值。

#### double

64位（双精度）浮点数值，如 IEE 754 标准中所规定的。

**Int** 和 **double** 都是 [num](https://api.dartlang.org/dev/dart-core/num-class.html) 的子类。Num 类型包含像 +，-，/ 和 * 这样的基本运算符，也是 **abs()**、**ceil()** 和 **floor()** 适用的类型。（像 &gt;&gt; 的位运算符定义在 int 类中。）如果你从 num 和它的子类中找不到你想要的，试着看看 [dart:math](https://api.dartlang.org/dev/dart-math) 库。

整数是没有小数点的数字。下面是一些定义整数字面量的例子：

```dart
int x = 1;
int hex = 0xDEADBEEF;
```

如果一个数字包含小数点，那么它是一个浮点数。下面是一些定义浮点数字面量的例子：

```dart
double y = 1.1;
double exponents = 1.42e5;
```

下面是一些数值和字符串互相转换的例子：

```dart
// String -> int
var one = int.parse('1');
assert(one == 1);

// String -> double
var onePointOne = double.parse('1.1');
assert(onePointOne == 1.1);

// int -> String
String oneAsString = 1.toString();
assert(oneSAsString == '1');

// double -> String
String piAsString = 3.14159.toStringAsFixed(2);
assert(piAsString == '3.14');
```

整数类型支持传统的位运算符，比如移位 (&lt;&lt;, &gt;&gt;) 、按位与 (&) 和按位或 (|)。下面是一个例子：

```dart
assert((3 << 1) == 6); // 0011 << 1 == 0110
assert((3 >> 1) == 1); // 0011 >> 1 == 0001
assert((3 | 4) == 7); // 0011 | 0100 == 0111
```

以字面量定义的数值是编译期常量。许多算术表达式也同样是编译器常量，只要它们的操作数是编译期常数且最后得到一个数值。

```dart
const msPerSecond = 1000;
const secondsUntilRetry = 5;
const msUntilRetry = secondsUntilRetry * msPerSecond;
```

### 字符串

Dart 的字符串是以 UTF-16 编码单元组成的序列。你可以使用单引号或者双引号来创建字符串：

```dart
var s1 = 'Single quotes work well for string literals.';
var s2 = "Double quotes work just as well.";
var s3 = 'It\'s easy to escape the string delimiter.';
var s4 = "It's even easier to use the other delimiter.";
```

你可以使用 **${*expression*}** 将一个表达式插入到字符串中。如果这个表达式是一个标识符，你可以省略 {}。为了得到一个对象的字符串表示，Dart 会调用对象的 **toString()** 方法。

```dart
var s = 'string interpolation';

assert('Dart has $s, which is very handy.' ==
    'Dart has string interpolation, ' +
        'which is very handy.');
assert('That deserves all caps. ' +
        '${s.toUpperCase()} is very handy!' ==
    'That deserves all caps. ' +
        'STRING INTERPOLATION is very handy!');
```

> 提示：== 运算符测试两个对象是否相等。两个字符串相等的条件是它们包含同样的编码单位序列

你可以通过并排字符串字面量或者使用 **+** 运算符来串联字符串：

```dart
var s1 = 'String '
    'concatenation'
    " works even over line breaks.";
assert(s1 ==
    'String concatenation works even over '
    'line breaks.');

var s2 = 'The + operator ' + 'works, as well.';
assert(s2 == 'The + operator works, as well.');
```

另一种方式是创建一个多行字符串：使用三个引号（单引号或双引号）来标记：

```dart
var s1 = '''
You can create
multi-line strings like this one.
''';

var s2 = """This is also a
multi-line string.""";
```

你可以通过 **r** 前缀来创建一个”原始的“字符串：

```dart
var s = r"In a raw string, even \n isn't special.";
```

要详细了解 Unicode 字符在字符串中是怎样表示的，请看 [符文](#)。

只要所有插值表达式是编译期常量，可以计算出 null 或者 数值、字符串、布尔值，那么这个字面量的字符串就是编译期常量。

```dart
// 可作为常量字符串的组成部分
const aConstNum = 0;
const aConstBool = true;
const aConstString = 'a constant string';

// 不可作为常量字符串的组成部分
var aNum = 0;
var aBool = true;
var aString = 'a string';
const aConstList = [1, 2, 3];

const validConstString = '$aConstNum $aConstBool $aConstString';
// const invalidConstString = '$aNum $aBool $aString $aConstList';
```

要了解更多使用字符串的信息，请看 [字符串和正则表达式](#)。

### 布尔

为了表示布尔值，Dart 内置了一个名字为 **bool** 的类型。只有两个对象拥有布尔类型：布尔字面量 **true** 和 **false**，它们两个都是编译期常量。

Dart 的类型安全意味着你不能使用像 **if (*nonbooleanValue*)** 这样的代码。取而代之，你需要明确地检查值，像是：

```dart
// 检查是否是空字符串
var fullName = '';
assert(fullName.isEmpty);

// 检查是否为0
var hitPoints = 0;
assert(hitPoints <= 0);

// 检查是否为空
var unicorn;
assert(unicorn == null);

// 检查是否是NaN
var iMeantToDoThis = 0 / 0;
assert(iMeantToDoThis.isNaN);
```

### 列表

“数组”或者有序的对象组，也许是大部分编程语言中最常用的集合类型了。在 Dart 中，数组是类型为 [List](https://api.dartlang.org/dev/dart-core/List-class.html) 的对象，所以人们通常称之为“列表”。

Dart 的列表字面量看起来就像 JavaScript 的数组字面量。下面是一个简单的 Dart 列表：

```dart
var list = [1, 2, 3];
```

> 提示：分析器推断上面的 **list** 类型是 **List&lt;int&gt;**。如果你试图添加一个非整数值对象到这个列表中，分析器或者运行时会报告一个错误。要了解详细信息，请看 [类型推断](https://www.dartlang.org/guides/language/sound-dart#type-inference)。

列表使用基于0的索引，也就是说 0 是列表中第一个元素的索引，而 **list.length - 1** 是最后一个元素的索引。你可以像 JavaScript 一样获取 list 的长度和它的元素：

```dart
var list = [1, 2, 3];
assert(list.length == 3);
assert(list[1] == 2);

list[1] = 1;
assert(list[1] == 1);
```

要创建一个作为编译期常量的列表，在列表字面量前加上 **const**：

```dart
var constantList = const [1, 2, 3];
// constantList[1] = 1; // 这一行会引发一个错误
```

列表类型有许多方便的方法可以用来操作列表。要了解更多内容，请看 [泛型](#) 和 [集合](#)。

### 映射

通常来说，映射是一个关联了键和值的对象。键和值都可以是任意类型的对象。*键*是唯一的，但是你可以多次使用相同的*值*。Dart 通过映射字面量和 [Map](https://api.dartlang.org/dev/dart-core/Map-class.html) 类型来支持映射。

下面是几个简单的 Dart 映射，使用字面量创建：

```dart
var gifts = {
  // 键:    值
  'first': 'partridge',
  'second': 'turtledoves',
  'fifth': 'golden rings'
};

var nobleGases = {
  2: 'helium',
  10: 'neon',
  18: 'argon',
};
```

> 提示：分析器推断出 **gifts** 拥有类型 **Map&lt;String, String&gt;**，而 **nobleGases** 拥有类型 **Map&lt;int, String&gt;**。如果你试图添加错误的类型到上面的映射中，分析器或者运行时会报告一个错误。要了解更多信息，请看 [类型推断](#)。

你可以通过映射的构造函数创建同样的对象：

```dart
var gifts = Map();
gifts['first'] = 'partridge';
gifts['second'] = 'turtledoves';
gifts['fifth'] = 'golden rings';

var nobleGases = Map();
nobleGases[2] = 'helium';
nobleGases[10] = 'neon';
nobleGases[18] = 'argon';
```

> 提示：你可能对 **new Map()** 这样的形式会更熟悉。在 Dart 2 中，关键字 **new** 是可选的。详情请看 [使用构造函数](#)。

添加一个新的键值对到已存在的映射，方法和 JavaScript 一样：

```dart
var gifts = {'first': 'partridge'};
gifts['fourth'] = 'calling birds'; // 添加一个键值对
```

从映射中取得一个值也和 JavaScript 的写法一样：

```dart
var gifts = {'first': 'partridge'};
assert(gifts['first'] == 'partridge');
```

如果你查找一个不存在的键，会得到 null：

```dart
var gifts = {'first': 'partridge'};
assert(gifts['fifth'] == null);
```

使用 **.length** 去获得映射中键值对的数量：

```dart
var gifts = {'first': 'partridge'};
gifts['fourth'] = 'calling birds';
assert(gifts.length == 2);
```

要创建一个作为编译期常量的映射，在映射字面量前加上 **const**：

```dart
final constantMap = const {
  2: 'helium',
  10: 'neon',
  18: 'argon',
};

// constantMap[2] = 'Helium'; // 这一行会引发一个错误
```

要了解更多关于映射的内容，请看 [泛型](#) 和 [集合](#)。

### 符文

在 Dart 中，符文 (rune) 表示字符串中 UTF-32 编码的码位。

Unicode 为世界上所有的书写系统中的每个字母、数字和符号都定义了一个唯一数值。因为 Dart 的字符串是 UTF-16 码位的序列，在字符串中表示32位 Unicode 值需要特殊的语法。

表示一个 Unicode 码位的通常方式是 **\uXXXX**，其中 XXXX 是一个4位16进制数字。比如，心形符号  (♥)  表示为 **\u2665**。要指定多于或少于4位的16进制数字，将数字放到花括号里。比如，哈哈笑的 emoji  (😆)  表示为 **\u{1f600}**。

[字符串](https://api.dartlang.org/dev/dart-core/String-class.html) 类中有几个属性可以用来提取符文信息。**codeUnitAt** 和 **codeUnit** 属性返回16位编码单元。使用 **runes** 属性来获取一个字符串的符文。

下面的例子展示了符文、16位编码单元和32位编码单元的关系：

```dart
main() {
  var clapping = '\u{1f44f}';
  print(clapping);
  print(clapping.codeUnits);
  print(clapping.runes.toList());

  Runes input = new Runes(
      '\u2665  \u{1f605}  \u{1f60e}  \u{1f47b}  \u{1f596}  \u{1f44d}');
  print(new String.fromCharCodes(input));
}
```

> 提示：请谨慎使用列表操作来处理符文。这些方法可能很容易失效，而且依赖特定的语言、字符集和具体的操作。要了解更多信息，请看 Stack Overflow 上的 [How do I reverse a String in Dart?](http://stackoverflow.com/questions/21521729/how-do-i-reverse-a-string-in-dart) 

### 符号

一个符号 ([Symbols](https://api.dartlang.org/dev/dart-core/Symbol-class.html))  对象表示 Dart 程序中已声明的操作或标识。你可能永远都不需要用到符号，但是它们对于通过名称来标识引用的接口非常重要，因为缩写改变标识符的名字但不改变标识符的符号。

要获取一个标识符的符号，使用符号字面量，语法是 **#** 后面跟上标识符：

```dart
#radix
#bar
```

符号字面量是编译期常量。

## 函数

Dart 是一个完全的面向对象语言，所以甚至连函数也是对象，而且拥有一个类型 [Function](https://api.dartlang.org/dev/dart-core/Function-class.html)。这意味着函数可以被赋值给一个变量，或者作为参数传递给其他函数。你可以可以把一个 Dart  类实例作为函数来调用，只要它是一个函数。详情请看 [可调用的类](#)。

下面的例子展示如何实现一个函数：

```dart
bool isNoble(int atomicNumber) {
  return _nobleGases[atomicNumber] != null;
}
```

尽管 Effective Dart 推荐 [为公共API添加类型注释](https://www.dartlang.org/guides/language/effective-dart/design#prefer-type-annotating-public-fields-and-top-level-variables-if-the-type-isnt-obvious)，但是如果你忽略了类型，函数依然是可用的：

```dart
isNoble(atomicNumber) {
  return _nobleGases[atomicNumber] != null;
}
```

对那些只包含一个表达式的函数，你可以使用简写的语法：

```dart
bool isNoble(int atomicNumber) => _nobleGases[atomicNumber] != null;
```

这里的 **=> *expre*** 语法是 **{ return *expr*; }** 的简写。符号 **=>** 有时被称为胖箭头语法。

> 提示：只有单个表达式——而不是语句——可以出现在箭头 (=>) 和 分号 (;) 的中间。比如，你不可以放 [if 语句](#)，但是可以使用 [条件表达式](#)。

函数有两种类型的参数：必须参数和可选参数。必须参数在参数列表的前面，可选参数跟在后面。

### 可选参数

可选参数可以是位置参数或者命名参数，但不可以两者兼是。

#### 可选命名参数

当调用一个函数时，你可以通过 *参数名: 参数值* 的格式指定命名参数。比如：

```dart
enableFlags(bold: true, hidden: false);
```

当定义一个函数时，使用 *{参数1, 参数2, ...}* 的格式来指定命名参数：

```dart
/// 设置可选的"加粗”和“隐藏”标志
void enableFlags({bool bold, bool hidden}) {
  // ...
}
```

#### 可选位置参数

包裹函数的参数集到 **[]** 中来表明它们是可选参数：

```dart
String say(String from, String msg, [String device]) {
  var result = '$from says $msg';
  if (device != null) {
    result = '$result with a $device';
  }
  return result;
}
```

下面的例子展示调用该函数时不带可选参数：

```dart
assert(say('Bob', 'Howdy') == 'Bob says Howdy');
```

下面的例子展示调用该函数时带上第三个参数：

```dart
assert(say('Bob', 'Howdy', 'smoke signal') ==
    'Bob says Howdy with a smoke signal');
```

#### 参数默认值

你可以使用 **=** 来为函数参数定义默认值，可适用于命名参数和位置参数。默认值必须是编译期常量。如果没有提供默认值，默认值便是 **null**。

下面的例子展示为命名参数设置默认值：

```dart
/// 设置可选的“加粗”和“隐藏”标志
void enableFlags({bool bold = false, bool hidden = false}) {
  // ...
}

// “加粗”将会是true，隐藏将会是false
enableFlags(bold: true);
```

> 弃用提示：以前的代码可能会使用冒号 (:) 而不是 = 来设置命名参数的默认值。原因是之前只有 : 可以用来给命名参数设置默认值。而现在对 = 的支持可能会被废弃，所以我们推荐你 [使用 = 来指定默认值](https://www.dartlang.org/tools/pub/pubspec#sdk-constraints)。

下一个例子展示如果为位置参数设置默认值：

```dart
String say(String from, String msg,
    [String device = 'carrier pigeon', String mood]) {
  var result = '$from says $msg';
  if (device != null) {
    result = '$result with a $device';
  }
  if (mood != null) {
    result = '$result (in a $mood mood)';
  }
  return result;
}

assert(say('Bob', 'Howdy') ==
    'Bob says Howdy with a carrier pigeon');
```

你有可以使用列表或者映射作为默认值。下面的例子定义了一个函数 **doStuff()**，它为参数 **list** 指定了一个默认的列表，为参数 **gifts** 指定了一个默认的映射。

```dart
void doStuff(
    {List<int> list = const [1, 2, 3],
    Map<String, String> gifts = const {
      'first': 'paper',
      'second': 'cotton',
      'third': 'leather'
    }}) {
  print('list:  $list');
  print('gifts: $gifts');
}
```

### main() 函数

每一个应用都有一个顶级的 **main()** 函数作为这个应用的入口。**main()** 函数返回 **void** 而且有一个可选的参数，类型为 **List&lt;String&gt;**。

下面的例子是 web app 里面的 **main()** 函数：

```dart
void main() {
  querySelector('#sample_text_id')
    ..text = 'Click me!'
    ..onClick.listen(reverseText);
}
```

> 提示：上面代码中的 .. 语法被称作 [级联](#)。使用级联，你可以在一个单个对象的成员上进行多次的操作。

下面的例子是命令行程序中的 **main()** 函数，它接受命令行参数：

```dart
// 像这样运行该程序：dart args.dart 1 test
void main(List<String> arguments) {
  print(arguments);

  assert(arguments.length == 2);
  assert(int.parse(arguments[0]) == 1);
  assert(arguments[1] == 'test');
}
```

你可以使用 [args 库](https://pub.dartlang.org/packages/args) 来定义和解析命令行参数。

### 函数作为一等对象

你可以把函数作为参数传递给其他函数。比如：

```dart
void printElement(int element) {
  print(element);
}

var list = [1, 2, 3];

// 把 printElement 作为参数
list.forEach(printElement);
```

你可以可以把函数赋值为一个变量，比如；

```dart
var loudify = (msg) => '!!! ${msg.toUpperCase()} !!!';
assert(loudify('hello') == '!!! HELLO !!!');
```

这个例子使用了匿名函数。下一节会详细讲解匿名函数。

### 匿名函数

大部分函数都有一个名字，比如 **main()** 或者 **printElement()**。你也可以创建无名函数，它们叫做“匿名函数”，有时也被称为 "lambda" 或者 "闭包"。你可能会将匿名函数赋值给一个变量，以便后续使用，比如，你可以将它添加到一个集合，或者从集合移除。

匿名函数看起来就像一个命名函数——括号中0个或多个参数、逗号隔开、可选的类型注释。

之后的代码块包含了函数的主体：

```
([[Type] param1[, …]]) { 
  codeBlock; 
}; 
```

下面的例子定义了一个匿名函数，包含一个无类型的参数 **item**。这个函数会从列表中的每一个元素调用，打印一个包含了在指定索引处的值的字符串。

```dart
var list = ['apples', 'bananas', 'oranges'];
list.forEach((item) {
  print('${list.indexOf(item)}: $item');
});
```

如果这个函数只包含一个语句，你可以使用箭头符号简化它，它们的效果是等价的：

```dart
list.forEach(
    (item) => print('${list.indexOf(item)}: $item'));
```

### 词法作用域 

Dart 是词法作用域语言，意味着变量的作用域是静态确定的，简单地通过代码的布局来确定。你可以”沿着花括号向外走“来看是否一个变量在作用域中。

下面是一个嵌套函数的例子，它包含了各个层级的作用域中的变量：

```dart
bool topLevel = true;

void main() {
  var insideMain = true;

  void myFunction() {
    var insideFunction = true;

    void nestedFunction() {
      var insideNestedFunction = true;

      assert(topLevel);
      assert(insideMain);
      assert(insideFunction);
      assert(insideNestedFunction);
    }
  }
}
```

注意 **nestedFunction()** 可以使用各个层级的变量，一直到最外层。

### 词法闭包

”闭包“指可以访问词法作用域中变量的一个函数对象，即使这个函数是在它原本作用域的外部被使用的。

函数可以关闭定义在它周围作用域中的变量。在下面的例子中，**makeAdder()** 捕获了变量 **addBy**。无论返回的函数到哪儿，它都记得 **addBy**。

```dart
/// 返回一个函数，该函数会添加 "addBy" 到
/// 这个函数的参数上并返回
Function makeAdder(num addBy) {
  return (num i) => addBy + i;
}

void main() {
  // 创建一个加2的函数
  var add2 = makeAdder(2);

  // 创建一个加4的函数
  var add4 = makeAdder(4);

  assert(add2(3) == 5);
  assert(add4(3) == 7);
}
```

### 验证函数的相等性

下面的例子验证了顶级函数、静态函数和实例方法的相等性：

```dart
void foo() {} // 一个顶级函数

class A {
  static void bar() {} // 一个静态函数
  void baz() {} // 一个实例方法
}

void main() {
  var x;

  // 比较顶级函数
  x = foo;
  assert(foo == x);

  // 比较静态函数
  x = A.bar;
  assert(A.bar == x);

  // 比较实例方法
  var v = A(); // Instance #1 of A
  var w = A(); // Instance #2 of A
  var y = w;
  x = w.baz;

  // 闭包指向同一个实例，
  // 因此它们是相等的
  assert(y.baz == x);

  // 闭包指向不同的实例，
  // 因此它们是不相等的
  assert(v.baz != w.baz);
}
```

### 返回值

所有函数都有返回值。如果没有指定返回值，那么语句 **return null;** 会被隐式地加到函数体上：

```dart
foo() {}

assert(foo() == null);
```

## 运算符

Dart 定义了下面表格里的这些运算符。你可以重写其中大部分的运算符，在 [运算符重载](#) 部分有更详细的描述。

| 描述           | 运算符                                                       |
| -------------- | ------------------------------------------------------------ |
| 一元后缀       | *expr*++    *expr*--    ()    []    .    ?.                  |
| 一元前缀       | -*expr*    !*expr*    ~*expr*    ++*expr*    --*expr*        |
| 乘除           | *    /    %    ~/                                            |
| 加减           | +    -                                                       |
| 移位           | <<    >>                                                     |
| 按位与         | &                                                            |
| 按位异或       | ^                                                            |
| 按位或         | \|                                                           |
| 关系和类型检查 | &gt;=    &gt;    &lt;=    &lt;    as    is    is!            |
| 相等性         | ==    !=                                                     |
| 逻辑与         | &&                                                           |
| 逻辑或         | \|\|                                                         |
| 如果为空       | ??                                                           |
| 条件           | *expr1* ? *expr2* : *expr3*                                  |
| 级联           | ..                                                           |
| 赋值           | =    *=    /=    ~/=    %=    +=    -=    <<=    >>=    &=    ^=    \|=    ??= |

使用运算符创建的是表达式。下面是一些表达式的例子：

```dart
a++
a + b
a = b
a == b
c ? a : b
a is T
```

在 [运算符表](#) 中，每一个表达式都比它下面的表达式优先级高。比如，取余运算符 **%** 的优先级就比等于运算符高（因此先执行），而等于运算符的优先级又比逻辑与运算符 **==** 高。优先级意味着下面两行代码的执行方式相同：

```dart
// 括号可提高可读性
if ((n % i == 0) && (d % i == 0)) ...

// 可读性差，但是效果等价
if (n % i == 0 && d % i == 0) ...
```

> 警告：对于作用于两个操作数的操作符，最左边的操作数决定了哪个版本操作符会被使用。比如，如果你有一个 Vector 对象和 Point 对象，**aVector + aPoint** 使用 Vector 版本的 +。

### 算术运算符

Dart 支持通常的算术运算符，如下表所示。

| 运算符  | 含义                           |
| ------- | ------------------------------ |
| +       | 加                             |
| -       | 减                             |
| -*expr* | 取反（改变一个表达式的正负号） |
| *       | 乘                             |
| /       | 除                             |
| ~/      | 整数除，返回整数结果           |
| %       | 获取整数除的余数（取模）       |

例子：

```dart
assert(2 + 3 == 5);
assert(2 - 3 == -1);
assert(2 * 3 == 6);
assert(5 / 2 == 2.5); // 结果是 double
assert(5 ~/ 2 == 2); // 结果是 int
assert(5 % 2 == 1); // 取余

assert('5/2 = ${5 ~/ 2} r ${5 % 2}' == '5/2 = 2 r 1');
```

Dart 也支持前缀和后缀的自增、自减运算符：

| 运算符 | 含义                                  |
| ------ | ------------------------------------- |
| ++var  | var = var + 1（表达式的值是 var + 1） |
| var--  | var = var + 1（表达式的值是 var）     |
| --var  | var = var -1（表达式的值是 var - 1）  |
| var--  | var = var - 1（表达式的值四 var）     |

例子：

```dart
var a, b;

a = 0;
b = ++a; // 在过取值之前自增
assert(a == b); // 1 == 1

a = 0;
b = a++; // 在取值之后自增
assert(a != b); // 1 != 0

a = 0;
b = --a; // 在取值之前自减
assert(a == b); // -1 == -1

a = 0;
b = a--; // 在取值之后自减
assert(a != b); // -1 != 0
```

### 相等和关系运算符

下表列出了相等和关系运算符的含义。

| 运算符 | 含义               |
| ------ | ------------------ |
| ==     | 相等；看下面的讨论 |
| !=     | 不等               |
| &gt;   | 大于               |
| &lt;   | 小于               |
| &gt;=  | 大于等于           |
| &lt;=  | 小于等于           |

要判断两个对象 x 和 y 是否代表相同的事物，使用 **==** 运算符。（在少数情况下，当你想知道两个对象是否就是同一个对象，使用 [identical()](https://api.dartlang.org/dev/dart-core/identical.html)。）下面是 **==** 运算符的工作原理：

1. 如果 *x* 或者 *y* 是空，仅当两者都是空时返回 true，否则返回 false。
2. 返回方法 *x.==(y)* 的调用结果。（是的，像 **==** 这样的运算符就是在它第一个操作数上调用的方法。你甚至可以重写许多运算符，包括 **==**，详情请看 [运算符重载](#)。

这里是一些使用相等和关系运算符的例子：

```dart
assert(2 == 2);
assert(2 != 3);
assert(3 > 2);
assert(2 < 3);
assert(3 >= 3);
assert(2 <= 3);
```

### 类型检测运算符

运算符 **as**、**is** 和 **is!** 可以在运行期方便地进行类型检查。

| 运算符 | 含义                           |
| ------ | ------------------------------ |
| as     | 类型转换                       |
| is     | 如果对象拥有指定类型返回 true  |
| is!    | 如果对象拥有指定类型返回 false |

如果 **obj** 实现了接口 **T** ，那么表达式 **obj is T** 的结果是 true。比如，**obj is Object** 总是返回 true。

使用 **as** 运算符将对象转换成指定类型。通常的，你应该使用它作为跟随在 **is** 后面使用该对象作为表达式这种情况的简写。比如，考虑以下代码：

```dart
if (emp is Person) {
  // 类型检查
  emp.firstName = 'Bob';
}
```

你可以使用 **as** 运算符使代码更简洁：

```dart
(emp as Person).firstName = 'Bob';
```

> 说明：上面的代码并不是完全等价的。如果 **emp** 是空或者不是 Person，第一个例子（使用 is）什么都不做，而第二个（使用 as）会抛出一个异常。

### 赋值运算符

如你所见，你可以使用 **=** 运算符进行赋值。要在仅当被赋值的变量为空时才进行赋值，使用 **??=** 运算符。

```dart
// 赋值到 a
a = value;
// 如果 b 为空才赋值到 b；否则 b 保留原始值
b ??= value;
```

复合赋值运算符比如 **+=** 组合了一个其他运算符到赋值运算符。

| =    | -=   | /=   | %=        | &gt;&gt;= | ^=   |
| ---- | ---- | ---- | --------- | --------- | ---- |
| +=   | *=   | ~/   | &lt;&lt;= | &=        | \|=  |

下面解释复合赋值运算符的原理：

|                 | 复合赋值  | 等价的表达式 |
| --------------- | --------- | ------------ |
| 对运算符 *op*： | a *op*= b | a = a *op* b |
| 例子：          | a += b    | a = a + b    |

下面的例子同时使用了赋值运算符和复合赋值运算符：

```dart
var a = 2; // 使用 = 赋值
a *= 3; // 赋值并进行乘法：a = a * 3
assert(a == 6);
```

### 逻辑运算符

你可以使用逻辑运算符反转或者组合布尔表达式。

| 运算符  | 含义                                               |
| ------- | -------------------------------------------------- |
| !*expr* | 反转后面表达式的值（false 变 true，true 变 false） |
| \|\|    | 逻辑或                                             |
| &&      | 逻辑与                                             |

下面是一个使用逻辑运算符的例子：

```dart
if (!done && (col == 0 || col == 3)) {
  // ...一些操作...
}
```

### 按位和移位运算符

在 Dart 中你可以操作数值中的各个位。通常你需要在整数上使用这些按位和移位运算符。

| 运算符   | 含义                                   |
| -------- | -------------------------------------- |
| &        | 按位与                                 |
| \|       | 按位或                                 |
| ^        | 按位异或                               |
| ~*expr*  | 一元按位补码（0s 变成 1s；1s 变成 0s） |
| &lt;&lt; | 左移位                                 |
| &gt;&gt; | 右移位                                 |

下面是使用按位和移位操作符的例子：

```dart
final value = 0x22;
final bitmask = 0x0f;

assert((value & bitmask) == 0x02); // 按位与
assert((value & ~bitmask) == 0x20); // 按位与、按位补码
assert((value | bitmask) == 0x2f); // 按位或
assert((value ^ bitmask) == 0x2d); // 按位异或
assert((value << 4) == 0x220); // 左移位
assert((value >> 4) == 0x02); // 右移位
```

### 条件表达式

Dart 有两个表达式可以让你简明地计算可能需要 [if-else](#) 语句的表达式：

*condition ? expr1 : expr2*

如果 *condition* 是 true，计算 *expr1*（并且返回它的值）；否则，计算并返回 *expr2* 的值。

*expr1 ?? expr 2*

如果 *expr1* 非空，返回它的值；否则，计算并返回 *expr2* 的值。

当你需要根据一个布尔表达式进行赋值时，考虑使用 **?:**。

```dart
var visibility = isPublic ? 'public' : 'private';
```

如果布尔表达式进行的是空值判断，考虑使用 **??**。

```dart
String playerName(String name) => name ?? 'Guest';
```

上一个例子至少可以改写为其他两种形式，但是没有那么简洁：

```dart
// 比使用 ?: 运算符的长一点
String playerName(String name) => name != null ? name : 'Guest';

// 使用 if-else 语句的长版本
String playerName(String name) {
  if (name != null) {
    return name;
  } else {
    return 'Guest';
  }
}
```

### 级联符号

级联 (**..**) 允许你在同一个对象上进行一系列操作。除了方法调用，你也可以访问同一个对象的属性。这样通常可以让你免于创建临时变量并且写出更加流畅的代码。

考虑以下代码：

```dart
querySelector('#confirm') // 获取一个对象
  ..text = 'Confirm' // 使用它的成员
  ..classes.add('important')
  ..onClick.listen((e) => window.alert('Confirmed!'));
```

第一个方法调用，**querySelector()**，返回一个选择器对象。作用在这个选择器对象上的级联标记后面的代码，忽略所有随后可能的返回值。

前面的代码等同于：

```dart
var button = querySelector('#confirm');
button.text = 'Confirm';
button.classes.add('important');
button.onClick.listen((e) => window.alert('Confirmed!'));
```

你也可以嵌套级联。比如：

```dart
final addressBook = (AddressBookBuilder()
      ..name = 'jenny'
      ..email = 'jenny@example.com'
      ..phone = (PhoneNumberBuilder()
            ..number = '415-555-0100'
            ..label = 'home')
          .build())
    .build();
```

请小心地在那些返回真实对象地方法上构造级联。比如，下面地调用会失败：

```dart
var sb = StringBuffer();
sb.write('foo')
  ..write('bar'); // 错误：void 没有定义 'write' 方法
```

代码 **sb.write()** 返回 void，你不能在 void 上构造级联。

> 说明：严格地说，级联的”两点“标记不是一个运算符。它是 Dart 语法的一部分。

### 其他运算符

你已经在其他例子中看到过剩下的大部分运算符了：

| 运算符 | 名称             | 含义                                                         |
| ------ | ---------------- | ------------------------------------------------------------ |
| ()     | 函数调用         | 代表一个函数调用                                             |
| []     | 列表访问         | 引用列表中指定索引处的值                                     |
| .      | 成员访问         | 引用一个表达式的属性；比如：**foo.bar** 选取了表达式 **foo** 的 **bar** 属性 |
| ?.     | 有条件的成员访问 | 类似 **.**，但是左操作数可以为空；比如：**foo.bar** 选取了表达式 **foo** 的 **bar** 属性除非 **foo** 是空（在这种情况下 **foo?.bar** 的值是空） |

要了解更多关于 **.**、**?.** 和 **..** 的内容，请看 [类](#)。


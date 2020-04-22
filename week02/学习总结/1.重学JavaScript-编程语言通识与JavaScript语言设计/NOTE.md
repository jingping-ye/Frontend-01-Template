# 重学JavaScript:编程语言通识与JavaScript语言设计

## 语言按语法分类

- 非形式语言
  - 中文，英文
- 形式语言（formal language theory）（乔姆斯基谱系）
  - 0型 无限制文法
  - 1型 上下文相关文法
  - 2型 上下文无关文法
  - 3型 正则文法

## 文法

### 0型-无限制文法

- 相对于其他文法来说
- 有严格定义的文法

在BNF定义上:

```sh
?::=?
<A><B>::=<C>
```

### 1型- 上下文相关文法

> 一个词放在不同的地方意义不同，跟上下文相关

- 对搜索引擎不友好

在BNF定义上:

```sh
?<A>?::=?<B>?
```

### 2型- 上下文无关文法

>  一个词无论放在哪个位置都是相同的含义

- 大部分语言是主体上的上下文无关文法。
- js不是完全的上下文无关文法，99%都是上下文无关文法，小部分是违反上下文文法的。

举例：this

this不是上下文无关文法，this的多变在于语义上的多变，它在语法上是不变的。`a.this`和`this.a`是两个意思，这个是上下文相关。js中的`get`是1型文法

在BNF定义上:

```sh
<A>::=?
```

### 3型- 正规文法

> 能用正则表达式解析的文法

- 限制了表达能力

大部分语言采用了折中的方案，分为词法和语法的部分。词法部分采用正则做一遍粗略的处理，把语言变为单个词，再把词作为输入流，做语法分析。

在BNF定义上:

```sh
<A>::=<A>?
<A>::=?<A>X
```

## 产生式(BNF)

* `*`重复多次
* `|`或
* `+`至少一次
* `()`代表集合
* `{}`代表作为整体

### 举例1：一门语言的组成

> 假设该语言是由a和b组成，情况分析为：

- 1. 若干个a
- 2. 若干个b
- 3. 若干个a和b

```sh
//	情况1和情况2
<Program>：：="a"+|"b"+

//	情况3：使用递归表示,
<Program>::= <Program>"a"+ | <Program> "b"+
```

### 举例2：定义一个整数加法

```sh
//	定义加法(连加)
//	情况1：数字1+数字2
//	情况2：数字1+数字2+数字3... -> 递归解决
<Expression> = <DecimalNumber> | <Expression> "+" <DecimalNumber>

//	定义数字0~9
<Number> ::= "0" | "1" | "2" |... "9"

//	定制十进制数整数
//	情况1：数字0
//	情况2：非数字0开头的整数
<DecimalNumber> ::= "0" | {("1" | "2" |... "9") <Number>*}


```

### 举例3：加法基础上的四则运算（整数）

```sh
//	定义加法(连加)
//	情况1：数字1+数字2
//	情况2：数字1+数字2+数字3... -> 递归解决
<AddExpression> = <DecimalNumber> | <AddExpression> "+" <DecimalNumber>

//	扩展的加法
//	支持在加法的基础上进行乘运算
<AddExpression> = <MultipleExpression> | <AddExpression> "+" <MultipleExpression>

//	定义乘法
//	情况1：数字1 * 数字2
//	情况2：数字1*数字2*数字3... -> 递归解决
<MultipleExpression> = <DecimalNumber> | <MultipleExpression> "+" <DecimalNumber>


//	定义逻辑表达式
<LogicalExpression> = <AddExpression> | <LogicalExpression> "||" <AddExpression>|<LogicalExpression> "&&" <AddExpression>

//	定义数字0~9
<Number> ::= "0" | "1" | "2" |... "9"

//	定制十进制数整数
//	情况1：数字0
//	情况2：非数字0开头的整数
<DecimalNumber> ::= "0" | {("1" | "2" |... "9") <Number>*}

//	定义优先级
<PrimaryExpression> = <DecimalNumber> |
	"("<LogicalExpression>")"
```

## 其他产生式

- EBNF
- ABNF

## js 产生式

```sh
//	+ 和 - 加粗表示，用于表示终结符
AdditiveExpression:
	MultiplecativeExpression
	AdditiveExpression + MultiplecativeExpression
	AdditiveExpression - MultiplecativeExpression
```

详见 ECMA 262 [Grammar Summary]

## 图灵完备性

- 图灵机：凡是可以计算的都可以计算的出来
- 并不是一切东西不是都能计算出来：图灵机不能算出另一台图灵机是否停机
- 实现图灵机的方式
  - 命令式-goto
  - 命令式-if和while
  - 声明式-lambda 递归

## 动态与静态

动态

- 在用户的设备/在线服务器上
- 产品实际运行时
- Runtime

静态:

- 在程序员的设备上
- 产品开发时
- Compiletime

## 类型系统

- 动态类型系统与静态类型系统
- 强类型与弱类型
  - String + Number 产生了隐式转换
  - String == Boolean
- 复合类型
  - 结构体: 对象就是结构体
  - 函数签名：函数的参数类型和返回值类型  (T1, T2) => T3
- 子类型
  - 逆变/协变

ps: ts就是在js中套了一个静态类型系统

```sh
数组有个父类型的数组，然后传了一个子类型数组进去。
凡是能用Array<Parent>的地方，都能用Array<Child>
凡是能用Fuction<Child>的地方，都能用Function<Parent>
```

## 一般命令式编程语言

- Atom:最小单位的符号，比如标识符
  - Identifier
  - Literal
- Expression
  - Atom
  - Operator 操作符
  - Punctuator
- Statement
  - Expression
  - Keyword
  - Pynctuator
- Structure 结构化
  - Function
  - Class
  - Process
  - Namespace
- Program 程序集
  - Program
  - Module
  - Package
  - Library



## 现代语言的特例

- c++中，`*`可能表示乘号或者指针，具体是哪个，取决于星号前面的标识符是否被声明为类型。
- vb中，`<`可能是小于号，也可能是XML直接量的开始，取决于当前位置是否可以接受XML直接量
- Python中，行首的tab符和空格会根据上一行的行首空白以一定规则被处理成虚拟终结符indent或dedent
- JavaScript中，`/`可能是除号，也可能是正则表达式开头，处理方式类型于`VB`,字符串模板中也需要特殊处理`}`,还有自动插入分号规则。

## 其他

### 乔姆斯基

> **诺姆·乔姆斯基** Noam Chomsky

美国语言学家、哲学家、认识学家、逻辑学家、政治评论家。

### 计算机文法谱系 - 乔姆斯基体系

| 文法                             | 语言           | 自动机               | 产生式规则              |
| -------------------------------- | -------------- | -------------------- | ----------------------- |
| 0-型（无限制文法\|短语结构文法） | 递归可枚举语言 | 图灵机               | α -> β（无限制）        |
| 1-型（上下文相关文法）           | 上下文相关语言 | 线性有界非确定图灵机 | α*A*β -> αγβ            |
| 2-型（上下文无关文法）           | 上下文无关语言 | 非确定下推自动机     | *A* -> γ                |
| 3-型（正规文法）                 | 正则语言       | 有限状态自动机       | *A* -> *aB* <br/>A -> a |

- 0-型：产生所有可被图灵机识别的语言。

### 图灵机

Turing machine，确定型图灵机，是[英国](https://zh.wikipedia.org/wiki/英国)[数学家](https://zh.wikipedia.org/wiki/数学家)[艾伦·图灵](https://zh.wikipedia.org/wiki/艾伦·图灵)于1936年提出的一种将人的计算行为抽象掉的[数学逻辑机](https://zh.wikipedia.org/w/index.php?title=数学逻辑机&action=edit&redlink=1)，其更抽象的意义为一种[计算模型](https://zh.wikipedia.org/wiki/计算模型)，可以看作等价于任何有限逻辑数学过程的终极强大逻辑机器。

图灵记模型：输入集合、输出结合、内部状态、固定的程序指令。

图灵完备：简单来说，能够抽象成图灵机的系统或编程语言就是图灵完备的；一切可计算的问题图灵机都能计算，因此满足这样要求的逻辑系统、装置或者编程语言就叫图灵完备的。

... 三体，脱水计算器???

### 直接可转为机器语言的语言

- LISP

- [Brainfuck ](https://zh.wikipedia.org/wiki/Brainfuck)：一种极小化的程序语言，它是由 Urban Müller 在 1993 年创造的。由于 fuck 在英语中是脏话，这种语言有时被称为 Brainf*ck 或 Brainf***，或被简称为 BF。

### 巴科斯范式(BNF)

> Backus Normal Form。巴科斯范式（英语：Backus Normal Form，缩写为 BNF）是一种用于表示上下文无关文法的语言，上下文无关文法描述了一类形式语言。它是由约翰·巴科斯（John Backus）和彼得·诺尔（Peter Naur）首先引入的用来描述计算机语言语法的符号集。

### [Bjarne Stroustrup（比雅尼·斯特劳斯特鲁普）](https://zh.wikipedia.org/wiki/比雅尼·斯特劳斯特鲁普)

1950 年 12 月 30 日生于丹麦奥胡斯郡，计算机科学家。他以创造 C++ 编程语言而闻名，被称为“C++ 之父”。

### 静态语言与动态语言

| 类型     | 何时确定变量类型 | 是够必须提前申明变量类型 | 变量类型是否可以转换     | 举例                    |
| -------- | ---------------- | ------------------------ | ------------------------ | ----------------------- |
| 静态语言 | 编译时           | 是                       | 只能强制转换(强类型定义) | C++/Java/C#             |
| 动态语言 | 运行时           | 否                       | 会自动转换（弱类型定义） | PHP/ASP/Ruby/Javascript |

### 其他

- 协变与逆变：[ https://jkchao.github.io/typescript-book-chinese/tips/covarianceAndContravariance.html](https://jkchao.github.io/typescript-book-chinese/tips/covarianceAndContravariance.html)
- Yacc 与 Lex 快速入门：[ https://www.ibm.com/developerworks/cn/linux/sdk/lex/index.html](https://www.ibm.com/developerworks/cn/linux/sdk/lex/index.html)
- 关于元编程：[ https://www.zhihu.com/question/23856985](https://www.zhihu.com/question/23856985)
- 编程语言的自举：[ https://www.cnblogs.com/lidyan/p/6727184.html](https://www.cnblogs.com/lidyan/p/6727184.html)
- 推荐阅读：ECMA-262 Grammar Summary 部分
- 左递归和右递归？？？
- 回溯？？？
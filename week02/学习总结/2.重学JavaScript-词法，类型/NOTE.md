# 2.重学JavaScript|词法，类型

## 讲述顺序

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

## 字符集

一个字符对应一个码点。

### ASCLL字符集

- ASCLL字符，大多数语言包容，128个字符。

- JavaScript使用的字符集不是ASCLL字符。

```js
//	打印
<script>
  for (let i = 0; i < 128; i++) {
    document.write("<span style='background:red'>" + String.fromCharCode(i) + "</span><br/>");
  }
</script>

//	使用\u转义，打印“厉害”
"厉害".charCodeAt(0).toString(16); // 5389
"厉害".charCodeAt(1).toString(16); // 5bb3
var \u5389\u5bb3 = 1;
console.log(厉害); // 1

//	“*”.codePointAt(0).toString(16)
```



### Unicode字符集

- 应用范围最广，支持度最好
- emoji

## InputElement

### whitespace 空白符

- <TAB>: tab键产生的空格  `\t` 制表符
  - 表格的特点：保持整齐
  - 缺陷：tab的长度有限。早期tab的长度设定为8位（打字机时代）。
- <VT>: 纵向制表符 `\v`

- <USP> :unicode里面的空格
- <FF>: form feed 10
- <SP>: 普通空格 32
- <NBSP>: no-break space 
  - 起到断词的作用（断词但是不换行）
- <ZWNBSP>: FEFF  zero width no-break space

### LineTerminator 换行符

- <LF>::line feed `\n`
- <CR>: CARRIAGE RETURN 回车
- <LS>: Line separator 分行符
- <PS>:paragraph seprator

### comment 注释

- 单行
- 多行

### token 意义字符

#### Punctuator 符号

`()、;`

#### Keywords 关键字

let 、if...

- Future reserved Keywords: enum

#### Identifier 标识符

`let i document write`

- 变量名的部分
  - 变量名不能和关键词重合
- 属性的部分
  - 属性能和关键词重合
- 一般以大写或者小写字母开头

#### Literal 直接量

#### Number

- IEE 754 Double Float

  - sign(1) 符号位
  - Exponent (11)科学计数法
  - Fraction(52) 精度部分，表示值

- Grammar

  - DecimalLiteral 十进制

    `0、0.、.2、1e3`

  - BinaryIntegerLiteral 二进制

    `0b111` =>1

  - OctallntegerLiteral 八进制

    `0O10` => 8

  - HexIntegerLiteral 十六进制写法

    `0xFF`

- Practice

  - Safe Interger

  - Float Compare浮点数不能直接比较,存在精度问题，正确的比较方法如下：

    ```js
    Math.abs(0.1+0.2-0.3) <= Number.EPSILON // true
    Math.abs(0.1+0.2-0.3) === 0 // false
    ```

    

  - 

#### String

- Charatar 字符

- Codepoint 码点
- Encoding
- 字符集
  - ASCLL
  - UniCODE
  - UCS
  - GB 中文 收录了ASCLL和中文
    - GB2312
    - GBK(GB13000)
    - GB18030
  - ISO-8859 欧洲
  - BIG5 台湾 繁体中文

```js
97 .toString(2) // 1100001
```

```js
function UTF8_Encoding(string){
    //	return new Buffer();
}
```

- Grammer
  - "abc" 双引号
  - 'abc' 单引号
  - \`abc\` template

#### Boolean

#### Object

#### Null

#### Undefined

#### Symbol





## 其他

- https://home.unicode.org/
- https://www.fileformat.info/info/unicode/
- 计算浮点数的一个工具：[ https://github.com/camsong/blog/issues/9](https://github.com/camsong/blog/issues/9)
- 正则表达式：[ https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions)
- 揭秘 0.1 + 0.2 != 0.3 https://www.barretlee.com/blog/2016/09/28/ieee754-operation-in-js/
- ASCII，Unicode 和 UTF-8 ：[ http://www.ruanyifeng.com/blog/2007/10/ascii_unicode_and_utf-8.html](http://www.ruanyifeng.com/blog/2007/10/ascii_unicode_and_utf-8.html)

- [字符集](https://zh.wikipedia.org/zh/字符编码)：字符编码（英语：Character encoding）、字集码是把字符集中的字符编码为指定集合中某一对象（例如：比特模式、自然数序列、8 位组或者电脉冲），以便文本在计算机中存储和通过通信网络的传递。常见的例子包括将拉丁字母表编码成摩斯电码和 ASCII。其中，ASCII 将字母、数字和其它符号编号，并用 7 比特的二进制来表示这个整数。通常会额外使用一个扩充的比特，以便于以 1 个字节的方式存储。在计算机技术发展的早期，如 ASCII（1963 年）和 EBCDIC（1964 年）这样的字符集逐渐成为标准。但这些字符集的局限很快就变得明显，于是人们开发了许多方法来扩展它们。对于支持包括东亚 CJK 字符家族在内的写作系统的要求能支持更大量的字符，并且需要一种系统而不是临时的方法实现这些字符的编码。
- [Unicode ](https://zh.wikipedia.org/zh-hans/Unicode)：中文：万国码、国际码、统一码、单一码。是计算机科学领域里的一项业界标准。它对世界上大部分的文字系统进行了整理、编码，使得电脑可以用更为简单的方式来呈现和处理文字。
- [ASCII ](https://zh.wikipedia.org/wiki/ASCII)：（American Standard Code for Information Interchange，美国信息交换标准代码）是基于拉丁字母的一套电脑编码系统。它主要用于显示现代英语，而其扩展版本延伸美国标准信息交换码则可以部分支持其他西欧语言，并等同于国际标准 ISO/IEC 646。美国信息交换标准代码是这套编码系统的传统命名，互联网号码分配局现在更倾向于使用它的新名字 US-ASCII[2]。美国信息交换标准代码是美国电气和电子工程师协会里程碑之一。
- Token：记号、标记。JS 里有效的输入元素都可以叫 Token。
- [NBSP ](https://zh.wikipedia.org/wiki/不换行空格)：不换行空格（英语：no-break space，NBSP）是空格字符，用途是禁止自动换行。HTML 页面显示时会自动合并多个连续的空白字符（whitespace character），但该字符是禁止合并的，因此该字符也称作“硬空格”（hard space、fixed space）。Unicode 码点为：U+00A0 no-break space。
- [零宽空格](https://zh.wikipedia.org/zh-hans/零宽空格)：（zero-width space, ZWSP）是一种不可打印的 Unicode 字符，用于可能需要换行处。在 HTML 页面中，零宽空格可以替代。但是在一些网页浏览器（例如 Internet Explorer 的版本 6 或以下）不支持零宽空格的功能。
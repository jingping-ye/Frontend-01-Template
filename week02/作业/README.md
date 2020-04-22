# 作业

- 写一个正则表达式 匹配所有 Number 直接量

```js
let reg = /0|([1-9]\d*\.?\d*)|(0\.\d*[1-9])/;
reg.test(1); // true
reg.test(0); // true
reg.test(1.0); //true
reg.test(0.1); //true
reg.test(-1); // true
reg.test(-1.1); // true
```

- 写一个 UTF-8 Encoding 的函数

```js
function UTF8_Encoding(str){
   return new TextEncoder().encode(str);
}
UTF8_Encoding('a'); // Uint8Array [97]
UTF8_Encoding('作业');  // Uint8Array(6) [228, 189, 156, 228, 184, 154]
```

- 写一个正则表达式，匹配所有的字符串直接量，单引号和双引号

  不太明白是什么意思。。。。

```js
function checkStr(str){
    let reg = /(.*?)/
    return reg.test(str);
}
```


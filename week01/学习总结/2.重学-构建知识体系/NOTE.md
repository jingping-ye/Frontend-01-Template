# 2. 重学|构建知识体系

- ecma262 javascript的现行标准。

- 好的资料基本是英文的。

- 英文看多了就懂了，技术圈的用词和普通用词是另一套。

- $0表示当前选中的元素

- 所有语言都有输入的最小元素

- 语法：A2-A5

- Reference 

  ```js
  //	a.b是一个reference类型 js和3完全不同
  a.b = 3;
  delete  a.b
  delete 3
  ```

- w3c的状态

  - working draft 草稿，不能使用
  - proposed recommendation 建议推荐,委员会达成一致，待公众批评
  - candidate Recommendation 候选标准
  - Recommendation 推荐
  - Retired 废弃

## 参考链接

**主要参考网站：**

- https://www.ecma-international.org/ 
- https://developer.mozilla.org/en-US/docs/Web
- https://whatwg.org/

**课上涉及网址：**

- https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-262.pdf
- https://www.w3school.com.cn/html/html_entities.asp
- https://www.w3.org/1999/xhtml/
- https://html.spec.whatwg.org/multipage/
- https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element

## 参考文件：

**请学员们在课件中查看**（链接: [https://pan.baidu.com/s/1ET3y5eexynf6xJKpNwHMRw ](https://pan.baidu.com/s/1ET3y5eexynf6xJKpNwHMRw)密码:nepb）

- 前端技术 2.xmind
- ECMA-262.pdf
- html-standard.pdf

## 参考名词：

- XMind：思维导图软件（[ https://www.xmind.cn/）](https://www.xmind.cn/）)
- DTD：Document Type Definition（[ https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd）](https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd）)
- Entity：实体（在 HTML 语境下就是 & 符后边的东西）
- ARIA：Accessible Rich Internet Applications（[ https://www.w3.org/TR/html-aria/）](https://www.w3.org/TR/html-aria/）)
- Token：有效的输入元素
- Comment：注释
- WhiteSpace：空白符
- Line Terminator：行终止符
- Atom：原子
- Semantics：语义
- Runtime：运行时

## 其他有助于你理解的知识（选看）：

- 计算机组成原理
- 操作系统
- 编译原理
- 学员给出的课上参考代码：

> Array.prototype.map.call($0.querySelectorAll(‘code’), e => e.innerText).join(’\n’)
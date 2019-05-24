### 类型转换

```javascript
"4px"-2 = NaN

obj === null  // 检测为null  (一般用!判断null和其他一起)
```

> 使用+ 将非数字转为数字,等同于Number(...)

```javascript
 +apples + +oranges  //两个数字字符串相加

 alert( 4 ** (1/2) ); // 2 (1 / 2 幂相当于开方，这是数学常识)
 alert( 8 ** (1/3) ); // 2 (1 / 3 幂相当于开三次方)
```

> 代码风格  推荐   [stardardjs风格](https://standardjs.com/rules-zhcn.html#javascript-standard-style)

> 使用ESlint 做代码自动检测 备选jshlint    prettier好像不错  webstorm自带

> 使用mocha进行自动化测试

> 使用babel新规范

### 数据类型

> 数字类型

```javascript
// 这些是相同的写法
let billion = 1000000000
let billion = 1e9

let ms = 0.0000012
let ms = 1.2e-6

// 数字类型转换
let num = 255;

alert( num.toString(16) );  // ff
alert( num.toString(2) );   // 11111111
alert( 123456..toString(36) ); // 2n9c

// Mach.trunc 舍弃小数点后的  和ceil类似 ceil负数会加  不支持ie
//  toFixed(n) 将点数后的数字四舍五入到 n 个数字并返回结果的字符串表示。
//  (推荐第二种)
let num = 12.34;
alert( num.toFixed(5) ); // "12.34000", added zeroes to make exactly 5 digits

// 浮点数运算一定要转为整数 再除, 同样适用于 php java c perl ruby
```

> 字符串

```javascript
//只要记住：if (~str.indexOf(...)) 读作 “if found”。

if (~str.indexOf(...)) === if ( str.indexOf(...) != -1)

// includes, startsWith, endsWith  
str.includes(substr, pos)  // 和上面一样,更现代的写法
str.startWith(substr)

// 截取字符串总是使用
str.slice(start, end)

// 比较两个字符串

// 调用 str.localeCompare(str2)：
// 根据语言规则，如果 str 大于 str2 返回 1。
// 如果if str 小于 str2 返回 -1。
// 如果相等，返回 0。
```

> 数组

```javascript
// 清空数组最好的方法就是：
arr.length = 0;
```

遍历数组的元素：

- `for (let i=0; i<arr.length; i++)`  — 运行的最快, 可兼容旧版本浏览器。
- `for (let item of arr)`  — 现代语法，只能访问 items。
- `for (let i in arr)`  — 永远不会使用。

数组删除或添加元素

`array.splice(start[, deleteCount[, item1[, item2[, *...]]]]*)`

如果我们想检查是否包含需要的元素，并且不想知道确切的索引，那么 `arr.includes` 是首选。

```javascript
let users = [
  {id: 1, name: "John"},
  {id: 2, name: "Pete"},
  {id: 3, name: "Mary"}
];

let user = users.find(item => item.id == 1);

alert(user.name); // John
```

数组经常被使用，以至于有一种特殊的方法用于判断：[Array.isArray(value)](https://developer.mozilla.org/zh/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray)。如果 `value` 是一个数组，则返回 `true`；否则返回 `false`。

数组方法备忘录：

- 添加/删除元素：
  
  - `push(...items)`  — 从结尾添加元素，
  - `pop()`  — 从结尾提取元素，
  - `shift()`  — 从开头提取元素，
  - `unshift(...items)`  — 从开头添加元素，
  - `splice(pos, deleteCount, ...items)`  — 从  `index`  开始：删除  `deleteCount`  元素并在当前位置插入元素。
  - `slice(start, end)`  — 它从所有元素的开始索引  `"start"`  复制到  `"end"`  (不包括  `"end"`) 返回一个新的数组。
  - `concat(...items)`  — 返回一个新数组：复制当前数组的所有成员并向其中添加  `items`。如果有任何`items`  是一个数组，那么就取其元素。

- 查询元素：
  
  - `indexOf/lastIndexOf(item, pos)`  — 从  `pos`  找到  `item`，则返回索引否则返回  `-1`。
  - `includes(value)`  — 如果数组有  `value`，则返回  `true`，否则返回  `false`。
  - `find/filter(func)`  — 通过函数过滤元素，返回  `true`  条件的符合 find 函数的第一个值或符合 filter 函数的全部值。
  - `findIndex`  和  `find`  类似，但返回索引而不是值。

- 转换数组：
  
  - `map(func)`  — 从每个元素调用  `func`  的结果创建一个新数组。
  - `sort(func)`  — 将数组倒序排列，然后返回。
  - `reverse()`  — 在原地颠倒数组，然后返回它。
  - `split/join`  — 将字符串转换为数组并返回。
  - `reduce(func, initial)`  — 通过为每个元素调用  `func`  计算数组上的单个值并在调用之间传递中间结果。

- 迭代元素：
  
  - `forEach(func)`  — 为每个元素调用  `func`，不返回任何东西。

- 其他： –  `Array.isArray(arr)`  检查  `arr`  是否是一个数组。

请注意，`sort`，`reverse`  和  `splice`  方法修改数组本身。

这些方法是最常用的方法，它们覆盖 99％ 的用例。但是还有其他几个：

- [arr.some(fn)](https://developer.mozilla.org/zh/docs/Web/JavaScript/Reference/Global_Objects/Array/some)/[arr.every(fn)](https://developer.mozilla.org/zh/docs/Web/JavaScript/Reference/Global_Objects/Array/every)  检查数组。
  
  在类似于  `map`  的数组的每个元素上调用函数  `fn`。如果任何/所有结果为  `true`，则返回  `true`，否则返回  `false`。

- [arr.fill(value, start, end)](https://developer.mozilla.org/zh/docs/Web/JavaScript/Reference/Global_Objects/Array/fill)  — 从  `start`  到  `end`  用  `value`  重复填充数组。

- [arr.copyWithin(target, start, end)](https://developer.mozilla.org/zh/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin)  — copies its elements from position  `start`  till position  `end`  into  *itself*, at position  `target`  (overwrites existing).将其元素从  `start`  到  `end`  在  `target`  位置复制到  **本身**（覆盖现有）。

- ``Array.from(obj[, mapFn, thisArg])` 将可迭代对象或类数组对象 `obj` 转化为真正的 `Array` 数组，然后我们就可以对它应用数组的方法。可选参数 `mapFn` 和 `thisArg` 允许我们对每个元素都应用一个函数。

> **Map**

[Map](https://developer.mozilla.org/zh/docs/Web/JavaScript/Reference/Global_Objects/Map) 是一个键值对的集合，很像 `Object`。但主要的区别是，`Map` 允许所有数据类型作为键。



###  DOM



| Method                   | Searches by... | Can call on an element? | Live? |
| ------------------------ | -------------- | ----------------------- | ----- |
| `getElementById`         | `id`           | -                       | -     |
| `getElementsByName`      | `name`         | -                       | ✔     |
| `getElementsByTagName`   | tag or `'*'`   | ✔                       | ✔     |
| `getElementsByClassName` | class          | ✔                       | ✔     |
| `querySelector`          | CSS-selector   | ✔                       | -     |
| `querySelectorAll`       | CSS-selector   | ✔                       | -     |



>  attributes 的一些方法：

- `elem.hasAttribute(name)` —— 检查是否存在这个特性
- `elem.getAttribute(name)` —— 获取这个特性
- `elem.setAttribute(name, value)` —— 把这个特性设置为 name 值
- `elem.removeAttribute(name)` —— 移除这个特性
- `elem.attributes` —— 所有特性的集合



>  `classList` 方法：

- `elem.classList.add/remove("class")` —— 添加/移除类。
- `elem.classList.toggle("class")` —— 如果类存在就移除，否则添加。
- `elem.classList.contains("class")` —— 返回 `true/false`，检查给定类。



> 在管理 class 时，有两个 DOM 属性：

- `className` —— 字符串值可以很好地管理整个类集合。
- `classList` —— 拥有 `add/remove/toggle/contains` 方法的对象可以很好地支持单独的类。

>  改变样式：

- `style` 属性是一个带有 camelCased 样式的对象。对它的读取和修改 `"style"` 属性中的单个属性等价。要留意如果应用 `important` 和其他稀有内容 —— 在 [MDN](https://developer.mozilla.org/zh/docs/Web/API/CSSStyleDeclaration) 上有一个方法列表。
- `style.cssText` 属性对应于整个“样式”属性，即完整的样式字符串。

 获取已经解析的样式（对应于所有类，在应用所有 CSS 并计算最终值后）：

- `getComputedStyle(elem[, pseudo])` 返回与 `style` 对象类似且包含了所有类的对象，是只读的。

>  滚动：

- 读取当前的滚动：`window.pageYOffset/pageXOffset`
- 改变当前的滚动：
  - `window.scrollTo(pageX,pageY)` — 绝对定位
  - `window.scrollBy(x,y)` — 相对当前位置的滚动
  - `elem.scrollIntoView(top)` — 滚动到正好`elem`可视的位置（`elem` 与窗口的顶部/底部对齐）

###  事件

这里有一张最有用的 DOM 事件列表，请看：

**鼠标事件：**

- `click` —— 当鼠标点击一个元素时（触摸屏设备在 tap 时生成）。
- `contextmenu` —— 当鼠标右击一个元素时。
- `mouseover` / `mouseout` —— 当鼠标光标移入或移出一个元素时。
- `mousedown` / `mouseup` —— 当鼠标按下/释放一个元素时。
- `mousemove` —— 当鼠标移出时。

**表单元素事件**：

- `submit` —— 当访问者提交了一个 `<form>` 时。
- `focus` —— 当访问者聚焦一个元素时，例如 `<input>`。

**键盘事件**：

- `keydown` and `keyup` —— 当访问者按下然后松开按钮时。

**Document 事件**：

- `DOMContentLoaded` —— 当加载和处理 HTML 时，DOM 将会被完整地构建。

**CSS 事件**：

- `transitionend` —— 当 CSS 动画完成时。

>  有 3 种方法可以分发事件处理器：

1. HTML 属性：`onclick="..."`。
2. DOM 属性 `elem.onclick = function`。
3. 方法：添加 `elem.addEventListener(event, handler[, phase])`，移除 `removeEventListener`。
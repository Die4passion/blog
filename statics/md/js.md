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

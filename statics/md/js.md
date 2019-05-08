### 类型转换

```js
"4px"-2 = NaN

obj === null  检测为null  (一般用!判断null和其他一起)
```

> 使用+ 将非数字转为数字,等同于Number(...)

```js
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

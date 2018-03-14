
####三、字符串的扩展
> 字符串遍历
```JavaScript
//for...of 循环遍历字符串
//除了遍历字符串，这个遍历器最大的优点是可以识别大于0xFFFF的码点，传统的for循环无法识别这样的码点。
for (let char of 'apple') {
  console.log(char)
}
//'a' 'p' 'p' 'l' 'e'
```
> repeat()
```JavaScript
//repeat(n) 方法返回一个新字符串，表示将原字符串重复n次。
//参数n的规则 ： 
// @1. n为数字    n > -1，n为小数时取底，NaN等同于0
// @2. n为字符串  会先转换成数字

document.write('<h1>hello world !</h1>'.repeat(3.5))//输出 3条 hello world

```
> 模板字符串反引号 `` 和 嵌入变量 ${}
```JavaScript
let news = `<h1>都是是最棒的！</h1>`
document.write(news) //都是是最棒的！

//模板字符串中可以 嵌入变量 ${}
const txt = '中国共产党人'
news = `<h1>${txt}都是是最棒的！</h1>`
document.write(news) //中国共产党人都是是最棒的！

//${} {}内可以写入任意表达式 / 对象属性 / 函数，进行运算
let x = 1
let y = 2
let z = { a : 3, b : 4 }
let t = function(){
      return "验证嵌入模板字符中成功 : "
}
let reg = `${t()}${x * 2} + ${y * 2} - ${z.a + z.b}`.repeat(2.5)
console.log(reg) //输出2次  验证嵌入模板字符中成功 : 2 + 4 - 7
```
> indexOf  includes  startsWith  endsWith
```JavaScript
//indexOf()    : 用来确定一个字符串是否包含在另一个字符串中
//includes()   : 返回布尔值，表示是否找到了参数字符串。
//startsWith() : 返回布尔值，表示参数字符串是否在原字符串的头部。
//endsWith()   : 返回布尔值，表示参数字符串是否在原字符串的尾部。

let test = '中国共产党人是最棒的 in the world'
console.log(test.indexOf('中国'))     // 0
console.log(test.indexOf('牛'))       // -1
console.log(test.indexOf('共产党'))   // 2
console.log(test.includes('中国'))    // true
console.log(test.startsWith('中国'))  // true
console.log(test.endsWith('world'))   // true

//使用第二个参数n时，endsWith的行为与其他两个方法有所不同。
//它针对前n个字符，而其他两个方法针对从第n个位置直到字符串结束。
console.log(test.includes('中国',1))   // false
console.log(test.startsWith('国',0))   // false
console.log(test.startsWith('共',2))   // true
console.log(test.endsWith('中国',0))   // false
console.log(test.endsWith('中国',1))   // false
console.log(test.endsWith('中国',2))   // true
```
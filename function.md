####五、函数的扩展
> 箭头函数
```JavaScript
//拥有1个参数时：
var a = b => b 
var a = function(b){
    return b
}
a(5) // 输出 5
//拥有多个参数或者没有参数时：圆括号代表参数部分
var f = () => 5
var f1 = (x,y) => x+y
f()     // 5
f1(2,3) // 5 
//代码块多于一行代码时：
var fn = (x,y,z) => {
    let a = x + y
    let b = x + z
    return a * b
}
//箭头函数最大用处就是：使得表达更加简洁
const isEven = n => n % 2 === 0
const square = n => n * n
isEven(5) // false
square(5) // 25

```
> 参数指定默认值
```JavaScript
function Point(x = 0, y = 0) {
  this.x = x;
  this.y = y;
}
const p = new Point();
console.log(p)  // Point {x: 0, y: 0}

//参数变量是默认声明的，所以不能用let或const再次声明。
function foo(x = 5) {
  let x = 1;   // error
  const x = 2; // error
}

//参数默认值是惰性求值的。
let x = 99;
function foo(p = x + 1) {
  console.log(p);
}
console.log( foo() )   // 100
x = 100;
console.log( foo() )   // 101
```



##八、函数
```JavaScript
    @1.
		function add(x,y=1){
			if(x===0){
				throw new Error('this is error!')
			}
			return x+y
		}
		console.log(add(1))
		console.log(add.length) //输出为 1，打印出参数个数，当参数有默认值时，不计入参数个数，
	@2. use stric  严谨模式
	@3. 参数解构在函数中
		let json = {
			'x' : 1,
			'y' : 2
		}
		function ads({x,y=1}){
			console.log(x,y)
		}
		asd(json)  // 1 2
	@4.	判断对象，数组是否为空
		let json = {
			x : 1,
			y : 2
		}
		//检查是否存在某个键（key）
		console.log( 'x' in json )  //输出为 true
		console.log( 'z' in json )  //输出为 false
		console.log( 0 in arr) // true
		let arr = [,,5,,,]
		//根据数组的索引 in 数组 检查是否有值
		console.log(2 in arr) //true
		console.log(0 in arr) //false
	@5.	数组的遍历
		let arr = [1,2,3,4,5,6,7,,9]
		arr.forEach((item,index) => console.log(index,item) )

		arr.map( x => )

	@6
		//===同值相等 Object.is() 严格相等
		console.log(+0===-0)   //true
		console.log(NaN===NaN) //false
		console.log(Object.is(+0,-0)) // false
		console.log(Object.is(NaN,NaN)) //true
	@7.
		let aa = {a:1,b:2,c:3,d:4}
		console.log(Object.keys(aa)) // ['a','b','c','d']
	@8.
		let a = {
			name : 'cat'
		}
		let b = {
			[a.name] : 'xiaobai'
		}
		console.log(b) //{cat:'xiaobai'}
		console.log(b.cat) //xiaobai
```
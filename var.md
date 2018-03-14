####一、let 和 const
```JavaScript
let    -> 只在let命令所在的代码块内有效
const  -> 声明一个只读的常量,作用域等同于let
          const实际上保证的，并不是变量的值不得改动，而是变量指向的那个内存地址不得改动
var    -> 掌握好作用域的使用,更多参考ES5
```
> let
```JavaScript
1.代码块
    ES5:
        (function(){
            console.log("ES5") // 输出 ES5
        })()

    ES6：
        {
            console.log("ES6") // 输出 ES6
            var a = 10;
            let b = 11;
        }
        console.log(a) // 10
        console.log(b) // 报错 b is not defined

2.let 不存在变量提升
    console.log(a) // 10
    var a = 10;

    console.log(b) // b is not defined
    let b = 10;

3.如果代码块出现let,const声明,那么一旦形成封闭作用域,在"声明之前使用"就会报错   
    typeof f; // undefined
    var f = 100;
    if(true){
        console.log(f) // 报错 f is not defined 
        f = 50;   // 报错 f is not defined
        typeof f; // 报错 f is not defined
        let f;
    }

4.重复声明也会报错
    var num = 10;
    var num = 50;
    let num = 11; // num has already been declared

5.闭包
    for(var i=0;i<10;i++){

    }
    console.log(i) // 10
    for(let l=0;l<10;l++){

    }
    console.log(l) // l is not defined

    // var:
    var arr = [];
    for(var i=0;i<10;i++){
        arr[i] = function(){
            console.log(i)       
        }
    }
    arr[5]() // 10

    // let
    var arr = [];
    for(let i=0;i<10;i++){
        arr[i] = function(){
            console.log(i)       
        }
    }
    arr[1]() // 1
    arr[5]() // 5
    arr[8]() // 8

```
> const
```javaScript
1.声明const 后面必须跟值,且不能修改
    var abc; // undeifned
    let cba; // undefined
    const bba; // Missing initializer in const declaration

    const msg = "hello"
    console.log(msg) // hello 
    msg = "world"
    console.log(msg) // Assignment to constant variable.

2.内存地址不得改动,并非是值不得改动
    // 这里实际是改变了内存地址
    const num = 10;
    num = 5; // 'num' has already been declared  
    
    const arr = []
    arr.push("hello") // ["hello"]
    arr[0] = "world" // ["world"]  // 这里改变的是值
    arr = ["ddy"] // Assignment to constant variable 这里改变的就是内存的引用

```

####二、变量的解构与赋值及扩展运算符...

> 对象的扩展运算符 ...
```JavaScript
       function aaa(){
			console.log(arguments[0])
			console.log(arguments[1])
			console.log(arguments[2])
			console.log(arguments[3])
		}
		aaa(1,2,3)  // 输出为 1 2 3 undefined
		function bbb(...arg){
			console.log(arg[1])
			console.log(arg[2])
			console.log(arg[3])
			console.log(arg[4])
		}
		bbb(1,2,3) // 输出为 1 2 3 undefined
```
```JavaScript
       rest运算符---> 剩余的部分 （一般用在父子孙组件之间的传值）
	   function aaa(first,...arg){
			console.log(arg.lenth)
			console.log(first)
			for(let val of arg){
				console.log(val)
			}
		}
		aaa(1,2,3,4,5,6,7,8,9)
		// 输出为 8
		// 输出为 1
		// 输出为 2 3 4 5 6 7 8 9
```
> 解构：从数组和对象中提取值，对变量进行赋值，
```JavaScript
//数组解构赋值按照顺序
//常用于处理 res.data
let array = [1,2,[3,4],5]  
let [a,b,[c,d],e] = array
console.log(a)   // 输出 1
console.log(d)   // 输出 4

let [,,c] = [1,2,3]
console.log(c) // 3

let [a,...b] = [1,2,3,4,5]
console.log(b) // [2,3,4,5]

```
```JavaScript
//对象/JSON解构要有相同的"键"，且无关顺序

//Object
let {a,b} = {b:2,a:1,c:3}
console.log(a)  // 1
console.log(b)  // 2

//JSON
let json = {       
   'a' : '我是'，
   'b' : 'json'
}
let {a,b} = json
console.log(a)   // 我是
console.log(b)   // json
```
> 字符串解构
```JavaScript
let {a,b,c,d,e} = 'hello' 
console.log(a)  // h
console.log(b)  // e
console.log(c)  // l
console.log(d)  // l
console.log(e)  // o
```
> undefined 和 null 对比
```JavaScript
//undefined  无        转换成数字是--》 NaN   意思就是  缺少值
//null       无对象     转换成数字是--》 0     意思就是   不是对象
//例：
function ddd(){
    return 'hey boy !'
}
let [a,b='hello',c='world',d=ddd()] = ['say',undefined,null]
console.log(a)  // say
console.log(b)  // hello
console.log(c)  // null
console.log(d)  // hey boy !
```
> 如果事先声明了变量 x 那么解构必须在 () 里 
```JavaScript
let x
({x} = {x:111})  
 console.log(x)   // 111
```

> 传参解构 可以拥有默认值
```JavaScript
function add([a,b,c=3]){  
    return a+b+c
}
console.log(add([1,2]))    // 6
console.log(add([1,2,5]))  // 8

```
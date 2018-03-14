
####四、数值的判断与扩展方法
```JavaScript
	let a = 22/7
	//isFinite  是否为数字
	console.log(Number.isFinite(a))  // true
	console.log(Number.isFinite('a'))// false
	console.log(Number.isFinite(NaN))  // false
	console.log(Number.isFinite(undefined))  // false
	//isNaN
	console.log(Number.isNaN(NaN)) //true
	//parseInt parseFloat
	console.log(Number.parseInt('12.12')) //输出为 12
	console.log(Number.parseFloat('12.12')) //输出为 12.12
	//isInteger 判断是否为整数
	console.log(Number.isInteger(12)) //true

	//常数
	在JS中的最大值为 Number.MAX_SAFE_INTEGER 也就是Math.pow(2,53)
	在JS中的最小值为 Number.MIN_SAFE_INTEGER 也就是-Math.pow(2,53)

	//isSafeInteger 判断数字是否在安全数字范围内
	console.log(Number.isSafeInteger(1231231)) //true
```

####六、Math对象
```JavaScript
    @1.trunc 如果内容能被格式化成数字，去掉小数部分，输出整数部分，如果不能被格式化成数字，输出NaN
		console.log(Math.trunc(4.1))   // 4
	   	console.log(Math.trunc('4.1')) // 4
	   	console.log(Math.trunc('4aa')) // NaN
	@2.sign 正负数的判断


	@3.cbrt 立方根

	@4.clz32 32位二进制

	@5.imul
	@6.hypot 返回参数的平方和的平方根
```




##九、symbol 标记 一种新的数据类型
```JavaScript
    ES5 常用数据类型
	var a = new String
	var b = new Number
	var c = new Boolean
	var d = new Array
	var e = new Object
	ES6
	var f = Symbol() //原始数据类型不需要new 它的值不和任何值相等
	console.log(typeof f) // symbol
	@1.
		var obj = {z:0,y:8}
		var a = Symbol('a')
		var b = Symbol('b')
		obj[a] = 'this is A'
		obj[b] = 'this is B'
		for(let key in obj){
			console.log(obj[key]) //输出中没有obj[a],obj[b]
		}
		console.log(obj) //输出包含obj[a],obj[b]
```




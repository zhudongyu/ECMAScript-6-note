```JavaScript
/* concat()
	1.不会改变现有的数组
	2.连接两个或多个数组，返回被连接后的新数组 */
	var a = [1,2,3];
	var b = [4,5,6];
	var c = [7,8,9];
	var d = a.concat(b,c) //[1,2,3,4,5,6,7,8,9]
```
```JavaScript
/*slice(start,end)
	1.不会改变现有的数组
	2.截取数组中的部分元素，并返回一个新的数组
	3.start : 必填，起始下标（包含）；
	  end : 可选，结束下标（不包含），当结束小标不存在时，默认最后
*/
	var a = [1,2,3,4,5,6]
	var b = a.slice(2,4) //[3,4]
	var c = a.slice(4)   //[5,6]
```
```JavaScript
/*push()
	1.改变现有的数组(包括长度)
	2.末尾添加一个或多个元素，并返回新的长度。*/
	var a = [1,2,3]
	var l = a.push(4,5,6,7) // 7 返回新的长度
	console.log(a) 		    //[1,2,3,4,5,6,7]
```
```JavaScript
/*unshift()
	1.改变现有的数组(包括长度)
	2.开头添加一个或多个元素，并返回新的长度。*/
	var a = [3,4,5]
	var l = a.unshift(1,2)  // 5 返回新的长度
	console.log(a) 			//[1,2,3,4,5]
```
```JavaScript
/*splice(index,howMany,item1,...itemN)
	1.改变现有的数组(包括长度)
	2.数组中添加/删除项目，然后返回被删除的‘元素组成的新数组’。
	3.index   : 必填，添加/删除元素的下标
	  howMany : 必填，要删除元素的数量，为0，不会删除元素
	  item..  : 选填，向数组的index下标处添加新的元素*/
	var a = [1,2,3,4,5]
	var b = a.splice(2,2,'ss')
	console.log(b) // [3,4] 返回被删除的元素组成的新数组
	console.log(a) // [1,2,'ss',5]
```
```JavaScript
/*pop()
	1.改变现有的数组(包括长度)
	2.删除数组的最后一个元素，并返回其值*/
	var a = [1,2,3]
	var b = a.pop() // 3
	console.log(a) 	// [1,2]
	var c = a.pop() // 2
	console.log(a)  //[1]
	var d = a.pop() //1
	console.log(a)  //[]
	var e = a.pop() // undefined （这时数组已经空了，不会改变数组，返回undefined值）
	console.log(a)  //[]
```
```JavaScript
/*shif()
	1.改变现有的数组(包括长度)
	2.删除数组的第一个元素，并返回其值*/
	var a = [1,2,3]
	var b = a.shift() // 1
	console.log(a) 	  // [2,3]
	var c = a.shift() // 2
	console.log(a)    //[3]
	var d = a.shift() //3
	console.log(a)    // []
	var e = a.shift() //undefined （这时数组已经空了，不会改变数组，返回undefined值）
	console.log(a)    // []
```
```JavaScript
/*sort(sortby)
	1.改变现有的数组(不包括长度)
	2.仅仅是对数组的元素进行排序，是对数组的引用，返回的还是原数组；
	3.sortby : 可选，规定排序规则，必须是函数，该函数接收两个参数a和b
		注意：@1.如果使用时没有传入sortby,将按照字符编码顺序对数组中的元素进行排序，且元素都应该转换成字符串
	  		 @2.sortby使用，比较a和b，如果a < b ,返回小于0的值，a排在b前，a = b ,返回0，a>b 返回 大于0的值*/
	//数字排序
	var a = [3,2,6,7,1,4,5]
	var sortNumber = function(a,b){
		return a-b
	}
	a.sort(sortNumber) //[1,2,3,4,5,6,7]
	//默认字符编码排序 (排的是字符串的首字母)
	var a = ['s','aa','ddy','hello','world']
	a.sort() //["aa", "ddy", "hello", "s", "world"]
```
```JavaScript
/*reverse()
	1.改变现有的数组（不包括长度）
	2.颠倒数组中元素的顺序*/
	var a = [1,2,3,4,5,6,7]
	a.reverse() //[7,6,5,4,3,2,1]
	/*join(separator)
		1.不会改变现有的数组
		2.不带separaor参数时，仅仅是将数组中的所有元素放入一个字符串中，并返回结果
		3.带有separaor参数时，同时会通过指定的separator(分隔符)分隔元素，在返回结果*/
	var a = [1,2,3,4,5,6]
	var b = a.join()     // "1,2,3,4,5,6"
	var c = a.join('-')  // "1-2-3-4-5-6"
	var d = a.join(' ')  // "1 2 3 4 5 6" 空格符
	console.log(a)       // [1,2,3,4,5,6]
```
```JavaScript
/*toString()
		1.不会改变现有的数组
		2.把数组转换为字符串，并返回结果*/
	var a = [1,2,3,4,5]
	var b = a.toString() // 1,2,3,4,5
	var c = a.join();
	console.log(b === c) //true
```
```JavaScript
	/*forEach()
		1.*/
	/*map()
		1.*/
	/*filter()
		1.*/
	/*reduce()
		1.*/
	/*indexOf()
		1.*/
```
```JavaScript
// array of 用于将一组值 转换为数组
//Array.of总是返回 参数值 组成的数组。如果没有参数，就返回一个空数组。
Array.of(); // []
Array.of(undefined); // [undefined]
Array.of(1); // [1]
Array.of(1, 2); // [1, 2]

//正常情况后端返回的数组前端解析如下
		let txt = '[813.13,641.57,1090,717.20,0,0,0,0.596,538.31]'
		let arr = evel(txt)或者let arr = JSON.parse(txt)
		//
		let arr = Array.of(3,10,8,11,'acv')
		console.log(arr) //[3,10,8,11,'acv']
```
```JavaScript
    json  ---> 一种数据格式
	jsonp ---> 跨域的数据访问  也就是aaa.com访问bbb.com的数据，

	@1.
		//后端返回  json的数组格式
		let json = {
			'0' : 'a',
			'1' : 'b',
			'2' : 'c',
			'3' : 'd',
			length ： 3 //必须写上长度
		}
		//前端处理成数组
		let arr = Array.from(json)
		console.log(arr) //['a','b','c','d']
```
```JavaScript
//空位
// 以下会将数组的空位，转为undefined，也就是说，这个方法不会忽略空位。
Array.from(['a',,'b']) // [ "a", undefined, "b" ]
[...['a',,'b']] // [ "a", undefined, "b" ]
[,'a','b',,].copyWithin(2,0) // [,"a",,"a"]
new Array(3).fill('a') // ["a","a","a"]
let arr = [, ,];
for (let i of arr) {
    console.log(1);
}
Array.from(123) //[] 数字时返回空数组

// entries()、keys()、values()、find()和findIndex()会将空位处理成undefined
// entries()
[...[,'a'].entries()] // [[0,undefined], [1,"a"]]

// keys()
[...[,'a'].keys()] // [0,1]

// values()
[...[,'a'].values()] // [undefined,"a"]

// find()
[,'a'].find(x => true) // undefined

// findIndex()
[,'a'].findIndex(x => true) // 0

```
```JavaScript
//copyWithin(target,start,end) 在当前数组内部，将指定位置的成员复制到其他位置(会覆盖原有成员），然后返回当前数组。
//--target（必需）：从该位置开始替换数据。如果为负值，表示倒数。
//--start（可选）：从该位置开始读取数据，默认为 0。如果为负值，表示倒数。
//--end（可选）：到该位置前停止读取数据，默认等于数组长度。如果为负值，表示倒数。
//从 3 号位直到数组结束的成员（4 和 5），复制到从 0 号位开始的位置，结果覆盖了原来的 1 和 2。
[1, 2, 3, 4, 5].copyWithin(0, 3); //// [4, 5, 3, 4, 5]
// 将3号位复制到0号位
[1, 2, 3, 4, 5].copyWithin(0, 3, 4); // [4, 2, 3, 4, 5]
// -2相当于3号位，-1相当于4号位
[1, 2, 3, 4, 5].copyWithin(0, -2, -1); // [4, 2, 3, 4, 5]
```
```JavaScript
// find() 用于找出第一个符合条件的数组成员
// 它的参数是一个回调函数，所有数组成员依次执行该回调函数，直到找出第一个返回值为true的成员，然后返回该成员。如果没有符合条件的成员，则返回undefined。
[1, 4, -5, 10].find( value => value < 0); //5
[1, 4, -5, 10].find(function (value,index,arr) { return value < 0 });
//findIndex() 返回第一个符合条件的数组成员的位置，如果所有成员都不符合条件，则返回-1。
[1, 5, 10, 15].findIndex(function(value, index, arr) {
    return value > 9;
}); // 2

// 这两个方法都可以接受第二个参数，用来绑定回调函数的this对象。
function f(v){
    return v > this.age;
}
let person = {name: 'John', age: 20};
[10, 12, 26, 15].find(f, person);    // 26
// 上面的代码中，find函数接收了第二个参数person对象，回调函数中的this对象指向person对象。


// 这两个方法都可以发现NaN，弥补了数组的indexOf方法的不足。
[NaN].indexOf(NaN); // -1
[NaN].findIndex(y => Object.is(NaN, y)); // 0
```

```JavaScript
//fill(value,start,end) 使用给定值，填充一个数组。
//快速创建二位数组
let arr1 = new Array(3);
let arr2 = arr1.fill(new Array(2).fill(0));
//从 1 号位开始，向原数组填充 7，到 2 号位之前结束
['a', 'b', 'c'].fill(7, 1, 2); // ['a', 7, 'c']
```
```JavaScript

// 数组遍历
		let arr = ['a,'b','c','d','e']
		for(let value of arr){
			console.log(value)
		}
		// a b c d e
		for(let index of arr.keys()){
			console.log(index)
		}
		// 0 1 2 3 4
		for(let [index,value] of arr.entries()){
			console.log(index,value)
		}

		let word = arr.entries()

		console.log(word.next().value) //';'
		console.log(word.next().value)
		console.log(word.next().value)
		console.log(word.next().value)
		console.log(word.next().value)
		console.log(word.next().value)
		console.log(word.next().value)



// entries()，keys()和values()它们都返回一个遍历器对象,可以用for...of循环进行遍历，
// values()是对键值的遍历
// keys()是对键名的遍历
// entries()是对键值对的遍历。
for (let [key, value] of ['a', 'b'].entries()) {
    console.log(key, value);
}
// 0 "a"
// 1 "b"

// 如果不使用for...of循环，可以手动调用遍历器对象的next方法，进行遍历。
let letter = ['a', 'b', 'c'];
let entries = letter.entries();
console.log(entries.next().value); // [0, 'a']
console.log(entries.next().value); // [1, 'b']
console.log(entries.next().value); // [2, 'c']
```
```JavaScript
// includes() 返回一个布尔值，表示某个数组是否包含给定的值
[1, 2, 3].includes(2)     // true
[1, 2, 3].includes(4)     // false
[1, 2, NaN].includes(NaN) // true
[1, 2, 3,null].includes(null) // true

[NaN].indexOf(NaN) // -1 全等判断所以不存在
[NaN].includes(NaN) // true

//第二个参数表示搜索的起始位置，默认为0。
[1, 2, 3].includes(3, 3);  // false
[1, 2, 3].includes(3, -1); // true 倒数

//Map 和 Set 数据结构有一个has方法，需要注意与includes区分。
// --Map 结构的has方法，是用来查找键名的，比如Map.prototype.has(key)、WeakMap.prototype.has(key)、Reflect.has(target, propertyKey)。
// --Set 结构的has方法，是用来查找值的，比如Set.prototype.has(value)、WeakSet.prototype.has(value)。

```

```JavaScript
//Object.is(NaN, NaN) true 判断两个值是否全等
Object.is(1,1);  //true
Object.is(1,'1');  //false
```


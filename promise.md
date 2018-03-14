#### Promise介绍与使用

> console.dir(Promise)  
> Promise是一个构造函数 拥有常用方法all/reject/resolve，原型上有常用方法then/catch

```JavaScript
// 以往的异步解决 --> 回调
function test (callBack) {
    setTimeout(function(){
        console.log("11111");
        callBack();
    })
};
var fn = function () {
    console.log("22222");
};
test(fn); //这样就会先输出 11111 然后输出 22222
// 弊端 --> 回调地狱 ：嵌套太深，无法维护，阅读性太难！
```

```JavaScript
//Promise 接收一个参数-->函数，并且这个函数传入两个参数-->resolve/reject
//resolve : 将Promise状态置为fullfiled（继续保持）---> 简单来说就是：异步操作执行'成功'后的操作的回调函数
//reject  : 将Promise状态置为rejected(拒绝了)    ---> 简单来说就是：异步操作执行'失败'后的操作的回调函数

//先定义三个函数 --> 三步曲
var stateNum
var step1 = function(resolve,reject){
	//异步操作 利用setTimeout的延时模拟ajax请求
		setTimeout(function(){
			stateNum = Math.floor(Math.random()*10) + 1
			console.log('step1函数执行完成')
			if(stateNum > 5){
				resolve('resolve :' + stateNum)
			}else{
				reject('step1 the stateNum so small')
			}
		},1000)
}
var step2 = function(resolve,reject){
		setTimeout(function(){
			stateNum = Math.floor(Math.random()*10) + 1
			console.log('step2函数执行完成')
			if(stateNum > 5){
				resolve('resolve :' + stateNum)
			}else{
				reject('step2 the stateNum so small')
			}
		},1000)
}
var step3 = function(resolve,reject){
		setTimeout(function(){
			stateNum = Math.floor(Math.random()*10) + 1
			console.log('step3函数执行完成')
			if(stateNum > 5){
				resolve('resolve :' + stateNum)
			}else{
				reject('step3 the stateNum so small')
			}
		},1000)
}

//细节注意：Promise被new成一个对象后会立即执行传进去的参数（函数），
//所以一般我们用Promise的时候会将它包在一个函数中，在需要的时候去运行这个函数,然后 将Promise对象 return 出去 如下：
function runAsync_1(){
	return  new Promise(step1)
}
runAsync_1() 
//在运行完函数runAsync_1()后，我们得到了一个Promise对象,这个对象的状态为fullfiled和rejected中的一种,

//运行Promise对象上的then/catch方法
//then :  接收两个参数，也就是两个函数，这两个函数中都有一个参数，分别对应在runAsync_1中调用resolve/reject时传的参数
//        但是一般情况下then中只传入一个参数，也就是执行fullfiled状态的函数，rejected状态的函数写入到catch中。
//catch : 1.和then方法中的第二个参数（函数）的用法一样，用来指定reject的回调
//        2.catch还有另外一个作用：在执行resolve的回调（也就是then中的第一个参数）时，如果抛出异常（代码错了），那么并不会报错卡死js,
          而是会进到这个catch方法中，

//简单的一个异步情况系下
runAsync_1() 
   .then(function(res){console.log(res)})
   .catch(function(res){console.log(res)})

//当需要按顺序执行多个异步的情况下
runAsync_1() 
      .then(function(res){
          console.log(res);     
          return runAsync_2(); 
      })
      .then(function(res){
          console.log(res);     
          return runAsync_3(); 
      })
      .then(function(res){
          console.log(res);     
          return  "也可以不return Promise对象，直接把数据传给下面的then"
      })
      .then(function(res){
          console.log(res); 
      })
      .catch(function(res){
          console.log(res); 
      })
```
```JavaScript
// all 方法
//Promise的all方法提供了 并行 执行异步操作的能力，并且在所有异步操作执行完成后才执行回调
//通俗的说就是'谁跑的慢，以谁为准开始执行回调'
Promise.all(
	[runAsync_1(),runAsync_2(),runAsync_3()]
).then(function(results){
	console.log(results)
}).catch(function(results){
	console.log(results)
})

//race 用法和all是样的，但意思上跟all正好相反，
//race通俗的说就是'谁跑的快，就以谁为准开始执行回调'
//但是，其他的异步操作仍然会执行



console.time("step")
console.timeEnd("step")
可以得到一个相对的时间，参数必须一样。可以用来参考程序的执行效率问题
```







































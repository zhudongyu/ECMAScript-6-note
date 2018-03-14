#### async 精华
```JavaScript
1. async是什么 ？
   promise 已经初步解决了异步问题，而async 号称终极异步解决方案（ES7）。
2. async 使用总结之 5 条黄金法则
   -- async/await 黄金搭档必须一起使用，而且是要基于 Promise 的。
   -- async 表示这是一个异步函数，await 只能应用在这个 async 函数里面
   -- await 表示在这里，会等待 Promise 返回结果之后在继续执行
   -- await 后面跟着的应该是一个 Promise 对象，如果不是，也就是返回其他值的情况下，代码不会出现错误，但是也不会出现代码同步的效果了。
   -- await 必须在 async 函数的上下文当中
3. 特点
   -- 保证代码的可读性以及代码的顺序性
   -- 使我们的阅读逻辑更加清晰
4. 示例
      var sleep = function (time) {
          return new Promise(function(resolve,reject){
              setTimeout(function(){
                  console.log("睡了一觉，现在我睡好了")
                  resolve("睡了一觉，现在我睡好了");//promise一定要有返回状态
              },time)
          })
      }

      var start = async function(){
          // try 正常时候的代码
          try {
              console.log("start loading ......");

              await sleep(5000); // 等待方法执行完成后在往下走
    
              console.log("end loading ......");
          }catch(err){
              // 这里输出报错之后的内容，也就是这里会捕捉到错误
              console.log(err)
          }
      }
      start();

```
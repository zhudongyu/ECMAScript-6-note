```JavaScript
//Symbol

//Javascript 的第七种数据类型
//前六种是 ：undefined null Boolean String Number Object

//1.每一个Symbol值都是独一无二的
let s1 = Symbol();
let s2 = Symbol();
s1 === s2 //false

typeof s1 // symbol

//2.Symbol函数可以接受一个字符串作为参数，表示对 Symbol 实例的描述，主要是为了在控制台显示，或者转为字符串时，比较容易区分。

let s1 = Symbol('foo');
let s2 = Symbol('bar');

s1 // Symbol(foo)
s2 // Symbol(bar)

s1.toString() // "Symbol(foo)"
s2.toString() // "Symbol(bar)"
//3.Symbol 值不能与其他类型的值进行运算，会报错。

let sym = Symbol('My symbol');

"your symbol is " + sym // TypeError: can't convert symbol to string

//但是，Symbol 值可以显式转为字符串。
String(sym) // 'Symbol(My symbol)'
sym.toString() // 'Symbol(My symbol)'
//Symbol 值也可以转为布尔值，但是不能转为数值。
let sym = Symbol();
Boolean(sym) // true
!sym  // false

if (sym) {
    // ...
}


//库 功能代码的集合
//框架 由众多库组成，产品
//架构：产品设计  实际蓝图




//防抖，事件频繁触发带来的DOMdoudong

var count = 0;
var conyainer = document.getElementById("container")
function getUSerAction(e) {
    console.log(this)
    console。log（e）
    conyainer.innerHTML=count++;


    return true
}

var setUSerAction = debounce(getss,1000,true)

conyainer.onmousemove = setUSerAction

document.getElementById('button').addEventListener("click",function (ev) {
    setUSerAction.cancel()
});


//dop 面向切面编程
//1.捕捉事件，在触发纸钱，我们来人为捕捉进行处理，控制嫌疑人
//2，在捕捉的方法中，对时间的触发时间判断，审讯嫌疑人
//3.根据一个标准（间隔时间）来对第二部的方法进行分流处理。释放或者关押


//调用的方法，事件触发间隔的时间
function debounce(func,wait,immediate) {
    var timeout,result;//用户触发的时间间隔，
    //释放，判断成功之后同行

        debounced.cancel = function () {
            clearTimeout(timeout);
            timeout = null;
        }
    var debounced = function () {

    };
    // return function () {
        //第二次进来，清除掉计时器
        var context = this;
        var args = arguments;
        clearTimeout(timeout);


        //开始边界 true 立马执行，然后等待进行判断
        if(immediate){
        //    当timeout是undefined,null    callNow为true
            var callnow = !timeout;

            //写一个延迟方法，来判断是否停顿了一秒，停止了就把timeout变成null
            //不断的触发，就不断的重新赋值。所以就不会执行。直到停了一秒
            timeout = setTimeout(function () {
                timeout = null;
            },wait);
            //第一次为true 等待1秒之后，又会为true
            if(callnow) {
                result = func.apply(context,args)
            }


        }else {
            timeout = setTimeout(function () {
                /*result = */ func.apply(context,args)
            })
        }


        //执行第一次得到一个 timeout变量。func 延迟wait 执行
        // timeout = setTimeout(func,wait)
        // timeout = setTimeout(function () {
        //     func.apply(context,args); //call也是一样的，来改变方法执行时的作用域
        // //    args 是数组
        // },wait)

        return result
        //直到wait 没有动作了，就执行方法。
    }
}



//用户希望能够自己控制执行边界。

//开始边界，结束边界。


//解决：问题三  加上一个控制变量  Boolean ： immediate


//凡是 编码对象是function方法的，一定要考虑到，它可能会有返回值！

//凡是代码中有异步或者回调函数的，一定要记得写异常处理方法或者取消功能接口。
// ajax success :false
//延迟会有可能没有执行，或者出现异常导致执行不了，
```
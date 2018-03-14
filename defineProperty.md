
```JavaScript
//监听对象的改变的
var obj = {};
var val = "Hello"
Object.defineProperty(obj,"name",{
    get:function(){//在获取的时候调用
        console.log("get...");
        return val;
    },
    //监听值的改变
    set:function(value){//在设置的时候调用
        console.log("set...");
        val = value;
    }
});

obj.name  // "Hello"
obj.name = "DonyK"  //"DonyK" 
obj.name  // "DonyK" 
```

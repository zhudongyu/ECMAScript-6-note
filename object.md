```JavaScript
//1.简写 注意，简洁写法的属性名总是字符串
let birth = '2000/01/01';
const Person = {
    name: '张三',
    //属性简写
    birth, //等同于birth: birth  键名和键值 一样时
    //对象中的方法简写
    hello() { console.log('我的名字是', this.name); }// 等同于hello: function ()...

};
//在模块化写法中很实用

let mokuai = {};
const getItem = function (key) {
    return key in mokuai ? mokuai[key] : null;
};
const setItem = function (key, value) {
    mokuai[key] = value;
};
const clear = function () {
    mokuai = {};
};
export default { getItem, setItem, clear };


const obj = {
    get foo() {},
    set foo(x) {}
};
```
```JavaScript
//2.同值相等 Object.is()
Object.is('foo', 'foo')// true
Object.is({}, {})// false

// == 会转换类型
// === NaN 不等于自身， +0 等于 -0
// Object.is() 和 === 行为基本一致，不同点就在 NaN 和 +0 -0

+0 === -0 //true
NaN === NaN // false

Object.is(+0, -0) // false
Object.is(NaN, NaN) // true

```
```JavaScript

//3.Object.assign(target, source1, source2) 非常实用
// 如果目标对象与源对象有同名属性，或多个源对象有同名属性，则后面的属性会覆盖前面的属性。
//注意于常见场景实用：
// 1.浅拷贝 如果源对象某个属性的值是对象，那么目标对象拷贝得到的是这个对象的引用。
const obj1 = {a: {b: 1}};
const obj2 = Object.assign({}, obj1);

obj1.a.b = 2;
obj2.a.b // 2
//2.同名属性的替换  Lodash 的_.defaultsDeep方法深拷贝
const target = { a: { b: 'c', d: 'e' } }
const source = { a: { b: 'hello' } }
Object.assign(target, source) // { a: { b: 'hello' } }
//3.数组的处理 Object.assign把数组视为属性名为 0、1、2 的对象，因此源数组的 0 号属性4覆盖了目标数组的 0 号属性1。
Object.assign([1, 2, 3], [4, 5]) // [4, 5, 3]
//4.为对象添加属性
//将x属性和y属性添加到Point类的对象实例。
class Point {
    constructor(x, y) {
        Object.assign(this, {x, y});
    }
}
//为对象添加方法
Object.assign(SomeClass.prototype, {
    someMethod(arg1, arg2) {
    ···
    },
    anotherMethod() {
    ···
    }
});
//5.合并多个对象
const merge = (target, ...sources) => Object.assign(target, ...sources);
const merge = (...sources) => Object.assign({}, ...sources);
//6.为属性指定默认值
const defaultOption ={
    url: {
        host: 'xxxxx.com',
        port: 7070
    }
};
const processContent = function (options) {
    return Object.assign({}, defaultOption, options);
};
let newOption = {
    url: {
        port: 8000
    }
};
processContent(newOption); // {url: {port: 8000}}

//一个好处 ：新的配置顶掉了默认配置，就可以很灵活的按照我们的需求改变或者增添配置
//一个坏处 ：同名属性的替换，一定要注意
```
```JavaScript
//4.属性的遍历
//@1.for...in 遍历对象自身的和继承的可枚举属性（不含 Symbol 属性）。
//@2.Object.keys(obj) 返回一个数组，包括对象自身的（不含继承的）所有可枚举属性（不含 Symbol 属性）的键名。
//@3.Reflect.ownKeys(obj) 返回一个数组，包含对象自身的所有键名，不管键名是 Symbol 或字符串，也不管是否可枚举。
Reflect.ownKeys({ [Symbol()]:0, b:0, 10:0, 2:0, a:0 })// ['2', '10', 'b', 'a', Symbol()]
```
```JavaScript
//5.super 关键字
// 众所周知 this关键字总是指向函数所在的当前对象，ES6 又新增了另一个类似的关键字super，指向当前对象的原型对象。
const proto = {
    foo: 'hello'
};

const obj = {
    find() {
        return super.foo;
    }
};

Object.setPrototypeOf(obj, proto);
obj.find() // "hello"
```
```JavaScript
//6.Object.keys() Object.values() Object.entries() 供for...of循环使用。 会过滤忽略属性名为 Symbol 值的属性
let {keys, values, entries} = Object;
let obj = { a: 1, b: 2, c: 3 };

//keys() 返回数组
Object.keys(obj) // ["a","b","c"]
for (let key of keys(obj)) {
    console.log(key); // 'a', 'b', 'c'
}
//values() 返回数组
values(obj) // [1,2,3]
for (let value of values(obj)) {
    console.log(value); // 1, 2, 3
}
// entries() 返回一个数组，成员是参数对象自身的键值对数组
entries(obj) // [ ['a', 1], ['b', 2], ['c', 3] ]
for (let [key, value] of entries(obj)) {
    console.log([key, value]); // ['a', 1], ['b', 2], ['c', 3]
}
//Object.entries的基本用途是遍历对象的属性。
let obj = { one: 1, two: 2 };
for (let [k, v] of Object.entries(obj)) {
    console.log(
        `${JSON.stringify(k)}: ${JSON.stringify(v)}`
    );
}
// "one": 1
// "two": 2
// Object.entries方法的另一个用处是，将对象转为真正的Map结构。
const obj = { foo: 'bar', baz: 42 };
const map = new Map(Object.entries(obj));
map // Map { foo: "bar", baz: 42 }

```
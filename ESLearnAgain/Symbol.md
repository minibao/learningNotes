#Symbol

symbol一种新的原始数据类型，表示独一无二一的值。是第七种类型，
分别是：

undefined
null
boolean
string
number
object
symbol


Symbol值通过Symbol函数生成。就是说，对象的属性名现在可以有两种类型：

一种是原来就有的字符串
一种是新增的Symbol类型

凡是Symbol类型都是独一无二一的，可以保证不会与其它属性名产生冲突

一个简单的定义：
let s = Symbol()
typeof s  // symbol

###注意1
Symbol不能使用new命令，会报错。也就是说Symbol值不是对象，所以不能添加属性。可以理解它是一种类型似于字符串的数据类型。

再举一个栗子：

let s1 = Symbol('foo')
let s2 = Symbol('foo')

console.log(s1) //Symbol(foo)
console.log(s2) //Symbol(foo)
console.log(s1 == s2) // false
console.log(s1 === s2) // false

虽然s1和s2打印的结果上看起来一样，但是通过判断是不等的，这就是symbol的特性。

###注意2
Symbol不能和其它类型作运算，否则会报错。


####Symbol可以转为字符串

let sym = Symbol('My symbol');

String(sym) // 'Symbol(My symbol)'
sym.toString() // 'Symbol(My symbol)'


###注意3
Symbol不能转为数字类型否则会报错

let s1 = Symbol('1')
Number(s1)

Uncaught TypeError: Cannot convert a Symbol value to a number


###作为属性名的Symbol
既然Symbol是独一无二的，那么可以把Symbol值作为标识符，用于对象的属性名，可以当作健（key）使用

举个栗子
let keySymbol = Symbol()

let a = {}
a[keySymbol] = 'a'

let b = {
	[keySymbol] : 'b'
}

console.log(a) // {Symbol(): "a"}
console.log(b) // {Symbol(): "b"}

###注意4
Symbol值作为对象属性名时，不能用点运算符
同理，在对象内部，使用Symbol定义属性时，Symbol值必须放在括号之中


###Object.getOwnPropertySymbols方法
Object.getOwnPropertySymbols方法返回一个数组，成员是当前 对象的所有用作属性的Symbol值

栗子：

const obj = {};
let a = Symbol('a');
let b = Symbol('b');

obj[a] = 'Hello';
obj[b] = 'World';

const objectSymbols = Object.getOwnPropertySymbols(obj);

console.log(objectSymbols) // [Symbol(a), Symbol(b)]


###Object.defineProperty

Object.defineProperty(obj, foo, {
	value: "foobar"
})

正常情况下这个obj是不能被for in 枚举的，由于Object.defineProperty中有个enumerable属性，默认是false即不能枚举。
需要设置成true才能正常被枚举

Object.defineProperty(obj, foo, {
	enumerable: true,
	value: "foobar"
})

可以用 for in 循环出来了

for (let i in obj) {
    console.log(i); // foobar，（如果enumerable属性没设置或者是false，则是空的）
}


###Symbol.hasInstance
对象Symbol.hasInstance属性，指向一个内部方法。当其它对象使用instanceof运算符，判断是否为该对象的实例时，会调用这个方法。比如，foo instanceof Foo在语言内部，初建调用的是Foo[Symbol.hasIntance](foo)
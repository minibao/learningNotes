# Set

set最大的优势是数组去重骚操作

##case1

const arr2 = [1, 2, 2, 3, 3, 4, 4, 5]

const set2 = new Set(arr2) // {1, 2, 3, 4, 5}一个set对象

console.log('arr2',...arr2) // 1, 2, 3, 4, 5 字符序列化后

同时提供了两组转数组的方法fun1和fun2

###fun1
console.log('set2', [...set2]) /*先用 ...序列化，再装时数组*/

###fun2
console.log('set2', Array.from(set2)) /*直接用官方提供的方法，Array.from() 把set对象转成数组*/
/*个人建议用第二种方法，虽然第一种看上去很骚气*/


##Set提供的方法
add(value)：添加某个值，返回 Set 结构本身。
delete(value)：删除某个值，返回一个布尔值，表示删除是否成功。
has(value)：返回一个布尔值，表示该值是否为Set的成员。
clear()：清除所有成员，没有返回值。

##Set提供的遍历
keys()：返回键名的遍历器
values()：返回键值的遍历器
entries()：返回键值对的遍历器
forEach()：使用回调函数遍历每个成员

写一个有用的案例
const arr = [2, 3, 5, 4, 5, 2, 2]
const s = new Set(arr)

s.forEach((x, y) => {
    console.log(x, y)
});

##Set实现数组的交并
let a = new Set([1, 2, 3])
let b = new Set([4, 3, 2])

console.log(a)
console.log(b)

###并集
let union = new Set([...a, ...b])
console.log(union)

###交集
let intersect = new Set([...a].filter(x => b.has(x)))
console.log(intersect)

###差集a
let difference = new Set([...a].filter(x => !b.has(x)))
console.log(difference)

###差集b
let difference1 = new Set([...b].filter(x => !a.has(x)))
console.log(difference1)


#Map

des: 官方很明确的说明了，由于传统的键值对只能用``字符串``当作``键``，在日常操作中很受限制

object: 字符串对应值
Map: 值对应值

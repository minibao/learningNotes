# Set

set最大的优势是数组去重骚操作

##case1

const arr2 = [1, 2, 2, 3, 3, 4, 4, 5]

const set2 = new Set(arr2) // {1, 2, 3, 4, 5}一个set对象

console.log('arr2',...arr2) // 1, 2, 3, 4, 5 字符序列化后

同时提供了两组转数组的方法

###fun1
console.log('set2', [...set2]) // 先用 ...序列化，再装时数组

###fun2
console.log('set2', Array.from(set2)) // 直接用官方提供的方法，Array.from() 把set对象转成数组

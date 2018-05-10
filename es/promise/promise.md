#Promise
promise相比于回调函数更加的强大
对象的状态不受外界影响。Promise对象代表一个异步操作，有三种状态

pending: 进行中
fulfilled: 已成功
rejected: 已失败
只有异步的操作结果可以决定当前是哪一种结果，任何其它操作都无法改变这个状态。符合它的名字`承诺`

状态改变不会再变，有两种变化可能
pending -> fulfilled
pending -> rejected
只要这种情况发生，状态就凝固了，不再变了，会一直保持这个结果，称之为resolved(已定型)

resolved的Promise是在本轮事件循环的末尾执行，总是易于 本轮循环的同步任务。

###Promise看到现在总算听懂一句比较有用的话：
一般来说，调用resolve或reject以后，Promise的使命就完成了，后继操作应该放到then方法里面，而不应该直接写在resolve或reject的后面。所以，最好在它们前端 加上return语句，这样就不会有意外。
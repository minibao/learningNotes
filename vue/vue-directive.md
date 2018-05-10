#directive

除了一些默认的v-model和v-show，Vue也允许注册算定义指令。
注意，在Vue2.0中，代码利用和抽象的主要形式是组件。
然而，有的情况下，你仍然需要对普通DOM元素进行底层操作，这时候就会用到自定义指令。
举个粟子：

// 注册一个全局自定义指令 `v-focus`
Vue.directive('focus', {
  // 当被绑定的元素插入到 DOM 中时……
  inserted: function (el) {
    // 聚焦元素
    el.focus()
  }
})

// 注册一个局部directive
directives: {
  focus: {
    // 指令的定义
    inserted: function (el) {
      el.focus()
    }
  }
}


<input v-focus>就能在dom里使用


##钩子函数

什么是钩子函数
它是一种事件劫持机制，也就是说它会比你的事件更早进行执行处理。

指令定义对象可以提供如下几个钩子函数（均为可选）

bind: 只调用一次，指令第一次绑定到元素时调用。在这里可以进行一次性的初始化设置。

inserted: 被绑定元素插入父节点时调用

update: 所在组件的VNode更新时调用，但是可能发生在其子VNode更新之前。指令的值可能发生了改变，但是你可以通过比较更新前后的值来忽略不必要的模板更新

componentUpdated: 指令所在组件的VNode及其子VNode全部更新后调用。

unbind: 只调用一次，指令与元素解绑时调用。
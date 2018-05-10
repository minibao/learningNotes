#mixins

mixins是一种分Vue组件中可复用功能的非常灵活的方式。混入对象可以包含任意组件选项。当组件使用混入对象时，所有混入对象的选项将被混入该组件本身的选项。

mixins的一点理解
组件在引用之后相当于在父组件内开辟了一块单独的空间，来根据父组件props过来的值进行相应的操作，单本质上两者还是泾渭分明的，相对独立的。
而mixins则是在引入组件之后，则是将组件内部的内容如data等方法、method等属性与父组件相应内容进行合并。相当于在引入后，父组件的各种属性方法都被扩充了。


单纯组件引用：
父组件 + 子组件 >>> 父组件 + 子组件

mixins：
父组件 + 子组件 >>> new父组件

###tips
值得注意的是，在使用Mixins时，父组件同时拥着子组件内的各种属性方法，但这并不是意味着他们同时共享、同时处理这些变量，两者之间除了合并，是不会进行任何通信的。

在注册全局mixins时要注意，一旦注册了全局mixins后，这东西威力无穷。谨慎使用全局混入对象，因为会影响到每个单独创建的 Vue 实例 (包括第三方模板)。大多数情况下，只应当应用于自定义选项，就像上面示例一样。也可以将其用作 Plugins 以避免产生重复应用

正常下就用局部注册，每个文件导入使用。


##全局注册

Vue.mixin({
	created: function () {
	    this.hello()
	},
	methods: {
	  hello: function () {
	      console.log('hello from mixin1111!')
	  }
	}
})

注册后类似一种加所有的vue methodes的操作，只要在方法里都可以使用。

##局部注册

定义一个混入对象
var myMixin = {
  created: function () {
    this.hello()
  },
  methods: {
    hello: function () {
        console.log('hello from mixin!')
    }
  }
}


export default {
    name: 'AppTempl',
    mixins: [myMixin], // mixin在这里使用了
    directives: {
      focus: {
        // 指令的定义
        inserted: function (el) {
          el.focus()
        }
      }
    },
    components: {
      'mixins-templ': mixinsTempl
    },
    data () {
      return {
        message: '你好！！',
        groceryList: [
          { id: 0, text: '蔬菜' },
          { id: 1, text: '奶酪' },
          { id: 2, text: '随便其它什么人吃的东西1200' }
        ]
      }
    }
  }
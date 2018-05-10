#生命周期

beforeCreate
created
beforeMount
mounted
beforeUpdate
updated
activated
deactivated
beforeDestroy
destroyed

##1.beforeCreate
官方说明：在实例初始化之后，数据观测（data observer）和event/watcher事件配置之前被调用。
解释：这个时期，this变量还不能使用，在data下的数据，和methods下的方法，watcher中的事件都不能获得到

beforeCreate() {
	console.log(this.page); // undefined
	console.log{this.showPage); // undefined
},
data() {
	return {
		page: 123
	}
},
methods: {
	showPage() {
		console.log(this.page);
	}
}

##created
官方说明：实例已经创建完成之后被调用。 在这一步，实例已完成以下的配置：数据观测(data observer)，属性和方法的运算watch/event事件回调。然而，挂载阶段还没开始，$el属性目前不可见。
解决说明：这个时候可以操作vue实例的数据和各种方法，但是还不能对"dom"节点进行操作

created() {
	console.log(this.page); // 123
	console.log{this.showPage); // ...
	$('select').select2(); // jQuery插件需要操作相关dom，不会起作用
},
data() {
	return {
	 page: 123
	}
},
methods: {
	showPage() {
	 console.log(this.page);
	}
}

3.beforeMounte
官方说明：在挂载开始之前被调用,相关的render函数首次被调用。

4.mounted
官方说明： el被被新创建的vm.$el替换，并挂载到实例上去之后调用该钩子。如果root实例挂载了一个文档内元素，当mounted被调用时vm.$el也在文档内。
解释说明：挂载完毕，这时dom节点被渲染到文档内，一些需要dom的操作在些时才能正常进行

mounted() {
	$('select').select2(); // jQuery插件可以正常使用
},
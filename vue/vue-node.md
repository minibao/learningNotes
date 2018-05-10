#VUE在node下的初始化


正常的配置
var app = new Vue({
    el: '#app',
    components: {
         app: App
    }
})


手动挂载，延迟处理
new Vue({
	render: h => h(App)
})
.$mount("#app")


完整配置
new Vue({
	el: '#app',
	router,
	render: h => h(App)
	// render: x => x(App)
	// 这里的render: x => x(App)是es6的写法
	// 转换过来就是：  暂且可理解为是渲染App组件
	// render:(function(x){
	//  return x(App);
	// });
});
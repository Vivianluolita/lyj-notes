### 项目搭建
1. 先安装webpack vue 
```
vue init webpack Vue-Project

```
2. header组件负责头  左侧组件  右侧组件（右侧包含分页等  考虑vue路由）
3. 编写App.vue 去掉`id = App`
4. 渲染index.html `<view-router></view-router>`
5. 当没有el实例时候，需要手动挂载$mount,重写main.js
```
import Vue from 'vue';
import VueRouter from 'vue-router';
import App from './App';
Vue.use(VueRouter);// 安装路由功能
let routes = [
  {
    path: '/',
    name: 'index',
    component: App,
    children: [
      {path: '/goods', component: goods},
      {path: '/ratings', component: ratings},
      {path: '/seller', component: seller}
    ]
  }
];
let router = new VueRouter({
  'linkActiveClass': 'active',
  routes
});
let app = new Vue({
  router
}).$mount('#app');
export default app;

```
- [vue-router如何定义嵌套路由](https://www.kancloud.cn/hanxuming/vue-iq/733853)
- [router-link组件及其属性](https://www.kancloud.cn/hanxuming/vue-iq/738708)
-[keep-alive 动态组件缓存](https://cn.vuejs.org/v2/guide/components-dynamic-async.html)
6. element-ui
```
npm install --save element-ui
main.js 

```
7. element-ui
```
el-menu 菜单
el-menu-item 菜单项 
el-submenu 菜单项（单项）

[深入理解vue中的slot与slot-scope](https://juejin.im/post/5a69ece0f265da3e5a5777ed)
[element-ui menu](http://element.eleme.io/#/zh-CN/component/menu)

```
8. config/index.js
```
assetsPublicPath：资源目录，默认是这样配置的assetsPublicPath: '/'，指assetsSubDirectory目录也就是js,css,img等资源相对于服务器host地址，传说中的绝对路径，host是什么,ip地址加端口号，比如http://192.168.0.102:8089/new...，其host指的就是http://192.168.0.102:8089，所以如果你如果和我一样，用的是tomcat服务器，那就会遇到当我们要访问我们的网页时,访问的地址是http://ip:port/projectName/in...一般没有项目会直接用http://ip:port/index.html这个地址。所以像上面提到的js路径地址，这时就会被解析成http://ip:port/static/js/mani...，而正确的的url路径应该是http://ip:port/projectName/st...，所以我们需要将assetsPublicPath: '/'改成assetsPublicPath: '/projectName/'，这样才能保证资源的正确发布。
[webpack再入门，说一下那些不入流的知识点](https://segmentfault.com/a/1190000010627001)

修改index.js
build: {
    // Template for index.html
    index: path.resolve(__dirname, './dist/index.html'),

    // Paths 修改dist 配置
    assetsRoot: path.resolve(__dirname, './dist'),
    assetsSubDirectory: 'static',
    assetsPublicPath: '',
npm run build生成dist目录下的静态资源，并上传的gh-pages
```


## Vue项目案例demo

## 第一章 Vue.js简介

> 从前端开发趋势分析开始，引入 MVVM 开发框架和 Vue.js，接着对比流行框架Angular 和 React，最后详细介绍 Vue.js 的核心思想-数据驱动和组件化。

### 为什么用Vue进行开发?

* Vue.js的定义

  * 轻量级的构建用户界面的MVVM框架

  * 数据驱动:  

    > 不需要手动操作DOM, 只需要改变数据Model, 只要数据发生变化, Directives指令就会操作对应的DOM

  * 双向数据绑定的原理: 视图和数据保持一致
    >1. Model -> View
    >     * 从服务器获取数据通过渲染展现到视图上
    >     * 每当数据更新, 会再次进行渲染,从而更新视图.
    >
    >2. Model <- View
    >
    >   * 页面也会通过用户的交互,产生状态,数据的变化.
    >   * 将视图对数据的更新同步到数据, 以至于同步到后台服务器
    >
    >​

  * 组件化的前端开发

    > 页面上每个独立的可视/可交互的区域为一个组件
    >
    > 每个组件对应一个工程目录, 组件所需要的各自资源在做个目录下就近维护
    >
    > 页面是组件的容器, 组件可以嵌套,自由组合形成完整的页面
    >
    > ​

  ​

* MVVM框架 (Vue.js / React.js / Angular.js)
  - M:  Model(数据层)对应的是JS对象

  - V: View(视图层)对应的是DOM操作

  - VM: Vue实例, 负责M与V的交互

    ​

  - 针对具有复杂交互逻辑的前端应用

  - 提供基本的框架抽象

  - 通过Ajax数据持久化

  - 双向数据绑定

  ​


* Vue比较其他前端框架的优势

  * 对比Angular React
    * Vue.js更轻量,  gzip后大小只有20k, 适合移动端开发
    * 渲染速度快
    * 依赖少, 上手快
    * 综合了其他框架的优势, 如`Virtual DOM` , 视图组件
    * 有配套的路由和负责状态管理的库


*   代码少, 速度快的开发模式

    * 使用`Vue.js+ES6+Webpack`，采用组件化、模块化的开发方式，用更少的代码做更快速的开发

      ​




* Vue.js生态环境

  * 开源项目


* 基于ES6语法的插件
    * vue-router
    * vue-resoure


* 完善的社区, Github超过46k+
  * 兼容和性能
    * 主流浏览器和手机都支持

* 2.0和1.0的区别

  * 先去github上看作者的issue# changes

  ​


### 学习目标

*  流程及开发方法

  了解一个项目完整的开发流程

  学会组件化、模块化的开发模式

  掌握使用Vue-cli脚手架初始化Vue.js项目

  了解webpack的打包原理

  学会模拟json后端数据，前后端分离开发

  学会es6+eslint的开发方式


* 第三方组件

  学会使用`stylus`编写模块化的CSS

  学会使用`vue-router`开发单页应用

  学会使用`vue-resource`与后端数据交互

  学会如何在Vue.js框架里和第三方JS插件交互


* 设计思想与模式

  学会使用Vue.js的过渡编写酷炫的交互动画

  了解移动端设备像素比的概念

  学会制作并使用图标字

  学会解决移动端1px边框问题

  学会移动端经典的`css sticky footer`布局

  学会flex弹性布局

  ---

## 第2章 Vue-cli 开启 Vuejs 项目

> 1. Vue-cli: Vue的脚手架工具
>    * 目录结构
>    * 代码部署
>    * 本地调试
>    * 热加载
>    * 单元测试



## 第3章 项目实战-准备工作

> 分析外卖 APP 商家页面的需求，准备图片资源，利用 icon-moon 把 svg 制作成图标字体，对代码的目录结构设计，最后 mock 测试数据。



## 第4章 项目实战-页面骨架开发

> 设计页面的骨架，拆分组件，商品、评论和商家详情页利用 Vue-router 做切换，最后还介绍了 flex 弹性布局以及移动端 1 像素 border 实现的小技巧。



## 第5章 项目实战-header组件开发

> 编写 header 头部组件，应用 Vue-resource 从服务端读取数据，介绍如何在 Vue.js 中使用过渡动画，如何编写 css sticky footer 布局，如何从需求中抽象出 star 星星组件...



## 第6章 项目实战-goods 商品列表页开发

> 编写 goods 商品组件，包括它的子组件 shopcart 购物车。介绍了如何在 Vue.js 应用第三方 JS 插件 better-scroll实现列表滚动，并配合 Vue.js 的计算属性来实现左右列表的联动。应用了自定义 Vue.js 过渡动画实现了购物车的飞入动画效果，介绍了在 Vue.js中父子组件如何通讯...



## 第7章 项目实战-food 商品详情页实现

> 编写 food 商品详情页组件，介绍了图片占位的技巧，并从需求中抽象出的 split 分隔组件和 ratingselect 评论组件，实现自定义过滤器 datefilter...



## 第8章 项目实战-ratings评价列表页实现

> 编写 ratings 评价列表页，感受在 Vue.js 中复用组件的好处，实现快速开发...



## 第9章 项目实战-seller 商家详情页实现

> 编写 seller 商家详情页，实现一套通用移动端数据存取方案，以及对项目做一些体验上的优化..



## 第10章 项目实战-项目编译打包

> 上线前的最后一步，编译打包Vue.js 项目。介绍了 webpack 编译时的配置，如何利用node.js 开启一个server本地调试...



## 第11章 课程总结

> 对课程做总结，并列出了课程所提到的主要知识点的链接，作为课程的延伸学习..


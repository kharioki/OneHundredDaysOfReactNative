


# 注意事项

## 开发环境
* nvm -> nodeJS 版本切换
* react-native-cli 版本查看
* react-native 版本查看(项目中)
* react-native 版本升级及降级(项目中)
* react-native webstorm 语法智能提示

## JavaScript语法转换器

   语法转换器可以使编写代码的过程更加享受，因为开发者可以借助转换器直接使用新的JavaScirpt语法标准，而无需等待JS解释器的支持。

   React Native从0.5.0版本开始已经内置Babel转换器。你可以查看Babel的文档来了解有关它可以转换的语法的详情。

   这里可以看到目前React Native默认开启的语法转换特性。

   ES5

       保留关键字: promise.catch(function() { });

   ES6

       箭头函数Arrow functions: <C onPress={() => this.setState({pressed: true})}
       块级作用域Block scoping: let greeting = 'hi';
       数组的扩展运算Call spread: Math.max(...array);
       类Classes: class C extends React.Component { render() { return <View />; } }
       常量Constants: const answer = 42;
       解构Destructuring: var {isActive, style} = this.props;
       for...of: for (var num of [1, 2, 3]) {}
       模块Modules: import React, { Component } from 'react';
       动态属性键Computed Properties: var key = 'abc'; var obj = {[key]: 10};
       对象方法的简写Object Consise Method: var obj = { method() { return 10; } };
       对象属性的简写Object Short Notation: var name = 'vjeux'; var obj = { name };
       参数的扩展运算Rest Params: function(type, ...args) { }
       字符串模板Template Literals: var who = 'world'; var str = `Hello ${who}`;

   ES7

       对象的扩展运算Object Spread: var extended = { ...obj, a: 10 };
       参数列表末尾允许放置逗号Function Trailing Comma: function f(a, b, c,) { }
       Async函数: async function doStuffAsync() { const foo = await doOtherStuffAsync(); };

   其他特性

       JSX: <View style={{color: 'red'}} />
       Flow: function foo(x: ?number): string {}

   接口兼容（Polyfills）

   许多标准功能也都在支持的JavaScript运行环境上做了兼容支持。

   浏览器

       console.{log, warn, error, info, trace, table}
       CommonJS require
       XMLHttpRequest, fetch
       {set, clear}{Timeout, Interval, Immediate}, {request, cancel}AnimationFrame
       navigator.geolocation

   ES6

       Object.assign
       String.prototype.{startsWith, endsWith, repeat, includes}
       Array.from
       Array.prototype.{find, findIndex}

   ES7

       Object.{entries, values}

   其他特性

       __DEV__


## AppRegistry 坑, moduleName与class对象是分开定义的

## es6 写react-native 对象旧es5

## es6 详解系列blog

## 每个组件只能return一个单独的View容器

## 封装组件

## js打包(curl url -o main.jsbundel)及app内部发布

## flexbox 布局
* View style flex的坑, 默认每个View都自带display默认每个View都自带display: flex及flex容器各样式属性的默认值, flexDirection默认值不同于html5的横排而是竖排
* View style flex alignItems 默认值为'stretch', 容器的子元素这个方向的宽或高会继承这个方向父元素的宽或高, 设置为'center'后容器中的子元素变为内容自适应这个方向的宽或高
* View style flex 当容器中只有一个子元素时,容器设置justifyContent: 'center'和'space-around'效果是一样的

## View
* Text 才能使用html5部分文本样式, 其他标记, 如View不会生效
* 标记的style写法, 字面量二个大括号, 单个style定义一个大括号, 多个style定义一个大括号+数组
* 属性ref使用方法及作用(js获取react-native元素对象)
* 通过ref获取元素对象, 改变style样式属性(setNativeStyle)

## Image
* react-native 静态图片 不需要手动指定尺寸
* ios原生app 资源图片 不需要手动指定尺寸
* network 网络图片
* 本地文件系统中的图片(重要! 比如:相册图片, 还未查看camera roll例子)
* 模拟实现背景图片

* resize Mode(cover, contain, stretch), 前二者效果同css3 background-size
* 图片预加载 0.25版本开始直接支持
* 图片加载进度控制
* 图片加载onError触发后,会自动重新发几次请求,造成多次onLoadStart
* 获取图片实际尺寸(多用于网络图片)
* 支持gif动画图(ios)
* tintColor 设置所有非透明的像素点颜色, 矢量图上特别有用
* capInsets {top: number, left: number, bottom: number, right: number}
  (对图片)当图片被缩放的时候，capInsets指定的角上的尺寸会被固定而不进行缩放，而中间和边上其他的部分则会被拉伸。这在制作一些可变大小的圆角按钮、阴影、以及其它资源的时候非常有用（译注：这就是常说的九宫格或者.9图

## CSS
* 支持rgba配色, 如backgroundColor: 'rgba(0, 0, 100, 0.25)'
* 支持opacity透明度
* Text中的子Text连backgroundColor都可以继承-_-!!!

## Text
* Text中的子Text设置padding,margin无效

## Dimensions
* Dimensions.get('window').width/height, 必须等初始View加载完成后才有值, 否则为undefined

## gesture/responder (非常重要, 有点复杂)
* 普通事件响应  支持从捕获,目标,冒泡三个阶段的事件的处理, 支持阻止捕获和冒泡  (注意:响应者的生命周期)
* 手势事件响应  PanResponder支持特殊手势响应, 也同时支持普通事件响应

## Animatation
*  Animated 默认可以对Image, Text, View实现动画, 可以扩展动画组件, 通过直接的API声明来产生实际动画
*  LayoutAnimation 实现效果相对比较简单, 通过state改变来产生实际动画
*  注意Animation动画设置的View的位置,

## Navigator
*  Navigator自定义手势事件, 切换动画等(需要使用Navigator而不是NavigatorIOS, 垂直旋转, 侧滑回退等)
*  顶部StausBar预留20pt, NavigatorIOS.title预留44pt, Navigator.title高度暂未知(猜测也是44pt)
*  同一个NavigatorIOS的title栏设置隐藏或显示后, 无法再变更成显示或隐藏(???不确定???)
*  使最外层的navigator的component部分显示时, 一定得保证statusbar显示, 否则会导致navigator的顶部不会跟在statusbar之下
*  NavigatorIOS(Navigator也一样), 使用TabBarIOSj时, 不得不在最外层包一个NavigatorIOS(Navigator), 判断nav的willfocus和didfocus时需要在最外层留意一下判断条件的区别
*  NavigatorIOS在push时, 如果push前的主屏有一些动画效果, 比如(react-native-swipe的ScrollView的scrollTo动画效果), 有时会出现图片切换了一部分, 没有全部切换到底的问题...
*  放弃Navigator, 改为尝试Navigator
*  Navigator动画采用各种SwipeJump时, 会和同方向的react-native-swipe手势事件冲突, 导致第三方插件swipe效果失效
*  Navigator不会自动计算并空出NavBar的高度给子View(在StatusBar显示时, 会自动空出对应的高度), 需要在renderScene中自定义空出, 如果Navigator加载时StatusBar隐藏了, 则不会计算StatusBar的高度
*  Navigator目前试下来, 只能靠自定义事件修改主屏定义根Navigator的属性navigatorBar(navigatorIOS可以依靠push时改写navBar的设置), 才能针对不同的route显示(隐藏)不同的自定义navBar
*  NavigatorBar设置背景透明度有效,但透明的范围只有高度的一半,还未找到导致该问题的原因@todo

## ScrollView
*  @todo 尝试, 以及上拉刷新, 属性控制, 优化, 定制

## ListView
*  @todo 尝试, 以及上拉刷新, 下拉加载, 属性控制, 优化, 定制

## SegmentedControl
* ios -> SegmentedControlIOS
* android -> react-native-radio-buttons

## radioButton
* react-native-radio-buttons

## checkbox
* Switch or react-native-item-checkbox

## TabBar(bottom)
* ios -> TabBarIOS
* android -> react-native-scrollable-tab-view (scroll Tab effect, also can use as top tabs)
* TabBarIOS内使用Navigator, 当切换TabBarItem时, 会自动重绘Navigator的内容, 需要自已定义shouldComponentUpdate, 在state里加一个更新state的时间戳, 来避免无谓的重绘操作
* TabBarIOS切换TabBarItem时, react-native-swiper图片正在切换时, 也会导致没有切换完整的问题
* 因为上面一条的问题, @todo 尝试一下用第三方的TabBar组件替换TabBarIOS, 或者只是android上使用 (react-native-tab-navigator || react-natve-tabs)
* react-native-tab-navigator ios试验成功, 但和TabBarIOS相比存在tab切换的View高度不包含底部bar高度的问题, 将无法实现TabBarIOS中半透明显示tab切换的View部分的效果

## upload/download + progress

## fetch
*  已支持timeout设置

## 版本
* 新版本导致API的位置有所变化, 使用旧api方式会报警告


## 组件自定义事件通信
* 不同组件间的通信, tabbarIOS切换时的通信等
* RCTDeviceEventEmitter
* 需要单独将所有自定义事件定义成对象的形式, 方便管理, 调用, 避免手写自定义事件名称(避免手写字符串失误)

## 模拟ios的viewWill/DidAppear和android的activity的onResume
* Navigator的context绑定willfocus和didfocus事件监听, 要注意的是, 当被其他View在加载时遮住时, 事件会触发2次,
  事件监听处理器中编写逻辑代码可能需要加入小间隔的函数节流方式, 获者有更好的方式来避免

## 优化避免无谓的render
* 生命周期事件shouldComponentUpdate
* 通过定义ref='字符串'或ref= (component) => {this._component = component}, this._component.setNativeProps(changedProps)

## View的基础及常用组件需要预先定义好
* 详见mui

## 调用源生能力的常用组件需要预先定义好
* 详见h5+

# Daily

# day1
## An entrance advertisement swiper app
* ios9 how to set LanchImage
* react-native-swiper
* CSS, Image(resizeMode), Dimensions, PixelRatio

# day2
## An entrance animation app
* countdown
* Animated, position'absolute'

# day3
* StatusBar
* TabBarIOS

# day4
* react-native-tab-navigator android/ios替代TabBarIOS
* react-native-linear-gradient element(for styling button)
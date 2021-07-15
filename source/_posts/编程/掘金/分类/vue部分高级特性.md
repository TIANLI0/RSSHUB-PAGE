
---
title: 'vue部分高级特性'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1638187555b14d558e4688f402055bb3~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 22:24:55 GMT
thumbnail: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1638187555b14d558e4688f402055bb3~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h2 data-id="heading-0">概述</h2>
<p>文章将讲述指令、混入、高阶组件、函数式组件、@hook、异步组件等内容。如果文中有不当的地方欢迎指正哦！</p>
<h2 data-id="heading-1">特性以及部分原理</h2>
<h3 data-id="heading-2">自定义指令（directive）</h3>
<p>除了核心功能默认内置的指令 (v-model 和 v-show)，Vue 也允许注册自定义指令。有时候我们想对dom进行操作的时候，就可以使用自定义指令，比如设置标题样式并且让标题一直固定在页面上方，可以使用全局注册或者局部注册。然后你可以在模板中任何元素上使用新的 v-title property。</p>
<pre><code class="copyable">//全局注册
<div id="app">
    <div v-title>hello world</div>
</div>
<script>
    Vue.directive('title', &#123;
        inserted: function (el) &#123;
            console.log(el)
            el.style.position = 'fixed' 
            el.style.top = '50px' 
            el.style.left = '48%' 
            el.style.color = '#409EFF' 
        &#125;
    &#125;)

    new Vue(&#123;
        el: '#app',
        data: &#123;
            message: 'hello!'
        &#125;
    &#125;)
</script>
<style>
   #app&#123;
       height: 1000px
   &#125; 
</style>
//局部注册
  new Vue(&#123;
    el: '#app',
    directives: &#123;
        title: &#123;
            inserted: function (el) &#123;
                console.log(el)
                el.style.position = 'fixed'
                el.style.top = '50px'
                el.style.left = '48%'
                el.style.color = '#409EFF'
            &#125;
        &#125;
    &#125;
  &#125;)
<span class="copy-code-btn">复制代码</span></code></pre>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1638187555b14d558e4688f402055bb3~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h4 data-id="heading-3">directive钩子函数参数</h4>
<p>指令钩子函数会被传入以下参数：</p>
<ul>
<li>el：指令所绑定的元素，可以用来直接操作 DOM。</li>
<li>binding：一个对象，包含以下 property：</li>
</ul>
<ol>
<li>name：指令名，不包括 v- 前缀。</li>
<li>value：指令的绑定值，例如：v-my-directive="1 + 1" 中，绑定值为 2。</li>
<li>oldValue：指令绑定的前一个值，仅在 update 和 componentUpdated 钩子中可用。无论值是否改变都可用。</li>
<li>expression：字符串形式的指令表达式。例如 v-my-directive="1 + 1" 中，表达式为 "1 + 1"。</li>
<li>arg：传给指令的参数，可选。例如 v-my-directive:foo 中，参数为 "foo"。</li>
<li>modifiers：一个包含修饰符的对象。例如：v-my-directive.foo.bar 中，修饰符对象为 &#123; foo: true, bar: true &#125;。</li>
</ol>
<ul>
<li>vnode：Vue 编译生成的虚拟节点。移步 VNode API 来了解更多详情。</li>
<li>oldVnode：上一个虚拟节点，仅在 update 和 componentUpdated 钩子中可用。</li>
</ul>
<p>我们打印下函数传入的参数，其实简单来说就是el就是绑定dom元素，binging指令：后所携带的具体内容，VNode就当还未生成的节点好了。</p>
<pre><code class="copyable"><div v-title:arr="message">hello world</div>
Vue.directive('title', &#123;
        inserted: function (el, binding, vnode) &#123;
            console.log(el, binding, vnode)
            el.style.position = 'fixed' 
            el.style.top = '50px' 
            el.style.left = '48%' 
            el.style.color = '#409EFF' 
        &#125;
    &#125;)
<span class="copy-code-btn">复制代码</span></code></pre>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f7ca06dcfb2f4034acc2ce3fc19950cc~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h4 data-id="heading-4">钩子函数</h4>
<p>一个指令定义对象可以提供如下几个钩子函数 (均为可选)：</p>
<ul>
<li>bind：只调用一次，指令第一次绑定到元素时调用。在这里可以进行一次性的初始化设置。</li>
<li>inserted：被绑定元素插入父节点时调用 (仅保证父节点存在，但不一定已被插入文档中)。</li>
<li>update：所在组件的 VNode 更新时调用，但是可能发生在其子 VNode 更新之前。指令的值可能发生了改变，也可能没有。但是你可以通过比较更新前后的值来忽略不必要的模板更新 (详细的钩子函数参数见下)。</li>
<li>componentUpdated：指令所在组件的 VNode 及其子 VNode 全部更新后调用</li>
<li>unbind：只调用一次，指令与元素解绑时调用。</li>
</ul>
<p>我们可以测试下钩子函数的调用时机：</p>
<pre><code class="copyable"><div id="app">
    <div id="txt" v-title:data="sum">value: &#123;&#123;sum&#125;&#125;</div>
</div>
<script>
    new Vue(&#123;
        el: '#app',
        data: &#123;
            sum: 0
        &#125;,
        directives: &#123;
            title: &#123;
                bind: (el, bind) => &#123; console.log(bind.value, 'a') &#125;,// 第一次绑定元素时调用
                inserted: (el, bind) => &#123; console.log(bind.value, 'b') &#125;,// 当被绑定的元素插入到 DOM 中时……
                update: (el, bind) => &#123; console.log(bind.value, 'c') &#125;,// 所在组件VNode发生更新时调用
                componentUpdated: (el, bind) => &#123; console.log(bind.value, 'd') &#125;, // 指令所在组件的 VNode 及其子 VNode 全部更新后调用
                unbind: (el, bind) => &#123; console.log(bind.value, 'e') &#125;    // 只调用一次，指令与元素解绑时调用
            &#125;
        &#125;,
        mounted() &#123;
            console.log(this.sum, '???')
            let timer = setInterval(() => &#123;
                this.sum++
            &#125;, 200)
            setTimeout(() => &#123;
                clearInterval(timer)
            &#125;, 3000)
        &#125;
    &#125;)
</script>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2eca9c48154b451084e5fab075dbf3a7~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h4 data-id="heading-5">指令大致原理</h4>
<p>在页面渲染的过程中，分别有创建(create)、激活(avtivate)、更新(update)、移除(remove)、销毁(destroy)，在这些过程中，框架在每个时段都会调用相应的钩子函数，这些hooks中一部分的函数就包含了我们的指令。源码部分我了解的不多，给大家推荐一篇vue指令原理相关博文<a href="https://link.juejin.cn/?target=https%3A%2F%2Fwww.cnblogs.com%2Fgerry2019%2Fp%2F14940770.html%25E3%2580%2582" target="_blank" rel="nofollow noopener noreferrer" title="https://www.cnblogs.com/gerry2019/p/14940770.html%E3%80%82" ref="nofollow noopener noreferrer">www.cnblogs.com/gerry2019/p…</a></p>
<h3 data-id="heading-6">混入</h3>
<p>官方是这样定义的：混入 (mixin) 提供了一种非常灵活的方式，来分发 Vue 组件中的可复用功能。一个混入对象可以包含任意组件选项。当组件使用混入对象时，所有混入对象的选项将被“混合”进入该组件本身的选项。其实就是vue实例的一个复用。实用场景：公共组件或者功能，例如获取用户白名单、菜单返回、公共基础table。
值得注意的点：</p>
<ol>
<li>当组件和混入对象含有同名选项时，这些选项将以恰当的方式混合。比如，数据对象在内部会进行浅合并 (一层属性深度)，在和组件的数据发生冲突时以组件数据优先。</li>
<li>同名钩子函数将混合为一个数组，因此都将被调用。另外，混入对象的钩子将在组件自身钩子之前调用。</li>
<li>值为对象的选项，例如 methods, components 和 directives，将被混合为同一个对象。两个对象键名冲突时，取组件对象的键值对。</li>
</ol>
<pre><code class="copyable">var mixin = &#123;
  data: function () &#123;
    return &#123;
      message: 'hello',
      foo: 'abc'
    &#125;
  &#125;
&#125;

new Vue(&#123;
  mixins: [mixin],
  data: function () &#123;
    return &#123;
      message: 'goodbye',
      bar: 'def'
    &#125;
  &#125;,
  created: function () &#123;
    console.log(this.$data)
    // => &#123; message: "goodbye", foo: "abc", bar: "def" &#125;
  &#125;
&#125;)
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-7">高阶组件</h3>
<p>一个函数接受一个组件为参数，返回一个包装后的组件。其实在vue中，组件可以当做一个函数，那从本质上来说，高阶组件就是高阶函数（JavaScript的函数其实都指向某个变量。既然变量可以指向函数，函数的参数能接收变量，那么一个函数就可以接收另一个函数作为参数，这种函数就称之为高阶函数）</p>
<h4 data-id="heading-8">高阶函数</h4>
<p>举例一个最简单的高阶函数计算次方</p>
<pre><code class="copyable"> function pow(x, y, f)&#123;
    return f(x, y);
  &#125;
  pow(3, 3, Math.pow)
<span class="copy-code-btn">复制代码</span></code></pre>
<p>在es6中也有很多高阶函数，如map、reduce、filter。</p>
<h4 data-id="heading-9">高阶组件的例子</h4>
<pre><code class="copyable"><div id="app">
    <hoc></hoc>
</div>
<script>
    const view = &#123;
        template: `<span>
                    <span>test hoc ...</span>
                    </span>`,
        props: ["result", "loading"],
    &#125;;
    const test = (wrapped, txt = 'hello') => &#123;
        return &#123;
            render(h) &#123;
                const args = &#123;
                    props: &#123;
                        result: this.result,
                        loading: this.loading,
                    &#125;,
                &#125;;
                const wrapper = h("div", [
                    h(wrapped, args),
                    'loading'
                ]);
                return wrapper
            &#125;
        &#125;
    &#125;
    const hoc = test(view, 'hui')
    console.log(hoc);

    new Vue(&#123;
        el: '#app',
        components: &#123;
            hoc
        &#125;,
        data: &#123;
            sum: 0
        &#125;
    &#125;)
</script>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f9adf8cd08ef4754b32ad34e16f48fe7~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h4 data-id="heading-10">值得注意的点</h4>
<ol>
<li>高阶组件(HOC)应该是无副作用的纯函数，且不应该修改原组件,就是组件是一个新的组件，不会对原组件做修改。</li>
<li>高阶组件(HOC)不关心你传递的数据(props)是什么，并且被包装组件(WrappedComponent)不关心数据来源</li>
<li>高阶组件(HOC)接收到的 props 应该透传给被包装组件(WrappedComponent)</li>
<li>在高阶组件中渲染函数向子组件中传递作用域插槽时候要注意上下文</li>
</ol>
<h3 data-id="heading-11">动态组件 异步组件 递归组件</h3>
<h4 data-id="heading-12">动态组件</h4>
<p>可以在同组件之间进行动态切换，
动态切换可以通过 Vue 的  元素加一个特殊的 is attribute 来实现：</p>
<pre><code class="copyable"><!-- 组件会在 `currentTabComponent` 改变时改变 -->
<!DOCTYPE html>
<html>
  <head>
    <title>Dynamic Components Example</title>
    <script src="https://unpkg.com/vue"></script>
    <style>
      .tab-button &#123;
        padding: 6px 10px;
        border-top-left-radius: 3px;
        border-top-right-radius: 3px;
        border: 1px solid #ccc;
        cursor: pointer;
        background: #f0f0f0;
        margin-bottom: -1px;
        margin-right: -1px;
      &#125;
      .tab-button:hover &#123;
        background: #e0e0e0;
      &#125;
      .tab-button.active &#123;
        background: #e0e0e0;
      &#125;
      .tab &#123;
        border: 1px solid #ccc;
        padding: 10px;
      &#125;
    </style>
  </head>
  <body>
    <div id="dynamic-component-demo" class="demo">
      <button
        v-for="tab in tabs"
        v-bind:key="tab"
        v-bind:class="['tab-button', &#123; active: currentTab === tab &#125;]"
        v-on:click="currentTab = tab"
      >
        &#123;&#123; tab &#125;&#125;
      </button>

      <component v-bind:is="currentTabComponent" class="tab"></component>
    </div>

    <script>
      Vue.component("tab-home", &#123;
        template: "<div>Home component</div>"
      &#125;);
      Vue.component("tab-posts", &#123;
        template: "<div>Posts component</div>"
      &#125;);
      Vue.component("tab-archive", &#123;
        template: "<div>Archive component</div>"
      &#125;);

      new Vue(&#123;
        el: "#dynamic-component-demo",
        data: &#123;
          currentTab: "Home",
          tabs: ["Home", "Posts", "Archive"]
        &#125;,
        computed: &#123;
          currentTabComponent: function() &#123;
            return "tab-" + this.currentTab.toLowerCase();
          &#125;
        &#125;
      &#125;);
    </script>
  </body>
</html>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-13">异步组件</h4>
<p>在大型应用中，我们可能需要将应用分割成小一些的代码块，并且只在需要的时候才从服务器加载一个模块。为了简化，Vue 允许你以一个工厂函数的方式定义你的组件，这个工厂函数会异步解析你的组件定义。Vue 只有在这个组件需要被渲染的时候才会触发该工厂函数，且会把结果缓存起来供未来重渲染。</p>
<pre><code class="copyable">Vue.component('async-example', function (resolve, reject) &#123;
  setTimeout(function () &#123;
    // 向 `resolve` 回调传递组件定义
    resolve(&#123;
      template: '<div>I am async!</div>'
    &#125;)
  &#125;, 1000)
&#125;)
<span class="copy-code-btn">复制代码</span></code></pre>
<p>在vue-cli中在使用异步组件</p>
<pre><code class="copyable">const first =()=>import(/* webpackChunkName: "group-foo" */ "../components/first.vue");
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-14">vue中部分钩子函数(@hook)</h3>
<p>Vue 实例同时在其事件接口中提供了其它的方法。我们可以：</p>
<blockquote>
<p>通过 $on(eventName, eventHandler) 侦听一个事件</p>
</blockquote>
<blockquote>
<p>通过 $once(eventName, eventHandler) 一次性侦听一个事件</p>
</blockquote>
<blockquote>
<p>通过 $off(eventName, eventHandler) 停止侦听一个事件</p>
</blockquote>
<p>你通常不会用到这些，但是当你需要在一个组件实例上手动侦听事件时，它们是派得上用场的。它们也可以用于代码组织工具。例如，你可能经常看到这种集成一个第三方库的模式。官网提供一个案例：在不使用beforeDestroy钩子清picker</p>
<pre><code class="copyable">//案例一
mounted: function () &#123;
  var picker = new Pikaday(&#123;
    field: this.$refs.input,
    format: 'YYYY-MM-DD'
  &#125;)

  this.$once('hook:beforeDestroy', function () &#123;
    picker.destroy()
  &#125;)
&#125;
//案例二
//在父组件在子组件渲染阶段做一些操作
<child
  @hook:mounted="handle"
  @hook:beforeUpdated="xxx"
  @hook:updated="xxx"
/>
method () &#123;
  handle() &#123;
  // do something...
  &#125;
&#125;,
<span class="copy-code-btn">复制代码</span></code></pre>
<p>在vue生命周期中周期都有对应的钩子函数</p>
<h3 data-id="heading-15">插件</h3>
<p>插件通常用来为 Vue 添加全局功能。插件的功能范围没有严格的限制——一般有下面几种：</p>
<ul>
<li>
<p>添加全局方法或者 property。如：vue-custom-element</p>
</li>
<li>
<p>添加全局资源：指令/过滤器/过渡等。如 vue-touch</p>
</li>
<li>
<p>通过全局混入来添加一些组件选项。如 vue-router</p>
</li>
<li>
<p>添加 Vue 实例方法，通过把它们添加到 Vue.prototype 上实现。</p>
</li>
<li>
<p>一个库，提供自己的 API，同时提供上面提到的一个或多个功能。如 vue-router</p>
</li>
</ul>
<p>自定义插件</p>
<pre><code class="copyable">MyPlugin.install = function (Vue, options) &#123;
  // 1. 添加全局方法或 property
  Vue.myGlobalMethod = function () &#123;
    // 逻辑...
  &#125;

  // 2. 添加全局资源
  Vue.directive('my-directive', &#123;
    bind (el, binding, vnode, oldVnode) &#123;
      // 逻辑...
    &#125;
    ...
  &#125;)

  // 3. 注入组件选项
  Vue.mixin(&#123;
    created: function () &#123;
      // 逻辑...
    &#125;
    ...
  &#125;)

  // 4. 添加实例方法
  Vue.prototype.$myMethod = function (methodOptions) &#123;
    // 逻辑...
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-16">后续</h3>
<p>文章都在在官网文档上的整理和归纳，只是停留在表层，欢迎大家指正。定下 下一个目标：写一个小型vue-router。</p>
<h4 data-id="heading-17">引用</h4>
<p>vue官网 <a href="https://link.juejin.cn/?target=https%3A%2F%2Fcn.vuejs.org%2Fv2%2Fapi" target="_blank" rel="nofollow noopener noreferrer" title="https://cn.vuejs.org/v2/api" ref="nofollow noopener noreferrer">cn.vuejs.org/v2/api</a><br>
探索Vue高阶组件 <a href="https://link.juejin.cn/?target=https%3A%2F%2Fwww.jianshu.com%2Fp%2F6b149189e035" target="_blank" rel="nofollow noopener noreferrer" title="https://www.jianshu.com/p/6b149189e035" ref="nofollow noopener noreferrer">www.jianshu.com/p/6b149189e…</a><br>
Vue 进阶必学之高阶组件 HOC <a href="https://link.juejin.cn/?target=https%3A%2F%2Fzhuanlan.zhihu.com%2Fp%2F126552443" target="_blank" rel="nofollow noopener noreferrer" title="https://zhuanlan.zhihu.com/p/126552443" ref="nofollow noopener noreferrer">zhuanlan.zhihu.com/p/126552443</a> <br>
Vue指令实现原理 <a href="https://link.juejin.cn/?target=https%3A%2F%2Fwww.cnblogs.com%2Fgerry2019%2Fp%2F14940770.html" target="_blank" rel="nofollow noopener noreferrer" title="https://www.cnblogs.com/gerry2019/p/14940770.html" ref="nofollow noopener noreferrer">www.cnblogs.com/gerry2019/p…</a></p></div>  
</div>
            
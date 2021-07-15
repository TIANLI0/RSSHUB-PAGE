
---
title: '路由懒加载import和require用法的区别'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c71a6f9388bb462491990fc83b0157d0~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 19:33:49 GMT
thumbnail: 'https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c71a6f9388bb462491990fc83b0157d0~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h2 data-id="heading-0">vue-router同步和异步普通用法：</h2>
<pre><code class="copyable">// 普通import同步加载用法
import HelloWorld from "@/components/HelloWorld.vue"
export default new Router(&#123;
  routes:[
    &#123;
      path: "/",
      name: "HelloWorld",
      component: HelloWorld
    &#125;
  ]
&#125;)
 
// import 异步加载用法
export default new Router(&#123;
  routes:[
    &#123;
      path: "/",
      name: "HelloWorld",
      component: () => import("@/components/HelloWorld.vue")
    &#125;
  ]
&#125;)
 
// require 异步加载用法
export default new Router(&#123;
  routes:[
    &#123;
      path: "/",
      name: "HelloWorld",
      component: resolve => (require(["@/components/HelloWorld.vue"], resolve))
    &#125;
  ]
&#125;)
<span class="copy-code-btn">复制代码</span></code></pre>
<p><strong>上面是加载路由最常用的三种方法，那有时候需要几个路由合并到一起加载怎么办呢，按照官方教程的写法：</strong></p>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c71a6f9388bb462491990fc83b0157d0~tplv-k3u1fbpfcp-watermark.image" alt="QQ截图20210715113017.png" loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="copyable">const Foo = () => import(/* webpackChunkName: "group-foo" */ './Foo.vue')
const Bar = () => import(/* webpackChunkName: "group-foo" */ './Bar.vue')
const Baz = () => import(/* webpackChunkName: "group-foo" */ './Baz.vue')
<span class="copy-code-btn">复制代码</span></code></pre>
<p>import通过这种特殊注释语法，将几个路由放到一个组中，实际我平时也是按照这种方式去分组的，但这有时候不喜欢这种注释的风格咋办呢？</p>
<ul>
<li>实际上require也可以通过webpack提供的require.ensure功能进行分组（其实这属于老语法，import才是新语法），下面写法和官方文档是等价的。</li>
</ul>
<pre><code class="copyable">const Foo = resolve => require.ensure([], () => resolve(require('./Foo.vue')), 'group-foo')
const Bar = resolve => require.ensure([], () => resolve(require('./Bar.vue')), 'group-foo')
const Baz = resolve => require.ensure([], () => resolve(require('./Baz.vue')), 'group-foo')
<span class="copy-code-btn">复制代码</span></code></pre>
<p><strong>参数就不细说了，直接附上webpack相关文档说明，方便理解。</strong></p>
<pre><code class="copyable">在webpack 2的官网上写了这么一句话：
 
require.ensure()特定于的的的WebPack并由进口()取代。
所以，在webpack 2里面应该是不建议使用require.ensure()这个方法的。但是目前该方法仍然有效，所以可以简单介绍一下。包括在webpack 1中也是可以使用。下面是require.ensure的语法：
 
require.ensure(
  dependencies：String [],
  callback：function(require),
  errorCallback：function(error),
  chunkName：String
)
require.ensure()接受四个参数：
第一个参数的依赖关系是一个数组，代表了当前需要进来的模块的一些依赖; 
第二个参数回调就是一个回调函数其中需要注意的是，这个回调函数有一个参数要求，通过这个要求就可以在回调函数内动态引入其他模块值得注意的是，虽然这个要求是回调函数的参数，理论上可以换其他名称，但是实际上是不能换的，否则的的的的WebPack就无法静态分析的时候处理它; 
第三个参数errorCallback比较好理解，就是处理错误的回调; 
第四个参数chunkName则是指定打包的组块名称。

<span class="copy-code-btn">复制代码</span></code></pre></div>  
</div>
            
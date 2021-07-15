
---
title: 'Vue2.x项目骨架屏注入(上)'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a7504daa371f4c3ba28293a37ab18f52~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Tue, 13 Jul 2021 19:54:44 GMT
thumbnail: 'https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a7504daa371f4c3ba28293a37ab18f52~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h1 data-id="heading-0">骨架屏注入实践一：vue-skeleton-webpack-plugin</h1>
<p>骨架屏是在页面数据尚未加载前先给用户展示出页面的大致结构，直到请求数据返回后再渲染页面，补充进需要显示的数据内容。</p>
<p>骨架屏是预渲染机制中一种增强用户体验的方式。</p>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a7504daa371f4c3ba28293a37ab18f52~tplv-k3u1fbpfcp-watermark.image" alt="02.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p>生成骨架屏的技术方案有很多，大概方案有：</p>
<blockquote>
<ul>
<li>
<p>1、手动编写骨架屏代码</p>
</li>
<li>
<p>2、通过预渲染手动书写的代码生成相应的骨架屏， 比如：vue-skeleton-webpack-plugin</p>
</li>
<li>
<p>3、饿了么内部的生成骨架页面的工具：page-skeleton-webpack-plugin</p>
</li>
<li>
<p>4、JavaScript操作DOM 的方式结合 Puppeteer 自动生成网页骨架屏</p>
</li>
<li>
<p>其他... ...</p>
</li>
</ul>
</blockquote>
<p>本文主要介绍其中的一种：<strong><code>vue-skeleton-webpack-plugin</code></strong></p>
<h2 data-id="heading-1">（一）单页面骨架屏具体操作</h2>
<h3 data-id="heading-2">1、在项目中安装 vue-skeleton-webpack-plugin</h3>
<pre><code class="hljs language-js copyable" lang="js">npm i vue-skeleton-webpack-plugin -D
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-3">2、创建一个仅使用骨架屏组件的入口文件：</h3>
<p><img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8226ada78cd349cdbb46b78daca452d8~tplv-k3u1fbpfcp-watermark.image" alt="07.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p><strong>/src/components/Skeleton/entry-skeleton.js</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">import</span> Vue <span class="hljs-keyword">from</span> <span class="hljs-string">'vue'</span>;
<span class="hljs-keyword">import</span> Skeleton <span class="hljs-keyword">from</span> <span class="hljs-string">'./Skeleton'</span>;

<span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span> <span class="hljs-keyword">new</span> Vue(&#123;
    <span class="hljs-attr">components</span>: &#123;
        Skeleton
    &#125;,
    <span class="hljs-attr">template</span>: <span class="hljs-string">'<Skeleton />'</span>
&#125;);
<span class="copy-code-btn">复制代码</span></code></pre>
<p><strong>/src/components/Skeleton/Skeleton.vue</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><template>
    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"skeleton-wrapper"</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">header</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"skeleton-header"</span>></span><span class="hljs-tag"></<span class="hljs-name">header</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">section</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"skeleton-block"</span>></span>
            <span class="hljs-tag"><<span class="hljs-name">img</span> <span class="hljs-attr">src</span>=<span class="hljs-string">"data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB2aWV3Qm94PSIwIDAgMTA4MCAyNjEiPjxkZWZzPjxwYXRoIGlkPSJiIiBkPSJNMCAwaDEwODB2MjYwSDB6Ii8+PGZpbHRlciBpZD0iYSIgd2lkdGg9IjIwMCUiIGhlaWdodD0iMjAwJSIgeD0iLTUwJSIgeT0iLTUwJSIgZmlsdGVyVW5pdHM9Im9iamVjdEJvdW5kaW5nQm94Ij48ZmVPZmZzZXQgZHk9Ii0xIiBpbj0iU291cmNlQWxwaGEiIHJlc3VsdD0ic2hhZG93T2Zmc2V0T3V0ZXIxIi8+PGZlQ29sb3JNYXRyaXggaW49InNoYWRvd09mZnNldE91dGVyMSIgdmFsdWVzPSIwIDAgMCAwIDAuOTMzMzMzMzMzIDAgMCAwIDAgMC45MzMzMzMzMzMgMCAwIDAgMCAwLjkzMzMzMzMzMyAwIDAgMCAxIDAiLz48L2ZpbHRlcj48L2RlZnM+PGcgZmlsbD0ibm9uZSIgZmlsbC1ydWxlPSJldmVub2RkIiB0cmFuc2Zvcm09InRyYW5zbGF0ZSgwIDEpIj48dXNlIGZpbGw9IiMwMDAiIGZpbHRlcj0idXJsKCNhKSIgeGxpbms6aHJlZj0iI2IiLz48dXNlIGZpbGw9IiNGRkYiIHhsaW5rOmhyZWY9IiNiIi8+PHBhdGggZmlsbD0iI0Y2RjZGNiIgZD0iTTIzMCA0NGg1MzN2NDZIMjMweiIvPjxyZWN0IHdpZHRoPSIxNzIiIGhlaWdodD0iMTcyIiB4PSIzMCIgeT0iNDQiIGZpbGw9IiNGNkY2RjYiIHJ4PSI0Ii8+PHBhdGggZmlsbD0iI0Y2RjZGNiIgZD0iTTIzMCAxMThoMzY5djMwSDIzMHpNMjMwIDE4MmgzMjN2MzBIMjMwek04MTIgMTE1aDIzOHYzOUg4MTJ6TTgwOCAxODRoMjQydjMwSDgwOHpNOTE3IDQ4aDEzM3YzN0g5MTd6Ii8+PC9nPjwvc3ZnPg=="</span>></span>
            <span class="hljs-tag"><<span class="hljs-name">img</span> <span class="hljs-attr">src</span>=<span class="hljs-string">"data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB2aWV3Qm94PSIwIDAgMTA4MCAyNjEiPjxkZWZzPjxwYXRoIGlkPSJiIiBkPSJNMCAwaDEwODB2MjYwSDB6Ii8+PGZpbHRlciBpZD0iYSIgd2lkdGg9IjIwMCUiIGhlaWdodD0iMjAwJSIgeD0iLTUwJSIgeT0iLTUwJSIgZmlsdGVyVW5pdHM9Im9iamVjdEJvdW5kaW5nQm94Ij48ZmVPZmZzZXQgZHk9Ii0xIiBpbj0iU291cmNlQWxwaGEiIHJlc3VsdD0ic2hhZG93T2Zmc2V0T3V0ZXIxIi8+PGZlQ29sb3JNYXRyaXggaW49InNoYWRvd09mZnNldE91dGVyMSIgdmFsdWVzPSIwIDAgMCAwIDAuOTMzMzMzMzMzIDAgMCAwIDAgMC45MzMzMzMzMzMgMCAwIDAgMCAwLjkzMzMzMzMzMyAwIDAgMCAxIDAiLz48L2ZpbHRlcj48L2RlZnM+PGcgZmlsbD0ibm9uZSIgZmlsbC1ydWxlPSJldmVub2RkIiB0cmFuc2Zvcm09InRyYW5zbGF0ZSgwIDEpIj48dXNlIGZpbGw9IiMwMDAiIGZpbHRlcj0idXJsKCNhKSIgeGxpbms6aHJlZj0iI2IiLz48dXNlIGZpbGw9IiNGRkYiIHhsaW5rOmhyZWY9IiNiIi8+PHBhdGggZmlsbD0iI0Y2RjZGNiIgZD0iTTIzMCA0NGg1MzN2NDZIMjMweiIvPjxyZWN0IHdpZHRoPSIxNzIiIGhlaWdodD0iMTcyIiB4PSIzMCIgeT0iNDQiIGZpbGw9IiNGNkY2RjYiIHJ4PSI0Ii8+PHBhdGggZmlsbD0iI0Y2RjZGNiIgZD0iTTIzMCAxMThoMzY5djMwSDIzMHpNMjMwIDE4MmgzMjN2MzBIMjMwek04MTIgMTE1aDIzOHYzOUg4MTJ6TTgwOCAxODRoMjQydjMwSDgwOHpNOTE3IDQ4aDEzM3YzN0g5MTd6Ii8+PC9nPjwvc3ZnPg=="</span>></span>
        <span class="hljs-tag"></<span class="hljs-name">section</span>></span>
    <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="hljs-tag"></<span class="hljs-name">template</span>></span>

<span class="hljs-tag"><<span class="hljs-name">script</span>></span><span class="javascript">
<span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span> &#123;
    <span class="hljs-attr">name</span>: <span class="hljs-string">'skeleton'</span>
&#125;;
</span><span class="hljs-tag"></<span class="hljs-name">script</span>></span>

<span class="hljs-tag"><<span class="hljs-name">style</span> <span class="hljs-attr">scoped</span>></span><span class="css">
<span class="hljs-selector-class">.skeleton-header</span> &#123;
    <span class="hljs-attribute">height</span>: <span class="hljs-number">152px</span>;
    <span class="hljs-attribute">background</span>: grey;
    <span class="hljs-attribute">margin-top</span>: <span class="hljs-number">60px</span>;
    <span class="hljs-attribute">width</span>: <span class="hljs-number">152px</span>;
    <span class="hljs-attribute">margin</span>: <span class="hljs-number">60px</span> auto;
&#125;
<span class="hljs-selector-class">.skeleton-block</span> &#123;
    <span class="hljs-attribute">display</span>: flex;
    <span class="hljs-attribute">flex-direction</span>: column;
    <span class="hljs-attribute">padding-top</span>: <span class="hljs-number">8px</span>;
&#125;
</span><span class="hljs-tag"></<span class="hljs-name">style</span>></span>
</span><span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-4">3、创建一个用于服务端渲染的 webpack 配置对象，将刚创建的入口文件指定为 entry 依赖入口：build/webpack.skeleton.conf.js</h3>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">const</span> path = <span class="hljs-built_in">require</span>(<span class="hljs-string">'path'</span>)
<span class="hljs-keyword">const</span> merge = <span class="hljs-built_in">require</span>(<span class="hljs-string">'webpack-merge'</span>)
<span class="hljs-keyword">const</span> baseWebpackConfig = <span class="hljs-built_in">require</span>(<span class="hljs-string">'./webpack.base.conf'</span>)
<span class="hljs-keyword">const</span> nodeExternals = <span class="hljs-built_in">require</span>(<span class="hljs-string">'webpack-node-externals'</span>)

<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">resolve</span>(<span class="hljs-params">dir</span>) </span>&#123;
  <span class="hljs-keyword">return</span> path.join(__dirname, dir)
&#125;

<span class="hljs-built_in">module</span>.exports = merge(baseWebpackConfig, &#123;
  <span class="hljs-attr">target</span>: <span class="hljs-string">'node'</span>, <span class="hljs-comment">// 区别默认的‘web’</span>
  <span class="hljs-attr">devtool</span>: <span class="hljs-literal">false</span>,
  <span class="hljs-attr">entry</span>: &#123;
    <span class="hljs-attr">app</span>: resolve(<span class="hljs-string">'../src/components/Skeleton/entry-skeleton.js'</span>)  <span class="hljs-comment">// 多页传入对象</span>
  &#125;,
  <span class="hljs-attr">output</span>: <span class="hljs-built_in">Object</span>.assign(&#123;&#125;, baseWebpackConfig.output, &#123;
    <span class="hljs-attr">libraryTarget</span>: <span class="hljs-string">'commonjs2'</span>
  &#125;),
  <span class="hljs-attr">externals</span>: nodeExternals(&#123;
    <span class="hljs-attr">whitelist</span>: <span class="hljs-regexp">/\.css$/</span>
  &#125;),
  <span class="hljs-attr">plugins</span>: []
&#125;)
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-5">4、创建一个用于服务端渲染的 webpack 配置对象，将刚创建的入口文件指定为 entry 依赖入口：build/webpack.dev.conf.js和build/webpack.prod.conf.js</h3>
<pre><code class="hljs language-js copyable" lang="js">... ...
<span class="hljs-keyword">const</span> SkeletonWebpackPlugin = <span class="hljs-built_in">require</span>(<span class="hljs-string">'vue-skeleton-webpack-plugin'</span>)

<span class="hljs-built_in">module</span>.exports = merge(baseWebpackConfig, &#123;
    ... ...
    <span class="hljs-attr">plugins</span>: [
       ... ....
        <span class="hljs-comment">// inject skeleton content(DOM & CSS) into HTML</span>
        <span class="hljs-keyword">new</span> SkeletonWebpackPlugin(&#123;
            <span class="hljs-attr">webpackConfig</span>: <span class="hljs-built_in">require</span>(<span class="hljs-string">'./webpack.skeleton.conf'</span>),
            <span class="hljs-attr">quiet</span>: <span class="hljs-literal">true</span>
        &#125;),
    ]
&#125;)
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-6">5、安装后运行，npm run dev 运行，报错：</h3>
<pre><code class="hljs language-js copyable" lang="js"> <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> <span class="hljs-built_in">Error</span>(
  ^

<span class="hljs-built_in">Error</span>:

Vue packages version mismatch:

- vue@<span class="hljs-number">2.5</span><span class="hljs-number">.16</span>
- vue-server-renderer@<span class="hljs-number">2.6</span><span class="hljs-number">.12</span>

This may cause things to work incorrectly. Make sure to use the same version <span class="hljs-keyword">for</span> both.
<span class="copy-code-btn">复制代码</span></code></pre>
<p>原因：<code>vue</code>的版本与<code>vue-server-renderer</code>版本不一致导致的，因此需要vue与vue-server-renderer安装同一个版本。</p>
<blockquote>
<p>注：</p>
<p>原项目的vue版本是<a href="https://link.juejin.cn/?target=mailto%3Avue%402.3.3" target="_blank" title="mailto:vue@2.3.3" ref="nofollow noopener noreferrer">vue@2.3.3</a>，但是为了统一，尝试了<a href="https://link.juejin.cn/?target=mailto%3Avue-server-renderer%402.3.3" target="_blank" title="mailto:vue-server-renderer@2.3.3" ref="nofollow noopener noreferrer">vue-server-renderer@2.3.3</a>及<a href="https://link.juejin.cn/?target=mailto%3Avue-server-renderer%402.3.4" target="_blank" title="mailto:vue-server-renderer@2.3.4" ref="nofollow noopener noreferrer">vue-server-renderer@2.3.4</a><a href="https://link.juejin.cn/?target=mailto%3A%2Bvue%402.3.4" target="_blank" title="mailto:+vue@2.3.4" ref="nofollow noopener noreferrer">+vue@2.3.4</a>，无效，升级为<a href="https://link.juejin.cn/?target=mailto%3Avue%402.5.16" target="_blank" title="mailto:vue@2.5.16" ref="nofollow noopener noreferrer">vue@2.5.16</a><a href="https://link.juejin.cn/?target=mailto%3A%2Bvue-server-renderer%402.5.16" target="_blank" title="mailto:+vue-server-renderer@2.5.16" ref="nofollow noopener noreferrer">+vue-server-renderer@2.5.16</a></p>
</blockquote>
<pre><code class="hljs language-js copyable" lang="js">npm i vue@<span class="hljs-number">2.5</span><span class="hljs-number">.16</span> vue-server-renderer@<span class="hljs-number">2.5</span><span class="hljs-number">.16</span> -D
<span class="copy-code-btn">复制代码</span></code></pre>
<p>再次<code>npm run dev </code>即ok</p>
<h2 data-id="heading-7">（二）多页面骨架屏具体操作</h2>
<h3 data-id="heading-8">1、再新建<code>Skeleton2.vue</code>文件：</h3>
<p><strong>/src/components/Skeleton2.vue</strong></p>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/85f6e0ebd7d44ea8a0be5a72ac73a661~tplv-k3u1fbpfcp-watermark.image" alt="08.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p><strong>注解：</strong></p>
<blockquote>
<p>要是多个页面不同的，则需要编写对应页面的不同的骨架屏（css样式编写的页面），这样才能一一匹配，
因此需要写对应页面骨架屏的样式或者是ui的设计（页面采用图片或base64）；</p>
<p>总结一句话：这样交互虽好，但是工作量是比较大的，要是页面后期改动较大的话，则整个骨架屏都需要改动。</p>
</blockquote>
<pre><code class="hljs language-js copyable" lang="js"><template>
    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"skeleton-wrapper"</span>></span>Skeleton For Home<span class="hljs-tag"></<span class="hljs-name">div</span>></span></span>
</template>

<span class="xml"><span class="hljs-tag"><<span class="hljs-name">script</span>></span><span class="javascript">

<span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span> &#123;
    <span class="hljs-attr">name</span>: <span class="hljs-string">'skeleton2'</span>
&#125;;
</span><span class="hljs-tag"></<span class="hljs-name">script</span>></span></span>

<span class="xml"><span class="hljs-tag"><<span class="hljs-name">style</span> <span class="hljs-attr">scoped</span>></span><span class="css">

<span class="hljs-selector-class">.skeleton-header</span> &#123;
    <span class="hljs-attribute">height</span>: <span class="hljs-number">152px</span>;
    <span class="hljs-attribute">background</span>: grey;
    <span class="hljs-attribute">margin-top</span>: <span class="hljs-number">60px</span>;
    <span class="hljs-attribute">width</span>: <span class="hljs-number">152px</span>;
    <span class="hljs-attribute">margin</span>: <span class="hljs-number">60px</span> auto;
&#125;

<span class="hljs-selector-class">.skeleton-block</span> &#123;
    <span class="hljs-attribute">display</span>: flex;
    <span class="hljs-attribute">flex-direction</span>: column;
    <span class="hljs-attribute">padding-top</span>: <span class="hljs-number">8px</span>;
&#125;
</span><span class="hljs-tag"></<span class="hljs-name">style</span>></span></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-9">2、修改入口文件<code>entry-skeleton.js</code></h3>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">import</span> Vue <span class="hljs-keyword">from</span> <span class="hljs-string">'vue'</span>;
<span class="hljs-keyword">import</span> Skeleton <span class="hljs-keyword">from</span> <span class="hljs-string">'./Skeleton'</span>;
<span class="hljs-keyword">import</span> Skeleton2 <span class="hljs-keyword">from</span> <span class="hljs-string">'./Skeleton2'</span>; <span class="hljs-comment">// 新增</span>

<span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span> <span class="hljs-keyword">new</span> Vue(&#123;
    <span class="hljs-attr">components</span>: &#123;
        Skeleton,
        Skeleton2 <span class="hljs-comment">// 新增</span>
    &#125;,
    <span class="hljs-comment">// 注意：id="skeleton"或id="skeleton2"中的id是关键，是控制对应是否显示的关键</span>
    <span class="hljs-attr">template</span>: <span class="hljs-string">`
                <div>
                    <Skeleton
                     id="skeleton" style="display:none"/>
                    <Skeleton2 id="skeleton2" style="display:none"/>
                </div>
            `</span>
&#125;);
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-10">3、修改<code>build/webpack.dev.conf.js</code>和<code>build/webpack.prod.conf.js</code></h3>
<blockquote>
<p>注解：build/webpack.prod.conf.js一定要配置，因为打包上线的时候需要注入的。</p>
</blockquote>
<pre><code class="hljs language-js copyable" lang="js">... ...
<span class="hljs-keyword">const</span> SkeletonWebpackPlugin = <span class="hljs-built_in">require</span>(<span class="hljs-string">'vue-skeleton-webpack-plugin'</span>)
... ...
    <span class="hljs-attr">plugins</span>: [
        <span class="hljs-comment">// inject skeleton content(DOM & CSS) into HTML</span>
        <span class="hljs-keyword">new</span> SkeletonWebpackPlugin(&#123;
            <span class="hljs-attr">webpackConfig</span>: <span class="hljs-built_in">require</span>(<span class="hljs-string">'./webpack.skeleton.conf'</span>),
            <span class="hljs-attr">quiet</span>: <span class="hljs-literal">true</span>,
            <span class="hljs-attr">minimize</span>: <span class="hljs-literal">true</span>, <span class="hljs-comment">// 选填 SPA 下是否需要压缩注入 HTML 的 JS 代码</span>
            <span class="hljs-attr">router</span>: &#123;
                <span class="hljs-attr">mode</span>: <span class="hljs-string">'hash'</span>,
                <span class="hljs-attr">routes</span>: [
                    &#123; <span class="hljs-comment">// 插入骨架屏路由1</span>
                        <span class="hljs-attr">path</span>: <span class="hljs-regexp">/\/comboHelper/</span>, <span class="hljs-comment">// 路由是采用正则,哪个页面需要加入骨架屏则写对应页面的页面路由</span>
                        skeletonId: <span class="hljs-string">'skeleton'</span> <span class="hljs-comment">// 此处就是对应是否显示入口文件entry-skeleton.js中template那个id的html显示的</span>
                    &#125;,
                    &#123; <span class="hljs-comment">// 插入骨架屏路由1</span>
                        <span class="hljs-attr">path</span>: <span class="hljs-regexp">/\/commercialActivity\?/</span>,
                        skeletonId: <span class="hljs-string">'skeleton'</span>
                    &#125;,
                    &#123;
                        <span class="hljs-attr">path</span>: <span class="hljs-string">'/'</span>,
                        <span class="hljs-attr">skeletonId</span>: <span class="hljs-string">'skeleton2'</span>,
                    &#125;,
                ]
            &#125;
        &#125;),
    ]
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-11"><code>注意事项：</code></h4>
<p><strong><a href="https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Flavas-project%2Fvue-skeleton-webpack-plugin%23%25E4%25BD%25BF%25E7%2594%25A8%25E5%25A4%259A%25E4%25B8%25AA-skeleton-%25E6%2597%25B6%25E6%2597%25A0%25E6%25B3%2595%25E5%258C%25B9%25E9%2585%258D%25E5%25BD%2593%25E5%2589%258D%25E8%25B7%25AF%25E7%2594%25B1%25E8%25B7%25AF%25E5%25BE%2584" target="_blank" rel="nofollow noopener noreferrer" title="https://github.com/lavas-project/vue-skeleton-webpack-plugin#%E4%BD%BF%E7%94%A8%E5%A4%9A%E4%B8%AA-skeleton-%E6%97%B6%E6%97%A0%E6%B3%95%E5%8C%B9%E9%85%8D%E5%BD%93%E5%89%8D%E8%B7%AF%E7%94%B1%E8%B7%AF%E5%BE%84" ref="nofollow noopener noreferrer">使用多个 Skeleton 时无法匹配当前路由路径的？</a></strong></p>
<p>用于匹配每个 <code>Skeleton</code> 的 <code>path</code>选项可以填写字符串或者正则。如果想匹配 <code>/page1?key=value</code> 这样的路由路径，可以直接写正则 <code>path: /^/page1/</code>。</p>
<p>实际中本项目若是动态参数的路由，路由写成：</p>
<pre><code class="hljs language-js copyable" lang="js">path: <span class="hljs-string">'/play/:type/:id'</span>,    <span class="hljs-comment">//如路由为动态参数，必须跟router的配置一样</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>无效，改为<strong>正则的即ok</strong></p>
<pre><code class="hljs language-js copyable" lang="js">path: <span class="hljs-regexp">/\/commercialActivity\?/</span>,
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-12">总结</h2>
<ul>
<li>
<p>手写HTML、CSS的方式为目标页定制骨架屏</p>
</li>
<li>
<p>骨架屏可以理解为是当数据还未加载进来前，页面的一个空白版本，一个简单的关键渲染路径</p>
</li>
<li>
<p>主要思路就是使用<code> vue-server-renderer</code> 这个本来用于服务端渲染的插件，用来把我们写的.vue文件处理为HTML，插入到页面模板的挂载点中，完成骨架屏的注入。缺点：这种方式不甚文明，如果页面样式改变了，还得改一遍骨架屏，增加了维护成本。</p>
</li>
<li>
<p>使用图片作为骨架屏：简单暴力，让UI同学多花点功夫；小米商城的移动端页面采用的就是这个方法，它是使用了一个Base64的图片来作为骨架屏。</p>
</li>
<li>
<p>交互问题：当dom节点数据加载回来后，骨架屏与真正页面会有一个空白屏的过渡，当网速很慢的情况下，这个白屏现象就会很明显！（<code>首屏骨架->然后挂载vue白屏直->页面</code>）</p>
</li>
</ul></div>  
</div>
            
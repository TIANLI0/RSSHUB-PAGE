
---
title: '_React源码系列3_React组件初渲染原理'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4711d8925e4d4c82975c96899fd5614f~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Tue, 13 Jul 2021 05:23:20 GMT
thumbnail: 'https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4711d8925e4d4c82975c96899fd5614f~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h2 data-id="heading-0">一、组件</h2>
<blockquote>
<p>组件可以将UI切分成一些独立的、可复用的部件，这样我们就只需要专注于每个单独的部件开发。组件的概念类似于 <code>JS函数</code> ，它接受任意的入参（即 “props”），并返回用于描述页面展示内容的 React 元素。</p>
</blockquote>
<p><img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4711d8925e4d4c82975c96899fd5614f~tplv-k3u1fbpfcp-watermark.image" alt="components.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h2 data-id="heading-1">二、React组件</h2>
<h3 data-id="heading-2">2.1 函数组件</h3>
<blockquote>
<p>函数式组件就是通过编写 <code>JavaScript</code> 函数来定义的组件，通过接受一个<code>props对象</code> 并返回一个<code>React元素</code>来实现组件。</p>
</blockquote>
<pre><code class="hljs language-jsx copyable" lang="jsx"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">Welcome</span>(<span class="hljs-params">props</span>)</span>&#123;
    <span class="hljs-keyword">return</span> <span class="xml"><span class="hljs-tag"><<span class="hljs-name">h1</span>></span>Hello,&#123;props.name&#125;<span class="hljs-tag"></<span class="hljs-name">h1</span>></span></span>
&#125;

<span class="hljs-comment">// <Welcome name='Tom'></Welcome></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-3">2.2 类组件</h3>
<blockquote>
<p>类组件是通过 <code>ES6</code> 的 <code>class</code> 来定义的组件，类组件相较于函数组件有一些额外的特性，这个我们会在下节组件更新中详细介绍。</p>
</blockquote>
<pre><code class="hljs language-jsx copyable" lang="jsx"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Welcome</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">React</span>.<span class="hljs-title">Component</span> </span>&#123;
    <span class="hljs-function"><span class="hljs-title">render</span>(<span class="hljs-params"></span>)</span>&#123;
        <span class="hljs-keyword">return</span> <span class="xml"><span class="hljs-tag"><<span class="hljs-name">h1</span>></span>Hello,&#123;this.props.name&#125;<span class="hljs-tag"></<span class="hljs-name">h1</span>></span></span>
    &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p>这两个组件初渲染的结果是等价的</p>
</blockquote>
<h3 data-id="heading-4">三、组件的初渲染原理</h3>
<blockquote>
<p>React中组件分为两类，一类是内置的原生组件，像div、p、span这些原生组件的<code>type</code> 是字符串，第二类是自定义组件，他的 <code>type</code> 类型是一个函数</p>
</blockquote>
<h3 data-id="heading-5">3.1 函数组件</h3>
<blockquote>
<p>函数组件编译后结果</p>
<ul>
<li><code>$$typeof: Symbol(react.element)</code> 代表这个 <code>JSX</code> 是个组件</li>
<li>传入的 <code>name</code> 会被挂在 <code>props</code> 上</li>
<li><code>type</code> 属性的值是一个函数</li>
</ul>
</blockquote>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e2f7d1dec0e5442e8a8eabd3d2dce8e7~tplv-k3u1fbpfcp-watermark.image" alt="函数组件编译.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h3 data-id="heading-6">3.2 类组件</h3>
<blockquote>
<ul>
<li>类组件需要注意的是，<code>type</code>的原型上 <code>isReactComponent</code> 属性使用来标识该元素是否为类组件</li>
</ul>
</blockquote>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/82b31668526a4559afe3903e52c4fab4~tplv-k3u1fbpfcp-watermark.image" alt="类组件编译.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h3 data-id="heading-7">3.3 组件初渲染原理</h3>
<p><img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/851fa947b2074f4abfe94d96d1130bec~tplv-k3u1fbpfcp-watermark.image" alt="组件初渲染.png" loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">// 接着上一篇文章，修改createDOM代码</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">createDOM</span>(<span class="hljs-params">vdom</span>)</span>&#123;
    <span class="hljs-keyword">let</span> &#123;type,props&#125; = vdom;
    <span class="hljs-keyword">let</span> dom;
    <span class="hljs-keyword">if</span>(type === REACT_TEXT)&#123;
        dom = <span class="hljs-built_in">document</span>.createTextNode(props.content);
    &#125;<span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span>(<span class="hljs-keyword">typeof</span> type === <span class="hljs-string">'function'</span>)&#123; <span class="hljs-comment">// 组件</span>
        <span class="hljs-keyword">if</span>(type.isReactComponent)&#123;  <span class="hljs-comment">// 类组件</span>
            <span class="hljs-keyword">return</span> mountClassComponent(vdom);
        &#125;<span class="hljs-keyword">else</span>&#123; <span class="hljs-comment">// 函数组件</span>
            <span class="hljs-keyword">return</span> mountFunctionComponent(vdom);
        &#125;
    &#125;<span class="hljs-keyword">else</span>&#123;
        dom = <span class="hljs-built_in">document</span>.createElement(props.content);
    &#125;
    
    <span class="hljs-keyword">if</span>(props)&#123;
        updateProps(dom,&#123;&#125;,props);
        <span class="hljs-keyword">if</span>(<span class="hljs-keyword">typeof</span> props.children == <span class="hljs-string">'object'</span> && props.children.type)&#123;
           render(props.children,dom)
        &#125;<span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span>(<span class="hljs-built_in">Array</span>.isArray(props.children))&#123;
            reconcileChildren(props.children,dom)
        &#125;
    &#125;
    vdom.dom = dom
    <span class="hljs-keyword">return</span> dom
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-8">3.4 函数组件的挂载</h3>
<blockquote>
<p>函数组件的挂载原理就是将 <code>type</code> 执行得到的 <code>vdom</code> 传入到 <code>createDOM</code> 中生成真实DOM</p>
</blockquote>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">mountFunctionComponent</span>(<span class="hljs-params">vdom</span>)</span>&#123;
    <span class="hljs-keyword">const</span> [type,props] = vdom;
    <span class="hljs-keyword">const</span> renderVdom = type(props);
    <span class="hljs-keyword">return</span> createDOM(renderVdom);
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-9">3.5 类组件的挂载</h3>
<blockquote>
<p>类组件的父类 <code>Component</code> 的原型上有一个属性 <code>isReactComponent</code> 值是一个空对象</p>
</blockquote>
<h4 data-id="heading-10">3.5.1 <code>Component</code>类</h4>
<blockquote>
<p><code>Component.js</code>  实现简易 <code>Component</code> 类</p>
</blockquote>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">export</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Component</span> </span>&#123;
    <span class="hljs-keyword">static</span> isReactComponent = &#123;&#125;<span class="hljs-comment">// 用于标识类组件</span>
    <span class="hljs-function"><span class="hljs-title">constructor</span>(<span class="hljs-params">props</span>)</span>&#123;
        <span class="hljs-built_in">this</span>.props = props
    &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-11">3.5.2 挂载类组件</h4>
<blockquote>
<p>类组件的挂载原理，先通过 <code> new type</code> 得到类的实例，在调用实例的 <code>render</code> 方法生成vdom，最后将得到的 <code>vdom</code> 传入到 <code>createDOM</code> 中生成真实DOM</p>
</blockquote>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">mountClassComponent</span>(<span class="hljs-params">vdom</span>)</span>&#123;
    <span class="hljs-keyword">const</span> [type,props] = vdom;
    <span class="hljs-keyword">const</span> classInstance = <span class="hljs-keyword">new</span> type(props);
    <span class="hljs-keyword">const</span> renderVdom = classInstance.render(renderVdom);
    <span class="hljs-keyword">return</span> renderVdom
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li><a href="https://juejin.cn/collection/6973197064960229384" target="_blank" title="https://juejin.cn/collection/6973197064960229384">React源码系列</a></li>
</ul></div>  
</div>
            
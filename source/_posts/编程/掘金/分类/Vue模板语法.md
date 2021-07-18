
---
title: 'Vue模板语法'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4e558a06bb194f6a8eb21eef58d3bcf2~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 20:32:21 GMT
thumbnail: 'https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4e558a06bb194f6a8eb21eef58d3bcf2~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h1 data-id="heading-0">1. 模板语法概述</h1>
<h2 data-id="heading-1">1.1. 如何理解前端渲染？</h2>
<p>把数据填充到HTML标签中</p>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4e558a06bb194f6a8eb21eef58d3bcf2~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h2 data-id="heading-2">1.2. 前端渲染方式</h2>
<ul>
<li>原生js拼接字符串</li>
<li>使用前端模板引擎</li>
<li>使用vue特有的模板语法</li>
<li>文档碎片 document.createDocumentFragment</li>
<li>利用es6 `` 反引号拼接字符串</li>
</ul>
<h3 data-id="heading-3">1.2.1. 原生js拼接字符串</h3>
<p>基本上就是将数据以字符串的方式拼接到HTML标签中，前端代码风格大体上如下。</p>
<p><strong>缺点</strong>：不同开发人员的代码风格差别很大，随着业务的复杂，后期的维护变得逐渐困难起来。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> d = data.weather;
<span class="hljs-keyword">var</span> info = <span class="hljs-built_in">document</span>.getElementById(<span class="hljs-string">'info'</span>);
info.innerHTML = <span class="hljs-string">''</span>;
<span class="hljs-keyword">for</span>(<span class="hljs-keyword">var</span> i=<span class="hljs-number">0</span>;i<d.length;i++)&#123;
    <span class="hljs-keyword">var</span> date = d[i].date;
    <span class="hljs-keyword">var</span> day = d[i].info.day;
    <span class="hljs-keyword">var</span> night = d[i].info.night;
    <span class="hljs-keyword">var</span> tag = <span class="hljs-string">''</span>;
    tag += <span class="hljs-string">'<span>日期：'</span>+date+<span class="hljs-string">'</sapn><ul>'</span>;
    tag += <span class="hljs-string">'<li>白天天气：'</span>+day[<span class="hljs-number">1</span>]+<span class="hljs-string">'</li>'</span>
    tag += <span class="hljs-string">'<li>白天温度：'</span>+day[<span class="hljs-number">2</span>]+<span class="hljs-string">'</li>'</span>
    tag += <span class="hljs-string">'<li>白天风向：'</span>+day[<span class="hljs-number">3</span>]+<span class="hljs-string">'</li>'</span>
    tag += <span class="hljs-string">'<li>白天风速：'</span>+day[<span class="hljs-number">4</span>]+<span class="hljs-string">'</li>'</span>
    tag += <span class="hljs-string">'</ul>'</span>;
    <span class="hljs-keyword">var</span> div = <span class="hljs-built_in">document</span>.createElement(<span class="hljs-string">'div'</span>); div.innerHTML = tag;
    info.appendChild(div);
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-4">1.2.2. 使用前端模板引擎</h3>
<p>下面代码是基于模板引擎art-template的一段代码，与拼接字符串相比，代码明显规范了很多，它拥有自己的一套模板语法规则。</p>
<p><strong>优点</strong>：大家都遵循同样的规则写代码，代码可读性明显提高了，方便后期的维护。
<strong>缺点</strong>：没有专门提供事件机制。</p>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e7bbbdd42fb942adad05d12ef83928b2~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h3 data-id="heading-5">1.2.3. 模板语法概览</h3>
<ul>
<li>差值表达式</li>
<li>指令</li>
<li>事件绑定</li>
<li>属性绑定</li>
<li>样式绑定</li>
<li>分支循环结构</li>
</ul>
<h1 data-id="heading-6">2. 指令</h1>
<p>官网：<a href="https://link.juejin.cn/?target=https%3A%2F%2Fcn.vuejs.org%2Fv2%2Fapi%2F" target="_blank" rel="nofollow noopener noreferrer" title="https://cn.vuejs.org/v2/api/" ref="nofollow noopener noreferrer">cn.vuejs.org/v2/api/</a></p>
<h2 data-id="heading-7">2.1. 什么是指令？</h2>
<ul>
<li>指令的本质就是自定义属性</li>
<li>指令的格式：以v-开始（比如：v-cloak）</li>
</ul>
<h2 data-id="heading-8">2.2. v-cloak指令用法</h2>
<h3 data-id="heading-9">2.2.1. 为什么会有闪烁问题？</h3>
<p>代码加载的时候先加载HTML 把插值语法当做HTML内容加载到页面上 当加载完js后才把插值语法替换掉 所以我们会看到闪烁问题</p>
<h3 data-id="heading-10">2.2.2. 如何解决插值语法的闪烁问题？</h3>
<p>v-cloak</p>
<h3 data-id="heading-11">2.2.3. 解决该问题的原理</h3>
<p>先隐藏，替换好值之后再显示最终的值</p>
<pre><code class="hljs language-js copyable" lang="js"><style type=<span class="hljs-string">"text/css"</span>>
  <span class="hljs-comment">/* 
    1、通过属性选择器 选择到 带有属性 v-cloak的标签  让他隐藏
 */</span>
  [v-cloak]&#123;
    <span class="hljs-comment">/* 元素隐藏    */</span>
    <span class="hljs-attr">display</span>: none;
  &#125;
  </style>
<span class="xml"><span class="hljs-tag"><<span class="hljs-name">body</span>></span>
  <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">id</span>=<span class="hljs-string">"app"</span>></span>
    <span class="hljs-comment"><!-- 2、 让带有插值 语法的   添加 v-cloak 属性 
         在 数据渲染完场之后，v-cloak 属性会被自动去除，
         v-cloak一旦移除也就是没有这个属性了  属性选择器就选择不到该标签
 也就是对应的标签会变为可见
    --></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span>  <span class="hljs-attr">v-cloak</span>  ></span>&#123;&#123;msg&#125;&#125;<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
  <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
  <span class="hljs-tag"><<span class="hljs-name">script</span> <span class="hljs-attr">type</span>=<span class="hljs-string">"text/javascript"</span> <span class="hljs-attr">src</span>=<span class="hljs-string">"js/vue.js"</span>></span><span class="hljs-tag"></<span class="hljs-name">script</span>></span>
  <span class="hljs-tag"><<span class="hljs-name">script</span> <span class="hljs-attr">type</span>=<span class="hljs-string">"text/javascript"</span>></span><span class="javascript">
    <span class="hljs-keyword">var</span> vm = <span class="hljs-keyword">new</span> Vue(&#123;
      <span class="hljs-comment">//  el   指定元素 id 是 app 的元素  </span>
      <span class="hljs-attr">el</span>: <span class="hljs-string">'#app'</span>,
      <span class="hljs-comment">//  data  里面存储的是数据</span>
      <span class="hljs-attr">data</span>: &#123;
        <span class="hljs-attr">msg</span>: <span class="hljs-string">'Hello Vue'</span>
      &#125;
    &#125;);
</span><span class="hljs-tag"></<span class="hljs-name">script</span>></span>
<span class="hljs-tag"></<span class="hljs-name">body</span>></span></span>
</html>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-12">2.3. 数据绑定指令</h2>
<h3 data-id="heading-13">2.3.1. v-text</h3>
<ul>
<li>v-text填充纯文本</li>
<li>v-text指令用于将数据填充到标签中，作用于插值表达式类似，但是没有闪动问题</li>
<li>如果数据中有HTML标签会将html标签一并输出</li>
<li>注意：此处为单向绑定，数据对象上的值改变，插值会发生变化；但是当插值发生变化并不会影响数据对象的值</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"><div id=<span class="hljs-string">"app"</span>>
    <!--  
注意:在指令中不要写插值语法  直接写对应的变量名称 
        在 v-text 中 赋值的时候不要在写 插值语法
一般属性中不加 &#123;&#123;&#125;&#125;  直接写 对应 的数据名 
-->
    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">p</span> <span class="hljs-attr">v-text</span>=<span class="hljs-string">"msg"</span>></span><span class="hljs-tag"></<span class="hljs-name">p</span>></span></span>
    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">p</span>></span>
        <span class="hljs-comment"><!-- Vue  中只有在标签的 内容中 才用插值语法 --></span>
        &#123;&#123;msg&#125;&#125;
    <span class="hljs-tag"></<span class="hljs-name">p</span>></span></span>
</div>

<span class="xml"><span class="hljs-tag"><<span class="hljs-name">script</span>></span><span class="javascript">
    <span class="hljs-keyword">new</span> Vue(&#123;
        <span class="hljs-attr">el</span>: <span class="hljs-string">'#app'</span>,
        <span class="hljs-attr">data</span>: &#123;
            <span class="hljs-attr">msg</span>: <span class="hljs-string">'Hello Vue.js'</span>
        &#125;
    &#125;);

</span><span class="hljs-tag"></<span class="hljs-name">script</span>></span></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-14">2.3.2. v-html</h3>
<ul>
<li>用法和v-text 相似  但是他可以将HTML片段填充到标签中</li>
<li>可能有安全问题, 一般只在可信任内容上使用 <code>v-html</code>，<strong>永不</strong>用在用户提交的内容上</li>
<li>它与v-text区别在于v-text输出的是纯文本，浏览器不会对其再进行html解析，但v-html会将其当html标签解析后输出。</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"><div id=<span class="hljs-string">"app"</span>>
　　<span class="xml"><span class="hljs-tag"><<span class="hljs-name">p</span> <span class="hljs-attr">v-html</span>=<span class="hljs-string">"html"</span>></span><span class="hljs-tag"></<span class="hljs-name">p</span>></span></span> <!-- 输出：html标签在渲染的时候被解析 -->
    
    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">p</span>></span>&#123;&#123;message&#125;&#125;<span class="hljs-tag"></<span class="hljs-name">p</span>></span></span> <!-- 输出：<span>通过双括号绑定</span> -->
    
　　<span class="xml"><span class="hljs-tag"><<span class="hljs-name">p</span> <span class="hljs-attr">v-text</span>=<span class="hljs-string">"text"</span>></span><span class="hljs-tag"></<span class="hljs-name">p</span>></span></span> <!-- 输出：<span>html标签在渲染的时候被源码输出</span> -->
</div>
<span class="xml"><span class="hljs-tag"><<span class="hljs-name">script</span>></span><span class="javascript">
　　<span class="hljs-keyword">let</span> app = <span class="hljs-keyword">new</span> Vue(&#123;
　　<span class="hljs-attr">el</span>: <span class="hljs-string">"#app"</span>,
　　<span class="hljs-attr">data</span>: &#123;
　　　　<span class="hljs-attr">message</span>: <span class="hljs-string">"<span>通过双括号绑定</span>"</span>,
　　　　<span class="hljs-attr">html</span>: <span class="hljs-string">"<span>html标签在渲染的时候被解析</span>"</span>,
　　　　<span class="hljs-attr">text</span>: <span class="hljs-string">"<span>html标签在渲染的时候被源码输出</span>"</span>,
　　&#125;
 &#125;);
</span><span class="hljs-tag"></<span class="hljs-name">script</span>></span></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-15">2.3.3. v-pre</h3>
<ul>
<li>显示原始信息跳过编译过程</li>
<li>跳过这个元素和它的子元素的编译过程。</li>
<li><strong>一些静态的内容不需要编译加这个指令可以加快渲染</strong></li>
</ul>
<pre><code class="hljs language-js copyable" lang="js">    <span v-pre>&#123;&#123; <span class="hljs-built_in">this</span> will not be compiled &#125;&#125;</span>    
<!--  显示的是&#123;&#123; <span class="hljs-built_in">this</span> will not be compiled &#125;&#125;  -->
<span class="xml"><span class="hljs-tag"><<span class="hljs-name">span</span> <span class="hljs-attr">v-pre</span>></span>&#123;&#123;msg&#125;&#125;<span class="hljs-tag"></<span class="hljs-name">span</span>></span></span>  
     <!--   即使data里面定义了msg这里仍然是显示的&#123;&#123;msg&#125;&#125;  -->
<span class="xml"><span class="hljs-tag"><<span class="hljs-name">script</span>></span><span class="javascript">
    <span class="hljs-keyword">new</span> Vue(&#123;
        <span class="hljs-attr">el</span>: <span class="hljs-string">'#app'</span>,
        <span class="hljs-attr">data</span>: &#123;
            <span class="hljs-attr">msg</span>: <span class="hljs-string">'Hello Vue.js'</span>
        &#125;
    &#125;);

</span><span class="hljs-tag"></<span class="hljs-name">script</span>></span></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-16">2.4. 数据响应式</h2>
<h3 data-id="heading-17">2.4.1. 如何理解响应式</h3>
<ul>
<li>① html5中的响应式（屏幕尺寸的变化导致样式的变化）</li>
<li>② 数据的响应式（数据的变化导致页面内容的变化）</li>
</ul>
<h3 data-id="heading-18">2.4.2. 什么是数据绑定</h3>
<p>数据绑定：将数据填充到标签中</p>
<h3 data-id="heading-19">2.4.3. v-once</h3>
<ul>
<li>只编译一次</li>
<li>显示内容之后不再具有响应式功能</li>
<li>执行一次性的插值【当数据改变时，插值处的内容不会继续更新】</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js">  <!-- 即使data里面定义了msg 后期我们修改了 仍然显示的是第一次data里面存储的数据即 Hello Vue.js  -->
     <span class="xml"><span class="hljs-tag"><<span class="hljs-name">span</span> <span class="hljs-attr">v-once</span>></span>&#123;&#123; msg&#125;&#125;<span class="hljs-tag"></<span class="hljs-name">span</span>></span></span>    
<span class="xml"><span class="hljs-tag"><<span class="hljs-name">script</span>></span><span class="javascript">
    <span class="hljs-keyword">new</span> Vue(&#123;
        <span class="hljs-attr">el</span>: <span class="hljs-string">'#app'</span>,
        <span class="hljs-attr">data</span>: &#123;
            <span class="hljs-attr">msg</span>: <span class="hljs-string">'Hello Vue.js'</span>
        &#125;
    &#125;);
</span><span class="hljs-tag"></<span class="hljs-name">script</span>></span></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h1 data-id="heading-20">3. 双向数据绑定指令</h1>
<h2 data-id="heading-21">3.1. 什么是双向数据绑定？</h2>
<ul>
<li>当数据发生变化的时候，视图也就发生变化</li>
<li>当视图发生变化的时候，数据也会跟着同步变化</li>
</ul>
<h2 data-id="heading-22">3.2. 双向数据绑定分析</h2>
<h3 data-id="heading-23">3.2.1. v-model指令用法</h3>
<ul>
<li>model是一个指令，限制在<code><input></code>、<code><select></code>、<code><textarea></code>、components（组件） 中使用</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"> <div id=<span class="hljs-string">"app"</span>>
      <span class="xml"><span class="hljs-tag"><<span class="hljs-name">div</span>></span>&#123;&#123;msg&#125;&#125;<span class="hljs-tag"></<span class="hljs-name">div</span>></span></span>
      <span class="xml"><span class="hljs-tag"><<span class="hljs-name">div</span>></span>
          当输入框中内容改变的时候，  页面上的msg  会自动更新
        <span class="hljs-tag"><<span class="hljs-name">input</span> <span class="hljs-attr">type</span>=<span class="hljs-string">"text"</span> <span class="hljs-attr">v-model</span>=<span class="hljs-string">'msg'</span>></span>
      <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
  <span class="hljs-tag"></<span class="hljs-name">div</span>></span></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-24">3.3. MVVM设计思想</h2>
<p>MVC 是后端的分层开发概念； MVVM是前端视图层的概念，主要关注于 视图层分离，也就是说：MVVM把前端的视图层，分为了 三部分 Model, View , VM ViewModel</p>
<ul>
<li>① M(model)
<ul>
<li>数据层   Vue  中 数据层 都放在 data 里面</li>
</ul>
</li>
<li>② V(view视图)
<ul>
<li>Vue  中  view      即 我们的HTML页面</li>
</ul>
</li>
<li>③ VM(View-Model)控制器     将数据和视图层建立联系
<ul>
<li>vm 即  Vue 的实例  就是 vm</li>
</ul>
</li>
</ul>
<p><img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/52d263e5f579497a8af1e2821fb36909~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h1 data-id="heading-25">4. 事件绑定</h1>
<h2 data-id="heading-26">4.1. Vue如何处理事件？</h2>
<h3 data-id="heading-27">4.1.1. v-on指令用法</h3>
<p>用来绑定事件的</p>
<pre><code class="hljs language-js copyable" lang="js"><input type=‘button<span class="hljs-string">'  v-on:click='</span>num++<span class="hljs-string">'/>
</span><span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-28">4.1.1.1. v-on简写形式</h4>
<pre><code class="hljs language-js copyable" lang="js"><input type=‘button<span class="hljs-string">' @click='</span>num++<span class="hljs-string">'/>
</span><span class="copy-code-btn">复制代码</span></code></pre>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b03051d0926c41b8854c3b44acdcda26~tplv-k3u1fbpfcp-watermark.image" alt="@click.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h2 data-id="heading-29">4.2. 事件函数的调用方式</h2>
<h3 data-id="heading-30">4.2.1. 直接绑定函数名称</h3>
<pre><code class="hljs language-js copyable" lang="js"><button v-on:click=<span class="hljs-string">'say'</span>>Hello</button>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-31">4.2.2. 调用函数</h3>
<pre><code class="hljs language-js copyable" lang="js"><button v-on:click=<span class="hljs-string">'say()'</span>>Say hi</button>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-32">4.3. 事件函数参数传递</h2>
<h3 data-id="heading-33">4.3.1. 普通参数和事件对象</h3>
<h4 data-id="heading-34">4.3.1.1. vue中 事件对象 怎么使用</h4>
<ul>
<li>通过默认的事件参数</li>
<li>通过$event 使用</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"><button v-on:click=<span class="hljs-string">'say("hi",$event)'</span>>Say hi</button>
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-js copyable" lang="js"><body>
    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">id</span>=<span class="hljs-string">"app"</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">div</span>></span>&#123;&#123;num&#125;&#125;<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">div</span>></span>
            <span class="hljs-comment"><!-- 如果事件直接绑定函数名称，那么默认会传递事件对象作为事件函数的第一个参数 --></span>
            <span class="hljs-tag"><<span class="hljs-name">button</span> <span class="hljs-attr">v-on:click</span>=<span class="hljs-string">'handle1'</span>></span>点击1<span class="hljs-tag"></<span class="hljs-name">button</span>></span>
            <span class="hljs-comment"><!-- 2、如果事件绑定函数调用，那么事件对象必须作为最后一个参数显示传递，
                 并且事件对象的名称必须是$event 
            --></span>
            <span class="hljs-tag"><<span class="hljs-name">button</span> <span class="hljs-attr">v-on:click</span>=<span class="hljs-string">'handle2(123, 456, $event)'</span>></span>点击2<span class="hljs-tag"></<span class="hljs-name">button</span>></span>
        <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
    <span class="hljs-tag"></<span class="hljs-name">div</span>></span></span>
    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">script</span> <span class="hljs-attr">type</span>=<span class="hljs-string">"text/javascript"</span> <span class="hljs-attr">src</span>=<span class="hljs-string">"js/vue.js"</span>></span><span class="hljs-tag"></<span class="hljs-name">script</span>></span></span>
    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">script</span> <span class="hljs-attr">type</span>=<span class="hljs-string">"text/javascript"</span>></span><span class="javascript">
        <span class="hljs-keyword">var</span> vm = <span class="hljs-keyword">new</span> Vue(&#123;
            <span class="hljs-attr">el</span>: <span class="hljs-string">'#app'</span>,
            <span class="hljs-attr">data</span>: &#123;
                <span class="hljs-attr">num</span>: <span class="hljs-number">0</span>
            &#125;,
            <span class="hljs-attr">methods</span>: &#123;
                <span class="hljs-attr">handle1</span>: <span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params">event</span>) </span>&#123;
                    <span class="hljs-built_in">console</span>.log(event.target.innerHTML)
                &#125;,
                <span class="hljs-attr">handle2</span>: <span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params">p, p1, event</span>) </span>&#123;
                    <span class="hljs-built_in">console</span>.log(p, p1)
                    <span class="hljs-built_in">console</span>.log(event.target.innerHTML)
                    <span class="hljs-built_in">this</span>.num++;
                &#125;
            &#125;
        &#125;);
    </span><span class="hljs-tag"></<span class="hljs-name">script</span>></span></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-35">4.4. 事件修饰符</h2>
<ul>
<li>在事件处理程序中调用 <code>event.preventDefault()</code> 或 <code>event.stopPropagation()</code> 是非常常见的需求。</li>
<li>Vue 不推荐我们操作DOM    为了解决这个问题，Vue.js 为 <code>v-on</code> 提供了<strong>事件修饰符</strong></li>
<li>修饰符是由点开头的指令后缀来表示的</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"><!-- 阻止单击事件继续传播 -->
<span class="xml"><span class="hljs-tag"><<span class="hljs-name">a</span> <span class="hljs-attr">v-on:click.stop</span>=<span class="hljs-string">"doThis"</span>></span><span class="hljs-tag"></<span class="hljs-name">a</span>></span></span>

<!-- 提交事件不再重载页面 -->
<span class="xml"><span class="hljs-tag"><<span class="hljs-name">form</span> <span class="hljs-attr">v-on:submit.prevent</span>=<span class="hljs-string">"onSubmit"</span>></span><span class="hljs-tag"></<span class="hljs-name">form</span>></span></span>

<!-- 修饰符可以串联   即阻止冒泡也阻止默认事件 -->
<span class="xml"><span class="hljs-tag"><<span class="hljs-name">a</span> <span class="hljs-attr">v-on:click.stop.prevent</span>=<span class="hljs-string">"doThat"</span>></span><span class="hljs-tag"></<span class="hljs-name">a</span>></span></span>

<!-- 只当在 event.target 是当前元素自身时触发处理函数 -->
<!-- 即事件不是从内部元素触发的 -->
<span class="xml"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">v-on:click.self</span>=<span class="hljs-string">"doThat"</span>></span>...<span class="hljs-tag"></<span class="hljs-name">div</span>></span></span>

使用修饰符时，顺序很重要；相应的代码会以同样的顺序产生。因此，用 v-on:click.prevent.self 会阻止所有的点击，而 v-on:click.self.prevent 只会阻止对元素自身的点击。
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-36">4.4.1.<code>.stop</code>阻止冒泡</h3>
<pre><code class="hljs language-js copyable" lang="js"><a v-on:click.stop=<span class="hljs-string">"handle"</span>>跳转</a>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-37">4.4.2. <code>.prevent</code>阻止默认行为</h3>
<pre><code class="hljs language-js copyable" lang="js"><a v-on:click.prevent=<span class="hljs-string">"handle"</span>>跳转</a>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-38">4.5.按键修饰符</h2>
<p>在做项目中有时会用到键盘事件，在监听键盘事件时，我们经常需要检查详细的按键。Vue 允许为 <code>v-on</code> 在监听键盘事件时添加按键修饰符</p>
<pre><code class="hljs language-js copyable" lang="js"><!-- 只有在 <span class="hljs-string">`keyCode`</span> 是 <span class="hljs-number">13</span> 时调用 <span class="hljs-string">`vm.submit()`</span> -->
<input v-on:keyup.13="submit">

<!-- -当点击enter 时调用 `vm.submit()` -->
<input v-on:keyup.enter="submit">

<!--当点击enter或者space时  时调用 `vm.alertMe()`   -->
<input type="text" v-on:keyup.enter.space="alertMe" >

常用的按键修饰符
.enter =>    enter键
.tab => tab键
.delete (捕获“删除”和“退格”按键) =>  删除键
.esc => 取消键
.space =>  空格键
.up =>  上
.down =>  下
.left =>  左
.right =>  右

<script>
var vm = new Vue(&#123;
        el:"#app",
        methods: &#123;
              submit:function()&#123;&#125;,
              alertMe:function()&#123;&#125;,
        &#125;
    &#125;)

</script>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-39">4.5.1. <code>.enter</code>回车键</h3>
<pre><code class="hljs language-js copyable" lang="js"><input v-on:keyup.enter=<span class="hljs-string">'submit'</span>>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-40">4.5.2. <code>.esc</code>退出键</h3>
<pre><code class="hljs language-js copyable" lang="js"><input v-on:keyup.delete=<span class="hljs-string">'handle'</span>>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-41">4.6.自定义按键修饰符</h2>
<p>在Vue中可以通过<code>config.keyCodes</code>自定义按键修饰符别名</p>
<pre><code class="hljs language-js copyable" lang="js"><div id=<span class="hljs-string">"app"</span>>
    预先定义了keycode <span class="hljs-number">116</span>（即F5）的别名为f5，因此在文字输入框中按下F5，会触发prompt方法
    <input type=<span class="hljs-string">"text"</span> v-on:keydown.f5=<span class="hljs-string">"prompt()"</span>>
</div>

<span class="xml"><span class="hljs-tag"><<span class="hljs-name">script</span>></span><span class="javascript">

    Vue.config.keyCodes.f5 = <span class="hljs-number">116</span>;

    <span class="hljs-keyword">let</span> app = <span class="hljs-keyword">new</span> Vue(&#123;
        <span class="hljs-attr">el</span>: <span class="hljs-string">'#app'</span>,
        <span class="hljs-attr">methods</span>: &#123;
            <span class="hljs-attr">prompt</span>: <span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params"></span>) </span>&#123;
                alert(<span class="hljs-string">'我是 F5！'</span>);
            &#125;
        &#125;
    &#125;);
</span><span class="hljs-tag"></<span class="hljs-name">script</span>></span></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-42">4.6.1. 全局 config.keyCodes 对象</h3>
<pre><code class="hljs language-js copyable" lang="js">Vue.config.keyCodes.f1 = <span class="hljs-number">112</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>注意 112 对应键盘的keycode 值</li>
<li>f1可以自定义任何名字</li>
</ul>
<h1 data-id="heading-43">5. 属性绑定</h1>
<h2 data-id="heading-44">5.1. Vue如何动态处理属性？</h2>
<h3 data-id="heading-45">5.1.1. v-bind指令用法</h3>
<p>指令被用来响应地更新 HTML 属性</p>
<pre><code class="hljs language-js copyable" lang="js"><a v-bind:href=<span class="hljs-string">'url'</span>>跳转</a>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-46">5.1.2. 缩写形式</h3>
<pre><code class="hljs language-js copyable" lang="js"><a :href=<span class="hljs-string">'url'</span>>跳转</a>
<span class="copy-code-btn">复制代码</span></code></pre>
<ol start="2">
<li>v-model的低层实现原理分析</li>
</ol>
<pre><code class="hljs language-js copyable" lang="js"><input v-bind:value=<span class="hljs-string">"msg"</span> v-on:input=<span class="hljs-string">"msg=$event.target.value"</span>>
<span class="copy-code-btn">复制代码</span></code></pre>
<h1 data-id="heading-47">6. 样式绑定</h1>
<h2 data-id="heading-48">6.1. class样式处理</h2>
<p>注意：v-bind:class指令可以与普通的class特性共存</p>
<h3 data-id="heading-49">6.1.1. 对象语法</h3>
<ul>
<li>通过v-bind:class = &#123;   键： 值 &#125;</li>
<li>键 代表一个类名 如果这个值 为true  表示 显示这个类名</li>
<li>如果这个值 为false   表示 不显示这个类名</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-number">1</span>、 v-bind 中支持绑定一个对象 
如果绑定的是一个对象 则 键为 对应的类名  值 为对应data中的数据 
<!-- 
HTML最终渲染为 <ul <span class="hljs-class"><span class="hljs-keyword">class</span></span>=<span class="hljs-string">"box textColor textSize"</span>></ul>
注意：
textColor，textSize  对应的渲染到页面上的CSS类名
isColor，isSize  对应vue data中的数据  如果为<span class="hljs-literal">true</span> 则对应的类名 渲染到页面上 


当 isColor 和 isSize 变化时，<span class="hljs-class"><span class="hljs-keyword">class</span>列表将相应的更新，
例如，将<span class="hljs-title">isSize</span>改成<span class="hljs-title">false</span>，
<span class="hljs-title">class</span>列表将变为 <<span class="hljs-title">ul</span> <span class="hljs-title">class</span></span>=<span class="hljs-string">"box textColor"</span>></ul>
-->

<span class="xml"><span class="hljs-tag"><<span class="hljs-name">ul</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"box"</span> <span class="hljs-attr">v-bind:class</span>=<span class="hljs-string">"&#123;textColor:isColor, textSize:isSize&#125;"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">li</span>></span>学习Vue<span class="hljs-tag"></<span class="hljs-name">li</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">li</span>></span>学习Node<span class="hljs-tag"></<span class="hljs-name">li</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">li</span>></span>学习React<span class="hljs-tag"></<span class="hljs-name">li</span>></span>
<span class="hljs-tag"></<span class="hljs-name">ul</span>></span></span>
  <span class="xml"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">v-bind:style</span>=<span class="hljs-string">"&#123;color:activeColor,fontSize:activeSize&#125;"</span>></span>对象语法<span class="hljs-tag"></<span class="hljs-name">div</span>></span></span>

<span class="xml"><span class="hljs-tag"><<span class="hljs-name">sript</span>></span>
var vm= new Vue(&#123;
    el:'.box',
    data:&#123;
        isColor:true,
        isSize:true，
    activeColor:"red",
        activeSize:"25px",
    &#125;
&#125;)
<span class="hljs-tag"></<span class="hljs-name">sript</span>></span></span>
<span class="xml"><span class="hljs-tag"><<span class="hljs-name">style</span>></span><span class="css">

    <span class="hljs-selector-class">.box</span>&#123;
        <span class="hljs-attribute">border</span>:<span class="hljs-number">1px</span> dashed <span class="hljs-number">#f0f</span>;
    &#125;
    <span class="hljs-selector-class">.textColor</span>&#123;
        <span class="hljs-attribute">color</span>:<span class="hljs-number">#f00</span>;
        <span class="hljs-attribute">background-color</span>:<span class="hljs-number">#eef</span>;
    &#125;
    <span class="hljs-selector-class">.textSize</span>&#123;
        <span class="hljs-attribute">font-size</span>:<span class="hljs-number">30px</span>;
        <span class="hljs-attribute">font-weight</span>:bold;
    &#125;
</span><span class="hljs-tag"></<span class="hljs-name">style</span>></span></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-js copyable" lang="js"><div v-bind:<span class="hljs-class"><span class="hljs-keyword">class</span></span>=<span class="hljs-string">"&#123; active: isActive &#125;"</span>></div>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-50">6.1.2. 数组语法</h3>
<ul>
<li>通过v-bind:class =[ 值1，值2 ]</li>
<li>值1、值2 对应 data 中的 数据</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-number">2</span>、  v-bind 中支持绑定一个数组    数组中classA和 classB 对应为data中的数据

这里的classA  对用data 中的  classA
这里的classB  对用data 中的  classB
<ul <span class="hljs-class"><span class="hljs-keyword">class</span></span>=<span class="hljs-string">"box"</span> :<span class="hljs-class"><span class="hljs-keyword">class</span></span>=<span class="hljs-string">"[classA, classB]"</span>>
    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">li</span>></span>学习Vue<span class="hljs-tag"></<span class="hljs-name">li</span>></span></span>
    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">li</span>></span>学习Node<span class="hljs-tag"></<span class="hljs-name">li</span>></span></span>
    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">li</span>></span>学习React<span class="hljs-tag"></<span class="hljs-name">li</span>></span></span>
</ul>
<span class="xml"><span class="hljs-tag"><<span class="hljs-name">script</span>></span><span class="javascript">
<span class="hljs-keyword">var</span> vm= <span class="hljs-keyword">new</span> Vue(&#123;
    <span class="hljs-attr">el</span>:<span class="hljs-string">'.box'</span>,
    <span class="hljs-attr">data</span>:&#123;
        <span class="hljs-attr">classA</span>:‘textColor‘,
        <span class="hljs-attr">classB</span>:‘textSize‘
    &#125;
&#125;)
</span><span class="hljs-tag"></<span class="hljs-name">script</span>></span></span>
<span class="xml"><span class="hljs-tag"><<span class="hljs-name">style</span>></span><span class="css">
    <span class="hljs-selector-class">.box</span>&#123;
        <span class="hljs-attribute">border</span>:<span class="hljs-number">1px</span> dashed <span class="hljs-number">#f0f</span>;
    &#125;
    <span class="hljs-selector-class">.textColor</span>&#123;
        <span class="hljs-attribute">color</span>:<span class="hljs-number">#f00</span>;
        <span class="hljs-attribute">background-color</span>:<span class="hljs-number">#eef</span>;
    &#125;
    <span class="hljs-selector-class">.textSize</span>&#123;
        <span class="hljs-attribute">font-size</span>:<span class="hljs-number">30px</span>;
        <span class="hljs-attribute">font-weight</span>:bold;
    &#125;
</span><span class="hljs-tag"></<span class="hljs-name">style</span>></span></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-js copyable" lang="js"><div v-bind:<span class="hljs-class"><span class="hljs-keyword">class</span></span>=<span class="hljs-string">"[activeClass, errorClass]"</span>></div>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-51">6.1.3. 绑定对象和绑定数组 的区别</h3>
<ul>
<li>绑定对象的时候 对象的属性 即要渲染的类名 对象的属性值对应的是 data 中的数据</li>
<li>绑定数组的时候数组里面存的是data 中的数据</li>
</ul>
<h3 data-id="heading-52">6.1.4. 对象绑定和数组绑定可以混用吗？</h3>
<ul>
<li>数组中可以存储任何数据类型</li>
<li>对象的值中也可以存储任何数据类型</li>
</ul>
<h2 data-id="heading-53">6.2. style样式处理</h2>
<pre><code class="hljs language-js copyable" lang="js"> <div v-bind:style=<span class="hljs-string">"styleObject"</span>>绑定样式对象</div><span class="hljs-string">'
 
<!-- CSS 属性名可以用驼峰式 (camelCase) 或短横线分隔 (kebab-case，记得用单引号括起来)    -->
 <div v-bind:style="&#123; color: activeColor, fontSize: fontSize,background:'</span>red<span class="hljs-string">' &#125;">内联样式</div>

<!--组语法可以将多个样式对象应用到同一个元素 -->
<div v-bind:style="[styleObj1, styleObj2]"></div>


<script>
new Vue(&#123;
      el: '</span>#app<span class="hljs-string">',
      data: &#123;
        styleObject: &#123;
          color: '</span>green<span class="hljs-string">',
          fontSize: '</span>30px<span class="hljs-string">',
          background:'</span>red<span class="hljs-string">'
        &#125;，
        activeColor: '</span>green<span class="hljs-string">',
   fontSize: "30px"
      &#125;,
      styleObj1: &#123;
             color: '</span>red<span class="hljs-string">'
       &#125;,
       styleObj2: &#123;
            fontSize: '</span>30px<span class="hljs-string">'
       &#125;

</script>
</span><span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-54">6.2.1. 对象语法</h3>
<ul>
<li>v-bind:style =  &#123;  键： 值 &#125;</li>
<li>键 代表 CSS的属性 值 中 存贮的是 CSS 属性值</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"><div v-bind:style=<span class="hljs-string">"&#123; color: activeColor, fontSize: fontSize &#125;"</span>></div>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-55">6.2.2. 数组语法</h3>
<ul>
<li>v-bind:style = [值1， 值2 ]</li>
<li>数组中的值1 和值2 中存储的是一个对象 这个对象里面存储的 css属性和 属性值</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"><div v-bind:style=<span class="hljs-string">"[baseStyles, overridingStyles]"</span>></div>
<span class="copy-code-btn">复制代码</span></code></pre>
<h1 data-id="heading-56">7. 分支循环结构</h1>
<h2 data-id="heading-57">7.1.分支结构</h2>
<ul>
<li>v-if</li>
<li>v-else</li>
<li>v-else-if</li>
<li>v-show</li>
</ul>
<h3 data-id="heading-58">7.1.1. v-if 使用场景</h3>
<ul>
<li>1- 多个元素 通过条件判断展示或者隐藏某个元素。或者多个元素</li>
<li>2- 进行两个视图之间的切换</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"><div id=<span class="hljs-string">"app"</span>>
        <!--  判断是否加载，如果为真，就加载，否则不加载-->
        <span class="xml"><span class="hljs-tag"><<span class="hljs-name">span</span> <span class="hljs-attr">v-if</span>=<span class="hljs-string">"flag"</span>></span>
           如果flag为true则显示,false不显示!
        <span class="hljs-tag"></<span class="hljs-name">span</span>></span></span>
</div>

<span class="xml"><span class="hljs-tag"><<span class="hljs-name">script</span>></span><span class="javascript">
    <span class="hljs-keyword">var</span> vm = <span class="hljs-keyword">new</span> Vue(&#123;
        <span class="hljs-attr">el</span>:<span class="hljs-string">"#app"</span>,
        <span class="hljs-attr">data</span>:&#123;
            <span class="hljs-attr">flag</span>:<span class="hljs-literal">true</span>
        &#125;
    &#125;)
</span><span class="hljs-tag"></<span class="hljs-name">script</span>></span></span>

----------------------------------------------------------

    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">v-if</span>=<span class="hljs-string">"type === 'A'"</span>></span>
       A
    <span class="hljs-tag"></<span class="hljs-name">div</span>></span></span>
  <!-- v-<span class="hljs-keyword">else</span>-<span class="hljs-keyword">if</span>紧跟在v-<span class="hljs-keyword">if</span>或v-<span class="hljs-keyword">else</span>-<span class="hljs-keyword">if</span>之后   表示v-<span class="hljs-keyword">if</span>条件不成立时执行-->
    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">v-else-if</span>=<span class="hljs-string">"type === 'B'"</span>></span>
       B
    <span class="hljs-tag"></<span class="hljs-name">div</span>></span></span>
    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">v-else-if</span>=<span class="hljs-string">"type === 'C'"</span>></span>
       C
    <span class="hljs-tag"></<span class="hljs-name">div</span>></span></span>
  <!-- v-<span class="hljs-keyword">else</span>紧跟在v-<span class="hljs-keyword">if</span>或v-<span class="hljs-keyword">else</span>-<span class="hljs-keyword">if</span>之后-->
    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">v-else</span>></span>
       Not A/B/C
    <span class="hljs-tag"></<span class="hljs-name">div</span>></span></span>

<span class="xml"><span class="hljs-tag"><<span class="hljs-name">script</span>></span><span class="javascript">
    <span class="hljs-keyword">new</span> Vue(&#123;
      <span class="hljs-attr">el</span>: <span class="hljs-string">'#app'</span>,
      <span class="hljs-attr">data</span>: &#123;
        <span class="hljs-attr">type</span>: <span class="hljs-string">'C'</span>
      &#125;
    &#125;)
</span><span class="hljs-tag"></<span class="hljs-name">script</span>></span></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-59">7.2. v-if与v-show的区别</h2>
<ul>
<li>v-show本质就是标签display设置为none，控制隐藏
<ul>
<li>v-show只编译一次，后面其实就是控制css，而v-if不停的销毁和创建，故v-show性能更好一点。</li>
</ul>
</li>
<li>v-if是动态的向DOM树内添加或者删除DOM元素
<ul>
<li>v-if切换有一个局部编译/卸载的过程，切换过程中合适地销毁和重建内部的事件监听和子组件</li>
</ul>
</li>
</ul>
<p><strong>概述</strong></p>
<ul>
<li>v-if控制元素是否渲染到页面</li>
<li>v-show控制元素是否显示（已经渲染到了页面）</li>
</ul>
<h2 data-id="heading-60">7.3. 循环结构</h2>
<h3 data-id="heading-61">7.3.1. v-for遍历数组</h3>
<pre><code class="hljs language-js copyable" lang="js"><li v-<span class="hljs-keyword">for</span>=<span class="hljs-string">'item in list'</span>>&#123;&#123;item&#125;&#125;</li>
<span class="xml"><span class="hljs-tag"><<span class="hljs-name">li</span> <span class="hljs-attr">v-for</span>=<span class="hljs-string">'(item,index) in list'</span>></span>&#123;&#123;item&#125;&#125; + '---' +&#123;&#123;index&#125;&#125;<span class="hljs-tag"></<span class="hljs-name">li</span>></span></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-62">7.3.2. key的作用：帮助Vue区分不同的元素，从而提高性能</h3>
<ul>
<li><strong>key来给每个节点做一个唯一标识</strong></li>
<li><strong>key的作用主要是为了高效的更新虚拟DOM</strong></li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"><li :key=<span class="hljs-string">'item.id'</span> v-<span class="hljs-keyword">for</span>=<span class="hljs-string">'(item,index) in list'</span>>&#123;&#123;item&#125;&#125; + <span class="hljs-string">'---'</span> &#123;&#123;index&#125;&#125;</li>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-63">7.3.3. v-for遍历对象</h3>
<pre><code class="hljs language-js copyable" lang="js"><div v-<span class="hljs-keyword">for</span>=<span class="hljs-string">'(value, key, index) in object'</span>></div>
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>value 代表对象中的每一项</li>
<li>Key 代表对应的键名</li>
<li>Index 代表对应的 索引</li>
</ul>
<h3 data-id="heading-64">7.3.4. v-if和v-for结合使用</h3>
<ul>
<li><strong>不推荐</strong>同时使用 <code>v-if</code> 和 <code>v-for</code></li>
<li>当 <code>v-if</code> 与 <code>v-for</code> 一起使用时，<code>v-for</code> 具有比 <code>v-if</code> 更高的优先级。</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"><div v-<span class="hljs-keyword">if</span>=<span class="hljs-string">'value==12'</span> v-<span class="hljs-keyword">for</span>=<span class="hljs-string">'(value, key, index) in object'</span>></div>
<span class="copy-code-btn">复制代码</span></code></pre></div>  
</div>
            
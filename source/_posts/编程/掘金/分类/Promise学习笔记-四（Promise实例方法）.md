
---
title: 'Promise学习笔记-四（Promise实例方法）'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/94672ef2c7554a109d6deb9df069593f~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 00:52:24 GMT
thumbnail: 'https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/94672ef2c7554a109d6deb9df069593f~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>@charset "UTF-8";.markdown-body&#123;line-height:1.75;font-family:Menlo,Monaco,Consolas,Courier New,monospace;letter-spacing:2px;background-image:linear-gradient(90deg,rgba(50,0,0,.05) 3%,transparent 0),linear-gradient(1turn,rgba(50,0,0,.05) 3%,transparent 0);background-size:20px 20px;background-position:50%;word-break:break-word;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1&#123;font-size:25px;margin-bottom:5px;border-left:5px solid #773098&#125;.markdown-body h1,.markdown-body h2&#123;display:inline-block;font-weight:700;padding-left:10px&#125;.markdown-body h2&#123;font-size:18px;border-left:5px solid #916dd5&#125;.markdown-body h3&#123;font-size:16px;font-weight:700;padding-left:10px;border-left:5px solid #d89cf6&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;border-radius:6px;display:block;margin:20px auto;object-fit:contain;box-shadow:2px 4px 7px #999&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;padding:.2em .5em;font-weight:700;font-size:1em;color:#916dd5;word-break:break-word;overflow-x:auto;background-color:none;border-radius:2px&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;display:block;font-size:12px;padding:16px 12px;margin:0;color:#333;word-break:normal;overflow-x:auto;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#916dd5;font-weight:700;border-bottom:1px solid #916dd5&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#773098&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #916dd5&#125;.markdown-body thead&#123;background-color:#916dd5;color:#fff;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#d89cf6&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #d89cf6;background-color:#f4eeff&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0;line-height:26px&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px;list-style-type:circle&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body b,.markdown-body strong&#123;color:#916dd5;font-weight:700&#125;.markdown-body b:before,.markdown-body strong:before&#123;content:"「"&#125;.markdown-body b:after,.markdown-body strong:after&#123;content:"」"&#125;.markdown-body em,.markdown-body i&#123;color:#916dd5&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><p><img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/94672ef2c7554a109d6deb9df069593f~tplv-k3u1fbpfcp-watermark.image" alt="promise实例方法.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h2 data-id="heading-0">实例方法then</h2>
<h3 data-id="heading-1">then方法的作用</h3>
<p>Promise的状态属性[[PromiseState]]不暴露在Promise对象上，所以不能以编程的方式检测Promise的状态，只有当Promise的状态改变时，通过<code>then()</code>方法采取特定的行动。接受两个参数：第一个是当Promise的状态变为<code>fulfilled</code>时要调用的函数，与异步操作相关的附加数据都会传递给这个完成函数（fulfillment function）；第二个是当Promise的状态变为<code>rejected</code>时要调用的函数，所有与失败状态相关的附加数据都会传递给这个拒绝函数（rejection function）。</p>
<h3 data-id="heading-2">then方法的源码</h3>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-built_in">Promise</span>.prototype.then = <span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params">onFulfilled, onRejected</span>) </span>&#123;
    <span class="hljs-keyword">if</span> (<span class="hljs-built_in">this</span>.constructor !== <span class="hljs-built_in">Promise</span>) &#123;
        <span class="hljs-comment">// 当前constructor不是Promise的构造器时，做些什么</span>
        <span class="hljs-keyword">return</span> safeThen(<span class="hljs-built_in">this</span>, onFulfilled, onRejected)
    &#125;
    <span class="hljs-comment">// 定义一个空的promise对象</span>
    <span class="hljs-keyword">var</span> res = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Promise</span>(noop)
    <span class="hljs-comment">// 添加成功处理函数和失败处理函数绑定</span>
    handle(<span class="hljs-built_in">this</span>, <span class="hljs-keyword">new</span> Handler(onFulfilled, onRejected, res))
    <span class="hljs-comment">// 将promise对象return，以便then的链式调用</span>
    <span class="hljs-keyword">return</span> res
&#125;
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">handler</span>(<span class="hljs-params">onFulfilled, onRejected, promise</span>) </span>&#123;
    <span class="hljs-built_in">this</span>.onFulfilled = <span class="hljs-keyword">typeof</span> onFulfilled === <span class="hljs-string">'function'</span> ? onFulfilled : <span class="hljs-literal">null</span>
    <span class="hljs-built_in">this</span>.onRejected = <span class="hljs-keyword">typeof</span> onRejectd === <span class="hljs-string">'function'</span> ? onRejected : <span class="hljs-literal">null</span>
    <span class="hljs-built_in">this</span>.promise = promise
&#125;
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">handle</span> (<span class="hljs-params">self, deferred</span>) </span>&#123;
    .....
    handleResolve(self, deferred)
&#125;
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">handleResolve</span>(<span class="hljs-params">self, deferred</span>) </span>&#123;
    <span class="hljs-comment">// 通过当前执行状态判断cb设置为成功函数还是拒绝函数</span>
    <span class="hljs-keyword">var</span> cb = self._state === <span class="hljs-number">1</span> ? deferred.onFulfilled : deferred.onRejected
    <span class="hljs-keyword">if</span> (cb === <span class="hljs-literal">null</span>) &#123;
        <span class="hljs-keyword">if</span> (self._state === <span class="hljs-number">1</span>) &#123; <span class="hljs-comment">// 执行成功，但没有传入成功处理函数，再次调用resolve，以便下一个串联的then方法捕获</span>
            resolve(deferred,promise, self._value)
        &#125; <span class="hljs-keyword">else</span> &#123;
            reject(deferred,promise, self._value)
        &#125;
        <span class="hljs-keyword">return</span>
    &#125;
    <span class="hljs-comment">// tryCallOne方法实现从resolve到then方法的值的穿透</span>
    <span class="hljs-keyword">var</span> ret = <span class="hljs-function"><span class="hljs-title">tryCallOne</span>(<span class="hljs-params">cb, self._value</span>)</span> &#123;
        <span class="hljs-keyword">if</span> (ret === IS_ERROR) &#123;
            reject(deferred,promise, LAST_ERROR)
        &#125; <span class="hljs-keyword">else</span> &#123;
            resolve(deferred,promise, ret)
        &#125;
    &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><code>then</code>的源码当中实现两个功能点：第一，<code>then</code>的链式调用；第二，<code>reject</code>和<code>resolve</code>输出值的穿透到<code>then</code>中处理。</p>
<ul>
<li>
<p>then的链式调用的实现，代码如下：</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-built_in">Promise</span>.prototype.then = <span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params">onFulfilled, onRejected</span>) </span>&#123;
    ....
    <span class="hljs-keyword">var</span> res = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Promise</span>(noop)
    handle(<span class="hljs-built_in">this</span>, <span class="hljs-keyword">new</span> Handler(onFulfilled, onRejected, res))
    <span class="hljs-keyword">return</span> res
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>首先在then的处理方法中又重新实例化了Promise对象，并且由<a href="https://juejin.cn/post/6981417003097538574" target="_blank" title="https://juejin.cn/post/6981417003097538574">Promise学习笔记-二</a>一文中的源码可以看到实例化时传入的noop是一个空函数，目的就是让<code>then</code>返回一个Promise对象。因为每个Promise对象都必定有自己的<code>then</code>处理函数，所以就达到了链式调用的目的。</p>
</li>
<li>
<p>从实例化时传入<code>resolve</code>或<code>reject</code>的值，到then方法的穿透，实现代码如下：</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">tryCallOne</span>(<span class="hljs-params">fn, a</span>) </span>&#123;
    <span class="hljs-keyword">try</span> &#123;
        <span class="hljs-keyword">return</span> fn(a)
    &#125; <span class="hljs-keyword">catch</span> (ex) &#123;
        LAST_ERROR = ex
        <span class="hljs-keyword">return</span> IS_ERROR
    &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>把<code>then</code>方法中传入的成功或失败处理函数和当前<code>self._value</code>传入到<code>tryCallOne()</code>方法，内部通过<code>fn(a)</code>实现<code>self._value</code>到then的穿透。</p>
</li>
<li>
<p>链式调用时的穿透。先看一个例子</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-keyword">let</span> promise = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Promise</span>(<span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params">resolve, reject</span>) </span>&#123;
    resolve(<span class="hljs-number">2</span>)
&#125;).then(<span class="hljs-literal">null</span>).then(<span class="hljs-function"><span class="hljs-params">res</span> =></span> &#123;
    <span class="hljs-built_in">console</span>.log(res) <span class="hljs-comment">// 2</span>
&#125;)
<span class="copy-code-btn">复制代码</span></code></pre>
<p>第一个then方法没有传成功处理函数时，第二个<code>then</code>房输出了<code>resolve</code>中的值。在<code>handleResolve()</code>方法中做了什么？</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">handleResolve</span> (<span class="hljs-params">self, deferred</span>) </span>&#123;
    <span class="hljs-keyword">var</span> cb = self._state === <span class="hljs-number">1</span> ? deferred.onFulfilled ? deferred.onRejected
    <span class="hljs-keyword">if</span> (cb === <span class="hljs-literal">null</span>) &#123;
        <span class="hljs-keyword">if</span> (self._state === <span class="hljs-number">1</span>) &#123;
            resolve(deferred.promise, self._value)
        &#125; <span class="hljs-keyword">else</span> &#123;
            reject(deferred.promise, self._value)
        &#125;
       <span class="hljs-keyword">return</span>
    &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>通过<code>handler</code>实例我们可以知道，当第一个<code>then</code>传入null时，在<code>handleResolve()</code>方法中的<code>cb</code>为<code>null</code>，且此时当前状态值<code>self._state</code>又为<code>1</code>，所以又重新调用了<code>resolve()</code>方法，且return掉了。此时相当于<code>var res = new Promise(noop)</code>实例添加了<code>resolve</code>的处理方法，进而第二个<code>then</code>方法可以处理并得到结果2。</p>
</li>
</ul>
<h2 data-id="heading-3">实例方法catch</h2>
<p><code>catch()</code>方法相当于只给其传入拒绝处理程序的then()方法。所以它的实现过程调用了实例上的<code>then()</code>方法。源码如下：</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-built_in">Promise</span>.prototype[<span class="hljs-string">'catch'</span>] = <span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params">onRejected</span>) </span>&#123;
    <span class="hljs-keyword">return</span> <span class="hljs-built_in">this</span>.then(<span class="hljs-literal">null</span>, onRejected)
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-4">实例方法finally</h2>
<h3 data-id="heading-5">finally方法的作用</h3>
<p><code>finally()</code>方法用于指定不管Promise对象状态如何，都会执行的操作。<code>finally()</code>的回调函数不接受任何参数，意味着没办法知道，前面的Promise的状态到底是<code>fulfilled</code>还是<code>rejected</code>。这表明<code>finally</code>里面的操作不依赖于Promise的执行结果。</p>
<h3 data-id="heading-6">finally用法</h3>
<p>服务器使用Promise处理请求，然后使用finally关掉服务器</p>
<pre><code class="hljs language-javascript copyable" lang="javascript">server.listen(port).then(<span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params"></span>) </span>&#123;
    ....
&#125;).finally(server.stop)
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-7">finally方法的源码</h3>
<p><code>finally()</code>本质上是<code>then</code>方法的特例。实现过程如下代码：</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-built_in">Promise</span>.prototype.finally = <span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params">f</span>) </span>&#123;
    <span class="hljs-keyword">return</span> <span class="hljs-built_in">this</span>.then(<span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params">value</span>) </span>&#123;
        <span class="hljs-keyword">return</span> <span class="hljs-built_in">Promise</span>.resolve(f ()).then(<span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params"></span>) </span>&#123;
            <span class="hljs-keyword">return</span> value
        &#125;)
    &#125;, <span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params">reason</span>) </span>&#123;
        <span class="hljs-keyword">return</span> <span class="hljs-built_in">Promise</span>.resolve(f ()).then(<span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params"></span>) </span>&#123;
            <span class="hljs-keyword">throw</span> reason
        &#125;)
    &#125;)
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-8">参考资料</h2>
<p><a href="https://link.juejin.cn/?target=https%3A%2F%2Fes6.ruanyifeng.com%2F%23docs%2Fpromise" target="_blank" rel="nofollow noopener noreferrer" title="https://es6.ruanyifeng.com/#docs/promise" ref="nofollow noopener noreferrer">ECMAScript 6 入门-Promise对象</a></p></div>  
</div>
            
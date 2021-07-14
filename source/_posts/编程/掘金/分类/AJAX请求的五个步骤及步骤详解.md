
---
title: 'AJAX请求的五个步骤及步骤详解'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7adb89a0df3f451da73c9946b0b22e55~tplv-k3u1fbpfcp-zoom-1.image'
author: 掘金
comments: false
date: Tue, 13 Jul 2021 02:01:43 GMT
thumbnail: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7adb89a0df3f451da73c9946b0b22e55~tplv-k3u1fbpfcp-zoom-1.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h2 data-id="heading-0">什么是AJAX?</h2>
<p>AJAX全称为“Asynchronous JavaScript and XML”（异步JavaScript和 XML），是一种创建交互式网页应用的网页开发技术。通过在后台与服务器进行少量数据交换，Ajax可以使网页实现异步更新。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新。而传统的网页(不使用 Ajax)如果需要更新内容，必需重载整个网页面。</p>
<h2 data-id="heading-1">AJAX的工作原理</h2>
<p>Ajax的工作原理相当于在用户和服务器之间加了一个中间层(AJAX引擎)，使用户操作与服务器响应异步化。客户端发送请求，请求交给xhr，xhr把请求提交给服务器，服务器进行业务处理，服务器响应数据交给xhr对象，xhr对象接收数据，由javascript把数据写到页面上，如下图所示：
<img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7adb89a0df3f451da73c9946b0b22e55~tplv-k3u1fbpfcp-zoom-1.image" alt="AJAX工作原理图" loading="lazy" referrerpolicy="no-referrer"></p>
<h2 data-id="heading-2">AJAX请求的五个步骤</h2>
<pre><code class="copyable">1.建立XMLHttpRequest对象;
2.设置回调函数;
3.配置请求信息，(如open,get方法)，使用open方法与服务器建立链接;
4.向服务器发送数据;
5.在回调函数中针对不同的响应状态进行处理;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-3">1.创建XMLHttpRequest异步对象</h3>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-keyword">var</span> xhr;  <span class="hljs-comment">//定义一个变量,用于存放XMLHttpRequest对象</span>
<span class="hljs-keyword">if</span>(<span class="hljs-built_in">window</span>.XMLHttpRequest) &#123; 
  <span class="hljs-comment">// code for IE7+, Firefox, Chrome, Opera, Safari</span>
  xhr = <span class="hljs-keyword">new</span> XMLHttpRequest();
&#125; <span class="hljs-keyword">else</span> &#123;
  <span class="hljs-comment">// code for IE6, IE5</span>
  xhr = <span class="hljs-keyword">new</span> ActiveXObject(<span class="hljs-string">"Microsoft.XMLHTTP"</span>);
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-4">2.设置回调函数</h3>
<pre><code class="hljs language-javascript copyable" lang="javascript">xhr.onreadystatechange = callback；
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-5">3.使用open方法与服务器建立连接</h3>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-comment">// get 方式</span>
xhr.open(<span class="hljs-string">"get"</span>, <span class="hljs-string">"test.php"</span>, <span class="hljs-literal">true</span>)

<span class="hljs-comment">// post 方式发送数据 需要设置请求头</span>
xhr.open(<span class="hljs-string">"post"</span>, <span class="hljs-string">"test.php"</span>, <span class="hljs-literal">true</span>)
xhr.setRequestHeader(<span class="hljs-string">"Content-Type"</span>, <span class="hljs-string">"application/x-www-form-urlencoded"</span>)
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-6">4.向服务器发送数据</h3>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-comment">// get 不需要传递参数</span>
xhr.send(<span class="hljs-literal">null</span>)

<span class="hljs-comment">// post 需要传递参数</span>
xhr.send(<span class="hljs-string">"name=jay&age=18"</span>)
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-7">5.在回调函数中对不同的响应状态进行处理</h3>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">callback</span>(<span class="hljs-params"></span>) </span>&#123;
  <span class="hljs-comment">// 判断异步对象的状态</span>
  <span class="hljs-keyword">if</span>(xhr.readyState == <span class="hljs-number">4</span>) &#123;
    <span class="hljs-comment">// 判断交互是否成功</span>
    <span class="hljs-keyword">if</span>(xhr.status == <span class="hljs-number">200</span>) &#123;
      <span class="hljs-comment">// 获取服务器响应的数据</span>
      <span class="hljs-keyword">var</span> res = xhr.responseText
      <span class="hljs-comment">// 解析数据</span>
      res = <span class="hljs-built_in">JSON</span>.parse(res)
    &#125;
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>ajax中的五种状态码
<ul>
<li>0：请求未初始化</li>
<li>1：服务器连接已建立(已调用open方法，但还未调用send)</li>
<li>2：请求已接收(已调用send方法)</li>
<li>3：请求处理中(请求已到达服务端，正在处理)</li>
<li>4：请求已完成，且响应已就绪</li>
<li>状态： 200——正确、404——未找到页面、500——错误</li>
</ul>
</li>
</ul>
<h2 data-id="heading-8">完整的AJAX实例</h2>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-comment">// -----1.创建XMLHttpRequest对象，也就是创建一个异步调用对象</span>
<span class="hljs-keyword">var</span> xhr = <span class="hljs-keyword">new</span> XMLHttpRequest();
<span class="hljs-comment">// -----3. 创建一个新的HTTP请求，并指定该请求的方法、URL及验证信息</span>
xhr.open(<span class="hljs-string">'post'</span>,<span class="hljs-string">'www.xxx.com'</span>,<span class="hljs-literal">true</span>)
<span class="hljs-comment">// 接收返回值</span>
<span class="hljs-comment">// -----2、设置响应HTTP请求状态变化的函数------5.回调函数对不同状态进行处理</span>
xhr.onreadystatechange = <span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params"></span>)</span>&#123;    <span class="hljs-comment">//xhr.onreadystatechange = callback;时间回调</span>
  <span class="hljs-keyword">if</span>(xhr.readyState === <span class="hljs-number">4</span>) &#123;
    <span class="hljs-keyword">if</span>(xhr.status >= <span class="hljs-number">200</span> && xhr.status < <span class="hljs-number">300</span> || CharacterData.status == <span class="hljs-number">304</span>) &#123;
      <span class="hljs-built_in">console</span>.log(xhr.responseText);
    &#125;
  &#125; 
&#125;
<span class="hljs-comment">// -----处理请求参数</span>
postData = &#123;<span class="hljs-string">"name1"</span>: <span class="hljs-string">"value1"</span>, <span class="hljs-string">"name2"</span>: <span class="hljs-string">"value2"</span>&#125;;
postData = (<span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params">value</span>)</span>&#123;
  <span class="hljs-keyword">var</span> dataString = <span class="hljs-string">""</span>;
  <span class="hljs-keyword">for</span>(<span class="hljs-keyword">var</span> key <span class="hljs-keyword">in</span> value)&#123;
       dataString += key+<span class="hljs-string">"="</span>+value[key]+<span class="hljs-string">"&"</span>;
  &#125;;
    <span class="hljs-keyword">return</span> dataString;
&#125;(postData));

<span class="hljs-comment">// 设置请求头</span>
xhr.setRequestHeader(<span class="hljs-string">"Content-type"</span>, <span class="hljs-string">"applicationx-www-form-urlencoded"</span>);
<span class="hljs-comment">// 异常处理</span>
xhr.onerror = <span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params"></span>) </span>&#123;
  <span class="hljs-built_in">console</span>.log(<span class="hljs-string">'Network request failed'</span>)
&#125;
<span class="hljs-comment">// 跨域携带cookie</span>
xhr.withCredentials = <span class="hljs-literal">true</span>;
<span class="hljs-comment">// ----4.发出请求</span>
xhr.send(postData);

<span class="copy-code-btn">复制代码</span></code></pre>
<p>参考文档：<a href="https://link.juejin.cn/?target=https%3A%2F%2Fblog.csdn.net%2Fchaopingyao%2Farticle%2Fdetails%2F106481895" target="_blank" rel="nofollow noopener noreferrer" title="https://blog.csdn.net/chaopingyao/article/details/106481895" ref="nofollow noopener noreferrer">参考文档1</a>、<a href="https://link.juejin.cn/?target=https%3A%2F%2Fwww.cnblogs.com%2Ftfxz%2Fp%2F12701681.html" target="_blank" rel="nofollow noopener noreferrer" title="https://www.cnblogs.com/tfxz/p/12701681.html" ref="nofollow noopener noreferrer">参考文档2</a></p></div>  
</div>
            

---
title: 'Vue之全局水印'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=6444'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 23:22:46 GMT
thumbnail: 'https://picsum.photos/400/300?random=6444'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><p>【需求】系统内页面显示水印，登录页面没有水印（退出登录时，登录页面不会显示水印）</p>
<h2 data-id="heading-0">1.创建水印Js文件</h2>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">/*
 * @Author: 刘小二
 * @Date: 2021-07-15 14:43:27
 * @LastEditTime: 2021-07-15 15:00:27
 * @LastEditors: Please set LastEditors
 * @Description: 添加水印
 * @FilePath: /huashijc_MeetingSys/src/common/warterMark.js
 */</span>
<span class="hljs-meta">'use strict'</span>
 
<span class="hljs-keyword">let</span> watermark = &#123;&#125;
 
<span class="hljs-keyword">let</span> setWatermark = <span class="hljs-function">(<span class="hljs-params">str</span>) =></span> &#123;
  <span class="hljs-keyword">let</span> id = <span class="hljs-string">'1.23452384164.123412415'</span>
 
  <span class="hljs-keyword">if</span> (<span class="hljs-built_in">document</span>.getElementById(id) !== <span class="hljs-literal">null</span>) &#123;
    <span class="hljs-built_in">document</span>.body.removeChild(<span class="hljs-built_in">document</span>.getElementById(id))
  &#125;
 
  <span class="hljs-keyword">let</span> can = <span class="hljs-built_in">document</span>.createElement(<span class="hljs-string">'canvas'</span>)
  can.width = <span class="hljs-number">250</span>
  can.height = <span class="hljs-number">120</span>
 
  <span class="hljs-keyword">let</span> cans = can.getContext(<span class="hljs-string">'2d'</span>)
  cans.rotate(-<span class="hljs-number">15</span> * <span class="hljs-built_in">Math</span>.PI / <span class="hljs-number">150</span>)
  cans.font = <span class="hljs-string">'20px Vedana'</span>
  cans.fillStyle = <span class="hljs-string">'rgba(200, 200, 200, 0.20)'</span>
  cans.textAlign = <span class="hljs-string">'left'</span>
  cans.textBaseline = <span class="hljs-string">'Middle'</span>
  cans.fillText(str, can.width / <span class="hljs-number">8</span>, can.height / <span class="hljs-number">2</span>)
 
  <span class="hljs-keyword">let</span> div = <span class="hljs-built_in">document</span>.createElement(<span class="hljs-string">'div'</span>)
  div.id = id
  div.style.pointerEvents = <span class="hljs-string">'none'</span>
  div.style.top = <span class="hljs-string">'35px'</span>
  div.style.left = <span class="hljs-string">'0px'</span>
  div.style.position = <span class="hljs-string">'fixed'</span>
  div.style.zIndex = <span class="hljs-string">'100000'</span>
  div.style.width = <span class="hljs-built_in">document</span>.documentElement.clientWidth + <span class="hljs-string">'px'</span>
  div.style.height = <span class="hljs-built_in">document</span>.documentElement.clientHeight + <span class="hljs-string">'px'</span>
  div.style.background = <span class="hljs-string">'url('</span> + can.toDataURL(<span class="hljs-string">'image/png'</span>) + <span class="hljs-string">') left top repeat'</span>
  <span class="hljs-built_in">document</span>.body.appendChild(div)
  <span class="hljs-keyword">return</span> id
&#125;
 
<span class="hljs-comment">// 该方法只允许调用一次</span>
watermark.set = <span class="hljs-function">(<span class="hljs-params">str</span>) =></span> &#123;
  <span class="hljs-keyword">let</span> id = setWatermark(str)
  <span class="hljs-built_in">setInterval</span>(<span class="hljs-function">() =></span> &#123;
    <span class="hljs-keyword">if</span> (<span class="hljs-built_in">document</span>.getElementById(id) === <span class="hljs-literal">null</span>) &#123;
      id = setWatermark(str)
    &#125;
  &#125;, <span class="hljs-number">500</span>)
  <span class="hljs-built_in">window</span>.onresize = <span class="hljs-function">() =></span> &#123;
    setWatermark(str)
  &#125;
&#125;

<span class="hljs-keyword">const</span> outWatermark = <span class="hljs-function">(<span class="hljs-params">id</span>) =></span> &#123;
    <span class="hljs-keyword">if</span> (<span class="hljs-built_in">document</span>.getElementById(id) !== <span class="hljs-literal">null</span>) &#123;
      <span class="hljs-keyword">const</span> div = <span class="hljs-built_in">document</span>.getElementById(id)
      div.style.display = <span class="hljs-string">'none'</span>
    &#125;
&#125;
watermark.out = <span class="hljs-function">() =></span> &#123;
    <span class="hljs-keyword">const</span> str = <span class="hljs-string">'1.23452384164.123412415'</span>
    outWatermark(str)
&#125;
 
<span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span> watermark
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-1">2.引入操作</h2>
<h3 data-id="heading-2">2.1 在App.vue中引用或其他页面</h3>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">// 1.在App.vue文件中，导入该文件</span>
<span class="hljs-keyword">import</span> Watemark <span class="hljs-keyword">from</span> <span class="hljs-string">'@/common/watermark'</span>;

computed: &#123;
  <span class="hljs-function"><span class="hljs-title">userName</span>(<span class="hljs-params"></span>)</span> &#123;
    <span class="hljs-keyword">const</span> name = <span class="hljs-built_in">this</span>.$store.state.user.name
    <span class="hljs-keyword">return</span> (name && name.length > <span class="hljs-number">0</span>) ? name : <span class="hljs-string">'未获取到用户名'</span>
  &#125;
&#125;,
<span class="hljs-function"><span class="hljs-title">mounted</span>(<span class="hljs-params"></span>)</span> &#123;
  Watermark.set(<span class="hljs-built_in">this</span>.userName)
&#125;

<span class="hljs-comment">// 2.在其他页面引用</span>
<span class="hljs-keyword">import</span> Watemark <span class="hljs-keyword">from</span> <span class="hljs-string">'@/common/watermark'</span>;

<span class="hljs-function"><span class="hljs-title">created</span>(<span class="hljs-params"></span>)</span> &#123;
  Watermark.set(<span class="hljs-string">'admin'</span>)
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-3">2.2 在router配置文件中引用</h3>
<pre><code class="hljs language-js copyable" lang="js">
<span class="hljs-keyword">const</span> outWatermark = <span class="hljs-function">(<span class="hljs-params">id</span>) =></span> &#123;
  <span class="hljs-keyword">if</span> (<span class="hljs-built_in">document</span>.getElementById(id) !== <span class="hljs-literal">null</span>) &#123;
    <span class="hljs-keyword">const</span> div = <span class="hljs-built_in">document</span>.getElementById(id)
    div.style.display = <span class="hljs-string">'none'</span>
  &#125;
&#125;

router.afterEach(<span class="hljs-function">(<span class="hljs-params">to</span>) =></span> &#123;
<span class="hljs-keyword">if</span>(to.path == <span class="hljs-string">'/'</span>)&#123;
Watermark.out() <span class="hljs-comment">// 清除水印</span>
&#125;<span class="hljs-keyword">else</span>&#123;
Watermark.set(<span class="hljs-string">'未获取到用户名'</span>) <span class="hljs-comment">// 设置水印title</span>
&#125;
&#125;);
<span class="copy-code-btn">复制代码</span></code></pre></div>  
</div>
            
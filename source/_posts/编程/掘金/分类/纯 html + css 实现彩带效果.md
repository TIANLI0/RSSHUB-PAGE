
---
title: '纯 html + css 实现彩带效果'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/bafb4cc911c147fba776aa7b203267f0~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Tue, 13 Jul 2021 19:04:23 GMT
thumbnail: 'https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/bafb4cc911c147fba776aa7b203267f0~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><p><img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/bafb4cc911c147fba776aa7b203267f0~tplv-k3u1fbpfcp-watermark.image" alt="ribbon.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p>这个效果看起来很酷，我们来实现一下。</p>
<p><strong>代码</strong></p>
<p>html - 一个容器，一个彩带</p>
<pre><code class="hljs language-css copyable" lang="css"><<span class="hljs-selector-tag">div</span> class="container">
  <<span class="hljs-selector-tag">div</span> class="ribbon">
    hello,world
  </<span class="hljs-selector-tag">div</span>>
</<span class="hljs-selector-tag">div</span>>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>css</p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.container</span> &#123;
    <span class="hljs-attribute">width</span>: <span class="hljs-number">500px</span>;
    <span class="hljs-attribute">height</span>: <span class="hljs-number">500px</span>;
    <span class="hljs-attribute">position</span>: relative;
    <span class="hljs-attribute">overflow</span>: hidden;
    <span class="hljs-attribute">border</span>: <span class="hljs-number">1px</span> solid <span class="hljs-number">#eee</span>;
&#125;
<span class="hljs-selector-pseudo">:root</span> &#123;
    --ribbonWidth: <span class="hljs-number">200px</span>;
    <span class="hljs-comment">/* 根据勾股定理计算出偏移量: 200*200 = x^2 + x^2 */</span>
    --offsetX: <span class="hljs-number">58.58px</span>; 
&#125;
<span class="hljs-selector-class">.ribbon</span> &#123;
    <span class="hljs-attribute">display</span>: inline-block;
    <span class="hljs-attribute">box-sizing</span>: border-box;
    <span class="hljs-attribute">text-align</span>: center;
    <span class="hljs-comment">/* 定位在右上角 */</span>
    <span class="hljs-attribute">position</span>: absolute;
    <span class="hljs-attribute">top</span>: <span class="hljs-number">0</span>;
    <span class="hljs-attribute">right</span>: <span class="hljs-number">0</span>;
    <span class="hljs-attribute">background</span>: <span class="hljs-number">#d4f5f6</span>;
    <span class="hljs-attribute">padding</span>: <span class="hljs-number">10px</span> <span class="hljs-number">0</span>;
    <span class="hljs-attribute">width</span>: <span class="hljs-built_in">var</span>(--ribbonWidth);
    
    <span class="hljs-comment">/* 定位彩带 */</span>
    <span class="hljs-comment">/* 以左下角为锚点进行旋转操作 */</span>
    <span class="hljs-attribute">transform-origin</span>: bottom left;
    <span class="hljs-attribute">transform</span>: <span class="hljs-built_in">translateY</span>(-<span class="hljs-number">100%</span>) <span class="hljs-built_in">translateX</span>(<span class="hljs-built_in">var</span>(--offsetX)) <span class="hljs-built_in">rotate</span>(<span class="hljs-number">45deg</span>);
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><code>translateY(-100%)</code></p>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1f6c2efe4c3b4bcb946fef21ede439ad~tplv-k3u1fbpfcp-watermark.image" alt="WXWorkCapture_16262309854716.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p><code> translateX(var(--offsetX))</code></p>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d3c50d707ed64c829c8192c4c334bb46~tplv-k3u1fbpfcp-watermark.image" alt="WXWorkCapture_16262310164958.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p><code>rotate(45deg)</code></p>
<p><img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6e4ecce75fb746a8b1a1a37f658e2508~tplv-k3u1fbpfcp-watermark.image" alt="WXWorkCapture_16262310333453.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p><code>overflow: hidden</code></p>
<p><img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0a55d5b262f64c09a74e0a331fcb5a7f~tplv-k3u1fbpfcp-watermark.image" alt="localhost_3000_ribon.html.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p>done!</p>
<p>在线代码演示 <a href="https://link.juejin.cn/?target=https%3A%2F%2Fjsbin.com%2Fjamajaj%2Fedit%3Fhtml%2Ccss%2Coutput" target="_blank" rel="nofollow noopener noreferrer" title="https://jsbin.com/jamajaj/edit?html,css,output" ref="nofollow noopener noreferrer">jsbin.com/jamajaj/edi…</a></p>
<p>想放哪个角落都可以！</p>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/58d289669bd44c868bc94f6e48e3da34~tplv-k3u1fbpfcp-watermark.image" alt="WXWorkCapture_16262313141830.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a3d2aad4735d4981a3deeaff84b5c73e~tplv-k3u1fbpfcp-watermark.image" alt="WXWorkCapture_16262313851799.png" loading="lazy" referrerpolicy="no-referrer"></p></div>  
</div>
            
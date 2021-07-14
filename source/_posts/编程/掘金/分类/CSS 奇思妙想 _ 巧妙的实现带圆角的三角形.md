
---
title: 'CSS 奇思妙想 _ 巧妙的实现带圆角的三角形'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/3e530cf2ac5d403d8f5cc4e03e8d25fe~tplv-k3u1fbpfcp-zoom-1.image'
author: 掘金
comments: false
date: Tue, 13 Jul 2021 18:12:19 GMT
thumbnail: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/3e530cf2ac5d403d8f5cc4e03e8d25fe~tplv-k3u1fbpfcp-zoom-1.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><p>之前在这篇文章中 -- <a href="https://juejin.cn/post/6950081305560219679" target="_blank" title="https://juejin.cn/post/6950081305560219679">《老生常谈之 CSS 实现三角形》</a>，介绍了 6 种使用 CSS 实现三角形的方式。</p>
<p>但是其中漏掉了一个非常重要的场景，<strong>如何使用纯 CSS 实现带圆角的三角形呢？</strong>，像是这样：</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/3e530cf2ac5d403d8f5cc4e03e8d25fe~tplv-k3u1fbpfcp-zoom-1.image" alt="A triangle with rounded" loading="lazy" referrerpolicy="no-referrer"></p>
<p>本文将介绍几种实现带圆角的三角形的实现方式。</p>
<h2 data-id="heading-0">法一. 全兼容的 SVG 大法</h2>
<p>想要生成一个带圆角的三角形，<strong>代码量最少</strong>、最好的方式是使用 SVG 生成。</p>
<p>使用 SVG 的 多边形标签 <code><polygon></code> 生成一个三边形，使用 SVG 的 <code>stroke-linejoin="round"</code> 生成连接处的圆角。</p>
<p>代码量非常少，核心代码如下：</p>
<pre><code class="hljs language-HTML copyable" lang="HTML"><span class="hljs-tag"><<span class="hljs-name">svg</span>  <span class="hljs-attr">width</span>=<span class="hljs-string">"250"</span> <span class="hljs-attr">height</span>=<span class="hljs-string">"250"</span> <span class="hljs-attr">viewBox</span>=<span class="hljs-string">"-50 -50 300 300"</span>></span>
  <span class="hljs-tag"><<span class="hljs-name">polygon</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"triangle"</span> <span class="hljs-attr">stroke-linejoin</span>=<span class="hljs-string">"round"</span> <span class="hljs-attr">points</span>=<span class="hljs-string">"100,0 0,200 200,200"</span>/></span>
<span class="hljs-tag"></<span class="hljs-name">svg</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-CSS copyable" lang="CSS"><span class="hljs-selector-class">.triangle</span> &#123;
    fill: <span class="hljs-number">#0f0</span>;
    stroke: <span class="hljs-number">#0f0</span>;
    stroke-<span class="hljs-attribute">width</span>: <span class="hljs-number">10</span>;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>实际图形如下：</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/12ee2b84034546388acf97bdf9689773~tplv-k3u1fbpfcp-zoom-1.image" alt="A triangle with rounded" loading="lazy" referrerpolicy="no-referrer"></p>
<p>这里，其实是借助了 SVG 多边形的 <code>stroke-linejoin: round</code> 属性生成的圆角，<code>stroke-linejoin</code> 是什么？它用来控制两条描边线段之间，有三个可选值：</p>
<ul>
<li><code>miter</code> 是默认值，表示用方形画笔在连接处形成尖角</li>
<li><code>round</code> 表示用圆角连接，实现平滑效果</li>
<li><code>bevel</code> 连接处会形成一个斜接</li>
</ul>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b82ca21398734144870a3c6cfbff5ac1~tplv-k3u1fbpfcp-zoom-1.image" alt loading="lazy" referrerpolicy="no-referrer"></p>
<p>我们实际是<strong>通过一个带边框，且边框连接类型为 <code>stroke-linejoin: round</code> 的多边形生成圆角三角形的</strong>。</p>
<p>如果，我们把底色和边框色区分开，实际是这样的：</p>
<pre><code class="hljs language-CSS copyable" lang="CSS"><span class="hljs-selector-class">.triangle</span> &#123;
    fill: <span class="hljs-number">#0f0</span>;
    stroke: <span class="hljs-number">#000</span>;
    stroke-<span class="hljs-attribute">width</span>: <span class="hljs-number">10</span>;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/70313c08b8864a819b150e0a29be2428~tplv-k3u1fbpfcp-zoom-1.image" alt loading="lazy" referrerpolicy="no-referrer"></p>
<h3 data-id="heading-1">通过 stroke-width 控制圆角大小</h3>
<p>那么如何控制圆角大小呢？也非常简单，通过控制 <code>stroke-width</code> 的大小，可以改变圆角的大小。</p>
<p>当然，要保持三角形大小一致，在增大/缩小 <code>stroke-width</code> 的同时，需要缩小/增大图形的 <code>width</code>/<code>height</code>：</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/60c7c6569a184aec8744e0bfc6884dae~tplv-k3u1fbpfcp-zoom-1.image" alt loading="lazy" referrerpolicy="no-referrer"></p>
<p>完整的 DEMO 你可以戳这里：<a href="https://link.juejin.cn/?target=https%3A%2F%2Fcodepen.io%2FChokcoco%2Fpen%2FeYWZvKo" target="_blank" rel="nofollow noopener noreferrer" title="https://codepen.io/Chokcoco/pen/eYWZvKo" ref="nofollow noopener noreferrer">CodePen Demo -- 使用 SVG 实现带圆角的三角形</a></p>
<h2 data-id="heading-2">法二. 图形拼接</h2>
<p>不过，上文提到了，<strong>使用纯 CSS 实现带圆角的三角形</strong>，但是上述第一个方法其实是借助了 SVG。那么仅仅使用 CSS，有没有办法呢？</p>
<p>当然，发散思维，CSS 有意思的地方正在于此处，用一个图形，能够有非常多种巧妙的解决方案！</p>
<p>我们看看，一个圆角三角形，它其实可以被拆分成几个部分：</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/99ee2beddb8a4672a8978ac869fca87f~tplv-k3u1fbpfcp-zoom-1.image" alt loading="lazy" referrerpolicy="no-referrer"></p>
<p>所以，其实我们只需要能够画出一个这样的带圆角的菱形，通过 3 个进行旋转叠加，就能得到圆角三角形：</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8b4f283b562044b2bdcde3b716d4d664~tplv-k3u1fbpfcp-zoom-1.image" alt loading="lazy" referrerpolicy="no-referrer"></p>
<h3 data-id="heading-3">绘制带圆角的菱形</h3>
<p>那么，接下来我们的目标就变成了绘制一个带圆角的菱形，方法有很多，本文给出其中一种方式：</p>
<ol>
<li>首先将一个正方形变成一个菱形，利用 <code>transform</code> 有一个固定的公式：</li>
</ol>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/97b710e7c2e7476f8bf2d99dfb1fd35c~tplv-k3u1fbpfcp-zoom-1.image" alt loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="hljs language-HTML copyable" lang="HTML"><span class="hljs-tag"><<span class="hljs-name">div</span>></span><span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-CSS copyable" lang="CSS"><span class="hljs-selector-tag">div</span> &#123;
    <span class="hljs-attribute">width</span>:  <span class="hljs-number">10em</span>;
    <span class="hljs-attribute">height</span>: <span class="hljs-number">10em</span>;
    <span class="hljs-attribute">transform</span>: <span class="hljs-built_in">rotate</span>(-<span class="hljs-number">60deg</span>) <span class="hljs-built_in">skewX</span>(-<span class="hljs-number">30deg</span>) <span class="hljs-built_in">scale</span>(<span class="hljs-number">1</span>, <span class="hljs-number">0.866</span>);
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><img src="https://user-images.githubusercontent.com/8554143/124758959-b23b8900-df61-11eb-9236-17f22071f155.gif" alt loading="lazy" referrerpolicy="no-referrer"></p>
<ol start="2">
<li>将其中一个角变成圆角：</li>
</ol>
<pre><code class="hljs language-CSS copyable" lang="CSS"><span class="hljs-selector-tag">div</span> &#123;
    <span class="hljs-attribute">width</span>:  <span class="hljs-number">10em</span>;
    <span class="hljs-attribute">height</span>: <span class="hljs-number">10em</span>;
    <span class="hljs-attribute">transform</span>: <span class="hljs-built_in">rotate</span>(-<span class="hljs-number">60deg</span>) <span class="hljs-built_in">skewX</span>(-<span class="hljs-number">30deg</span>) <span class="hljs-built_in">scale</span>(<span class="hljs-number">1</span>, <span class="hljs-number">0.866</span>);
  + <span class="hljs-attribute">border-top-right-radius</span>: <span class="hljs-number">30%</span>;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b363c47eee294c6a8c81ea1a603fbe05~tplv-k3u1fbpfcp-zoom-1.image" alt loading="lazy" referrerpolicy="no-referrer"></p>
<p>至此，我们就顺利的得到一个带圆角的菱形了！</p>
<h3 data-id="heading-4">拼接 3 个带圆角的菱形</h3>
<p>接下来就很简单了，我们只需要利用元素的另外两个伪元素，再生成 2 个带圆角的菱形，将一共 3 个图形旋转位移拼接起来即可！</p>
<p>完整的代码如下：</p>
<pre><code class="hljs language-HTML copyable" lang="HTML"><span class="hljs-tag"><<span class="hljs-name">div</span>></span><span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-CSS copyable" lang="CSS"><span class="hljs-selector-tag">div</span>&#123;
    <span class="hljs-attribute">position</span>: relative;
    <span class="hljs-attribute">background-color</span>: orange;
&#125;
<span class="hljs-selector-tag">div</span>:before,
div:after &#123;
    content: <span class="hljs-string">''</span>;
    <span class="hljs-attribute">position</span>: absolute;
    <span class="hljs-attribute">background-color</span>: inherit;
&#125;
<span class="hljs-selector-tag">div</span>,
<span class="hljs-selector-tag">div</span>:before,
div:after &#123;
    width:  <span class="hljs-number">10em</span>;
    <span class="hljs-attribute">height</span>: <span class="hljs-number">10em</span>;
    <span class="hljs-attribute">border-top-right-radius</span>: <span class="hljs-number">30%</span>;
&#125;
<span class="hljs-selector-tag">div</span> &#123;
    <span class="hljs-attribute">transform</span>: <span class="hljs-built_in">rotate</span>(-<span class="hljs-number">60deg</span>) <span class="hljs-built_in">skewX</span>(-<span class="hljs-number">30deg</span>) <span class="hljs-built_in">scale</span>(<span class="hljs-number">1</span>,.<span class="hljs-number">866</span>);
&#125;
<span class="hljs-selector-tag">div</span>:before &#123;
    transform: <span class="hljs-built_in">rotate</span>(-<span class="hljs-number">135deg</span>) <span class="hljs-built_in">skewX</span>(-<span class="hljs-number">45deg</span>) <span class="hljs-built_in">scale</span>(<span class="hljs-number">1.414</span>, .<span class="hljs-number">707</span>) <span class="hljs-built_in">translate</span>(<span class="hljs-number">0</span>,-<span class="hljs-number">50%</span>);
&#125;
<span class="hljs-selector-tag">div</span>:after &#123;
    transform: <span class="hljs-built_in">rotate</span>(<span class="hljs-number">135deg</span>) <span class="hljs-built_in">skewY</span>(-<span class="hljs-number">45deg</span>) <span class="hljs-built_in">scale</span>(.<span class="hljs-number">707</span>, <span class="hljs-number">1.414</span>) <span class="hljs-built_in">translate</span>(<span class="hljs-number">50%</span>);
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>就可以得到一个圆角三角形了！效果如下：</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/237e0be2a4fa404e8cc55274f1d051af~tplv-k3u1fbpfcp-zoom-1.image" alt="image" loading="lazy" referrerpolicy="no-referrer"></p>
<p>完整的代码你可以戳这里：<a href="https://link.juejin.cn/?target=https%3A%2F%2Fcodepen.io%2FChokcoco%2Fpen%2FvYmLVZr" target="_blank" rel="nofollow noopener noreferrer" title="https://codepen.io/Chokcoco/pen/vYmLVZr" ref="nofollow noopener noreferrer">CodePen Demo -- A triangle with rounded</a></p>
<h2 data-id="heading-5">法三. 图形拼接实现渐变色圆角三角形</h2>
<p>完了吗？没有！</p>
<p>上述方案，虽然不算太复杂，但是有一点还不算太完美的。就是无法支持渐变色的圆角三角形。像是这样：</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/aa3f2ad68b4f4171994aa99b6e20833d~tplv-k3u1fbpfcp-zoom-1.image" alt loading="lazy" referrerpolicy="no-referrer"></p>
<p>如果需要实现渐变色圆角三角形，还是有点复杂的。但真就还有人鼓捣出来了，下述方法参考至 -- <a href="https://link.juejin.cn/?target=https%3A%2F%2Fstackoverflow.com%2Fquestions%2F14446677%2Fhow-to-make-3-corner-rounded-triangle-in-css" target="_blank" rel="nofollow noopener noreferrer" title="https://stackoverflow.com/questions/14446677/how-to-make-3-corner-rounded-triangle-in-css" ref="nofollow noopener noreferrer">How to make 3-corner-rounded triangle in CSS</a>。</p>
<p>同样也是利用了多块进行拼接，但是这次我们的基础图形，会非常的复杂。</p>
<p>首先，我们需要实现这样一个容器外框，和上述的方法比较类似，可以理解为是一个圆角菱形（画出 border 方便理解）：</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9060c3c0d6c74ef88c5cfe2fccca2a8d~tplv-k3u1fbpfcp-zoom-1.image" alt loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="hljs language-HTML copyable" lang="HTML"><span class="hljs-tag"><<span class="hljs-name">div</span>></span><span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-CSS copyable" lang="CSS"><span class="hljs-selector-tag">div</span> &#123;
    <span class="hljs-attribute">width</span>: <span class="hljs-number">200px</span>;
    <span class="hljs-attribute">height</span>: <span class="hljs-number">200px</span>;
    <span class="hljs-attribute">transform</span>: <span class="hljs-built_in">rotate</span>(<span class="hljs-number">30deg</span>) <span class="hljs-built_in">skewY</span>(<span class="hljs-number">30deg</span>) <span class="hljs-built_in">scaleX</span>(<span class="hljs-number">0.866</span>);
    <span class="hljs-attribute">border</span>: <span class="hljs-number">1px</span> solid <span class="hljs-number">#000</span>;
    <span class="hljs-attribute">border-radius</span>: <span class="hljs-number">20%</span>;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>接着，我们同样使用两个伪元素，实现两个稍显怪异的图形进行拼接，算是对 <code>transform</code> 的各种用法的合集：</p>
<pre><code class="hljs language-CSS copyable" lang="CSS"><span class="hljs-selector-tag">div</span><span class="hljs-selector-pseudo">::before</span>,
<span class="hljs-selector-tag">div</span><span class="hljs-selector-pseudo">::after</span> &#123;
    <span class="hljs-attribute">content</span>: <span class="hljs-string">""</span>;
    <span class="hljs-attribute">position</span>: absolute;
    <span class="hljs-attribute">width</span>: <span class="hljs-number">200px</span>;
    <span class="hljs-attribute">height</span>: <span class="hljs-number">200px</span>;
&#125;
<span class="hljs-selector-tag">div</span><span class="hljs-selector-pseudo">::before</span> &#123;
    <span class="hljs-attribute">border-radius</span>: <span class="hljs-number">20%</span> <span class="hljs-number">20%</span> <span class="hljs-number">20%</span> <span class="hljs-number">55%</span>;
    <span class="hljs-attribute">transform</span>: <span class="hljs-built_in">scaleX</span>(<span class="hljs-number">1.155</span>) <span class="hljs-built_in">skewY</span>(-<span class="hljs-number">30deg</span>) <span class="hljs-built_in">rotate</span>(-<span class="hljs-number">30deg</span>) <span class="hljs-built_in">translateY</span>(-<span class="hljs-number">42.3%</span>) <span class="hljs-built_in">skewX</span>(<span class="hljs-number">30deg</span>) <span class="hljs-built_in">scaleY</span>(<span class="hljs-number">0.866</span>) <span class="hljs-built_in">translateX</span>(-<span class="hljs-number">24%</span>);
    <span class="hljs-attribute">background</span>: red;
&#125;
<span class="hljs-selector-tag">div</span><span class="hljs-selector-pseudo">::after</span> &#123;
    <span class="hljs-attribute">border-radius</span>: <span class="hljs-number">20%</span> <span class="hljs-number">20%</span> <span class="hljs-number">55%</span> <span class="hljs-number">20%</span>;
    <span class="hljs-attribute">background</span>: blue;
    <span class="hljs-attribute">transform</span>: <span class="hljs-built_in">scaleX</span>(<span class="hljs-number">1.155</span>) <span class="hljs-built_in">skewY</span>(-<span class="hljs-number">30deg</span>) <span class="hljs-built_in">rotate</span>(-<span class="hljs-number">30deg</span>) <span class="hljs-built_in">translateY</span>(-<span class="hljs-number">42.3%</span>) <span class="hljs-built_in">skewX</span>(-<span class="hljs-number">30deg</span>) <span class="hljs-built_in">scaleY</span>(<span class="hljs-number">0.866</span>) <span class="hljs-built_in">translateX</span>(<span class="hljs-number">24%</span>);
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>为了方便理解，制作了一个简单的变换动画：</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/eaba708ed065443faa1a980a2d4ec616~tplv-k3u1fbpfcp-zoom-1.image" alt loading="lazy" referrerpolicy="no-referrer"></p>
<p>本质就是实现了这样一个图形：</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0b104e7d14ce46f7afc71da85f299bd5~tplv-k3u1fbpfcp-zoom-1.image" alt="image" loading="lazy" referrerpolicy="no-referrer"></p>
<p>最后，给父元素添加一个 <code>overflow: hidden</code> 并且去掉父元素的 <code>border</code> 即可得到一个圆角三角形：</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a85229c5bda04633ba94a80848830e3f~tplv-k3u1fbpfcp-zoom-1.image" alt loading="lazy" referrerpolicy="no-referrer"></p>
<p>由于这两个元素重叠空间的特殊结构，此时，给两个伪元素添加同一个渐变色，会完美的叠加在一起：</p>
<pre><code class="hljs language-CSS copyable" lang="CSS"><span class="hljs-selector-tag">div</span><span class="hljs-selector-pseudo">::before</span>,
<span class="hljs-selector-tag">div</span><span class="hljs-selector-pseudo">::after</span>, &#123;
    <span class="hljs-attribute">background</span>: <span class="hljs-built_in">linear-gradient</span>(<span class="hljs-number">#0f0</span>, <span class="hljs-number">#03a9f4</span>);
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>最终得到一个渐变圆角三角形：</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/644b10a305cf45e8b3962d2771e18fdc~tplv-k3u1fbpfcp-zoom-1.image" alt loading="lazy" referrerpolicy="no-referrer"></p>
<p>上述各个图形的完整代码，你可以戳这里：<a href="https://link.juejin.cn/?target=https%3A%2F%2Fcodepen.io%2FChokcoco%2Fpen%2FLYyGRpV" target="_blank" rel="nofollow noopener noreferrer" title="https://codepen.io/Chokcoco/pen/LYyGRpV" ref="nofollow noopener noreferrer">CodePen Demo -- A triangle with rounded and gradient background</a></p>
<h2 data-id="heading-6">最后</h2>
<p>本文介绍了几种在 CSS 中实现带圆角三角形的方式，虽然部分有些繁琐，但是也体现了 CSS ”有趣且折磨人“ 的一面，具体应用的时候，还是要思考一下，对是否使用上述方式进行取舍，有的时候，切图也许是更好的方案。</p>
<p>好了，本文到此结束，希望对你有帮助 :)</p>
<p>想 Get 到最有意思的 CSS 资讯，千万不要错过我的公众号 -- <strong>iCSS前端趣闻</strong> 😄</p>
<p>更多精彩 CSS 技术文章汇总在我的 <a href="https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fchokcoco%2FiCSS" target="_blank" rel="nofollow noopener noreferrer" title="https://github.com/chokcoco/iCSS" ref="nofollow noopener noreferrer">Github -- iCSS</a> ，持续更新，欢迎点个 star 订阅收藏。</p>
<p>如果还有什么疑问或者建议，可以多多交流，原创文章，文笔有限，才疏学浅，文中若有不正之处，万望告知。</p></div>  
</div>
            
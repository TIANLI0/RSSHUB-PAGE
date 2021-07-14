
---
title: '🍊Flex布局最佳实践之骰子实战篇（面试高频考点，速来围观呀~）'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1518f4579dcb4b07beee520cd9b023ac~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Tue, 13 Jul 2021 06:02:56 GMT
thumbnail: 'https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1518f4579dcb4b07beee520cd9b023ac~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>@charset "UTF-8";.markdown-body&#123;line-height:1.75;font-family:Menlo,Monaco,Consolas,Courier New,monospace;letter-spacing:2px;background-image:linear-gradient(90deg,rgba(50,0,0,.05) 3%,transparent 0),linear-gradient(1turn,rgba(50,0,0,.05) 3%,transparent 0);background-size:20px 20px;background-position:50%;word-break:break-word;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1&#123;font-size:25px;margin-bottom:5px;border-left:5px solid #773098&#125;.markdown-body h1,.markdown-body h2&#123;display:inline-block;font-weight:700;padding-left:10px&#125;.markdown-body h2&#123;font-size:18px;border-left:5px solid #916dd5&#125;.markdown-body h3&#123;font-size:16px;font-weight:700;padding-left:10px;border-left:5px solid #d89cf6&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;border-radius:6px;display:block;margin:20px auto;object-fit:contain;box-shadow:2px 4px 7px #999&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;padding:.2em .5em;font-weight:700;font-size:1em;color:#916dd5;word-break:break-word;overflow-x:auto;background-color:none;border-radius:2px&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;display:block;font-size:12px;padding:16px 12px;margin:0;color:#333;word-break:normal;overflow-x:auto;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#916dd5;font-weight:700;border-bottom:1px solid #916dd5&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#773098&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #916dd5&#125;.markdown-body thead&#123;background-color:#916dd5;color:#fff;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#d89cf6&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #d89cf6;background-color:#f4eeff&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0;line-height:26px&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px;list-style-type:circle&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body b,.markdown-body strong&#123;color:#916dd5;font-weight:700&#125;.markdown-body b:before,.markdown-body strong:before&#123;content:"「"&#125;.markdown-body b:after,.markdown-body strong:after&#123;content:"」"&#125;.markdown-body em,.markdown-body i&#123;color:#916dd5&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><p>「本文已参与好文召集令活动，点击查看：<a href="https://juejin.cn/post/6978685539985653767" target="_blank" title="https://juejin.cn/post/6978685539985653767">后端、大前端双赛道投稿，2万元奖池等你挑战！</a>」</p>
<h1 data-id="heading-0">写在前面</h1>
<blockquote>
<p>在上一篇文章中，介绍了flex布局使用的基本语法，相信大家阅读完应该都掌握了~😚那么这一节给大家带来的是flex布局实战，我们将通过布局骰子点数的练习让大家更好地掌握flex布局，这也是面试中常见考察flex布局的方式哦，让我们一起来学习叭~</p>
</blockquote>
<h2 data-id="heading-1">一、骰子的布局</h2>
<h3 data-id="heading-2">骰子的样式</h3>
<p>这里给出样式代码：<br>
HTML:
<img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1518f4579dcb4b07beee520cd9b023ac~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer">
CSS:</p>
<p><img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/abb18605494842bd9f62718e8c08fb56~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer">
上面代码中，div元素（代表骰子的一个面）是Flex容器，span元素（代表一个点）是Flex项目。如果有多个项目，就要添加多个span元素，以此类推。
<img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1b2eb7e5f5524e5b896bea042fb0c06d~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer">
我们可以看到骰子上最多放置9个点。于是就存在多种布局：👇<br></p>
<p><img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/07fc6be16f924ac7bcac32e86ab87f14~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p>下面我们就来看看各种骰子布局应该怎么写叭~</p>
<h3 data-id="heading-3">单项目</h3>
<blockquote>
<p>首先是一个点在左上角的情况，flex布局默认就是左对齐的，因此一行代码就够了。</p>
</blockquote>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2b85b02f814b4bcab49073c097e11a71~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.box</span>&#123;
    <span class="hljs-attribute">display</span>:flex;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p>水平居中</p>
</blockquote>
<p><img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/bbb57ade7ab44e4e9dc448771318c730~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.box</span>&#123;
    <span class="hljs-attribute">display</span>:flex;
    <span class="hljs-attribute">justify-content</span>:center;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p>右上角</p>
</blockquote>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4a4814996bde457e9a7d57c321a71de8~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.box</span>&#123;
    <span class="hljs-attribute">display</span>:flex;
    <span class="hljs-attribute">justify-content</span>:flex-end;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p>垂直居中靠左</p>
</blockquote>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d5411892db694e4ea7f51cfbe42139c1~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.box</span>&#123;
    <span class="hljs-attribute">display</span>:flex;
    <span class="hljs-attribute">align-items</span>:center;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p>水平垂直居中</p>
</blockquote>
<p><img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/35adbd203c63432ba41793ba66f8d8da~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.box</span>&#123;
    <span class="hljs-attribute">display</span>:flex;
    <span class="hljs-attribute">justify-content</span>:center;
    <span class="hljs-attribute">align-items</span>:center;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p>垂直居中靠右</p>
</blockquote>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/74378ec83ed3458fa450192eafd37d6b~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.box</span>&#123;
    <span class="hljs-attribute">display</span>:flex;
    <span class="hljs-attribute">justify-content</span>:flex-end;
    <span class="hljs-attribute">align-items</span>:center;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p>左下角</p>
</blockquote>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1802064873fd46d4ac96657feea7d784~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.box</span>&#123;
    <span class="hljs-attribute">display</span>:flex;
    <span class="hljs-attribute">align-items</span>:flex-end;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p>水平居中靠下</p>
</blockquote>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/86444b2970444894ad68fcd3407c5161~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.box</span>&#123;
    <span class="hljs-attribute">display</span>:flex;
    <span class="hljs-attribute">justify-content</span>:center;
    <span class="hljs-attribute">align-items</span>:flex-end;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p>右下角</p>
</blockquote>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/cf0b46ece04043408965b75ba25b344a~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.box</span>&#123;
    <span class="hljs-attribute">display</span>:flex;
    <span class="hljs-attribute">justify-content</span>:flex-end;
    <span class="hljs-attribute">align-items</span>:flex-end;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-4">双项目</h3>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/be33f5a690324a32b0d6fb185034e496~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.box</span>&#123;
    <span class="hljs-attribute">display</span>:flex;
    <span class="hljs-attribute">justify-content</span>:space-between;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9f6bc4f53d2945e4aab46e3218b02fcf~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<blockquote>
<p>改变主轴方向即可</p>
</blockquote>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.box</span>&#123;
    <span class="hljs-attribute">display</span>:flex;
    <span class="hljs-attribute">justify-content</span>:space-between;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/aa888ca4eaf947429ce794b205595328~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.box</span>&#123;
    <span class="hljs-attribute">display</span>:flex;
    <span class="hljs-attribute">justify-content</span>:space-between;
    <span class="hljs-attribute">align-items</span>:center;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0969fa64bbbc404f970b7f03ca666893~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.box</span>&#123;
    <span class="hljs-attribute">display</span>:flex;
    <span class="hljs-attribute">justify-content</span>:space-between;
    <span class="hljs-attribute">align-items</span>:flex-end;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5835f861c7434a47b8227c391d8708a7~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.box</span>&#123;
    <span class="hljs-attribute">display</span>:flex;
&#125;
<span class="hljs-selector-class">.item</span><span class="hljs-selector-pseudo">:nth-child</span>(<span class="hljs-number">2</span>)&#123;
    <span class="hljs-attribute">align-self</span>:center;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/977712bf090a42ab8e3296881df8cb74~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.box</span>&#123;
    <span class="hljs-attribute">display</span>:flex;
    <span class="hljs-attribute">justify-content</span>:space-between
&#125;
<span class="hljs-selector-class">.item</span><span class="hljs-selector-pseudo">:nth-child</span>(<span class="hljs-number">2</span>)&#123;
    <span class="hljs-attribute">align-self</span>:flex-end;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-5">三项目</h3>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/fa46840af28440ae935a43934991f5f2~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.box</span>&#123;
    <span class="hljs-attribute">display</span>:flex;
&#125;
<span class="hljs-selector-class">.item</span><span class="hljs-selector-pseudo">:nth-child</span>(<span class="hljs-number">2</span>)&#123;
    <span class="hljs-attribute">align-self</span>:center;
&#125;
<span class="hljs-selector-class">.item</span><span class="hljs-selector-pseudo">:nth-child</span>(<span class="hljs-number">3</span>)&#123;
    <span class="hljs-attribute">align-self</span>:flex-end;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-6">四项目</h3>
<p><img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a238022599ff4917b90aa27649eafcd0~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer">
HTML代码如下：</p>
<pre><code class="hljs language-html copyable" lang="html"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"box"</span>></span>
  <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"column"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">span</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"item"</span>></span><span class="hljs-tag"></<span class="hljs-name">span</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">span</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"item"</span>></span><span class="hljs-tag"></<span class="hljs-name">span</span>></span>
  <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
  <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"column"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">span</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"item"</span>></span><span class="hljs-tag"></<span class="hljs-name">span</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">span</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"item"</span>></span><span class="hljs-tag"></<span class="hljs-name">span</span>></span>
  <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>CSS代码如下：</p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.box</span> &#123;
  <span class="hljs-attribute">display</span>: flex;
  <span class="hljs-attribute">flex-wrap</span>: wrap;
  <span class="hljs-attribute">align-content</span>: space-between;
&#125;

<span class="hljs-selector-class">.column</span> &#123;
  <span class="hljs-attribute">flex-basis</span>: <span class="hljs-number">100%</span>;
  <span class="hljs-attribute">display</span>: flex;
  <span class="hljs-attribute">justify-content</span>: space-between;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h1 data-id="heading-7">最后</h1>
<p>本文总结了Flex布局的实战，通过骰子上的点数布局带你深入理解flex布局的使用~<br>
如果这篇文章对你有帮助的话，麻烦点赞收藏哟~<br>
GitHub 博客地址: <a href="https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fskyblue309" target="_blank" rel="nofollow noopener noreferrer" title="https://github.com/skyblue309" ref="nofollow noopener noreferrer">github.com/skyblue309</a> 。<br>
笔者还有其他专栏，欢迎阅读~<br>
<a href="https://juejin.cn/column/6962133748536049672" target="_blank" title="https://juejin.cn/column/6962133748536049672">Vue从放弃到入门</a><br>
<a href="https://juejin.cn/column/6975658288390078500" target="_blank" title="https://juejin.cn/column/6975658288390078500">深入浅出JavaScript</a><br></p>
<h1 data-id="heading-8">后期更文计划</h1>
<ul>
<li>Grid布局原理及实战</li>
<li>vw和vh布局或许会成为新趋势？</li>
<li>原型及原型链相关内容</li>
</ul></div>  
</div>
            
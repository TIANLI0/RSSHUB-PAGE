
---
title: 'CSS 实现水平垂直居中的总结'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=2195'
author: 掘金
comments: false
date: Thu, 15 Jul 2021 04:38:57 GMT
thumbnail: 'https://picsum.photos/400/300?random=2195'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h1 data-id="heading-0">一. 水平垂直居中</h1>
<h2 data-id="heading-1">1. 绝对定位 + 负margin</h2>
<p><em>HTML</em></p>
<pre><code class="hljs language-html copyable" lang="html"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"parent"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"child"</span>></span>一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><em>CSS</em></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.parent</span> &#123;
  <span class="hljs-attribute">height</span>: <span class="hljs-number">500px</span>;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">1px</span> solid red;
  <span class="hljs-attribute">position</span>: relative;
&#125;
<span class="hljs-selector-class">.child</span> &#123;
  <span class="hljs-attribute">width</span>: <span class="hljs-number">300px</span>;
  <span class="hljs-attribute">height</span>: <span class="hljs-number">100px</span>;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">1px</span> solid green;
  <span class="hljs-attribute">position</span>: absolute;
  <span class="hljs-attribute">top</span>: <span class="hljs-number">50%</span>;
  <span class="hljs-attribute">left</span>: <span class="hljs-number">50%</span>;
  <span class="hljs-attribute">margin-left</span>: -<span class="hljs-number">150px</span>;  <span class="hljs-comment">/* 宽度的-50% */</span>
  <span class="hljs-attribute">margin-top</span>: -<span class="hljs-number">50px</span>;    <span class="hljs-comment">/* 高度的-50% */</span>
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>缺点：需要固定居中元素的宽高。</p>
<h2 data-id="heading-2">2. 绝对定位 + margin: auto</h2>
<p><em>HTML</em></p>
<pre><code class="hljs language-html copyable" lang="html"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"parent"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"child"</span>></span>一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><em>CSS</em></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.parent</span> &#123;
  <span class="hljs-attribute">height</span>: <span class="hljs-number">500px</span>;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">1px</span> solid red;
  <span class="hljs-attribute">position</span>: relative;
&#125;
<span class="hljs-selector-class">.child</span> &#123;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">1px</span> solid green;
  <span class="hljs-attribute">width</span>: <span class="hljs-number">300px</span>;
  <span class="hljs-attribute">height</span>: <span class="hljs-number">200px</span>;
  <span class="hljs-attribute">position</span>: absolute;
  <span class="hljs-attribute">top</span>: <span class="hljs-number">0</span>;
  <span class="hljs-attribute">bottom</span>: <span class="hljs-number">0</span>;
  <span class="hljs-attribute">left</span>: <span class="hljs-number">0</span>;
  <span class="hljs-attribute">right</span>: <span class="hljs-number">0</span>;
  <span class="hljs-attribute">margin</span>: auto;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>缺点：需要固定居中元素的宽高，否则其宽高会被设为100%</p>
<h2 data-id="heading-3">3. 绝对定位 + translate</h2>
<p><em>HTML</em></p>
<pre><code class="hljs language-html copyable" lang="html"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"parent"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"child"</span>></span>一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><em>CSS</em></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.parent</span> &#123;
  <span class="hljs-attribute">height</span>: <span class="hljs-number">500px</span>;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">1px</span> solid red;
  <span class="hljs-attribute">position</span>: relative;
&#125;
<span class="hljs-selector-class">.child</span> &#123;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">1px</span> solid green;
  <span class="hljs-attribute">position</span>: absolute;
  <span class="hljs-attribute">top</span>: <span class="hljs-number">50%</span>;
  <span class="hljs-attribute">left</span>: <span class="hljs-number">50%</span>;
  <span class="hljs-attribute">transform</span>: <span class="hljs-built_in">translate</span>(-<span class="hljs-number">50%</span>, -<span class="hljs-number">50%</span>);
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>优点：不需要固定居中元素的宽高。</p>
<h2 data-id="heading-4">4. flex 布局</h2>
<p><em>HTML</em></p>
<pre><code class="hljs language-html copyable" lang="html"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"parent"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"child"</span>></span>一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><em>CSS</em></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.parent</span> &#123;
  <span class="hljs-attribute">height</span>: <span class="hljs-number">500px</span>;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">1px</span> solid red;
  <span class="hljs-attribute">display</span>: flex;
  <span class="hljs-attribute">justify-content</span>: center;  <span class="hljs-comment">/* 水平居中 */</span>
  <span class="hljs-attribute">align-items</span>: center;      <span class="hljs-comment">/* 垂直居中 */</span>
&#125;
<span class="hljs-selector-class">.child</span> &#123;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">1px</span> solid green;
  <span class="hljs-attribute">width</span>: <span class="hljs-number">300px</span>;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>优点：不需要固定居中元素的宽高。</p>
<p>兼容性：目前移动端已经完全可以使用 Flex 布局，而 PC 端某些旧浏览器支持度不高。</p>
<h2 data-id="heading-5">5. 单行文本的水平垂直居中</h2>
<p><em>HTML</em></p>
<pre><code class="hljs language-html copyable" lang="html"><span class="hljs-tag"><<span class="hljs-name">p</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"content"</span>></span>
    单行文本单行文本单行文本
<span class="hljs-tag"></<span class="hljs-name">p</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><em>CSS</em></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.content</span> &#123;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">3px</span> solid red;
  <span class="hljs-attribute">line-height</span>:<span class="hljs-number">300px</span>;
  <span class="hljs-attribute">text-align</span>:center;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h1 data-id="heading-6">二. 水平居中</h1>
<h2 data-id="heading-7">1. margin auto</h2>
<p><em>HTML</em></p>
<pre><code class="hljs language-html copyable" lang="html"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"parent"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"child"</span>></span>一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><em>CSS</em></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.parent</span> &#123;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">3px</span> solid red;
&#125;
<span class="hljs-selector-class">.child</span> &#123;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">3px</span> solid blue;
  <span class="hljs-attribute">width</span>: <span class="hljs-number">300px</span>;
  <span class="hljs-attribute">margin</span>: <span class="hljs-number">0</span> auto;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>缺点：需要固定居中元素的宽。</p>
<h2 data-id="heading-8">2. text-align + inline-block</h2>
<p><em>HTML</em></p>
<pre><code class="hljs language-html copyable" lang="html"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"parent"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"child"</span>></span>一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><em>CSS</em></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.parent</span> &#123;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">3px</span> solid red;
  <span class="hljs-attribute">text-align</span>: center;
&#125;
<span class="hljs-selector-class">.child</span> &#123;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">3px</span> solid blue;
  <span class="hljs-attribute">width</span>: <span class="hljs-number">300px</span>;
  <span class="hljs-attribute">display</span>: inline-block;
  <span class="hljs-attribute">text-align</span><span class="hljs-selector-pseudo">:left</span>;  <span class="hljs-comment">/* 重置文本位置 */</span>
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>缺点：为了居中元素，文本也跟着居中了，因此可能需要重置文本位置。</p>
<h1 data-id="heading-9">三. 垂直居中</h1>
<h2 data-id="heading-10">1. table 自带功能</h2>
<p><em>HTML</em></p>
<pre><code class="hljs language-html copyable" lang="html"><span class="hljs-tag"><<span class="hljs-name">table</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"parent"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">tr</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">td</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"child"</span>></span>
        一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字
      <span class="hljs-tag"></<span class="hljs-name">td</span>></span>
    <span class="hljs-tag"></<span class="hljs-name">tr</span>></span>
<span class="hljs-tag"></<span class="hljs-name">table</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><em>CSS</em></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.parent</span> &#123;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">1px</span> solid red;
  <span class="hljs-attribute">height</span>: <span class="hljs-number">600px</span>;
&#125;
<span class="hljs-selector-class">.child</span> &#123;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">1px</span> solid green;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-11">2. div 伪装成 table</h2>
<p><em>HTML</em></p>
<pre><code class="hljs language-html copyable" lang="html"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"table"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"td"</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"child"</span>></span>一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
    <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><em>CSS</em></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-tag">div</span><span class="hljs-selector-class">.table</span> &#123;
  <span class="hljs-attribute">display</span>: table;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">1px</span> solid red;
  <span class="hljs-attribute">height</span>: <span class="hljs-number">500px</span>;
&#125;
<span class="hljs-selector-tag">div</span><span class="hljs-selector-class">.tr</span> &#123;
  <span class="hljs-attribute">display</span>: table-row;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">1px</span> solid green;
&#125;
<span class="hljs-selector-tag">div</span><span class="hljs-selector-class">.td</span> &#123;
  <span class="hljs-attribute">display</span>: table-cell;
  <span class="hljs-attribute">vertical-align</span>: middle;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">1px</span> solid blue;
&#125;
<span class="hljs-selector-class">.child</span> &#123;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">3px</span> solid black;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-12">3. 100% 高度的 after before 加上 inline-block</h2>
<p><em>HTML</em></p>
<pre><code class="hljs language-html copyable" lang="html"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"parent"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"child"</span>></span>一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字一段文字<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><em>CSS</em></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-class">.parent</span> &#123;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">3px</span> solid red;
  <span class="hljs-attribute">height</span>: <span class="hljs-number">500px</span>;
  <span class="hljs-attribute">text-align</span>: center;
&#125;
<span class="hljs-selector-class">.child</span> &#123;
  <span class="hljs-attribute">border</span>: <span class="hljs-number">3px</span> solid black;
  <span class="hljs-attribute">display</span>: inline-block;
  <span class="hljs-attribute">width</span>: <span class="hljs-number">300px</span>;
  <span class="hljs-attribute">vertical-align</span>: middle;
&#125;
<span class="hljs-selector-class">.parent</span><span class="hljs-selector-pseudo">::before</span> &#123;
  <span class="hljs-attribute">content</span>: <span class="hljs-string">''</span>;
  <span class="hljs-attribute">outline</span>: <span class="hljs-number">3px</span> solid red;
  <span class="hljs-attribute">display</span>: inline-block;
  <span class="hljs-attribute">height</span>: <span class="hljs-number">100%</span>;
  <span class="hljs-attribute">vertical-align</span>: middle;
&#125;
<span class="hljs-selector-class">.parent</span><span class="hljs-selector-pseudo">::after</span> &#123;
  <span class="hljs-attribute">content</span>: <span class="hljs-string">''</span>;
  <span class="hljs-attribute">outline</span>: <span class="hljs-number">3px</span> solid red;
  <span class="hljs-attribute">display</span>: inline-block;
  <span class="hljs-attribute">height</span>: <span class="hljs-number">100%</span>;
  <span class="hljs-attribute">vertical-align</span>: middle;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre></div>  
</div>
            
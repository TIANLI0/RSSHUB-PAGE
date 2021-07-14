
---
title: 'Canvas 入门指南（二） — 如何使用 canvas 画一个滑稽'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=1946'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 01:07:21 GMT
thumbnail: 'https://picsum.photos/400/300?random=1946'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><p>前情提要：<a href="https://juejin.cn/post/6963197337350963230" target="_blank" title="https://juejin.cn/post/6963197337350963230">Canvas 入门指南</a></p>
<p>最后效果图：</p>
<p>![CleanShot 2021-07-14 at 16.01.37](./material/yide-canvas/CleanShot 2021-07-14 at 16.01.37-6249726.png)</p>
<h2 data-id="heading-0">教程</h2>
<ol>
<li>获取 canvas 对象</li>
<li>获取 context 对象</li>
<li>加一点点细节</li>
<li>大功告成</li>
</ol>
<p>分析一下上图，基本都是圆弧。设置几个同心圆以及拼接几段圆弧即可本画。</p>
<h3 data-id="heading-1">大体轮廓</h3>
<ol>
<li>首先设置填充颜色，通过取色可以了解到填充颜色为 <code>rgb(241, 201, 96)</code></li>
<li>画一个完整的圆形</li>
</ol>
<pre><code class="hljs language-js copyable" lang="js">context.fillStyle = <span class="hljs-string">'rgb(241, 201, 96)'</span>;
context.arc(<span class="hljs-number">100</span>, <span class="hljs-number">100</span>, <span class="hljs-number">50</span>, <span class="hljs-number">0</span>, <span class="hljs-number">2</span> * <span class="hljs-built_in">Math</span>.PI, <span class="hljs-literal">true</span>);
context.fill();
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-2">嘴巴</h3>
<ol>
<li>画一个半圆，特点是与轮廓成一个同心圆</li>
</ol>
<pre><code class="hljs language-js copyable" lang="js">context.lineWidth = <span class="hljs-number">2</span>;
context.arc(<span class="hljs-number">100</span>, <span class="hljs-number">100</span>, <span class="hljs-number">40</span>, <span class="hljs-number">0</span>, <span class="hljs-built_in">Math</span>.PI, <span class="hljs-literal">false</span>);
context.stroke();
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-3">眼睛轮廓</h3>
<p>眼睛轮廓会比较麻烦，分为左眼以及右眼</p>
<p>两个眼睛主题部分都是由两个同心圆组成</p>
<p>左眼</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">// 左眼</span>
context.beginPath();
context.arc(<span class="hljs-number">75</span>, <span class="hljs-number">90</span>, <span class="hljs-number">20</span>, <span class="hljs-built_in">Math</span>.PI * <span class="hljs-number">1.1</span>, <span class="hljs-built_in">Math</span>.PI * <span class="hljs-number">1.9</span>, <span class="hljs-literal">false</span>);
context.stroke();

context.beginPath();
context.arc(<span class="hljs-number">75</span>, <span class="hljs-number">90</span>, <span class="hljs-number">10</span>, <span class="hljs-built_in">Math</span>.PI * <span class="hljs-number">1.1</span>, <span class="hljs-built_in">Math</span>.PI * <span class="hljs-number">1.9</span>, <span class="hljs-literal">false</span>); 
context.stroke();

context.beginPath();
context.arc(<span class="hljs-number">60</span>, <span class="hljs-number">85</span>, <span class="hljs-number">5</span>, <span class="hljs-built_in">Math</span>.PI, <span class="hljs-built_in">Math</span>.PI * <span class="hljs-number">2</span>, <span class="hljs-literal">true</span>); <span class="hljs-comment">// 左眼左连接处</span>
context.stroke();

context.beginPath();
context.arc(<span class="hljs-number">90</span>, <span class="hljs-number">85</span>, <span class="hljs-number">5</span>, <span class="hljs-built_in">Math</span>.PI, <span class="hljs-built_in">Math</span>.PI * <span class="hljs-number">2</span>, <span class="hljs-literal">true</span>); <span class="hljs-comment">// 左眼 右连接处</span>
context.stroke();
<span class="copy-code-btn">复制代码</span></code></pre>
<p>右眼：</p>
<pre><code class="hljs language-js copyable" lang="js">context.beginPath();
context.arc(<span class="hljs-number">125</span>, <span class="hljs-number">90</span>, <span class="hljs-number">20</span>, <span class="hljs-built_in">Math</span>.PI * <span class="hljs-number">1.1</span>, <span class="hljs-built_in">Math</span>.PI * <span class="hljs-number">1.9</span>, <span class="hljs-literal">false</span>);
context.stroke();

context.beginPath();
context.arc(<span class="hljs-number">125</span>, <span class="hljs-number">90</span>, <span class="hljs-number">10</span>, <span class="hljs-built_in">Math</span>.PI * <span class="hljs-number">1.1</span>, <span class="hljs-built_in">Math</span>.PI * <span class="hljs-number">1.9</span>, <span class="hljs-literal">false</span>);
context.stroke();

context.beginPath();
context.arc(<span class="hljs-number">110</span>, <span class="hljs-number">85</span>, <span class="hljs-number">5</span>, <span class="hljs-built_in">Math</span>.PI, <span class="hljs-built_in">Math</span>.PI * <span class="hljs-number">2</span>, <span class="hljs-literal">true</span>); <span class="hljs-comment">// 右眼左连接处</span>
context.stroke();

context.beginPath();
context.arc(<span class="hljs-number">140</span>, <span class="hljs-number">85</span>, <span class="hljs-number">5</span>, <span class="hljs-built_in">Math</span>.PI, <span class="hljs-built_in">Math</span>.PI * <span class="hljs-number">2</span>, <span class="hljs-literal">true</span>); <span class="hljs-comment">// 右眼右连接处</span>
context.stroke();
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-4">眼球</h3>
<p>眼球是最后一步，只是一个填充的圆形而已</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">// 右眼球</span>
context.fillStyle = <span class="hljs-string">'black'</span>;
context.beginPath();
context.arc(<span class="hljs-number">115</span>, <span class="hljs-number">80</span>, <span class="hljs-number">5</span>, <span class="hljs-number">0</span>, <span class="hljs-built_in">Math</span>.PI * <span class="hljs-number">2</span>, <span class="hljs-literal">false</span>);
context.fill();

<span class="hljs-comment">// 左眼球</span>
context.fillStyle = <span class="hljs-string">'black'</span>;
context.beginPath();
context.arc(<span class="hljs-number">65</span>, <span class="hljs-number">80</span>, <span class="hljs-number">5</span>, <span class="hljs-number">0</span>, <span class="hljs-built_in">Math</span>.PI * <span class="hljs-number">2</span>, <span class="hljs-literal">false</span>);
context.fill();
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-5">小结</h2>
<p>总体来说，这个<strong>滑稽</strong>比较简单。也有可以优化的地方，比如使用 Path2D 来保存信息再次利用。
<br>
<br></p>
<p><em><strong>PS:大家看了后觉得对自己有帮助可以三连留言,欢迎提出宝贵意见，也欢迎各位对相关技术有兴趣的开发者（由团队开发人员微信号x118422邀请）入群，在线解答讨论数据可视化、优化图表性能等方面的技术问题~</strong></em></p></div>  
</div>
            
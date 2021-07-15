
---
title: 'Unity 不能在节点隐藏的时候更改子节点的父对象'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=9585'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 02:29:29 GMT
thumbnail: 'https://picsum.photos/400/300?random=9585'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h2 data-id="heading-0">描述</h2>
<p>在 Unity 中使用物体池，在父节点进行隐藏的时候，把子物体回归到池里，即重设父对象，但此时 Unity 会报错：</p>
<blockquote>
<p>Cannot set the parent of the GameObject 'show_(Clone)' while
activating or deactivating the parent GameObject 'db'.</p>
<p>UnityEngine.Transform:SetParent(Transform, Boolean)</p>
</blockquote>
<h2 data-id="heading-1">原因</h2>
<p>正如提示的，Unity 限制了在显示或隐藏的时候，对子节点进行更改父对象操作。</p>
<h2 data-id="heading-2">解决</h2>
<p>经过尝试，虽然限制了子节点的操作，但是不限制子节点的子节点，即在中间增加一个空物体来隔离，这里就可以放到池里。</p>
<p>当需要使用时，判断有没有中间物体存在，若无则先创建：</p>
<pre><code class="hljs language-csharp copyable" lang="csharp">    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-built_in">bool</span> <span class="hljs-title">ShowLive</span>(<span class="hljs-params"><span class="hljs-built_in">string</span> livePath</span>)</span>
    &#123;
        <span class="hljs-keyword">if</span> (!m_Transform)
        &#123;
            <span class="hljs-comment">// 因为不能在禁用的时候，放回池里，所以只能通过中间空节点</span>
            <span class="hljs-keyword">var</span> go = <span class="hljs-keyword">new</span> GameObject();
            m_Transform = go.transform;
            m_Transform.SetParent(transform, <span class="hljs-literal">false</span>);
        &#125;
        
        <span class="hljs-keyword">return</span> <span class="hljs-literal">true</span>;
    &#125;
<span class="copy-code-btn">复制代码</span></code></pre></div>  
</div>
            
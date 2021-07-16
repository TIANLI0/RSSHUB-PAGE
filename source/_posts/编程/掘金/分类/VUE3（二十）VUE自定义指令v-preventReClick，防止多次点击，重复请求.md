
---
title: 'VUE3（二十）VUE自定义指令v-preventReClick，防止多次点击，重复请求'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/cdce9dd114a04eb7950bcd093bc74b20~tplv-k3u1fbpfcp-zoom-1.image'
author: 掘金
comments: false
date: Thu, 15 Jul 2021 18:35:09 GMT
thumbnail: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/cdce9dd114a04eb7950bcd093bc74b20~tplv-k3u1fbpfcp-zoom-1.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><p>VUE不仅为我们提供了自定义组件，还提供了自定义指令。当然，这个玩意我在VUE2中是没有用到过的。</p>
<p>VUE3中我大概试一下这个自定义指令：</p>
<p>官方文档：</p>
<p><a href="https://link.juejin.cn/?target=https%3A%2F%2Fvue3js.cn%2Fdocs%2Fzh%2Fguide%2Fcustom-directive.html%23%25E5%258A%25A8%25E6%2580%2581%25E6%258C%2587%25E4%25BB%25A4%25E5%258F%2582%25E6%2595%25B0" target="_blank" rel="nofollow noopener noreferrer" title="https://vue3js.cn/docs/zh/guide/custom-directive.html#%E5%8A%A8%E6%80%81%E6%8C%87%E4%BB%A4%E5%8F%82%E6%95%B0" ref="nofollow noopener noreferrer">vue3js.cn/docs/zh/gui…</a></p>
<h3 data-id="heading-0">一：注册全局指令</h3>
<p>在main.ts中加入如下配置：</p>
<pre><code class="hljs language-typescript copyable" lang="typescript"><span class="hljs-comment">// =======================================================</span>
<span class="hljs-comment">// 注册一个全局自定义指令 `v-focus`</span>
app.directive(<span class="hljs-string">'console'</span>, &#123;
    <span class="hljs-comment">// 当被绑定的元素插入到 DOM 中时……</span>
    <span class="hljs-function"><span class="hljs-title">mounted</span>(<span class="hljs-params">el</span>)</span> &#123;
        <span class="hljs-comment">// Focus the element</span>
        <span class="hljs-comment">// el.focus()</span>
        <span class="hljs-built_in">console</span>.log(<span class="hljs-string">'自定义全局指令v-console 注册成功'</span>);
    &#125;
&#125;)
 
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-1">二：注册局部指令</h3>
<p>在某个页面的js中：</p>
<pre><code class="hljs language-typescript copyable" lang="typescript"> name: <span class="hljs-string">"index"</span>,
    <span class="hljs-attr">components</span>: &#123;&#125;,
    <span class="hljs-comment">/**
     * <span class="hljs-doctag">@name</span>: 自定义指令（局部注册）
     * <span class="hljs-doctag">@author</span>: camellia
     * <span class="hljs-doctag">@email</span>: guanchao_gc<span class="hljs-doctag">@qq</span>.com
     * <span class="hljs-doctag">@date</span>: 2021-02-25 
     */</span>
    <span class="hljs-attr">directives</span>: &#123;
        <span class="hljs-comment">// v-part</span>
        <span class="hljs-attr">part</span>: &#123;
            <span class="hljs-comment">// 指令的定义</span>
            <span class="hljs-function"><span class="hljs-title">mounted</span>(<span class="hljs-params">el: <span class="hljs-built_in">any</span></span>)</span> &#123;
                <span class="hljs-comment">// el.focus()</span>
                <span class="hljs-built_in">console</span>.log(el);
                <span class="hljs-built_in">console</span>.log(<span class="hljs-string">'自定义局部指令注册成功！'</span>);
            &#125;
        &#125;
    &#125;,
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-2">三：v-preventReClick，防止多次点击，重复请求</h3>
<pre><code class="hljs language-typescript copyable" lang="typescript">name: <span class="hljs-string">"index"</span>,
    <span class="hljs-attr">components</span>: &#123; &#125;,
    <span class="hljs-comment">/**
     * <span class="hljs-doctag">@name</span>: 自定义指令（局部注册）
     * <span class="hljs-doctag">@author</span>: camellia
     * <span class="hljs-doctag">@email</span>: guanchao_gc<span class="hljs-doctag">@qq</span>.com
     * <span class="hljs-doctag">@date</span>: 2021-02-25 
     */</span>
    <span class="hljs-attr">directives</span>: &#123;
        <span class="hljs-comment">// v-part</span>
        <span class="hljs-attr">preventReClick</span>: &#123;
            <span class="hljs-comment">// 指令的定义</span>
            <span class="hljs-function"><span class="hljs-title">mounted</span>(<span class="hljs-params">el: <span class="hljs-built_in">any</span>, binding:<span class="hljs-built_in">any</span></span>)</span> &#123;
                <span class="hljs-comment">// el.focus()</span>
                <span class="hljs-built_in">console</span>.log(el);
                <span class="hljs-built_in">console</span>.log(binding);
                <span class="hljs-comment">// console.log('自定义局部指令注册成功！');</span>
                el.addEventListener(<span class="hljs-string">'click'</span>, <span class="hljs-function">() =></span> &#123;
                    <span class="hljs-keyword">if</span> (!el.disabled) &#123;
                        <span class="hljs-built_in">console</span>.log(<span class="hljs-number">123</span>);
                        el.disabled = <span class="hljs-literal">true</span>;
                        <span class="hljs-built_in">setTimeout</span>(<span class="hljs-function">() =></span> &#123;
                            el.disabled = <span class="hljs-literal">false</span>;
                        &#125;, binding.value || <span class="hljs-number">300</span>);
                    &#125;
                &#125;);
            &#125;
        &#125;
    &#125;,
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-3">四：调用方式</h3>
<pre><code class="hljs language-typescript copyable" lang="typescript"><button <span class="hljs-meta">@click</span>=<span class="hljs-string">"handle"</span> v-preventReClick>提交</button>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>以上大概就是VUE3中自定义指令的大概使用。</p>
<p>有好的建议，请在下方输入你的评论。
欢迎访问个人博客
<a href="https://link.juejin.cn/?target=https%3A%2F%2Fguanchao.site" target="_blank" rel="nofollow noopener noreferrer" title="https://guanchao.site" ref="nofollow noopener noreferrer">guanchao.site</a></p>
<p>欢迎访问小程序：</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/cdce9dd114a04eb7950bcd093bc74b20~tplv-k3u1fbpfcp-zoom-1.image" alt="在这里插入图片描述" loading="lazy" referrerpolicy="no-referrer"></p></div>  
</div>
            
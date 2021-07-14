
---
title: '_动态界面 json2render_ 动态表单中使用自定义容器组件'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8144e56398304afd873362a7618d16f5~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Tue, 13 Jul 2021 05:11:04 GMT
thumbnail: 'https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8144e56398304afd873362a7618d16f5~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;color:#595959;font-size:15px;font-family:-apple-system,system-ui,BlinkMacSystemFont,Helvetica Neue,PingFang SC,Hiragino Sans GB,Microsoft YaHei,Arial,sans-serif;background-image:linear-gradient(90deg,rgba(60,10,30,.04) 3%,transparent 0),linear-gradient(1turn,rgba(60,10,30,.04) 3%,transparent 0);background-size:20px 20px;background-position:50%&#125;.markdown-body p&#123;color:#595959;font-size:15px;line-height:2;font-weight:400&#125;.markdown-body p+p&#123;margin-top:16px&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;padding:30px 0;margin:0;color:#135ce0&#125;.markdown-body h1&#123;position:relative;text-align:center;font-size:22px;margin:50px 0&#125;.markdown-body h1:before&#123;position:absolute;content:"";top:-10px;left:50%;width:32px;height:32px;transform:translateX(-50%);background-size:100% 100%;opacity:.36;background-repeat:no-repeat;background:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAABGdBTUEAALGPC/xhBQAAACBjSFJNAAB6JgAAgIQAAPoAAACA6AAAdTAAAOpgAAA6mAAAF3CculE8AAABfVBMVEX///8Ad/8AgP8AgP8AgP8Aff8AgP8Af/8AgP8AVf8Af/8Af/8AgP8AgP8Af/8Afv8AAP8Afv8Afv8Aef8AgP8AdP8Afv8AgP8AgP8Acf8Ae/8AgP8Af/8AgP8Af/8Af/8AfP8Afv8AgP8Af/8Af/8Afv8Afv8AgP8Afv8AgP8Af/8Af/8AgP8AgP8Afv8AgP8Af/8AgP8AgP8AgP8Ae/8Afv8Af/8AgP8Af/8AgP8Af/8Af/8Aff8Af/8Abf8AgP8Af/8AgP8Af/8Af/8Afv8AgP8AgP8Afv8Afv8AgP8Af/8Aff8AgP8Afv8AgP8Aff8AgP8AfP8AgP8Ae/8AgP8Af/8AgP8AgP8AgP8Afv8AgP8AgP8AgP8Afv8AgP8AgP8AgP8AgP8AgP8Af/8AgP8Af/8Af/8Aev8Af/8AgP8Aff8Afv8AgP8AgP8AgP8Af/8AgP8Af/8Af/8AgP8Afv8AgP8AgP8AgP8AgP8Af/8AeP8Af/8Af/8Af//////rzEHnAAAAfXRSTlMAD7CCAivatxIDx5EMrP19AXdLEwgLR+6iCR/M0yLRzyFF7JupSXn8cw6v60Q0QeqzKtgeG237HMne850/6Qeq7QaZ+WdydHtj+OM3qENCMRYl1B3K2U7wnlWE/mhlirjkODa9FN/BF7/iNV/2kASNZpX1Wlf03C4stRGxgUPclqoAAAABYktHRACIBR1IAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAB3RJTUUH4gEaBzgZ4yeM3AAAAT9JREFUOMvNUldbwkAQvCAqsSBoABE7asSOBRUVVBQNNuy9996789+9cMFAMHnVebmdm+/bmdtbQv4dOFOW2UjPzgFyLfo6nweKfIMOBYWwFtmMPGz2Yj2pJI0JDq3udJW6VVbmKa9I192VQFV1ktXUAl5NB0cd4KpnORqsEO2ZIRpF9gJfE9Dckqq0KuZt7UAH5+8EPF3spjsRpCeQNO/tA/qDwIDA+OCQbBoKA8NOdjMySgcZGVM6jwcgRuUiSs0nlPFNSrEpJfU0jTLD6llqbvKxei7OzvkFNQohi0vAsj81+MoqsCaoPOQFgus/1LyxichW+hS2JWCHZ7VlF9jb187pIAYcHiViHAMnp5mTjJ8B5xeEXF4B1ze/fTh/C0h398DDI9HB07O8ci+vRBdvdGnfP4gBuM8vw7X/G3wDmFhFZEdxzjMAAAAldEVYdGRhdGU6Y3JlYXRlADIwMTgtMDEtMjZUMDc6NTY6MjUrMDE6MDA67pVWAAAAJXRFWHRkYXRlOm1vZGlmeQAyMDE4LTAxLTI2VDA3OjU2OjI1KzAxOjAwS7Mt6gAAABl0RVh0U29mdHdhcmUAd3d3Lmlua3NjYXBlLm9yZ5vuPBoAAAAWdEVYdFRpdGxlAGp1ZWppbl9sb2dvIGNvcHlxapmKAAAAV3pUWHRSYXcgcHJvZmlsZSB0eXBlIGlwdGMAAHic4/IMCHFWKCjKT8vMSeVSAAMjCy5jCxMjE0uTFAMTIESANMNkAyOzVCDL2NTIxMzEHMQHy4BIoEouAOoXEXTyQjWVAAAAAElFTkSuQmCC)&#125;.markdown-body h2&#123;position:relative;font-size:20px;border-left:4px solid;padding:0 0 0 10px;margin:30px 0&#125;.markdown-body h3&#123;font-size:16px&#125;.markdown-body ul&#123;list-style:disc outside;margin-left:2em;margin-top:1em&#125;.markdown-body li&#123;line-height:2;color:#595959&#125;.markdown-body img.loaded&#123;margin:0 auto;display:block&#125;.markdown-body blockquote&#123;background:#fff9f9;margin:2em 0;padding:2px 20px;border-left:4px solid #b2aec5&#125;.markdown-body blockquote p&#123;color:#666;line-height:2&#125;.markdown-body a&#123;color:#036aca;border-bottom:1px solid rgba(3,106,202,.8);font-weight:400;text-decoration:none&#125;.markdown-body em strong,.markdown-body strong&#123;color:#036aca&#125;.markdown-body hr&#123;border-top:1px solid #135ce0&#125;.markdown-body pre&#123;overflow:auto&#125;.markdown-body code,.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body table&#123;border-collapse:collapse;margin:1rem 0;overflow-x:auto&#125;.markdown-body table td,.markdown-body table th&#123;border:1px solid #dfe2e5;padding:.6em 1em&#125;.markdown-body table tr&#123;border-top:1px solid #dfe2e5&#125;.markdown-body table tr:nth-child(2n)&#123;background-color:#f6f8fa&#125;</style><h2 data-id="heading-0">需求</h2>
<p>上次碰到一个需求要求动态表单配置中加载另一个动态表单配置的组件，利用 <code>json2render</code> 已经能实现这个功能，具体实现 <a href="https://juejin.cn/post/6979885639319683086" target="_blank" title="https://juejin.cn/post/6979885639319683086">[动态界面 json2render] 动态界面中加载自定义模板组件</a></p>
<p>这次需求又升级了，要求动态配置的组件具有容器 slot 特性，内部还可以放组件进去，就是需要定义多个 slot 后在引用组件时候将 children 组件放到对应 slot 里，需求主要是解决能通过配置定义具有内部布局的自定义组件，实现只提供几种简单的布局组件配合样式就能创建多种风格的组件</p>
<p>上一个版本的 <code>json2render</code> 还不支持这个特性，这个功能后来也加上了</p>
<h2 data-id="heading-1">效果</h2>
<p>先看下最后要达到的效果，本示例基于 Vue3</p>
<p>动态组件的配置定义如下</p>
<pre><code class="hljs language-json copyable" lang="json">&#123;
  <span class="hljs-attr">"fields"</span>: [
    &#123;
      <span class="hljs-attr">"component"</span>: <span class="hljs-string">"h1"</span>,
      <span class="hljs-attr">"props"</span>: &#123;
        <span class="hljs-attr">"style"</span>: &#123; <span class="hljs-attr">"fontSize"</span>: <span class="hljs-string">"40pt"</span> &#125;
      &#125;,
      <span class="hljs-attr">"children"</span>: [
        &#123; <span class="hljs-attr">"component"</span>: <span class="hljs-string">"span"</span>, <span class="hljs-attr">"text"</span>: <span class="hljs-string">"标题: "</span> &#125;,
        <span class="hljs-comment">// 具有命名的 slot</span>
        &#123; <span class="hljs-attr">"component"</span>: <span class="hljs-string">"slot"</span>, <span class="hljs-attr">"name"</span>: <span class="hljs-string">"header"</span> &#125;
      ]
    &#125;,
    &#123; <span class="hljs-attr">"component"</span>: <span class="hljs-string">"p"</span>, <span class="hljs-attr">"text"</span>: <span class="hljs-string">"正文"</span> &#125;,
    <span class="hljs-comment">// 默认的 slot，并将 props 传递给 scope 给 children 用</span>
    &#123; <span class="hljs-attr">"component"</span>: <span class="hljs-string">"slot"</span>, <span class="hljs-attr">"props"</span>: &#123; <span class="hljs-attr">"attrValue"</span>: <span class="hljs-string">"aaaaa"</span> &#125; &#125;
  ]
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>引用动态组件，并在内部对应 slot 显示内容</p>
<pre><code class="hljs language-json copyable" lang="json">&#123;
  <span class="hljs-attr">"datasource"</span>: &#123;
    <span class="hljs-comment">// 用于远程加载动态组件的数据源，自动加载</span>
    <span class="hljs-attr">"template"</span>: &#123;
      <span class="hljs-attr">"type"</span>: <span class="hljs-string">"fetch"</span>,
      <span class="hljs-attr">"url"</span>: <span class="hljs-string">"/data/components/slotcmp.json"</span>,
      <span class="hljs-attr">"auto"</span>: <span class="hljs-literal">true</span>,
      <span class="hljs-attr">"props"</span>: &#123; <span class="hljs-attr">"method"</span>: <span class="hljs-string">"GET"</span>, <span class="hljs-attr">"params"</span>: &#123;&#125; &#125;,
      <span class="hljs-attr">"defaultData"</span>: <span class="hljs-literal">false</span>
    &#125;
  &#125;,
  <span class="hljs-attr">"fields"</span>: [
    &#123;
      <span class="hljs-attr">"component"</span>: <span class="hljs-string">"div"</span>,
      <span class="hljs-attr">"children"</span>: [
        &#123;
          <span class="hljs-attr">"component"</span>: <span class="hljs-string">"v-jrender"</span>,
          <span class="hljs-attr">"condition"</span>: <span class="hljs-string">"$:template.data"</span>,
          <span class="hljs-attr">"props"</span>: <span class="hljs-string">"$:template.data"</span>,
          <span class="hljs-comment">// v-jrender 之前不支持设置 children，现在提供支持</span>
          <span class="hljs-attr">"children"</span>: &#123;
            <span class="hljs-comment">// 默认 slot</span>
            <span class="hljs-attr">"default"</span>: [
              <span class="hljs-comment">// 利用转换表达式获取父级传过来的 scope 里 attrValue 属性值</span>
              &#123; <span class="hljs-attr">"component"</span>: <span class="hljs-string">"span"</span>, <span class="hljs-attr">"text"</span>: <span class="hljs-string">"#:inner text $&#123;scope.attrValue&#125;"</span> &#125;
            ],
            <span class="hljs-comment">// 命名 slot</span>
            <span class="hljs-attr">"header"</span>: [&#123; <span class="hljs-attr">"component"</span>: <span class="hljs-string">"span"</span>, <span class="hljs-attr">"text"</span>: <span class="hljs-string">"标题slot内容"</span> &#125;]
          &#125;
        &#125;
      ]
    &#125;
  ]
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>最后效果如下</p>
<p><img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8144e56398304afd873362a7618d16f5~tplv-k3u1fbpfcp-watermark.image" alt="008i3skNly1gsfj8yuzmxj30w60dg3zx.jpeg" loading="lazy" referrerpolicy="no-referrer"></p>
<p>如果直接使用 <code>v-jrender</code> 组件，而配置里包含有 component 是 slot 的节点也可直接在 <code>v-jrender</code> 的 children 加入内容</p>
<pre><code class="hljs language-vue copyable" lang="vue"><script setup>
import &#123; ref &#125; from 'vue'

const fields = ref([&#123;
    component: 'div',
    children: [&#123;
        component: 'slot'
    &#125;]
&#125;])
</script>
<template>
    <v-jrender :fields="fields">
        <!-- slot 处渲染的内容 -->
        <div>content</div>
    </v-jrender>
<template>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-2">原理</h2>
<h3 data-id="heading-3">插槽概念</h3>
<p>vue 具有插槽特性，在定义组件时可在某个位置加一个插槽 slot，当使用该组件时在组件的 children 节点会渲染到定义插槽的位置</p>
<pre><code class="hljs language-vue copyable" lang="vue"><button type="submit">
  <slot></slot>
</button>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>插槽还可以命名，让 children 节点渲染到具有特定名称的位置</p>
<pre><code class="hljs language-vue copyable" lang="vue"><div class="container">
  <header>
    <slot name="header"></slot>
  </header>
  <main>
    <slot></slot>
  </main>
  <footer>
    <slot name="footer"></slot>
  </footer>
</div>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>vue 运行时会得到声明的 slot，在 vue3 运行时实例具有一个 slots 对象，成员是以组件内 slot 命名的方法集合，该方法集合都会返回 vnode 数组，分别是定义在对应 slot 里的 children</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-comment">// 当前对象 slots 成员</span>
<span class="hljs-keyword">const</span> ctx = &#123;
  <span class="hljs-attr">slots</span>: &#123;
    <span class="hljs-function"><span class="hljs-title">default</span>(<span class="hljs-params">scope</span>)</span> &#123;
      <span class="hljs-comment">// 返回 vnodes</span>
    &#125;,
    <span class="hljs-function"><span class="hljs-title">header</span>(<span class="hljs-params">scope</span>)</span> &#123;
      <span class="hljs-comment">// 返回 vnodes</span>
    &#125;,
    <span class="hljs-function"><span class="hljs-title">footer</span>(<span class="hljs-params">scope</span>)</span> &#123;
      <span class="hljs-comment">// 返回 vnodes</span>
    &#125;
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-4">json2render 基于 Vue 的渲染扩展</h3>
<p>json2render 基于 vue3 的实现提供了在每个节点 setup 环节的 hook 扩展操作，这个操作可以实现在渲染前对节点进行预处理，根据条件改变节点属性，这个处理只会在节点首次初始化过程中执行，不会影响界面响应数据变化时候的性能</p>
<p>hook 的定义方法如下</p>
<pre><code class="hljs language-javascript copyable" lang="javascript">() => <span class="hljs-function">(<span class="hljs-params">field, next</span>) =></span> &#123;
  <span class="hljs-comment">// field 是当前节点的定义</span>
  <span class="hljs-comment">// 这里可以对 field 的属性进行预处理，变更属性</span>
  next(field)
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>如果想支持 slot 特性需要实现一个 hook，具体过程是父节点执行 hook 时遍历所有 children，当 child 的 component 属性值是 <code>slot</code> 时认定该节点是 slot 节点用来显示 slot 的内容，用 child 的 name 属性（默认default）查找 slots 里对应名称的方法并执行，用返回的 vnode 集合替换 children 对应的元素，在渲染的时候会就可实现在特定 slot 位置渲染对应 children</p>
<h2 data-id="heading-5">关于</h2>
<p>关于 json2render 实现原理涉及到东西很多，在最新版本里主要就是增加了 <code>dependency injection</code> 机制，使之能够合理的扩展新功能以及在所有子节点中共享在 children 定义的的 slots，具体参考项目 <a href="https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Ffyl080801%2Fjson-to-render" target="_blank" rel="nofollow noopener noreferrer" title="https://github.com/fyl080801/json-to-render" ref="nofollow noopener noreferrer">json2render</a>，网慢访问 <a href="https://link.juejin.cn/?target=https%3A%2F%2Fgitee.com%2Ffyl080801%2Fjson-to-render" target="_blank" rel="nofollow noopener noreferrer" title="https://gitee.com/fyl080801/json-to-render" ref="nofollow noopener noreferrer">国内镜像</a></p></div>  
</div>
            

---
title: 'VUE开发小技巧：hover出来的图标使用ElementUI的dropdown'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/fb5a496cda0d487781a42331567a087e~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 19:38:57 GMT
thumbnail: 'https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/fb5a496cda0d487781a42331567a087e~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;color:#383838;font-size:15px;line-height:37.5px;letter-spacing:2px;word-break:break-word;font-family:-apple-system,BlinkMacSystemFont,Segoe UI,Roboto,Oxygen,Ubuntu,Cantarell,Open Sans,Helvetica Neue,sans-serif;scroll-behavior:smooth;background-image:linear-gradient(0deg,transparent 24%,rgba(201,195,195,.329) 25%,hsla(0,8%,80.4%,.05) 26%,transparent 27%,transparent 74%,hsla(0,5.2%,81%,.185) 75%,rgba(180,176,176,.05) 76%,transparent 77%,transparent),linear-gradient(90deg,transparent 24%,rgba(204,196,196,.226) 25%,hsla(0,4%,66.1%,.05) 26%,transparent 27%,transparent 74%,hsla(0,5.2%,81%,.185) 75%,rgba(180,176,176,.05) 76%,transparent 77%,transparent);background-color:#fff;background-size:50px 50px;padding-bottom:120px&#125;.markdown-body ::selection&#123;color:#fff;background-color:#a862ea&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;margin:30px 0 15px;color:#a862ea&#125;.markdown-body h1&#123;line-height:2;font-size:1.4em&#125;.markdown-body h1~p:first-of-type:first-letter&#123;color:#a862ea;float:left;font-size:2em;margin-right:.4em;font-weight:bolder&#125;.markdown-body h2&#123;font-size:1.2em&#125;.markdown-body h3&#123;font-size:1.1em&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:2em&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;padding-left:.2em&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:10px&#125;.markdown-body li::marker&#123;color:#a862ea&#125;.markdown-body li,.markdown-body p&#123;opacity:.9;vertical-align:baseline;transition:all .1s ease&#125;.markdown-body li:hover,.markdown-body p:hover&#123;opacity:1&#125;.markdown-body a&#123;display:inline-block;color:#a862ea;cursor:pointer;padding-bottom:2px;text-decoration:none;position:relative&#125;.markdown-body a:after&#123;content:"";position:absolute;width:98%;height:2px;bottom:0;left:0;transform:scaleX(0);background-color:#a862ea;transform-origin:bottom right;transition:transform .3s ease-in-out&#125;.markdown-body a:hover:after&#123;transform:scaleX(1);transform-origin:bottom left&#125;.markdown-body a:active,.markdown-body a:link&#123;color:#a862ea&#125;.markdown-body img&#123;max-width:100%;user-select:none;margin:1em 0;box-shadow:0 0 20px 0 #e7daff;transition:transform .2s ease 0s;background-color:#f8f5ff&#125;.markdown-body img:hover&#123;opacity:1;transform:translateY(-2px)&#125;.markdown-body blockquote&#123;padding:.5em 1em;margin:15px 0;border-top-left-radius:2px;border-bottom-left-radius:2px;border-left:4px solid #a862ea;background-color:#f8f5ff&#125;.markdown-body blockquote>p&#123;margin:0&#125;.markdown-body code&#123;padding:2px .4em;overflow-x:auto;color:#a862ea;font-weight:700;word-break:break-word;font-family:Operator Mono,Consolas,Monaco,Menlo,monospace;background-color:#f8f5ff&#125;.markdown-body pre&#123;margin:2em 0;box-shadow:0 0 20px #e7daff&#125;.markdown-body pre>code&#123;display:block;padding:1.5em;word-break:normal;font-size:.9em;font-style:normal;font-weight:400;font-family:Operator Mono,Consolas,Monaco,Menlo,monospace;line-height:22.5px;color:#383838;border-radius:3px;scroll-behavior:smooth&#125;.markdown-body pre>code::-webkit-scrollbar&#123;height:6px;background-color:#f8f5ff&#125;.markdown-body pre>code::-webkit-scrollbar-thumb&#123;background-color:#e7daff;border-bottom-left-radius:3px;border-bottom-right-radius:3px&#125;.markdown-body hr&#123;margin:2em 0;border-top:1px solid #a862ea&#125;.markdown-body table&#123;font-size:12px;max-width:100%;overflow:auto;border-collapse:collapse;border:1px solid #e7daff&#125;.markdown-body thead&#123;color:#a862ea;background:#f8f5ff&#125;.markdown-body td,.markdown-body th&#123;padding:1em .5em&#125;.markdown-body tr&#123;background-color:#fcfcfc&#125;@media (max-width:720px)&#123;.markdown-body&#123;font-size:12px&#125;&#125;</style><h1 data-id="heading-0">一、前言-问题描述🌟</h1>
<p>当我们把鼠标移动到某个区域，hover显示出功能图标后，我们点击图标弹出功能菜单，但当鼠标移出hover区域或者移动到弹出的功能菜单时，原来的功能图标消失了，这显然不是我们需要的效果，效果如下：</p>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/fb5a496cda0d487781a42331567a087e~tplv-k3u1fbpfcp-watermark.image" alt="现象.gif" loading="lazy" referrerpolicy="no-referrer">
现在我们希望当弹出功能菜单后，鼠标移出hover区域或者移动到弹出的功能菜单时，此时hover区域的功能图标不消失，我们需要怎样实现了？</p>
<h1 data-id="heading-1">二、解决方案🙉</h1>
<h3 data-id="heading-2">解决思路</h3>
<p>我们<strong>创建一个class，使之和hover动作的样式一致</strong>，当我们<strong>点击功能图标弹出功能菜单时，我们给hover区域的dom元素加上这个class，而当功能菜单弹窗消失时，我们就去掉这个class</strong>。</p>
<h3 data-id="heading-3">具体实现</h3>
<p>先梳理一下上面gif图的html结构：</p>
<p>class="app-list"的dom节点下有多个class="app-item"的dom，
其中每个列表项的应用ref="'app'+item.app_id",这样我们就可以通过app_id找到每个列表项。当我们把鼠标hover至每个app-item时，app-item中class="app-options"的dom会显示出来，app-options中包含了一个class="more-btn"的dom节点，该节点使用了ElementUI的dropdown下拉菜单组件，当点击more-btn时，下拉菜单显示。</p>
<pre><code class="hljs language-html copyable" lang="html"><span class="hljs-tag"><<span class="hljs-name">ul</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"app-list"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">li</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"app-item"</span> <span class="hljs-attr">:ref</span>=<span class="hljs-string">"'app'+item.app_id"</span> <span class="hljs-attr">v-for</span>=<span class="hljs-string">"item in appList"</span> <span class="hljs-attr">:key</span>=<span class="hljs-string">"item.app_id"</span> @<span class="hljs-attr">click</span>=<span class="hljs-string">"toAppManage(item.app_id)"</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"ipu-flex"</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">img</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"app-logo"</span> <span class="hljs-attr">:src</span>=<span class="hljs-string">"item.app_logo"</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"ipu-flex ipu-flex-vertical ipu-flex-justify-space ipu-flex-grow-1"</span>></span>
          <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"app-name"</span>></span>&#123;&#123;item.app_name&#125;&#125;<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
          <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"create-time"</span>></span>&#123;&#123;item.create_date&#125;&#125;<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
        <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
      <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"app-description"</span>></span>&#123;&#123;item.app_desc&#125;&#125;<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"ipu-flex-grow-1"</span>></span><span class="hljs-tag"></<span class="hljs-name">div</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"app-options"</span> @<span class="hljs-attr">click.stop</span>></span>

        <span class="hljs-tag"><<span class="hljs-name">el-tooltip</span>  <span class="hljs-attr">effect</span>=<span class="hljs-string">"dark"</span> <span class="hljs-attr">content</span>=<span class="hljs-string">"预览"</span> <span class="hljs-attr">placement</span>=<span class="hljs-string">"top"</span> <span class="hljs-attr">:enterable</span>=<span class="hljs-string">"false"</span>></span>
          <span class="hljs-tag"><<span class="hljs-name">i</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"ri-eye-fill"</span>></span><span class="hljs-tag"></<span class="hljs-name">i</span>></span>
        <span class="hljs-tag"></<span class="hljs-name">el-tooltip</span>></span>

        <span class="hljs-tag"><<span class="hljs-name">el-dropdown</span> <span class="hljs-attr">trigger</span>=<span class="hljs-string">"click"</span> @<span class="hljs-attr">command</span>=<span class="hljs-string">"onAppAction"</span> <span class="hljs-attr">placement</span>=<span class="hljs-string">"bottom-start"</span> @<span class="hljs-attr">visible-change</span>=<span class="hljs-string">"visibleChange($event, item.app_id)"</span>></span>
          <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"more-btn"</span>></span>
            <span class="hljs-tag"><<span class="hljs-name">i</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"ri-more-fill"</span>></span><span class="hljs-tag"></<span class="hljs-name">i</span>></span>
          <span class="hljs-tag"></<span class="hljs-name">div</span>></span>

          <span class="hljs-tag"><<span class="hljs-name">el-dropdown-menu</span> <span class="hljs-attr">slot</span>=<span class="hljs-string">"dropdown"</span>></span>
            <span class="hljs-tag"><<span class="hljs-name">el-dropdown-item</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"ipu-flex-middle"</span> <span class="hljs-attr">:command</span>=<span class="hljs-string">"&#123;type:'set', appId: item.app_id&#125;"</span>></span>
              <span class="hljs-tag"><<span class="hljs-name">span</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"child-action-name"</span>></span>应用设置<span class="hljs-tag"></<span class="hljs-name">span</span>></span>
            <span class="hljs-tag"></<span class="hljs-name">el-dropdown-item</span>></span>
            <span class="hljs-tag"><<span class="hljs-name">el-dropdown-item</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"ipu-flex-middle"</span> <span class="hljs-attr">:command</span>=<span class="hljs-string">"&#123;type:'delete', appId: item.app_id&#125;"</span>></span>
              <span class="hljs-tag"><<span class="hljs-name">span</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"child-action-name"</span>></span>删除应用<span class="hljs-tag"></<span class="hljs-name">span</span>></span>
            <span class="hljs-tag"></<span class="hljs-name">el-dropdown-item</span>></span>
          <span class="hljs-tag"></<span class="hljs-name">el-dropdown-menu</span>></span>
        <span class="hljs-tag"></<span class="hljs-name">el-dropdown</span>></span>

      <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
    <span class="hljs-tag"></<span class="hljs-name">li</span>></span>
  <span class="hljs-tag"></<span class="hljs-name">ul</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>再来看CSS部分的代码，CSS部分采用SCSS预处理器编写：</p>
<p>.app-options在普通状态下由于transform: translateY(42px);向下移了42px而隐藏，当鼠标移至.app-item上时，我们给它的hover事件上设置了transform: translateY(4px)；这时.app-options由于上移而显示，同时我们在.app-item上定义了一个.select样式，它的样式与hover事件的样式一致。</p>
<pre><code class="hljs language-SCSS copyable" lang="SCSS"><span class="hljs-selector-class">.app-list</span> &#123;
        <span class="hljs-attribute">margin-top</span>: <span class="hljs-number">30px</span>;
        <span class="hljs-attribute">display</span>:flex;
        <span class="hljs-attribute">flex-wrap</span>: wrap;
        gap: <span class="hljs-number">20px</span>;
        <span class="hljs-selector-class">.app-item</span> &#123;
          <span class="hljs-attribute">overflow</span>: hidden;
          <span class="hljs-attribute">cursor</span>: pointer;
          <span class="hljs-attribute">position</span>: relative;
          <span class="hljs-attribute">width</span>: <span class="hljs-number">258px</span>;
          <span class="hljs-attribute">height</span>: <span class="hljs-number">206px</span>;
          <span class="hljs-attribute">padding</span>:<span class="hljs-number">20px</span>;
          <span class="hljs-attribute">background</span>: <span class="hljs-number">#FFFFFF</span>;
          <span class="hljs-attribute">border</span>: <span class="hljs-number">1px</span> solid <span class="hljs-number">#F2F6FC</span>;
          <span class="hljs-attribute">border-radius</span>: <span class="hljs-number">4px</span>;
          <span class="hljs-attribute">display</span>: flex;
          <span class="hljs-attribute">flex-direction</span>: column;
          &<span class="hljs-selector-pseudo">:hover</span>  &#123;
            <span class="hljs-attribute">box-shadow</span>: <span class="hljs-number">0px</span> <span class="hljs-number">2px</span> <span class="hljs-number">12px</span> rgba(<span class="hljs-number">0</span>, <span class="hljs-number">0</span>, <span class="hljs-number">0</span>, <span class="hljs-number">0.06</span>);
            <span class="hljs-selector-class">.app-options</span> &#123;
              <span class="hljs-attribute">transform</span>: translateY(<span class="hljs-number">4px</span>);
            &#125;
          &#125;
          &<span class="hljs-selector-class">.select</span> &#123;
            <span class="hljs-attribute">box-shadow</span>: <span class="hljs-number">0px</span> <span class="hljs-number">2px</span> <span class="hljs-number">12px</span> rgba(<span class="hljs-number">0</span>, <span class="hljs-number">0</span>, <span class="hljs-number">0</span>, <span class="hljs-number">0.06</span>);
            <span class="hljs-selector-class">.app-options</span> &#123;
              <span class="hljs-attribute">transform</span>: translateY(<span class="hljs-number">4px</span>);
            &#125;
          &#125;
          <span class="hljs-selector-class">.app-logo</span> &#123;
            <span class="hljs-attribute">background</span>: <span class="hljs-number">#fff</span>;
            <span class="hljs-attribute">border-radius</span>: <span class="hljs-number">6px</span>;
            <span class="hljs-attribute">width</span>: <span class="hljs-number">50px</span>;
            <span class="hljs-attribute">height</span>: <span class="hljs-number">50px</span>;
            <span class="hljs-attribute">margin-right</span>: <span class="hljs-number">14px</span>;
          &#125;
          <span class="hljs-selector-class">.app-name</span> &#123;
            <span class="hljs-attribute">font-size</span>: <span class="hljs-number">16px</span>;
            <span class="hljs-attribute">line-height</span>: <span class="hljs-number">24px</span>;
            <span class="hljs-attribute">color</span>: <span class="hljs-number">#606266</span>;
            <span class="hljs-attribute">overflow</span>: hidden;
            <span class="hljs-attribute">white-space</span>: nowrap;
            <span class="hljs-attribute">text-overflow</span>: ellipsis;
          &#125;
          <span class="hljs-selector-class">.create-time</span> &#123;
            <span class="hljs-attribute">font-size</span>: <span class="hljs-number">14px</span>;
            <span class="hljs-attribute">line-height</span>: <span class="hljs-number">22px</span>;
            <span class="hljs-attribute">color</span>: rgba(<span class="hljs-number">0</span>, <span class="hljs-number">0</span>, <span class="hljs-number">0</span>, .<span class="hljs-number">45</span>);
          &#125;
          <span class="hljs-selector-class">.app-description</span> &#123;
            <span class="hljs-attribute">margin-top</span>: <span class="hljs-number">19px</span>;
            <span class="hljs-attribute">font-size</span>: <span class="hljs-number">12px</span>;
            <span class="hljs-attribute">line-height</span>: <span class="hljs-number">20px</span>;
            <span class="hljs-attribute">color</span>: <span class="hljs-number">#909399</span>;
            <span class="hljs-attribute">display</span>: -webkit-box;
            -webkit-line-clamp: <span class="hljs-number">3</span>;
            -webkit-box-orient: vertical;
            <span class="hljs-attribute">overflow</span>: hidden;
            <span class="hljs-attribute">text-overflow</span>: ellipsis;
          &#125;
          <span class="hljs-selector-class">.app-options</span> &#123;
            <span class="hljs-attribute">align-self</span>: flex-end;
            <span class="hljs-attribute">display</span>: flex;
            <span class="hljs-attribute">justify-content</span>: flex-end;
            <span class="hljs-attribute">transform</span>: translateY(<span class="hljs-number">42px</span>);
            <span class="hljs-attribute">transition</span>: transform .<span class="hljs-number">3s</span> ease-in-out;
            <span class="hljs-selector-tag">i</span> &#123;
              <span class="hljs-attribute">font-size</span>: <span class="hljs-number">20px</span>;
              <span class="hljs-attribute">line-height</span>: <span class="hljs-number">20px</span>;
              <span class="hljs-attribute">color</span>: rgba(<span class="hljs-number">144</span>, <span class="hljs-number">147</span>, <span class="hljs-number">153</span>, <span class="hljs-number">1</span>);
            &#125;
            <span class="hljs-selector-class">.more-btn</span> &#123;
              <span class="hljs-attribute">margin-left</span>:<span class="hljs-number">20px</span>;
            &#125;
          &#125;
        &#125;
      &#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>JS部分梳理：</p>
<p>ElementUI的dropdown下拉菜单组件可以通过<code>监听visible-change事件</code>，获取下拉菜单的状态，出现则为 true，隐藏则为 false。于是我们<code>在组件上添加@visible-change="visibleChange($event, item.app_id)，并传入app_id</code>。我们可以<code>通过app_id找到对应的dom节点，然后根据下拉菜单的状态给此dom节点添加或移除select样式</code>。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-function"><span class="hljs-title">visibleChange</span>(<span class="hljs-params">e, appId</span>)</span> &#123;
    <span class="hljs-keyword">if</span> (e) &#123;
      <span class="hljs-built_in">this</span>.$refs[<span class="hljs-string">'app'</span> + appId][<span class="hljs-number">0</span>].classList.add(<span class="hljs-string">'select'</span>)
    &#125; <span class="hljs-keyword">else</span> &#123;
      <span class="hljs-built_in">this</span>.$refs[<span class="hljs-string">'app'</span> + appId][<span class="hljs-number">0</span>].classList.remove(<span class="hljs-string">'select'</span>)
    &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>最终我们实现了当弹出功能菜单后，鼠标移出hover区域或者移动到弹出的功能菜单时，此时hover区域的功能图标不消失的效果，如下图：</p>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f1094bd66fba4a1892a8c96a25699dad~tplv-k3u1fbpfcp-watermark.image" alt="结果.gif" loading="lazy" referrerpolicy="no-referrer"></p>
<h1 data-id="heading-4">三、总结与举一反三✨</h1>
<p><strong>创建一个class，使之和hover动作的样式一致</strong>，当我们<strong>点击功能图标弹出功能菜单时，我们给hover区域的dom元素加上这个class，而当功能菜单弹窗消失时，我们就去掉这个class</strong>。通过这个原理我们实现了想要的效果，类似的ElementUI的
Popover 弹出框组件、Tooltip 文字提示组件，我们想在移动到弹出框、文字提示区域时，原来hover显示的图标不消失，都可以运用此技巧~</p></div>  
</div>
            
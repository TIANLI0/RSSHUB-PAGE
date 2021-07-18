
---
title: 'vue中使用svg图片（cli2.x、cli3.x、cli4.x配置）'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/78b536b1905e4b2b980c0c7d034b558b~tplv-k3u1fbpfcp-zoom-1.image'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 18:39:17 GMT
thumbnail: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/78b536b1905e4b2b980c0c7d034b558b~tplv-k3u1fbpfcp-zoom-1.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h3 data-id="heading-0">一、安装 svg-sprite-loader 插件</h3>
<pre><code class="hljs language-js copyable" lang="js"> npm install svg-sprite-loader
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-1">二、基于 vue-cli2.x 项目 webpack 配置</h3>
<p>配置build文件夹中的 webpack.base.conf.js 文件</p>
<pre><code class="hljs language-js copyable" lang="js"> <span class="hljs-comment">//注意 url-loader 中要将 icons 文件夹排除, 不让 url-loader 处理该文件夹</span>
<span class="hljs-attr">exclude</span>: [resolve(<span class="hljs-string">'src/icons'</span>)],
&#123;
        <span class="hljs-attr">test</span>: <span class="hljs-regexp">/\.svg$/</span>,
        loader: <span class="hljs-string">'svg-sprite-loader'</span>,
        <span class="hljs-attr">include</span>: [resolve(<span class="hljs-string">'src/icons'</span>)],
        <span class="hljs-attr">options</span>: &#123;
          <span class="hljs-attr">symbolId</span>: <span class="hljs-string">'icon-[name]'</span>
        &#125;
      &#125;,
<span class="copy-code-btn">复制代码</span></code></pre>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/78b536b1905e4b2b980c0c7d034b558b~tplv-k3u1fbpfcp-zoom-1.image" alt="在这里插入图片描述" loading="lazy" referrerpolicy="no-referrer"></p>
<h3 data-id="heading-2">三、基于 vue-cli3.x 和 cli4.x 项目 webpack 配置</h3>
<p>配置根目录中的 vue.config.js 文件</p>
<pre><code class="hljs language-js copyable" lang="js">  <span class="hljs-comment">/* svg 相关配置 */</span>
    <span class="hljs-attr">chainWebpack</span>: <span class="hljs-function"><span class="hljs-params">config</span> =></span> &#123;
        <span class="hljs-keyword">const</span> svgRule = config.module.rule(<span class="hljs-string">'svg'</span>);
        <span class="hljs-comment">// 清空默认svg规则</span>
        svgRule.uses.clear();
        <span class="hljs-comment">//针对svg文件添加svg-sprite-loader规则</span>
        svgRule
            .test( <span class="hljs-regexp">/\.svg$/</span>)
            .use(<span class="hljs-string">'svg-sprite-loader'</span>)
            .loader(<span class="hljs-string">'svg-sprite-loader'</span>)
            .options(&#123;
                <span class="hljs-attr">symbolId</span>: <span class="hljs-string">'icon-[name]'</span>
            &#125;);
    &#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9b523fbcc044472393ba3d7f886a41cc~tplv-k3u1fbpfcp-zoom-1.image" alt="在这里插入图片描述" loading="lazy" referrerpolicy="no-referrer"></p>
<h3 data-id="heading-3">四、封装 SvgIcon 组件</h3>
<p>在 src→components 中新建SvgIcon文件夹，在 SvgIcon 下新建 index.vue(代码如下)</p>
<pre><code class="hljs language-js copyable" lang="js"><template>
  <span class="xml"><span class="hljs-tag"><<span class="hljs-name">svg</span> <span class="hljs-attr">:class</span>=<span class="hljs-string">"svgClass"</span> <span class="hljs-attr">aria-hidden</span>=<span class="hljs-string">"true"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">use</span> <span class="hljs-attr">:xlink:href</span>=<span class="hljs-string">"iconName"</span> /></span>
  <span class="hljs-tag"></<span class="hljs-name">svg</span>></span></span>
</template>

<span class="xml"><span class="hljs-tag"><<span class="hljs-name">script</span>></span><span class="javascript">
  <span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span> &#123;
    <span class="hljs-attr">name</span>: <span class="hljs-string">'SvgIcon'</span>,
    <span class="hljs-attr">props</span>: &#123;
      <span class="hljs-attr">iconClass</span>: &#123;
        <span class="hljs-attr">type</span>: <span class="hljs-built_in">String</span>,
        <span class="hljs-attr">required</span>: <span class="hljs-literal">true</span>
      &#125;,
      <span class="hljs-attr">className</span>: &#123;
        <span class="hljs-attr">type</span>: <span class="hljs-built_in">String</span>
      &#125;
    &#125;,
    <span class="hljs-attr">computed</span>: &#123;
      <span class="hljs-function"><span class="hljs-title">iconName</span>(<span class="hljs-params"></span>)</span> &#123;
        <span class="hljs-keyword">return</span> <span class="hljs-string">`#icon-<span class="hljs-subst">$&#123;<span class="hljs-built_in">this</span>.iconClass&#125;</span>`</span>
      &#125;,
      <span class="hljs-function"><span class="hljs-title">svgClass</span>(<span class="hljs-params"></span>)</span> &#123;
        <span class="hljs-keyword">if</span> (<span class="hljs-built_in">this</span>.className) &#123;
          <span class="hljs-keyword">return</span> <span class="hljs-string">'svg-icon '</span> + <span class="hljs-built_in">this</span>.className
        &#125; <span class="hljs-keyword">else</span> &#123;
          <span class="hljs-keyword">return</span> <span class="hljs-string">'svg-icon'</span>
        &#125;
      &#125;
    &#125;
  &#125;
</span><span class="hljs-tag"></<span class="hljs-name">script</span>></span></span>

<span class="xml"><span class="hljs-tag"><<span class="hljs-name">style</span> <span class="hljs-attr">scoped</span>></span><span class="css">
  <span class="hljs-selector-class">.svg-icon</span> &#123;
    <span class="hljs-attribute">width</span>: <span class="hljs-number">1em</span>;
    <span class="hljs-attribute">height</span>: <span class="hljs-number">1em</span>;
    <span class="hljs-attribute">vertical-align</span>: -<span class="hljs-number">0.15em</span>;
    fill: currentColor;
    <span class="hljs-attribute">overflow</span>: hidden;
  &#125;
</span><span class="hljs-tag"></<span class="hljs-name">style</span>></span></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9d78fde46fe24afeb0a393e61dc34923~tplv-k3u1fbpfcp-zoom-1.image" alt="在这里插入图片描述" loading="lazy" referrerpolicy="no-referrer"></p>
<h3 data-id="heading-4">五、全局注册 svg 组件</h3>
<p>在 src 下新建 icons 文件夹，在 icons下新建 index.js 和 svg文件夹，svg文件夹用于存放 svg 图片，index.js 用于加载所有 svg 文件和全局注册组件(代码如下)</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">import</span> Vue <span class="hljs-keyword">from</span> <span class="hljs-string">'vue'</span>
<span class="hljs-keyword">import</span> SvgIcon <span class="hljs-keyword">from</span> <span class="hljs-string">'../components/SvgIcon/index'</span><span class="hljs-comment">//svg组件</span>
<span class="hljs-comment">//全局注册组件</span>
Vue.component(<span class="hljs-string">'svg-icon'</span>, SvgIcon)
<span class="hljs-comment">// 定义一个加载目录的函数</span>
<span class="hljs-keyword">const</span> requireAll = <span class="hljs-function"><span class="hljs-params">requireContext</span> =></span> requireContext.keys().map(requireContext)
<span class="hljs-keyword">const</span> req = <span class="hljs-built_in">require</span>.context(<span class="hljs-string">'./svg'</span>, <span class="hljs-literal">false</span>, <span class="hljs-regexp">/\.svg$/</span>)
<span class="hljs-comment">// 加载目录下的所有的 svg 文件</span>
requireAll(req)
<span class="copy-code-btn">复制代码</span></code></pre>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/56cbf57d186a44dcb5a875a3e50fb1f3~tplv-k3u1fbpfcp-zoom-1.image" alt="在这里插入图片描述" loading="lazy" referrerpolicy="no-referrer"></p>
<h3 data-id="heading-5">六、在 main.js 项目入口文件中导入 icons 文件</h3>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a8defff44c884294baee06de8c55d89a~tplv-k3u1fbpfcp-zoom-1.image" alt="在这里插入图片描述" loading="lazy" referrerpolicy="no-referrer"></p>
<h3 data-id="heading-6">七、使用方法</h3>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">//icon-class：svg图片的文件名</span>
<span class="hljs-comment">//class-name：svg图片的样式类名</span>
<svg-icon icon-<span class="hljs-class"><span class="hljs-keyword">class</span></span>=<span class="hljs-string">"time"</span> <span class="hljs-class"><span class="hljs-keyword">class</span>-<span class="hljs-title">name</span></span>=<span class="hljs-string">"icon"</span> />
<span class="copy-code-btn">复制代码</span></code></pre>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b290b538fb1e435e995cbde78d281c45~tplv-k3u1fbpfcp-zoom-1.image" alt="在这里插入图片描述" loading="lazy" referrerpolicy="no-referrer"></p>
<h3 data-id="heading-7">八、可能遇到的问题</h3>
<ul>
<li>宽高样式不生效：在样式后面加上 <strong>!important</strong></li>
<li>颜色不生效：打开 <strong>svg</strong> 文件，删除文件中所有的 <strong>fill</strong> 属性</li>
</ul>
<h3 data-id="heading-8"><strong><a href="https://link.juejin.cn/?target=https%3A%2F%2Fblog.csdn.net%2FXHL1314mmq" target="_blank" rel="nofollow noopener noreferrer" title="https://blog.csdn.net/XHL1314mmq" ref="nofollow noopener noreferrer">我的CSDN → 传送门</a></strong></h3></div>  
</div>
            
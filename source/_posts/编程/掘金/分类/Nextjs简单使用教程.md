
---
title: 'Next.js简单使用教程'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=2613'
author: 掘金
comments: false
date: Tue, 13 Jul 2021 19:05:16 GMT
thumbnail: 'https://picsum.photos/400/300?random=2613'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h2 data-id="heading-0">简介</h2>
<blockquote>
<p>Next.js 是一个轻量级的 React 服务端渲染应用框架。</p>
</blockquote>
<p>官网链接：<a href="https://link.juejin.cn/?target=https%3A%2F%2Fwww.nextjs.cn%2F" target="_blank" rel="nofollow noopener noreferrer" title="https://www.nextjs.cn/" ref="nofollow noopener noreferrer">www.nextjs.cn/</a></p>
<p><strong>优点：</strong></p>
<ul>
<li>
<p>零配置</p>
<p>自动编译并打包。从一开始就为生产环境而优化。</p>
</li>
<li>
<p>混合模式： SSG 和 SSR</p>
<p>在一个项目中同时支持构建时预渲染页面（SSG）和请求时渲染页面（SSR）</p>
</li>
<li>
<p>增量静态生成</p>
<p>在构建之后以增量的方式添加并更新静态预渲染的页面。</p>
</li>
<li>
<p>支持 TypeScript</p>
<p>自动配置并编译 TypeScript。</p>
</li>
<li>
<p>快速刷新</p>
<p>快速、可靠的实时编辑体验，已在 Facebook 级别的应用上规模上得到验证。</p>
</li>
<li>
<p>基于文件系统的路由</p>
<p>每个 <code>pages</code> 目录下的组件都是一条路由。</p>
</li>
<li>
<p>API 路由</p>
<p>创建 API 端点（可选）以提供后端功能。</p>
</li>
<li>
<p>内置支持CSS</p>
<p>使用 CSS 模块创建组件级的样式。内置对 Sass 的支持。</p>
</li>
<li>
<p>代码拆分和打包</p>
<p>采用由 Google Chrome 小组创建的、并经过优化的打包和拆分算法。</p>
</li>
</ul>
<h2 data-id="heading-1">创建Next.js项目</h2>
<h3 data-id="heading-2">手动创建Next.js项目</h3>
<blockquote>
<p>mkdir nextDemo//创建项目</p>
<p>npm init            //初始化项目</p>
<p>npm i react react-dom next --save          //添加依赖</p>
</blockquote>
<p>在<code>package.json</code>中添加快捷键命令</p>
<pre><code class="hljs language-JSON copyable" lang="JSON"> <span class="hljs-string">"scripts"</span>: &#123;
    <span class="hljs-attr">"test"</span>: <span class="hljs-string">"echo \"Error: no test specified\" && exit 1"</span>,
    <span class="hljs-attr">"dev"</span> : <span class="hljs-string">"next"</span> ,
    <span class="hljs-attr">"build"</span> : <span class="hljs-string">" next build"</span>,
    <span class="hljs-attr">"start"</span> : <span class="hljs-string">"next start"</span>
  &#125;,
<span class="copy-code-btn">复制代码</span></code></pre>
<p>创建<code>pages</code>文件夹和文件</p>
<p>在项目根目录创建<code>pages</code>文件夹并在<code>pages</code>文件夹中创建<code>index.js</code>文件</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">Index</span>(<span class="hljs-params"></span>)</span>&#123;
    <span class="hljs-keyword">return</span> (
        <span class="xml"><span class="hljs-tag"><<span class="hljs-name">div</span>></span>Hello Next.js<span class="hljs-tag"></<span class="hljs-name">div</span>></span></span>
    )
&#125;
<span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span> Index
<span class="copy-code-btn">复制代码</span></code></pre>
<p>运行项目</p>
<blockquote>
<p>npm run dev</p>
</blockquote>
<h3 data-id="heading-3"><code>creact-next-app</code>快速创建项目</h3>
<p><code>create-next-app</code>可以快速的创建<code>Next.js</code>项目，它就是一个脚手架。</p>
<blockquote>
<p>npm install -g create-next-app//全局安装脚手架</p>
<p>create-next-app nextDemo//基于脚手架创建项目</p>
<p>cd nextDemo</p>
<p>npm run dev//运行项目</p>
</blockquote>
<p><strong>目录结构介绍：</strong></p>
<ul>
<li>components文件夹: 这里是专门放置自己写的组件的，这里的组件不包括页面，指公用的或者有专门用途的组件。</li>
<li>node_modules文件夹：Next项目的所有依赖包都在这里，一般我们不会修改和编辑这里的内容。</li>
<li>pages文件夹：这里是放置页面的，这里边的内容会自动生成路由，并在服务器端渲染，渲染好后进行数据同步。</li>
<li>static文件夹： 这个是静态文件夹，比如项目需要的图片、图标和静态资源都可以放到这里。</li>
<li>.gitignore文件： 这个主要是控制git提交和上传文件的，简称就是忽略提交。</li>
<li>package.json文件：定义了项目所需要的文件和项目的配置信息（名称、版本和许可证），最主要的是使用<code>npm install</code> 就可以下载项目所需要的所有包。</li>
</ul>
<h2 data-id="heading-4">Pages</h2>
<p>在 Next.js 中，一个 <strong>page（页面）</strong> 就是一个从 <code>.js</code>、<code>jsx</code>、<code>.ts</code> 或 <code>.tsx</code> 文件导出（export）的 <a href="https://link.juejin.cn/?target=https%3A%2F%2Freactjs.org%2Fdocs%2Fcomponents-and-props.html" target="_blank" rel="nofollow noopener noreferrer" title="https://reactjs.org/docs/components-and-props.html" ref="nofollow noopener noreferrer">React 组件</a> ，这些文件存放在 <code>pages</code> 目录下。每个 page（页面）都使用其文件名作为路由（route）。</p>
<p>如果你创建了一个命名为 <code>pages/about.js</code> 的文件并导出（export）一个如下所示的 React 组件，则可以通过 <code>/about</code> 路径进行访问。</p>
<h2 data-id="heading-5">路由</h2>
<p>页面跳转一般有两种形式，第一种是利用标签<code><Link></code>,第二种是用js编程的方式进行跳转，也就是利用<code>Router</code>组件</p>
<h3 data-id="heading-6">Link</h3>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">import</span> React <span class="hljs-keyword">from</span> <span class="hljs-string">'react'</span>
<span class="hljs-keyword">import</span> Link <span class="hljs-keyword">from</span> <span class="hljs-string">'next/link'</span>


<span class="hljs-keyword">const</span> Home = <span class="hljs-function">() =></span> (
  <span class="xml"><span class="hljs-tag"><></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span>></span>我是首页<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span>></span><span class="hljs-tag"><<span class="hljs-name">Link</span> <span class="hljs-attr">href</span>=<span class="hljs-string">"/pageA"</span>></span><span class="hljs-tag"><<span class="hljs-name">a</span>></span>去A页面<span class="hljs-tag"></<span class="hljs-name">a</span>></span><span class="hljs-tag"></<span class="hljs-name">Link</span>></span><span class="hljs-tag"></<span class="hljs-name">div</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span>></span><span class="hljs-tag"><<span class="hljs-name">Link</span> <span class="hljs-attr">href</span>=<span class="hljs-string">"/pageB"</span>></span><span class="hljs-tag"><<span class="hljs-name">a</span>></span>去B页面<span class="hljs-tag"></<span class="hljs-name">a</span>></span><span class="hljs-tag"></<span class="hljs-name">Link</span>></span><span class="hljs-tag"></<span class="hljs-name">div</span>></span>

  <span class="hljs-tag"></></span></span>
)

<span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span> Home
<span class="copy-code-btn">复制代码</span></code></pre>
<p>注意：用<code><Link></code>标签进行跳转是非常容易的，但是又一个小坑需要你注意一下，就是他不支持兄弟标签并列的情况。</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"> <span class="hljs-comment">//错误写法</span>
 <div>
  <span class="xml"><span class="hljs-tag"><<span class="hljs-name">Link</span> <span class="hljs-attr">href</span>=<span class="hljs-string">"/pageA"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">span</span>></span>去A页面<span class="hljs-tag"></<span class="hljs-name">span</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">span</span>></span>前端博客<span class="hljs-tag"></<span class="hljs-name">span</span>></span>
  <span class="hljs-tag"></<span class="hljs-name">Link</span>></span></span>
</div>

<span class="hljs-comment">//正确写法</span>
<span class="xml"><span class="hljs-tag"><<span class="hljs-name">Link</span> <span class="hljs-attr">href</span>=<span class="hljs-string">"/pageA"</span>></span>
  <span class="hljs-tag"><<span class="hljs-name">a</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">span</span>></span>去A页面<span class="hljs-tag"></<span class="hljs-name">span</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">span</span>></span>前端博客<span class="hljs-tag"></<span class="hljs-name">span</span>></span>
  <span class="hljs-tag"></<span class="hljs-name">a</span>></span>
<span class="hljs-tag"></<span class="hljs-name">Link</span>></span></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-7">Router</h3>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-keyword">import</span> Router <span class="hljs-keyword">from</span> <span class="hljs-string">'next/router'</span>

<button onClick=&#123;<span class="hljs-function">()=></span>&#123;Router.push(<span class="hljs-string">'/pageA'</span>)&#125;&#125;>去A页面</button>

<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-8">参数传递与接收</h3>
<p>在<code>Next.js</code>中只能通过通过query（<code>?id=1</code>）来传递参数，而不能通过(<code>path:id</code>)的形式传递参数。</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-keyword">import</span> Link <span class="hljs-keyword">from</span> <span class="hljs-string">'next/link'</span>

<span class="hljs-comment">//传递</span>
<Link href=<span class="hljs-string">"/blogDetail?bid=23"</span>><span class="xml"><span class="hljs-tag"><<span class="hljs-name">a</span>></span>&#123;blog.title&#125;<span class="hljs-tag"></<span class="hljs-name">a</span>></span></span></Link>

    
    
<span class="hljs-comment">//blog.js</span>
<span class="hljs-keyword">import</span> &#123; withRouter&#125; <span class="hljs-keyword">from</span> <span class="hljs-string">'next/router'</span>
<span class="hljs-keyword">import</span> Link <span class="hljs-keyword">from</span> <span class="hljs-string">'next/link'</span>

<span class="hljs-keyword">const</span> BlogDetail = <span class="hljs-function">(<span class="hljs-params">&#123;router&#125;</span>)=></span>&#123;
    <span class="hljs-keyword">return</span> (
        <span class="xml"><span class="hljs-tag"><></span>
            <span class="hljs-tag"><<span class="hljs-name">div</span>></span>blog id: &#123;router.query.name&#125;<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
            <span class="hljs-tag"><<span class="hljs-name">Link</span> <span class="hljs-attr">href</span>=<span class="hljs-string">"/"</span>></span><span class="hljs-tag"><<span class="hljs-name">a</span>></span>返回首页<span class="hljs-tag"></<span class="hljs-name">a</span>></span><span class="hljs-tag"></<span class="hljs-name">Link</span>></span>
        <span class="hljs-tag"></></span></span>
    )
&#125;
<span class="hljs-comment">//withRouter是Next.js框架的高级组件，用来处理路由用的</span>
<span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span> withRouter(BlogDetail)


<span class="hljs-comment">/************************************************************************************/</span>
<span class="hljs-keyword">import</span> Router <span class="hljs-keyword">from</span> <span class="hljs-string">'next/router'</span>

<button onClick=&#123;gotoBlogDetail&#125; >博客详情</button>

<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">gotoBlogDetail</span>(<span class="hljs-params"></span>)</span>&#123;
    Router.push(<span class="hljs-string">'/blogDetail?bid=23'</span>)
&#125;

<span class="hljs-comment">//object 形式</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">gotoBlogDetail</span>(<span class="hljs-params"></span>)</span>&#123;
    Router.push(&#123;
        <span class="hljs-attr">pathname</span>:<span class="hljs-string">"/blogDetail"</span>,
        <span class="hljs-attr">query</span>:&#123;
            <span class="hljs-attr">bid</span>:<span class="hljs-number">23</span>
        &#125;
    &#125;)
&#125;

<Link href=&#123;&#123;<span class="hljs-attr">pathname</span>:<span class="hljs-string">'/blogDetail'</span>,<span class="hljs-attr">query</span>:&#123;<span class="hljs-attr">bid</span>:<span class="hljs-number">23</span>&#125;&#125;><span class="xml"><span class="hljs-tag"><<span class="hljs-name">a</span>></span>博客详情<span class="hljs-tag"></<span class="hljs-name">a</span>></span></span></Link>

<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-9">动态路由</h3>
<pre><code class="copyable">pages/post/[pid].js
route : /post/abc  -->  query : &#123; "pid": "abc" &#125;


pages/post/[pid]/[comment].js
route : /post/abc/a-comment  -->  query : &#123; "pid": "abc", "comment": "a-comment" &#125;


<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-10">钩子事件</h3>
<p>利用钩子事件是可以作很多事情的，比如转换时的加载动画，关掉页面的一些资源计数器.....</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">//路由发生变化时</span>
Router.events.on(<span class="hljs-string">'routeChangeStart'</span>,<span class="hljs-function">(<span class="hljs-params">...args</span>)=></span>&#123;
    <span class="hljs-built_in">console</span>.log(<span class="hljs-string">'1.routeChangeStart->路由开始变化,参数为:'</span>,...args)
&#125;)

<span class="hljs-comment">//路由结束变化时</span>
Router.events.on(<span class="hljs-string">'routeChangeComplete'</span>,<span class="hljs-function">(<span class="hljs-params">...args</span>)=></span>&#123;
    <span class="hljs-built_in">console</span>.log(<span class="hljs-string">'routeChangeComplete->路由结束变化,参数为:'</span>,...args)
&#125;)

<span class="hljs-comment">//浏览器 history触发前</span>
Router.events.on(<span class="hljs-string">'beforeHistoryChange'</span>,<span class="hljs-function">(<span class="hljs-params">...args</span>)=></span>&#123;
    <span class="hljs-built_in">console</span>.log(<span class="hljs-string">'3,beforeHistoryChange->在改变浏览器 history之前触发,参数为:'</span>,...args)
&#125;)

<span class="hljs-comment">//路由跳转发生错误时</span>
Router.events.on(<span class="hljs-string">'routeChangeError'</span>,<span class="hljs-function">(<span class="hljs-params">...args</span>)=></span>&#123;
    <span class="hljs-built_in">console</span>.log(<span class="hljs-string">'4,routeChangeError->跳转发生错误,参数为:'</span>,...args)
&#125;)

<span class="hljs-comment">/****************************hash路由***********************************/</span>

Router.events.on(<span class="hljs-string">'hashChangeStart'</span>,<span class="hljs-function">(<span class="hljs-params">...args</span>)=></span>&#123;
    <span class="hljs-built_in">console</span>.log(<span class="hljs-string">'5,hashChangeStart->hash跳转开始时执行,参数为:'</span>,...args)
&#125;)

Router.events.on(<span class="hljs-string">'hashChangeComplete'</span>,<span class="hljs-function">(<span class="hljs-params">...args</span>)=></span>&#123;
    <span class="hljs-built_in">console</span>.log(<span class="hljs-string">'6,hashChangeComplete->hash跳转完成时,参数为:'</span>,...args)
&#125;)
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-11">获取数据</h2>
<h3 data-id="heading-12"><code>getStaticProps</code></h3>
<p><strong>构建时请求数据</strong></p>
<p>在build阶段将页面构建成静态的html文件，这样线上直接访问HTML文件，性能极高。</p>
<ul>
<li>使用<code>getStaticProps</code>方法在build阶段返回页面所需的数据。</li>
<li>如果是动态路由的页面，使用<code>getStaticPaths</code>方法来返回所有的路由参数，以及是否需要回落机制。</li>
</ul>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-comment">// posts will be populated at build time by getStaticProps()</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">Blog</span>(<span class="hljs-params">&#123; posts &#125;</span>) </span>&#123;
  <span class="hljs-keyword">return</span> (
    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">ul</span>></span>
      &#123;posts.map((post) => (
        <span class="hljs-tag"><<span class="hljs-name">li</span>></span>&#123;post.title&#125;<span class="hljs-tag"></<span class="hljs-name">li</span>></span>
      ))&#125;
    <span class="hljs-tag"></<span class="hljs-name">ul</span>></span></span>
  )
&#125;

<span class="hljs-comment">// This function gets called at build time on server-side.</span>
<span class="hljs-comment">// It won't be called on client-side, so you can even do</span>
<span class="hljs-comment">// direct database queries. See the "Technical details" section.</span>
<span class="hljs-keyword">export</span> <span class="hljs-keyword">async</span> <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">getStaticProps</span>(<span class="hljs-params">context</span>) </span>&#123;
  <span class="hljs-comment">// Call an external API endpoint to get posts.</span>
  <span class="hljs-comment">// You can use any data fetching library</span>
  <span class="hljs-keyword">const</span> res = <span class="hljs-keyword">await</span> fetch(<span class="hljs-string">'https://.../posts'</span>)
  <span class="hljs-keyword">const</span> posts = <span class="hljs-keyword">await</span> res.json()

  <span class="hljs-comment">// By returning &#123; props: &#123; posts &#125; &#125;, the Blog component</span>
  <span class="hljs-comment">// will receive `posts` as a prop at build time</span>
  <span class="hljs-keyword">return</span> &#123;
    <span class="hljs-attr">props</span>: &#123;
      posts,
    &#125;,
  &#125;
&#125;

<span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span> Blog
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-13"><code>getServerSideProps</code></h3>
<p><strong>每次访问时请求数据</strong></p>
<p>页面中<code>export</code>一个<code>async</code>的<code>getServerSideProps</code>方法，next就会在每次请求时候在服务端调用这个方法。</p>
<ul>
<li>方法只会在服务端运行，每次请求都运行一边<code>getServerSideProps</code>方法</li>
<li>如果页面通过浏览器端<code>Link</code>组件导航而来，Next会向服务端发一个请求，然后在服务端运行<code>getServerSideProps</code>方法，然后返回JSON到浏览器。</li>
</ul>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">Page</span>(<span class="hljs-params">&#123; data &#125;</span>) </span>&#123;
  <span class="hljs-comment">// Render data...</span>
&#125;

<span class="hljs-comment">// This gets called on every request</span>
<span class="hljs-keyword">export</span> <span class="hljs-keyword">async</span> <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">getServerSideProps</span>(<span class="hljs-params">context</span>) </span>&#123;
  <span class="hljs-comment">// Fetch data from external API</span>
  <span class="hljs-keyword">const</span> res = <span class="hljs-keyword">await</span> fetch(<span class="hljs-string">`https://.../data`</span>)
  <span class="hljs-keyword">const</span> data = <span class="hljs-keyword">await</span> res.json()

  <span class="hljs-comment">// Pass data to the page via props</span>
  <span class="hljs-keyword">return</span> &#123; <span class="hljs-attr">props</span>: &#123; data &#125; &#125;
&#125;

<span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span> Page
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-14">CSS支持</h2>
<h3 data-id="heading-15">添加全局样式表</h3>
<p>要将样式表添加到您的应用程序中，请在 <code>pages/_app.js</code> 文件中导入（import）CSS 文件。</p>
<p>在生产环境中，所有 CSS 文件将自动合并为一个经过精简的 <code>.css</code> 文件。</p>
<p>你应该 <strong>只在 <a href="https://link.juejin.cn/?target=https%3A%2F%2Fwww.nextjs.cn%2Fdocs%2Fadvanced-features%2Fcustom-app" target="_blank" rel="nofollow noopener noreferrer" title="https://www.nextjs.cn/docs/advanced-features/custom-app" ref="nofollow noopener noreferrer"><code>pages/_app.js</code></a> 文件中导入（import）样式表</strong>。</p>
<p>从 Next.js <strong>9.5.4</strong> 版本开始，你可以在应用程序中的任何位置从 <code>node_modules</code> 目录导入（import） CSS 文件了。</p>
<p>对于导入第三方组件所需的 CSS，可以在组件中进行。</p>
<h3 data-id="heading-16">添加组件级CSS</h3>
<ul>
<li>
<p><code>[name].module.css</code></p>
<pre><code class="hljs language-css copyable" lang="css">//login<span class="hljs-selector-class">.module</span><span class="hljs-selector-class">.css</span>
<span class="hljs-selector-class">.loginDiv</span>&#123;
    <span class="hljs-attribute">color</span>: red;
&#125;

//修改第三方样式
<span class="hljs-selector-class">.loginDiv</span> :<span class="hljs-built_in">global</span>(.active)&#123;
    color:<span class="hljs-built_in">rgb</span>(<span class="hljs-number">30</span>, <span class="hljs-number">144</span>, <span class="hljs-number">255</span>) <span class="hljs-meta">!important</span>;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-keyword">import</span> styles <span class="hljs-keyword">from</span> <span class="hljs-string">'./login.module.css'</span>

<div className=&#123;styles.loginDiv&#125;/>

<span class="copy-code-btn">复制代码</span></code></pre>
<p>Next.js 允许你导入（import）具有 <code>.scss</code> 和 <code>.sass</code> 扩展名的 Sass 文件。 你可以通过 CSS 模块以及 <code>.module.scss</code> 或 <code>.module.sass</code> 扩展名来使用组件及的 Sass</p>
<blockquote>
<p>npm i sass --save</p>
</blockquote>
<p>如果要配置 Sass 编译器，可以使用 <code>next.config.js</code> 文件中的 <code>sassOptions</code> 参数进行配置。</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-keyword">const</span> path = <span class="hljs-built_in">require</span>(<span class="hljs-string">'path'</span>)

<span class="hljs-built_in">module</span>.exports = &#123;
  <span class="hljs-attr">sassOptions</span>: &#123;
    <span class="hljs-attr">includePaths</span>: [path.join(__dirname, <span class="hljs-string">'styles'</span>)],
  &#125;,
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
</li>
<li>
<p><code>CSS-in-JS</code></p>
<p>可以使用任何现有的 CSS-in-JS 解决方案。 最简单的一种是内联样式：</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><p style=&#123;&#123; <span class="hljs-attr">color</span>: <span class="hljs-string">'red'</span> &#125;&#125;>hi there</p>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>使用 <code>styled-jsx</code> 的组件就像这样</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">HelloWorld</span>(<span class="hljs-params"></span>) </span>&#123;
  <span class="hljs-keyword">return</span> (
    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">div</span>></span>
      Hello world
      <span class="hljs-tag"><<span class="hljs-name">p</span>></span>scoped!<span class="hljs-tag"></<span class="hljs-name">p</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">style</span> <span class="hljs-attr">jsx</span>></span><span class="css">&#123;`
        <span class="hljs-selector-tag">p</span> &#123;
          <span class="hljs-attribute">color</span>: blue;
        &#125;
        <span class="hljs-selector-tag">div</span> &#123;
          <span class="hljs-attribute">background</span>: red;
        &#125;
        <span class="hljs-keyword">@media</span> (<span class="hljs-attribute">max-width</span>: <span class="hljs-number">600px</span>) &#123;
          <span class="hljs-selector-tag">div</span> &#123;
            <span class="hljs-attribute">background</span>: blue;
          &#125;
        &#125;
      `&#125;</span><span class="hljs-tag"></<span class="hljs-name">style</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">style</span> <span class="hljs-attr">global</span> <span class="hljs-attr">jsx</span>></span><span class="css">&#123;`
        <span class="hljs-selector-tag">body</span> &#123;
          <span class="hljs-attribute">background</span>: black;
        &#125;
      `&#125;</span><span class="hljs-tag"></<span class="hljs-name">style</span>></span>
    <span class="hljs-tag"></<span class="hljs-name">div</span>></span></span>
  )
&#125;

<span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span> HelloWorld
<span class="copy-code-btn">复制代码</span></code></pre>
</li>
</ul>
<h2 data-id="heading-17">自定义Header</h2>
<pre><code class="hljs language-js copyable" lang="js"><Head>
    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">title</span>></span>技术胖是最胖的！<span class="hljs-tag"></<span class="hljs-name">title</span>></span></span>
    <span class="xml"><span class="hljs-tag"><<span class="hljs-name">meta</span> <span class="hljs-attr">charSet</span>=<span class="hljs-string">'utf-8'</span> /></span></span>
</Head>
<span class="copy-code-btn">复制代码</span></code></pre></div>  
</div>
            
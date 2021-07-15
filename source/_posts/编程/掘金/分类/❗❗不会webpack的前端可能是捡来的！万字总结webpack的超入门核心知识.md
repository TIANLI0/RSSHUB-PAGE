
---
title: '❗❗不会webpack的前端可能是捡来的！万字总结webpack的超入门核心知识'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d70d9b5e09d84341b966bcfa310fe29b~tplv-k3u1fbpfcp-zoom-1.image'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 14:26:00 GMT
thumbnail: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d70d9b5e09d84341b966bcfa310fe29b~tplv-k3u1fbpfcp-zoom-1.image'
---

<div>   
<div class="markdown-body"><style>@charset "UTF-8";.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1:first-child,.markdown-body h2:first-child,.markdown-body h3:first-child,.markdown-body h4:first-child,.markdown-body h5:first-child,.markdown-body h6:first-child&#123;margin-top:-1.5rem;margin-bottom:1rem&#125;.markdown-body h1:before,.markdown-body h2:before,.markdown-body h3:before,.markdown-body h4:before,.markdown-body h5:before,.markdown-body h6:before&#123;content:"#";display:inline-block;color:#3eaf7c;padding-right:.23em&#125;.markdown-body h1&#123;position:relative;font-size:2.5rem;margin-bottom:5px&#125;.markdown-body h1:before&#123;font-size:2.5rem&#125;.markdown-body h2&#123;padding-bottom:.5rem;font-size:2.2rem;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:1.5rem;padding-bottom:0&#125;.markdown-body h4&#123;font-size:1.25rem&#125;.markdown-body h5&#123;font-size:1rem&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body strong&#123;color:#3eaf7c&#125;.markdown-body img&#123;max-width:100%;border-radius:2px;display:block;margin:auto;border:3px solid rgba(62,175,124,.2)&#125;.markdown-body hr&#123;border:none;border-top:1px solid #3eaf7c;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;overflow-x:auto;padding:.2rem .5rem;margin:0;color:#3eaf7c;font-weight:700;font-size:.85em;background-color:rgba(27,31,35,.05);border-radius:3px&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75;border-radius:6px;border:2px solid #3eaf7c&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;font-weight:500;text-decoration:none;color:#3eaf7c&#125;.markdown-body a:active,.markdown-body a:hover&#123;border-bottom:1.5px solid #3eaf7c&#125;.markdown-body a:before&#123;content:"⇲"&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #3eaf7c&#125;.markdown-body thead&#123;background:#3eaf7c;color:#fff;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:rgba(62,175,124,.2)&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:.5rem solid;border-color:#42b983;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body details&#123;outline:none;border:none;border-left:4px solid #3eaf7c;padding-left:10px;margin-left:4px&#125;.markdown-body details summary&#123;cursor:pointer;border:none;outline:none;background:#fff;margin:0 -17px&#125;.markdown-body details summary::-webkit-details-marker&#123;color:#3eaf7c&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body ol li::marker&#123;color:#3eaf7c&#125;.markdown-body ul li&#123;list-style:none&#125;.markdown-body ul li:before&#123;content:"•";margin-right:4px;color:#3eaf7c&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><p>「本文已参与好文召集令活动，点击查看：<a href="https://juejin.cn/post/6978685539985653767" target="_blank" title="https://juejin.cn/post/6978685539985653767">后端、大前端双赛道投稿，2万元奖池等你挑战！</a>」</p>
<h1 data-id="heading-0">🎨序言</h1>
<p>众所周知，在前端工程化日趋复杂的今天，模块化打包工具在我们的日常开发中起着越来越重要的作用，而其中， <code>webpack</code> 已然是前端打包构建的不二选择。</p>
<p>说到 <code>webpack</code> ，可能很多小伙伴会觉得既熟悉又陌生，熟悉是因为在我们开发的每一个项目中，都会使用到它。而陌生在于， <code>webpack</code> 有着复杂的配置和五花八门的功能而感到陌生。</p>
<p>因此，我们有时候会被这复杂的配置先吓到，从而被劝退学习。</p>
<p>然而，在技术更新迭代这么快的一个大环境下， <code>webpack</code> 还是很值得我们去学习的。</p>
<p>在下面的这篇文章中，将讲解 <code>webpack</code> 的入门核心概念。一起来学习吧~🎬</p>
<h1 data-id="heading-1">📅一、webpack究竟是什么</h1>
<h2 data-id="heading-2">1、写在前面</h2>
<p>当我们要写一个网页时，首先我们会先创建一个 <code>index.html</code> 文件，之后在可能还会有一些 <code>js</code> 文件，那么我们就会在 <code>html</code> 文件中，引入这些 <code>js</code> 文件。</p>
<p>试想一下，如果 <code>js</code> 文件很多，然后我们一个个引入，这样如果遇到报错了呢？会不会就很难定位到是哪个文件错了，这样就会使得开发效率非常低下了。</p>
<p>因此，就有了 <code>webpack</code> 。 <code>webpack</code> 会将我们所写的代码，进行一个翻译，并将翻译完的内容，进行一个模块化的打包，使得项目变得工程化。</p>
<p>接下来，我们就来讲解， <code>webpack</code> 究竟是什么以及怎么安装使用。</p>
<h2 data-id="heading-3">2、什么是模块打包工具？</h2>
<p><code>webpack</code> 有时候会被误认为是一个 <code>js</code> 的翻译器，但其实 <code>webpack</code> 称不上是一个 <code>js</code> 的翻译器。</p>
<p>因为它只认识 <code>import</code> 这样类似的语句，而不认识其他的 <code>js</code> 高级语法。所以如果称它是一个 <code>js</code> 的翻译器，实际上是我们高看了它。</p>
<p>查看官方的定义我们可以发现， <code>webpack</code> 是一个<strong>模块打包工具</strong>，同时 <code>webpack</code> 也可以支持 <code>commonjs</code> 的模块打包规范。</p>
<p>然而，随着时间的推移和技术的不断更新， <code>webpack</code> 不再是只会打包 <code>js</code> 的<strong>模块打包工具</strong>， <code>webpack</code> 现在还支持 <code>css文件</code> 、 <code>jpg</code> 、 <code>png</code> 等各种文件的打包。</p>
<h1 data-id="heading-4">📐二、如何用Webpack搭建环境</h1>
<h2 data-id="heading-5">1、安装node</h2>
<p><code>webpack</code> 是基于 <code>nodejs</code> 开发的模块打包工具，本质上是由 <code>node</code> 实现的。因此我们要先安装本机的 <code>node</code> 环境。<a href="https://link.juejin.cn/?target=https%3A%2F%2Fnodejs.org%2Fzh-cn%2F" target="_blank" rel="nofollow noopener noreferrer" title="https://nodejs.org/zh-cn/" ref="nofollow noopener noreferrer">这里附上官方网站的链接，建议大家下载稳定版本</a></p>
<p>之后查询本机的 <code>node</code> 和 <code>npm</code> 版本，查看是否安装成功。</p>
<pre><code class="hljs language-bash copyable" lang="bash">node -v
npm -v
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-6">2、创建项目</h2>
<p>先创建一个项目，假设命名为 <code>webpack-demo</code> 。之后在该项目下<strong>通过以下命令创建一个文件夹：</strong></p>
<pre><code class="hljs language-bash copyable" lang="bash">mkdir webpack-demo
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-7">3、初始化项目</h2>
<p>进入 <code>webpack-demo</code> 文件，初始化项目。<strong>命令行如下：</strong></p>
<pre><code class="hljs language-bash copyable" lang="bash"><span class="hljs-built_in">cd</span> webpack-demo
npm init 或 npm init -y //加-y表示默认自动配置项
<span class="copy-code-btn">复制代码</span></code></pre>
<p>之后一路 <code>Enter</code> 回车即可。</p>
<p>大家可以看到项目结构，以上操作就是在 <code>webpack-demo</code> 文件下创建了一个 <code>package.json</code> 文件，之后我们把 <code>package.json</code> 文件的内进行改造。<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-json copyable" lang="json">&#123;
  <span class="hljs-attr">"name"</span>: <span class="hljs-string">"webpack-demo"</span>,
  <span class="hljs-attr">"version"</span>: <span class="hljs-string">"1.0.0"</span>,
  <span class="hljs-attr">"description"</span>: <span class="hljs-string">""</span>,
    <span class="hljs-comment">//将这个项目设置为私有</span>
  <span class="hljs-attr">"private"</span>:<span class="hljs-literal">true</span>,
  <span class="hljs-comment">//"main": "index.js", //去掉入口文件</span>
  <span class="hljs-attr">"scripts"</span>: &#123;
    <span class="hljs-attr">"test"</span>: <span class="hljs-string">"echo \"Error: no test specified\" && exit 1"</span>
  &#125;,
  <span class="hljs-comment">//写上作者名</span>
  <span class="hljs-attr">"author"</span>: <span class="hljs-string">"Monday"</span>,
  <span class="hljs-comment">//保持项目私有</span>
  <span class="hljs-attr">"license"</span>: <span class="hljs-string">"ISC"</span>
&#125;

<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-8">4、安装webpack</h2>
<p><strong>第一种方式：全局安装</strong></p>
<pre><code class="hljs language-bash copyable" lang="bash">npm install webpack webpack-cli -g
<span class="copy-code-btn">复制代码</span></code></pre>
<p><strong>第二种方式：当前项目下安装</strong></p>
<pre><code class="hljs language-bash copyable" lang="bash">npm install webpack webpack-cli -D
<span class="copy-code-btn">复制代码</span></code></pre>
<p>在这里的建议是选择第二种方式进行安装。那为什么呢？是因为全局安装 <code>webpack</code> 有什么问题吗？</p>
<p>事实上，全局安装只会安装一个版本。</p>
<p>那么假如我们现在要跑两个项目，并且这两个项目出现原先安装的 <code>webpack</code> 版本不一样，安装低版本 <code>webpack</code> 的项目，就有可能会导致在我们的本机中运行不起来。所以建议是使用第二种方式进行安装。</p>
<hr>
<p>安装完成之后，我们还要来查询当前使用的 <code>webpack</code> 版本号，以确保我们是否已经安装成功。<strong>具体命令行如下：</strong></p>
<pre><code class="hljs language-bash copyable" lang="bash">npx webpack -v
<span class="copy-code-btn">复制代码</span></code></pre>
<p>这个时候就有小伙伴会有疑问说，为什么前面还要加个 <code>npx</code> 才能查找版本号。</p>
<p>原因在于，我们只在当前项目中安装，所以 <code>webpack</code> 这个命令在全局中并没有找到。而 <code>node</code> 提供了 <code>npx</code> ，这个时候 <code>npx</code> 就可以找到我们所运行项目目录下的 <code>node-module</code> 中的 <code>webpack</code> 安装包，所以这种方式是把我们的 <code>webpack</code> 安装在我们的项目内，然后通过 <code>npx</code> 去运行 <code>webpack</code> 就可以了。</p>
<h2 data-id="heading-9">5、安装具体版本的webpack</h2>
<p>如果我们想要安装具体版本号的 <code>webpack</code> ，那么我们先查看 <code>webpack</code> 的版本号信息。<strong>命令如下：</strong></p>
<pre><code class="hljs language-bash copyable" lang="bash">npm info webpack
<span class="copy-code-btn">复制代码</span></code></pre>
<p>查到具体版本号以后，使用以下命令进行安装：</p>
<pre><code class="hljs language-bash copyable" lang="bash">npm install webpack@4.16.5 webpack-cli -D //4.16.5表示版本号
<span class="copy-code-btn">复制代码</span></code></pre>
<h1 data-id="heading-10">⚙️三、Webpack的配置文件</h1>
<h2 data-id="heading-11">1、默认配置文件</h2>
<p>很多时候，我们还没写配置文件，项目就成功跑起来了。这并不是因为不用写，而是 <code>webpack</code> 团队提前帮我们写好了很多<strong>默认的配置文件</strong>，使得我们在运行项目时不用进行过多的配置就可以达到我们的使用需求。那下面，就跟着大家一起来写一个配置文件。</p>
<p>我们先来了解下项目结构，在我们创建完项目时，我们的源代码一般放在 <code>src</code> 文件夹下，并且打包后的文件一般放在 <code>dist</code> 文件下，同时 <code>webpack</code> 的配置文件命名为 <code>webpack.config.js</code> ，并且放在项目的根目录下。</p>
<pre><code class="hljs language-bash copyable" lang="bash">├── dist 放置打包后的文件
├── src 放置项目源代码
├── webpack.config.js webpack配置文件
├── package-lock.json
├── package.json
<span class="copy-code-btn">复制代码</span></code></pre>
<p>看完项目结构，我们来了解一下 <code>webpack</code> 的<strong>配置文件</strong>具体需要怎么配置。<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">//node的核心模块</span>
<span class="hljs-keyword">const</span> path = <span class="hljs-built_in">require</span>(<span class="hljs-string">'path'</span>);

<span class="hljs-built_in">module</span>.exports = &#123;
    <span class="hljs-comment">//设置为development时，代码不会进行压缩；设置为production时，代码会进行压缩。</span>
    <span class="hljs-attr">mode</span>:<span class="hljs-string">'production'</span>,
<span class="hljs-comment">// 放置入口文件，明确怎么打包，要打包哪一个文件</span>
<span class="hljs-attr">entry</span>: <span class="hljs-string">'./src/index.js'</span>,
    <span class="hljs-comment">//entry: &#123;</span>
    <span class="hljs-comment">//    main: './src/index.js'</span>
    <span class="hljs-comment">//&#125;,</span>
<span class="hljs-comment">// 输出，表明webpack应该怎么输出，输出到哪个地方</span>
<span class="hljs-attr">output</span>: &#123;
<span class="hljs-attr">filename</span>: <span class="hljs-string">'bundle.js'</span>,
<span class="hljs-comment">// 指打包后的文件要放在哪个文件下</span>
        <span class="hljs-comment">// __dirname表示该项目的根目录</span>
<span class="hljs-attr">path</span>: path.resolve(__dirname, <span class="hljs-string">'dist'</span>)
&#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>了解完基本配置，此时可能有小伙伴心里有一个疑惑， <code>webpack</code> 配置文件的命名一定要命名为 <code>webpack.config.js</code> 吗，是否可以命名为其他的呢？</p>
<p><strong>答案是肯定可以的</strong>，不过我们需要进行一个特殊处理。平常如果我们命名为 <code>webpack.config.js</code> 时，可以直接使用 <code>npm webpack</code> 来跑我们的项目。如果不用这个命名时，假设命名为 <code>webpackconfig.js</code> ，那么我们可以通过以下命令行，来打包我们具体的项目。</p>
<pre><code class="hljs language-bash copyable" lang="bash"> npx webpack --config webpackconfig.js 
<span class="copy-code-btn">复制代码</span></code></pre>
<p>以上命令行的意思为：指让 <code>webpack</code> 来帮我们打包，具体打包哪一个文件呢？以 <code>webpackconfig.js</code> 为配置文件，来帮我们打包。</p>
<h2 data-id="heading-12">2、用npm script来简化我们的打包代码</h2>
<p>看完上面的内容，相信小伙伴们对 <code>webpack</code> 有了一个基础的认识。</p>
<p>那试想以下，经常要使用 <code>npx webpack</code> 来帮我们打包文件，这样是不是会有点略显麻烦呢？</p>
<p>所以，我们来再了解一个内容：使用 <code>npm script</code> 来简化我们的打包代码。</p>
<p>在我们的项目根目录下，会有一个 <code>package.json</code> 文件，这个文件的<strong>代码如下：</strong></p>
<pre><code class="hljs language-json copyable" lang="json">&#123;
  <span class="hljs-attr">"name"</span>: <span class="hljs-string">"webpack-demo"</span>,
  <span class="hljs-attr">"version"</span>: <span class="hljs-string">"1.0.0"</span>,
  <span class="hljs-attr">"description"</span>: <span class="hljs-string">""</span>,
  <span class="hljs-attr">"private"</span>: <span class="hljs-literal">true</span>,
  <span class="hljs-attr">"main"</span>: <span class="hljs-string">"index.js"</span>,
  <span class="hljs-attr">"scripts"</span>: &#123;
    <span class="hljs-attr">"test"</span>: <span class="hljs-string">"echo \"Error: no test specified\" && exit 1"</span>
  &#125;,
  <span class="hljs-attr">"author"</span>: <span class="hljs-string">"Monday"</span>,
  <span class="hljs-attr">"license"</span>: <span class="hljs-string">"ISC"</span>,
  <span class="hljs-attr">"devDependencies"</span>: &#123;
    <span class="hljs-attr">"webpack"</span>: <span class="hljs-string">"^5.39.1"</span>,
    <span class="hljs-attr">"webpack-cli"</span>: <span class="hljs-string">"^4.7.2"</span>
  &#125;
&#125;

<span class="copy-code-btn">复制代码</span></code></pre>
<p>大家定位到scripts部分，接下来，我们把script部分进行一个改造。具体代码如下：</p>
<pre><code class="hljs language-json copyable" lang="json"> <span class="hljs-string">"scripts"</span>: &#123;
    <span class="hljs-comment">/* webpack 会先到node_module下面进行打包*/</span>
    <span class="hljs-attr">"bundle"</span>: <span class="hljs-string">"webpack"</span>
  &#125;,
<span class="copy-code-btn">复制代码</span></code></pre>
<p>改造完成以后，我们就相当于在 <code>package.json</code> 里面配置了一个 <code>npm script</code> ，上面的代码意思为这个 <code>script</code> 对应的名字叫做 <code>bundle</code> ，之后呢， <code>bundle</code> 的底层会帮助我们执行 <code>webpack</code> ，并进行打包。</p>
<p>这么编写之后，我们就不再需要使用 <code>npx webpack</code> 来做运行 <code>webpack</code> ，而是使用 <code>npm run bundle</code> 来做命令进行打包。</p>
<h2 data-id="heading-13">3、浅谈webpack打包输出内容</h2>
<p>讲解完上面的内容，我们来对 <code>webpack</code> 打包以后控制台的一些输出内容进行归纳总结。</p>





































<table><thead><tr><th align="center">输出内容</th><th align="center">具体含义</th></tr></thead><tbody><tr><td align="center">hash</td><td align="center">代表本次打包对应的唯一哈希值</td></tr><tr><td align="center">version</td><td align="center">代表此次打包使用的webpack的版本</td></tr><tr><td align="center">time</td><td align="center">当前项目整体打包的具体耗时</td></tr><tr><td align="center">assets</td><td align="center">打包后的文件具体是哪一个，比如：bundle.js</td></tr><tr><td align="center">size</td><td align="center">打包后文件的大小</td></tr><tr><td align="center">chunks</td><td align="center">放置自己对应文件的id值以及对应文件所引入其他文件的id值</td></tr><tr><td align="center">chunk Names</td><td align="center">对应entry配置的main</td></tr></tbody></table>
<h1 data-id="heading-14">🔑四、Loader</h1>
<h2 data-id="heading-15">1、引例阐述</h2>
<p><code>Webpack</code> 默认是知道如何打包 <code>js</code> 模块的，但是它不知道 <code>jpg</code> 这种文件该怎么打包。</p>
<p>这个时候我们需要在 <code>webpack.config.js</code> 文件下做配置，配置 <code>file-loader</code> 。我们在配置中增加一个新的 <code>module</code> 。<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>:&#123;
    <span class="hljs-attr">rules</span>:[&#123;
        <span class="hljs-attr">test</span>:<span class="hljs-regexp">/\.jpg$/</span>,
        use:&#123;
            <span class="hljs-attr">loader</span>:<span class="hljs-string">'file-loader'</span>
        &#125;
    &#125;]
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>接下来我们来正向分析下 <code>webpack</code> 是如何打包 <code>jpg</code> 这种静态文件的。</p>
<p>首先 <code>webpack</code> 会进入<code>src</code> 目录， <code>new</code> 一个 <code>index.js</code> 文件，那么现在我们要对这个文件进行打包。</p>
<p>所以，我在命令行里，运行了 <code>npm run bundle</code> 。当你运行 <code>npm run bundle</code> 时，实际上在执行的是 <code>package.json</code> 里面的 <code>script</code> ，这个 <code>script</code> 帮我们运行 <code>webpack</code> ，然后呢， <code>webpack</code> 帮我们做打包。这个时候 <code>webpack</code> 就会去找它相对应的配置，根据这个配置帮我们做打包。</p>
<p>那么我们来看一下，如果我们遇到的是 <code>js</code> 文件，那么 <code>webpack</code> 默认会进行打包。但是呢？如果遇到的是一张 <code>jpg</code> 的图片呢？ <code>webpack</code> 这个时候就懵了， <code>webpack</code> 并不认识 <code>jpg</code> 这种格式的代码。</p>
<p>因此，我们就可以引用一个模块module，来帮我们打包。这个模块叫 <code>file-loader</code> ，<code>file-loader</code> 这个 <code>loader</code> 就可以帮助我们完成打包的过程。</p>
<p>那么实际上， <code>file-loader</code> 的底层，帮我们做了什么事情呢？</p>
<p>当我们打包 <code>jpg</code> 文件时， <code>webpack</code> 会把 <code>jpg</code> 文件移动到 <code>dist</code> 文件下，并且对 <code>jpg</code> 文件赋予一个新的名称。然后呢，它会把这个名称作为一个返回值，返回给我们引入模块的变量之中。</p>
<p>这就是 <code>file-loader</code> 底层处理打包文件的一个流程。</p>
<p>当然。 <code>file-loader</code> 不仅仅可以处理 <code>jpg</code> 这样的文件图片。理论上，它还可以处理<strong>很多种类型的静态资源</strong>。</p>
<h2 data-id="heading-16">2、什么是Loader</h2>
<p>阐述了 <code>file-loader</code> 之后，相信大家对 <code>loader </code> 有了一个基础认识。那么我们现在就来对loader的基础定义进行梳理。<strong>具体如下：</strong></p>
<p>本身 <code>webpack</code> 对于一些文件是不知道如何处理的，但是 <code>loader</code> 知道。所以呢，当遇到一些 <code>非js</code> 文件时，一般去求助于 <code>loader</code> 就可以了。因此我们就需要让 <code>webpack</code> 去求助 <code>loader</code> 模块，来识别出 <code>非js</code> 的文件。</p>
<p>引用 <code>webpack</code> 官方中文文档的一句话，文档中说到： <code>webpack</code> 只能理解 <code>JavaScript</code> 和 <code>JSON</code> 文件，这是 <code>webpack</code> 开箱可用的自带能力。<strong>loader</strong> 让 <code>webpack</code> 能够去处理其他类型的文件，并将它们转换为有效模块，以供<strong>应用程序</strong>使用，以及被添加到<strong>依赖图</strong>中。本质上， <code>loader</code> 是导出为函数的 <code>JavaScript</code> 模块。</p>
<h2 data-id="heading-17">3、使用Loader打包静态资源（图片篇）</h2>
<h3 data-id="heading-18">（1）自定义命名图片</h3>
<p>如果我们现在要对打包后的图片进行自定义命名，那该怎么做呢？</p>
<p>我们在 <code>webpack.config.js</code> 文件下的 <code>module</code> 再进行改进。<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>:&#123;
    <span class="hljs-attr">rules</span>:[&#123;
        <span class="hljs-attr">test</span>:<span class="hljs-regexp">/\.jpg$/</span>,
        use:&#123;
            <span class="hljs-attr">loader</span>:<span class="hljs-string">'file-loader'</span>,
            <span class="hljs-attr">options</span>: &#123;
                <span class="hljs-comment">//placeholder 占位符</span>
                <span class="hljs-attr">name</span>: <span class="hljs-string">'[name]_[hash].[ext]'</span>
            &#125;
        &#125;
    &#125;]
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>通过配置 <code>options</code> ，就可以达到图片自定义命名的效果。</p>
<h3 data-id="heading-19">（2）打包各种类型的图片文件</h3>
<p>假设我们现在不局限于打包 <code>jpg</code> 文件，还想要打包其他的图片文件。<strong>那么我们可以这样配置：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>:&#123;
    <span class="hljs-attr">rules</span>:[&#123;
        <span class="hljs-attr">test</span>:<span class="hljs-regexp">/\.(jpg|png|gif)$/</span>,
        use:&#123;
            <span class="hljs-attr">loader</span>:<span class="hljs-string">'file-loader'</span>,
            <span class="hljs-attr">options</span>: &#123;
                <span class="hljs-comment">//placeholder 占位符</span>
                <span class="hljs-attr">name</span>: <span class="hljs-string">'[name]_[hash].[ext]'</span>
            &#125;
        &#125;
    &#125;]
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>通过正则表达式的方式，来增加新的图片类型。</p>
<h3 data-id="heading-20">（3）打包到image文件下</h3>
<p>假设我们现在想要把打包后的文件放到 <code>image</code> 文件下，那该怎么做呢？<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>:&#123;
    <span class="hljs-attr">rules</span>:[&#123;
        <span class="hljs-attr">test</span>:<span class="hljs-regexp">/\.(jpg|png|gif)$/</span>,
        use:&#123;
            <span class="hljs-attr">loader</span>:<span class="hljs-string">'file-loader'</span>,
            <span class="hljs-attr">options</span>: &#123;
                <span class="hljs-comment">//placeholder 占位符</span>
                <span class="hljs-attr">name</span>: <span class="hljs-string">'[name]_[hash].[ext]'</span>,
                <span class="hljs-comment">//将jpg、png和gif图片文件，指定到dist目录下的images文件下</span>
                <span class="hljs-attr">outputPath</span>: <span class="hljs-string">'images/'</span>
            &#125;
        &#125;
    &#125;]
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-21">（4）url-loader</h3>
<p>在使用了 <code>file-loader</code> 之后，我们再来了解一个知识点： <code>url-loader</code> 。 <code>url-loader</code> 可以达到几近 <code>file-loader</code> 的效果。具体使用方法如下：</p>
<pre><code class="hljs language-bash copyable" lang="bash">npm i url-loader -D
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>:&#123;
    <span class="hljs-attr">rules</span>:[&#123;
        <span class="hljs-attr">test</span>:<span class="hljs-regexp">/\.(jpg|png|gif)$/</span>,
        use:&#123;
            <span class="hljs-attr">loader</span>:<span class="hljs-string">'url-loader'</span>,
            <span class="hljs-attr">options</span>: &#123;
                <span class="hljs-attr">name</span>: <span class="hljs-string">'[name]_[hash].[ext]'</span>,
                <span class="hljs-attr">outputPath</span>: <span class="hljs-string">'images/'</span>
            &#125;
        &#125;
    &#125;]
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>我们只要安装上 <code>url-loader</code> ，并且在配置中将 <code>file-loader</code> 替换为 <code>url-loader</code> 即可。</p>
<p>但值得注意的是，使用 <code>url-loader</code> 进行打包，会有一些需要注意的事项。</p>
<p>当你去打包一个 <code>jpg</code> 文件的时候，与 <code>file-loader</code> 不一样的是， <code>url-loader</code> 会将图片转换成一个 <code>base64</code> 的字符串，然后直接放到我们 <code>dist</code> 目录下的 <code>bundle.js</code> 里面，而不是单独生成一个图片文件。</p>
<p>好处就是，直接访问，而不用去文件夹下访问，节省了一次 <code>http</code> 请求。</p>
<p>而带来的坏处就是，如果这个 <code>js</code> 文件特别大，那么打包生成的js文件也将会特别大，随之加载这个 <code>js</code> 的时间就会很长。</p>
<p>所以， <code>url-loader</code> 的最佳使用方式是什么呢？</p>
<p>如果说我们引入的图片很小，只有 <code>1~2KB</code> 等小的体积，那么这个图片以 <code>base64</code> 的形式打包到 <code>js</code> 文件里，是一个很好的选择，就没有必要让这么小的图片再去发一次 <code>http</code> 请求。</p>
<p>但假设这个图片很大的话，那么尽量不要使用 <code>url-loader</code> ，而使用 <code>file-loader</code> ，把这个图片打包到dist目录下，不要打包到 <code>bundle.js</code> 里面。不然会使得 <code>bundle.js</code> 文件变得很大，使得加载时间变得很长，不利于维护。</p>
<p>还有一种方法就是，我们可以直接在 <code>url-loader</code> 下再加一个配置： <code>limit</code> 。<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>:&#123;
    <span class="hljs-attr">rules</span>:[&#123;
        <span class="hljs-attr">test</span>:<span class="hljs-regexp">/\.(jpg|png|gif)$/</span>,
        use:&#123;
            <span class="hljs-attr">loader</span>:<span class="hljs-string">'url-loader'</span>,
            <span class="hljs-attr">options</span>: &#123;
                <span class="hljs-attr">name</span>: <span class="hljs-string">'[name]_[hash].[ext]'</span>,
                <span class="hljs-attr">outputPath</span>: <span class="hljs-string">'images/'</span>,
                <span class="hljs-comment">//20480=>20KB</span>
                <span class="hljs-attr">limit</span>: <span class="hljs-number">20480</span>
            &#125;
        &#125;
    &#125;]
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>通过以上代码我们可以知道，当使用 <code>url-loader</code> 时，我们可以给其加一个 <code>limit</code> 属性。那么上面代码所要表达的意思就是，当图片文件大小大于 <code>20KB</code> 时，我们使用 <code>url-loader</code> 打包。当大于 <code>20KB</code> 时，就将图片文件放到 <code>dist</code> 的 <code>images</code> 文件下。</p>
<h2 data-id="heading-22">4、使用Loader打包静态资源（样式篇）</h2>
<h3 data-id="heading-23">（1）打包css文件</h3>
<p>比如说，我们现在想要让一张图片的大小为 <code>150*150</code> ，那么我们就需要写下样式来修改这张图片。那 <code>webpack</code> 如何打包 <code>css</code> 文件呢？</p>
<p>我们可以使用 <code>css-loader</code> 和 <code>style-loader</code> 来对文件进行打包。<strong>具体配置如下：</strong></p>
<pre><code class="hljs language-bash copyable" lang="bash">npm install sass-loader node-sass --save-dev
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>:&#123;
    <span class="hljs-attr">rules</span>:[&#123;
        <span class="hljs-attr">test</span>:<span class="hljs-regexp">/\.(jpg|png|gif)$/</span>,
        use:&#123;
            <span class="hljs-attr">loader</span>:<span class="hljs-string">'file-loader'</span>,
            <span class="hljs-attr">options</span>: &#123;
                <span class="hljs-comment">//placeholder 占位符</span>
                <span class="hljs-attr">name</span>: <span class="hljs-string">'[name]_[hash].[ext]'</span>,
                <span class="hljs-attr">outputPath</span>: <span class="hljs-string">'images/'</span>
            &#125;
        &#125;
    &#125;,&#123;
        <span class="hljs-attr">test</span>:<span class="hljs-regexp">/\.css$/</span>,
        use:[<span class="hljs-string">'style-loader'</span>, <span class="hljs-string">'css-loader'</span>]
    &#125;]
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><code>css-loader</code> 会帮我们分析出，几个 <code>css</code> 文件之间的关系，最终把一个 <code>css</code> 文件，合并成一个 <code>css</code> 。那 <code>style-loader</code> 的作用又是是什么呢？</p>
<p>在得到了 <code>css-loader</code> 生成的 <code>css</code> 文件之后， <code>style-loader</code> 会把这段内容挂载到页面的 <code>head</code> 部分，并将样式挂载到 <code>head</code> 中的 <code><style></style></code> 里面。</p>
<h3 data-id="heading-24">（2）打包sass文件</h3>
<p>如果是要打包 <code>sass</code> 文件呢，则使用 <code>sass-loader</code> 、 <code>style-loader</code> 和 <code>css-loader</code> 这三个 <code>loader</code> 来对文件进行打包。<strong>具体配置如下：</strong></p>
<pre><code class="hljs language-bash copyable" lang="bash">npm install sass-loader node-sass --save-dev
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>:&#123;
    <span class="hljs-attr">rules</span>:[&#123;
        <span class="hljs-attr">test</span>:<span class="hljs-regexp">/\.(jpg|png|gif)$/</span>,
        use:&#123;
            <span class="hljs-attr">loader</span>:<span class="hljs-string">'file-loader'</span>,
            <span class="hljs-attr">options</span>: &#123;
                <span class="hljs-comment">//placeholder 占位符</span>
                <span class="hljs-attr">name</span>: <span class="hljs-string">'[name]_[hash].[ext]'</span>,
                <span class="hljs-attr">outputPath</span>: <span class="hljs-string">'images/'</span>
            &#125;
        &#125;
    &#125;,&#123;
        <span class="hljs-attr">test</span>:<span class="hljs-regexp">/\.scss$/</span>,
        use:[
            <span class="hljs-string">'style-loader'</span>, 
            <span class="hljs-string">'css-loader'</span>, 
            <span class="hljs-string">'sass-loader'</span>
        ]
    &#125;]
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>值得注意的是， <code>loader</code> 的执行顺序是<strong>从下到上，从右到左</strong>。</p>
<p>所以当我们去执行一个 <code>sass</code> 文件时，首先会执行 <code>sass-loader</code> ，之后执行 <code>css-loader</code> ，最后才执行 <code>style-loader</code> 。</p>
<h3 data-id="heading-25">（3）兼容性问题</h3>
<p>有时候我们如果想要兼容多个浏览器时，那么我们可能会在 <code>css</code> 文件里面添加 <code>-webkit-</code> 等厂商的前缀。但是呢，要知道 <code>webpack</code> 是没办法识别这些前缀的。这个时候我们了解一个新的 <code>loader</code> ，就是 <code>postcss-loader</code> ，这个loader可以自动地帮我们添加<strong>厂商前缀</strong>的信息。<strong>具体使用方式如下：</strong></p>
<p>首先我们先安装 <code>postcss-loader</code> 这个库，具体代码如下：</p>
<pre><code class="hljs language-bash copyable" lang="bash">npm i postcss-loader -D
<span class="copy-code-btn">复制代码</span></code></pre>
<p>安装完成之后，我们在项目根目录下创建一个新的文件，名字叫 <code>postcss.config.js</code> ，之后对这个文件进行配置，<strong>代码如下：</strong></p>
<p>首先安装 <code>autoprefixer</code> ：</p>
<pre><code class="hljs language-bash copyable" lang="bash">npm install autoprefixer -D
<span class="copy-code-btn">复制代码</span></code></pre>
<p>安装完成之后，现在我们在  <code>postcss.config.js</code>  文件下来使用它，<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>.exports = &#123;
    <span class="hljs-attr">Plugin</span>:[
        <span class="hljs-built_in">require</span>(<span class="hljs-string">'autoprefixer'</span>)
    ]
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>接下来我们在 <code>webpack.config.js</code> 文件下面，使用 <code>postcss-loader</code> 。<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>:&#123;
    <span class="hljs-attr">rules</span>:[&#123;
        <span class="hljs-attr">test</span>:<span class="hljs-regexp">/\.(jpg|png|gif)$/</span>,
        use:&#123;
            <span class="hljs-attr">loader</span>:<span class="hljs-string">'file-loader'</span>,
            <span class="hljs-attr">options</span>: &#123;
                <span class="hljs-comment">//placeholder 占位符</span>
                <span class="hljs-attr">name</span>: <span class="hljs-string">'[name]_[hash].[ext]'</span>,
                <span class="hljs-attr">outputPath</span>: <span class="hljs-string">'images/'</span>
            &#125;
        &#125;
    &#125;,&#123;
        <span class="hljs-attr">test</span>:<span class="hljs-regexp">/\.scss$/</span>,
        use:[
            <span class="hljs-string">'style-loader'</span>, 
            <span class="hljs-string">'css-loader'</span>, 
            <span class="hljs-string">'sass-loader'</span>,
            <span class="hljs-string">'postcss-loader'</span>
        ]
    &#125;]
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>通过以上方式， <code>webpack </code> 就可以在帮我们打包静态文件时，把对应的需要加入厂商前缀的样式给添加上前缀。</p>
<h2 data-id="heading-26">5、增加配置项</h2>
<p>假设我们现在想要给某一个 <code>loader</code> 增加配置项，比如说我们要给 <code>css-loader</code> 增加配置项，那么我们可以对代码进行如下处理。<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>:&#123;
    <span class="hljs-attr">rules</span>:[&#123;
        <span class="hljs-attr">test</span>:<span class="hljs-regexp">/\.(jpg|png|gif)$/</span>,
        use:&#123;
            <span class="hljs-attr">loader</span>:<span class="hljs-string">'file-loader'</span>,
            <span class="hljs-attr">options</span>: &#123;
                <span class="hljs-comment">//placeholder 占位符</span>
                <span class="hljs-attr">name</span>: <span class="hljs-string">'[name]_[hash].[ext]'</span>,
                <span class="hljs-attr">outputPath</span>: <span class="hljs-string">'images/'</span>
            &#125;
        &#125;
    &#125;,&#123;
        <span class="hljs-attr">test</span>:<span class="hljs-regexp">/\.scss$/</span>,
        use:[
            <span class="hljs-string">'style-loader'</span>, 
            &#123;
                <span class="hljs-attr">loader</span>: <span class="hljs-string">'css-loader'</span>,
                <span class="hljs-attr">options</span>: &#123;
                    <span class="hljs-comment">//表明前面要先走sass-loader和postcss-loader</span>
                    <span class="hljs-attr">importLoaders</span>: <span class="hljs-number">2</span>
                &#125;
            &#125;, 
            <span class="hljs-string">'sass-loader'</span>,
            <span class="hljs-string">'postcss-loader'</span>
        ]
    &#125;]
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>从以上代码中我们可以看到，当我们想要给 <code>css-loader</code> 增加配置项时，那么不再使用字符串的形式，我们把字符串转化成一个对象。在对象里面，我们填写相应的 <code>loader</code> 和 <code>options</code> 配置，这样就达到了我们想要的需求。</p>
<hr>
<p>有时候我们在一个页面上，如果全局引入 <code>css</code> ，可能会很容易导致<strong>样式冲突问题</strong>。那这种情况该怎么处理呢？</p>
<p>为此我们可以借助 <code>css-loader</code> 中的 <code>modules</code> 来实现 <code>css</code> 的模块化，旨在让引入的 <code>css</code> 文件拥有它独立的模块。那具体该怎么使用呢？</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>:&#123;
        <span class="hljs-attr">test</span>:<span class="hljs-regexp">/\.scss$/</span>,
        use:[
            <span class="hljs-string">'style-loader'</span>, 
            &#123;
                <span class="hljs-attr">loader</span>: <span class="hljs-string">'css-loader'</span>,
                <span class="hljs-attr">options</span>: &#123;
                    <span class="hljs-comment">//表明前面要先走sass-loader和postcss-loader</span>
                    <span class="hljs-attr">importLoaders</span>: <span class="hljs-number">2</span>,
                    <span class="hljs-attr">modules</span>: <span class="hljs-literal">true</span>
                &#125;
            &#125;,
            <span class="hljs-string">'sass-loader'</span>,
            <span class="hljs-string">'postcss-loader'</span>
        ]
    &#125;]
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>从以上代码中我们可以知道，通过 <code>modules:true</code> 语句，就可以开启 <code>css</code> 的模块化打包。开启之后，我们就可以在各种文件下引入。<strong>引入方式如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">import</span> style <span class="hljs-keyword">from</span> <span class="hljs-string">'./index.scss'</span>;

<span class="hljs-keyword">var</span> img = <span class="hljs-keyword">new</span> Image(); 
img.src = bug;
img.classList.add(style.bug);
<span class="copy-code-btn">复制代码</span></code></pre>
<p>从上述代码中我们可以看到，开启 <code>module</code> 后，就可以随心所欲的引用该 <code>css</code> 中的内容啦！</p>
<h2 data-id="heading-27">6、如何使用webpack打包字体文件</h2>
<p>有时候我们在项目中有可能会遇到想要引入字体的问题，那 <code>webpack</code> 如何打包字体呢？<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>:&#123;
<span class="hljs-attr">rules</span>:[&#123;
<span class="hljs-attr">test</span>: <span class="hljs-regexp">/\.(eot|ttf|svg)$/</span>,
use: &#123;
<span class="hljs-attr">loader</span>: <span class="hljs-string">'file-loader'</span>,
&#125;

&#125;]
&#125;,
<span class="copy-code-btn">复制代码</span></code></pre>
<p>通过以上代码我们可以知道，跟 <code>webpack</code> 相关的静态文件格式为 <code>eot、ttf和svg</code> 等格式，所以需要需要把这几种类型引入。同时，跟其相关的 <code>loader</code> 为 <code>file-loader</code> 。</p>
<p>学完关于如何打包静态资源后，建议可以再用官方文档的相关部分来进行复习，<a href="https://link.juejin.cn/?target=https%3A%2F%2Fwebpack.js.org%2Fguides%2Fasset-management%2F" target="_blank" rel="nofollow noopener noreferrer" title="https://webpack.js.org/guides/asset-management/" ref="nofollow noopener noreferrer">具体链接戳</a>~</p>
<h1 data-id="heading-28">🧲五、使用plugins让打包更便携</h1>
<h2 data-id="heading-29">1、html-webpack-plugin</h2>
<p>在学习了如何使用 <code>loader</code> 来打包静态文件之后，接下来我们一起来了解在 <code>webpack</code> 中，如何使用 <code>plugins </code> 让打包更便捷。</p>
<p>我们在打包项目时， <code>webpack</code> 总是会把打包后的内容放到 <code>dist</code> 目录下。这个时候我们可能还需要自行再去创建一个 <code>index.html</code> 来引入核心文件。那这样会不会就显得略有点麻烦了？</p>
<p>因此， <code>webpack</code> 给我们提供了 <code>plugin</code> 插件来解决这个问题。</p>
<p>首先，我们先来安装 <code>plugin</code> ，<strong>具体命令行如下：</strong></p>
<pre><code class="hljs language-bash copyable" lang="bash">npm install html-webpack-plugin -D
<span class="copy-code-btn">复制代码</span></code></pre>
<p>接下来我们将插件引入 <code>webpack.config.js</code> 当中，<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">const</span> HtmlWebpackPlugin = <span class="hljs-built_in">require</span>(<span class="hljs-string">'html-webpack-plugin'</span>);

plugins: [<span class="hljs-keyword">new</span> HtmlWebpackPlugin(&#123;
<span class="hljs-comment">//表明要引用哪一个模板</span>
<span class="hljs-attr">template</span>: <span class="hljs-string">'src/index.html'</span>
&#125;)]
<span class="copy-code-btn">复制代码</span></code></pre>
<p>现在，我们来梳理一下 <code>htmlWebpackPlugin</code> 如何帮我们完成自动打包。</p>
<p>首先， <code>htmlWebpackPlugin</code> 会在打包结束后，自动生成一个 <code>html</code> 文件。之后呢，把打包生成的 <code>js</code> 文件自动引入到这个 <code>html</code> 文件中。</p>
<p>所以，从某种程度上来说就是， <code>plugin</code> 可以在 <code>webpack</code> 运行到某个时刻的时候，自动地帮你做一些事情。即当我们打包结束的这儿一时刻， <code>plugin</code> 会自动帮我们创建 <code>html</code> 文件以供我们直接使用。</p>
<h2 data-id="heading-30">2、clean-webpack-plugin</h2>
<p>有时候我们有可能对 <code>webpack.config.js</code> 中的output所对应的filename进行修改，这就很容易导致在打包过程中遇到多文件冲突。</p>
<p>那么我们想要实现的就是，在打包时，先清空原来的dist文件夹，然后再生成一个新的dist文件夹。如何处理呢？请看下方。</p>
<p>首先我们先安装依赖 <code>clean-webpack-plugin</code> ，<strong>具体命令行如下：</strong></p>
<pre><code class="hljs language-bash copyable" lang="bash">npm install clean-webpack-plugin -D
<span class="copy-code-btn">复制代码</span></code></pre>
<p>接下来我们将插件引入 <code>webpack.config.js</code> 当中，<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">const</span> CleanWebpackPlugin = <span class="hljs-built_in">require</span>(<span class="hljs-string">'clean-webpack-plugin'</span>);

plugins: [<span class="hljs-keyword">new</span> HtmlWebpackPlugin(&#123;
<span class="hljs-comment">//表明要引用哪一个模板</span>
<span class="hljs-attr">template</span>: <span class="hljs-string">'src/index.html'</span>
&#125;),<span class="hljs-keyword">new</span> CleanWebpackPlugin([<span class="hljs-string">'dist'</span>])]
<span class="copy-code-btn">复制代码</span></code></pre>
<p>通过以上代码，就可以在我们项目打包时，先删除 <code>dist</code> 文件夹，之后再创建一个新的文件夹。</p>
<h1 data-id="heading-31">🗞️六、Entry和Output</h1>
<p>接下来我们再来看 <code>webpack</code> 中的 <code>entry</code> 和 <code>output</code> 中几个比较核心的配置。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>.exports = &#123;
<span class="hljs-attr">mode</span>:<span class="hljs-string">'development'</span>,
<span class="hljs-comment">// 放置入口文件，明确怎么打包</span>
<span class="hljs-attr">entry</span>:&#123;
<span class="hljs-attr">main</span>: <span class="hljs-string">'./src/index.js'</span>,
<span class="hljs-attr">sub</span>: <span class="hljs-string">'./src/index.js'</span>
&#125;,
<span class="hljs-attr">plugins</span>: [<span class="hljs-keyword">new</span> HtmlWebpackPlugin(&#123;
<span class="hljs-comment">//表明要引用哪一个模板</span>
<span class="hljs-attr">template</span>: <span class="hljs-string">'src/index.html'</span>
&#125;),<span class="hljs-keyword">new</span> CleanWebpackPlugin([<span class="hljs-string">'dist'</span>])],
<span class="hljs-comment">// 输出，表明webpack应该怎么输出</span>
<span class="hljs-attr">output</span>: &#123;
<span class="hljs-comment">//如果把资源放在cdn下，则引入cdn</span>
<span class="hljs-attr">publicPath</span>: <span class="hljs-string">'http://cdn.com.cn'</span>,
<span class="hljs-comment">//当entry有多个入口文件时，用[]可以输出多个文件</span>
<span class="hljs-attr">filename</span>: <span class="hljs-string">'[name].js'</span>,
<span class="hljs-comment">// 指打包后的文件要放在哪个文件下</span>
<span class="hljs-attr">path</span>: path.resolve(__dirname, <span class="hljs-string">'dist'</span>)
&#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h1 data-id="heading-32">🗺️七、SourceMap</h1>
<h2 data-id="heading-33">1、引例阐述</h2>
<p>有时候，我们在写代码时，总会莫名的出bug。看着控制台那红红的报错，心里总归很不是滋味。同时，如果我们没有配置好 <code>webpack</code> 的话，那错误找起来简直是很恐怖的。</p>
<p>比如，在开发模式下，我们默认 <code>webpack.config.js</code> 像下面这样配置，<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>.exports = &#123;
<span class="hljs-attr">mode</span>:<span class="hljs-string">'development'</span>,
<span class="hljs-attr">devtool</span>: <span class="hljs-string">'none'</span>,
    <span class="hljs-attr">entry</span>:&#123;
        <span class="hljs-comment">//打包到dist目录下的main.js</span>
<span class="hljs-attr">main</span>: <span class="hljs-string">'./src/index.js'</span>
&#125;,
    <span class="hljs-attr">output</span>: &#123;
<span class="hljs-comment">//用[]可以生成多个文件</span>
<span class="hljs-attr">filename</span>: <span class="hljs-string">'[name].js'</span>,
<span class="hljs-comment">// 指打包后的文件要放在哪个文件下</span>
<span class="hljs-attr">path</span>: path.resolve(__dirname, <span class="hljs-string">'dist'</span>)
&#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>然后呢，假设我们现在代码里面错把 <code>console.log</code> 写成  <code>consele.log</code> 。那么现在<strong>控制台的打印效果如下：</strong></p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d70d9b5e09d84341b966bcfa310fe29b~tplv-k3u1fbpfcp-zoom-1.image" alt="sourceMap" loading="lazy" referrerpolicy="no-referrer"></p>
<p>大家可以看到，此时的错误定位到打包后的 <code>main.js</code> 文件里面的第<strong>96</strong>行。那试想一下，如果我们的业务代码特别多，报错有可能就是在文件中的上前行了。</p>
<p>这样的场景并不是我们想看到的。我们想做的事情呢就是，希望 <code>webpack</code> 打包完成之后就把错误直接抛给我们，并把其对应的具体文件地址显示出来。也就是我们出错的那个代码文件，而不是打包后的文件 <code>main.js</code> 。</p>
<p>因此， <code>webpack</code> 给我们提供了 <code>sourceMap</code> 这个配置，来解决这个问题。</p>
<h2 data-id="heading-34">2、sourceMap</h2>
<p>我们现在把 <code>devtool</code> 这个配置，改成 <code>sourceMap</code> 。<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>.exports = &#123;
<span class="hljs-attr">mode</span>:<span class="hljs-string">'development'</span>,
<span class="hljs-attr">devtool</span>: <span class="hljs-string">'source-map'</span>,
    <span class="hljs-attr">entry</span>:&#123;
        <span class="hljs-comment">//打包到dist目录下的main.js</span>
<span class="hljs-attr">main</span>: <span class="hljs-string">'./src/index.js'</span>
&#125;,
    <span class="hljs-attr">output</span>: &#123;
<span class="hljs-comment">//用[]可以生成多个文件</span>
<span class="hljs-attr">filename</span>: <span class="hljs-string">'[name].js'</span>,
<span class="hljs-comment">// 指打包后的文件要放在哪个文件下</span>
<span class="hljs-attr">path</span>: path.resolve(__dirname, <span class="hljs-string">'dist'</span>)
&#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>改完之后呢，我们来看一下<strong>控制台的打印结果：</strong></p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/dd5fd576df1c4c0b9ffef8feef1ac76b~tplv-k3u1fbpfcp-zoom-1.image" alt="sourceMap" loading="lazy" referrerpolicy="no-referrer"></p>
<p>现在大家可以看到，改成 <code>source-map</code> 的配置之后，报错的定位直接到了我们自己所编写代码的目录下，即 <code>index.js</code> 。而不再是大海捞针似的在 <code>main.js</code> 里面找。</p>
<h2 data-id="heading-35">3、sourceMap常见配置</h2>
<p>看完上面的例子之后，相信大家对 <code>SourceMap</code> 有了一定的了解。接下来我们来看一下 <code>sourceMap</code> 的一些常见配置。<strong>具体看看下方：</strong></p>

































<table><thead><tr><th align="center">SourceMap</th><th align="center">含义</th></tr></thead><tbody><tr><td align="center">inline-source-map</td><td align="center">报错时将行和列都显示出来</td></tr><tr><td align="center">cheap-inline-source-map</td><td align="center">报错时只知道哪一行出错了，不知道在哪一列</td></tr><tr><td align="center">cheap-module-source-map</td><td align="center"><strong>生产环境最佳实践</strong>，不仅管自己的业务代码错误，还要管其他的其他的错误，像loader、其他第三方模块的错误等等</td></tr><tr><td align="center">eval</td><td align="center">eval是打包速度最快的一种方式，但如果遇到业务代码比较复杂的情况下，用eval提示出来的效果可能不太全面</td></tr><tr><td align="center">module-eval-source-map</td><td align="center">用module，表明不仅要显示业务错误，还要显示loader、第三方错误等等</td></tr><tr><td align="center">cheap-module-eval-source-map</td><td align="center">开发环境最佳实践</td></tr></tbody></table>
<h1 data-id="heading-36">🧱八、使用WebpackDevServer提升开发效率</h1>
<h2 data-id="heading-37">1、--watch</h2>
<p>事实上，如果我们不采用 <code>WebpackDevServer</code> 的方式来开发的话，那么我们每一次想要查看编译后的运行结果，都需要先命令行编译 <code>npm run bundle</code> 命令，之后再打开 <code>dist</code> 目录下的 <code>index.html</code> 文件才能重新查看。这样一来二往的，难免效率低下。我们期待的结果是什么呢？</p>
<p>我们把 <code>package.json</code> 文件里的 <code>script</code> 进行一番改造，<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-json copyable" lang="json"><span class="hljs-string">"scripts"</span>: &#123;
    <span class="hljs-attr">"watch"</span>: <span class="hljs-string">"webpack --watch"</span>,
    <span class="hljs-attr">"bundle"</span>: <span class="hljs-string">"webpack"</span>
  &#125;,
<span class="copy-code-btn">复制代码</span></code></pre>
<p>通过以上代码大家可以看到，将 <code>webpack</code> 后面加上 <code>--watch</code> 字段，然后运行 <code>npm run watch</code> ，就可以每次修改完代码后， <code>webpack</code> 实现自动监听，而不用像以往那样，每修改一次代码都要对再重新运行命令来对 <code>webpack</code> 进行打包。</p>
<h2 data-id="heading-38">2、webpackDevServer</h2>
<p>但是呢，这种方式可能还不够友好，毕竟开发者总是懒惰的，能尽量让程序来干活就不要用手工来干活。</p>
<p>实际上我们想要达到的效果是，当我们运行完 <code>npm run watch</code> 这行命令的时候，不仅能自动帮我们实现打包，同时还能帮我们打开控制台，并且模拟一些服务器上的特性。那么我们就可以通过 <code>webpackDevServer</code> 来实现我们想要的效果。如何使用 <code>webpckDevServer</code> 呢？具体看下方。</p>
<h3 data-id="heading-39">（1）安装webpackDevServer</h3>
<p>我们现在项目中安装webpackDevServer，<strong>具体命令行如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js">npm install webpack-dev-server -D
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-40">（2）配置package.json文件</h3>
<p>接下来我们来配置 <code>package.json</code> 文件的 <code>script</code> 。<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-json copyable" lang="json"><span class="hljs-string">"scripts"</span>: &#123;
    <span class="hljs-attr">"watch"</span>: <span class="hljs-string">"webpack --watch"</span>,
    <span class="hljs-attr">"start"</span>: <span class="hljs-string">"webpack-dev-server"</span>
  &#125;,
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-41">（3）配置 webpack文件</h3>
<p>接下面我们来配置 <code>webpack.config.js</code> 文件，<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>.exports = &#123;
<span class="hljs-attr">mode</span>:<span class="hljs-string">'development'</span>,
<span class="hljs-attr">devtool</span>: <span class="hljs-string">'source-map'</span>,
<span class="hljs-comment">// 放置入口文件，明确怎么打包</span>
<span class="hljs-attr">entry</span>:&#123;
<span class="hljs-attr">main</span>: <span class="hljs-string">'./src/index.js'</span>
&#125;,
<span class="hljs-attr">devServer</span>: &#123;
<span class="hljs-attr">contentBase</span>: <span class="hljs-string">'./dist'</span>,
<span class="hljs-comment">// 当运行完npm run start时，会自动的帮我们打开浏览器</span>
<span class="hljs-attr">open</span>: <span class="hljs-literal">true</span>
&#125;,
    <span class="hljs-attr">output</span>: &#123;
<span class="hljs-comment">//用[]可以生成多个文件</span>
<span class="hljs-attr">filename</span>: <span class="hljs-string">'[name].js'</span>,
<span class="hljs-comment">// 指打包后的文件要放在哪个文件下</span>
<span class="hljs-attr">path</span>: path.resolve(__dirname, <span class="hljs-string">'dist'</span>)
&#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>那么现在，我们来看下， <code>webpackDevServer</code> 如何做到自动打开浏览器。<strong>详情见下图：</strong></p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/08b8311a5e0e48e88fbd4d47f1a7ddc2~tplv-k3u1fbpfcp-zoom-1.image" alt="webpackDevServer" loading="lazy" referrerpolicy="no-referrer"></p>
<p>大家可以看到，通过 <code>webpackDevServer</code> ，它不但会监听到我们的文件发生了改变，重新帮我们进行打包。同时它还会<strong>自动的帮我们重新刷新浏览器</strong>，并且会<strong>自动地帮我们打开浏览器</strong>。所以用它呢，可以<strong>大大提升我们的代码开发效率</strong>。</p>
<h3 data-id="heading-42">（4）配置端口号</h3>
<p><code>webpackDevServer</code> 默认我们服务器的端口号是 <code>8080</code> ，如果我们想要修改它为其他的端口号，该怎么做呢？</p>
<p>我们需要在来修改 <code>webpack.config.js</code> 文件下的 <code>DevServer</code> ，<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>.exports = &#123;
<span class="hljs-attr">mode</span>:<span class="hljs-string">'development'</span>,
<span class="hljs-attr">devtool</span>: <span class="hljs-string">'source-map'</span>,
<span class="hljs-comment">// 放置入口文件，明确怎么打包</span>
<span class="hljs-attr">entry</span>:&#123;
<span class="hljs-attr">main</span>: <span class="hljs-string">'./src/index.js'</span>
&#125;,
<span class="hljs-attr">devServer</span>: &#123;
<span class="hljs-attr">contentBase</span>: <span class="hljs-string">'./dist'</span>,
<span class="hljs-comment">// 当运行完npm run start时，会自动的帮我们打开浏览器</span>
<span class="hljs-attr">open</span>: <span class="hljs-literal">true</span>,
        <span class="hljs-comment">//修改端口号</span>
        <span class="hljs-attr">port</span>: <span class="hljs-number">3000</span>
&#125;,
    <span class="hljs-attr">output</span>: &#123;
<span class="hljs-comment">//用[]可以生成多个文件</span>
<span class="hljs-attr">filename</span>: <span class="hljs-string">'[name].js'</span>,
<span class="hljs-comment">// 指打包后的文件要放在哪个文件下</span>
<span class="hljs-attr">path</span>: path.resolve(__dirname, <span class="hljs-string">'dist'</span>)
&#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>我们只需要在 <code>devServer</code> 里面加上一个 <code>port</code> 的配置，即可实现<strong>自定义端口号</strong>。</p>
<p>同时值得注意的是，当我们在用 <code>webpackDevServer</code> 帮我们项目做打包时，它不会自动生成 <code>dist</code> 目录，那这是为什么呢？用 <code>webpackDevServer</code> 打包后的项目会放在我们的<strong>电脑内存</strong>中，这在某种程度下可以有效的提升项目的打包速度，让打包变得更快。</p>
<h1 data-id="heading-43">🌡️九、Hot Module Replacement 热模块更新</h1>
<h2 data-id="heading-44">1、引例阐述</h2>
<p>假设我们现在要实现一个<strong>新增元素</strong>的功能，这个功能所要达到的效果是每点击一次按钮，就新添加一次文本 <code>item</code> 。<strong>具体实现代码如下：</strong></p>
<p><strong>index.js文件：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">import</span> <span class="hljs-string">'./style.css'</span>;

<span class="hljs-keyword">var</span> btn = <span class="hljs-built_in">document</span>.createElement(<span class="hljs-string">'button'</span>);
btn.innerHTML = <span class="hljs-string">'新增'</span>;
<span class="hljs-built_in">document</span>.body.appendChild(btn);

btn.onclick = <span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params"></span>)</span>&#123;
    <span class="hljs-keyword">var</span> div = <span class="hljs-built_in">document</span>.createElement(<span class="hljs-string">'div'</span>);
    div.innerHTML = <span class="hljs-string">'item'</span>;
    <span class="hljs-built_in">document</span>.body.appendChild(div);
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><strong>style.css文件：</strong></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-tag">div</span><span class="hljs-selector-pseudo">:nth-of-type</span>(odd)&#123;
    <span class="hljs-attribute">background</span>: yellow;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>此时浏览器的显示效果<strong>如下图所示：</strong></p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a1b5f239c144484c98d1a736ca35060b~tplv-k3u1fbpfcp-zoom-1.image" alt="HMR①" loading="lazy" referrerpolicy="no-referrer"></p>
<hr>
<p>假设我们现在来给css的背景改个颜色，比如说改成紫色。<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-css copyable" lang="css"><span class="hljs-selector-tag">div</span><span class="hljs-selector-pseudo">:nth-of-type</span>(odd)&#123;
    <span class="hljs-attribute">background</span>: purple;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>此时我们保存后浏览器会重新进行刷新，之后每一个 <code>item</code> 又要重新 <code>append</code> 进来。<strong>如下图：</strong></p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/fffe7f0c427c4ec7887a993c2fa9e594~tplv-k3u1fbpfcp-zoom-1.image" alt="HMR②" loading="lazy" referrerpolicy="no-referrer"></p>
<p>那这种情况下可能就不是我们想要的结果了。我们希望的是，所有的 <code>item</code> 不进行重新刷新，并且当 <code>css</code> 样式改变的时候，对应的 <code>item</code> 颜色也可以得到改变。那么这就要引出 <code>webpackDevServer</code> 中的一个内容：热模块更新 <code>Hot Module Replacement</code> 。接下来我们来了解热模块更新相关的配置。</p>
<h2 data-id="heading-45">2、热模块更新配置</h2>
<p>热模块更新，即Hot Module Replacement，简称为 <code>HMR</code> 。</p>
<p>接下来我们在 <code>webpack.config.js</code> 文件夹下进行配置。<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">//node的核心模块</span>
<span class="hljs-keyword">const</span> path = <span class="hljs-built_in">require</span>(<span class="hljs-string">'path'</span>);
<span class="hljs-keyword">const</span> HtmlWebpackPlugin = <span class="hljs-built_in">require</span>(<span class="hljs-string">'html-webpack-plugin'</span>);
<span class="hljs-keyword">const</span> CleanWebpackPlugin = <span class="hljs-built_in">require</span>(<span class="hljs-string">'clean-webpack-plugin'</span>);
<span class="hljs-keyword">const</span> webpack = <span class="hljs-built_in">require</span>(<span class="hljs-string">'webpack'</span>);

<span class="hljs-built_in">module</span>.exports = &#123;
<span class="hljs-attr">mode</span>:<span class="hljs-string">'development'</span>,
<span class="hljs-attr">devtool</span>: <span class="hljs-string">'source-map'</span>,
<span class="hljs-comment">// 放置入口文件，明确怎么打包</span>
<span class="hljs-attr">entry</span>:&#123;
<span class="hljs-attr">main</span>: <span class="hljs-string">'./src/index.js'</span>
&#125;,
<span class="hljs-attr">devServer</span>: &#123;
<span class="hljs-attr">contentBase</span>: <span class="hljs-string">'./dist'</span>,
<span class="hljs-comment">// 当运行完npm run start时，会自动的帮我们打开浏览器</span>
<span class="hljs-attr">open</span>: <span class="hljs-literal">true</span>,
<span class="hljs-attr">port</span>: <span class="hljs-number">8080</span>,
<span class="hljs-comment">// 让我们的webpackDevServer开启hotModuleReplacement这样子的功能</span>
<span class="hljs-attr">hot</span>: <span class="hljs-literal">true</span>,
<span class="hljs-comment">// 即便HMR没有生效，也不让浏览器自动刷新</span>
<span class="hljs-attr">hotOnly</span>: <span class="hljs-literal">true</span>
&#125;,
<span class="hljs-attr">module</span>:&#123;
<span class="hljs-attr">rules</span>:[&#123;
<span class="hljs-attr">test</span>:<span class="hljs-regexp">/\.(jpg|png|gif)$/</span>,
use:&#123;
<span class="hljs-attr">loader</span>:<span class="hljs-string">'file-loader'</span>,
<span class="hljs-attr">options</span>: &#123;
<span class="hljs-comment">//placeholder 占位符</span>
<span class="hljs-attr">name</span>: <span class="hljs-string">'[name]_[hash].[ext]'</span>,
<span class="hljs-attr">outputPath</span>: <span class="hljs-string">'images/'</span>,
<span class="hljs-attr">limit</span>: <span class="hljs-number">10240</span>
&#125;
&#125;
&#125;,&#123;
<span class="hljs-attr">test</span>:<span class="hljs-regexp">/\.scss$/</span>,
use:[
<span class="hljs-string">'style-loader'</span>, 
&#123;
<span class="hljs-attr">loader</span>: <span class="hljs-string">'css-loader'</span>,
<span class="hljs-attr">options</span>: &#123;
<span class="hljs-comment">//表明前面要先走sass-loader和postcss-loader</span>
<span class="hljs-attr">importLoaders</span>: <span class="hljs-number">2</span>,
<span class="hljs-attr">modules</span>: <span class="hljs-literal">true</span>
&#125;
&#125;, 
<span class="hljs-string">'sass-loader'</span>,
<span class="hljs-string">'postcss-loader'</span>
]
&#125;,&#123;
<span class="hljs-attr">test</span>:<span class="hljs-regexp">/\.css$/</span>,
use:[
<span class="hljs-string">'style-loader'</span>,
<span class="hljs-string">'css-loader'</span>,
<span class="hljs-string">'postcss-loader'</span>
]
&#125;]
&#125;,
<span class="hljs-attr">plugins</span>: [<span class="hljs-keyword">new</span> HtmlWebpackPlugin(&#123;
<span class="hljs-comment">//表明要引用哪一个模板</span>
<span class="hljs-attr">template</span>: <span class="hljs-string">'src/index.html'</span>
&#125;),<span class="hljs-keyword">new</span> CleanWebpackPlugin([<span class="hljs-string">'dist'</span>]),
<span class="hljs-keyword">new</span> webpack.HotModuleReplacementPlugin()
],
<span class="hljs-comment">// 输出，表明webpack应该怎么输出</span>
<span class="hljs-attr">output</span>: &#123;
<span class="hljs-comment">// 下载middle：npm install express webpack-dev-middleware -D</span>
<span class="hljs-attr">publicPath</span>: <span class="hljs-string">'/'</span>,
<span class="hljs-comment">//用[]可以生成多个文件</span>
<span class="hljs-attr">filename</span>: <span class="hljs-string">'[name].js'</span>,
<span class="hljs-comment">// 指打包后的文件要放在哪个文件下</span>
<span class="hljs-attr">path</span>: path.resolve(__dirname, <span class="hljs-string">'dist'</span>)
&#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>通过以上代码我们可以知道，配置 <code>devServer</code> 下的 <code>hot</code> 和 <code>hotOnly</code> ，以及 <code>plugins</code> 下的 <code>new webpack.HotModuleReplacementPlugin()</code> ，来达到热模块更新的效果。</p>
<p>接下来我们来看一下，进行配置之后，浏览器的效果。<strong>详情见下图：</strong></p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1deb9fa7548c4aebb3a425d3250ef6a3~tplv-k3u1fbpfcp-zoom-1.image" alt="HMR③" loading="lazy" referrerpolicy="no-referrer"></p>
<p>大家可以看到，加上这几个配置之后， <code>item</code> 不会再重新刷新了，而是在原来的基础上进行样式修改。</p>
<h1 data-id="heading-46">📀十、使用Babel处理ES6语法</h1>
<h2 data-id="heading-47">1、ES6语法转换为ES5语法</h2>
<p>继续，接下来我们来了解，如何使用webpack和babel，来编写ES6的语法。</p>
<p>大家都知道，ES6的语法规范是2015年才正式出版的。所以有时候，并不是所有的浏览器都支持ES6语法。因此，我们现在想要做的事情就是，在webpack打包时，能够将ES6的语法转换为ES5的语法。这样，项目运行的时候，浏览器就不会报错了。</p>
<p>那怎么实现这样子的打包呢？接下来我们一起来了解一下。</p>
<p>首先我们打开<a href="https://link.juejin.cn/?target=https%3A%2F%2Fbabeljs.io%2Fsetup%23installation" target="_blank" rel="nofollow noopener noreferrer" title="https://babeljs.io/setup#installation" ref="nofollow noopener noreferrer">babel的官方网站</a>，按照步骤，我们一步步在 <code>webpack</code> 中使用 <code>babel</code> 。</p>
<p><strong>第一步：</strong> 安装 <code>babel-loader</code> 和 <code>@babel/core</code> 这两个库。<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-bash copyable" lang="bash">npm install --save-dev babel-loader @babel/core
<span class="copy-code-btn">复制代码</span></code></pre>
<p><code>babel-loader</code> 是帮助webpack进行打包使用的一个工具，而 <code>@babel/core</code> 则是 <code>babel</code> 的一个核心库，它能够让 <code>babel</code> 去识别 <code>js</code> 代码里的内容，然后呢把 <code>js</code> 代码转换成 <code>AST</code> 抽象语法树，之后再把抽象语法树编译成一些新的语法。</p>
<p><strong>第二步：</strong> 在 <code>webpack.config.js</code> 文件下的配置项里增设规则。<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>: &#123;
    <span class="hljs-attr">rules</span>: [
        &#123;
            <span class="hljs-attr">test</span>: <span class="hljs-regexp">/\.m?js$/</span>,
            exclude: <span class="hljs-regexp">/node_modules/</span>,
            use: &#123;
                <span class="hljs-attr">loader</span>: <span class="hljs-string">"babel-loader"</span>,
                <span class="hljs-attr">options</span>: &#123;
                    <span class="hljs-attr">presets</span>: [<span class="hljs-string">'@babel/preset-env'</span>]
                &#125;
            &#125;
        &#125;
    ]
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><strong>第三步：</strong> 安装 <code>@babel/preset-env</code> 。<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-bash copyable" lang="bash">npm install @babel/preset-env --save-dev
<span class="copy-code-btn">复制代码</span></code></pre>
<p>为什么要安装这个模块呢？实际上，当我们使用 <code>babel-loader</code> 处理文件时，实际上 <code>babel-loader</code> 只是 <code>webpack</code> 和 <code>babel</code> 之间做通信的一个桥梁，它只是帮我们打开了一个通道，但是它并不会帮我们把 <code>ES6</code> 的语法转换为 <code>ES5</code> 的语法。所以，我们就还需要借助一些其他的模块，来做这项工作。这个模块就是前面我们说的，<strong>preset-env</strong> 。</p>
<p><code>babel/preset-env</code> ，包含了所有 <code>ES6</code> 转换为 <code>ES5</code> 的语法规则，当使用此模块打包时，就可以把我们所有 <code>js</code> 中 <code>ES6</code> 的代码转换为 <code>ES5</code> 了。具体配置方式见以上<strong>第二步</strong>。</p>
<h2 data-id="heading-48">2、Babel-polyfill</h2>
<p>通过以上的方式，我们可以达到将ES6语法转换为ES5语法的效果。但是呢，我们还要考虑到的一个问题就是，如果遇到像promise这一类新的语法变量，或者时像数组里面map这一类的函数，低版本的浏览器里面，实际上还是不存在的。虽然我们做了语法解释和语法翻译，但也只是翻译了一部分。还有一些对象和函数，在低版本的浏览器还是没有的。</p>
<p>所以呢，这个时候我们不仅要使用 <code>babel/preset-env</code> 做语法转换，还要<strong>把这些缺失的变量和函数补充到低版本的浏览器里面</strong>。</p>
<p>那怎么补充呢，这个时候我们就需要借助 <code>babel-polyfill</code> 这个工具来进行补充。接下来讲解这个模块的使用操作。</p>
<p>第一步： 定位到<a href="https://link.juejin.cn/?target=https%3A%2F%2Fbabeljs.io%2Fdocs%2Fen%2Fbabel-polyfill" target="_blank" rel="nofollow noopener noreferrer" title="https://babeljs.io/docs/en/babel-polyfill" ref="nofollow noopener noreferrer">官方文档</a>，安装 <code>babel-polyfill</code> 。<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-bash copyable" lang="bash">npm install --save @babel/polyfill
<span class="copy-code-btn">复制代码</span></code></pre>
<p>第二步： 引入该模块。<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">import</span> <span class="hljs-string">"@babel/polyfill"</span>;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>通常情况下，这段代码放到项目的 <code>js</code> 入口文件下。</p>
<p>第三步： 改造 <code>webpack.cofig.js</code> 文件下的 <code>module</code> ，减少打包大小。<strong>具体代码如下：</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">module</span>: &#123;
    <span class="hljs-attr">rules</span>: [
        &#123;
            <span class="hljs-attr">test</span>: <span class="hljs-regexp">/\.m?js$/</span>,
            exclude: <span class="hljs-regexp">/node_modules/</span>,
            use: &#123;
                <span class="hljs-attr">loader</span>: <span class="hljs-string">"babel-loader"</span>,
                <span class="hljs-attr">options</span>: &#123;
<span class="hljs-attr">presets</span>: [[<span class="hljs-string">'@babel/preset-env'</span>],&#123;
<span class="hljs-attr">useBuiltIns</span>: <span class="hljs-string">'usage'</span>
&#125;]
  &#125;
            &#125;
        &#125;
    ]
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>这段代码的意思就是，当用 <code>babel-polyfill</code> 填充低版本浏览器特性的时候，不是把是多有的特性都加进来，而是根据我们的业务代码来决定到底到加什么。</p>
<p>同时， <code>babel-preset</code> 也有很多其他值得学习的配置属性，这里不再进行讲解。大家可以自行到<a href="https://link.juejin.cn/?target=https%3A%2F%2Fbabeljs.io%2Fdocs%2Fen%2Fusage" target="_blank" rel="nofollow noopener noreferrer" title="https://babeljs.io/docs/en/usage" ref="nofollow noopener noreferrer">官方文档</a>上进行查看~</p>
<h1 data-id="heading-49">📚十一、结束语</h1>
<p>写完这篇文章的时候，突然想起上次面试时的面试官。在最后的反问环节问他关于 <code>webpack</code> 的问题，他说 <code>webpack</code> 一般会让对公司业务很熟悉的员工来处理，毕竟前端工程化不是儿戏。</p>
<p>当时我还没有很大的感触，但现在学到这里突然就想到了那个场景。确实是这样，我这才学了不到它的冰山一角，就已经感到 <code>webpack</code> 的庞大工程了。如果在打包时候，但凡有一个小地方的配置出现问题，就有可能引发整个项目的不可收拾局面。（当然一般情况下不会出现这样的情况，言重了……）</p>
<p>在学习 <code>webpack</code> 的过程中，要<strong>明确好自己所使用的webpack版本</strong>。比如周一刚开始迷迷糊糊的，感觉版本4和版本5都差不多。但对于 <code>webpack</code> 来说，这完全就是在跟它开玩笑。每一个依赖都有4和5对应的版本，而不是说想用哪个就哪个。如果胡乱使用的话，无形之中可能会报错到怀疑人生……</p>
<p>因此，确定好此时用 <code>webpack</code> 打包时所使用的版本，并在使用 <code>npm</code> 依赖时也同样要找到对应的版本来进行使用，降低错误的发生。</p>
<p>到这里，关于webpack的超入门知识就讲到这里啦！希望对大家有帮助~</p>
<h1 data-id="heading-50">🐣彩蛋 One More Thing</h1>
<h2 data-id="heading-51">往期推荐</h2>
<ul>
<li><a href="https://juejin.cn/column/6976040277068759077" target="_blank" title="https://juejin.cn/column/6976040277068759077">vuejs基础知识系列</a></li>
<li><a href="https://juejin.cn/column/6976041758945706015" target="_blank" title="https://juejin.cn/column/6976041758945706015">vuejs原理分析系列</a></li>
</ul>
<h2 data-id="heading-52">番外篇</h2>
<blockquote>
<ul>
<li>关注公众号<strong>星期一研究室</strong>，第一时间关注学习干货，<strong>更多精选专栏待你解锁</strong>~</li>
<li>如果这篇文章对你有用，记得<strong>留个脚印jio</strong>再走哦~</li>
<li>以上就是本文的全部内容！我们下期见！👋👋👋</li>
</ul>
</blockquote></div>  
</div>
            
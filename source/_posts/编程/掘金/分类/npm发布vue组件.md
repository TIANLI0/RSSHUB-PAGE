
---
title: 'npm发布vue组件'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/29df7994578d4c6894efc51214ff79d8~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 21:42:41 GMT
thumbnail: 'https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/29df7994578d4c6894efc51214ff79d8~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><p>参考:</p>
<ul>
<li><a href="https://link.juejin.cn/?target=https%3A%2F%2Fwww.cnblogs.com%2Fyalong%2Fp%2F10388384.html" target="_blank" rel="nofollow noopener noreferrer" title="https://www.cnblogs.com/yalong/p/10388384.html" ref="nofollow noopener noreferrer">npm发布vue组件</a></li>
<li><a href="https://juejin.cn/post/6844903636808499214#heading-1" target="_blank" title="https://juejin.cn/post/6844903636808499214#heading-1">手把手教你封装 Vue 组件，并使用 npm 发布</a></li>
<li><a href="https://link.juejin.cn/?target=https%3A%2F%2Fblog.csdn.net%2Ftaoerchun%2Farticle%2Fdetails%2F82531549" target="_blank" rel="nofollow noopener noreferrer" title="https://blog.csdn.net/taoerchun/article/details/82531549" ref="nofollow noopener noreferrer">npm发布包</a></li>
</ul>
<h4 data-id="heading-0">初始化项目</h4>
<pre><code class="hljs language-js copyable" lang="js">vue init webpack-simple yyl-npm-practice

<span class="hljs-comment">//然后根据提示</span>
cd yyl-npm-practice
npm install
npm run dev
<span class="copy-code-btn">复制代码</span></code></pre>
<p>为什么不使用<code>vue init webpack npm-practice</code>初始化项目，因为开发组件不需要太多的配置，配置过多会引起配置麻烦，使用webpack-simple足够。</p>
<h4 data-id="heading-1">文件目录配置</h4>
<p>参考了一下 <a href="https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2FElemeFE%2Felement" target="_blank" rel="nofollow noopener noreferrer" title="https://github.com/ElemeFE/element" ref="nofollow noopener noreferrer">element</a> ,适合多插件使用，怎么建立文件夹放自己的组件完全取决于你自己，最后只要在webpack的入口和出口配置对应的即可。</p>
<pre><code class="copyable">├── src/                           // 源码目录
│   ├── packages/                  // 组件目录
│   │   ├── myButton/              // 组件1
    │   │   ├── myButton.vue       // 组件代码
    │   │   ├── index.js           // 挂载插件
        ├── myText/                // 组件2
    │   │   ├── myText.vue         // 组件代码
    │   │   ├── index.js           // 挂载插件
│   ├── App.vue                    // 页面入口
│   ├── main.js                    // 程序入口
│   ├── index.js                   // （所有）插件入口
├── index.html                     // 入口html文件
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-2">按需引入，即单组件引入</h4>
<p>packages/myButton/myButton.vue:</p>
<pre><code class="hljs language-vue copyable" lang="vue"><template>
    <div>
        MyButton组件
    </div>
</template>


<script>
export default &#123;
    name: 'MyButton',//注意要填写，不然多组件时候进行遍历的时候就无法自动获取组件名称
&#125;
</script>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>packages/myButton/index.js:</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">import</span> MyButton <span class="hljs-keyword">from</span> <span class="hljs-string">'./myButton.vue'</span>

<span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span> &#123;
    <span class="hljs-comment">//Vue为vue的构造函数，options为可选配置项</span>
    <span class="hljs-function"><span class="hljs-title">install</span>(<span class="hljs-params">Vue,options</span>)</span>&#123;
        Vue.component(MyButton.name, MyButton);
    &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>以上为止一个组件插件就已经封装成功，最后我们测试发布到npm上即可。</p>
<p><strong>测试使用：</strong>
main.js引入：</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">import</span> Vue <span class="hljs-keyword">from</span> <span class="hljs-string">'vue'</span>
<span class="hljs-keyword">import</span> App <span class="hljs-keyword">from</span> <span class="hljs-string">'./App.vue'</span>

<span class="hljs-comment">//引入组件使用Vue.use时候会自动执行install方法，从而挂载了组件到Vue构造函数上</span>
<span class="hljs-keyword">import</span> MyButton <span class="hljs-keyword">from</span> <span class="hljs-string">'./packages/myButton/index.js'</span>
Vue.use(MyButton)

<span class="hljs-keyword">new</span> Vue(&#123;
  <span class="hljs-attr">el</span>: <span class="hljs-string">'#app'</span>,
  <span class="hljs-attr">render</span>: <span class="hljs-function"><span class="hljs-params">h</span> =></span> h(App)
&#125;)
<span class="copy-code-btn">复制代码</span></code></pre>
<p>App.vue:</p>
<pre><code class="hljs language-vue copyable" lang="vue"><template>
  <div id="app">
    <my-button />
  </div>
</template>

<script>
export default &#123;
  name: 'app'
&#125;
</script>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>显示：</p>
<p><img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/29df7994578d4c6894efc51214ff79d8~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h4 data-id="heading-3">多组件情况下，全局引入所有组件</h4>
<p>我们在src目录下，即App.vue同级下创建index.js，
src/index.js:(所有组件的入口)</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">import</span> MyButton <span class="hljs-keyword">from</span> <span class="hljs-string">'./packages/myButton/myButton.vue'</span>
<span class="hljs-keyword">import</span> MyText <span class="hljs-keyword">from</span> <span class="hljs-string">'./packages/myText/myText.vue'</span>


<span class="hljs-keyword">const</span> components = [
    MyButton,
    MyText
    <span class="hljs-comment">// ...如果还有的话继续添加</span>
]

  <span class="hljs-comment">// 这一步判断window.Vue是否存在，因为直接引用vue.min.js， 它会把Vue绑到Window上，我们直接引用打包好的js才能正常跑起来。</span>
<span class="hljs-keyword">if</span> (<span class="hljs-keyword">typeof</span> <span class="hljs-built_in">window</span> !== <span class="hljs-string">'undefined'</span> && <span class="hljs-built_in">window</span>.Vue) &#123;
    components.map(<span class="hljs-function"><span class="hljs-params">component</span> =></span> &#123;
        Vue.component(component.name, component);
    &#125;)
&#125;

<span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span> &#123;
    <span class="hljs-comment">//Vue为vue的构造函数，options为可选配置项</span>
    <span class="hljs-function"><span class="hljs-title">install</span>(<span class="hljs-params">Vue,options=&#123;&#125;</span>)</span>&#123;
        components.map(<span class="hljs-function"><span class="hljs-params">component</span> =></span> &#123;
            Vue.component(component.name, component);
        &#125;)
    &#125;
&#125;

<span class="hljs-comment">//效果等价于</span>
<span class="hljs-comment">// const install = function(Vue,options=&#123;&#125;) &#123;</span>
<span class="hljs-comment">//     components.map(component => &#123;</span>
<span class="hljs-comment">//         Vue.component(component.name, component);</span>
<span class="hljs-comment">//     &#125;)</span>
<span class="hljs-comment">// &#125;</span>
<span class="hljs-comment">// export default &#123;</span>
<span class="hljs-comment">//     install</span>
<span class="hljs-comment">// &#125;</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><strong>测试</strong>
src/main.js:</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">import</span> Vue <span class="hljs-keyword">from</span> <span class="hljs-string">'vue'</span>
<span class="hljs-keyword">import</span> App <span class="hljs-keyword">from</span> <span class="hljs-string">'./App.vue'</span>


<span class="hljs-keyword">import</span> AllComponents <span class="hljs-keyword">from</span> <span class="hljs-string">'./index'</span>
Vue.use(AllComponents)

<span class="hljs-keyword">new</span> Vue(&#123;
  <span class="hljs-attr">el</span>: <span class="hljs-string">'#app'</span>,
  <span class="hljs-attr">render</span>: <span class="hljs-function"><span class="hljs-params">h</span> =></span> h(App)
&#125;)
<span class="copy-code-btn">复制代码</span></code></pre>
<p>src/App.vue:</p>
<pre><code class="hljs language-vue copyable" lang="vue"><template>
  <div id="app">
    <my-button />
    <my-text />
  </div>
</template>

<script>
export default &#123;
  name: 'app'
&#125;
</script>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>显示：</p>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/63587b7d61454f96a5ec22da0bf3c532~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h4 data-id="heading-4">发布前操作，账号注册和配置</h4>
<ul>
<li>配置修改：</li>
</ul>
<p>webpack.config.js配置开发环境和生产环境入口：</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">// ... 此处省略代码 </span>
<span class="hljs-comment">// 执行环境</span>
<span class="hljs-keyword">const</span> NODE_ENV = process.env.NODE_ENV

<span class="hljs-built_in">module</span>.exports = &#123;
  <span class="hljs-comment">// 根据不同的执行环境配置不同的入口</span>
  <span class="hljs-attr">entry</span>: NODE_ENV == <span class="hljs-string">'development'</span> ? <span class="hljs-string">'./src/main.js'</span> : <span class="hljs-string">'./src/index.js'</span>,
  <span class="hljs-attr">output</span>: &#123;
    <span class="hljs-comment">// 修改打包出口，在最外级目录打包出一个index.js 文件，我们 import 默认会指向这个文件</span>
    <span class="hljs-attr">path</span>: path.resolve(__dirname, <span class="hljs-string">'./dist'</span>),
    <span class="hljs-attr">publicPath</span>: <span class="hljs-string">'/dist/'</span>,
    <span class="hljs-attr">filename</span>: <span class="hljs-string">'outy-test.js'</span>,
    <span class="hljs-attr">library</span>: <span class="hljs-string">'outy-test'</span>, <span class="hljs-comment">// 指定的就是你使用require时的模块名</span>
    <span class="hljs-attr">libraryTarget</span>: <span class="hljs-string">'umd'</span>, <span class="hljs-comment">// libraryTarget会生成不同umd的代码,可以只是commonjs标准的，也可以是指amd标准的，也可以只是通过script标签引入的</span>
    <span class="hljs-attr">umdNamedDefine</span>: <span class="hljs-literal">true</span> <span class="hljs-comment">// 会对 UMD 的构建过程中的 AMD 模块进行命名。否则就使用匿名的 define</span>
  &#125;,
  <span class="hljs-comment">// ... 此处省略代码 </span>
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>package.json:<br>
private字段(<strong>private</strong>是true的时候不能发布到npm,<strong>需设置成false</strong>)； 并<strong>增加main字段</strong>， main字段是require方法可以通过这个配置找到入口文件，这输入模块加载规范。并且查看<strong>name是否为重名</strong>，重名则需要换一个名称发布，因为发布时候不允许重名。如何查找名称是否被使用过,<a href="https://link.juejin.cn/?target=https%3A%2F%2Fwww.npmjs.com%2F" target="_blank" rel="nofollow noopener noreferrer" title="https://www.npmjs.com/" ref="nofollow noopener noreferrer">登录npm</a>进行search查一下，如果查到内容说明存在过。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">"name"</span>: <span class="hljs-string">"outy-test"</span>,
<span class="hljs-comment">// 发布开源因此需要将这个字段改为 false</span>
<span class="hljs-string">"private"</span>: <span class="hljs-literal">false</span>,
<span class="hljs-comment">// 这个指 import outy-test 的时候它会去检索的路径</span>
<span class="hljs-string">"main"</span>: <span class="hljs-string">"dist/outy-test.js"</span>,
<span class="copy-code-btn">复制代码</span></code></pre>
<p><strong>index.html</strong>:<br>
因为刚才我们更改webpack.config.js时候把输入文件的filename默认名称<strong>build.js更改为了outy-test.js</strong>因此需要对应上。</p>
<pre><code class="hljs language-html copyable" lang="html"><span class="hljs-meta"><!DOCTYPE <span class="hljs-meta-keyword">html</span>></span>
<span class="hljs-tag"><<span class="hljs-name">html</span> <span class="hljs-attr">lang</span>=<span class="hljs-string">"en"</span>></span>
  <span class="hljs-tag"><<span class="hljs-name">head</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">meta</span> <span class="hljs-attr">charset</span>=<span class="hljs-string">"utf-8"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">title</span>></span>outy-test<span class="hljs-tag"></<span class="hljs-name">title</span>></span>
  <span class="hljs-tag"></<span class="hljs-name">head</span>></span>
  <span class="hljs-tag"><<span class="hljs-name">body</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">id</span>=<span class="hljs-string">"app"</span>></span><span class="hljs-tag"></<span class="hljs-name">div</span>></span>
    <span class="hljs-comment"><!--原来的--></span>
    <span class="hljs-comment"><!-- <script src="/dist/build.js"></script> --></span>
    <span class="hljs-tag"><<span class="hljs-name">script</span> <span class="hljs-attr">src</span>=<span class="hljs-string">"/dist/outy-test.js"</span>></span><span class="hljs-tag"></<span class="hljs-name">script</span>></span>
  <span class="hljs-tag"></<span class="hljs-name">body</span>></span>
<span class="hljs-tag"></<span class="hljs-name">html</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>运行打包命令生成dist文件夹，<code>npm run build</code></li>
</ul>
<p>如果不需要生成该map文件，可以找到webpack.config.js文件注释掉图示内容。</p>
<p><img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/86de563d12c441619bb53532808b2a1b~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a1ff08d4ff4348fdaa82d11820be9b01~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h4 data-id="heading-5">发布到npm</h4>
<ul>
<li>首先<a href="https://link.juejin.cn/?target=https%3A%2F%2Fwww.npmjs.com%2F" target="_blank" rel="nofollow noopener noreferrer" title="https://www.npmjs.com/" ref="nofollow noopener noreferrer">注册npm账号</a></li>
<li><code>npm login</code>，登录
<ul>
<li>坑(<a href="https://link.juejin.cn/?target=https%3A%2F%2Fblog.csdn.net%2Fweixin_42038245%2Farticle%2Fdetails%2F117072614" target="_blank" rel="nofollow noopener noreferrer" title="https://blog.csdn.net/weixin_42038245/article/details/117072614" ref="nofollow noopener noreferrer">参考</a>)：npm源如果为淘宝源会报500错误，必须修改为npm源才能登录：</li>
</ul>
</li>
</ul>
<p><code>npm config set registry https://registry.npmjs.org/</code></p>
<p><img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/232267a5ebfe449085e6cdf53ecf8089~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<ul>
<li><code>npm publish</code>，发布
<ul>
<li>遇到的问题，注册的时候邮箱没验证，打开邮箱验证即可不会出现下面403错误。</li>
</ul>
</li>
</ul>
<p><img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a64a00c02f014e37ad979f9be8909d6c~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer">
发布成功的图示为：</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e3ee5618d1a249f5bd619959b8a9d555~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/46626d0c139245b5b056ab87f7f44de6~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h4 data-id="heading-6">使用</h4>
<ul>
<li>安装</li>
</ul>
<p><code>npm i outy-test -S</code></p>
<ul>
<li>mian.js引入</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">import</span> OutyTest <span class="hljs-keyword">from</span> <span class="hljs-string">'outy-test'</span>
Vue.use(OutyTest)
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>使用</li>
</ul>
<pre><code class="hljs language-vue copyable" lang="vue"><template>
  <div class="home">
    <my-button></my-button>
    <my-text></my-text>
  </div>
</template>
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>显示</li>
</ul>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ad70f3221f4a47dea7fff0729c85f148~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p></div>  
</div>
            
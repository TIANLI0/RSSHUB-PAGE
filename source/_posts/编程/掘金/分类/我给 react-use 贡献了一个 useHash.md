
---
title: '我给 react-use 贡献了一个 useHash'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=8595'
author: 掘金
comments: false
date: Thu, 15 Jul 2021 04:44:04 GMT
thumbnail: 'https://picsum.photos/400/300?random=8595'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><p><strong>目录</strong></p>
<ul>
<li>动机 & 目标</li>
<li><code>useHash</code> - 读写 hash 值</li>
<li><code>useHashSearchParams</code> - 读写 hash 的查询参数</li>
<li><code>useHashSearchParamsJSON</code> - 按 JSON 格式读写 hash 的查询参数</li>
<li>小结</li>
</ul>
<h2 data-id="heading-0">动机 & 目标</h2>
<p>在基于 hash 模式的web单页应用中，经常需要读写 hash 中的查询参数，例如从 hash 查询参数中读取商品ID。在 React 应用中，如果直接解析<code>window.location.hash</code>值，则 hash 变化时无法收到更新，你还需要监听<code>hashchange</code>事件来更新内部状态，这些繁琐的步骤可以封装成自定义 hooks，同时更进一步给参数加上自动类型解析和序列化，使其支持任意参数值类型（包括嵌套的JSON对象），全部这些功能仅需要一个简单的 hook 即可实现。</p>
<p>下面是最终实现的 hook 效果，通过<code>useHashSearchParamsJSON</code> hook 读写指定的查询参数，并且自动解析出正确的类型。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">// http://a/b/c#/a/b/c?id=1&name="jim"</span>
 
<span class="hljs-comment">// 获取指定的查询参数值</span>
<span class="hljs-keyword">const</span> [id, setId] = useHashSearchParamsJSON(<span class="hljs-string">'id'</span>)
<span class="hljs-built_in">console</span>.log(id) <span class="hljs-comment">// 1</span>
 
<span class="hljs-comment">// 获取全部查询参数</span>
<span class="hljs-keyword">const</span> [params, setParams] = useHashSearchParamsJSON()
<span class="hljs-built_in">console</span>.log(params) <span class="hljs-comment">// &#123;id: 1, name: "jim"&#125;</span>

<span class="hljs-comment">// 更新参数</span>
setParams(&#123;...params, <span class="hljs-attr">id</span>: <span class="hljs-number">2</span>&#125;)
<span class="hljs-comment">// http://a/b/c#/a/b/c?id=2&name="jim"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面的 hook 并非一步到位实现的，而是分为三个不同粒度的 hook，分别是<code>useHash</code>(读写 hash 串)、<code>useHashSearchParams</code>(读写查询参数)和<code>userHashSearchParamsJSON</code>(读写带类型的查询参数)，下面本文将介绍如何逐步实现这些自定义的 hooks，从中你除了可以将这些自定义 hooks 用到自己的项目中，同时还可以学习到如何封装自己的 hooks 以便提取可复用的逻辑。</p>
<h2 data-id="heading-1"><code>useHash</code> - 读写 hash 值</h2>
<p>路由参数包含在 URL 的 hash 值中，实现读写路由参数的基础是先实现读写 hash 值，hooks 原型如下：</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">// hash: string - hash 串</span>
<span class="hljs-comment">// setHash: (hash: string) => void - 更新 hash 串</span>
<span class="hljs-keyword">const</span> [hash, setHash] = useHash()
<span class="copy-code-btn">复制代码</span></code></pre>
<p>它返回两个参数，第一个参数是当前 URL 中的 hash 串，第二个参数是 hash 串的更新函数，使用示例如下：</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">// http://www.abc.com/#/path/to/page?id=1</span>

<span class="hljs-keyword">const</span> [hash, setHash] = useHash();
<span class="hljs-built_in">console</span>.log(hash); <span class="hljs-comment">// "#/path/to/page?id=1"</span>

setHash(<span class="hljs-string">"#/path/to/page?id=2"</span>);
<span class="hljs-built_in">console</span>.log(hash); <span class="hljs-comment">// "#/path/to/page?id=2"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>基于以上的期望行为，实现<code>useHash</code>的代码如下，其关键点在于自动监听了<code>hashchange</code>事件，省去了需要使用者重复编写的代码（只有切实的减少工作量和错误，你封装的 hook 才可能会有被其他人使用的欲望）：</p>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-keyword">import</span> &#123; useState, useCallback, useEffect &#125; <span class="hljs-keyword">from</span> <span class="hljs-string">"react"</span>;
 
<span class="hljs-comment">/**
* 读写 URL hash 串，并自动响应 URL hash 串的变化
*/</span>
<span class="hljs-keyword">export</span> <span class="hljs-keyword">const</span> useHash = <span class="hljs-function">() =></span> &#123;
  <span class="hljs-keyword">const</span> [hash, setHash] = useState(<span class="hljs-function">() =></span> <span class="hljs-built_in">window</span>.location.hash);
 
  <span class="hljs-keyword">const</span> onHashChange = useCallback(<span class="hljs-function">() =></span> &#123;
    setHash(<span class="hljs-built_in">window</span>.location.hash);
  &#125;, []);
 
  <span class="hljs-comment">// 监听 hash 串的变化</span>
  useEffect(<span class="hljs-function">() =></span> &#123;
    <span class="hljs-built_in">window</span>.addEventListener(<span class="hljs-string">"hashchange"</span>, onHashChange);
    <span class="hljs-keyword">return</span> <span class="hljs-function">() =></span> &#123;
      <span class="hljs-built_in">window</span>.removeEventListener(<span class="hljs-string">"hashchange"</span>, onHashChange);
    &#125;;
  &#125;, []);
 
  <span class="hljs-keyword">const</span> _setHash = useCallback(
    <span class="hljs-function">(<span class="hljs-params">newHash: <span class="hljs-built_in">string</span></span>) =></span> &#123;
      <span class="hljs-keyword">if</span> (newHash !== hash) &#123;
        <span class="hljs-built_in">window</span>.location.hash = newHash;
      &#125;
    &#125;,
    [hash]
  );
 
  <span class="hljs-keyword">return</span> [hash, _setHash] <span class="hljs-keyword">as</span> <span class="hljs-keyword">const</span>;
&#125;;
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p><code>useHash</code>的实现合入到 <a href="https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fstreamich%2Freact-use%2Fblob%2Fmaster%2Fdocs%2FuseHash.md" target="_blank" rel="nofollow noopener noreferrer" title="https://github.com/streamich/react-use/blob/master/docs/useHash.md" ref="nofollow noopener noreferrer">react-use</a> 仓库，可以引入 react-use 包直接使用。</p>
</blockquote>
<h2 data-id="heading-2"><code>useHashSearchParams</code> - 读写 hash 的查询参数</h2>
<p>有了<code>useHash</code>我们可以方便的读写 URL hash 值了，接下来要实现读写 hash 中的查询参数，查询参数格式是<code>key1=value1&key2=value2&...</code>，其核心是解析查询参数中的键值对。</p>
<p>hooks 的原型如下：</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">// value: string - 指定 key 的值</span>
<span class="hljs-comment">// setValue: (value: string) => void - 更新指定 key 的值</span>
<span class="hljs-keyword">const</span> [value, setValue] = useHashSearchParams(key)

<span class="hljs-comment">// query: Record<string, string> - 所有查询参数</span>
<span class="hljs-comment">// setQuery: (query: Record<string, string>) => void - 更新查询参数</span>
<span class="hljs-keyword">const</span> [query, setQuery] = useHashSearchParams()
<span class="copy-code-btn">复制代码</span></code></pre>
<p>它返回两个参数，第一个参数表示指定的 key 的值（或者所有 key/value 组成的对象），第二个参数用于更新指定的 key 的值（或者更新整个查询参数）。使用示例如下：</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">// http://a/b/c#/a/b/c?id=1&name=jim</span>
 
<span class="hljs-comment">// 读取单个查询参数</span>
<span class="hljs-keyword">const</span> [id, setId] = useHashSearchParams(<span class="hljs-string">"id"</span>);
<span class="hljs-built_in">console</span>.log(id); <span class="hljs-comment">// "1"</span>
<span class="hljs-comment">// 修改单个查询参数</span>
setId(<span class="hljs-number">2</span>);
<span class="hljs-built_in">console</span>.log(id); <span class="hljs-comment">// "2"</span>
 
<span class="hljs-comment">// 读取所有查询参数</span>
<span class="hljs-keyword">const</span> [params, setParams] = useHashSearchParams();
<span class="hljs-built_in">console</span>.log(params); <span class="hljs-comment">// &#123;id: "1", name: "jim"&#125;</span>
<span class="hljs-comment">// 修改整个查询参数</span>
setParams(&#123; <span class="hljs-attr">name</span>: <span class="hljs-string">"jack"</span> &#125;);
<span class="hljs-built_in">console</span>.log(params); <span class="hljs-comment">// &#123;id: "1", name: "jack"&#125;</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>实现思路：读取时调用<code>useHash</code>获取 URL hash 值，然后截取 hash 中的查询串，并使用<code>URLSearchParams</code>解析成键值对返回。写入时修改键值对，然后拼接成查询串，调用<code>setHash</code>写回 URL hash 值。这里关键点是注意查询参数的 key/value 编码和解码，使用<code>URLSearchParams</code>解析 hash 串时，它会帮我们解码，将查询参数序列化成 hash 串时，我们需要自行进行编码。此外，要注意区分读写的是单个还是所有的查询参数。</p>
<p>最终代码实现如下：</p>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-keyword">import</span> &#123; useHash &#125; <span class="hljs-keyword">from</span> <span class="hljs-string">"./useHash"</span>;
<span class="hljs-keyword">import</span> &#123; useCallback &#125; <span class="hljs-keyword">from</span> <span class="hljs-string">"react"</span>;
 
<span class="hljs-comment">// 重载函数签名</span>
<span class="hljs-keyword">interface</span> UseHashSearchParamsType &#123;
  (key: <span class="hljs-built_in">string</span>, defaultValue?: <span class="hljs-built_in">string</span>): <span class="hljs-keyword">readonly</span> [<span class="hljs-built_in">string</span>, <span class="hljs-function">(<span class="hljs-params">value: <span class="hljs-built_in">any</span></span>) =></span> <span class="hljs-built_in">void</span>];
  (): <span class="hljs-keyword">readonly</span> [
    Record<<span class="hljs-built_in">string</span>, <span class="hljs-built_in">string</span>>,
    <span class="hljs-function">(<span class="hljs-params">searchParams: Record<<span class="hljs-built_in">string</span>, <span class="hljs-built_in">any</span>></span>) =></span> <span class="hljs-built_in">void</span>
  ];
&#125;
 
<span class="hljs-keyword">export</span> <span class="hljs-keyword">const</span> useHashSearchParams: UseHashSearchParamsType = (
  key?: <span class="hljs-built_in">any</span>,
  defaultValue?: <span class="hljs-built_in">any</span>
): <span class="hljs-function"><span class="hljs-params">any</span> =></span> &#123;
  <span class="hljs-keyword">const</span> [hash, setHash] = useHash();
  <span class="hljs-keyword">const</span> questionIndex = hash.indexOf(<span class="hljs-string">"?"</span>);
  <span class="hljs-keyword">const</span> search = questionIndex !== -<span class="hljs-number">1</span> ? hash.substring(questionIndex) : <span class="hljs-string">""</span>;
  <span class="hljs-comment">// 解析查询参数</span>
  <span class="hljs-keyword">const</span> usp = <span class="hljs-keyword">new</span> URLSearchParams(search);
 
  <span class="hljs-keyword">const</span> hashSearchParams: Record<<span class="hljs-built_in">string</span>, <span class="hljs-built_in">string</span>> = &#123;&#125;;
  usp.forEach(<span class="hljs-function">(<span class="hljs-params">value, key</span>) =></span> &#123;
    hashSearchParams[key] = value;
  &#125;);
 
  <span class="hljs-keyword">const</span> setHashSearchParams = useCallback(
    <span class="hljs-function">(<span class="hljs-params">searchParams: Record<<span class="hljs-built_in">string</span>, <span class="hljs-built_in">any</span>></span>) =></span> &#123;
      <span class="hljs-keyword">const</span> searchPrefix =
        (questionIndex !== -<span class="hljs-number">1</span> ? hash.slice(<span class="hljs-number">0</span>, questionIndex) : hash.slice(<span class="hljs-number">0</span>)) +
        <span class="hljs-string">"?"</span>;
      <span class="hljs-comment">// 拼接查询参数，并进行编码处理</span>
      <span class="hljs-keyword">const</span> search = <span class="hljs-built_in">Object</span>.keys(searchParams).reduce(<span class="hljs-function">(<span class="hljs-params">finalSearch, key</span>) =></span> &#123;
        <span class="hljs-keyword">if</span> (finalSearch) finalSearch += <span class="hljs-string">"&"</span>;
        <span class="hljs-keyword">const</span> value = <span class="hljs-built_in">String</span>(searchParams[key]);
        finalSearch += <span class="hljs-built_in">encodeURIComponent</span>(key);
        <span class="hljs-comment">// remove '=' if param with empty value</span>
        <span class="hljs-keyword">if</span> (value) &#123;
          finalSearch += <span class="hljs-string">"="</span> + <span class="hljs-built_in">encodeURIComponent</span>(value);
        &#125;
        <span class="hljs-keyword">return</span> finalSearch;
      &#125;, <span class="hljs-string">""</span>);
      setHash(searchPrefix + search);
    &#125;,
    [hash, questionIndex, setHash]
  );
 
  <span class="hljs-keyword">if</span> (key) &#123;
    <span class="hljs-keyword">return</span> [
      hashSearchParams[key] === <span class="hljs-literal">undefined</span>
        ? defaultValue
        : hashSearchParams[key],
      <span class="hljs-function">(<span class="hljs-params">value: <span class="hljs-built_in">any</span></span>) =></span>
        setHashSearchParams(&#123; ...hashSearchParams, [key]: <span class="hljs-built_in">String</span>(value) &#125;),
    ];
  &#125; <span class="hljs-keyword">else</span> &#123;
    <span class="hljs-keyword">return</span> [hashSearchParams, setHashSearchParams];
  &#125;
&#125;;
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p><code>useHashSearchParams</code>已提交 PR 到 <a href="https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fstreamich%2Freact-use%2Fpull%2F1300" target="_blank" rel="nofollow noopener noreferrer" title="https://github.com/streamich/react-use/pull/1300" ref="nofollow noopener noreferrer">react-use</a> 仓库，待合入后，可引入 react-use 包使用</p>
</blockquote>
<h2 data-id="heading-3"><code>useHashSearchParamsJSON</code> - 按 JSON 格式读写 hash 的查询参数</h2>
<p>基于<code>useHashSearchParams</code>已经可以很方便的实现对 URL hash 中的查询参数进行读写了，但是这里的参数值都是字符串类型，实际使用时经常还需要根据字段所属类型进行类型解析，例如<code>http://a/b/c#/a/b/c?id=1&name=jim</code>中的 id 是数值类型，使用时需要先调用<code>parseInt</code>解析成数字，对于实际业务开发非常不便。</p>
<p>我期望路由参数能自包含数据类型，同时又能序列化成字符串，最佳的数据格式就是 JSON 格式了。将查询参数序列化为 JSON 后作为 hash 串，使用时解析 JSON 得到正确的数据类型，同时还可以支持在 hash 中存放复杂的 JSON 对象，从而支持页面间跳转时传递 JavaScript 纯对象。</p>
<p>hooks 原型如下：</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">// value: any - 指定 key 的值，任意类型</span>
<span class="hljs-comment">// setValue: (value: any) => void - 更新指定 key 的值</span>
<span class="hljs-keyword">const</span> [value, setValue] = useHashSearchParamsJSON(key)

<span class="hljs-comment">// query: Record<string, any> - 所有查询参数，其中值可以是任意类型</span>
<span class="hljs-comment">// setQuery: (query: Record<string, any>) => void - 更新查询参数</span>
<span class="hljs-keyword">const</span> [query, setQuery] = useHashSearchParamsJSON()
<span class="copy-code-btn">复制代码</span></code></pre>
<p>使用示例如下：</p>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-comment">// http://a/b/c#/a/b/c?id=1&name="jim"</span>
 
<span class="hljs-keyword">const</span> [id, setId] = useHashSearchParamsJSON<<span class="hljs-built_in">number</span>>(<span class="hljs-string">'id'</span>)
<span class="hljs-built_in">console</span>.log(id) <span class="hljs-comment">// 1</span>
 
<span class="hljs-keyword">const</span> [name, setName] = useHashSearchParamsJSON<<span class="hljs-built_in">string</span>>(<span class="hljs-string">'name'</span>)
<span class="hljs-built_in">console</span>.log(name) <span class="hljs-comment">// "jim"</span>
 
<span class="hljs-keyword">const</span> [params, setParams] = useHashSearchParamsJSON()
<span class="hljs-built_in">console</span>.log(params) <span class="hljs-comment">// &#123;id: 1, name: "jim"&#125;</span>
setParams(&#123;<span class="hljs-attr">empty</span>: <span class="hljs-literal">true</span>&#125;)
<span class="hljs-built_in">console</span>.log(params) <span class="hljs-comment">// &#123;id: 1, name: "jim", empty: true&#125;</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>实现思路：读取时先通过<code>useHashSearchParams</code>获取查询参数值的字符串表示，然后通过<code>JSON.parse</code>解析得到 JS 类型。写入时先通过<code>JSON.stringify</code>序列化成字符串表示，然后通过<code>useHashSearchParams</code>提供的更新函数写回到 hash 串中。</p>
<p>实现代码如下：</p>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-keyword">import</span> &#123; useCallback &#125; <span class="hljs-keyword">from</span> <span class="hljs-string">'react'</span>
<span class="hljs-keyword">import</span> &#123; useHashSearchParams &#125; <span class="hljs-keyword">from</span> <span class="hljs-string">'react-use'</span>
 
<span class="hljs-keyword">const</span> mapValues = <span class="hljs-function">(<span class="hljs-params">src, fn</span>) =></span>
  <span class="hljs-built_in">Object</span>.keys(src).reduce(
    <span class="hljs-function">(<span class="hljs-params">target, key</span>) =></span> <span class="hljs-built_in">Object</span>.assign(target, &#123; [key]: fn(src[key]) &#125;),
    &#123;&#125;
  );
 
<span class="hljs-comment">// 重载函数签名</span>
<span class="hljs-keyword">interface</span> UseRouteParamsType &#123;
  <T = <span class="hljs-built_in">any</span>>(key: <span class="hljs-built_in">string</span>, defaultValue?: T): [T | <span class="hljs-literal">undefined</span>, <span class="hljs-function">(<span class="hljs-params">value: T</span>) =></span> <span class="hljs-built_in">void</span>]
  <T = <span class="hljs-built_in">any</span>>(): [Record<<span class="hljs-built_in">string</span>, T | <span class="hljs-literal">undefined</span>>, <span class="hljs-function">(<span class="hljs-params">searchParams: Record<<span class="hljs-built_in">string</span>, T></span>) =></span> <span class="hljs-built_in">void</span>]
&#125;

<span class="hljs-keyword">export</span> <span class="hljs-keyword">const</span> useHashSearchParamsJSON: UseRouteParamsType = (key?: <span class="hljs-built_in">any</span>, defaultValue?: <span class="hljs-built_in">any</span>): <span class="hljs-function"><span class="hljs-params">any</span> =></span> &#123;
  <span class="hljs-keyword">const</span> dispatch = useTDispatch()
  <span class="hljs-comment">// 获取指定 key 的 value 值，此时是字符串格式</span>
  <span class="hljs-keyword">const</span> [json, setJson] = useHashSearchParams(key)
  <span class="hljs-keyword">let</span> value: <span class="hljs-built_in">any</span>
 
  <span class="hljs-comment">// 调用 JSON.parse 解析 JSON 字符串到 JS 值，解析可能会失败需捕获异常处理</span>
  <span class="hljs-keyword">try</span> &#123;
    value = key
      ? json === <span class="hljs-literal">undefined</span>
        ? defaultValue
        : <span class="hljs-built_in">JSON</span>.parse(json)
      : _.mapValues(json, <span class="hljs-function">(<span class="hljs-params">v</span>) =></span> <span class="hljs-built_in">JSON</span>.parse(v))
  &#125; <span class="hljs-keyword">catch</span> (err) &#123;
    <span class="hljs-comment">// debugErr(err)</span>
  &#125;

  <span class="hljs-comment">// 调用 JSON.stringify 序列化 JS 值成 JSON 字符串</span>
  <span class="hljs-keyword">const</span> setValue = useCallback(
    <span class="hljs-function">(<span class="hljs-params">newValue: <span class="hljs-built_in">any</span></span>) =></span> &#123;
      <span class="hljs-keyword">if</span> (key) &#123;
        setJson(<span class="hljs-built_in">JSON</span>.stringify(newValue))
      &#125; <span class="hljs-keyword">else</span> &#123;
        setJson(_.mapValues(newValue, <span class="hljs-function">(<span class="hljs-params">v</span>) =></span> <span class="hljs-built_in">JSON</span>.stringify(v)))
      &#125;
    &#125;,
    [dispatch.shared, key, setJson, value]
  )
 
  <span class="hljs-keyword">return</span> [value, setValue]
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p><code>useHashSearchParamsJSON</code>适用范围比较有限，不考虑合入 react-use，如果需要可以参考上述代码自行在项目中实现。</p>
</blockquote>
<h2 data-id="heading-4">小结</h2>
<p>本文实现的对路由参数进行读写的 hooks，本身具有很强的实用价值，其次可作为自定义 hooks 的学习参考。此外，遇到功能复杂的 hooks 可尝试像本文一样先分解 hooks 然后分步实现：先找出更通用的 hooks(如<code>useHash</code>)，再基于已有的 hook 实现功能更特定的 hooks(如<code>useHashSearchParams</code>)。</p></div>  
</div>
            

---
title: '重学JS之Generator函数'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=3927'
author: 掘金
comments: false
date: Thu, 15 Jul 2021 23:00:49 GMT
thumbnail: 'https://picsum.photos/400/300?random=3927'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h2 data-id="heading-0">一、概念</h2>
<p>Generator 函数是协程在 ES6 的实现，最大特点就是可以交出函数的执行权（即暂停执行）。</p>
<pre><code class="copyable">function* gen(x) &#123;  let y = yield x + 2;  return y;&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码就是一个 Generator 函数。它不同于普通函数，是可以暂停执行的，所以函数名之前要加星号，以示区别。</p>
<p>整个 Generator 函数就是一个封装的异步任务，或者说是异步任务的容器。异步操作需要暂停的地方，都用 yield 语句注明。Generator 函数的执行方法如下：</p>
<pre><code class="copyable">let g = gen(1);console.log(g.next()); console.log(g.next()); 
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，调用 Generator 函数，会返回一个内部指针（即<a href="https://link.juejin.cn/?target=https%3A%2F%2Fes6.ruanyifeng.com%2F%23docs%2Fiterator" target="_blank" rel="nofollow noopener noreferrer" title="https://es6.ruanyifeng.com/#docs/iterator" ref="nofollow noopener noreferrer">遍历器</a> ）g 。</p>
<p><strong>这是 Generator 函数不同于普通函数的另一个地方，即执行它不会返回结果，返回的是指针对象。</strong></p>
<p>调用指针 g 的 next 方法，会移动内部指针（即执行异步任务的第一段），指向第一个遇到的 yield 语句，上例是执行到 x + 2 为止。</p>
<p>换言之，next 方法的作用是分阶段执行 Generator 函数。每次调用 next 方法，会返回一个对象，表示当前阶段的信息（ value 属性和 done 属性）。</p>
<p>value 属性是 yield 语句后面表达式的值，表示当前阶段的值；</p>
<p>done 属性是一个布尔值，表示 Generator 函数是否执行完毕，即是否还有下一个阶段。</p>
<p>结果如下：</p>
<pre><code class="copyable">&#123; value: 3, done: false &#125;
&#123; value: undefined, done: true &#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-1">二、Generator 函数的数据交换和错误处理</h2>
<p>Generator 函数可以暂停执行和恢复执行，这是它能封装异步任务的根本原因。</p>
<p>除此之外，它还有两个特性，使它可以作为异步编程的完整解决方案：函数体内外的数据交换和错误处理机制。</p>
<p>next 方法返回值的 value 属性，是 Generator 函数向外输出数据；next 方法还可以接受参数，这是向 Generator 函数体内输入数据。</p>
<pre><code class="copyable">function* gen(x)&#123;
  var y = yield x + 2;
  return y;
&#125;

var g = gen(1);
g.next() // &#123; value: 3, done: false &#125;
g.next(2) // &#123; value: 2, done: true &#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，第一个 next 方法的 value 属性，返回表达式 x + 2 的值（3）。第二个 next 方法带有参数2，这个参数可以传入 Generator 函数，作为上个阶段异步任务的返回结果，被函数体内的变量 y 接收。因此，这一步的 value 属性，返回的就是2（变量 y 的值）。</p>
<p>Generator 函数内部还可以部署错误处理代码，捕获函数体外抛出的错误。</p>
<pre><code class="copyable">function* gen(x)&#123;
  let y;
  try &#123;
    y = yield x + 2;
  &#125; catch (e)&#123; 
    console.log(e); // 此处打印出错了
  &#125;
  return y;
&#125;

var g = gen(1);
console.log(g.next()); 
console.log(g.throw('出错了'));  // 被catch捕获
// 打印结果
&#123; value: 3, done: false &#125;
出错了
&#123; value: undefined, done: true &#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码的最后一行，Generator 函数体外，使用指针对象的 throw 方法抛出的错误，可以被函数体内的 try ... catch 代码块捕获。这意味着，出错的代码与处理错误的代码，实现了时间和空间上的分离，这对于异步编程无疑是很重要的。</p>
<h2 data-id="heading-2">三、Generator 函数的用法</h2>
<p>下面看看如何使用 Generator 函数，执行一个真实的异步任务。</p>
<pre><code class="copyable">var fetch = require('node-fetch');function* gen () &#123;  let url = 'https://api.github.com/users/github';  let result = yield fetch(url);  console.log(result.bio);&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，Generator 函数封装了一个异步操作，该操作先读取一个远程接口，然后从 JSON 格式的数据解析信息。就像前面说过的，这段代码非常像同步操作，除了加上了 yield 命令。</p>
<p>执行这段代码的方法如下:</p>
<pre><code class="copyable">var g = gen();
var result = g.next();

result.value.then(function(data)&#123;
  return data.json();
&#125;).then(function(data)&#123;
  g.next(data);
&#125;);
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，首先执行 Generator 函数，获取遍历器对象，然后使用 next 方法（第二行），执行异步任务的第一阶段。由于 <a href="https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fbitinn%2Fnode-fetch" target="_blank" rel="nofollow noopener noreferrer" title="https://github.com/bitinn/node-fetch" ref="nofollow noopener noreferrer">Fetch 模块</a>返回的是一个 Promise 对象，因此要用 then 方法调用下一个next 方法。</p>
<p>可以看到，虽然 Generator 函数将异步操作表示得很简洁，但是流程管理却不方便（即何时执行第一阶段、何时执行第二阶段）。</p>
<p>转自 阮一峰 <a href="https://link.juejin.cn/?target=https%3A%2F%2Fes6.ruanyifeng.com%2F%23docs%2Fgenerator" target="_blank" rel="nofollow noopener noreferrer" title="https://es6.ruanyifeng.com/#docs/generator" ref="nofollow noopener noreferrer">es6.ruanyifeng.com/#docs/gener…</a></p></div>  
</div>
            
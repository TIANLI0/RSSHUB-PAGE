
---
title: '包装对象 Boolean，Number，String'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=8213'
author: 掘金
comments: false
date: Thu, 15 Jul 2021 18:43:36 GMT
thumbnail: 'https://picsum.photos/400/300?random=8213'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h1 data-id="heading-0">包装对象</h1>
<blockquote>
<p>对象是 JavaScript 语言最主要的数据类型，三种原始类型的值——数值、字符串、布尔值——在一定条件下，也会自动转为对象，也就是原始类型的“包装对象”</p>
</blockquote>
<p>所谓“包装对象”，指的是与数值、字符串、布尔值分别相对应的Number、String、Boolean三个原生对象。这三个原生对象可以把原始类型的值变成（包装成）对象。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> v1 = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Number</span>(<span class="hljs-number">123</span>);
<span class="hljs-keyword">var</span> v2 = <span class="hljs-keyword">new</span> <span class="hljs-built_in">String</span>(<span class="hljs-string">'abc'</span>);
<span class="hljs-keyword">var</span> v3 = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Boolean</span>(<span class="hljs-literal">true</span>);

<span class="hljs-keyword">typeof</span> v1 <span class="hljs-comment">// "object"</span>
<span class="hljs-keyword">typeof</span> v2 <span class="hljs-comment">// "object"</span>
<span class="hljs-keyword">typeof</span> v3 <span class="hljs-comment">// "object"</span>

v1 == <span class="hljs-number">123</span> <span class="hljs-comment">// true</span>
v2 == <span class="hljs-string">'abc'</span> <span class="hljs-comment">// true</span>
v3 == <span class="hljs-literal">true</span> <span class="hljs-comment">// true</span>

v1 === <span class="hljs-number">123</span> <span class="hljs-comment">// false</span>
v2 === <span class="hljs-string">'abc'</span> <span class="hljs-comment">// false</span>
v3 === <span class="hljs-literal">true</span> <span class="hljs-comment">// false</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，基于原始类型的值，生成了三个对应的包装对象。可以看到，v1、v2、v3都是对象，且与对应的简单类型值不相等。</p>
<pre><code class="hljs language-js copyable" lang="js">包装对象的设计目的，首先是使得“对象”这种类型可以覆盖 JavaScript 所有的值，
整门语言有一个通用的数据模型，其次是使得原始类型的值也有办法调用自己的方法。
<span class="copy-code-btn">复制代码</span></code></pre>
<p>Number、String和Boolean这三个原生对象，如果不作为构造函数调用（即调用时不加new），而是作为普通函数调用，用于将任意类型的值转为数值、字符串和布尔值。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">// 字符串转为数值</span>
<span class="hljs-built_in">Number</span>(<span class="hljs-string">'123'</span>) <span class="hljs-comment">// 123</span>

<span class="hljs-comment">// 数值转为字符串</span>
<span class="hljs-built_in">String</span>(<span class="hljs-number">123</span>) <span class="hljs-comment">// "123"</span>

<span class="hljs-comment">// 数值转为布尔值</span>
<span class="hljs-built_in">Boolean</span>(<span class="hljs-number">123</span>) <span class="hljs-comment">// true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>总结一下，这三个对象作为构造函数使用（带有new）时，可以将原始类型的值转为对象；作为普通函数使用时（不带有new），可以将任意类型的值，转为原始类型的值。</p>
<h2 data-id="heading-1">实例方法</h2>
<p>三种包装对象各自提供了许多实例方法，详见后文。这里介绍两种它们共同具有、从Object对象继承的方法：valueOf()和toString()。</p>
<h3 data-id="heading-2">valueOf()</h3>
<p>valueOf()方法返回包装对象实例对应的原始类型的值。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">new</span> <span class="hljs-built_in">Number</span>(<span class="hljs-number">123</span>).valueOf()  <span class="hljs-comment">// 123</span>
<span class="hljs-keyword">new</span> <span class="hljs-built_in">String</span>(<span class="hljs-string">'abc'</span>).valueOf() <span class="hljs-comment">// "abc"</span>
<span class="hljs-keyword">new</span> <span class="hljs-built_in">Boolean</span>(<span class="hljs-literal">true</span>).valueOf() <span class="hljs-comment">// true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-3">toString()</h3>
<p>toString()方法返回对应的字符串形式。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">new</span> <span class="hljs-built_in">Number</span>(<span class="hljs-number">123</span>).toString() <span class="hljs-comment">// "123"</span>
<span class="hljs-keyword">new</span> <span class="hljs-built_in">String</span>(<span class="hljs-string">'abc'</span>).toString() <span class="hljs-comment">// "abc"</span>
<span class="hljs-keyword">new</span> <span class="hljs-built_in">Boolean</span>(<span class="hljs-literal">true</span>).toString() <span class="hljs-comment">// "true"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-4">原始类型与实例对象的自动转换</h2>
<p>某些场合，原始类型的值会自动当作包装对象调用，即调用包装对象的属性和方法。这时，JavaScript 引擎会自动将原始类型的值转为包装对象实例，并在使用后立刻销毁实例。</p>
<p>比如，字符串可以调用length属性，返回字符串的长度。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'abc'</span>.length <span class="hljs-comment">// 3</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，abc是一个字符串，本身不是对象，不能调用length属性。JavaScript 引擎自动将其转为包装对象，在这个对象上调用length属性。调用结束后，这个临时对象就会被销毁。这就叫原始类型与实例对象的自动转换。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> str = <span class="hljs-string">'abc'</span>;
str.length <span class="hljs-comment">// 3</span>

<span class="hljs-comment">// 等同于</span>
<span class="hljs-keyword">var</span> strObj = <span class="hljs-keyword">new</span> <span class="hljs-built_in">String</span>(str)
<span class="hljs-comment">// String &#123;</span>
<span class="hljs-comment">//   0: "a", 1: "b", 2: "c", length: 3, [[PrimitiveValue]]: "abc"</span>
<span class="hljs-comment">// &#125;</span>
strObj.length <span class="hljs-comment">// 3</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，字符串abc的包装对象提供了多个属性，length只是其中之一。</p>
<p>自动转换生成的包装对象是只读的，无法修改。所以，字符串无法添加新属性。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> s = <span class="hljs-string">'Hello World'</span>;
s.x = <span class="hljs-number">123</span>;
s.x <span class="hljs-comment">// undefined</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码为字符串s添加了一个x属性，结果无效，总是返回undefined。</p>
<p>另一方面，调用结束后，包装对象实例会自动销毁。这意味着，下一次调用字符串的属性时，实际是调用一个新生成的对象，而不是上一次调用时生成的那个对象，所以取不到赋值在上一个对象的属性。如果要为字符串添加属性，只有在它的原型对象String.prototype上定义</p>
<h2 data-id="heading-5">自定义方法</h2>
<p>除了原生的实例方法，包装对象还可以自定义方法和属性，供原始类型的值直接调用。</p>
<p>比如，我们可以新增一个double方法，使得字符串和数字翻倍。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">String</span>.prototype.double = <span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params"></span>) </span>&#123;
  <span class="hljs-keyword">return</span> <span class="hljs-built_in">this</span>.valueOf() + <span class="hljs-built_in">this</span>.valueOf();
&#125;;

<span class="hljs-string">'abc'</span>.double()
<span class="hljs-comment">// abcabc</span>

<span class="hljs-built_in">Number</span>.prototype.double = <span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params"></span>) </span>&#123;
  <span class="hljs-keyword">return</span> <span class="hljs-built_in">this</span>.valueOf() + <span class="hljs-built_in">this</span>.valueOf();
&#125;;

(<span class="hljs-number">123</span>).double() <span class="hljs-comment">// 246</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码在String和Number这两个对象的原型上面，分别自定义了一个方法，从而可以在所有实例对象上调用。注意，最后一行的123外面必须要加上圆括号，否则后面的点运算符（.）会被解释成小数点。</p>
<h1 data-id="heading-6">Boolean 对象</h1>
<blockquote>
<p>Boolean对象是 JavaScript 的三个包装对象之一。作为构造函数，它主要用于生成布尔值的包装对象实例。</p>
</blockquote>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> b = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Boolean</span>(<span class="hljs-literal">true</span>);

<span class="hljs-keyword">typeof</span> b <span class="hljs-comment">// "object"</span>
b.valueOf() <span class="hljs-comment">// true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码的变量b是一个Boolean对象的实例，它的类型是对象，值为布尔值true。</p>
<p>注意，false对应的包装对象实例，布尔运算结果也是true。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">if</span> (<span class="hljs-keyword">new</span> <span class="hljs-built_in">Boolean</span>(<span class="hljs-literal">false</span>)) &#123;
  <span class="hljs-built_in">console</span>.log(<span class="hljs-string">'true'</span>);
&#125; <span class="hljs-comment">// true</span>

<span class="hljs-keyword">if</span> (<span class="hljs-keyword">new</span> <span class="hljs-built_in">Boolean</span>(<span class="hljs-literal">false</span>).valueOf()) &#123;
  <span class="hljs-built_in">console</span>.log(<span class="hljs-string">'true'</span>);
&#125; <span class="hljs-comment">// 无输出</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码的第一个例子之所以得到true，是因为false对应的包装对象实例是一个对象，进行逻辑运算时，被自动转化成布尔值true（因为所有对象对应的布尔值都是true）。而实例的valueOf方法，则返回实例对应的原始值，本例为false。</p>
<h2 data-id="heading-7">Boolean 函数的类型转换作用</h2>
<p>Boolean对象除了可以作为构造函数，还可以单独使用，将任意值转为布尔值。这时Boolean就是一个单纯的工具方法。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">Boolean</span>(<span class="hljs-literal">undefined</span>) <span class="hljs-comment">// false</span>
<span class="hljs-built_in">Boolean</span>(<span class="hljs-literal">null</span>) <span class="hljs-comment">// false</span>
<span class="hljs-built_in">Boolean</span>(<span class="hljs-number">0</span>) <span class="hljs-comment">// false</span>
<span class="hljs-built_in">Boolean</span>(<span class="hljs-string">''</span>) <span class="hljs-comment">// false</span>
<span class="hljs-built_in">Boolean</span>(<span class="hljs-literal">NaN</span>) <span class="hljs-comment">// false</span>

<span class="hljs-built_in">Boolean</span>(<span class="hljs-number">1</span>) <span class="hljs-comment">// true</span>
<span class="hljs-built_in">Boolean</span>(<span class="hljs-string">'false'</span>) <span class="hljs-comment">// true</span>
<span class="hljs-built_in">Boolean</span>([]) <span class="hljs-comment">// true</span>
<span class="hljs-built_in">Boolean</span>(&#123;&#125;) <span class="hljs-comment">// true</span>
<span class="hljs-built_in">Boolean</span>(<span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params"></span>) </span>&#123;&#125;) <span class="hljs-comment">// true</span>
<span class="hljs-built_in">Boolean</span>(<span class="hljs-regexp">/foo/</span>) <span class="hljs-comment">// true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>顺便提一下，使用双重的否运算符（!）也可以将任意值转为对应的布尔值。</p>
<pre><code class="hljs language-js copyable" lang="js">!!<span class="hljs-literal">undefined</span> <span class="hljs-comment">// false</span>
!!<span class="hljs-literal">null</span> <span class="hljs-comment">// false</span>
!!<span class="hljs-number">0</span> <span class="hljs-comment">// false</span>
!!<span class="hljs-string">''</span> <span class="hljs-comment">// false</span>
!!<span class="hljs-literal">NaN</span> <span class="hljs-comment">// false</span>

!!<span class="hljs-number">1</span> <span class="hljs-comment">// true</span>
!!<span class="hljs-string">'false'</span> <span class="hljs-comment">// true</span>
!![] <span class="hljs-comment">// true</span>
!!&#123;&#125; <span class="hljs-comment">// true</span>
!!<span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params"></span>)</span>&#123;&#125; <span class="hljs-comment">// true</span>
!!<span class="hljs-regexp">/foo/</span> <span class="hljs-comment">// true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>最后，对于一些特殊值，Boolean对象前面加不加new，会得到完全相反的结果，必须小心。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">if</span> (<span class="hljs-built_in">Boolean</span>(<span class="hljs-literal">false</span>)) &#123;
  <span class="hljs-built_in">console</span>.log(<span class="hljs-string">'true'</span>);
&#125; <span class="hljs-comment">// 无输出</span>

<span class="hljs-keyword">if</span> (<span class="hljs-keyword">new</span> <span class="hljs-built_in">Boolean</span>(<span class="hljs-literal">false</span>)) &#123;
  <span class="hljs-built_in">console</span>.log(<span class="hljs-string">'true'</span>);
&#125; <span class="hljs-comment">// true</span>

<span class="hljs-keyword">if</span> (<span class="hljs-built_in">Boolean</span>(<span class="hljs-literal">null</span>)) &#123;
  <span class="hljs-built_in">console</span>.log(<span class="hljs-string">'true'</span>);
&#125; <span class="hljs-comment">// 无输出</span>

<span class="hljs-keyword">if</span> (<span class="hljs-keyword">new</span> <span class="hljs-built_in">Boolean</span>(<span class="hljs-literal">null</span>)) &#123;
  <span class="hljs-built_in">console</span>.log(<span class="hljs-string">'true'</span>);
&#125; <span class="hljs-comment">// true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h1 data-id="heading-8">Number 对象</h1>
<blockquote>
<p>Number对象是数值对应的包装对象，可以作为构造函数使用，也可以作为工具函数使用。</p>
</blockquote>
<p>作为构造函数时，它用于生成值为数值的对象。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> n = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Number</span>(<span class="hljs-number">1</span>);
<span class="hljs-keyword">typeof</span> n <span class="hljs-comment">// "object"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，Number对象作为构造函数使用，返回一个值为1的对象。</p>
<p>作为工具函数时，它可以将任何类型的值转为数值。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">Number</span>(<span class="hljs-literal">true</span>) <span class="hljs-comment">// 1</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码将布尔值true转为数值1。Number作为工具函数的用法，详见<a href="https://juejin.cn/post/6980169329555800078" target="_blank" title="https://juejin.cn/post/6980169329555800078">js数据类型知多少</a>。</p>
<h2 data-id="heading-9">静态属性</h2>
<ul>
<li>Number对象拥有以下一些静态属性（即直接定义在Number对象上的属性，而不是定义在实例上的属性）。</li>
<li>Number.POSITIVE_INFINITY：正的无限，指向Infinity。</li>
<li>Number.NEGATIVE_INFINITY：负的无限，指向-Infinity。</li>
<li>Number.NaN：表示非数值，指向NaN。</li>
<li>Number.MIN_VALUE：表示最小的正数（即最接近0的正数，在64位浮点数体系中为5e-324），相应的，最接近0的负数为-Number.MIN_VALUE。</li>
<li>Number.MAX_SAFE_INTEGER：表示能够精确表示的最大整数，即9007199254740991。</li>
<li>Number.MIN_SAFE_INTEGER：表示能够精确表示的最小整数，即-9007199254740991。</li>
</ul>
<h2 data-id="heading-10">实例方法（常用）</h2>
<h3 data-id="heading-11">Number.prototype.toString()</h3>
<p>Number对象部署了自己的toString方法，用来将一个数值转为字符串形式。</p>
<pre><code class="hljs language-js copyable" lang="js">(<span class="hljs-number">10</span>).toString() <span class="hljs-comment">// "10"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>toString方法可以接受一个参数，表示输出的进制。如果省略这个参数，默认将数值先转为十进制，再输出字符串；否则，就根据参数指定的进制，将一个数字转化成某个进制的字符串。</p>
<pre><code class="hljs language-js copyable" lang="js">(<span class="hljs-number">10</span>).toString(<span class="hljs-number">2</span>) <span class="hljs-comment">// "1010"</span>
(<span class="hljs-number">10</span>).toString(<span class="hljs-number">8</span>) <span class="hljs-comment">// "12"</span>
(<span class="hljs-number">10</span>).toString(<span class="hljs-number">16</span>) <span class="hljs-comment">// "a"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，10一定要放在括号里，这样表明后面的点表示调用对象属性。如果不加括号，这个点会被 JavaScript 引擎解释成小数点，从而报错。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-number">10.</span>toString(<span class="hljs-number">2</span>)
<span class="hljs-comment">// SyntaxError: Unexpected token ILLEGAL</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>只要能够让 JavaScript 引擎不混淆小数点和对象的点运算符，各种写法都能用。除了为10加上括号，还可以在10后面加两个点，JavaScript 会把第一个点理解成小数点（即10.0），把第二个点理解成调用对象属性，从而得到正确结果。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-number">10.</span>.toString(<span class="hljs-number">2</span>)
<span class="hljs-comment">// "1010"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>// 其他方法还包括</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-number">10</span> .toString(<span class="hljs-number">2</span>) <span class="hljs-comment">// "1010"</span>
<span class="hljs-number">10.0</span>.toString(<span class="hljs-number">2</span>) <span class="hljs-comment">// "1010"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>这实际上意味着，可以直接对一个小数使用toString方法。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-number">10.5</span>.toString() <span class="hljs-comment">// "10.5"</span>
<span class="hljs-number">10.5</span>.toString(<span class="hljs-number">2</span>) <span class="hljs-comment">// "1010.1"</span>
<span class="hljs-number">10.5</span>.toString(<span class="hljs-number">8</span>) <span class="hljs-comment">// "12.4"</span>
<span class="hljs-number">10.5</span>.toString(<span class="hljs-number">16</span>) <span class="hljs-comment">// "a.8"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>通过方括号运算符也可以调用toString方法。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-number">10</span>[<span class="hljs-string">'toString'</span>](<span class="hljs-number">2</span>) <span class="hljs-comment">// "1010"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>toString方法只能将十进制的数，转为其他进制的字符串。如果要将其他进制的数，转回十进制，需要使用parseInt方法。</p>
<h3 data-id="heading-12">Number.prototype.toFixed()</h3>
<p>toFixed()方法先将一个数转为指定位数的小数，然后返回这个小数对应的字符串</p>
<pre><code class="hljs language-js copyable" lang="js">(<span class="hljs-number">10</span>).toFixed(<span class="hljs-number">2</span>) <span class="hljs-comment">// "10.00"</span>
<span class="hljs-number">10.005</span>.toFixed(<span class="hljs-number">2</span>) <span class="hljs-comment">// "10.01"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，10和10.005先转成2位小数，然后转成字符串。其中10必须放在括号里，否则后面的点会被处理成小数点。</p>
<p>toFixed()方法的参数为小数位数，有效范围为0到100，超出这个范围将抛出 RangeError 错误。</p>
<p>由于浮点数的原因，小数5的四舍五入是不确定的，使用的时候必须小心。</p>
<pre><code class="hljs language-js copyable" lang="js">(<span class="hljs-number">10.055</span>).toFixed(<span class="hljs-number">2</span>) <span class="hljs-comment">// 10.05</span>
(<span class="hljs-number">10.005</span>).toFixed(<span class="hljs-number">2</span>) <span class="hljs-comment">// 10.01</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-13">自定义方法</h2>
<p>与其他对象一样，Number.prototype对象上面可以自定义方法，被Number的实例继承。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">Number</span>.prototype.add = <span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params">x</span>) </span>&#123;
  <span class="hljs-keyword">return</span> <span class="hljs-built_in">this</span> + x;
&#125;;

<span class="hljs-number">8</span>[<span class="hljs-string">'add'</span>](<span class="hljs-number">2</span>) <span class="hljs-comment">// 10</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码为Number对象实例定义了一个add方法。在数值上调用某个方法，数值会自动转为Number的实例对象，所以就可以调用add方法了。由于add方法返回的还是数值，所以可以链式运算。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">Number</span>.prototype.subtract = <span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params">x</span>) </span>&#123;
  <span class="hljs-keyword">return</span> <span class="hljs-built_in">this</span> - x;
&#125;;

(<span class="hljs-number">8</span>).add(<span class="hljs-number">2</span>).subtract(<span class="hljs-number">4</span>)
<span class="hljs-comment">// 6</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码在Number对象的实例上部署了subtract方法，它可以与add方法链式调用。</p>
<p>注意，数值的自定义方法，只能定义在它的原型对象Number.prototype上面，数值本身是无法自定义属性的。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> n = <span class="hljs-number">1</span>;
n.x = <span class="hljs-number">1</span>;
n.x <span class="hljs-comment">// undefined</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，n是一个原始类型的数值。直接在它上面新增一个属性x，不会报错，但毫无作用，总是返回undefined。这是因为一旦被调用属性，n就自动转为Number的实例对象，调用结束后，该对象自动销毁。所以，下一次调用n的属性时，实际取到的是另一个对象，属性x当然就读不出来。</p>
<h1 data-id="heading-14">String</h1>
<blockquote>
<p>String对象是 JavaScript 原生提供的三个包装对象之一，用来生成字符串对象。</p>
</blockquote>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> s1 = <span class="hljs-string">'abc'</span>;
<span class="hljs-keyword">var</span> s2 = <span class="hljs-keyword">new</span> <span class="hljs-built_in">String</span>(<span class="hljs-string">'abc'</span>);

<span class="hljs-keyword">typeof</span> s1 <span class="hljs-comment">// "string"</span>
<span class="hljs-keyword">typeof</span> s2 <span class="hljs-comment">// "object"</span>

s2.valueOf() <span class="hljs-comment">// "abc"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，变量s1是字符串，s2是对象。由于s2是字符串对象，s2.valueOf方法返回的就是它所对应的原始字符串。</p>
<p>字符串对象是一个类似数组的对象（很像数组，但不是数组）。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">new</span> <span class="hljs-built_in">String</span>(<span class="hljs-string">'abc'</span>)
<span class="hljs-comment">// String &#123;0: "a", 1: "b", 2: "c", length: 3&#125;</span>

(<span class="hljs-keyword">new</span> <span class="hljs-built_in">String</span>(<span class="hljs-string">'abc'</span>))[<span class="hljs-number">1</span>] <span class="hljs-comment">// "b"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，字符串abc对应的字符串对象，有数值键（0、1、2）和length属性，所以可以像数组那样取值。</p>
<p>除了用作构造函数，String对象还可以当作工具方法使用，将任意类型的值转为字符串。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">String</span>(<span class="hljs-literal">true</span>) <span class="hljs-comment">// "true"</span>
<span class="hljs-built_in">String</span>(<span class="hljs-number">5</span>) <span class="hljs-comment">// "5"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码将布尔值true和数值5，分别转换为字符串。</p>
<h2 data-id="heading-15">实例属性</h2>
<h3 data-id="heading-16">String.prototype.length</h3>
<p>字符串实例的length属性返回字符串的长度。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'abc'</span>.length <span class="hljs-comment">// 3</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-17">实例方法</h2>
<h3 data-id="heading-18">String.prototype.charAt()</h3>
<p>charAt方法返回指定位置的字符，参数是从0开始编号的位置。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> s = <span class="hljs-keyword">new</span> <span class="hljs-built_in">String</span>(<span class="hljs-string">'abc'</span>);

s.charAt(<span class="hljs-number">1</span>) <span class="hljs-comment">// "b"</span>
s.charAt(s.length - <span class="hljs-number">1</span>) <span class="hljs-comment">// "c"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>这个方法完全可以用数组下标替代。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'abc'</span>.charAt(<span class="hljs-number">1</span>) <span class="hljs-comment">// "b"</span>
<span class="hljs-string">'abc'</span>[<span class="hljs-number">1</span>] <span class="hljs-comment">// "b"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>如果参数为负数，或大于等于字符串的长度，charAt返回空字符串。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'abc'</span>.charAt(-<span class="hljs-number">1</span>) <span class="hljs-comment">// ""</span>
<span class="hljs-string">'abc'</span>.charAt(<span class="hljs-number">3</span>) <span class="hljs-comment">// ""</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-19">String.prototype.concat()</h3>
<p>concat方法用于连接两个字符串，返回一个新字符串，不改变原字符串。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> s1 = <span class="hljs-string">'abc'</span>;
<span class="hljs-keyword">var</span> s2 = <span class="hljs-string">'def'</span>;

s1.concat(s2) <span class="hljs-comment">// "abcdef"</span>
s1 <span class="hljs-comment">// "abc"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>该方法可以接受多个参数。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'a'</span>.concat(<span class="hljs-string">'b'</span>, <span class="hljs-string">'c'</span>) <span class="hljs-comment">// "abc"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>如果参数不是字符串，concat方法会将其先转为字符串，然后再连接。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> one = <span class="hljs-number">1</span>;
<span class="hljs-keyword">var</span> two = <span class="hljs-number">2</span>;
<span class="hljs-keyword">var</span> three = <span class="hljs-string">'3'</span>;

<span class="hljs-string">''</span>.concat(one, two, three) <span class="hljs-comment">// "123"</span>
one + two + three <span class="hljs-comment">// "33"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，concat方法将参数先转成字符串再连接，所以返回的是一个三个字符的字符串。作为对比，加号运算符在两个运算数都是数值时，不会转换类型，所以返回的是一个两个字符的字符串。</p>
<h3 data-id="heading-20">String.prototype.slice()</h3>
<p>slice()方法用于从原字符串取出子字符串并返回，不改变原字符串。它的第一个参数是子字符串的开始位置，第二个参数是子字符串的结束位置（不含该位置）。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'JavaScript'</span>.slice(<span class="hljs-number">0</span>, <span class="hljs-number">4</span>) <span class="hljs-comment">// "Java"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>如果省略第二个参数，则表示子字符串一直到原字符串结束。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'JavaScript'</span>.slice(<span class="hljs-number">4</span>) <span class="hljs-comment">// "Script"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>如果参数是负值，表示从结尾开始倒数计算的位置，即该负值加上字符串长度。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'JavaScript'</span>.slice(-<span class="hljs-number">6</span>) <span class="hljs-comment">// "Script"</span>
<span class="hljs-string">'JavaScript'</span>.slice(<span class="hljs-number">0</span>, -<span class="hljs-number">6</span>) <span class="hljs-comment">// "Java"</span>
<span class="hljs-string">'JavaScript'</span>.slice(-<span class="hljs-number">2</span>, -<span class="hljs-number">1</span>) <span class="hljs-comment">// "p"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>如果第一个参数大于第二个参数（正数情况下），slice()方法返回一个空字符串。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'JavaScript'</span>.slice(<span class="hljs-number">2</span>, <span class="hljs-number">1</span>) <span class="hljs-comment">// ""</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-21">String.prototype.substring()</h3>
<p>substring方法用于从原字符串取出子字符串并返回，不改变原字符串，跟slice方法很相像。它的第一个参数表示子字符串的开始位置，第二个位置表示结束位置（返回结果不含该位置）。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'JavaScript'</span>.substring(<span class="hljs-number">0</span>, <span class="hljs-number">4</span>) <span class="hljs-comment">// "Java"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>如果省略第二个参数，则表示子字符串一直到原字符串的结束。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'JavaScript'</span>.substring(<span class="hljs-number">4</span>) <span class="hljs-comment">// "Script"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>如果第一个参数大于第二个参数，substring方法会自动更换两个参数的位置。<br>
上面代码中，调换substring方法的两个参数，都得到同样的结果。</p>
<p>如果参数是负数，substring方法会自动将负数转为0。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'JavaScript'</span>.substring(-<span class="hljs-number">3</span>) <span class="hljs-comment">// "JavaScript"</span>
<span class="hljs-string">'JavaScript'</span>.substring(<span class="hljs-number">4</span>, -<span class="hljs-number">3</span>) <span class="hljs-comment">// "Java"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，第二个例子的参数-3会自动变成0，等同于'JavaScript'.substring(4, 0)。由于第二个参数小于第一个参数，会自动互换位置，所以返回Java。</p>
<p>由于这些规则违反直觉，因此不建议使用substring方法，应该优先使用slice。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'JavaScript'</span>.substring(<span class="hljs-number">10</span>, <span class="hljs-number">4</span>) <span class="hljs-comment">// "Script"</span>
<span class="hljs-comment">// 等同于</span>
<span class="hljs-string">'JavaScript'</span>.substring(<span class="hljs-number">4</span>, <span class="hljs-number">10</span>) <span class="hljs-comment">// "Script"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>由于这些规则违反直觉，因此不建议使用substring方法，应该优先使用slice。</p>
<h3 data-id="heading-22">String.prototype.substr()</h3>
<p>substr方法用于从原字符串取出子字符串并返回，不改变原字符串，跟slice和substring方法的作用相同。</p>
<p>substr方法的第一个参数是子字符串的开始位置（从0开始计算），第二个参数是子字符串的长度。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'JavaScript'</span>.substr(<span class="hljs-number">4</span>, <span class="hljs-number">6</span>) <span class="hljs-comment">// "Script"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>如果省略第二个参数，则表示子字符串一直到原字符串的结束。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'JavaScript'</span>.substr(<span class="hljs-number">4</span>) <span class="hljs-comment">// "Script"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>如果第一个参数是负数，表示倒数计算的字符位置。如果第二个参数是负数，将被自动转为0，因此会返回空字符串。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'JavaScript'</span>.substr(-<span class="hljs-number">6</span>) <span class="hljs-comment">// "Script"</span>
<span class="hljs-string">'JavaScript'</span>.substr(<span class="hljs-number">4</span>, -<span class="hljs-number">1</span>) <span class="hljs-comment">// ""</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，第二个例子的参数-1自动转为0，表示子字符串长度为0，所以返回空字符串。</p>
<h3 data-id="heading-23">String.prototype.indexOf(),String.prototype.lastIndexOf()</h3>
<p>indexOf方法用于确定一个字符串在另一个字符串中第一次出现的位置，返回结果是匹配开始的位置。如果返回-1，就表示不匹配。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'hello world'</span>.indexOf(<span class="hljs-string">'o'</span>) <span class="hljs-comment">// 4</span>
<span class="hljs-string">'JavaScript'</span>.indexOf(<span class="hljs-string">'script'</span>) <span class="hljs-comment">// -1</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>indexOf方法还可以接受第二个参数，表示从该位置开始向后匹配。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'hello world'</span>.indexOf(<span class="hljs-string">'o'</span>, <span class="hljs-number">6</span>) <span class="hljs-comment">// 7</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>lastIndexOf方法的用法跟indexOf方法一致，主要的区别是lastIndexOf从尾部开始匹配，indexOf则是从头部开始匹配。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'hello world'</span>.lastIndexOf(<span class="hljs-string">'o'</span>) <span class="hljs-comment">// 7</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>另外，lastIndexOf的第二个参数表示从该位置起向前匹配。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'hello world'</span>.lastIndexOf(<span class="hljs-string">'o'</span>, <span class="hljs-number">6</span>) <span class="hljs-comment">// 4</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-24">String.prototype.trim()</h3>
<p>trim方法用于去除字符串两端的空格，返回一个新字符串，不改变原字符串。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'  hello world  '</span>.trim()
<span class="hljs-comment">// "hello world"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>该方法去除的不仅是空格，还包括制表符（\t、\v）、换行符（\n）和回车符（\r）。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'\r\nabc \t'</span>.trim() <span class="hljs-comment">// 'abc'</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-25">String.prototype.toLowerCase(),String.prototype.toUpperCase()</h3>
<p>toLowerCase方法用于将一个字符串全部转为小写，toUpperCase则是全部转为大写。它们都返回一个新字符串，不改变原字符串。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'Hello World'</span>.toLowerCase()
<span class="hljs-comment">// "hello world"</span>

<span class="hljs-string">'Hello World'</span>.toUpperCase()
<span class="hljs-comment">// "HELLO WORLD"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-26">String.prototype.match()</h3>
<p>match方法用于确定原字符串是否匹配某个子字符串，返回一个数组，成员为匹配的第一个字符串。如果没有找到匹配，则返回null。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'cat, bat, sat, fat'</span>.match(<span class="hljs-string">'at'</span>) <span class="hljs-comment">// ["at"]</span>
<span class="hljs-string">'cat, bat, sat, fat'</span>.match(<span class="hljs-string">'xt'</span>) <span class="hljs-comment">// null</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>返回的数组还有index属性和input属性，分别表示匹配字符串开始的位置和原始字符串。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> matches = <span class="hljs-string">'cat, bat, sat, fat'</span>.match(<span class="hljs-string">'at'</span>);
matches.index <span class="hljs-comment">// 1</span>
matches.input <span class="hljs-comment">// "cat, bat, sat, fat"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>match方法还可以使用正则表达式作为参数</p>
<h3 data-id="heading-27">String.prototype.search()，String.prototype.replace()</h3>
<p>search方法的用法基本等同于match，但是返回值为匹配的第一个位置。如果没有找到匹配，则返回-1。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'cat, bat, sat, fat'</span>.search(<span class="hljs-string">'at'</span>) <span class="hljs-comment">// 1</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>replace方法用于替换匹配的子字符串，一般情况下只替换第一个匹配（除非使用带有g修饰符的正则表达式）。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'aaa'</span>.replace(<span class="hljs-string">'a'</span>, <span class="hljs-string">'b'</span>) <span class="hljs-comment">// "baa"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-28">String.prototype.split()</h3>
<p>split方法按照给定规则分割字符串，返回一个由分割出来的子字符串组成的数组。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'a|b|c'</span>.split(<span class="hljs-string">'|'</span>) <span class="hljs-comment">// ["a", "b", "c"]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>如果分割规则为空字符串，则返回数组的成员是原字符串的每一个字符。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'a|b|c'</span>.split(<span class="hljs-string">''</span>) <span class="hljs-comment">// ["a", "|", "b", "|", "c"]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>如果省略参数，则返回数组的唯一成员就是原字符串。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'a|b|c'</span>.split() <span class="hljs-comment">// ["a|b|c"]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>如果满足分割规则的两个部分紧邻着（即两个分割符中间没有其他字符），则返回数组之中会有一个空字符串。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'a||c'</span>.split(<span class="hljs-string">'|'</span>) <span class="hljs-comment">// ['a', '', 'c']</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>如果满足分割规则的部分处于字符串的开头或结尾（即它的前面或后面没有其他字符），则返回数组的第一个或最后一个成员是一个空字符串。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'|b|c'</span>.split(<span class="hljs-string">'|'</span>) <span class="hljs-comment">// ["", "b", "c"]</span>
<span class="hljs-string">'a|b|'</span>.split(<span class="hljs-string">'|'</span>) <span class="hljs-comment">// ["a", "b", ""]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>split方法还可以接受第二个参数，限定返回数组的最大成员数。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'a|b|c'</span>.split(<span class="hljs-string">'|'</span>, <span class="hljs-number">0</span>) <span class="hljs-comment">// []</span>
<span class="hljs-string">'a|b|c'</span>.split(<span class="hljs-string">'|'</span>, <span class="hljs-number">1</span>) <span class="hljs-comment">// ["a"]</span>
<span class="hljs-string">'a|b|c'</span>.split(<span class="hljs-string">'|'</span>, <span class="hljs-number">2</span>) <span class="hljs-comment">// ["a", "b"]</span>
<span class="hljs-string">'a|b|c'</span>.split(<span class="hljs-string">'|'</span>, <span class="hljs-number">3</span>) <span class="hljs-comment">// ["a", "b", "c"]</span>
<span class="hljs-string">'a|b|c'</span>.split(<span class="hljs-string">'|'</span>, <span class="hljs-number">4</span>) <span class="hljs-comment">// ["a", "b", "c"]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，split方法的第二个参数，决定了返回数组的成员数。</p></div>  
</div>
            
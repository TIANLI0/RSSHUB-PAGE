
---
title: 'Object'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=324'
author: 掘金
comments: false
date: Thu, 15 Jul 2021 18:25:55 GMT
thumbnail: 'https://picsum.photos/400/300?random=324'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h1 data-id="heading-0">Object</h1>
<blockquote>
<p>在JavaScript中，几乎所有的对象都是Object的实例，它们都会从Object.prototype继承属性和方法。（<a href="https://link.juejin.cn/?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2Fdocs%2FWeb%2FJavaScript%2FReference%2FGlobal_Objects%2FObject" target="_blank" rel="nofollow noopener noreferrer" title="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object" ref="nofollow noopener noreferrer">MDN</a>定义）</p>
</blockquote>
<p>我们在控制台打印一下Object （<strong>注意Object O是大写</strong>）</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">console</span>.dir(<span class="hljs-built_in">Object</span>)  <span class="hljs-comment">// ƒ Object() </span>
<span class="hljs-keyword">typeof</span> <span class="hljs-built_in">Object</span> <span class="hljs-comment">// function</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-js copyable" lang="js">&#123;&#125;  <span class="hljs-keyword">instanceof</span> <span class="hljs-built_in">Object</span>  <span class="hljs-comment">// true</span>
[]  <span class="hljs-keyword">instanceof</span> <span class="hljs-built_in">Object</span>  <span class="hljs-comment">// true</span>
()=>&#123;&#125;  <span class="hljs-keyword">instanceof</span> <span class="hljs-built_in">Object</span> <span class="hljs-comment">// true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-1">Object()</h2>
<p>Object本身是一个函数，可以当作工具方法使用，将任意值转为对象。这个方法常用于保证某个值一定是对象。如果参数为空（或者为undefined和null），Object()返回一个空对象。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> obj = <span class="hljs-built_in">Object</span>();  <span class="hljs-comment">// &#123;&#125;</span>
<span class="hljs-comment">// 等同于</span>
<span class="hljs-keyword">var</span> obj = <span class="hljs-built_in">Object</span>(<span class="hljs-literal">undefined</span>);
<span class="hljs-keyword">var</span> obj = <span class="hljs-built_in">Object</span>(<span class="hljs-literal">null</span>);

obj <span class="hljs-keyword">instanceof</span> <span class="hljs-built_in">Object</span> <span class="hljs-comment">// true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码的含义，是将undefined和null转为对象，结果得到了一个空对象obj。</p>
<p>instanceof运算符用来验证，一个对象是否为指定的构造函数的实例。obj instanceof Object返回true，就表示obj对象是Object的实例。</p>
<p>如果参数是原始类型的值，Object方法将其转为对应的包装对象的实例。包装对象后面会介绍。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> obj = <span class="hljs-built_in">Object</span>(<span class="hljs-number">1</span>); 相当于 <span class="hljs-keyword">var</span> obj = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Number</span>(<span class="hljs-number">1</span>)
obj <span class="hljs-keyword">instanceof</span> <span class="hljs-built_in">Object</span> <span class="hljs-comment">// true</span>
obj <span class="hljs-keyword">instanceof</span> <span class="hljs-built_in">Number</span> <span class="hljs-comment">// true</span>

<span class="hljs-keyword">var</span> obj = <span class="hljs-built_in">Object</span>(<span class="hljs-string">'foo'</span>); 相当于 <span class="hljs-keyword">var</span> obj = <span class="hljs-keyword">new</span> <span class="hljs-built_in">String</span>(<span class="hljs-number">1</span>)
obj <span class="hljs-keyword">instanceof</span> <span class="hljs-built_in">Object</span> <span class="hljs-comment">// true</span>
obj <span class="hljs-keyword">instanceof</span> <span class="hljs-built_in">String</span> <span class="hljs-comment">// true</span>

<span class="hljs-keyword">var</span> obj = <span class="hljs-built_in">Object</span>(<span class="hljs-literal">true</span>); 相当于 <span class="hljs-keyword">var</span> obj = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Boolean</span>(<span class="hljs-number">1</span>)
obj <span class="hljs-keyword">instanceof</span> <span class="hljs-built_in">Object</span> <span class="hljs-comment">// true</span>
obj <span class="hljs-keyword">instanceof</span> <span class="hljs-built_in">Boolean</span> <span class="hljs-comment">// true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，Object函数的参数是各种原始类型的值，转换成对象就是原始类型值对应的包装对象。</p>
<p>如果Object方法的参数是一个对象，它总是返回该对象，即不用转换。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> arr = [];
<span class="hljs-keyword">var</span> obj = <span class="hljs-built_in">Object</span>(arr); <span class="hljs-comment">// 返回原数组</span>
obj === arr <span class="hljs-comment">// true</span>

<span class="hljs-keyword">var</span> value = &#123;&#125;;
<span class="hljs-keyword">var</span> obj = <span class="hljs-built_in">Object</span>(value) <span class="hljs-comment">// 返回原对象</span>
obj === value <span class="hljs-comment">// true</span>

<span class="hljs-keyword">var</span> fn = <span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params"></span>) </span>&#123;&#125;;
<span class="hljs-keyword">var</span> obj = <span class="hljs-built_in">Object</span>(fn); <span class="hljs-comment">// 返回原函数</span>
obj === fn <span class="hljs-comment">// true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>利用这一点，可以写一个判断变量是否为对象的函数。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">isObject</span>(<span class="hljs-params">value</span>) </span>&#123;
  <span class="hljs-keyword">return</span> value === <span class="hljs-built_in">Object</span>(value);
&#125;

isObject([]) <span class="hljs-comment">// true</span>
isObject(<span class="hljs-literal">true</span>) <span class="hljs-comment">// false</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>Object()总结：</p>
<ul>
<li>如果参数为 null 或 undefined或空字符串，将会创建并返回一个空对象</li>
<li>如果传进去的是一个基本类型的值，则会构造其包装类型的对象</li>
<li>如果传进去的是引用类型的值，仍然会返回这个值，返回的值和传进去的值有相同的引用地址</li>
</ul>
<h2 data-id="heading-2">Object 构造函数</h2>
<p>Object不仅可以当作工具函数使用，还可以当作构造函数使用，即前面可以使用new命令。
Object构造函数的首要用途，是直接通过它来生成新对象。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> obj = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Object</span>();
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p>注意，通过var obj = new Object()的写法生成新对象，与字面量的写法var obj = &#123;&#125;是等价的。或者说，后者只是前者的一种简便写法。</p>
</blockquote>
<p>Object构造函数的用法与工具方法可以说是一模一样。使用时，可以接受一个参数，如果该参数是一个对象，则直接返回这个对象；如果是一个原始类型的值，则返回该值对应的包装对象</p>
<p>以下为<a href="https://link.juejin.cn/?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2Fdocs%2FWeb%2FJavaScript%2FReference%2FGlobal_Objects%2FObject" target="_blank" rel="nofollow noopener noreferrer" title="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object" ref="nofollow noopener noreferrer">MDN</a>上的原话</p>
<blockquote>
<p>当以非构造函数形式被调用时，Object 的行为等同于 new Object()。</p>
</blockquote>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> o1 = &#123;<span class="hljs-attr">a</span>: <span class="hljs-number">1</span>&#125;;
<span class="hljs-keyword">var</span> o2 = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Object</span>(o1);
o1 === o2 <span class="hljs-comment">// true</span>

<span class="hljs-keyword">var</span> obj = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Object</span>(<span class="hljs-number">123</span>);
obj <span class="hljs-keyword">instanceof</span> <span class="hljs-built_in">Number</span> <span class="hljs-comment">// true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-3">Object 的静态方法</h2>
<p>所谓“静态方法”，是指部署在Object对象自身的方法。（只介绍常用）</p>
<h2 data-id="heading-4">Object.keys()</h2>
<blockquote>
<p>Object.keys方法用来遍历对象的属性。参数是一个对象，返回一个数组。该数组的成员都是该对象自身的（而不是继承的）所有属性名。<strong>Object.keys方法只返回可枚举的属性</strong></p>
</blockquote>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> obj = &#123;
  <span class="hljs-attr">p1</span>: <span class="hljs-number">123</span>,
  <span class="hljs-attr">p2</span>: <span class="hljs-number">456</span>
&#125;;

<span class="hljs-built_in">Object</span>.keys(obj) <span class="hljs-comment">// ["p1", "p2"]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>想得到值 而不是属性名可以用 Object.values() 这个方法</p>
<p>Object.assign()</p>
<blockquote>
<p>介绍<a href="https://juejin.cn/post/6981272992923795486" target="_blank" title="https://juejin.cn/post/6981272992923795486">浅拷贝</a>中已经讲过</p>
</blockquote>
<p>Object.freeze()</p>
<blockquote>
<p>表示冻结一个对象，一个被冻结的对象再也不能被修改；冻结了一个对象则不能向这个对象添加新的属性，不能删除已有属性，不能修改该对象已有属性的可枚举性、可配置性、可写性，以及不能修改已有属性的值。此外，冻结一个对象后该对象的原型也不能被修改。</p>
</blockquote>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">const</span> obj = &#123;
  <span class="hljs-attr">prop</span>: <span class="hljs-number">42</span>
&#125;;

<span class="hljs-built_in">Object</span>.freeze(obj);

obj.prop = <span class="hljs-number">33</span>; <span class="hljs-comment">// Throws an error </span>

<span class="hljs-built_in">console</span>.log(obj.prop); <span class="hljs-comment">// 42</span>

<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-5">Object.getPrototypeOf()</h2>
<blockquote>
<p>获取对象的原型(Prototype)对象。</p>
</blockquote>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> obj = &#123;&#125;
<span class="hljs-built_in">Object</span>.getPrototypeOf(obj) === obj.__proto__
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-6">Object 的实例方法</h2>
<p>除了静态方法，还有不少方法定义在Object.prototype对象。它们称为实例方法，所有Object的实例对象都继承了这些方法。</p>
<p>Object实例对象的方法，这里只介绍下面三个</p>
<ul>
<li>Object.prototype.valueOf()：返回当前对象对应的值。</li>
<li>Object.prototype.toString()：返回当前对象对应的字符串形式。</li>
<li>Object.prototype.hasOwnProperty()：判断某个属性是否为当前对象自身的属性，还是继承自原型对象的属性。</li>
</ul>
<h2 data-id="heading-7">Object.prototype.valueOf()</h2>
<p>valueOf方法的作用是返回一个对象的“值”，默认情况下返回对象本身。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> obj = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Object</span>();
obj.valueOf() === obj <span class="hljs-comment">// true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>除了下面的例子，可以认为valueOf，都是返回对象的本身。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> obj = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Boolean</span>(<span class="hljs-literal">false</span>);
obj.valueOf()  <span class="hljs-comment">// false</span>
注意，obj为<span class="hljs-literal">true</span>，obj是一个对象。
<span class="copy-code-btn">复制代码</span></code></pre>
<p>valueOf方法的主要用途是，JavaScript 自动类型转换时会默认调用这个方法</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> obj = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Object</span>();
<span class="hljs-number">1</span> + obj <span class="hljs-comment">// "1[object Object]"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码将对象obj与数字1相加，这时 JavaScript 就会默认调用valueOf()方法，求出obj的值再与1相加。所以，如果自定义valueOf方法，就可以得到想要的结果。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> obj = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Object</span>();
obj.valueOf = <span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params"></span>) </span>&#123;
  <span class="hljs-keyword">return</span> <span class="hljs-number">2</span>;
&#125;;

<span class="hljs-number">1</span> + obj <span class="hljs-comment">// 3</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码自定义了obj对象的valueOf方法，于是1 + obj就得到了3。这种方法就相当于用自定义的obj.valueOf，覆盖Object.prototype.valueOf。</p>
<h2 data-id="heading-8">Object.prototype.toString()</h2>
<p>toString方法的作用是返回一个对象的字符串形式，默认情况下返回类型字符串。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> o1 = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Object</span>();
o1.toString() <span class="hljs-comment">// "[object Object]"</span>

<span class="hljs-keyword">var</span> o2 = &#123;<span class="hljs-attr">a</span>:<span class="hljs-number">1</span>&#125;;
o2.toString() <span class="hljs-comment">// "[object Object]"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码表示，对于一个对象调用toString方法，会返回字符串[object Object]，该字符串说明对象的类型。</p>
<p>字符串[object Object]本身没有太大的用处，但是通过自定义toString方法，可以让对象在自动类型转换时，得到想要的字符串形式。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> obj = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Object</span>();

obj.toString = <span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params"></span>) </span>&#123;
  <span class="hljs-keyword">return</span> <span class="hljs-string">'hello'</span>;
&#125;;

obj + <span class="hljs-string">' '</span> + <span class="hljs-string">'world'</span> <span class="hljs-comment">// "hello world"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码表示，当对象用于字符串加法时，会自动调用toString方法。由于自定义了toString方法，所以返回字符串hello world。</p>
<p>数组、字符串、函数、Date 对象都分别部署了自定义的toString方法，覆盖了Object.prototype.toString方法。</p>
<pre><code class="hljs language-js copyable" lang="js">[<span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>].toString() <span class="hljs-comment">// "1,2,3"</span>

<span class="hljs-string">'123'</span>.toString() <span class="hljs-comment">// "123"</span>

(<span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params"></span>) </span>&#123;
  <span class="hljs-keyword">return</span> <span class="hljs-number">123</span>;
&#125;).toString()
<span class="hljs-comment">// "function () &#123;</span>
<span class="hljs-comment">//   return 123;</span>
<span class="hljs-comment">// &#125;"</span>

(<span class="hljs-keyword">new</span> <span class="hljs-built_in">Date</span>()).toString()
<span class="hljs-comment">// "Tue May 10 2016 09:11:31 GMT+0800 (CST)"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，数组、字符串、函数、Date 对象调用toString方法，并不会返回[object Object]，因为它们都自定义了toString方法，覆盖原始方法。</p>
<h3 data-id="heading-9">toString() 的应用：判断数据类型</h3>
<p>Object.prototype.toString方法返回对象的类型字符串，因此可以用来判断一个值的类型。</p>
<p>由于实例对象可能会自定义toString方法，覆盖掉Object.prototype.toString方法，所以为了得到类型字符串，最好直接使用Object.prototype.toString方法。通过函数的call方法，可以在任意值上调用这个方法，帮助我们判断这个值的类型。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">Object</span>.prototype.toString.call(value)
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码表示对value这个值调用Object.prototype.toString方法。</p>
<p>不同数据类型的Object.prototype.toString方法返回值如下。</p>
<ul>
<li>数值：返回[object Number]。</li>
<li>字符串：返回[object String]。</li>
<li>布尔值：返回[object Boolean]。</li>
<li>undefined：返回[object Undefined]。</li>
<li>null：返回[object Null]。</li>
<li>数组：返回[object Array]。</li>
<li>arguments 对象：返回[object Arguments]。</li>
<li>函数：返回[object Function]。</li>
<li>Error 对象：返回[object Error]。</li>
<li>Date 对象：返回[object Date]。</li>
<li>RegExp 对象：返回[object RegExp]。</li>
<li>其他对象：返回[object Object]。</li>
</ul>
<p>这就是说，Object.prototype.toString可以看出一个值到底是什么类型。</p>
<h2 data-id="heading-10">Object.prototype.hasOwnProperty()</h2>
<p>Object.prototype.hasOwnProperty方法接受一个字符串作为参数，返回一个布尔值，<strong>表示该实例对象自身是否具有该属性。</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> obj = &#123;
  <span class="hljs-attr">p</span>: <span class="hljs-number">123</span>
&#125;;

obj.hasOwnProperty(<span class="hljs-string">'p'</span>) <span class="hljs-comment">// true</span>
obj.hasOwnProperty(<span class="hljs-string">'toString'</span>) <span class="hljs-comment">// false</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上面代码中，对象obj自身具有p属性，所以返回true。toString属性是继承的，所以返回false。</p></div>  
</div>
            

---
title: 'ES6 数组'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=9450'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 02:30:16 GMT
thumbnail: 'https://picsum.photos/400/300?random=9450'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h3 data-id="heading-0">1.数组声明</h3>
<h4 data-id="heading-1">（1）创建数组</h4>
<p>使用对象方式创建数组</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">new</span> <span class="hljs-built_in">Array</span>(<span class="hljs-number">1</span>, <span class="hljs-string">''</span>huihui);
<span class="copy-code-btn">复制代码</span></code></pre>
<p>使用字面量创建数组</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">const</span> array = [<span class="hljs-number">1</span>, <span class="hljs-string">'huihui];
</span><span class="copy-code-btn">复制代码</span></code></pre>
<p>数组是引用类型可以使用const声明并修改它的值</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">const</span> array = [<span class="hljs-number">1</span>, <span class="hljs-string">'huihui'</span>];
array.push(<span class="hljs-string">'cute'</span>);
<span class="copy-code-btn">复制代码</span></code></pre>
<p>使用原型的length属性可以获取数组元素数量</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">const</span> array = [<span class="hljs-number">1</span>, <span class="hljs-string">'huihui'</span>];
<span class="hljs-built_in">console</span>.log(array.length)
<span class="copy-code-btn">复制代码</span></code></pre>
<p>数组可以设置任何值，下面是使用索引添加数组</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = [<span class="hljs-string">'huihui'</span>];
arr[<span class="hljs-number">1</span>] = <span class="hljs-number">18</span>;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>下面是直接设置3号数组，会将1/2索引的数组定义为undefined</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = [<span class="hljs-string">'huihui'</span>];
arr[<span class="hljs-number">3</span>] = <span class="hljs-number">19</span>;
<span class="hljs-built_in">console</span>.log(a[<span class="hljs-number">1</span>])    <span class="hljs-comment">// undefined</span>
<span class="hljs-built_in">console</span>.log(a[<span class="hljs-number">2</span>])    <span class="hljs-comment">// undefined</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>声明多个空元素的数组</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Array</span>(<span class="hljs-number">3</span>);
<span class="hljs-built_in">console</span>.log(arr.length)    <span class="hljs-comment">// 3</span>
<span class="hljs-built_in">console</span>.log(arr)    <span class="hljs-comment">// [empty × 3]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-2">（2）Array.of</h4>
<p>使用Array.of 与 new Array 不同的是设置一个参数时不会创建一个空元素的数组</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = <span class="hljs-built_in">Array</span>.of(<span class="hljs-number">3</span>);
<span class="hljs-built_in">console</span>.log(arr)    <span class="hljs-comment">// [3]</span>

arr = <span class="hljs-built_in">Array</span>.of(<span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>);
<span class="hljs-built_in">console</span>.log(arr);    <span class="hljs-comment">// [1, 2, 3]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-3">（3）类型检测</h4>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">console</span>.log(<span class="hljs-built_in">Array</span>.isArray([<span class="hljs-string">'huihui'</span>, <span class="hljs-number">18</span>]));    <span class="hljs-comment">// true</span>
<span class="hljs-built_in">console</span>.log(<span class="hljs-built_in">Array</span>.isArray(<span class="hljs-number">9</span>))    <span class="hljs-comment">// false</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-4">2.类型转换</h3>
<p>可以将数组转换为字符串 也可以将其他类型转换为数组</p>
<h4 data-id="heading-5">（1）字符串</h4>
<p>使用.toString()将数组转换为字符转</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">console</span>.log(([<span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>]).toString());    <span class="hljs-comment">// 1,2,3</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>使用函数String转换为字符串</p>
<pre><code class="hljs language-jsn copyable" lang="jsn">console.log(String([1, 2, 3]))
<span class="copy-code-btn">复制代码</span></code></pre>
<p>使用join连接字符串</p>
<pre><code class="hljs language-js copyable" lang="js">consoe.log([<span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>].join(<span class="hljs-string">'-'</span>))    <span class="hljs-comment">// 1-2-3</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-6">（2）Array.from</h4>
<p>使用Array.from可将类数组转化为数组
<strong>类数组指包含length属性或可迭代的对象</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> str = <span class="hljs-string">'张小慧'</span>;
<span class="hljs-built_in">console</span>.log(<span class="hljs-built_in">Array</span>.from(str))    <span class="hljs-comment">// ["张", "小", "慧"]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>为对象设置length属性后也可以转化为数组，但要下标为数值或数值字符串</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> str = &#123;
  <span class="hljs-number">0</span>: <span class="hljs-string">'zxh'</span>,
  <span class="hljs-string">'1'</span>: <span class="hljs-number">18</span>,
  <span class="hljs-attr">length</span>: <span class="hljs-number">2</span>
&#125;;
<span class="hljs-built_in">console</span>.log(<span class="hljs-built_in">Array</span>.from(str)); <span class="hljs-comment">//["zxh", 18]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-7">3.展开语法</h3>
<h4 data-id="heading-8">（1）数组合并</h4>
<p>使用展开语法合来合并数组要比concat更加简单，使用...可将数组展开为多个值</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> a = [<span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>];
<span class="hljs-keyword">let</span> b = [<span class="hljs-string">'a'</span>, ...a];
<span class="hljs-built_in">console</span>.log(b)    <span class="hljs-comment">// ['a', 1, 2, 3]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-9">（2）函数参数</h4>
<p>使用展开语法可替代arguments来接收任意数量的参数。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> <span class="hljs-function"><span class="hljs-title">hd</span>(<span class="hljs-params">...args</span>)</span>&#123;
    <span class="hljs-built_in">console</span>.log(args);
&#125;
hd(<span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>);    <span class="hljs-comment">// [1, 2, 3]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>使用展开语法也可用于接收部分参数</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> <span class="hljs-function"><span class="hljs-title">hd</span>(<span class="hljs-params">name, ...args</span>)</span>&#123;
    <span class="hljs-built_in">console</span>.log(args);
&#125;
hd(<span class="hljs-string">"huihui"</span>, <span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>);    <span class="hljs-comment">// [1, 2, 3]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-10">4.解构赋值</h3>
<p>解构是一种更简单的赋值特性，可以理解为分解一个数据的结构</p>
<h4 data-id="heading-11">（1）基本使用</h4>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> [name, age] = [<span class="hljs-string">'huihui'</span>, <span class="hljs-number">19</span>];
<span class="hljs-built_in">console</span>.log(name, age)    <span class="hljs-comment">// huihui 19</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>结构赋值数组</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">test</span>(<span class="hljs-params"></span>) </span>&#123;
    <span class="hljs-keyword">return</span> [<span class="hljs-string">'huihui'</span>, <span class="hljs-number">19</span>]
&#125;
<span class="hljs-keyword">let</span> [name, age] = test();
<span class="hljs-built_in">console</span>.log(name, age)    <span class="hljs-comment">// huihui 19</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>剩余解构指用一个变量来接收剩余参数</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> [a, ...b] = [<span class="hljs-string">'test'</span>, <span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>, <span class="hljs-number">4</span>];
<span class="hljs-built_in">console</span>.log(b)    <span class="hljs-comment">// [1, 2, 3, 4]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>字符串解构</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">const</span> [...test] = <span class="hljs-string">'zhangxiaohui'</span>;
<span class="hljs-built_in">console</span>.log(test);    <span class="hljs-comment">// ["z", "h", "a", "n", "g", "x", "i", "a", "o", "h", "u", "i"]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-12">（2）简洁定义</h4>
<p>只赋值部分变量</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> [, age] = [<span class="hljs-string">'huihui'</span>, <span class="hljs-number">18</span>];
<span class="hljs-built_in">console</span>.log(age)    <span class="hljs-comment">// 18</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>使用展开语法获取多个值</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> [name, ...arr] = [<span class="hljs-string">'huihui'</span>, <span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>, <span class="hljs-number">4</span>, <span class="hljs-number">5</span>];
<span class="hljs-built_in">console</span>.log(name);    <span class="hljs-comment">// huihui</span>
<span class="hljs-built_in">console</span>.log(arr);    <span class="hljs-comment">// [1, 2, 3, 4, 5]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-13">（3）默认值</h4>
<p>为变量设置默认值</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> [name, age = <span class="hljs-number">18</span>] = [<span class="hljs-string">'huihui'</span>];
<span class="hljs-built_in">console</span>.log(age);    <span class="hljs-comment">// 18</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-14">（4）函数参数</h4>
<p>函数参数的使用</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">test</span>(<span class="hljs-params">[a, b]</span>) </span>&#123;
    <span class="hljs-built_in">console</span>.log(a, b)
&#125;
test([<span class="hljs-string">'huihui'</span>, <span class="hljs-number">18</span>])
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-15">5.管理元素</h3>
<h4 data-id="heading-16">（1）基本使用</h4>
<h5 data-id="heading-17">push</h5>
<p>压入元素，直接改变原数组，返回值为数组元素的数量</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> test = [<span class="hljs-number">1</span>];
test.push(<span class="hljs-number">2</span>);
<span class="hljs-built_in">console</span>.log(test)    <span class="hljs-comment">// [1, 2]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> test = [&#123;<span class="hljs-attr">name</span>: <span class="hljs-string">'huihui'</span>&#125;];
test.push(&#123;<span class="hljs-attr">name</span>: <span class="hljs-string">'dudu'</span>&#125;);
<span class="hljs-built_in">console</span>.log(test);    <span class="hljs-comment">// [&#123;name: 'huihui'&#125;, &#123;name: 'dudu'&#125;]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-18">pop</h5>
<p>从末尾弹出元素，直接改变原数组，返回值是弹出的元素</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> test = [<span class="hljs-number">1</span>, <span class="hljs-number">2</span>];
<span class="hljs-built_in">console</span>.log(test.pop())    <span class="hljs-comment">// 2</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> test = [&#123;<span class="hljs-attr">name</span>: <span class="hljs-string">'huihui'</span>&#125;]; 
<span class="hljs-built_in">console</span>.log(test.pop());    <span class="hljs-comment">// ['huihui']</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-19">shift</h5>
<p>从数组前面取出一个元素</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> test = [<span class="hljs-string">'huihui'</span>, <span class="hljs-number">19</span>];
<span class="hljs-built_in">console</span>.log(test.shift())    <span class="hljs-comment">// 'huihui'</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> test = [&#123;<span class="hljs-attr">name</span>: <span class="hljs-string">'huihui'</span>&#125;]; 
<span class="hljs-built_in">console</span>.log(test.shift());    <span class="hljs-comment">// &#123;name: "huihui"&#125;</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-20">unshift</h5>
<p>从数组前面添加元素</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> test = [<span class="hljs-number">2</span>, <span class="hljs-number">3</span>];
<span class="hljs-built_in">console</span>.log(test.unshift(<span class="hljs-number">0</span>, <span class="hljs-number">1</span>))    <span class="hljs-comment">// 4</span>
<span class="hljs-built_in">console</span>.log(test)    <span class="hljs-comment">// [0, 1, 2, 3]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> test = [&#123;<span class="hljs-attr">name</span>: <span class="hljs-string">'huihui'</span>&#125;];
test.unshift(&#123;<span class="hljs-attr">name</span>: <span class="hljs-string">'dudu'</span>&#125;);
<span class="hljs-built_in">console</span>.log(test);    <span class="hljs-comment">//[&#123;name: "dudu"&#125;, &#123;name: "huihui"&#125;]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-21">fill</h5>
<p>使用fill数组填充元素</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">console</span>.dir(<span class="hljs-built_in">Array</span>(<span class="hljs-number">4</span>).fill(<span class="hljs-string">"huihui"</span>)); <span class="hljs-comment">//["huihui", "huihui", "huihui", "huihui"]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>指定填充位置</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">console</span>.log([<span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>, <span class="hljs-number">4</span>].fill(<span class="hljs-string">"huihui"</span>, <span class="hljs-number">1</span>, <span class="hljs-number">2</span>)); <span class="hljs-comment">//[1, "huihui", 3, 4]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-22">slice</h5>
<p>使用slice方法从数组中截取部分元素<strong>注意是截取，这里只能取到截取的元素，并不会改变原数组</strong>不传第二个参数时截取到数组最后的元素。</p>
<p><code>arr.slice(start, end)    // 表示从从start位置开始截取，从end-1个位置结束截取</code></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = [<span class="hljs-number">0</span>, <span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>, <span class="hljs-number">4</span>, <span class="hljs-number">5</span>, <span class="hljs-number">6</span>];
<span class="hljs-built_in">console</span>.log(arr.slice(<span class="hljs-number">1</span>, <span class="hljs-number">3</span>)); <span class="hljs-comment">// [1,2]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>不设置参数是获取所有元素</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = [<span class="hljs-number">0</span>, <span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>, <span class="hljs-number">4</span>, <span class="hljs-number">5</span>, <span class="hljs-number">6</span>];
<span class="hljs-built_in">console</span>.log(arr.slice()); <span class="hljs-comment">//[0, 1, 2, 3, 4, 5, 6]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-23">splice</h5>
<p>使用splice方法可以添加、删除、替换数组中的元素，会对原数组进行改变，返回值为删除的数量</p>
<p><code>删除数组元素的第一个参数为从哪开始删除，第二个参数为删除的数量，第三个参数为在删除位置添加的元素</code></p>
<p>删除</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = [<span class="hljs-number">0</span>, <span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>, <span class="hljs-number">4</span>, <span class="hljs-number">5</span>, <span class="hljs-number">6</span>];
<span class="hljs-built_in">console</span>.log(arr.splice(<span class="hljs-number">1</span>, <span class="hljs-number">3</span>)); <span class="hljs-comment">//返回删除的元素 [1, 2, 3] </span>
<span class="hljs-built_in">console</span>.log(arr); <span class="hljs-comment">//删除数据后的原数组 [0, 4, 5, 6]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>添加/替换</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = [<span class="hljs-number">0</span>, <span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>, <span class="hljs-number">4</span>, <span class="hljs-number">5</span>, <span class="hljs-number">6</span>];
<span class="hljs-built_in">console</span>.log(arr.splice(<span class="hljs-number">1</span>, <span class="hljs-number">3</span>, <span class="hljs-string">'huihui'</span>, <span class="hljs-string">'19'</span>)); <span class="hljs-comment">//[1, 2, 3]</span>
<span class="hljs-built_in">console</span>.log(arr); <span class="hljs-comment">//[0, "huihui", "19", 4, 5, 6]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-24">（2）合并拆分</h4>
<h5 data-id="heading-25">join</h5>
<p>使用join连接成字符串</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = [<span class="hljs-string">'huihui'</span>, <span class="hljs-number">19</span>];
<span class="hljs-built_in">console</span>.log(arr.join(<span class="hljs-string">'-'</span>))    <span class="hljs-comment">// "huihui-19"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-26">split</h5>
<p>使用split 方法用于将字符串分割成数组，类似join 方法的反函数</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> str = <span class="hljs-string">'huihui-19'</span>;
<span class="hljs-built_in">console</span>.log(str.split(<span class="hljs-string">"-"</span>))    <span class="hljs-comment">// ["huihui", "19"]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-27">concat</h5>
<p>concat 方法用于连接两个或多个数组，元素是值类型的是复制操作，如果是引用类型还是指向同一对象</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> array = [<span class="hljs-string">"huihui"</span>,  <span class="hljs-number">18</span>];
<span class="hljs-keyword">let</span> array1 = [<span class="hljs-number">1</span>, <span class="hljs-number">2</span>];
<span class="hljs-keyword">let</span> array2 = [<span class="hljs-number">3</span>, <span class="hljs-number">4</span>];
<span class="hljs-built_in">console</span>.log(array.concat(array1, array2));    <span class="hljs-comment">// ["huihui", 18, 1, 2, 3, 4]=</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>也可以使用扩展语法实现连接</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-built_in">console</span>.log([...array, ...array1, ...array2])
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-28">copyWithin</h5>
<p>使用copyWithin从数组中复制一部分到同数组中的另外位置</p>
<h4 data-id="heading-29">（3）查找元素</h4>
<h5 data-id="heading-30">indexOf</h5>
<p>使用indexOf从前向后查找元素出现的位置，如果找不到返回-1</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = [<span class="hljs-number">7</span>, <span class="hljs-number">3</span>, <span class="hljs-number">2</span>, <span class="hljs-number">8</span>, <span class="hljs-number">2</span>, <span class="hljs-number">6</span>];
<span class="hljs-built_in">console</span>.log(arr.indexOf(<span class="hljs-number">2</span>)); <span class="hljs-comment">// 2 从前面查找2出现的位置</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><strong>注意: indexOf 是 === 严格类型约束</strong></p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = [<span class="hljs-number">7</span>, <span class="hljs-number">3</span>, <span class="hljs-number">2</span>, <span class="hljs-string">'8'</span>, <span class="hljs-number">2</span>, <span class="hljs-number">6</span>];
<span class="hljs-built_in">console</span>.log(arr.indexOf(<span class="hljs-number">8</span>)); <span class="hljs-comment">// -1</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>第二个参数用于指定查找开始位置</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = [<span class="hljs-number">7</span>, <span class="hljs-number">3</span>, <span class="hljs-number">2</span>, <span class="hljs-number">8</span>, <span class="hljs-number">2</span>, <span class="hljs-number">6</span>];
<span class="hljs-comment">//从第二个元素开始向后查找</span>
<span class="hljs-built_in">console</span>.log(arr.indexOf(<span class="hljs-number">2</span>, <span class="hljs-number">3</span>)); <span class="hljs-comment">//4</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-31">lastIndexOf</h5>
<p>从后向前找元素出现的位置，如果找不到返回-1</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = [<span class="hljs-number">7</span>, <span class="hljs-number">3</span>, <span class="hljs-number">2</span>, <span class="hljs-number">8</span>, <span class="hljs-number">2</span>, <span class="hljs-number">6</span>];
<span class="hljs-built_in">console</span>.log(arr.lastIndexOf(<span class="hljs-number">2</span>)); <span class="hljs-comment">// 4 从后查找2出现的位置</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>第二个参数用于指定查找的位置</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = [<span class="hljs-number">7</span>, <span class="hljs-number">3</span>, <span class="hljs-number">2</span>, <span class="hljs-number">8</span>, <span class="hljs-number">2</span>, <span class="hljs-number">6</span>];
<span class="hljs-comment">//从第五个元素向前查找</span>
<span class="hljs-built_in">console</span>.log(arr.lastIndexOf(<span class="hljs-number">2</span>, <span class="hljs-number">5</span>));

<span class="hljs-comment">//从最后一个字符向前查找</span>
<span class="hljs-built_in">console</span>.log(arr.lastIndexOf(<span class="hljs-number">2</span>, -<span class="hljs-number">2</span>));
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-32">includes</h5>
<p>使用includes查找字符串返回值是布尔值</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = [<span class="hljs-number">7</span>, <span class="hljs-number">3</span>, <span class="hljs-number">2</span>, <span class="hljs-number">6</span>];
<span class="hljs-built_in">console</span>.log(arr.includes(<span class="hljs-number">6</span>)); <span class="hljs-comment">//true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>includes 函数实现原理</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">includes</span>(<span class="hljs-params">array, item</span>) </span>&#123;
  <span class="hljs-keyword">for</span> (<span class="hljs-keyword">const</span> value <span class="hljs-keyword">of</span> array)
    <span class="hljs-keyword">if</span> (item === value) <span class="hljs-keyword">return</span> <span class="hljs-literal">true</span>;
    <span class="hljs-comment">// 注意这里是跳出for 循环返回false</span>
  <span class="hljs-keyword">return</span> <span class="hljs-literal">false</span>;
&#125;

<span class="hljs-built_in">console</span>.log(includes([<span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>, <span class="hljs-number">4</span>], <span class="hljs-number">3</span>)); <span class="hljs-comment">//true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-33">find</h5>
<p>find 方法找到后会把值返回 如果找不到返回值为undefined. 注意: 返回第一次查找的值，不再继续查找。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = [<span class="hljs-string">"huihui"</span>, <span class="hljs-string">"eva"</span>, <span class="hljs-string">"luna"</span>];

<span class="hljs-keyword">let</span> find = arr.find(<span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params">item</span>) </span>&#123;
  <span class="hljs-keyword">return</span> item == <span class="hljs-string">"huihui"</span>;
&#125;);

<span class="hljs-built_in">console</span>.log(find); <span class="hljs-comment">//huihui</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>使用includes 不能查找引用类型，因为它们的内存地址是不相等的。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">const</span> user = [&#123; <span class="hljs-attr">name</span>: <span class="hljs-string">"李四"</span> &#125;, &#123; <span class="hljs-attr">name</span>: <span class="hljs-string">"张三"</span> &#125;, &#123; <span class="hljs-attr">name</span>: <span class="hljs-string">"huihui"</span> &#125;];
<span class="hljs-keyword">const</span> find = user.includes(&#123; <span class="hljs-attr">name</span>: <span class="hljs-string">"huihui"</span> &#125;);
<span class="hljs-built_in">console</span>.log(find);
<span class="copy-code-btn">复制代码</span></code></pre>
<p>find可以方便的查找引用类型</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">const</span> user = [&#123; <span class="hljs-attr">name</span>: <span class="hljs-string">"李四"</span> &#125;, &#123; <span class="hljs-attr">name</span>: <span class="hljs-string">"张三"</span> &#125;, &#123; <span class="hljs-attr">name</span>: <span class="hljs-string">"huihui"</span> &#125;];
<span class="hljs-keyword">const</span> find = user.find(<span class="hljs-function"><span class="hljs-params">user</span> =></span> (user.name = <span class="hljs-string">"huihui"</span>));
<span class="hljs-built_in">console</span>.log(find);
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-34">findIndex</h5>
<p>findIndex 与 find 的区别是返回索引值，查找不到时返回-1</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = [<span class="hljs-number">7</span>, <span class="hljs-number">3</span>, <span class="hljs-number">2</span>, <span class="hljs-string">'8'</span>, <span class="hljs-number">2</span>, <span class="hljs-number">6</span>];

<span class="hljs-built_in">console</span>.log(arr.findIndex(<span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params">v</span>) </span>&#123;
<span class="hljs-keyword">return</span> v == <span class="hljs-number">8</span>;
&#125;)); <span class="hljs-comment">//3</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-35">find原理</h5>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = [<span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>, <span class="hljs-number">4</span>, <span class="hljs-number">5</span>];
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">find</span>(<span class="hljs-params">array, callback</span>) </span>&#123;
  <span class="hljs-built_in">console</span>.log(<span class="hljs-string">'callback'</span>, callback)
  <span class="hljs-keyword">for</span>(<span class="hljs-keyword">const</span> value <span class="hljs-keyword">of</span> array) &#123;
    <span class="hljs-keyword">if</span>(callback(value) === <span class="hljs-literal">true</span>) <span class="hljs-keyword">return</span> value
  &#125;
  <span class="hljs-keyword">return</span> <span class="hljs-literal">undefined</span>
&#125;
<span class="hljs-keyword">let</span> res = find(arr, <span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params">item</span>) </span>&#123;
  <span class="hljs-keyword">return</span> item == <span class="hljs-number">5</span>
&#125;);
<span class="hljs-built_in">console</span>.log(res)
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-36">（4）数组排序</h4>
<h5 data-id="heading-37">reverse</h5>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = [<span class="hljs-number">1</span>, <span class="hljs-number">4</span>, <span class="hljs-number">2</span>, <span class="hljs-number">9</span>];
<span class="hljs-built_in">console</span>.log(arr.reverse()); <span class="hljs-comment">//[9, 2, 4, 1]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-38">sort</h5>
<p>使用排序函数从大到小排序，参数一与参数二比较，返回正数为降序负数为升序</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> arr = [<span class="hljs-number">1</span>, <span class="hljs-number">4</span>, <span class="hljs-number">2</span>, <span class="hljs-number">9</span>];

<span class="hljs-built_in">console</span>.log(arr.sort(<span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params">v1, v2</span>) </span>&#123;
<span class="hljs-keyword">return</span> v2 - v1;
&#125;)); <span class="hljs-comment">//[9, 4, 2, 1]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-39">排序原理</h5>
<p>快速排序</p>
<h4 data-id="heading-40">（5）循环遍历</h4>
<h5 data-id="heading-41">for</h5>
<h5 data-id="heading-42">forEach</h5>
<p>forEach使函数作用在每个数组元素上，但是没有返回值
forEach不可以return</p>
<h5 data-id="heading-43">for/in</h5>
<p>遍历时的key值为数组的索引</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> lessons = [
  &#123;<span class="hljs-attr">title</span>: <span class="hljs-string">'媒体查询响应式布局'</span>,<span class="hljs-attr">category</span>: <span class="hljs-string">'css'</span>&#125;,
  &#123;<span class="hljs-attr">title</span>: <span class="hljs-string">'FLEX 弹性盒模型'</span>,<span class="hljs-attr">category</span>: <span class="hljs-string">'css'</span>&#125;,
  &#123;<span class="hljs-attr">title</span>: <span class="hljs-string">'MYSQL多表查询随意操作'</span>,<span class="hljs-attr">category</span>: <span class="hljs-string">'mysql'</span>&#125;
];

<span class="hljs-keyword">for</span> (<span class="hljs-keyword">const</span> key <span class="hljs-keyword">in</span> lessons) &#123;
    <span class="hljs-built_in">console</span>.log(key);
&#125;    <span class="hljs-comment">// 0 1 2</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-44">for/of</h5>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> lessons = [
  &#123;<span class="hljs-attr">title</span>: <span class="hljs-string">'媒体查询响应式布局'</span>,<span class="hljs-attr">category</span>: <span class="hljs-string">'css'</span>&#125;,
  &#123;<span class="hljs-attr">title</span>: <span class="hljs-string">'FLEX 弹性盒模型'</span>,<span class="hljs-attr">category</span>: <span class="hljs-string">'css'</span>&#125;,
  &#123;<span class="hljs-attr">title</span>: <span class="hljs-string">'MYSQL多表查询随意操作'</span>,<span class="hljs-attr">category</span>: <span class="hljs-string">'mysql'</span>&#125;
];
<span class="hljs-keyword">for</span> (<span class="hljs-keyword">const</span> item <span class="hljs-keyword">of</span> lessons) &#123;
  <span class="hljs-built_in">console</span>.log(item)
&#125;
<span class="hljs-comment">//  输出结果为:</span>
&#123;<span class="hljs-attr">title</span>: <span class="hljs-string">"媒体查询响应式布局"</span>, <span class="hljs-attr">category</span>: <span class="hljs-string">"css"</span>&#125;
&#123;<span class="hljs-attr">title</span>: <span class="hljs-string">"FLEX 弹性盒模型"</span>, <span class="hljs-attr">category</span>: <span class="hljs-string">"css"</span>&#125;
&#123;<span class="hljs-attr">title</span>: <span class="hljs-string">"MYSQL多表查询随意操作"</span>, <span class="hljs-attr">category</span>: <span class="hljs-string">"mysql"</span>&#125;

<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-45">（6）迭代器方法</h4>
<h5 data-id="heading-46">keys</h5>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> lessons = [
  &#123;<span class="hljs-attr">title</span>: <span class="hljs-string">'媒体查询响应式布局'</span>,<span class="hljs-attr">category</span>: <span class="hljs-string">'css'</span>&#125;,
  &#123;<span class="hljs-attr">title</span>: <span class="hljs-string">'FLEX 弹性盒模型'</span>,<span class="hljs-attr">category</span>: <span class="hljs-string">'css'</span>&#125;,
  &#123;<span class="hljs-attr">title</span>: <span class="hljs-string">'MYSQL多表查询随意操作'</span>,<span class="hljs-attr">category</span>: <span class="hljs-string">'mysql'</span>&#125;
];
<span class="hljs-built_in">console</span>.log(lessons.keys())    <span class="hljs-comment">// Array Iterator &#123;&#125; 为什么？为什么？</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">const</span> array = [<span class="hljs-string">"huihui"</span>, <span class="hljs-string">"eva"</span>];
<span class="hljs-keyword">const</span> keys = array.keys();    <span class="hljs-comment">// Array Iterator &#123;&#125;</span>
<span class="hljs-built_in">console</span>.log(keys.next());    <span class="hljs-comment">// &#123;value: 0, done: false&#125;</span>
<span class="hljs-built_in">console</span>.log(keys.next());    <span class="hljs-comment">// &#123;value: 1, done: false&#125;   </span>
<span class="hljs-built_in">console</span>.log(keys.next());    <span class="hljs-comment">// &#123;value: undefined, done: true&#125; </span>

<span class="hljs-keyword">for</span>(<span class="hljs-keyword">const</span> key <span class="hljs-keyword">of</span> array.keys()) &#123;
    <span class="hljs-built_in">console</span>.log(key)    <span class="hljs-comment">// 0 1</span>
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-47">values</h5>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">const</span> array = [<span class="hljs-string">"huihui"</span>, <span class="hljs-string">"eva"</span>];
<span class="hljs-keyword">const</span> keys = array.values();    <span class="hljs-comment">// Array Iterator &#123;&#125;</span>
<span class="hljs-built_in">console</span>.log(keys.next());    <span class="hljs-comment">// &#123;value: 0, done: false&#125;</span>
<span class="hljs-built_in">console</span>.log(keys.next());    <span class="hljs-comment">// &#123;value: 1, done: false&#125;    </span>
<span class="hljs-built_in">console</span>.log(keys.next());    <span class="hljs-comment">// &#123;value: undefined, done: true&#125;  </span>

<span class="hljs-keyword">for</span>(<span class="hljs-keyword">const</span> key <span class="hljs-keyword">of</span> array.values()) &#123;
    <span class="hljs-built_in">console</span>.log(key)    <span class="hljs-comment">// 'huihui' 'eva'</span>
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h5 data-id="heading-48">entries</h5>
<p>返回数组所有键值对</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">const</span> arr = [<span class="hljs-string">"a"</span>, <span class="hljs-string">"b"</span>, <span class="hljs-string">"c"</span>,];
<span class="hljs-keyword">for</span> (<span class="hljs-keyword">const</span> [key, value] <span class="hljs-keyword">of</span> arr.entries()) &#123;
  <span class="hljs-built_in">console</span>.log(key, value);
&#125;
<span class="hljs-comment">// 输出内容为</span>
<span class="hljs-number">0</span> <span class="hljs-string">"a"</span>
<span class="hljs-number">1</span> <span class="hljs-string">"b"</span>
<span class="hljs-number">2</span> <span class="hljs-string">"c"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-49">（7）扩展方法</h4>
<h5 data-id="heading-50">every</h5>
<h5 data-id="heading-51">some</h5>
<h5 data-id="heading-52">filter</h5>
<h5 data-id="heading-53">map</h5>
<h5 data-id="heading-54">reduce</h5>
<h4 data-id="heading-55">（8）数组应用</h4>
<h5 data-id="heading-56">（1）清空数组的几种方法</h5>
<h5 data-id="heading-57">（2）数组去重的几种方法</h5>
<p>---- 未完待续</p></div>  
</div>
            
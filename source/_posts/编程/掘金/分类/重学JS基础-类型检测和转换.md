
---
title: '重学JS基础-类型检测和转换'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=5569'
author: 掘金
comments: false
date: Sat, 17 Jul 2021 01:10:20 GMT
thumbnail: 'https://picsum.photos/400/300?random=5569'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h2 data-id="heading-0">一.类型检测</h2>
<h3 data-id="heading-1">1.typeof方法</h3>
<p>typeof是一个运算符，有2种使用方式：typeof(表达式)和typeof 变量名，第一种是对表达式做运算，第二种是对变量做运算。
typeof运算符的返回值包括如下几种：</p>
<ul>
<li>'undefined'              --未定义的变量或值</li>
<li>'boolean'                 --布尔类型的变量或值</li>
<li>'string'                     --字符串类型的变量或值</li>
<li>'number'                  --数字类型的变量或值</li>
<li>'object'               --对象类型的变量或值，或者null(这个是js历史遗留问题，将null作为object类型处理,因为设计的时候<code>null</code>是全 0，而对象是<code>000</code>开头，所以有这个误判)</li>
<li>'function'                 --函数类型的变量或值</li>
</ul>
<p>简单的示例</p>
<pre><code class="hljs language-javascript copyable" lang="javascript">    <span class="hljs-built_in">console</span>.log(<span class="hljs-keyword">typeof</span> a);    <span class="hljs-comment">//'undefined'</span>
    <span class="hljs-built_in">console</span>.log(<span class="hljs-keyword">typeof</span>(<span class="hljs-literal">true</span>));  <span class="hljs-comment">//'boolean'</span>
    <span class="hljs-built_in">console</span>.log(<span class="hljs-keyword">typeof</span> <span class="hljs-string">'123'</span>);  <span class="hljs-comment">//'string'</span>
    <span class="hljs-built_in">console</span>.log(<span class="hljs-keyword">typeof</span> <span class="hljs-number">123</span>);   <span class="hljs-comment">//'number'</span>
    <span class="hljs-built_in">console</span>.log(<span class="hljs-keyword">typeof</span> <span class="hljs-literal">NaN</span>);   <span class="hljs-comment">//'number'</span>
    <span class="hljs-built_in">console</span>.log(<span class="hljs-keyword">typeof</span> <span class="hljs-literal">null</span>);  <span class="hljs-comment">//'object'    </span>
    <span class="hljs-keyword">var</span> obj = <span class="hljs-keyword">new</span> <span class="hljs-built_in">String</span>();
    <span class="hljs-built_in">console</span>.log(<span class="hljs-keyword">typeof</span>(obj));    <span class="hljs-comment">//'object'</span>
    <span class="hljs-keyword">var</span>  fn = <span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params"></span>)</span>&#123;&#125;;
    <span class="hljs-built_in">console</span>.log(<span class="hljs-keyword">typeof</span>(fn));  <span class="hljs-comment">//'function'</span>
    <span class="hljs-built_in">console</span>.log(<span class="hljs-keyword">typeof</span>(<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">c</span></span>&#123;&#125;));  <span class="hljs-comment">//'function'</span>
    <span class="hljs-built_in">console</span>.log(<span class="hljs-keyword">typeof</span>([]));  <span class="hljs-comment">//'object'</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><strong>注意</strong>:这里typeof检测后返回的都是字符串,所以</p>
<pre><code class="hljs language-javascript copyable" lang="javascript">    <span class="hljs-keyword">typeof</span>(<span class="hljs-keyword">typeof</span>(<span class="hljs-number">11</span>));         <span class="hljs-comment">//"string"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>另外:</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">typeof</span>(<span class="hljs-literal">null</span>)=<span class="hljs-built_in">Object</span>  
<span class="hljs-keyword">typeof</span>(<span class="hljs-built_in">Object</span>)=<span class="hljs-function"><span class="hljs-keyword">function</span> //内置构造器的类型都是<span class="hljs-function"><span class="hljs-keyword">function</span>
</span></span><span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-2">2.instance of 方法</h3>
<p>typeof检测出Object类型的变量后不能进一步检测出是哪种Object(比如Array,Date)</p>
<p>而instanceof用于判断一个变量是否某个对象的实例比如：</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-built_in">console</span>.log([] <span class="hljs-keyword">instanceof</span> <span class="hljs-built_in">Array</span>);<span class="hljs-comment">//true</span>
<span class="hljs-built_in">console</span>.log(&#123;&#125; <span class="hljs-keyword">instanceof</span> <span class="hljs-built_in">Object</span>);<span class="hljs-comment">//true</span>
<span class="hljs-built_in">console</span>.log(<span class="hljs-regexp">/\d/</span> <span class="hljs-keyword">instanceof</span> <span class="hljs-built_in">RegExp</span>);<span class="hljs-comment">//true</span>
<span class="hljs-built_in">console</span>.log(<span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params"></span>)</span>&#123;&#125; <span class="hljs-keyword">instanceof</span> <span class="hljs-built_in">Object</span>);<span class="hljs-comment">//true</span>
<span class="hljs-built_in">console</span>.log(<span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params"></span>)</span>&#123;&#125; <span class="hljs-keyword">instanceof</span> <span class="hljs-built_in">Function</span>);<span class="hljs-comment">//true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>不过它不能判断js的基础数据类型</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-built_in">console</span>.log(<span class="hljs-string">''</span> <span class="hljs-keyword">instanceof</span> <span class="hljs-built_in">String</span>);<span class="hljs-comment">//false</span>
<span class="hljs-built_in">console</span>.log(<span class="hljs-number">1</span> <span class="hljs-keyword">instanceof</span> <span class="hljs-built_in">Number</span>);<span class="hljs-comment">//false</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><strong>除此之外，instanceof最大的用处便是用来检测自定义类，并且由于内部机制是通过instanceof是通过判断左边对象的原型琏中是否存在右边构造函数的prototype来判断类型，所以它也能检测继承关系</strong></p>
<p>一般情况</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">User</span>(<span class="hljs-params">name</span>)</span>&#123;<span class="hljs-built_in">this</span>.name = name&#125;
<span class="hljs-keyword">var</span> user = <span class="hljs-keyword">new</span> User()
user <span class="hljs-keyword">instanceof</span> User    <span class="hljs-comment">//true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>还有继承的情况</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">Foo</span>(<span class="hljs-params"></span>) </span>&#123;&#123;
<span class="hljs-built_in">this</span>.name = <span class="hljs-string">'wyh'</span>
<span class="hljs-built_in">this</span>.age = <span class="hljs-string">'23'</span>
&#125;

<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">GFoo</span>(<span class="hljs-params"></span>) </span>&#123;
<span class="hljs-built_in">this</span>.country = <span class="hljs-string">'China'</span>
&#125;

Foo.prototype = <span class="hljs-keyword">new</span> GFoo()

<span class="hljs-keyword">let</span> foo = <span class="hljs-keyword">new</span> Foo()
<span class="hljs-built_in">console</span>.log(foo <span class="hljs-keyword">instanceof</span> Foo)  <span class="hljs-comment">// true</span>
<span class="hljs-built_in">console</span>.log(foo <span class="hljs-keyword">instanceof</span> GFoo) <span class="hljs-comment">// true&#125;&#125;</span>

<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-3">3.使用Object.prototype.toString.call()</h3>
<p>调用Object.prototype.toString.call()方法可以判断出某个变量属于哪种js的内置对象，并且输出标准格式。</p>
<h4 data-id="heading-4">检测基本类型</h4>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-built_in">Object</span>.prototype.toString.call(<span class="hljs-literal">null</span>); <span class="hljs-comment">// "[object Null]"</span>
<span class="hljs-built_in">Object</span>.prototype.toString.call(<span class="hljs-literal">undefined</span>); <span class="hljs-comment">// "[object Undefined]"</span>
<span class="hljs-built_in">Object</span>.prototype.toString.call(“abc”);<span class="hljs-comment">// "[object String]"</span>
<span class="hljs-built_in">Object</span>.prototype.toString.call(<span class="hljs-number">123</span>);<span class="hljs-comment">// "[object Number]"</span>
<span class="hljs-built_in">Object</span>.prototype.toString.call(<span class="hljs-literal">true</span>);<span class="hljs-comment">// "[object Boolean]"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-5">检测引用类型</h4>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-built_in">Function</span> <span class="hljs-function"><span class="hljs-title">fn</span>(<span class="hljs-params"></span>)</span>&#123;
  <span class="hljs-built_in">console</span>.log(“test”);
&#125;
<span class="hljs-built_in">Object</span>.prototype.toString.call(fn); <span class="hljs-comment">// "[object Function]"</span>

<span class="hljs-keyword">var</span> date = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Date</span>();
<span class="hljs-built_in">Object</span>.prototype.toString.call(date); <span class="hljs-comment">// "[object Date]"</span>

<span class="hljs-keyword">var</span> arr = [<span class="hljs-number">1</span>,<span class="hljs-number">2</span>,<span class="hljs-number">3</span>];
<span class="hljs-built_in">Object</span>.prototype.toString.call(arr); <span class="hljs-comment">// "[object Array]"</span>

<span class="hljs-keyword">var</span> reg = <span class="hljs-regexp">/[hbc]at/gi</span>;
<span class="hljs-built_in">Object</span>.prototype.toString.call(reg); <span class="hljs-comment">// "[object RegExp]"</span>

<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-6">注意:无法检测自定义类型</h4>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">Person</span>(<span class="hljs-params">name, age</span>) </span>&#123;
    <span class="hljs-built_in">this</span>.name = name;
    <span class="hljs-built_in">this</span>.age = age;
&#125;
<span class="hljs-keyword">var</span> person = <span class="hljs-keyword">new</span> Person(<span class="hljs-string">"Rose"</span>, <span class="hljs-number">18</span>);
<span class="hljs-built_in">Object</span>.prototype.toString.call(arr); <span class="hljs-comment">// "[object Object]"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-7">4.实现一个类型判断函数</h3>
<p>思路:</p>
<ol>
<li>判断 null</li>
<li>使用 typeof 判断基础类型</li>
<li>使用<code>Object.prototype.toString.call(target)</code>来判断<strong>引用类型</strong></li>
</ol>
<h2 data-id="heading-8">二.类型转换</h2>
<h3 data-id="heading-9">1，显式类型转换</h3>
<h4 data-id="heading-10">Number()函数</h4>
<p>Number函数可以直接将括号里面的内容转化为类型为number的数字，对于无法转化的也不会报错，而是返回一个NaN。</p>
<p>注意:将null转化为数字返回0，将undefined转化为数字返回NaN</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-built_in">Number</span>(<span class="hljs-string">"123"</span>)   <span class="hljs-comment">//123</span>
<span class="hljs-built_in">Number</span>(<span class="hljs-string">'abc'</span>)  <span class="hljs-comment">//NaN</span>
<span class="hljs-built_in">Number</span>(<span class="hljs-literal">null</span>)   <span class="hljs-comment">//0</span>
<span class="hljs-built_in">Number</span>(underfined) <span class="hljs-comment">//NaN</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-11">String()函数</h4>
<p>String函数和Number一样，是可以直接将括号里面的内容转换为字符串的形式.</p>
<p>要注意的是</p>
<ul>
<li>当转化的是 null undefined这一类值的时候，返回的是字符串形式的"null"和"undefined"。</li>
<li>在转化1.00和1.10这类浮点数的时候，会自动消掉后面的0</li>
</ul>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-built_in">String</span>(<span class="hljs-number">999</span>)   <span class="hljs-comment">//"999"</span>
<span class="hljs-built_in">String</span>(<span class="hljs-literal">null</span>)  <span class="hljs-comment">//'null'</span>
<span class="hljs-built_in">String</span>(<span class="hljs-literal">undefined</span>)   <span class="hljs-comment">//"undefined"</span>
<span class="hljs-built_in">String</span>(<span class="hljs-number">1.00</span>)  <span class="hljs-comment">//1</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-12">parseInt()函数</h4>
<p>这个函数的作用，是将括号里面的值转化为整型。 可以接收第二个参数，即被转化的数字的进制类型</p>
<p>不过要注意的是</p>
<ul>
<li>使用这个函数转化类似于'123abc'的值不会报错，而是返回数字 123 ，这是因为这个函数在转化的时候，会默认停止在第一位非数字位.</li>
<li>在转化浮点数的时候，也只会保留整数部分。</li>
<li>对于完全无法转化的变量函数返回一个NaN。</li>
</ul>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-built_in">parseInt</span>(<span class="hljs-string">'16'</span>,<span class="hljs-number">8</span>) <span class="hljs-comment">//14 即将8进制的16转化为10进制</span>
<span class="hljs-built_in">parseInt</span>(<span class="hljs-string">"11aaa"</span>)   <span class="hljs-comment">//11</span>
<span class="hljs-built_in">parseInt</span>(<span class="hljs-string">"aaa11"</span>)   <span class="hljs-comment">//NaN</span>
<span class="hljs-built_in">parseInt</span>(<span class="hljs-string">'1.23abc'</span>) <span class="hljs-comment">//1</span>
<span class="hljs-built_in">parseInt</span>(<span class="hljs-string">'1.23'</span>)    <span class="hljs-comment">//1</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-13">parseFloat()函数</h4>
<p>这个函数和ParseInt()的特点几乎是相同的，不同的部分自然是这个函数可以转化的不再局限于整数，还可以转化浮点数。</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-built_in">console</span>.log(<span class="hljs-built_in">parseFloat</span>(<span class="hljs-string">"123"</span>));         <span class="hljs-comment">//123</span>
<span class="hljs-built_in">console</span>.log(<span class="hljs-built_in">parseFloat</span>(<span class="hljs-string">"123.123"</span>));     <span class="hljs-comment">//123.123</span>
<span class="hljs-built_in">console</span>.log(<span class="hljs-built_in">parseFloat</span>(<span class="hljs-string">"123.00"</span>));      <span class="hljs-comment">//123</span>
<span class="hljs-built_in">console</span>.log(<span class="hljs-built_in">parseFloat</span>(<span class="hljs-string">"123.12aaa31"</span>)); <span class="hljs-comment">//123.12</span>
<span class="hljs-built_in">console</span>.log(<span class="hljs-built_in">parseFloat</span>(<span class="hljs-string">"aaa123.1231"</span>)); <span class="hljs-comment">//NaN</span>
<span class="hljs-built_in">console</span>.log(<span class="hljs-built_in">parseFloat</span>(<span class="hljs-string">"aaa"</span>));         <span class="hljs-comment">//NaN</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-14">toString()方法</h4>
<p>这个方法与String()类似，但是有两个不同点，</p>
<ul>
<li>一个是这个方法是在变量后面加.toString来调用</li>
<li>一个是这个方法不能转化"null"和"undefined"</li>
</ul>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-keyword">var</span> a = <span class="hljs-number">123</span>
<span class="hljs-built_in">console</span>.log(a.toString());  <span class="hljs-comment">//"123"</span>
<span class="hljs-keyword">var</span> b;      
<span class="hljs-built_in">console</span>.log(b.toString());  <span class="hljs-comment">//"报错"</span>
<span class="hljs-keyword">var</span> c = <span class="hljs-literal">null</span>;
<span class="hljs-built_in">console</span>.log(c.toString());  <span class="hljs-comment">//"报错"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-15">Boolean()方法</h4>
<p>这个方法将括号中的内容转化为布尔值,转化的只要是对象最后都会返回true。</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-built_in">console</span>.log(<span class="hljs-built_in">Boolean</span>(<span class="hljs-number">1</span>));            <span class="hljs-comment">//true</span>
<span class="hljs-built_in">console</span>.log(<span class="hljs-built_in">Boolean</span>(<span class="hljs-number">0</span>));            <span class="hljs-comment">//false</span>
<span class="hljs-built_in">console</span>.log(<span class="hljs-built_in">Boolean</span>(<span class="hljs-string">""</span>));           <span class="hljs-comment">//false</span>
<span class="hljs-built_in">console</span>.log(<span class="hljs-built_in">Boolean</span>(<span class="hljs-literal">undefined</span>));    <span class="hljs-comment">//false</span>
<span class="hljs-built_in">console</span>.log(<span class="hljs-built_in">Boolean</span>([]));           <span class="hljs-comment">//true</span>
<span class="hljs-built_in">console</span>.log(<span class="hljs-built_in">Boolean</span>(&#123;&#125;));           <span class="hljs-comment">//true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-16">2，隐式类型转化</h3>
<h4 data-id="heading-17">isNaN()</h4>
<p>作用是判断一个变量 是不是 NaN,但是它在判断的时候做了一个类型转化，即先对括号中的内容进行Number的转化。</p>
<p>最后，不能转化为Number的都将返回false,所以它不能明确判断一个变量是不是NaN</p>
<pre><code class="hljs language-javasricpt copyable" lang="javasricpt">isNaN(123) //返回false
isNaN('abc') //返回true
isNaN(undefined) //返回true
isNaN(null) //返回false
isNaN(NaN) //返回True
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-18">++/-- +/-一元正负</h4>
<p>先调用Number()进行类型转换，然后再对变量进行运算符操作</p>
<pre><code class="hljs language-javascript copyable" lang="javascript">++ <span class="hljs-string">'123'</span>  <span class="hljs-comment">//返回number类型的124</span>
++ <span class="hljs-string">'abc'</span> <span class="hljs-comment">//返回number类型的NaN</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-19">加法运算符: +</h4>
<p>当运算符两侧有一个为String，调用的隐式方法为String()</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-number">123</span>+<span class="hljs-string">"aaa"</span>
<span class="hljs-comment">//"123aaa"</span>
<span class="hljs-number">123</span>+<span class="hljs-string">"111"</span>
<span class="hljs-comment">//"123111"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-20">其他运算符: - * / %</h4>
<p>先对运算符两侧的变量执行Number()类型转换，然后再做运算</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-string">"a"</span> - <span class="hljs-number">1</span>  <span class="hljs-comment">//结果为NaN</span>
<span class="hljs-number">1</span> * <span class="hljs-string">'a'</span>  <span class="hljs-comment">//结果为NaN</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-21">与或非: && || ！</h4>
<p>会使用Boolean()方法对表达式两边做隐式类型转换</p>
<h4 data-id="heading-22">比较运算符: > >= < <=</h4>
<p>两边有一个为非数字，都会先转化为数字（true转化为1，false转化为0），再进行比较，返回一个布尔值。</p>
<h4 data-id="heading-23">等于: ==</h4>
<p>这个比较会先把两边转化为相同类型，然后比较其值是否相等，注意 NaN==NaN返回false</p>
<h3 data-id="heading-24">3,装箱转换和拆箱转换</h3>
<h4 data-id="heading-25">装箱转换：把基本数据类型转化为对应的引用数据类型的操作</h4>
<p>每当读取一个基本类型的时候，后台就会创建一个对应的基本包装类型对象，从而让我们能够调用一些方法来操作这些数据。</p>
<p>比如</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> s1 = <span class="hljs-string">"abc"</span>;
<span class="hljs-keyword">var</span> s2 = s1.indexOf(<span class="hljs-string">"a"</span>)
<span class="copy-code-btn">复制代码</span></code></pre>
<p>变量s1是一个基本类型值，它不是对象，它不应该有方法。但是js内部为我们完成了一系列处理（即装箱），使得它能够调用方法,实现的机制如下：</p>
<ul>
<li>创建String类型的一个实例；</li>
<li>在实例上调用指定的方法；</li>
<li>销毁这个实例；</li>
</ul>
<p>后台隐式做了如下操作</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> s1  = <span class="hljs-keyword">new</span> <span class="hljs-built_in">String</span>(<span class="hljs-string">"some text"</span>);
<span class="hljs-keyword">var</span> s2 = s1.substring(<span class="hljs-number">2</span>);
s1 = <span class="hljs-literal">null</span>;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>这样就完成装箱，我们也就能在s1上调用方法了</p>
<h4 data-id="heading-26">拆箱转换：将引用类型对象转换为对应的值类型对象</h4>
<p>它是通过引用类型的valueOf()或者toString()方法来实现的。如果是自定义的对象，你也可以自定义它的valueOf()/tostring()方法，实现对这个对象的拆箱</p>
<p>比如</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> num = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Number</span>(<span class="hljs-number">10</span>);
<span class="hljs-built_in">console</span>.log(<span class="hljs-keyword">typeof</span>(num));   <span class="hljs-comment">//Object</span>
num = num + <span class="hljs-number">2</span>;
<span class="hljs-built_in">console</span>.log(<span class="hljs-keyword">typeof</span>(num));   <span class="hljs-comment">//Number</span>


<span class="hljs-keyword">var</span> o = &#123;
<span class="hljs-attr">valueOf</span>: <span class="hljs-function">() =></span> &#123; <span class="hljs-built_in">console</span>.log(<span class="hljs-string">"valueOf"</span>); <span class="hljs-keyword">return</span> <span class="hljs-number">1</span> &#125;,
<span class="hljs-attr">toString</span>: <span class="hljs-function">() =></span> &#123; <span class="hljs-built_in">console</span>.log(<span class="hljs-string">"toString"</span>); <span class="hljs-keyword">return</span> <span class="hljs-number">1</span> &#125;
&#125;

<span class="hljs-built_in">console</span>.log(o + <span class="hljs-string">"aaa"</span>); <span class="hljs-comment">// "1aaa"</span>
<span class="hljs-built_in">console</span>.log(o * <span class="hljs-number">2</span>);     <span class="hljs-comment">// 2</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><strong>注意</strong>：一般情况下它会先调用你的valueOf方法，如果发现不存在， 才会调用toString方法。</p>
<hr>
<h3 data-id="heading-27">最后</h3>
<p>感谢你能看到这里，欢迎在评论区留言交流，如果可以的话，不妨点个赞再走呀。</p></div>  
</div>
            
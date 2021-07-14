
---
title: '一次搞懂JavaScript类型隐式转换：__ == !__'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=4027'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 00:52:48 GMT
thumbnail: 'https://picsum.photos/400/300?random=4027'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h1 data-id="heading-0">前言</h1>
<p>想必大家在面试当中，往往都遇到过类似于给你一段奇怪的代码<code>[]+&#123;&#125;</code>让你写出输出结果的场景，本次就帮你一次搞懂js隐式转换，面试不再踩坑</p>
<h1 data-id="heading-1">分析：为什么有隐式转换？</h1>
<p>想知道什么是隐式转换，首先我们先搞懂什么是<code>显示类型转换</code>？<br></p>
<p>在执行某些操作时，由于我们需要调用对应类型所提供的api，或进行运算，会主动的改变变量的类型，例如String(),Number(),parsenInt(),toString()..等类似的方法，此类由我们手动转换类型的方式，称为显示类型转换<br></p>
<p>那么<code>隐式类型转换</code>呢？<br></p>
<p>JavaScript是弱类型语言，这意味着它不像Java，C++一样的强类型语言有预先确定的类型。<br>
并且变量的类型是由值的类型来决定的，这导致了一个问题，一个变量可能上一步骤操作中还是String，下一步操作可能立刻变为了Object，为了解决不同类型无法进行计算，JS底层会将不同类型转换为同一类型，由JS运行环境自动帮我们去做的类型转换，称为隐式类型转换</p>
<h1 data-id="heading-2">JS数据类型</h1>
<p>JS的两大类数据类型：</p>
<p>原始类型：Undefined、 Null、 String、 Number、 Boolean、Symbol<br>
引用类型：Object</p>
<p>Symbol是由ES6新提出的，我们这里先不讲</p>
<h1 data-id="heading-3">转换规则</h1>
<blockquote>
<p>ECMAScript 运行时系统会在需要时从事自动类型转换。为了阐明某些结构的语义，定义一集转换运算符是很有用的。这些运算符不是语言的一部分；在这里定义它们是为了协助语言语义的规范。转换运算符是多态的 — 它们可以接受任何 ECMAScript 语言类型 的值，但是不接受 规范类型 。</p>
</blockquote>
<p>既然规则是<a href="https://link.juejin.cn/?target=http%3A%2F%2Fyanhaijing.com%2Fes5%2F%23102" target="_blank" rel="nofollow noopener noreferrer" title="http://yanhaijing.com/es5/#102" ref="nofollow noopener noreferrer">ES5规范（见第9章类型转换）</a>定义的，那就没必要讨论为什么了，记住怎么用就好了。<br></p>
<p>我们来了解三个概念：</p>
<ul>
<li>转换为原始值</li>
<li>转换为数字</li>
<li>转换为字符串</li>
</ul>
<p>因为上边文档当中已有比较详细的描述，这里只做些简单的解释，详情请查阅文档</p>
<h2 data-id="heading-4">ToPrimitive(转换为原始值)</h2>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">/**
* <span class="hljs-doctag">@obj </span>需要转换的对象
* <span class="hljs-doctag">@type </span>期望转换为的原始数据类型，可选
*/</span>
ToPrimitive(obj,type) <span class="hljs-comment">//该方法接收两个参数</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>type可以为number或者string，两者的执行顺序有一些差别<br></p>
<p>string：调用Object的toString方法，如果为原始值则返回，否则再去调用Object的valueOf方法，如果为原始值则返回，否则抛出TypeError异常<br></p>
<p>number：调用Object的valueOf方法，如果为原始值则返回，否则再去调用Object的toString方法，如果为原始值则返回，否则抛出TypeError异常<br></p>
<p>其实就是调用方法先后，毕竟期望数据类型不同，如果是string当然优先调用toString。反之亦然。</p>
<p>并且type参数可以为空，这时候type的默认值会按照下面的规则设置：</p>
<p>该对象为Date，则type被设置为String否则，type被设置为Number</p>
<p>对于Date数据类型，我们更多期望获得的是其转为时间后的字符串，而非毫秒值，如果为number，则会取到对应的毫秒值，显然字符串使用更多。</p>
<p>其他类型对象按照取值的类型操作即可。</p>
<blockquote>
<p>概括而言，ToPrimitive转成何种原始类型，取决于type，type参数可选，若指定，则按照指定类型转换，若不指定，默认根据实用情况分两种情况，Date为string，其余对象为number。那么什么时候会指定type类型呢，那就要看下面两种转换方式了。</p>
</blockquote>
<h2 data-id="heading-5">toNumber</h2>
<p>某些特定情况下需要用到ToNumber方法来转成number<br>
如果为原始类型则转换为该参数的数值类型：</p>

































<table><thead><tr><th>输入类型</th><th>结果</th></tr></thead><tbody><tr><td>Undefined</td><td>NaN</td></tr><tr><td>Null</td><td>+0</td></tr><tr><td>Boolean</td><td>如果参数是true，结果为1<br>如果参数是false，此结果为+0</td></tr><tr><td>Number</td><td>结果等于输入的参数（不转换）</td></tr><tr><td>String</td><td>情况比较多，参考规范</td></tr><tr><td>Object</td><td>依次调用<br>1.先获取原始值调用ToPrimitive（输入参数type为number）<br>2.再将原始类型调用ToNumber（原始值）</td></tr></tbody></table>
<p>ps：对于String类型，特殊的情况比较多，一般只要掌握常见的就可以，和直接调用Number()函数结果是一致的。
需要注意的是，<code>如果当参数为Object类型的时候，会先调用ToPrimitive，type指定为number类型，获取原始类型后再调用ToNumber</code></p>
<h2 data-id="heading-6">toString</h2>
<p>ToString 运算符根据下表将其参数转换为字符串类型的值：</p>

































<table><thead><tr><th>输入类型</th><th>结果</th></tr></thead><tbody><tr><td>Undefined</td><td>"undefined"</td></tr><tr><td>Null</td><td>"null"</td></tr><tr><td>Boolean</td><td>如果参数是true，结果为"true"<br>如果参数是false，此结果为"false"</td></tr><tr><td>Number</td><td>情况比较多，参考规范</td></tr><tr><td>String</td><td>结果等于输入的参数（不转换</td></tr><tr><td>Object</td><td>依次调用<br>1.先获取原始值调用ToPrimitive（输入参数type为string）<br>2.再将原始类型调用ToString（原始值）</td></tr></tbody></table>
<p>常见的规律</p>
<ul>
<li>Undefined，null，boolean直接加上引号，例如'null'</li>
<li>number的规范则比较多，1为"1"，-1为"-1"，NaN为"NaN"</li>
<li>对象则是先转为原始值，再按照上面的步骤进行处理。</li>
</ul>
<h2 data-id="heading-7">valueOf</h2>
<p>当调用valueOf方法时，步骤如下：<br></p>
<ol>
<li>调用ToObject方法得到一个对象<code>（其实就是包装类型，感兴趣的同学可以自己去了解下）</code></li>
<li>原始数据类型转换为对应的内置对象，引用类型（Object）则不变</li>
<li>调用该对象内置的valueOf方法（继承自Object.prototype对象）</li>
</ol>
<p>不同内置对象的valueOf实现：</p>
<ul>
<li>String => 返回字符串值</li>
<li>Number => 返回数字值</li>
<li>Date => 返回一个数字，即时间值,字符串中内容是依赖于具体实现的</li>
<li>Boolean => 返回Boolean的this值</li>
<li>Object => 返回this</li>
</ul>
<h1 data-id="heading-8">隐式转换：重头戏来了 []==![]</h1>
<p>前面讲了那么多概念，其实就是为了大家可以充分理解，在运算隐式转换时，js究竟都做了什么<br></p>
<h2 data-id="heading-9">例：+运算</h2>
<ol>
<li>在进行运算时+左右分别进行进行ToPrimitive()操作，获取原始值</li>
<li>如果获取的原始值当中包含String，则对所有原始值执行toString处理后进行拼接</li>
<li>其他的都进行toNumber处理</li>
<li>在转换时ToPrimitive，除去Date为String外都按照ToPrimitive type为Number进行处理</li>
</ol>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-number">1</span>+<span class="hljs-string">'2'</span>+<span class="hljs-literal">false</span> <span class="hljs-comment">// '12false'</span>
<span class="hljs-comment">// 我们来拆解一下运算过程：</span>
<span class="hljs-comment">// 按执行顺序从左到右执行，先计算1+'2'</span>
<span class="hljs-comment">// 1. 左右两边同事进行ToPrimitive()操作，左边为原始类型，依旧是Number，右边为String</span>
<span class="hljs-comment">// 2. 因为返回的原始值当中包含String，于是对所有原始值进行toString处理，变为 '1'+'2'，得到结果'12'</span>
<span class="hljs-comment">// 3. 然后重复第一步操作，计算'12'+false</span>
<span class="hljs-comment">// 4. 左右两边都为原始值，但是'12'为String类型，则布尔值也转为'false'</span>
<span class="hljs-comment">// 5. '12'+'false' 进行拼接得到最后结果 '12false'</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-10">例：引用类型进行计算</h2>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> obj1 = &#123;
    <span class="hljs-attr">valueOf</span>:<span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params"></span>)</span>&#123;
        <span class="hljs-keyword">return</span> <span class="hljs-number">1</span>
    &#125;
&#125;
<span class="hljs-keyword">var</span> obj2 = &#123;
    <span class="hljs-attr">toString</span>:<span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params"></span>)</span>&#123;
        <span class="hljs-keyword">return</span> <span class="hljs-string">'a'</span>
    &#125;
&#125;
<span class="hljs-comment">// 下面我们还是拆解一下运算过程</span>
<span class="hljs-number">1</span>+obj1 <span class="hljs-comment">// 2</span>
<span class="hljs-comment">// 1. 左右两边同时进行ToPrimitive()操作，左边为原始类型，依旧是Number，右边为引用类型，按照type为number进行转换</span>
<span class="hljs-comment">// 2. 先调用obj1.valueOf方法，我们知道引用类型不会进行包装，于是直接调用obj1内部的valueOf方法，返回1</span>
<span class="hljs-comment">// 3. 得到两边都是number类型，于是直接进行相加1 + 1，输出2</span>
<span class="hljs-number">1</span>+obj2 <span class="hljs-comment">// 1a</span>
<span class="hljs-comment">// 1. 左右两边同时进行ToPrimitive()操作，左边为原始类型，依旧是Number，右边为引用类型，按照type为number进行转换</span>
<span class="hljs-comment">// 2. 先调用obj2.valueOf方法，我们知道引用类型不会进行包装，于是直接调用obj2内部的valueOf方法，因为valueOf方法没有重写，于是调用的是Object.prototype.valueOf返回的是obj2的this，发现得到的不是一个原始值，于是继续调用toString方法，返回 'a'</span>
<span class="hljs-comment">// 3. 得到2个原始类型后发现，其中包含String类型，于是调用toString全部转为string类型，得到'1'+'a'</span>
<span class="hljs-comment">// 4. 最终拼接出结果 '1a'</span>
obj1+obj2
<span class="hljs-comment">// 1.左右两边同时进行ToPrimitive()操作，根据上边的运算，我们知道obj1返回数值类型1，obj2返回是字符类型'a'</span>
<span class="hljs-comment">// 2.得到2个原始类型后发现，其中包含String类型，于是调用toString全部转为string类型，得到'1'+'a'</span>
<span class="hljs-comment">// 3. 最终拼接出结果 '1a'</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-11">例：==抽象相等比较</h2>
<p>这种比较分为两类</p>
<ul>
<li>类型相同</li>
<li>类型不同</li>
</ul>
<p>类型相同时不会发生隐式转换，于是我们只谈类型不同之时，这里的规律比较复杂，不过只要牢记一个点，进行+运算时是</p>
<pre><code class="hljs language-js copyable" lang="js">如果获取的原始值当中包含<span class="hljs-built_in">String</span>，则对所有原始值执行toString处理后进行拼接
<span class="copy-code-btn">复制代码</span></code></pre>
<p>而进行逻辑运算时，刚好相反</p>
<pre><code class="hljs language-js copyable" lang="js">如果获取的原始值当中包含<span class="hljs-built_in">String</span>，则尽量将<span class="hljs-built_in">String</span>转为<span class="hljs-built_in">Number</span>类型后进行比较
<span class="copy-code-btn">复制代码</span></code></pre>
<p>因为毕竟比较的期望还是数值的比较</p>
<p>1.如果均为number类型，直接比较</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-number">1</span> == <span class="hljs-number">2</span> <span class="hljs-comment">// false</span>
<span class="hljs-comment">//两边都是数值类型，没有隐式转换</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>2.如果x为string，y为number，x转成number进行比较</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-string">'0'</span> == <span class="hljs-number">0</span> <span class="hljs-comment">// true</span>
<span class="hljs-comment">// 其实就是我上边说的，如果有字符串将字符串转为数字 0 == 0 返回true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>3.存在boolean，安装toNumber将boolean转为1或0，再进行比较</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-number">3</span> == <span class="hljs-literal">true</span> <span class="hljs-comment">// false</span>
<span class="hljs-comment">// 还是获取原始值，3 == 1返回false</span>
<span class="hljs-string">'0'</span> == <span class="hljs-literal">false</span> <span class="hljs-comment">// true</span>
<span class="hljs-comment">// 获取原始值，'0' == 0，将String转为Number，0 == 0返回true</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>4.如果存在对象，调用ToPrimitive获取原始类型，再进行比较</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> obj = &#123;
    <span class="hljs-attr">valueOf</span>:<span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params"></span>)</span>&#123;
        <span class="hljs-keyword">return</span> <span class="hljs-string">'1'</span>
    &#125;
&#125;
<span class="hljs-number">1</span> == obj <span class="hljs-comment">// true</span>
<span class="hljs-comment">// 1. 两边同时调用ToPrimitive type为number进行转换，调用obj的valueOf方法，发现返回的是个原始值String类型</span>
<span class="hljs-comment">// 2. 于是对String类型进行处理，转换为Number类型</span>
<span class="hljs-comment">// 3. 1 == 1 于是返回 true</span>
[] == ![] <span class="hljs-comment">// true</span>
<span class="hljs-comment">// 1.[]作为对象ToPrimitive得到''</span>
<span class="hljs-comment">// 2.![]作为boolean转换得到0，有些同学可能会有疑问啊，[]为''，!''不应该为ture是1吗，其实不是，</span>
<span class="hljs-comment">//   我们知道引用类型[]其实是一个指向内存的地址，这个地址肯定是有的，于是!取反，则返回false，为0</span>
<span class="hljs-comment">// 3. '' == 0 发现包含字符串，于是toNumber转为number得到0 == 0 返回 true</span>
<span class="copy-code-btn">复制代码</span></code></pre></div>  
</div>
            
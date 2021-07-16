
---
title: '【Typescript】精选的知识点'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=7241'
author: 掘金
comments: false
date: Thu, 15 Jul 2021 18:31:30 GMT
thumbnail: 'https://picsum.photos/400/300?random=7241'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h2 data-id="heading-0">TS和JS的区别</h2>








































<table><thead><tr><th></th><th>ts</th><th>js</th></tr></thead><tbody><tr><td>函数返回值</td><td>有类型</td><td>无</td></tr><tr><td>函数参数</td><td>必填和可选参数</td><td>所有参数都是可选的</td></tr><tr><td>函数重载</td><td>有</td><td>无</td></tr><tr><td>typeof</td><td>推算一个变量的类型</td><td>获取变量的类型</td></tr><tr><td>extends</td><td>在 interface 中表示类型扩展，在条件类型语句中表示布尔运算，在泛型中起到限制的作用，在 class 中表示继承</td><td>在 class 中表示继承</td></tr><tr><td>window</td><td>window.a = &#123;&#125;报错，(window as any).a = &#123;&#125;;正确</td><td>window.a = &#123;&#125;没错</td></tr></tbody></table>
<h2 data-id="heading-1">基础基础</h2>
<h3 data-id="heading-2">ts的类型</h3>
<p>object表示非原始类型，也就是除number，string，boolean，symbol，null或undefined之外的类型。</p>
<p>除了js的类型，还有Tuple enum Any void Never unknown</p>
<h3 data-id="heading-3">string类型的数组，建议双引号</h3>
<h3 data-id="heading-4">Tuple</h3>
<p>元祖类型属于数组的一种，可以指定多种类型，个人觉得比数组功能强大</p>
<h3 data-id="heading-5">Void</h3>
<pre><code class="copyable">function voidFun(): void &#123;
  console.log("hello");
&#125;
voidFun()  //hello
<span class="copy-code-btn">复制代码</span></code></pre>
<p>注：声明一个 void 类型的变量没有什么作用，<code>因为它的值只能为 undefined 或 null</code></p>
<pre><code class="copyable">let unusable: void = undefined;
let unusable1: void ;
console.log(unusable);  //undefined
console.log(unusable1);  //undefined

let unusable: void  = null;
//unusable提示 ：type 'null' is not assignable to type 'void'
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-6">Null和Undefined</h3>
<p>默认情况下 null 和 undefined 是所有类型的子类型，然而，如果指定了--strictNullChecks 标记，null 和 undefined <code>只能赋值给 void 和它们各自的类型</code>。</p>
<pre><code class="copyable">let a: undefined = undefined;
let b: null = null;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-7">Never</h3>
<ul>
<li>never 类型表示的是那些永不存在的值的类型，例如，never 类型是那些总是会抛出异常或根本就不会有返回值的函数表达式或箭头函数表达式的返回值类型。</li>
<li>返回never的函数必须存在无法达到的终点</li>
<li>使用 never 可避免出现新增联合类型没有对应的实现，<code>目的就是写出类型绝对安全的代码</code>。</li>
</ul>
<pre><code class="hljs language-typescript copyable" lang="typescript"><span class="hljs-keyword">type</span> Foo = <span class="hljs-built_in">string</span> | <span class="hljs-built_in">number</span>;

<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">controlFlowAnalysisWithNever</span>(<span class="hljs-params">foo: Foo</span>) </span>&#123;
  <span class="hljs-keyword">if</span> (<span class="hljs-keyword">typeof</span> foo === <span class="hljs-string">"string"</span>) &#123;
    <span class="hljs-comment">// 这里 foo 被收窄为 string 类型</span>
  &#125; <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span> (<span class="hljs-keyword">typeof</span> foo === <span class="hljs-string">"number"</span>) &#123;
    <span class="hljs-comment">// 这里 foo 被收窄为 number 类型</span>
  &#125; <span class="hljs-keyword">else</span> &#123;
    <span class="hljs-comment">// foo 在这里是 never</span>
    <span class="hljs-keyword">const</span> check: <span class="hljs-built_in">never</span> = foo;
  &#125;
&#125;
改为
<span class="hljs-keyword">type</span> Foo = <span class="hljs-built_in">string</span> | <span class="hljs-built_in">number</span> | <span class="hljs-built_in">boolean</span>;

<span class="copy-code-btn">复制代码</span></code></pre>
<p>controlFlowAnalysisWithNever中else 分支的 foo 类型会被收窄为 boolean 类型，导致无法赋值给 never 类型，这时就会产生一个编译错误。确保代码绝对安全。</p>
<h3 data-id="heading-8">null undefined  never</h3>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> a:number
<span class="hljs-built_in">console</span>.log(a)  <span class="hljs-comment">//有--strictNullChecks标记，编译不过，否则编译通过</span>


定义但未赋值就是<span class="hljs-literal">undefined</span>
<span class="hljs-keyword">var</span> a:number|<span class="hljs-literal">undefined</span>
<span class="hljs-built_in">console</span>.log(a)  <span class="hljs-comment">//undefined</span>

<span class="hljs-literal">null</span>同理
<span class="copy-code-btn">复制代码</span></code></pre>
<p>没有--strictNullChecks标记，null与 undefined可以赋值给任何类型。 null与 undefined是所有其它类型的一个有效值</p>
<h3 data-id="heading-9">枚举（enum）：支持数字的和字符串</h3>
<p>枚举类型是定义标识，用于定义一些固定值。</p>
<p>一般首字母大写</p>
<ol>
<li>数字枚举</li>
</ol>
<ul>
<li>不赋值默认就是索引值，注意索引是从0开始</li>
<li>其余的成员会从 初始化的值 开始自动增长</li>
<li>在有初始化值之前元素的第一个是0开始</li>
</ul>
<p>比如pay_status  0未支付  1支付  2交易成功</p>
<pre><code class="hljs language-js copyable" lang="js">enum Flag &#123;success=<span class="hljs-number">1</span>, error=<span class="hljs-number">0</span>&#125;
<span class="hljs-keyword">var</span> f:Flag = Flag.success
<span class="hljs-built_in">console</span>.log(f)  <span class="hljs-comment">//1</span>

enum Color&#123;red,blue,green&#125;
<span class="hljs-keyword">var</span> c:Color = Color.red
<span class="hljs-built_in">console</span>.log(c)  <span class="hljs-comment">//0   </span>
不赋值默认就是索引值，注意索引是从<span class="hljs-number">0</span>开始


enum Color&#123;red,blue=<span class="hljs-number">5</span>,green&#125;
<span class="hljs-keyword">var</span> c:Color = Color.red
<span class="hljs-keyword">var</span> c1:Color = Color.blue
<span class="hljs-keyword">var</span> c2:Color = Color.green
<span class="hljs-built_in">console</span>.log(c,c1,c2)  <span class="hljs-comment">//0   5  6</span>
green没有值以上一个为基准
<span class="copy-code-btn">复制代码</span></code></pre>
<ol start="2">
<li>字符串枚举：相比数字枚举更具有可读性</li>
</ol>
<p>字符串枚举里，<code>每个成员都必须用字符串字面量</code>，或另外一个字符串枚举成员进行初始化。</p>
<pre><code class="hljs language-js copyable" lang="js">enum Direction &#123;
    Up = <span class="hljs-string">"UP"</span>,
    Down = <span class="hljs-string">"DOWN"</span>,
    Left = <span class="hljs-string">"LEFT"</span>,
    Right = <span class="hljs-string">"RIGHT"</span>,
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ol start="3">
<li>异构枚举：可以混合number和string类型，但是一般不这么使用</li>
</ol>
<pre><code class="hljs language-js copyable" lang="js">enum Test &#123;
    No = <span class="hljs-number">0</span>,
    Yes = <span class="hljs-string">"YES"</span>,
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><code>有时候表示类型，有时候表示值</code></p>
<p>表示值:</p>
<pre><code class="hljs language-typescript copyable" lang="typescript"><span class="hljs-built_in">enum</span> Pos &#123;
  LEFT,
  RIGHT
&#125;

<span class="hljs-keyword">let</span> p : Pos = Pos.RIGHT
<span class="hljs-built_in">console</span>.log(p)  <span class="hljs-comment">//1</span>
  
<span class="hljs-built_in">enum</span> Pos &#123;
  LEFT = <span class="hljs-number">5</span>,
  RIGHT
&#125;

<span class="hljs-keyword">let</span> p : Pos = Pos.RIGHT
<span class="hljs-built_in">console</span>.log(p) <span class="hljs-comment">//6</span>
  
<span class="hljs-built_in">enum</span> Pos &#123;
  LEFT = <span class="hljs-string">'1'</span>,
  RIGHT = <span class="hljs-string">'2'</span>
&#125;

<span class="hljs-keyword">let</span> p : Pos = Pos.RIGHT
<span class="hljs-built_in">console</span>.log(p) <span class="hljs-comment">// '2'</span>
  
<span class="hljs-built_in">enum</span> Pos &#123;
  A,
  B,
  LEFT = <span class="hljs-string">'1'</span>,
  RIGHT = <span class="hljs-string">'2'</span>,
&#125;

<span class="hljs-keyword">let</span> p : Pos = Pos.RIGHT
<span class="hljs-built_in">console</span>.log(p)  <span class="hljs-comment">//'2'</span>
<span class="hljs-built_in">console</span>.log(Pos[<span class="hljs-number">0</span>]) <span class="hljs-comment">// 'A'</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>表示类型</p>
<pre><code class="hljs language-typescript copyable" lang="typescript"><span class="hljs-built_in">enum</span> ActiveType &#123;
  Active,
  Inactive
&#125;

<span class="hljs-keyword">type</span> KeyOfType = keyof <span class="hljs-keyword">typeof</span> ActiveType <span class="hljs-comment">// "Active" | "Inactive"</span>

<span class="hljs-keyword">let</span> test: KeyOfType =  <span class="hljs-string">'Active'</span> || <span class="hljs-string">'Inactive'</span>   <span class="hljs-comment">//ok</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-10">高级类型</h2>
<ul>
<li>交叉类型：是将多个类型合并为一个类型</li>
</ul>
<p>我们大多是在混入（mixins）或其它不适合典型面向对象模型的地方看到交叉类型的使用。 （在JavaScript里发生这种情况的场合很多！）</p>
<pre><code class="hljs language-js copyable" lang="js">Person & Serializable & Loggable
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>联合类型</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js">padding: string | number
<span class="copy-code-btn">复制代码</span></code></pre>
<p><a href="https://link.juejin.cn/?target=https%3A%2F%2Fwww.tslang.cn%2Fdocs%2Fhandbook%2Fadvanced-types.html" target="_blank" rel="nofollow noopener noreferrer" title="https://www.tslang.cn/docs/handbook/advanced-types.html" ref="nofollow noopener noreferrer">www.tslang.cn/docs/handbo…</a></p>
<ul>
<li>类型保护与区分类型</li>
</ul>
<h3 data-id="heading-11">is： 此关键字用作用户类型防护，用来告诉 TS 如何辨别类型</h3>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-keyword">interface</span> Animal &#123;
  <span class="hljs-attr">walk</span>: <span class="hljs-function">() =></span> &#123;&#125;
&#125;
<span class="hljs-comment">//  cat is Animal用来告诉用户TS，cat是Animal类型</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">isAnimal</span>(<span class="hljs-params">cat: <span class="hljs-built_in">any</span></span>): <span class="hljs-title">cat</span> <span class="hljs-title">is</span> <span class="hljs-title">Animal</span> </span>&#123;
  <span class="hljs-keyword">return</span> (cat <span class="hljs-keyword">as</span> Animal).walk !== <span class="hljs-literal">undefined</span>;
&#125;

<span class="hljs-keyword">let</span> cat = &#123;&#125; 

<span class="hljs-keyword">if</span> (isAnimal(cat)) &#123;
  cat.walk() <span class="hljs-comment">// OK</span>
&#125; <span class="hljs-keyword">else</span> &#123;
  pet.walk() <span class="hljs-comment">// 类型“Bird”上不存在属性“swim”</span>
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>其他可用来判断类型的关键字还有 typeof，instanceof, in 等等。</p>
<h3 data-id="heading-12">typeOf</h3>
<p>typeof类型保护*只有两种形式能被识别： typeof v === "typename"和 typeof v !== "typename"， "typename"必须是 "number"， "string"， "boolean"或 "symbol"。 但是TypeScript并不会阻止你与其它字符串比较，语言不会把那些表达式识别为类型保护。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">padLeft</span>(<span class="hljs-params">value: string, padding: string | number</span>) </span>&#123;
<span class="hljs-comment">// 不必定义一个函数来判断类型是否是原始类型</span>
    <span class="hljs-keyword">if</span> (<span class="hljs-keyword">typeof</span> padding === <span class="hljs-string">"number"</span>) &#123;
        <span class="hljs-keyword">return</span> <span class="hljs-built_in">Array</span>(padding + <span class="hljs-number">1</span>).join(<span class="hljs-string">" "</span>) + value;
    &#125;
    <span class="hljs-keyword">if</span> (<span class="hljs-keyword">typeof</span> padding === <span class="hljs-string">"string"</span>) &#123;
        <span class="hljs-keyword">return</span> padding + value;
    &#125;
    <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> <span class="hljs-built_in">Error</span>(<span class="hljs-string">`Expected string or number, got '<span class="hljs-subst">$&#123;padding&#125;</span>'.`</span>);
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>instanceof</li>
</ul>
<p>instanceof类型保护是通过构造函数来细化类型的一种方式
instanceof的右侧要求是一个构造函数，TypeScript将细化为：</p>
<p>此构造函数的 prototype属性的类型，如果它的类型不为 any的话
构造签名所返回的类型的联合</p>
<h3 data-id="heading-13">可选参数和可选属性 ：<code>一定是可选，也就是带?</code></h3>
<p>使用了 --strictNullChecks，可选参数会被自动地加上 | undefined</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">f</span>(<span class="hljs-params">x: number, y?: number</span>) </span>&#123;
    <span class="hljs-keyword">return</span> x + (y || <span class="hljs-number">0</span>);
&#125;
f(<span class="hljs-number">1</span>, <span class="hljs-number">2</span>);
f(<span class="hljs-number">1</span>);
f(<span class="hljs-number">1</span>, <span class="hljs-literal">undefined</span>);
f(<span class="hljs-number">1</span>, <span class="hljs-literal">null</span>); <span class="hljs-comment">// error, 'null' is not assignable to 'number | undefined'</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>可选属性也会有同样的处理：</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">C</span> </span>&#123;
    <span class="hljs-attr">a</span>: number;
    b?: number;
&#125;
<span class="hljs-keyword">let</span> c = <span class="hljs-keyword">new</span> C();
c.a = <span class="hljs-number">12</span>;
c.a = <span class="hljs-literal">undefined</span>; <span class="hljs-comment">// error, 'undefined' is not assignable to 'number'</span>
c.b = <span class="hljs-number">13</span>;
c.b = <span class="hljs-literal">undefined</span>; <span class="hljs-comment">// ok</span>
c.b = <span class="hljs-literal">null</span>; <span class="hljs-comment">// error, 'null' is not assignable to 'number | undefined'</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-14">使用类型断言手动去除null或 undefined，语法是添加 !后缀</h3>
<pre><code class="hljs language-js copyable" lang="js">identifier!
从 identifier的类型里去除了 <span class="hljs-literal">null</span>和 <span class="hljs-literal">undefined</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-15">类型别名type：会给一个类型起个新名字</h3>
<ol>
<li>
<p>类型别名有时和接口很像，但是<code>可以作用于原始值，联合类型，元组以及其它任何你需要手写的类型</code>。</p>
</li>
<li>
<p>类型别名也<code>可以是泛型</code> - 我们可以添加类型参数并且在别名声明的右侧传入</p>
</li>
</ol>
<pre><code class="hljs language-js copyable" lang="js">type Container<T> = &#123; <span class="hljs-attr">value</span>: T &#125;;
<span class="copy-code-btn">复制代码</span></code></pre>
<ol start="3">
<li>可以使用类型别名来在属性里<code>引用自己</code></li>
</ol>
<pre><code class="hljs language-js copyable" lang="js">type Tree<T> = &#123;
    <span class="hljs-attr">value</span>: T;
    left: Tree<T>;
    right: Tree<T>;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ol start="4">
<li><code>注：类型别名不能出现在声明右侧的任何地方</code></li>
</ol>
<pre><code class="hljs language-js copyable" lang="js">type Yikes = <span class="hljs-built_in">Array</span><Yikes>; <span class="hljs-comment">// error</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-16">接口interface 和 类型别名type的区别</h3>
<ol>
<li><code>interface创建了一个新的名字</code>，可以在其它任何地方使用。 <code>type不创建新名字</code></li>
</ol>
<p>比如，错误信息就不会使用别名。</p>
<pre><code class="hljs language-js copyable" lang="js">type Alias = &#123; <span class="hljs-attr">num</span>: number &#125;
interface Interface &#123;
    <span class="hljs-attr">num</span>: number;
&#125;
declare <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">aliased</span>(<span class="hljs-params">arg: Alias</span>): <span class="hljs-title">Alias</span></span>;
declare <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">interfaced</span>(<span class="hljs-params">arg: Interface</span>): <span class="hljs-title">Interface</span></span>;

在编译器中将鼠标悬停在 interfaced上，显示它返回的是 Interface

悬停在 aliased上时，显示的却是对象字面量类型
<span class="copy-code-btn">复制代码</span></code></pre>
<ol start="2">
<li><code>type不能被 extends和 implements</code>（自己也不能 extends和 implements其它类型）。</li>
</ol>
<p>因为 软件中的对象应该对于扩展是开放的，但是对于修改是封闭的，你应该尽量去使用接口代替类型别名。</p>
<ol start="3">
<li>如果你无法通过interface来描述一个类型并且需要使用联合类型或元组类型，这时通常会使用type。</li>
</ol>
<blockquote>
<p>总结描述多种类型的方式：</p>
<ul>
<li>interface</li>
<li>联合类型</li>
<li>交叉类型</li>
<li>元组</li>
<li>type</li>
</ul>
</blockquote>
<p>type
可以通过多种方式得到新的类型
typeof  Tuple  对象</p>
<p>interface
类型可以合并</p>
<h3 data-id="heading-17">索引类型查询操作符 keyof</h3>
<p>用法：keyof T</p>
<p>索引访问操作符T[K]</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">getProperty</span><<span class="hljs-title">T</span>, <span class="hljs-title">K</span> <span class="hljs-title">extends</span> <span class="hljs-title">keyof</span> <span class="hljs-title">T</span>>(<span class="hljs-params">o: T, name: K</span>): <span class="hljs-title">T</span>[<span class="hljs-title">K</span>] </span>&#123;
    <span class="hljs-keyword">return</span> o[name]; <span class="hljs-comment">// o[name] is of type T[K]</span>
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="copyable">type Teacher = &#123;
  id: string;
  name: string;
&#125;;

type TeacherKeys = keyof Teacher; //"id" | "name"

let a: TeacherKeys =  'id' || 'name'  // ok
let a: TeacherKeys =  'other'  //error
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-18">keyof和 T[K]与字符串索引签名联合使用，keyof T会是 string`，并且 T[string]为索引签名的类型：</h3>
<pre><code class="hljs language-js copyable" lang="js">interface <span class="hljs-built_in">Map</span><T> &#123;
    [key: string]: T;
&#125;
<span class="hljs-keyword">let</span> keys: keyof <span class="hljs-built_in">Map</span><number>; <span class="hljs-comment">// string</span>
<span class="hljs-keyword">let</span> value: <span class="hljs-built_in">Map</span><number>[<span class="hljs-string">'foo'</span>]; <span class="hljs-comment">// number</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>keyof还可以做映射类型，具体可以看官网 <a href="https://link.juejin.cn/?target=https%3A%2F%2Fwww.tslang.cn%2Fdocs%2Fhandbook%2Fadvanced-types.html" target="_blank" rel="nofollow noopener noreferrer" title="https://www.tslang.cn/docs/handbook/advanced-types.html" ref="nofollow noopener noreferrer">www.tslang.cn/docs/handbo…</a></p>
<h3 data-id="heading-19">keyof typeof联合使用</h3>
<pre><code class="copyable">enum ActiveType &#123;
  Active,
  Inactive
&#125;

type KeyOfType = keyof typeof ActiveType // "Active" | "Inactive"
<span class="copy-code-btn">复制代码</span></code></pre>
<p>如果要获取 enum 的 key 类型，需要先把它当成值，用 typeof 再用 keyof。</p>
<pre><code class="hljs language-typescript copyable" lang="typescript"><span class="hljs-built_in">enum</span> ActiveType &#123;
  Active,
  Inactive
&#125;

<span class="hljs-keyword">type</span> KeyOfType = keyof ActiveType <span class="hljs-comment">// "toString" | "toFixed" | "toExponential" | "toPrecision" | "valueOf" | "toLocaleString"</span>

<span class="hljs-keyword">let</span> test : KeyOfType = <span class="hljs-string">'toString'</span>
<span class="hljs-built_in">console</span>.log(test) <span class="hljs-comment">//'toString'</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-20">类型断言2种方式</h3>
<ul>
<li>
<ol>
<li>尖括号</li>
</ol>
</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> someValue: any = <span class="hljs-string">"this is a string"</span>;

<span class="hljs-keyword">let</span> strLength: number = (<string>someValue).length;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>
<ol start="2">
<li>as语法</li>
</ol>
</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> someValue: any = <span class="hljs-string">"this is a string"</span>;

<span class="hljs-keyword">let</span> strLength: number = (someValue <span class="hljs-keyword">as</span> string).length;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>两种形式是等价的。 至于使用哪个大多数情况下是凭个人喜好；然而，<code>当你在TypeScript里使用JSX时，只有 as语法断言是被允许的</code>。</p>
<h2 data-id="heading-21">接口</h2>
<p>接口的作用，在面向对象的编程中，接口是一种规范的定义，起到一种限制和规范的作用。</p>
<p>可以对批量方法进行约束
<a href="https://link.juejin.cn/?target=https%3A%2F%2Fwww.tslang.cn%2Fdocs%2Fhandbook%2Finterfaces.html" target="_blank" rel="nofollow noopener noreferrer" title="https://www.tslang.cn/docs/handbook/interfaces.html" ref="nofollow noopener noreferrer">www.tslang.cn/docs/handbo…</a>
可选属性的好处之一是可以对可能存在的属性进行预定义，好处之二是可以捕获引用了不存在的属性时的错误。</p>
<p>把整个ReadonlyArray赋值到一个普通数组也是不可以的</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> a: number[] = [<span class="hljs-number">1</span>, <span class="hljs-number">2</span>, <span class="hljs-number">3</span>, <span class="hljs-number">4</span>];
<span class="hljs-keyword">let</span> ro: ReadonlyArray<number> = a;
a = ro; <span class="hljs-comment">// error!</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>readonly vs const</p>
<p>最简单判断该用readonly还是const的方法是看要把它做为变量使用还是做为一个属性。 做为变量使用的话用 const，若做为属性则使用readonly</p>
<ul>
<li>额外的属性检查</li>
</ul>
<p>绕开定义出错的方式：</p>
<ol>
<li>断言</li>
<li>索引签名</li>
<li>将这个对象赋值给一个另一个变量</li>
</ol>
<p>类型断言能绕开的问题：</p>
<ul>
<li>可索引的类型（可以对对象和数组的约束）</li>
</ul>
<p>TS支持两种索引签名：字符串和数字。 可以同时使用两种类型的索引，但是<code>数字索引的返回值必须是字符串索引返回值类型的子类型</code>。 这是因为当使用 number来索引时，JavaScript会将它转换成string然后再去索引对象。 也就是说用 100（一个number）去索引等同于使用"100"（一个string）去索引，因此两者需要保持一致。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Animal</span> </span>&#123;
    <span class="hljs-attr">name</span>: string;
&#125;
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Dog</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Animal</span> </span>&#123;
    <span class="hljs-attr">breed</span>: string;
&#125;

<span class="hljs-comment">// 错误：使用数值型的字符串索引，有时会得到完全不同的Animal!</span>
interface NotOkay &#123;
    [x: number]: Animal;
    [x: string]: Dog;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>字符串索引签名能够很好的描述dictionary模式，并且它们也会确保所有属性与其返回值类型相匹配。</p>
<pre><code class="hljs language-js copyable" lang="js">interface NumberDictionary &#123;
  [index: string]: number;
  length: number;    <span class="hljs-comment">// 可以，length是number类型</span>
  name: string       <span class="hljs-comment">// 错误，`name`的类型与索引类型返回值的类型不匹配</span>
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>可以将索引签名设置为只读</p>
<pre><code class="hljs language-js copyable" lang="js">interface ReadonlyStringArray &#123;
    readonly [index: number]: string;
&#125;
<span class="hljs-keyword">let</span> myArray: ReadonlyStringArray = [<span class="hljs-string">"Alice"</span>, <span class="hljs-string">"Bob"</span>];
myArray[<span class="hljs-number">2</span>] = <span class="hljs-string">"Mallory"</span>; <span class="hljs-comment">// error!</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>接口继承接口</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js">一个接口可以继承多个接口，创建出多个接口的合成接口。
interface Shape &#123;
    <span class="hljs-attr">color</span>: string;
&#125;
interface PenStroke &#123;
    <span class="hljs-attr">penWidth</span>: number;
&#125;
interface Square <span class="hljs-keyword">extends</span> Shape, PenStroke &#123;
    <span class="hljs-attr">sideLength</span>: number;
&#125;
<span class="hljs-keyword">let</span> square = <Square>&#123;&#125;;
square.color = <span class="hljs-string">"blue"</span>;
square.sideLength = <span class="hljs-number">10</span>;
square.penWidth = <span class="hljs-number">5.0</span>;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>混合类型</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js">interface Counter &#123;
    (start: number): string;
    interval: number;
    reset(): <span class="hljs-keyword">void</span>;
&#125;

<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">getCounter</span>(<span class="hljs-params"></span>): <span class="hljs-title">Counter</span> </span>&#123;&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>接口继承类</li>
</ul>
<p>当接口继承了一个类类型时，它会继承类的成员但不包括其实现。 就好像接口声明了所有类中存在的成员，但并没有提供具体实现一样。 接口同样会继承到类的private和protected成员。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Control</span> </span>&#123;
    private state: any;
&#125;

interface SelectableControl <span class="hljs-keyword">extends</span> Control &#123;
    select(): <span class="hljs-keyword">void</span>;
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Button</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Control</span> <span class="hljs-title">implements</span> <span class="hljs-title">SelectableControl</span> </span>&#123;
    <span class="hljs-function"><span class="hljs-title">select</span>(<span class="hljs-params"></span>)</span> &#123; &#125;
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">TextBox</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Control</span> </span>&#123;
    <span class="hljs-function"><span class="hljs-title">select</span>(<span class="hljs-params"></span>)</span> &#123; &#125;
&#125;

<span class="hljs-comment">// 错误：“Image”类型缺少“state”属性。</span>
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Image</span> <span class="hljs-title">implements</span> <span class="hljs-title">SelectableControl</span> </span>&#123;
    <span class="hljs-function"><span class="hljs-title">select</span>(<span class="hljs-params"></span>)</span> &#123; &#125;
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Location</span> </span>&#123;

&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-22">类</h2>
<p><a href="https://link.juejin.cn/?target=https%3A%2F%2Fwww.tslang.cn%2Fdocs%2Fhandbook%2Fclasses.html" target="_blank" rel="nofollow noopener noreferrer" title="https://www.tslang.cn/docs/handbook/classes.html" ref="nofollow noopener noreferrer">www.tslang.cn/docs/handbo…</a>
重写父类的方法</p>
<p>protected方法;不能在 Person类外使用 name，但是我们仍然可以通过 Employee类的实例方法访问，因为 Employee是由 Person派生而来的。</p>
<ul>
<li><code>抽象类中的抽象方法不包含具体实现并且必须在派生类中实现</code>。 抽象方法的语法与接口方法相似。 两者都是定义方法签名但不包含方法体。 然而，抽象方法必须包含 abstract关键字并且可以包含访问修饰符。</li>
</ul>
<p>如果有抽象方法，必须要有抽象类。抽象类的子类必须实现抽象类里面的抽象方法。</p>
<ul>
<li>把类当做接口使用</li>
</ul>
<p>为什么要静态方法？ 一般用得不多
静态方法里面没法直接调用类里面的实例属性。可以直接调用类里面的静态属性。</p>
<p><code>注意：类类型接口：对类的约束 和 抽象类有点相似</code></p>
<h2 data-id="heading-23">函数</h2>
<ul>
<li>可选参数和默认参数</li>
</ul>
<p><code>可选参数必须跟在必须参数后面</code></p>
<p>与普通可选参数不同的是，<code>带默认值的参数不需要放在必须参数的后面。 如果带默认值的参数出现在必须参数前面，用户必须明确的传入 undefined值来获得默认值</code>。</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">buildName</span>(<span class="hljs-params">firstName = <span class="hljs-string">"Will"</span>, lastName: string</span>) </span>&#123;
    <span class="hljs-keyword">return</span> firstName + <span class="hljs-string">" "</span> + lastName;
&#125;

<span class="hljs-keyword">let</span> result1 = buildName(<span class="hljs-string">"Bob"</span>);                  <span class="hljs-comment">// error, too few parameters</span>
<span class="hljs-keyword">let</span> result2 = buildName(<span class="hljs-string">"Bob"</span>, <span class="hljs-string">"Adams"</span>, <span class="hljs-string">"Sr."</span>);  <span class="hljs-comment">// error, too many parameters</span>
<span class="hljs-keyword">let</span> result3 = buildName(<span class="hljs-string">"Bob"</span>, <span class="hljs-string">"Adams"</span>);         <span class="hljs-comment">// okay and returns "Bob Adams"</span>
<span class="hljs-keyword">let</span> result4 = buildName(<span class="hljs-literal">undefined</span>, <span class="hljs-string">"Adams"</span>);     <span class="hljs-comment">// okay and returns "Will Adams"</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>剩余参数</li>
</ul>
<p>剩余参数会被当做个数不限的可选参数。 可以一个都没有，同样也可以有任意个。</p>
<ul>
<li>箭头函数</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Handler</span> </span>&#123;
    <span class="hljs-attr">info</span>: string;
    onClickGood = <span class="hljs-function">(<span class="hljs-params">e: Event</span>) =></span> &#123; <span class="hljs-built_in">this</span>.info = e.message &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>函数重载</li>
</ul>
<p>在定义重载的时候，一定要把最精确的定义放在最前面</p>
<h2 data-id="heading-24">泛型（类型变量T）</h2>
<p>泛型就是解决<code>类 接口 方法的复用性、以及对不确定数据类型的支持，还有类型校验</code>。any没有类型校验。</p>
<p>种类：泛型类  泛型函数 泛型接口</p>
<ul>
<li>
<p>泛型是一种函数，使用的T是类型变量</p>
</li>
<li>
<p>为什么使用泛型，不使用any？</p>
</li>
</ul>
<p>不会丢失信息。</p>
<p>使用any类型会导致这个函数可以接收任何类型的arg参数，这样就丢失了一些信息：传入的类型与返回的类型应该是相同的。如果我们传入一个数字，我们只知道任何类型的值都有可能被返回。因此，我们需要一种方法使返回值的类型与传入参数的类型是相同的。也就是使用了泛型（类型变量，只用于表示类型而不是值）</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">identity</span><<span class="hljs-title">T</span>>(<span class="hljs-params">arg: T</span>): <span class="hljs-title">T</span> </span>&#123;
    <span class="hljs-keyword">return</span> arg;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>泛型函数后，可以用两种方法使用：</li>
</ul>
<ol>
<li>传入所有的参数，包含类型参数：</li>
</ol>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> output = identity<string>(<span class="hljs-string">"myString"</span>);  <span class="hljs-comment">// type of output will be 'string'</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><code>明确的指定了T是string类型</code>，并做为一个参数传给函数，<code>使用了<>括起来而不是()</code></p>
<ol start="2">
<li><code>更普遍</code>。利用了类型推论 -- 即编译器会根据传入的参数自动地帮助我们确定T的类型</li>
</ol>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> output = identity(<span class="hljs-string">"myString"</span>);  <span class="hljs-comment">// type of output will be 'string'</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p><code>类型推论帮助我们保持代码精简和高可读性</code>。如果编译器不能够自动地推断出类型的话，只能像上面那样明确的传入T的类型，在一些复杂的情况下，这是可能出现的。</p>
<p>泛型的应用场景  啥时候使用索引签名  可选参数</p>
<ul>
<li>
<p>使用泛型变量</p>
</li>
<li>
<p>泛型类型</p>
</li>
<li>
<p>泛型类</p>
</li>
</ul>
<p>类有两部分：静态部分和实例部分。 泛型类指的是实例部分的类型，所以类的静态属性不能使用这个泛型类型。</p>
<ul>
<li>泛型约束</li>
</ul>
<p>extends<br>
在泛型约束中使用类型参数
在泛型里使用类类型</p>
<ul>
<li>泛型接口</li>
</ul>
<p>写法一：</p>
<pre><code class="hljs language-js copyable" lang="js">interface Config&#123;
    <T>(value:T):T
&#125;
<span class="hljs-keyword">var</span> getData:Config=<span class="hljs-function"><span class="hljs-keyword">function</span><<span class="hljs-title">T</span>>(<span class="hljs-params">value；T</span>)：<span class="hljs-title">T</span></span>&#123;
    <span class="hljs-keyword">return</span> value
&#125;
getData<string>(<span class="hljs-string">'张三'</span>)
<span class="copy-code-btn">复制代码</span></code></pre>
<p>写法二：</p>
<pre><code class="hljs language-js copyable" lang="js">interface Config<T>&#123;
    (value:T):T
&#125;
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">getData</span><<span class="hljs-title">T</span>>(<span class="hljs-params">value；T</span>)：<span class="hljs-title">T</span></span>&#123;
    <span class="hljs-keyword">return</span> value
&#125;
<span class="hljs-keyword">var</span> myGeData:Config<string> = getData
myGeData(<span class="hljs-string">'张三'</span>)
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>把类作为参数类型的泛型类</li>
</ul>
<ol>
<li>定义类</li>
<li>把类作为参数来约束数据传入的类型</li>
</ol>
<p>案例：
定义一个User的类这个类的作用就是映射数据库字段，然后定义一个MysqlDb的类用于操作数据库，然后把User类作为参数传入到MysqlDb中</p>
<p>每操作一数据表，就得重新传入数据类型，所以最好用泛型，造成代码重复</p>
<pre><code class="hljs language-js copyable" lang="js">泛型类

<span class="hljs-comment">//操作数据库的泛型类</span>
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MysqlDb</span><<span class="hljs-title">T</span>></span>&#123;
    add(info:T):boolean&#123;
        <span class="hljs-built_in">console</span>.log(info)
        <span class="hljs-keyword">return</span> <span class="hljs-literal">true</span>
    &#125;
    update(info:T,<span class="hljs-attr">id</span>:number):boolean&#123;&#125;
&#125;

<span class="hljs-comment">//定义一个User类和数据库映射</span>
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">user</span></span>&#123;
    <span class="hljs-attr">username</span>:string|<span class="hljs-literal">undefined</span>
&#125;
<span class="hljs-keyword">var</span> u = <span class="hljs-keyword">new</span> User()
u.username=<span class="hljs-string">'张三'</span>

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">user1</span></span>&#123;
    <span class="hljs-attr">username</span>:string|<span class="hljs-literal">undefined</span>
&#125;
<span class="hljs-keyword">var</span> u1 = <span class="hljs-keyword">new</span> User1()
u1.username=<span class="hljs-string">'张三'</span>

<span class="hljs-keyword">var</span> db = <span class="hljs-keyword">new</span> MysqlDb<User>()
db.add(u)
db.add(u1)

。。。可以添加多个
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-25">命名空间</h2>
<p>主要用于组织代码，避免命名冲突</p>
<pre><code class="hljs language-js copyable" lang="js">namespace A&#123;
    <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Dog</span></span>&#123;&#125;
&#125;
<span class="hljs-keyword">let</span> g = <span class="hljs-keyword">new</span> A.Dog()
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-26">命名空间和模块的区别</h2>
<p>命名空间：主要用于组织代码，避免命名冲突
模块：侧重代码的复用，一个模块里可能会有多个吗命名空间。</p>
<h2 data-id="heading-27">索引签名</h2>
<p>利用<code>「索引签名」</code>方式可以<code>为对象动态分配属性</code>(字符串键名和任何类型键值)，类似于js中的let obj = &#123;&#125;,obj.name = 'hannie'</p>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-keyword">interface</span> LooseObj &#123;
  [key: <span class="hljs-built_in">string</span>]: <span class="hljs-built_in">any</span>
&#125;

<span class="hljs-keyword">let</span> developer: LooseObj = &#123;&#125;;
developer.name = <span class="hljs-string">"hannie"</span>;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><code>「索引签名」</code>可以用来定义对象内的属性、值的类型，例如定义一个 React 组件，允许 Props 可以传任意 key 为 string，value 为 number 的 props。</p>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-keyword">interface</span> Props &#123;
  [key: <span class="hljs-built_in">string</span>]: <span class="hljs-built_in">number</span>
&#125;

<Component count=&#123;<span class="hljs-number">1</span>&#125; /> <span class="hljs-comment">// OK</span>
<span class="xml"><span class="hljs-tag"><<span class="hljs-name">Component</span> <span class="hljs-attr">count</span>=<span class="hljs-string">&#123;true&#125;</span> /></span></span> <span class="hljs-comment">// Error</span>
<span class="xml"><span class="hljs-tag"><<span class="hljs-name">Component</span> <span class="hljs-attr">count</span>=<span class="hljs-string">&#123;</span>'<span class="hljs-attr">1</span>'&#125; /></span></span> <span class="hljs-comment">// Error</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-28">如何为对象动态分配属性</h2>
<ul>
<li>
<ol>
<li>索引签名</li>
</ol>
</li>
</ul>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-keyword">interface</span> LooseObj &#123;
  [key: <span class="hljs-built_in">string</span>]: <span class="hljs-built_in">any</span>
&#125;

<span class="hljs-keyword">let</span> developer: LooseObj = &#123;&#125;;
developer.name = <span class="hljs-string">"hannie"</span>;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>
<ol start="2">
<li>定义可选的属性</li>
</ol>
</li>
</ul>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-keyword">interface</span> Developer &#123;
  <span class="hljs-attr">name</span>: <span class="hljs-built_in">string</span>;
  age?: <span class="hljs-built_in">number</span>;
  [key: <span class="hljs-built_in">string</span>]: <span class="hljs-built_in">any</span>
&#125;

<span class="hljs-keyword">let</span> developer: Developer = &#123; <span class="hljs-attr">name</span>: <span class="hljs-string">"hannie"</span> &#125;;
developer.age = <span class="hljs-number">18</span>;
developer.city = <span class="hljs-string">"beijing"</span>;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>
<ol start="3">
<li>Record<keysType,valuesType>：定义键类型为 keysType、值类型为 valuesType 的对象类型</li>
</ol>
</li>
</ul>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-keyword">interface</span> Developer <span class="hljs-keyword">extends</span> Record<string, any> &#123;
  <span class="hljs-attr">name</span>: <span class="hljs-built_in">string</span>;
  age?: <span class="hljs-built_in">number</span>;
&#125;

<span class="hljs-keyword">let</span> developer: Developer = &#123; <span class="hljs-attr">name</span>: <span class="hljs-string">"hannie"</span> &#125;;
developer.age = <span class="hljs-number">18</span>;
developer.city = <span class="hljs-string">"beijing"</span>;
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="copyable">泛型的反向推导
type V<T> = T
type NumberValue = V<number>

var a:NumberValue = 1
console.log(a)

索引签名
type Test = &#123;
  foo: number;
  bar: string
&#125;

type N = Test['foo'] // number
// 类型可以重新定义吗？




条件类型
type IsNumber<T> = T extends number ? number : string;

type A = IsNumber<2> // yes
type B = IsNumber<'3'> // no

let b:B = '2'
console.log(b)


type TypeName<T> = T extends string
  ? "string"
  : T extends boolean
      ? "boolean"
      : "object";

type T0 = TypeName<string>; // "string"
type T1 = TypeName<"a">; // "string"
type T2 = TypeName<true>; // "boolean"
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="copyable">  type Value<T> = T

type NumberValue = Value<number>

type V<T> = T
type NumberValue1 = V<number>

type Test = &#123;
  foo: number;
  bar: string
&#125;

type N = Test['foo'] // number
// 类型可以重新定义吗？

var a:NumberValue = 1
console.log(a)
type IsNumber<T> = T extends number ? number : string;

type A = IsNumber<2> // yes
type B = IsNumber<'3'> // no

let b:B = '2'
console.log(b)


type TypeName<T> = T extends string
  ? "string"
  : T extends boolean
      ? "boolean"
      : "object";

type T0 = TypeName<string>; // "string"
type T1 = TypeName<"a">; // "string"
type T2 = TypeName<true>; // "boolean"


<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-29">其他细节</h2>
<h3 data-id="heading-30">readonly vs const</h3>
<p>最简单判断该用readonly还是const的方法是看要把它做为变量使用还是做为一个属性。 做为变量使用的话用const，若做为属性则使用readonly。</p>
<p>const使用场景：如果一个变量不需要对它写入，那么其它使用这些代码的人也不能够写入它们</p>
<p>对象展开还有其它一些意想不到的限制。 首先，它仅包含对象 自身的可枚举属性。 大体上是说当你展开一个对象实例时，你会丢失其方法</p>
<pre><code class="copyable">class C &#123;
  p = 12;
  m() &#123;
  &#125;
&#125;
let c = new C();
let clone = &#123; ...c &#125;;
clone.p; // ok
clone.m(); // error!
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-31">&#123;&#125;|object|Object</h3>
<p>Object 接口定义了 Object.prototype 原型对象上的属性</p>
<pre><code class="copyable">const proto = &#123;&#125;;

Object.create(proto);     // OK
Object.create(null);      // OK
  
Object.create(undefined); // // Object prototype may only be an Object or null: undefined
Object.create(11);      // Object prototype may only be an Object or null: 11 
Object.create(true);      // Error
Object.create("oops");    // Error

<span class="copy-code-btn">复制代码</span></code></pre>
<p>object 表示的是常规的 Javascript 对象类型，非基础数据类型。</p>
<pre><code class="copyable">declare function create(o: object): void;
create(&#123; prop: 0 &#125;); // OK
create(null); // Error
create(undefined); // Error
create(42); // Error
create("string"); // Error
create(false); // Error
create(&#123;
  toString() &#123;
    return 3;
  &#125;,
&#125;); // OK
<span class="copy-code-btn">复制代码</span></code></pre>
<p>报错，只能对对象创建</p>
<p>&#123;&#125; 表示的非 null，非 undefined 的任意类型。</p>
<pre><code class="copyable">  interface User &#123;
  id: string
&#125;
 
interface User &#123;
  name: string
&#125;

interface User &#123;
  other: object
&#125; 
const user = &#123;&#125; as User
 
console.log(user.id);
console.log(user.name);
console.log(user.other);
user.other = &#123;a:1&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="copyable">interface User &#123;
  other: &#123;&#125;
&#125; 
user.other = null  报错
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="copyable">  interface User &#123;
  other: Object
&#125; 
const user = &#123;&#125; as User
user.other = &#123;toString()&#123;return 1&#125;&#125;  //报错
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="copyable">type User2 = string
let a = '' as User2
a = '2'
  
let isDone: boolean = false;
var a : string = '1'
let b : number = 1
  

<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-32">总结</h2>
<p>可以使用泛型来创建可重用的组件，一个组件可以支持多种类型的数据。 这样用户就可以以自己的数据类型来使用组件</p>
<p>总结this箭头函数实例可以推翻结果</p>
<p>在TypeScript里使用JSX时，只有as语法断言是被允许的。</p>
<p>尽可能地使用let来代替var</p>
<p><a href="https://link.juejin.cn/?target=https%3A%2F%2Ftypescript.bootcss.com%2Ffunctions.html" target="_blank" rel="nofollow noopener noreferrer" title="https://typescript.bootcss.com/functions.html" ref="nofollow noopener noreferrer">typescript.bootcss.com/functions.h…</a></p>
<h2 data-id="heading-33">类型键入</h2>
<p>类型键入允许 Typescript 像对象取属性值一样使用类型</p>
<pre><code class="copyable">type Teacher = &#123;
  id: string
  sthdentList: &#123;
    fristName: string
    lastName: string
  &#125;[]
&#125;

type UserIdType = Teacher['id'] // string
type SthdentList = Teacher['sthdentList'] // &#123; fristName: string; lastName: string; &#125;[]
type Friend = SthdentList[number] // &#123; fristName: string; lastName: string; &#125;  
<span class="copy-code-btn">复制代码</span></code></pre>
<p>UserIdType、SthdentList、Friend是得到的新类型</p>
<pre><code class="copyable">type Tuple = [number, string]
type First = Tuple[0] // number
type Second = Tuple[1] // string
<span class="copy-code-btn">复制代码</span></code></pre>
<p>同样也可以用于元祖</p>
<h2 data-id="heading-34">总结</h2>
<p>当类型不确定的情况下，考虑使用泛型</p>
<p>日常开发中经常用到的泛型有 Promise、Array、React.Component 等等。</p>
<p>同泛型一样，一般小项目用不到装饰器，但是看别人的框架要能看懂。</p>
<p>any放弃了类型检测，泛型可以限制传入什么类型并返回什么类型，但是可以支持不特定的数据类型。</p>
<p>开发的过程中可以尝试使用  keyof  enum  Tuple 类型判断 type interface 函数 class，泛型要能看得懂</p>
<p><a href="https://juejin.im/post/6876981358346895368" target="_blank" title="https://juejin.im/post/6876981358346895368">juejin.im/post/687698…</a></p>
<p><a href="https://juejin.im/post/6871752423577223176" target="_blank" title="https://juejin.im/post/6871752423577223176">juejin.im/post/687175…</a></p></div>  
</div>
            
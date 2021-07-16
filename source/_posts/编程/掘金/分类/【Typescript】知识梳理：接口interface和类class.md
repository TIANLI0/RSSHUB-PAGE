
---
title: '【Typescript】知识梳理：接口interface和类class'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=4502'
author: 掘金
comments: false
date: Thu, 15 Jul 2021 04:50:42 GMT
thumbnail: 'https://picsum.photos/400/300?random=4502'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><p>在面向对象语言中，接口（Interfaces）是对行为的抽象，而具体如何行动需要由类（classes）去实现（implement）。</p>
<h2 data-id="heading-0">接口interface</h2>
<p>接口interface是一系列抽象方法的声明，是一些方法特征的集合，这些方法都应该是抽象的，需要由具体的类去实现，然后第三方就可以通过这组抽象方法调用，让具体的类执行具体的方法。</p>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-keyword">interface</span> Test &#123;
    <span class="hljs-attr">name</span>: <span class="hljs-built_in">string</span>;
    age?: <span class="hljs-built_in">number</span>;<span class="hljs-comment">//?:可选属性</span>
    <span class="hljs-keyword">readonly</span> id: <span class="hljs-built_in">number</span>;<span class="hljs-comment">//readonly只读属性，不可赋值</span>
    [index:<span class="hljs-built_in">number</span>]:<span class="hljs-built_in">string</span> <span class="hljs-comment">//接口中可以将数组的索引值和元素设置为不同类型，索引值可以是数字或字符串。</span>
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-1">类class</h2>
<p>类描述了所创建的对象共同的属性和方法。</p>
<p>定义类的关键字为 class，后面紧跟类名，类可以包含以下几个模块（类的数据成员）：</p>
<ul>
<li><strong>字段</strong> − 字段是类里面声明的变量。字段表示对象的有关数据。</li>
<li><strong>构造函数</strong> − 类实例化时调用，可以为类的对象分配内存。</li>
<li><strong>方法</strong> − 方法为对象要执行的操作。</li>
</ul>
<h3 data-id="heading-2">创建类的数据成员和实例化对象</h3>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Car</span> </span>&#123; 
   <span class="hljs-comment">// 字段</span>
   <span class="hljs-attr">engine</span>:<span class="hljs-built_in">string</span>;    
   <span class="hljs-comment">// 构造函数</span>
   <span class="hljs-function"><span class="hljs-title">constructor</span>(<span class="hljs-params">engine:<span class="hljs-built_in">string</span></span>)</span> &#123; 
   <span class="hljs-comment">//this 关键字表示当前类实例化的对象。构造函数的参数名与字段名相同。</span>
      <span class="hljs-built_in">this</span>.engine = engine 
   &#125;    
   <span class="hljs-comment">// 方法</span>
   disp():<span class="hljs-built_in">void</span> &#123; 
      <span class="hljs-built_in">console</span>.log(<span class="hljs-string">"函数中显示发动机型号  :   "</span>+<span class="hljs-built_in">this</span>.engine) 
   &#125; 
&#125; 
<span class="hljs-comment">// 创建一个对象</span>
<span class="hljs-comment">//使用 new 关键字来实例化类的对象，类实例化时会调用构造函数，类中的字段属性和方法可以使用 **.** 号来访问。</span>
<span class="hljs-keyword">var</span> obj = <span class="hljs-keyword">new</span> Car(<span class="hljs-string">"XXSY1"</span>)
<span class="hljs-comment">// 访问字段</span>
<span class="hljs-built_in">console</span>.log(<span class="hljs-string">"读取发动机型号 :  "</span>+obj.engine)  
<span class="hljs-comment">// 访问方法</span>
obj.disp()
<span class="copy-code-btn">复制代码</span></code></pre>
<p>编译以上代码，得到以下 javascript 代码：</p>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> Car = <span class="hljs-comment">/** <span class="hljs-doctag">@class </span>*/</span> (<span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params"></span>) </span>&#123;
    <span class="hljs-comment">// 构造函数</span>
    <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">Car</span>(<span class="hljs-params">engine</span>) </span>&#123;
        <span class="hljs-built_in">this</span>.engine = engine;
    &#125;
    <span class="hljs-comment">// 方法</span>
    Car.prototype.disp = <span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params"></span>) </span>&#123;
        <span class="hljs-built_in">console</span>.log(<span class="hljs-string">"函数中显示发动机型号  :   "</span> + <span class="hljs-built_in">this</span>.engine);
    &#125;;
    <span class="hljs-keyword">return</span> Car;
&#125;());
<span class="hljs-comment">// 创建一个对象</span>
<span class="hljs-keyword">var</span> obj = <span class="hljs-keyword">new</span> Car(<span class="hljs-string">"XXSY1"</span>);
<span class="hljs-comment">// 访问字段</span>
<span class="hljs-built_in">console</span>.log(<span class="hljs-string">"读取发动机型号 :  "</span> + obj.engine);
<span class="hljs-comment">// 访问方法</span>
obj.disp();
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-3">类的继承</h3>
<p>类继承使用关键字 <strong>extends</strong>，子类除了不能继承父类的私有成员(方法和属性)和构造函数，其他的都可以继承。</p>
<p>TypeScript 一次只能继承一个类，不支持继承多个类，但 TypeScript 支持多重继承（A 继承 B，B 继承 C）。</p>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">child_class_name</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">parent_class_name</span>
</span><span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-4">访问控制修饰符</h3>
<p>TypeScript 中，可以使用访问控制符来保护对类、变量、方法和构造方法的访问。TypeScript 支持 3 种不同的访问权限。</p>
<ul>
<li><strong>public（默认）</strong> : 公有，可以在任何地方被访问。</li>
<li><strong>protected</strong> : 受保护，可以被其自身以及其子类和父类访问。</li>
<li><strong>private</strong> : 私有，只能被其定义所在的类访问。</li>
</ul>
<h2 data-id="heading-5">interface与class的区别和使用</h2>
<ul>
<li>interface:接口只声明成员方法，不做实现（抽象）。</li>
<li>class:类声明并实现方法。</li>
</ul>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-keyword">interface</span> ContentInterface &#123;
    getContent(): <span class="hljs-built_in">String</span>;
    <span class="hljs-comment">//每个实现该接口的类都必须实现getContent方法</span>
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Article</span> <span class="hljs-title">implements</span> <span class="hljs-title">ContentInterface</span> </span>&#123;
    <span class="hljs-comment">// 必须实现getContent方法</span>
    <span class="hljs-keyword">public</span> <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">getContent</span>(<span class="hljs-params"></span>): <span class="hljs-title">String</span> </span>&#123;
        <span class="hljs-keyword">return</span> <span class="hljs-string">'I am an article.'</span>;
    &#125; 
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Passage</span> <span class="hljs-title">implements</span> <span class="hljs-title">ContentInterface</span> </span>&#123;
    <span class="hljs-comment">// 但实现方式可以不同</span>
    <span class="hljs-keyword">public</span> <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">getContent</span>(<span class="hljs-params"></span>): <span class="hljs-title">String</span> </span>&#123;
        <span class="hljs-keyword">return</span> <span class="hljs-string">'I am a passage.'</span>
    &#125;
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">News</span> <span class="hljs-title">implements</span> <span class="hljs-title">ContentInterface</span> </span>&#123;
    <span class="hljs-comment">// 没有实现getContent方法，编译器会报错</span>
&#125;

<span class="hljs-keyword">let</span> a = <span class="hljs-keyword">new</span> Article();
<span class="hljs-keyword">let</span> p = <span class="hljs-keyword">new</span> Passage();

print(a); <span class="hljs-comment">// "I am an article."</span>
print(p); <span class="hljs-comment">// "I am a passage."</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-6">extends和implements区别和使用</h2>
<ul>
<li>在类的声明中，通过关键字extends来创建一个类的子类。关键字implements声明类使用一个或者多个接口。</li>
<li>extends 可<strong>继承某个类</strong>, 获取父类的所有的静态属性，继承之后可以使用父类的方法, 也可以重写父类的方法。</li>
<li>extends 可用来做<strong>接口的接口继承</strong>，通过其他接口来扩展自己，可多接口继承。</li>
<li>implements 可实现**类的多个接口继承****, 接口的方法一般为空的, 必须重写方法才能使用 。</li>
</ul>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">A</span>（类） <span class="hljs-keyword">extends</span> <span class="hljs-title">B</span>（类） <span class="hljs-title">implements</span> <span class="hljs-title">C</span>,<span class="hljs-title">D</span>,<span class="hljs-title">E</span>（接口）//类
    
<span class="hljs-title">Child_interface</span>（接口） <span class="hljs-keyword">extends</span> <span class="hljs-title">super_interface1</span>（接口）, <span class="hljs-title">super_interface2</span>（接口）,…,<span class="hljs-title">super_interfaceN</span>（接口）//接口
</span><span class="copy-code-btn">复制代码</span></code></pre></div>  
</div>
            
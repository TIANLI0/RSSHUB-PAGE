
---
title: '为什么let和const不能重复声明？为什么let和const存在暂时性死区？'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e10009691def439c9e3241f2dd1a242a~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Thu, 15 Jul 2021 18:18:57 GMT
thumbnail: 'https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e10009691def439c9e3241f2dd1a242a~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h1 data-id="heading-0">前言</h1>
<p>在面试时，面试官往往会问到var，let，const的区别是什么？我想大多数人对这个问题都心有成竹，你的答案大概是以下几个方面：</p>
<ol>
<li>var存在变量提升，而let和const不存在变量提升</li>
<li>var声明的变量会添加进window对象中，而let和const声明的变量不会</li>
<li>let和const声明的变量不可以重复声明</li>
<li>let和const声明的变量存在暂时性死区</li>
<li>const声明的基础类型不可修改，const声明的引用类型只能修改该引用类型的属性而不能给该变量重新赋值（const确定了一个地址，该地址不能被修改）</li>
<li>let和const存在块级作用域，而var不存在</li>
<li>let在for循环中每循环一次就会重新声明一次（因为let有块级作用域）</li>
</ol>
<p>是不是感觉自己说得好全了，然而面试官总是喜欢坑人的，下面两个问题就是用来坑你的。</p>
<p><strong>为什么let和const不能重复声明？为什么let和const存在暂时性死区？</strong></p>
<p>这也太坑了吧，我TMD怎么知道？好了好了，别吐槽，我们现在就来解决这个问题。</p>
<h1 data-id="heading-1">为什么let和const不能重复声明？</h1>
<p>在ES6规范有一个词叫做Global Enviroment Records(也就是全局环境变量记录)，它里面包含两个内容，一个是Object Enviroment Record(它不等同于window对象)，另一个是Reclarative Enviroment Record。</p>
<p>函数声明和使用var声明的变量会添加进入Object Enviroment Record中。
使用let声明和使用const声明的变量会添加入Reclarative Enviroment Record中。下面是ECMAscript规范中对var,let,const的一些约束。
我们来看一下ECMAscript对var,let,const声明的约束：</p>
<p><img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e10009691def439c9e3241f2dd1a242a~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p>也就是说：</p>
<p>使用var声明时，V8引擎只会检查Declarative Enviroment Record中是否有该变量，如果有，就会报错，否则将该变量添加入Object Enviroment Record中。
使用let和const声明时，引擎会同时检查Object Enviroment Record和Declarative Enviroment Record是否有该变量，如果有，则报错，否则将将变量添加入Declarative Enviroment Record中。
这就解释了为什么使用var声明的变量可以重复声明，而是用let和const声明的变量不可以重复声明。</p>
<h1 data-id="heading-2">为什么let和const存在暂时性死区？</h1>
<p>首先我们来问一个问题，let和const声明的变量的声明真的没有提升吗？我们来做一个简单的测试。</p>
<p><img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e7529cb8ff7c4c5ba67adeacb6573bb3~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p><img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/75fbac2acfe24ff78279a52766b46083~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p>可以看到，当我们使用Object.defineProperty在Object Enviroment Record中添加了一个变量a（使用Object.defineProperty会在Object Enviroment Record中加入一个变量，而直接使用window.a这种方式是不会往Object Enviroment Record添加变量的）。</p>
<p>当我们让let a和Object.defineProperty同时在一个代码块中时，没有报错
而当我们先执行Object.defineProperty后再用let声明a时，浏览器报错了。
其实这里就已经说明了一个问题，我想聪明的你也一定想到了。那就是let声明被提升了，但是使用let声明的变量还没有初始化，它连一个undefined的值都没有,我们使用chrome浏览器来进一步测试:</p>
<p><img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/87e68131998a454985616855c458d2fd~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer">
可以看到chrome中说在初始化前无法访问a。所以说，使用let和const声明的变量的声明提升了(看起来似乎很不可思议，尽管很多书上都会说let和const不存在变量提升，但实际上提升这个词本身就是不规范的)，但是没有初始化，连一个undefined的值都没有。</p>
<p>这就是暂时性死区出现的原因。</p>
<p>参考资料：
<a href="https://link.juejin.cn/?target=https%3A%2F%2Fblog.csdn.net%2Fqq_43670193%2Farticle%2Fdetails%2F115604870" target="_blank" rel="nofollow noopener noreferrer" title="https://blog.csdn.net/qq_43670193/article/details/115604870" ref="nofollow noopener noreferrer">blog.csdn.net/qq_43670193…</a></p></div>  
</div>
            
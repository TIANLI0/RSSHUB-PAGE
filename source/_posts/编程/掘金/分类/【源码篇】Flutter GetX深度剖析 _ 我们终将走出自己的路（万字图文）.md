
---
title: '【源码篇】Flutter GetX深度剖析 _ 我们终将走出自己的路（万字图文）'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d51af6c66258469faaef202b628a5c2c~tplv-k3u1fbpfcp-zoom-1.image'
author: 掘金
comments: false
date: Tue, 13 Jul 2021 17:51:07 GMT
thumbnail: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d51af6c66258469faaef202b628a5c2c~tplv-k3u1fbpfcp-zoom-1.image'
---

<div>   
<div class="markdown-body"><style>@charset "UTF-8";.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:14px;overflow-x:hidden;color:#353535&#125;.markdown-body h1&#123;padding-bottom:4px;font-size:30px&#125;.markdown-body h1,.markdown-body h2&#123;margin-top:36px;margin-bottom:10px;line-height:1.5;color:#005bb7&#125;.markdown-body h2&#123;position:relative;padding-left:16px;padding-right:10px;padding-bottom:10px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h2:before&#123;content:"「";position:absolute;top:-6px;left:-10px&#125;.markdown-body h2:after&#123;content:"」";position:absolute;top:6px;right:auto&#125;.markdown-body h3&#123;position:relative;padding-bottom:0;margin-top:30px;margin-bottom:10px;font-size:20px;line-height:1.5;color:#005bb7;padding-left:6px&#125;.markdown-body h3:before&#123;content:"»";padding-right:6px;color:#2196f3&#125;.markdown-body h4&#123;margin-top:24px;font-size:16px&#125;.markdown-body h4,.markdown-body h5&#123;padding-bottom:0;margin-bottom:10px;line-height:1.5;color:#005bb7;padding-left:6px&#125;.markdown-body h5&#123;margin-top:18px;font-size:14px&#125;.markdown-body h6&#123;padding-bottom:0;margin-top:12px;margin-bottom:10px;font-size:12px;line-height:1.5;color:#005bb7;padding-left:6px&#125;.markdown-body p&#123;line-height:inherit;margin-top:16px;margin-bottom:16px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;position:relative;width:98%;height:1px;margin-top:32px;margin-bottom:32px;background-image:linear-gradient(90deg,#007fff,rgba(255,0,0,.3),hsla(0,0%,100%,.1),rgba(255,0,0,.3),#007fff);border-width:0;overflow:visible&#125;.markdown-body hr:after&#123;content:"";position:absolute;margin:auto;left:0;right:0;bottom:0;top:0;display:inline-block;width:60px;height:20px;background:#fff;background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACgAAAAgCAYAAABgrToAAAADoklEQVRYR82XTYgcRRTHf2933Q1RjAa9eFO8JHoJ8RQVBQ2iBwXBET0YEUTXNVmNQtTpmeqaWV0XNRq/o4KoECSCEPSg4CF+BYUkIIiCoCJCPIhC/Ihh2Z0nVV27VnZnenumW9i6ddV7//frV69fVQurfMgq56NawFTPAU6QyomqXrw6wIZeyhCPebA5buNR+akKyGoAjd6BshthnYdSjqNcRVuOlIUsD2j0SuA94IwuMHdh5ZUykOUBXfSGbmKI54EtAeYIHSZoy5dl4JxvNYBOKdW1KE8BQ8AkVk6WhasWsAiN0TX9gveXQaPP+Aytpc4u+bMI06JNohsYYYYOR2lJWtS3OKDRfcAtQfgDoI6Vo4UCGb0OmAEuDvZvYmVbEd/igC3dzDz7gQu8sPA9kJDK27mBmjqBeLjTg90PDFOjWawFFQd06kZHEfaj3LAIpTRpSXsZ5E06zEYP9sDimnAApYaV2SLZG/wjMeqAkijwW4xQJ5Gf/ZzRC8OW3hiBTGGlURRswW55Bh/Ssxljrwew8l1PQaM14GngvGDzBUKdDsMeTtgU5o8B92PFlUf3YXUrHa7Fys6lBqcCGnX15YQ2A18FyPd7Crd1A3M8C1wdbH4DD3hWeP6IEXbQkG97ajR1HPFnuPP5jFFq1OWX7hl8WM9l1AO648uNfwLk7tytMeogty+xeQ4rO3r6bdcx1nuwOGsHmaXGtPzae4uzGnLH1kQkvpdZGrHjssBZJrL+pqS05KWc8tgITAPXRzYvYOXe/C2OV43eDcRBDtIhoS2f9wzc0Cv8Wls+zoFzUC5zF0U241h5uZtPfptp6OUM8wbK+cH5GEpCS17P3fJei0Z3+npTxryJ8CPzbKMtn/ZyWbkPGl0PuFPkmkjkcb4h4R2ZLwRq1H0ALmvjkf2HwK1Y+T1PY2XABe/sHJ6MxN5lnoSpnC/UGbsTaI5phK2R7x6s3Ffk5YoDOrWm3onwJHBmEP86bPmBrsGaenNoIdnxCH+gPEhLXi0Cl1VBvyPVLSh7gEuC62yAfOIUqabWEaaiucMIk6RyqJ+Q/QM69V26jjW86Gvov/EaoyT8zRCn+Xq7PVrbx0nuYUaO9wM3WAbjCE1NEUw09Um4UV+2OKfYfu5/S19gsAzGKqm6LE5FrShbdS0ku465DjDwKA/oQht19ejqbaEVuRbiLhuHByYLjtUAZpDutzP7cYdHsPJXWbjyNVgFwQoa1WXwf4Jd9YD/Ap80+yE7+u9aAAAAAElFTkSuQmCC);background-repeat:no-repeat;background-size:auto 100%;background-position-x:center&#125;.markdown-body code&#123;padding:.065em .4em;font-size:.87em;color:#c2185b;word-break:break-word;overflow-x:auto;background-color:#fff4f4;border-radius:2px&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;display:block;padding:16px 12px;margin:0;font-size:12px;color:#333;word-break:normal;overflow-x:auto;background:#f8f8f8&#125;.markdown-body pre>code::-webkit-scrollbar&#123;width:4px;height:4px&#125;.markdown-body pre>code::-webkit-scrollbar-track&#123;background-color:#bedcff&#125;.markdown-body pre>code::-webkit-scrollbar-thumb&#123;background-color:#2196f3;border-radius:10px&#125;.markdown-body a&#123;position:relative;text-decoration:none;color:#3da8f5;border-bottom:1px solid #bedcff&#125;.markdown-body a:hover&#123;color:#007fff;border-bottom-color:#007fff&#125;.markdown-body a:active&#123;color:#007fff&#125;.markdown-body a:after&#123;position:absolute;content:"";top:100%;left:0;width:100%;opacity:0;border-bottom:1px solid #bedcff;transition:top .3s,opacity .3s;transform:translateZ(0)&#125;.markdown-body a:hover:after&#123;top:0;opacity:1;border-bottom-color:#007fff&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #c3e0fd;border-spacing:0;border-collapse:collapse&#125;.markdown-body table thead&#123;color:#000;text-align:left;font-size:14px;background:#f6f6f6&#125;.markdown-body table tr:nth-child(2n)&#123;background-color:#f7fbff&#125;.markdown-body table tr:hover&#123;background-color:#e0edf7&#125;.markdown-body table td,.markdown-body table th&#123;padding:12px 8px;line-height:24px;border:1px solid #c3e0fd&#125;.markdown-body table th&#123;color:#005bb7;background-color:#dff0ff&#125;.markdown-body table td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#8c8c8c;border-left:4px solid #2196f3;background-color:#f0fdff;padding:1px 20px;margin:22px 0&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body b,.markdown-body blockquote>b,.markdown-body blockquote>strong,.markdown-body strong&#123;color:#2196f3&#125;.markdown-body em,.markdown-body i&#123;color:#4fc3f7&#125;.markdown-body del&#123;color:#ccc&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:4px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body details>summary&#123;outline:none;color:#005bb7;font-size:20px;font-weight:bolder;border-bottom:1px solid #bedcff;cursor:pointer&#125;.markdown-body details>p&#123;padding:10px 20px;margin:10px 0 0;color:#666;background-color:#f0fdff;border:2px dashed #2196f3&#125;.markdown-body h1::selection,.markdown-body h2::selection,.markdown-body h3::selection,.markdown-body h4::selection,.markdown-body h5::selection,.markdown-body h6::selection&#123;color:#005bb7;background-color:rgba(160,200,255,.15)&#125;.markdown-body p::selection&#123;color:#c80000&#125;.markdown-body a::selection,.markdown-body b::selection,.markdown-body del::selection,.markdown-body em::selection,.markdown-body i::selection,.markdown-body strong::selection&#123;background-color:transparent&#125;.markdown-body code::selection&#123;background-color:#ffeaeb&#125;.markdown-body pre>code::selection&#123;background-color:rgba(160,200,255,.25)&#125;.markdown-body ol ::selection,.markdown-body ul ::selection&#123;background-color:rgba(160,200,255,.15)&#125;.markdown-body .contains-task-list&#123;padding-left:14px;list-style:none&#125;.markdown-body .contains-task-list input[type=checkbox]&#123;position:relative&#125;.markdown-body .contains-task-list input[type=checkbox]:before&#123;content:"";position:absolute;top:0;left:0;right:0;bottom:0;width:inherit;height:inherit;background:#f0f8ff;border:1px solid #add6ff;border-radius:2px;box-sizing:border-box;z-index:1&#125;.markdown-body .contains-task-list input[type=checkbox]:checked:after&#123;content:"✓";position:absolute;top:-12px;left:0;right:0;bottom:0;width:0;height:0;color:#f55;font-size:20px;font-weight:700;z-index:2&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d51af6c66258469faaef202b628a5c2c~tplv-k3u1fbpfcp-zoom-1.image" alt="image-20210627221006498" loading="lazy" referrerpolicy="no-referrer"></p>
<h1 data-id="heading-0">前言</h1>
<blockquote>
<p><strong>人心中的成见是一座大山，任你怎么努力都休想搬动。</strong></p>
</blockquote>
<p>这是电影《哪吒》里申公豹说的一句话，也是贯彻整部电影的一个主题；或许这句话引起了太多人的共鸣：35岁职场危机，大厂卡本科学历，无房无车结婚难等等，所以，这句话也经常被人提起。</p>
<p>同时，因为GetX作者的一些言论，也让一些成见一直伴随着GetX这个框架。</p>
<p><strong>我写这篇文章，并不是为GetX正名</strong></p>
<ul>
<li>我自问自己并不是任何一个状态框架的死忠者，Provider和Bloc，我写了相关使用、原理剖析文章和相关代码生成插件</li>
<li>在我心中，这类框架并没有多么神秘</li>
<li>因为对其原理较熟，上手使用是一件较为容易的事，所以切换相关框架没有多大的时间成本</li>
<li>所以，我无需去做一个卫道者</li>
</ul>
<p>GetX整体设计，有不少优秀点思想，我希望将这些优秀设计思路展现给大家；或许会对你设计自己的框架有一些帮助，同时也是对自己思考历程的一个记录。</p>
<h1 data-id="heading-1">前置知识</h1>
<blockquote>
<p><strong>在说GetX设计思想之前，需要先介绍几个知识，在Flutter茁壮发展的历程里，他们都留下了浓墨重彩的一笔</strong></p>
</blockquote>
<h2 data-id="heading-2">InheritedWidget</h2>
<p><strong>不得不说，这个控件真的是一个神奇控件，它就仿佛是一把神兵利器</strong></p>
<ul>
<li>宝刀屠龙，号令天下，莫敢不从，倚天不出，谁与争锋</li>
<li>倚天剑，剑藏《九阴真经》</li>
<li>屠龙刀，刀藏《降龙十八掌》、《武穆遗书》</li>
</ul>
<p><strong>InheritedWidget这把神兵藏有什么？</strong></p>
<ul>
<li>依赖节点，数据传输</li>
<li>定点刷新机制</li>
</ul>
<h3 data-id="heading-3">数据传输</h3>
<p>InheritedWidget是我们统称的一个控件名，精髓还是<strong>InheritedElement</strong>，InheritedWidget的数据传递，来看下存和取这俩个过程</p>
<blockquote>
<p><strong>存数据</strong></p>
</blockquote>
<ul>
<li>InheritedWidget存数据，是一个比较简单的操作，存储在InheritedElement中即可</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">TransferDataWidget</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">InheritedWidget</span> </span>&#123;
  TransferDataWidget(&#123;<span class="hljs-keyword">required</span> Widget child&#125;) : <span class="hljs-keyword">super</span>(child: child);

  <span class="hljs-meta">@override</span>
  <span class="hljs-built_in">bool</span> updateShouldNotify(InheritedWidget oldWidget) => <span class="hljs-keyword">false</span>;

  <span class="hljs-meta">@override</span>
  InheritedElement createElement() => TransferDataElement(<span class="hljs-keyword">this</span>);
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">TransferDataElement</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">InheritedElement</span> </span>&#123;
  TransferDataElement(InheritedWidget widget) : <span class="hljs-keyword">super</span>(widget);

  <span class="hljs-comment">///<span class="markdown">随便初始化什么, 设置只读都行</span></span>
  <span class="hljs-built_in">String</span> value = <span class="hljs-string">'传输数据'</span>;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p><strong>取数据</strong></p>
</blockquote>
<ul>
<li>只要是 <strong>TransferDataWidget（上面InheritedWidget的子类）</strong> 的子节点，通过子节点的BuildContext（Element是BuildContext的实现类），都可以无缝的取数据</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-keyword">var</span> transferDataElement = context.getElementForInheritedWidgetOfExactType<TransferDataWidget>()
            <span class="hljs-keyword">as</span> TransferDataElement?;
<span class="hljs-keyword">var</span> msg = transferDataElement.value;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>可以发现，我们只需要通过Element的getElementForInheritedWidgetOfExactType方法，就可以拿到父节点的TransferDataElement实例（必须继承InheritedElement）</p>
<p>拿到实例后，自然就可以很简单的拿到相应数据了</p>
<blockquote>
<p><strong>原理</strong></p>
</blockquote>
<ul>
<li>可以发现我们是拿到了XxxInheritedElement实例，继而拿到了储存的值，所以关键在 <strong>getElementForInheritedWidgetOfExactType()</strong>  这个方法
<ul>
<li>代码很简单，就是从 _inheritedWidgets这个map里取值，泛型T是key</li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-keyword">abstract</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Element</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">DiagnosticableTree</span> <span class="hljs-keyword">implements</span> <span class="hljs-title">BuildContext</span> </span>&#123;

    <span class="hljs-built_in">Map</span><<span class="hljs-built_in">Type</span>, InheritedElement>? _inheritedWidgets;

    <span class="hljs-meta">@override</span>
    InheritedElement? getElementForInheritedWidgetOfExactType<T <span class="hljs-keyword">extends</span> InheritedWidget>() &#123;
        <span class="hljs-keyword">assert</span>(_debugCheckStateIsActiveForAncestorLookup());
        <span class="hljs-keyword">final</span> InheritedElement? ancestor = _inheritedWidgets == <span class="hljs-keyword">null</span> ? <span class="hljs-keyword">null</span> : _inheritedWidgets![T];
        <span class="hljs-keyword">return</span> ancestor;
    &#125;
    
    ...
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>接下来只要搞清楚 _inheritedWidgets 是怎么存值，那么一切都会明朗</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-keyword">abstract</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">ComponentElement</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Element</span> </span>&#123;
    
  <span class="hljs-meta">@mustCallSuper</span>
  <span class="hljs-keyword">void</span> mount(<span class="hljs-built_in">Element?</span> parent, <span class="hljs-built_in">dynamic</span> newSlot) &#123;
    ...
    _updateInheritance();
  &#125;
    
  <span class="hljs-keyword">void</span> _updateInheritance() &#123;
    <span class="hljs-keyword">assert</span>(_lifecycleState == _ElementLifecycle.active);
    _inheritedWidgets = _parent?._inheritedWidgets;
  &#125;
    
    ...
&#125;

<span class="hljs-keyword">abstract</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">ProxyElement</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">ComponentElement</span> </span>&#123;
    ...
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">InheritedElement</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">ProxyElement</span> </span>&#123;
    InheritedElement(InheritedWidget widget) : <span class="hljs-keyword">super</span>(widget);

    <span class="hljs-meta">@override</span>
    <span class="hljs-keyword">void</span> _updateInheritance() &#123;
        <span class="hljs-keyword">assert</span>(_lifecycleState == _ElementLifecycle.active);
        <span class="hljs-keyword">final</span> <span class="hljs-built_in">Map</span><<span class="hljs-built_in">Type</span>, InheritedElement>? incomingWidgets = _parent?._inheritedWidgets;
        <span class="hljs-keyword">if</span> (incomingWidgets != <span class="hljs-keyword">null</span>)
            _inheritedWidgets = HashMap<<span class="hljs-built_in">Type</span>, InheritedElement>.from(incomingWidgets);
        <span class="hljs-keyword">else</span>
            _inheritedWidgets = HashMap<<span class="hljs-built_in">Type</span>, InheritedElement>();
        _inheritedWidgets![widget.runtimeType] = <span class="hljs-keyword">this</span>;
    &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>整体上逻辑还是比较清晰</p>
<ol>
<li>遇到某个节点为 <strong>InheritedWidget</strong> 时，会将父节点的 _inheritedWidgets 变量给 incomingWidgets 这个临时变量
<ol>
<li>incomingWidgets 为空：为父类Element的 _inheritedWidgets 变量， 实例了一个map对象</li>
<li>incomingWidgets 不为空：将父节点_inheritedWidgets 所有数据深拷贝，返回一个全新的Map实例（含有父节点 _inheritedWidgets 所有数据），赋值给父类Element的 _inheritedWidgets 变量</li>
</ol>
</li>
<li>将自身实例赋值给父类Element的  _inheritedWidgets 变量，key为其widget的runtimeType</li>
</ol>
<blockquote>
<p><strong>为什么任何一个Widget的Element实例的 _inheritedWidgets 变量，可直接拿到父节点InheritedElement实例？</strong></p>
</blockquote>
<ul>
<li>Element中做了一个父节点向子节点赋值的操作：整个数据传输链清晰了</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-keyword">abstract</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Element</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">DiagnosticableTree</span> <span class="hljs-keyword">implements</span> <span class="hljs-title">BuildContext</span> </span>&#123;

    <span class="hljs-built_in">Map</span><<span class="hljs-built_in">Type</span>, InheritedElement>? _inheritedWidgets;

    <span class="hljs-keyword">void</span> _updateInheritance() &#123;
        <span class="hljs-keyword">assert</span>(_lifecycleState == _ElementLifecycle.active);
        _inheritedWidgets = _parent?._inheritedWidgets;
    &#125;

...
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>图示</li>
</ul>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b6ec4f4a30b049fdbb2082a9e1e2e885~tplv-k3u1fbpfcp-zoom-1.image" alt="InheritedWidget存取数据" loading="lazy" referrerpolicy="no-referrer"></p>
<h3 data-id="heading-4">刷新机制</h3>
<blockquote>
<p>InheritedElement和Element之间有一些交互，实际上自带了一套刷新机制</p>
</blockquote>
<ul>
<li>InheritedElement存子节点Element： _dependents，这个变量是用来存储，需要刷新的子Element</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">InheritedElement</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">ProxyElement</span> </span>&#123;
  InheritedElement(InheritedWidget widget) : <span class="hljs-keyword">super</span>(widget);

  <span class="hljs-keyword">final</span> <span class="hljs-built_in">Map</span><<span class="hljs-built_in">Element</span>, <span class="hljs-built_in">Object?</span>> _dependents = HashMap<<span class="hljs-built_in">Element</span>, <span class="hljs-built_in">Object?</span>>();

  <span class="hljs-meta">@protected</span>
  <span class="hljs-keyword">void</span> setDependencies(<span class="hljs-built_in">Element</span> dependent, <span class="hljs-built_in">Object?</span> value) &#123;
    _dependents[dependent] = value;
  &#125;

  <span class="hljs-meta">@protected</span>
  <span class="hljs-keyword">void</span> updateDependencies(<span class="hljs-built_in">Element</span> dependent, <span class="hljs-built_in">Object?</span> aspect) &#123;
    setDependencies(dependent, <span class="hljs-keyword">null</span>);
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>InheritedElement刷新子Element
<ul>
<li>notifyClients这个方法就是将 _dependents  存储的Element，全部拿了出来，传入notifyDependent</li>
<li>在notifyDependent方法中，传入Element调用了自身didChangeDependencies()方法</li>
<li>Element的didChangeDependencies() 方法会调用 markNeedsBuild() ，来刷新自身</li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">InheritedElement</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">ProxyElement</span> </span>&#123;
  InheritedElement(InheritedWidget widget) : <span class="hljs-keyword">super</span>(widget);

  <span class="hljs-keyword">final</span> <span class="hljs-built_in">Map</span><<span class="hljs-built_in">Element</span>, <span class="hljs-built_in">Object?</span>> _dependents = HashMap<<span class="hljs-built_in">Element</span>, <span class="hljs-built_in">Object?</span>>();

  <span class="hljs-meta">@protected</span>
  <span class="hljs-keyword">void</span> notifyDependent(<span class="hljs-keyword">covariant</span> InheritedWidget oldWidget, <span class="hljs-built_in">Element</span> dependent) &#123;
    dependent.didChangeDependencies();
  &#125;
    
  <span class="hljs-meta">@override</span>
  <span class="hljs-keyword">void</span> notifyClients(InheritedWidget oldWidget) &#123;
    <span class="hljs-keyword">for</span> (<span class="hljs-keyword">final</span> <span class="hljs-built_in">Element</span> dependent <span class="hljs-keyword">in</span> _dependents.keys) &#123;
      ...
      notifyDependent(oldWidget, dependent);
    &#125;
  &#125;
&#125;

<span class="hljs-keyword">abstract</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Element</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">DiagnosticableTree</span> <span class="hljs-keyword">implements</span> <span class="hljs-title">BuildContext</span> </span>&#123;
  ...
    
  <span class="hljs-meta">@mustCallSuper</span>
  <span class="hljs-keyword">void</span> didChangeDependencies() &#123;
    <span class="hljs-keyword">assert</span>(_lifecycleState == _ElementLifecycle.active); <span class="hljs-comment">// otherwise markNeedsBuild is a no-op</span>
    <span class="hljs-keyword">assert</span>(_debugCheckOwnerBuildTargetExists(<span class="hljs-string">'didChangeDependencies'</span>));
    markNeedsBuild();
  &#125;
    
  ...
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p><strong>InheritedWidget的子节点是怎么将自身Element</strong></p>
<p><strong>添加到InheritedElement的_dependents变量里的呢？</strong></p>
</blockquote>
<ul>
<li>Element里面有个 dependOnInheritedElement 方法
<ul>
<li>Element中dependOnInheritedElement方法，会传入<strong>InheritedElement</strong>实例 <strong>ancestor</strong></li>
<li>ancestor调用updateDependencies方法，将自身的Element实例传入</li>
<li>InheritedElement中就将这个Element，添加到_dependents变量中了</li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-keyword">abstract</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Element</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">DiagnosticableTree</span> <span class="hljs-keyword">implements</span> <span class="hljs-title">BuildContext</span> </span>&#123;
  ...
    
  <span class="hljs-meta">@override</span>
  InheritedWidget dependOnInheritedElement(InheritedElement ancestor, &#123; <span class="hljs-built_in">Object?</span> aspect &#125;) &#123;
    <span class="hljs-keyword">assert</span>(ancestor != <span class="hljs-keyword">null</span>);
    _dependencies ??= HashSet<InheritedElement>();
    _dependencies!.add(ancestor);
    ancestor.updateDependencies(<span class="hljs-keyword">this</span>, aspect);
    <span class="hljs-keyword">return</span> ancestor.widget;
  &#125;
    
  ...
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">InheritedElement</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">ProxyElement</span> </span>&#123;
  InheritedElement(InheritedWidget widget) : <span class="hljs-keyword">super</span>(widget);

  <span class="hljs-keyword">final</span> <span class="hljs-built_in">Map</span><<span class="hljs-built_in">Element</span>, <span class="hljs-built_in">Object?</span>> _dependents = HashMap<<span class="hljs-built_in">Element</span>, <span class="hljs-built_in">Object?</span>>();

  <span class="hljs-meta">@protected</span>
  <span class="hljs-keyword">void</span> setDependencies(<span class="hljs-built_in">Element</span> dependent, <span class="hljs-built_in">Object?</span> value) &#123;
    _dependents[dependent] = value;
  &#125;

  <span class="hljs-meta">@protected</span>
  <span class="hljs-keyword">void</span> updateDependencies(<span class="hljs-built_in">Element</span> dependent, <span class="hljs-built_in">Object?</span> aspect) &#123;
    setDependencies(dependent, <span class="hljs-keyword">null</span>);
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>dependOnInheritedElement该方法的使用也很简单
<ul>
<li>一般来说在某个Widget使用 getElementForInheritedWidgetOfExactType 获取父节点的 InheritedElement</li>
<li>然后将其传入 dependOnInheritedElement 方法中即可</li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-comment">// 举例</span>
<span class="hljs-keyword">var</span> inheritedElement = context
            .getElementForInheritedWidgetOfExactType<ChangeNotifierEasyP<T>>()
        <span class="hljs-keyword">as</span> EasyPInheritedElement<T>?;
context.dependOnInheritedElement(inheritedElement);
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p><strong>Provider核心原理，就是采用了InheritedWidget这种刷新机制</strong></p>
</blockquote>
<p>想详细了解Provider相关原理，可参考下面文章</p>
<ul>
<li><a href="https://juejin.cn/post/6968272002515894303" target="_blank" title="https://juejin.cn/post/6968272002515894303">源码篇：Flutter Provider的另一面（万字图文）</a></li>
</ul>
<blockquote>
<p><strong>图示</strong></p>
</blockquote>
<ul>
<li>来看下InheritedWidget刷新机制的图示</li>
</ul>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e34c385271c84dde922ced96a8eccf8d~tplv-k3u1fbpfcp-zoom-1.image" alt="InheritedWIdget刷新机制" loading="lazy" referrerpolicy="no-referrer"></p>
<h2 data-id="heading-5">路由小知识</h2>
<ul>
<li>路由Navigator中基本都是些操作路由的静态方法，NavigatorState是实现的具体逻辑</li>
</ul>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0ff6f068606843199faf6db54fbd7352~tplv-k3u1fbpfcp-zoom-1.image" alt="路由导图" loading="lazy" referrerpolicy="no-referrer"></p>
<p>大家在使用InheritedWidget获取数据的时候，或许有过这样一种困扰：A页面 ---> B页面 ---> C页面</p>
<p>如果我在A页面使用InheritedWidget储存了数据，跳转到B页面或者C页面，会发现使用context获取不到A页面的InheritedElement</p>
<p>这侧面证明了Navigator路由跳转：A页面跳转B页面，B页面并不是A页面的子节点</p>
<ul>
<li>大致结构：可勉强理解为，Navigator是所有页面父节点，页面与页面之间是平级关系</li>
</ul>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9536f5fa8642443fac08a768709c5b9e~tplv-k3u1fbpfcp-zoom-1.image" alt="路由结构" loading="lazy" referrerpolicy="no-referrer"></p>
<p><strong>这里我画了下大致结构，如有偏差，请务必指出来，我会尽快修改</strong></p>
<p><strong>关于Flutter路由原理解析，可参考此文章（作者为啥现在不更文了呢 ~~）</strong>：<a href="https://juejin.cn/post/6844903798398255111" target="_blank" title="https://juejin.cn/post/6844903798398255111">Flutter 路由原理解析</a></p>
<h2 data-id="heading-6">思考</h2>
<p>InheritedWidget为我们带了很多便利</p>
<ul>
<li>可以在一个Widget树范围，获取到我们想要InheritedElement（通过泛型区分即可）</li>
<li>InheritedElement和Element各种交互，也实现了一套极其简洁的刷新机制</li>
<li>进行一些深度封装，甚至可以无缝的管理很多控件的资源释放</li>
</ul>
<p>但是，Element提供的获取InheritedElement的方式，终究和路由机制无法很好的结合；这也模块设计无法避免的事情，或许某些模块设计的最优解，很难顾忌到其它模快的一些机制</p>
<p>InheritedWidget这把神兵利器，在我们学习Flutter历程中给予了很多帮助</p>
<ul>
<li>但是，当需求逐渐复杂，你的技术不断精进</li>
<li>屠龙刀这把神兵，或许渐渐的，不太适合你了</li>
<li>有时候，它甚至制约了你的出招</li>
<li>一位制造神兵的铁匠，在他心中，最好的神兵利器，或许永远是下一把</li>
</ul>
<p><strong>大部分的状态管理框架，将界面层和逻辑层分开，都是逻辑层来处理界面的刷新；逻辑层可以交给InheritedWidget存储管理；说明，我们自己也一定可以存储管理！</strong></p>
<ul>
<li>自己来管理逻辑层，可以摆脱Element树的约束，不用被困在Element树的父子节点中</li>
<li>在路由跳转的页面中，可以很轻松的获取上一页面，下一个页面或者上上一个页面逻辑层。</li>
</ul>
<p>这也是GetX中一个核心思想，这并不是一个多么新颖或高深技术，但是，我这觉得这是一种思维上的突破，可以带来更多的可能</p>
<h1 data-id="heading-7">依赖注入</h1>
<h2 data-id="heading-8">说明</h2>
<p>依赖注入有如下实现方式（维基百科）：</p>
<ul>
<li>基于接口。实现特定接口以供外部容器注入所依赖类型的对象。</li>
<li>基于 set 方法。实现特定属性的public set方法，来让外部容器调用传入所依赖类型的对象。</li>
<li>基于构造函数。实现特定参数的构造函数，在新建对象时传入所依赖类型的对象。</li>
<li>基于注解。基于<a href="https://link.juejin.cn/?target=https%3A%2F%2Fzh.wikipedia.org%2Fwiki%2FJava%25E6%25B3%25A8%25E8%25A7%25A3" target="_blank" rel="nofollow noopener noreferrer" title="https://zh.wikipedia.org/wiki/Java%E6%B3%A8%E8%A7%A3" ref="nofollow noopener noreferrer">Java的注解功能</a>，在私有变量前加“@Autowired”等注解，不需要显式的定义以上三种代码，便可以让外部容器传入对应的对象。该方案相当于定义了public的set方法，但是因为没有真正的set方法，从而不会为了实现依赖注入导致暴露了不该暴露的接口（因为set方法只想让容器访问来注入而并不希望其他依赖此类的对象访问）。</li>
</ul>
<blockquote>
<p>强耦合类型的，基于构造函数</p>
</blockquote>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Test</span> </span>&#123;
  <span class="hljs-built_in">String</span> msg;

  Test(<span class="hljs-built_in">String</span> msg) &#123;
    <span class="hljs-keyword">this</span>.msg = msg;
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p>set方式</p>
</blockquote>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Test</span> </span>&#123;
  <span class="hljs-built_in">String?</span> _msg;

  <span class="hljs-keyword">void</span> setMsg(<span class="hljs-built_in">String</span> msg) &#123;
    <span class="hljs-keyword">this</span>._msg = msg;
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>如果在Java中，图一时方便，直接在构造函数里面传值，然后需要的值越来越多，导致需要增加该构造函数传参，因为强耦合很多类，一改构造函数，爆红一大片（Dart构造函数可选参数的特性，就没有这类问题了）</p>
<ul>
<li>Getx注入的GetXController都是由GetX框架自己来维护的，如果没有GetX这个中间层会是什么样的？</li>
</ul>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/29e45762e3404e79bca2fb5fef7eef38~tplv-k3u1fbpfcp-zoom-1.image" alt="GetX依赖注入-前" loading="lazy" referrerpolicy="no-referrer"></p>
<ul>
<li>引入GetX这个中间层来管理
<ul>
<li>看下图，瞬间就想到了中介者模式</li>
<li>这也是控制反转的思想（创建对象的控制权本来在自己手上，现在交给了第三方）</li>
</ul>
</li>
</ul>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a24fc6072d534d739e801a8d53f5c46b~tplv-k3u1fbpfcp-zoom-1.image" alt="GetX依赖注入-后" loading="lazy" referrerpolicy="no-referrer"></p>
<h2 data-id="heading-9">Put</h2>
<blockquote>
<p>来看下GetX注入的操作</p>
</blockquote>
<ul>
<li>put使用</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-keyword">var</span> controller = Get.put(XxxGetxController());
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>看看内部操作
<ul>
<li>哎，各种骚操作</li>
<li>主要逻辑在Inst中，Inst是GetInterface的扩展类</li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">_GetImpl</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">GetInterface</span> </span>&#123;&#125;

<span class="hljs-keyword">final</span> Get = _GetImpl();

<span class="hljs-keyword">extension</span> Inst <span class="hljs-keyword">on</span> GetInterface &#123;
  S put<S>(S dependency,
          &#123;<span class="hljs-built_in">String?</span> tag,
          <span class="hljs-built_in">bool</span> permanent = <span class="hljs-keyword">false</span>,
          InstanceBuilderCallback<S>? builder&#125;) =>
      GetInstance().put<S>(dependency, tag: tag, permanent: permanent);
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>主要的逻辑看来还是GetInstance中
<ul>
<li>大家可以看看这地方单例的实现，我发现很多源码都用这种方式写的，非常简洁</li>
<li>全局的数据都是存在 _singl 中，这是个Map
<ul>
<li>key：对象的runtimeType或者类的Type + tag</li>
<li>value：_InstanceBuilderFactory类，我们传入dependedt对象会存入这个类中</li>
</ul>
</li>
<li>_singl 这个map存值的时候，不是用的put，而是用的putIfAbsent
<ul>
<li>如果map中有key和传入key相同的数据，传入的数据将不会被存储</li>
<li>也就是说相同类实例的对象，传入并不会被覆盖，只会存储第一条数据，后续被放弃</li>
</ul>
</li>
<li>最后使用find方法，返回传入的实例</li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">GetInstance</span> </span>&#123;
  <span class="hljs-keyword">factory</span> GetInstance() => _getInstance ??= GetInstance._();

  <span class="hljs-keyword">const</span> GetInstance._();

  <span class="hljs-keyword">static</span> GetInstance? _getInstance;

  <span class="hljs-keyword">static</span> <span class="hljs-keyword">final</span> <span class="hljs-built_in">Map</span><<span class="hljs-built_in">String</span>, _InstanceBuilderFactory> _singl = &#123;&#125;;

  S put<S>(
    S dependency, &#123;
    <span class="hljs-built_in">String?</span> tag,
    <span class="hljs-built_in">bool</span> permanent = <span class="hljs-keyword">false</span>,
    <span class="hljs-meta">@deprecated</span> InstanceBuilderCallback<S>? builder,
  &#125;) &#123;
    _insert(
        isSingleton: <span class="hljs-keyword">true</span>,
        name: tag,
        permanent: permanent,
        builder: builder ?? (() => dependency));
    <span class="hljs-keyword">return</span> find<S>(tag: tag);
  &#125;

  <span class="hljs-keyword">void</span> _insert<S>(&#123;
    <span class="hljs-built_in">bool?</span> isSingleton,
    <span class="hljs-built_in">String?</span> name,
    <span class="hljs-built_in">bool</span> permanent = <span class="hljs-keyword">false</span>,
    <span class="hljs-keyword">required</span> InstanceBuilderCallback<S> builder,
    <span class="hljs-built_in">bool</span> fenix = <span class="hljs-keyword">false</span>,
  &#125;) &#123;
    <span class="hljs-keyword">final</span> key = _getKey(S, name);
    _singl.putIfAbsent(
      key,
      () => _InstanceBuilderFactory<S>(
        isSingleton,
        builder,
        permanent,
        <span class="hljs-keyword">false</span>,
        fenix,
        name,
      ),
    );
  &#125;
    
  <span class="hljs-built_in">String</span> _getKey(<span class="hljs-built_in">Type</span> type, <span class="hljs-built_in">String?</span> name) &#123;
    <span class="hljs-keyword">return</span> name == <span class="hljs-keyword">null</span> ? type.toString() : type.toString() + name;
  &#125;
    
  S find<S>(&#123;<span class="hljs-built_in">String?</span> tag&#125;) &#123;
    <span class="hljs-keyword">final</span> key = _getKey(S, tag);
    <span class="hljs-keyword">if</span> (isRegistered<S>(tag: tag)) &#123;
      <span class="hljs-keyword">if</span> (_singl[key] == <span class="hljs-keyword">null</span>) &#123;
        <span class="hljs-keyword">if</span> (tag == <span class="hljs-keyword">null</span>) &#123;
          <span class="hljs-keyword">throw</span> <span class="hljs-string">'Class "<span class="hljs-subst">$S</span>" is not registered'</span>;
        &#125; <span class="hljs-keyword">else</span> &#123;
          <span class="hljs-keyword">throw</span> <span class="hljs-string">'Class "<span class="hljs-subst">$S</span>" with tag "<span class="hljs-subst">$tag</span>" is not registered'</span>;
        &#125;
      &#125;
      <span class="hljs-keyword">final</span> i = _initDependencies<S>(name: tag);
      <span class="hljs-keyword">return</span> i ?? _singl[key]!.getDependency() <span class="hljs-keyword">as</span> S;
    &#125; <span class="hljs-keyword">else</span> &#123;
      <span class="hljs-comment">// ignore: lines_longer_than_80_chars</span>
      <span class="hljs-keyword">throw</span> <span class="hljs-string">'"<span class="hljs-subst">$S</span>" not found. You need to call "Get.put(<span class="hljs-subst">$S</span>())" or "Get.lazyPut(()=><span class="hljs-subst">$S</span>())"'</span>;
    &#125;
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-10">find</h2>
<ul>
<li>find方法还是蛮简单的，就是从map中取数据的操作</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart">S find<S>(&#123;<span class="hljs-built_in">String?</span> tag&#125;) => GetInstance().find<S>(tag: tag);
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>看下具体逻辑
<ul>
<li>先判断 _singl 中是否含有该key的数据，有则取，无则抛异常</li>
<li>关键代码： <strong>_singl[key]!.getDependency() as S</strong>  ，直接通过key去map取值就行了</li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">GetInstance</span> </span>&#123;
  <span class="hljs-keyword">factory</span> GetInstance() => _getInstance ??= GetInstance._();

  <span class="hljs-keyword">const</span> GetInstance._();

  <span class="hljs-keyword">static</span> GetInstance? _getInstance;

  <span class="hljs-keyword">static</span> <span class="hljs-keyword">final</span> <span class="hljs-built_in">Map</span><<span class="hljs-built_in">String</span>, _InstanceBuilderFactory> _singl = &#123;&#125;;
    
  <span class="hljs-built_in">String</span> _getKey(<span class="hljs-built_in">Type</span> type, <span class="hljs-built_in">String?</span> name) &#123;
    <span class="hljs-keyword">return</span> name == <span class="hljs-keyword">null</span> ? type.toString() : type.toString() + name;
  &#125;
    
  <span class="hljs-built_in">bool</span> isRegistered<S>(&#123;<span class="hljs-built_in">String?</span> tag&#125;) => _singl.containsKey(_getKey(S, tag));
    
  S find<S>(&#123;<span class="hljs-built_in">String?</span> tag&#125;) &#123;
    <span class="hljs-keyword">final</span> key = _getKey(S, tag);
    <span class="hljs-keyword">if</span> (isRegistered<S>(tag: tag)) &#123;
      <span class="hljs-keyword">if</span> (_singl[key] == <span class="hljs-keyword">null</span>) &#123;
        <span class="hljs-keyword">if</span> (tag == <span class="hljs-keyword">null</span>) &#123;
          <span class="hljs-keyword">throw</span> <span class="hljs-string">'Class "<span class="hljs-subst">$S</span>" is not registered'</span>;
        &#125; <span class="hljs-keyword">else</span> &#123;
          <span class="hljs-keyword">throw</span> <span class="hljs-string">'Class "<span class="hljs-subst">$S</span>" with tag "<span class="hljs-subst">$tag</span>" is not registered'</span>;
        &#125;
      &#125;
      <span class="hljs-keyword">final</span> i = _initDependencies<S>(name: tag);
      <span class="hljs-keyword">return</span> i ?? _singl[key]!.getDependency() <span class="hljs-keyword">as</span> S;
    &#125; <span class="hljs-keyword">else</span> &#123;
      <span class="hljs-comment">// ignore: lines_longer_than_80_chars</span>
      <span class="hljs-keyword">throw</span> <span class="hljs-string">'"<span class="hljs-subst">$S</span>" not found. You need to call "Get.put(<span class="hljs-subst">$S</span>())" or "Get.lazyPut(()=><span class="hljs-subst">$S</span>())"'</span>;
    &#125;
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h1 data-id="heading-11">GetBuilder刷新机制</h1>
<h2 data-id="heading-12">使用</h2>
<p>为了知识的连续性，此处简单的写下使用</p>
<ul>
<li>逻辑层</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">GetCounterEasyLogic</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">GetxController</span> </span>&#123;
  <span class="hljs-keyword">var</span> count = <span class="hljs-number">0</span>;

  <span class="hljs-keyword">void</span> increase() &#123;
    ++count;
    update();
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>界面</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">GetCounterEasyPage</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">StatelessWidget</span> </span>&#123;
  <span class="hljs-keyword">final</span> GetCounterEasyLogic logic = Get.put(GetCounterEasyLogic());

  <span class="hljs-meta">@override</span>
  Widget build(BuildContext context) &#123;
    <span class="hljs-keyword">return</span> BaseScaffold(
      appBar: AppBar(title: <span class="hljs-keyword">const</span> Text(<span class="hljs-string">'计数器-简单式'</span>)),
      body: Center(
        child: GetBuilder<GetCounterEasyLogic>(builder: (logic) &#123;
          <span class="hljs-keyword">return</span> Text(
            <span class="hljs-string">'点击了 <span class="hljs-subst">$&#123;logic.count&#125;</span> 次'</span>,
            style: TextStyle(fontSize: <span class="hljs-number">30.0</span>),
          );
        &#125;),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: () => logic.increase(),
        child: Icon(Icons.add),
      ),
    );
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-13">GetBuilder</h2>
<p><strong>有一天，我躺在床上思考</strong></p>
<ul>
<li>Obx的状态管理，GetXController实例回收是放在路由里面，在很多场景下，存在一些局限性</li>
<li>后来我想到，GetBuilder使用带泛型，这就能拿到GetxController实例，GetBuilder又是StatefulWidget</li>
<li>这样就可以使用它来回收实例，能解决很多场景下，GetXController实例无法回收的问题（不使用Getx路由）</li>
<li>我兴致冲冲的打开Getx项目，准备提PR，然后发现GetBuilder已经在dispose里面写了回收实例的操作</li>
<li>淦！</li>
</ul>
<h3 data-id="heading-14">内置回收机制</h3>
<ul>
<li>此处精简很多代码，只展示回收机制的代码</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">GetBuilder</span><<span class="hljs-title">T</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">GetxController</span>> <span class="hljs-keyword">extends</span> <span class="hljs-title">StatefulWidget</span> </span>&#123;
  <span class="hljs-keyword">final</span> GetControllerBuilder<T> builder;
  <span class="hljs-keyword">final</span> <span class="hljs-built_in">bool</span> global;
  <span class="hljs-keyword">final</span> <span class="hljs-built_in">String?</span> tag;
  <span class="hljs-keyword">final</span> <span class="hljs-built_in">bool</span> autoRemove;
  <span class="hljs-keyword">final</span> T? init;

  <span class="hljs-keyword">const</span> GetBuilder(&#123;
    Key? key,
    <span class="hljs-keyword">this</span>.init,
    <span class="hljs-keyword">this</span>.global = <span class="hljs-keyword">true</span>,
    <span class="hljs-keyword">required</span> <span class="hljs-keyword">this</span>.builder,
    <span class="hljs-keyword">this</span>.autoRemove = <span class="hljs-keyword">true</span>,
    <span class="hljs-keyword">this</span>.initState,
    <span class="hljs-keyword">this</span>.tag,
  &#125;) : <span class="hljs-keyword">super</span>(key: key);


  <span class="hljs-meta">@override</span>
  GetBuilderState<T> createState() => GetBuilderState<T>();
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">GetBuilderState</span><<span class="hljs-title">T</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">GetxController</span>> <span class="hljs-keyword">extends</span> <span class="hljs-title">State</span><<span class="hljs-title">GetBuilder</span><<span class="hljs-title">T</span>>>
    <span class="hljs-title">with</span> <span class="hljs-title">GetStateUpdaterMixin</span> </span>&#123;
  T? controller;
  <span class="hljs-built_in">bool?</span> _isCreator = <span class="hljs-keyword">false</span>;
  VoidCallback? _remove;
  <span class="hljs-built_in">Object?</span> _filter;

  <span class="hljs-meta">@override</span>
  <span class="hljs-keyword">void</span> initState() &#123;
    <span class="hljs-keyword">super</span>.initState();
    widget.initState?.call(<span class="hljs-keyword">this</span>);

    <span class="hljs-keyword">var</span> isRegistered = GetInstance().isRegistered<T>(tag: widget.tag);

    <span class="hljs-keyword">if</span> (widget.global) &#123;
      <span class="hljs-keyword">if</span> (isRegistered) &#123;
        controller = GetInstance().find<T>(tag: widget.tag);
      &#125; <span class="hljs-keyword">else</span> &#123;
        controller = widget.init;
        GetInstance().put<T>(controller!, tag: widget.tag);
      &#125;
    &#125; <span class="hljs-keyword">else</span> &#123;
      controller = widget.init;
      controller?.onStart();
    &#125;

  &#125;

  <span class="hljs-meta">@override</span>
  <span class="hljs-keyword">void</span> dispose() &#123;
    <span class="hljs-keyword">super</span>.dispose();
    widget.dispose?.call(<span class="hljs-keyword">this</span>);
    <span class="hljs-keyword">if</span> (_isCreator! || widget.assignId) &#123;
      <span class="hljs-keyword">if</span> (widget.autoRemove && GetInstance().isRegistered<T>(tag: widget.tag)) &#123;
        GetInstance().delete<T>(tag: widget.tag);
      &#125;
    &#125;

    _remove?.call();

    controller = <span class="hljs-keyword">null</span>;
    _isCreator = <span class="hljs-keyword">null</span>;
    _remove = <span class="hljs-keyword">null</span>;
    _filter = <span class="hljs-keyword">null</span>;
  &#125;


  <span class="hljs-meta">@override</span>
  Widget build(BuildContext context) &#123;
    <span class="hljs-keyword">return</span> widget.builder(controller!);
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>代码里的逻辑还是相当清晰的，initState获取实例，dispose回收实例</p>
<ol>
<li>通过GetBuilder上泛型获取相应GetXController实例
<ul>
<li>不存在：使用init传入的实例</li>
<li>存在：直接使用；init传入的实例无效</li>
</ul>
</li>
<li>autoRemove可以控制是否自动回收GetXController实例
<ul>
<li>默认为true：默认开启自动回收</li>
<li>true：开启自动回收  false：关闭自动回收</li>
</ul>
</li>
</ol>
<h3 data-id="heading-15">刷新逻辑</h3>
<ul>
<li>这里仅保留刷新逻辑的相关代码，去掉了无需关注的代码</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-keyword">mixin</span> GetStateUpdaterMixin<T <span class="hljs-keyword">extends</span> StatefulWidget> <span class="hljs-keyword">on</span> State<T> &#123;
  <span class="hljs-keyword">void</span> getUpdate() &#123;
    <span class="hljs-keyword">if</span> (mounted) setState(() &#123;&#125;);
  &#125;
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">GetBuilder</span><<span class="hljs-title">T</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">GetxController</span>> <span class="hljs-keyword">extends</span> <span class="hljs-title">StatefulWidget</span> </span>&#123;
  <span class="hljs-keyword">final</span> GetControllerBuilder<T> builder;
  <span class="hljs-keyword">final</span> <span class="hljs-built_in">bool</span> global;
  <span class="hljs-keyword">final</span> T? init;
  <span class="hljs-keyword">final</span> <span class="hljs-built_in">Object?</span> id;
    
  <span class="hljs-keyword">const</span> GetBuilder(&#123;
    Key? key,
    <span class="hljs-keyword">this</span>.init,
    <span class="hljs-keyword">this</span>.id,
    <span class="hljs-keyword">this</span>.global = <span class="hljs-keyword">true</span>,
    <span class="hljs-keyword">required</span> <span class="hljs-keyword">this</span>.builder,
  &#125;) : <span class="hljs-keyword">super</span>(key: key);


  <span class="hljs-meta">@override</span>
  GetBuilderState<T> createState() => GetBuilderState<T>();
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">GetBuilderState</span><<span class="hljs-title">T</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">GetxController</span>> <span class="hljs-keyword">extends</span> <span class="hljs-title">State</span><<span class="hljs-title">GetBuilder</span><<span class="hljs-title">T</span>>>
    <span class="hljs-title">with</span> <span class="hljs-title">GetStateUpdaterMixin</span> </span>&#123;
  T? controller;

  <span class="hljs-meta">@override</span>
  <span class="hljs-keyword">void</span> initState() &#123;
    <span class="hljs-keyword">super</span>.initState();
    ...
     
    <span class="hljs-keyword">if</span> (widget.global) &#123;
      <span class="hljs-keyword">if</span> (isRegistered) &#123;
        controller = GetInstance().find<T>(tag: widget.tag);
      &#125; <span class="hljs-keyword">else</span> &#123;
        controller = widget.init;
        GetInstance().put<T>(controller!, tag: widget.tag);
      &#125;
    &#125; <span class="hljs-keyword">else</span> &#123;
      controller = widget.init;
      controller?.onStart();
    &#125;

    _subscribeToController();
  &#125;

  <span class="hljs-keyword">void</span> _subscribeToController() &#123;
    _remove?.call();
    _remove = (widget.id == <span class="hljs-keyword">null</span>)
        ? controller?.addListener(
            _filter != <span class="hljs-keyword">null</span> ? _filterUpdate : getUpdate,
          )
        : controller?.addListenerId(
            widget.id,
            _filter != <span class="hljs-keyword">null</span> ? _filterUpdate : getUpdate,
          );
  &#125;

  <span class="hljs-keyword">void</span> _filterUpdate() &#123;
    <span class="hljs-keyword">var</span> newFilter = widget.filter!(controller!);
    <span class="hljs-keyword">if</span> (newFilter != _filter) &#123;
      _filter = newFilter;
      getUpdate();
    &#125;
  &#125;

  <span class="hljs-meta">@override</span>
  <span class="hljs-keyword">void</span> didChangeDependencies() &#123;
    <span class="hljs-keyword">super</span>.didChangeDependencies();
    widget.didChangeDependencies?.call(<span class="hljs-keyword">this</span>);
  &#125;

  <span class="hljs-meta">@override</span>
  <span class="hljs-keyword">void</span> didUpdateWidget(GetBuilder oldWidget) &#123;
    <span class="hljs-keyword">super</span>.didUpdateWidget(oldWidget <span class="hljs-keyword">as</span> GetBuilder<T>);
    <span class="hljs-keyword">if</span> (oldWidget.id != widget.id) &#123;
      _subscribeToController();
    &#125;
    widget.didUpdateWidget?.call(oldWidget, <span class="hljs-keyword">this</span>);
  &#125;

  <span class="hljs-meta">@override</span>
  Widget build(BuildContext context) &#123;
    <span class="hljs-keyword">return</span> widget.builder(controller!);
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><strong>关键步骤</strong></p>
<ol>
<li>通过泛型获取注入的GetXController实例</li>
<li>添加监听代码
<ul>
<li>addListener：添加监听回调</li>
<li>addListenerId：添加监听回调，必须设置id，update刷新的时候也必须写上配套的id</li>
</ul>
</li>
<li>监听代码：核心代码就是getUpdate方法，方法在 GetStateUpdaterMixin 中
<ul>
<li>getUpdate()逻辑就是 setState()，刷新当前GetBuilder</li>
</ul>
</li>
</ol>
<blockquote>
<p><strong>图示</strong></p>
</blockquote>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/aacc1d13913a401bbb556aae09dc43e7~tplv-k3u1fbpfcp-zoom-1.image" alt="GetBuilder" loading="lazy" referrerpolicy="no-referrer"></p>
<h2 data-id="heading-16">Update</h2>
<ul>
<li>触发逻辑还是很简单的，使用update即可
<ul>
<li>Ids：和上面的Getbuilder对应起来了，可刷新对应设置id的GetBuilder</li>
<li>condition：是否刷新一个判断条件，默认为true（假设必须某个id大于3才能刷新：update([1, 2, 3, 4], index > 3) ）</li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-keyword">abstract</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">GetxController</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">DisposableInterface</span> <span class="hljs-title">with</span> <span class="hljs-title">ListNotifier</span> </span>&#123;
  <span class="hljs-keyword">void</span> update([<span class="hljs-built_in">List</span><<span class="hljs-built_in">Object</span>>? ids, <span class="hljs-built_in">bool</span> condition = <span class="hljs-keyword">true</span>]) &#123;
    <span class="hljs-keyword">if</span> (!condition) &#123;
      <span class="hljs-keyword">return</span>;
    &#125;
    <span class="hljs-keyword">if</span> (ids == <span class="hljs-keyword">null</span>) &#123;
      refresh();
    &#125; <span class="hljs-keyword">else</span> &#123;
      <span class="hljs-keyword">for</span> (<span class="hljs-keyword">final</span> id <span class="hljs-keyword">in</span> ids) &#123;
        refreshGroup(id);
      &#125;
    &#125;
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>看下关键方法 refresh()，在ListNotifier类中
<ul>
<li>可以发现，_updaters中泛型就是一个方法</li>
<li>在GetBuilder中添加的监听就是一个方法参数，方法体里面就是 setState()</li>
<li>齐活了！GetBuilder添加方法（方法体是setState），update遍历触发所有添加方法</li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-keyword">typedef</span> GetStateUpdate = <span class="hljs-keyword">void</span> <span class="hljs-built_in">Function</span>();
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">ListNotifier</span> <span class="hljs-keyword">implements</span> <span class="hljs-title">Listenable</span> </span>&#123;
  <span class="hljs-built_in">List</span><GetStateUpdate?>? _updaters = <GetStateUpdate?>[];

  HashMap<<span class="hljs-built_in">Object?</span>, <span class="hljs-built_in">List</span><GetStateUpdate>>? _updatersGroupIds =
      HashMap<<span class="hljs-built_in">Object?</span>, <span class="hljs-built_in">List</span><GetStateUpdate>>();

  <span class="hljs-meta">@protected</span>
  <span class="hljs-keyword">void</span> refresh() &#123;
    <span class="hljs-keyword">assert</span>(_debugAssertNotDisposed());
    _notifyUpdate();
  &#125;

  <span class="hljs-keyword">void</span> _notifyUpdate() &#123;
    <span class="hljs-keyword">for</span> (<span class="hljs-keyword">var</span> element <span class="hljs-keyword">in</span> _updaters!) &#123;
      element!();
    &#125;
  &#125;

  ...
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>如果在update中加了id参数，会走refreshGroup方法，逻辑和refresh几乎一样，差别是对id的判断：有则执行，无则跳过
<ul>
<li>遍历所有ids，然后执行refreshGroup方法</li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-keyword">abstract</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">GetxController</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">DisposableInterface</span> <span class="hljs-title">with</span> <span class="hljs-title">ListNotifier</span> </span>&#123;
  <span class="hljs-keyword">void</span> update([<span class="hljs-built_in">List</span><<span class="hljs-built_in">Object</span>>? ids, <span class="hljs-built_in">bool</span> condition = <span class="hljs-keyword">true</span>]) &#123;
    <span class="hljs-keyword">if</span> (!condition) &#123;
      <span class="hljs-keyword">return</span>;
    &#125;
    <span class="hljs-keyword">if</span> (ids == <span class="hljs-keyword">null</span>) &#123;
      refresh();
    &#125; <span class="hljs-keyword">else</span> &#123;
      <span class="hljs-keyword">for</span> (<span class="hljs-keyword">final</span> id <span class="hljs-keyword">in</span> ids) &#123;
        refreshGroup(id);
      &#125;
    &#125;
  &#125;
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">ListNotifier</span> <span class="hljs-keyword">implements</span> <span class="hljs-title">Listenable</span> </span>&#123;
  HashMap<<span class="hljs-built_in">Object?</span>, <span class="hljs-built_in">List</span><GetStateUpdate>>? _updatersGroupIds =
      HashMap<<span class="hljs-built_in">Object?</span>, <span class="hljs-built_in">List</span><GetStateUpdate>>();

  <span class="hljs-keyword">void</span> _notifyIdUpdate(<span class="hljs-built_in">Object</span> id) &#123;
    <span class="hljs-keyword">if</span> (_updatersGroupIds!.containsKey(id)) &#123;
      <span class="hljs-keyword">final</span> listGroup = _updatersGroupIds![id]!;
      <span class="hljs-keyword">for</span> (<span class="hljs-keyword">var</span> item <span class="hljs-keyword">in</span> listGroup) &#123;
        item();
      &#125;
    &#125;
  &#125;

  <span class="hljs-meta">@protected</span>
  <span class="hljs-keyword">void</span> refreshGroup(<span class="hljs-built_in">Object</span> id) &#123;
    <span class="hljs-keyword">assert</span>(_debugAssertNotDisposed());
    _notifyIdUpdate(id);
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-17">总结</h2>
<ul>
<li>来看下GetBuilder刷新图示</li>
</ul>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c6ff6fb2189d460db7b962392c130ec8~tplv-k3u1fbpfcp-zoom-1.image" alt="GetBuilder刷新机制" loading="lazy" referrerpolicy="no-referrer"></p>
<h1 data-id="heading-18">Obx刷新机制</h1>
<p>这套刷新机制，和我们常用的状态管理框架（provider，bloc）以及上面的GetBuilder，在使用上有一些区别</p>
<ul>
<li>
<p>变量上：基础类型，实体以及列表之类的数据类型，作者都封装了一套Rx类型，快捷在数据后加obs</p>
<ul>
<li>例如：RxString msg  = "test".obs（var  msg  = "test".obs）</li>
</ul>
</li>
<li>
<p>更新上：基础类型直接更新数据就行，实体需要以 .update() 的形式</p>
</li>
<li>
<p>使用上：使用这类变量，一般要加上 <strong>.value</strong> ，作者也给出一个快捷方式变量后面加个 <strong>()</strong></p>
<ul>
<li>我不太推荐加  <strong>()</strong> 的形式，对后续维护项目人太不友好了</li>
</ul>
</li>
</ul>
<p><strong>Obx刷新机制，最有趣应该就是变量改变后，包裹该变量的Obx会自动刷新！注意喔，仅仅是包裹该变量的Obx会刷新！其它的Obx并不会刷新。</strong></p>
<p>这是怎么做到的呢？</p>
<ul>
<li>实际上，实现起来很简单</li>
<li>但是，如果没有接触过这个思路，恐怕抓破头，都很难想出来，还能这么玩。。。</li>
</ul>
<h2 data-id="heading-19">使用</h2>
<p>简单的来看下使用</p>
<ul>
<li>logic</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">GetCounterRxLogic</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">GetxController</span> </span>&#123;
  <span class="hljs-keyword">var</span> count = <span class="hljs-number">0.</span>obs;

  <span class="hljs-comment">///<span class="markdown">自增</span></span>
  <span class="hljs-keyword">void</span> increase() => ++count;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>view</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">GetCounterRxPage</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">StatelessWidget</span> </span>&#123;
  <span class="hljs-keyword">final</span> GetCounterRxLogic logic = Get.put(GetCounterRxLogic());

  <span class="hljs-meta">@override</span>
  Widget build(BuildContext context) &#123;
    <span class="hljs-keyword">return</span> BaseScaffold(
      appBar: AppBar(title: <span class="hljs-keyword">const</span> Text(<span class="hljs-string">'计数器-响应式'</span>)),
      body: Center(
        child: Obx(() &#123;
          <span class="hljs-keyword">return</span> Text(
            <span class="hljs-string">'点击了 <span class="hljs-subst">$&#123;logic.count.value&#125;</span> 次'</span>,
            style: TextStyle(fontSize: <span class="hljs-number">30.0</span>),
          );
        &#125;),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: () => logic.increase(),
        child: Icon(Icons.add),
      ),
    );
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-20">Rx类变量</h2>
<p>此处以  <strong>RxInt</strong> 为例，来看下其内部实现</p>
<ul>
<li>先来看下整型后面的拓展 <strong>obs</strong> ，这是一个扩展类，<strong>0.obs</strong> 等同 <strong>RxInt(0)</strong></li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-keyword">extension</span> IntExtension <span class="hljs-keyword">on</span> <span class="hljs-built_in">int</span> &#123;
  <span class="hljs-comment">/// <span class="markdown">Returns a <span class="hljs-code">`RxInt`</span> with [this] <span class="hljs-code">`int`</span> as initial value.</span></span>
  RxInt <span class="hljs-keyword">get</span> obs => RxInt(<span class="hljs-keyword">this</span>);
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>来看下RxInt：这地方明确了使用 .value 运行时，会自动返回一个当前实例，并修改相应value数值</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">RxInt</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Rx</span><<span class="hljs-title">int</span>> </span>&#123;
  RxInt(<span class="hljs-built_in">int</span> initial) : <span class="hljs-keyword">super</span>(initial);

  <span class="hljs-comment">/// <span class="markdown">Addition operator.</span></span>
  RxInt <span class="hljs-keyword">operator</span> +(<span class="hljs-built_in">int</span> other) &#123;
    value = value + other;
    <span class="hljs-keyword">return</span> <span class="hljs-keyword">this</span>;
  &#125;

  <span class="hljs-comment">/// <span class="markdown">Subtraction operator.</span></span>
  RxInt <span class="hljs-keyword">operator</span> -(<span class="hljs-built_in">int</span> other) &#123;
    value = value - other;
    <span class="hljs-keyword">return</span> <span class="hljs-keyword">this</span>;
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>来看下父类 <strong>Rx</strong>
<ul>
<li>这地方出现了一个很重要的类：  <strong>_RxImpl</strong></li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Rx</span><<span class="hljs-title">T</span>> <span class="hljs-keyword">extends</span> <span class="hljs-title">_RxImpl</span><<span class="hljs-title">T</span>> </span>&#123;
  Rx(T initial) : <span class="hljs-keyword">super</span>(initial);

  <span class="hljs-meta">@override</span>
  <span class="hljs-built_in">dynamic</span> toJson() &#123;
    <span class="hljs-keyword">try</span> &#123;
      <span class="hljs-keyword">return</span> (value <span class="hljs-keyword">as</span> <span class="hljs-built_in">dynamic</span>)?.toJson();
    &#125; <span class="hljs-keyword">on</span> Exception <span class="hljs-keyword">catch</span> (_) &#123;
      <span class="hljs-keyword">throw</span> <span class="hljs-string">'<span class="hljs-subst">$T</span> has not method [toJson]'</span>;
    &#125;
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>_RxImpl 类继承了 RxNotifier 和 with 了 RxObjectMixin</li>
<li>这个类内容是比较庞大的，主要是 RxNotifier 和 RxObjectMixin 内容很多</li>
<li>代码很多，先展示下完整代码；在下一个说明处会进行简化</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-keyword">abstract</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">_RxImpl</span><<span class="hljs-title">T</span>> <span class="hljs-keyword">extends</span> <span class="hljs-title">RxNotifier</span><<span class="hljs-title">T</span>> <span class="hljs-title">with</span> <span class="hljs-title">RxObjectMixin</span><<span class="hljs-title">T</span>> </span>&#123;
  _RxImpl(T initial) &#123;
    _value = initial;
  &#125;

  <span class="hljs-keyword">void</span> addError(<span class="hljs-built_in">Object</span> error, [StackTrace? stackTrace]) &#123;
    subject.addError(error, stackTrace);
  &#125;

  Stream<R> map<R>(R mapper(T? data)) => stream.map(mapper);

  <span class="hljs-keyword">void</span> update(<span class="hljs-keyword">void</span> fn(T? val)) &#123;
    fn(_value);
    subject.add(_value);
  &#125;

  <span class="hljs-keyword">void</span> trigger(T v) &#123;
    <span class="hljs-keyword">var</span> firstRebuild = <span class="hljs-keyword">this</span>.firstRebuild;
    value = v;
    <span class="hljs-keyword">if</span> (!firstRebuild) &#123;
      subject.add(v);
    &#125;
  &#125;
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">RxNotifier</span><<span class="hljs-title">T</span>> = <span class="hljs-title">RxInterface</span><<span class="hljs-title">T</span>> <span class="hljs-title">with</span> <span class="hljs-title">NotifyManager</span><<span class="hljs-title">T</span>>;

<span class="hljs-title">mixin</span> <span class="hljs-title">NotifyManager</span><<span class="hljs-title">T</span>> </span>&#123;
  GetStream<T> subject = GetStream<T>();
  <span class="hljs-keyword">final</span> _subscriptions = <GetStream, <span class="hljs-built_in">List</span><StreamSubscription>>&#123;&#125;;

  <span class="hljs-built_in">bool</span> <span class="hljs-keyword">get</span> canUpdate => _subscriptions.isNotEmpty;

  <span class="hljs-keyword">void</span> addListener(GetStream<T> rxGetx) &#123;
    <span class="hljs-keyword">if</span> (!_subscriptions.containsKey(rxGetx)) &#123;
      <span class="hljs-keyword">final</span> subs = rxGetx.listen((data) &#123;
        <span class="hljs-keyword">if</span> (!subject.isClosed) subject.add(data);
      &#125;);
      <span class="hljs-keyword">final</span> listSubscriptions =
          _subscriptions[rxGetx] ??= <StreamSubscription>[];
      listSubscriptions.add(subs);
    &#125;
  &#125;

  StreamSubscription<T> listen(
    <span class="hljs-keyword">void</span> <span class="hljs-built_in">Function</span>(T) onData, &#123;
    <span class="hljs-built_in">Function?</span> onError,
    <span class="hljs-keyword">void</span> <span class="hljs-built_in">Function</span>()? onDone,
    <span class="hljs-built_in">bool?</span> cancelOnError,
  &#125;) =>
      subject.listen(
        onData,
        onError: onError,
        onDone: onDone,
        cancelOnError: cancelOnError ?? <span class="hljs-keyword">false</span>,
      );

  <span class="hljs-keyword">void</span> close() &#123;
    _subscriptions.forEach((getStream, _subscriptions) &#123;
      <span class="hljs-keyword">for</span> (<span class="hljs-keyword">final</span> subscription <span class="hljs-keyword">in</span> _subscriptions) &#123;
        subscription.cancel();
      &#125;
    &#125;);

    _subscriptions.clear();
    subject.close();
  &#125;
&#125;

<span class="hljs-keyword">mixin</span> RxObjectMixin<T> <span class="hljs-keyword">on</span> NotifyManager<T> &#123;
  <span class="hljs-keyword">late</span> T _value;

  <span class="hljs-keyword">void</span> refresh() &#123;
    subject.add(value);
  &#125;

  T call([T? v]) &#123;
    <span class="hljs-keyword">if</span> (v != <span class="hljs-keyword">null</span>) &#123;
      value = v;
    &#125;
    <span class="hljs-keyword">return</span> value;
  &#125;

  <span class="hljs-built_in">bool</span> firstRebuild = <span class="hljs-keyword">true</span>;

  <span class="hljs-built_in">String</span> <span class="hljs-keyword">get</span> string => value.toString();

  <span class="hljs-meta">@override</span>
  <span class="hljs-built_in">String</span> toString() => value.toString();

  <span class="hljs-built_in">dynamic</span> toJson() => value;

  <span class="hljs-meta">@override</span>
  <span class="hljs-built_in">bool</span> <span class="hljs-keyword">operator</span> ==(<span class="hljs-built_in">dynamic</span> o) &#123;
    <span class="hljs-keyword">if</span> (o <span class="hljs-keyword">is</span> T) <span class="hljs-keyword">return</span> value == o;
    <span class="hljs-keyword">if</span> (o <span class="hljs-keyword">is</span> RxObjectMixin<T>) <span class="hljs-keyword">return</span> value == o.value;
    <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>;
  &#125;

  <span class="hljs-meta">@override</span>
  <span class="hljs-built_in">int</span> <span class="hljs-keyword">get</span> hashCode => _value.hashCode;

  <span class="hljs-keyword">set</span> value(T val) &#123;
    <span class="hljs-keyword">if</span> (subject.isClosed) <span class="hljs-keyword">return</span>;
    <span class="hljs-keyword">if</span> (_value == val && !firstRebuild) <span class="hljs-keyword">return</span>;
    firstRebuild = <span class="hljs-keyword">false</span>;
    _value = val;

    subject.add(_value);
  &#125;

  T <span class="hljs-keyword">get</span> value &#123;
    <span class="hljs-keyword">if</span> (RxInterface.proxy != <span class="hljs-keyword">null</span>) &#123;
      RxInterface.proxy!.addListener(subject);
    &#125;
    <span class="hljs-keyword">return</span> _value;
  &#125;

  Stream<T?> <span class="hljs-keyword">get</span> stream => subject.stream;

  <span class="hljs-keyword">void</span> bindStream(Stream<T> stream) &#123;
    <span class="hljs-keyword">final</span> listSubscriptions =
        _subscriptions[subject] ??= <StreamSubscription>[];
    listSubscriptions.add(stream.listen((va) => value = va));
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>简化 _RxImpl，上面内容太多了，我这地方简化下，把需要关注的内容展示出来：此处有几个需要重点关注的点
<ul>
<li><strong>RxInt是一个内置callback的数据类型（GetStream）</strong></li>
<li><strong>RxInt的value变量改变的时候（set value），会触发subject.add(_value)，内部逻辑是自动刷新操作</strong></li>
<li><strong>获取RxInt的value变量的时候（get value），会有一个添加监听的操作，这个灰常重要！</strong></li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-keyword">abstract</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">_RxImpl</span><<span class="hljs-title">T</span>> <span class="hljs-keyword">extends</span> <span class="hljs-title">RxNotifier</span><<span class="hljs-title">T</span>> <span class="hljs-title">with</span> <span class="hljs-title">RxObjectMixin</span><<span class="hljs-title">T</span>> </span>&#123;

  <span class="hljs-keyword">void</span> update(<span class="hljs-keyword">void</span> fn(T? val)) &#123;
    fn(_value);
    subject.add(_value);
  &#125;
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">RxNotifier</span><<span class="hljs-title">T</span>> = <span class="hljs-title">RxInterface</span><<span class="hljs-title">T</span>> <span class="hljs-title">with</span> <span class="hljs-title">NotifyManager</span><<span class="hljs-title">T</span>>;

<span class="hljs-title">mixin</span> <span class="hljs-title">NotifyManager</span><<span class="hljs-title">T</span>> </span>&#123;
  GetStream<T> subject = GetStream<T>();
  <span class="hljs-keyword">final</span> _subscriptions = <GetStream, <span class="hljs-built_in">List</span><StreamSubscription>>&#123;&#125;;

  <span class="hljs-built_in">bool</span> <span class="hljs-keyword">get</span> canUpdate => _subscriptions.isNotEmpty;

  <span class="hljs-keyword">void</span> addListener(GetStream<T> rxGetx) &#123;
    <span class="hljs-keyword">if</span> (!_subscriptions.containsKey(rxGetx)) &#123;
      <span class="hljs-keyword">final</span> subs = rxGetx.listen((data) &#123;
        <span class="hljs-keyword">if</span> (!subject.isClosed) subject.add(data);
      &#125;);
      <span class="hljs-keyword">final</span> listSubscriptions =
          _subscriptions[rxGetx] ??= <StreamSubscription>[];
      listSubscriptions.add(subs);
    &#125;
  &#125;
&#125;

<span class="hljs-keyword">mixin</span> RxObjectMixin<T> <span class="hljs-keyword">on</span> NotifyManager<T> &#123;
  <span class="hljs-keyword">late</span> T _value;

  <span class="hljs-keyword">void</span> refresh() &#123;
    subject.add(value);
  &#125;

  <span class="hljs-keyword">set</span> value(T val) &#123;
    <span class="hljs-keyword">if</span> (subject.isClosed) <span class="hljs-keyword">return</span>;
    <span class="hljs-keyword">if</span> (_value == val && !firstRebuild) <span class="hljs-keyword">return</span>;
    firstRebuild = <span class="hljs-keyword">false</span>;
    _value = val;

    subject.add(_value);
  &#125;

  T <span class="hljs-keyword">get</span> value &#123;
    <span class="hljs-keyword">if</span> (RxInterface.proxy != <span class="hljs-keyword">null</span>) &#123;
      RxInterface.proxy!.addListener(subject);
    &#125;
    <span class="hljs-keyword">return</span> _value;
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>为啥GetStream的add会有刷新操作：删了很多代码，保留了重点代码
<ul>
<li>调用add方法时候，会调用 _notifyData 方法</li>
<li>_notifyData 方法中，会遍历 _onData 列表，根据条件会执行其泛型的 _data 的方法</li>
<li>我猜，_data 中的方法体，十有八九在某个地方肯定添加了 setState()</li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">GetStream</span><<span class="hljs-title">T</span>> </span>&#123;
  GetStream(&#123;<span class="hljs-keyword">this</span>.onListen, <span class="hljs-keyword">this</span>.onPause, <span class="hljs-keyword">this</span>.onResume, <span class="hljs-keyword">this</span>.onCancel&#125;);
  <span class="hljs-built_in">List</span><LightSubscription<T>>? _onData = <LightSubscription<T>>[];

  FutureOr<<span class="hljs-keyword">void</span>> addSubscription(LightSubscription<T> subs) <span class="hljs-keyword">async</span> &#123;
    <span class="hljs-keyword">if</span> (!_isBusy!) &#123;
      <span class="hljs-keyword">return</span> _onData!.add(subs);
    &#125; <span class="hljs-keyword">else</span> &#123;
      <span class="hljs-keyword">await</span> Future.delayed(<span class="hljs-built_in">Duration</span>.zero);
      <span class="hljs-keyword">return</span> _onData!.add(subs);
    &#125;
  &#125;

  <span class="hljs-keyword">void</span> _notifyData(T data) &#123;
    _isBusy = <span class="hljs-keyword">true</span>;
    <span class="hljs-keyword">for</span> (<span class="hljs-keyword">final</span> item <span class="hljs-keyword">in</span> _onData!) &#123;
      <span class="hljs-keyword">if</span> (!item.isPaused) &#123;
        item._data?.call(data);
      &#125;
    &#125;
    _isBusy = <span class="hljs-keyword">false</span>;
  &#125;

  T? _value;

  T? <span class="hljs-keyword">get</span> value => _value;

  <span class="hljs-keyword">void</span> add(T event) &#123;
    <span class="hljs-keyword">assert</span>(!isClosed, <span class="hljs-string">'You cannot add event to closed Stream'</span>);
    _value = event;
    _notifyData(event);
  &#125;
&#125;

<span class="hljs-keyword">typedef</span> OnData<T> = <span class="hljs-keyword">void</span> <span class="hljs-built_in">Function</span>(T data);

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">LightSubscription</span><<span class="hljs-title">T</span>> <span class="hljs-keyword">extends</span> <span class="hljs-title">StreamSubscription</span><<span class="hljs-title">T</span>> </span>&#123;
  OnData<T>? _data;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>图示，先来看下，Rx类具有的功能
<ul>
<li>get value 添加监听</li>
<li>set value 执行已添加的监听</li>
</ul>
</li>
</ul>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1fb0ca3570ba482bb8c3f35f2650ea2a~tplv-k3u1fbpfcp-zoom-1.image" alt="Rx类变量" loading="lazy" referrerpolicy="no-referrer"></p>
<h2 data-id="heading-21">Obx刷新机制</h2>
<blockquote>
<p>Obx最大的特殊之处，应该就是使用它的时候，不需要加泛型且能自动刷新，这是怎么做到的呢？</p>
</blockquote>
<ul>
<li>Obx：代码并不多，但是皆有妙用
<ul>
<li>Obx继承ObxWidget，ObxWidget实际上也是一个StatefulWidget</li>
<li>_ObxState 中代码就是核心代码了</li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Obx</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">ObxWidget</span> </span>&#123;
  <span class="hljs-keyword">final</span> WidgetCallback builder;

  <span class="hljs-keyword">const</span> Obx(<span class="hljs-keyword">this</span>.builder);

  <span class="hljs-meta">@override</span>
  Widget build() => builder();
&#125;


<span class="hljs-keyword">abstract</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">ObxWidget</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">StatefulWidget</span> </span>&#123;
  <span class="hljs-keyword">const</span> ObxWidget(&#123;Key? key&#125;) : <span class="hljs-keyword">super</span>(key: key);

  <span class="hljs-meta">@override</span>
  _ObxState createState() => _ObxState();

  <span class="hljs-meta">@protected</span>
  Widget build();
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">_ObxState</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">State</span><<span class="hljs-title">ObxWidget</span>> </span>&#123;
  RxInterface? _observer;
  <span class="hljs-keyword">late</span> StreamSubscription subs;

  _ObxState() &#123;
    _observer = RxNotifier();
  &#125;

  <span class="hljs-meta">@override</span>
  <span class="hljs-keyword">void</span> initState() &#123;
    subs = _observer!.listen(_updateTree, cancelOnError: <span class="hljs-keyword">false</span>);
    <span class="hljs-keyword">super</span>.initState();
  &#125;

  <span class="hljs-keyword">void</span> _updateTree(_) &#123;
    <span class="hljs-keyword">if</span> (mounted) &#123;
      setState(() &#123;&#125;);
    &#125;
  &#125;

  <span class="hljs-meta">@override</span>
  <span class="hljs-keyword">void</span> dispose() &#123;
    subs.cancel();
    _observer!.close();
    <span class="hljs-keyword">super</span>.dispose();
  &#125;

  Widget <span class="hljs-keyword">get</span> notifyChilds &#123;
    <span class="hljs-keyword">final</span> observer = RxInterface.proxy;
    RxInterface.proxy = _observer;
    <span class="hljs-keyword">final</span> result = widget.build();
    <span class="hljs-keyword">if</span> (!_observer!.canUpdate) &#123;
      <span class="hljs-keyword">throw</span> <span class="hljs-string">"""
      [Get] the improper use of a GetX has been detected. 
      You should only use GetX or Obx for the specific widget that will be updated.
      If you are seeing this error, you probably did not insert any observable variables into GetX/Obx 
      or insert them outside the scope that GetX considers suitable for an update 
      (example: GetX => HeavyWidget => variableObservable).
      If you need to update a parent widget and a child widget, wrap each one in an Obx/GetX.
      """</span>;
    &#125;
    RxInterface.proxy = observer;
    <span class="hljs-keyword">return</span> result;
  &#125;

  <span class="hljs-meta">@override</span>
  Widget build(BuildContext context) => notifyChilds;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-22">添加监听</h3>
<blockquote>
<p>一个控件想刷新，肯定有添加监听的逻辑，再在某个地方手动触发</p>
</blockquote>
<ul>
<li>
<p>看下_ObxState类在哪添加监听：只展示监听添加的代码</p>
</li>
<li>
<p><strong>_ObxState初始化的时候，会实例化一个 RxNotifier() 对象，使用 _observer变量接受：这个操作很重要</strong></p>
</li>
<li>
<p>initState中做了一个比较关键的操作，_observer的listener方法中，将 _updateTree方法传进去了，这个方法中的逻辑体就是  setState()</p>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">_ObxState</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">State</span><<span class="hljs-title">ObxWidget</span>> </span>&#123;
  RxInterface? _observer;
  <span class="hljs-keyword">late</span> StreamSubscription subs;

  _ObxState() &#123;
    _observer = RxNotifier();
  &#125;

  <span class="hljs-meta">@override</span>
  <span class="hljs-keyword">void</span> initState() &#123;
    subs = _observer!.listen(_updateTree, cancelOnError: <span class="hljs-keyword">false</span>);
    <span class="hljs-keyword">super</span>.initState();
  &#125;

  <span class="hljs-keyword">void</span> _updateTree(_) &#123;
    <span class="hljs-keyword">if</span> (mounted) &#123;
      setState(() &#123;&#125;);
    &#125;
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上述很多逻辑和 RxNotifier 类相关，来看下这个类</p>
<ul>
<li>RxNotifier 这个类，内部会实例一个 GetStream() 对象，然后赋值给 subject</li>
<li>上面赋值 _updateTree 方法被传入的  GetStream() 类中，最终添加 _onData 该列表变量中</li>
<li>瞟一眼  _notifyData方法，是不是遍历执行了  _onData 列表中item的方法（ item. _data?.call(data) ）</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">RxNotifier</span><<span class="hljs-title">T</span>> = <span class="hljs-title">RxInterface</span><<span class="hljs-title">T</span>> <span class="hljs-title">with</span> <span class="hljs-title">NotifyManager</span><<span class="hljs-title">T</span>>;

<span class="hljs-title">mixin</span> <span class="hljs-title">NotifyManager</span><<span class="hljs-title">T</span>> </span>&#123;
  GetStream<T> subject = GetStream<T>();
  <span class="hljs-keyword">final</span> _subscriptions = <GetStream, <span class="hljs-built_in">List</span><StreamSubscription>>&#123;&#125;;

  <span class="hljs-built_in">bool</span> <span class="hljs-keyword">get</span> canUpdate => _subscriptions.isNotEmpty;

  StreamSubscription<T> listen(
    <span class="hljs-keyword">void</span> <span class="hljs-built_in">Function</span>(T) onData, &#123;
    <span class="hljs-built_in">Function?</span> onError,
    <span class="hljs-keyword">void</span> <span class="hljs-built_in">Function</span>()? onDone,
    <span class="hljs-built_in">bool?</span> cancelOnError,
  &#125;) =>
      subject.listen(
        onData,
        onError: onError,
        onDone: onDone,
        cancelOnError: cancelOnError ?? <span class="hljs-keyword">false</span>,
      );
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">GetStream</span><<span class="hljs-title">T</span>> </span>&#123;
  <span class="hljs-keyword">void</span> <span class="hljs-built_in">Function</span>()? onListen;
  <span class="hljs-keyword">void</span> <span class="hljs-built_in">Function</span>()? onPause;
  <span class="hljs-keyword">void</span> <span class="hljs-built_in">Function</span>()? onResume;
  FutureOr<<span class="hljs-keyword">void</span>> <span class="hljs-built_in">Function</span>()? onCancel;

  GetStream(&#123;<span class="hljs-keyword">this</span>.onListen, <span class="hljs-keyword">this</span>.onPause, <span class="hljs-keyword">this</span>.onResume, <span class="hljs-keyword">this</span>.onCancel&#125;);
  <span class="hljs-built_in">List</span><LightSubscription<T>>? _onData = <LightSubscription<T>>[];

  FutureOr<<span class="hljs-keyword">void</span>> addSubscription(LightSubscription<T> subs) <span class="hljs-keyword">async</span> &#123;
    <span class="hljs-keyword">if</span> (!_isBusy!) &#123;
      <span class="hljs-keyword">return</span> _onData!.add(subs);
    &#125; <span class="hljs-keyword">else</span> &#123;
      <span class="hljs-keyword">await</span> Future.delayed(<span class="hljs-built_in">Duration</span>.zero);
      <span class="hljs-keyword">return</span> _onData!.add(subs);
    &#125;
  &#125;

  <span class="hljs-built_in">int?</span> <span class="hljs-keyword">get</span> length => _onData?.length;

  <span class="hljs-built_in">bool</span> <span class="hljs-keyword">get</span> hasListeners => _onData!.isNotEmpty;
    
  <span class="hljs-keyword">void</span> _notifyData(T data) &#123;
    _isBusy = <span class="hljs-keyword">true</span>;
    <span class="hljs-keyword">for</span> (<span class="hljs-keyword">final</span> item <span class="hljs-keyword">in</span> _onData!) &#123;
      <span class="hljs-keyword">if</span> (!item.isPaused) &#123;
        item._data?.call(data);
      &#125;
    &#125;
    _isBusy = <span class="hljs-keyword">false</span>;
  &#125;

  LightSubscription<T> listen(<span class="hljs-keyword">void</span> <span class="hljs-built_in">Function</span>(T event) onData,
      &#123;<span class="hljs-built_in">Function?</span> onError, <span class="hljs-keyword">void</span> <span class="hljs-built_in">Function</span>()? onDone, <span class="hljs-built_in">bool?</span> cancelOnError&#125;) &#123;
    <span class="hljs-keyword">final</span> subs = LightSubscription<T>(
      removeSubscription,
      onPause: onPause,
      onResume: onResume,
      onCancel: onCancel,
    )
      ..onData(onData)
      ..onError(onError)
      ..onDone(onDone)
      ..cancelOnError = cancelOnError;
    addSubscription(subs);
    onListen?.call();
    <span class="hljs-keyword">return</span> subs;
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>上面代码流程有一点绕，下面画了一个图，希望对各位有所帮助</li>
</ul>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e6d0cbba6d1149398b026ecb7b840b6e~tplv-k3u1fbpfcp-zoom-1.image" alt="Obx监听添加" loading="lazy" referrerpolicy="no-referrer"></p>
<h3 data-id="heading-23">监听转移</h3>
<blockquote>
<p><strong>在_ObxState类中做了一个很重要，监听对象转移的操作</strong></p>
<p><strong>_observer中的对象已经拿到了Obx控件内部的setState方法，现在需要将它转移出去啦！</strong></p>
</blockquote>
<ul>
<li>下面贴下将 _observer 中对象转移出去的代码：主要的逻辑就是在 notifyChilds 方法中
<ul>
<li><strong>RxInterface 类中有个 proxy 静态变量，这个变量十分重要，他是一个中转变量！</strong></li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart">`<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">_ObxState</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">State</span><<span class="hljs-title">ObxWidget</span>> </span>&#123;
  RxInterface? _observer;

  _ObxState() &#123;
    _observer = RxNotifier();
  &#125;

  Widget <span class="hljs-keyword">get</span> notifyChilds &#123;
    <span class="hljs-keyword">final</span> observer = RxInterface.proxy;
    RxInterface.proxy = _observer;
    <span class="hljs-keyword">final</span> result = widget.build();
    <span class="hljs-keyword">if</span> (!_observer!.canUpdate) &#123;
      <span class="hljs-keyword">throw</span> <span class="hljs-string">"""
      [Get] the improper use of a GetX has been detected. 
      You should only use GetX or Obx for the specific widget that will be updated.
      If you are seeing this error, you probably did not insert any observable variables into GetX/Obx 
      or insert them outside the scope that GetX considers suitable for an update 
      (example: GetX => HeavyWidget => variableObservable).
      If you need to update a parent widget and a child widget, wrap each one in an Obx/GetX.
      """</span>;
    &#125;
    RxInterface.proxy = observer;
    <span class="hljs-keyword">return</span> result;
  &#125;

  <span class="hljs-meta">@override</span>
  Widget build(BuildContext context) => notifyChilds;
&#125;

<span class="hljs-keyword">abstract</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">RxInterface</span><<span class="hljs-title">T</span>> </span>&#123;
  <span class="hljs-built_in">bool</span> <span class="hljs-keyword">get</span> canUpdate;

  <span class="hljs-keyword">void</span> addListener(GetStream<T> rxGetx);

  <span class="hljs-keyword">void</span> close();

  <span class="hljs-keyword">static</span> RxInterface? proxy;

  StreamSubscription<T> listen(<span class="hljs-keyword">void</span> <span class="hljs-built_in">Function</span>(T event) onData,
      &#123;<span class="hljs-built_in">Function?</span> onError, <span class="hljs-keyword">void</span> <span class="hljs-built_in">Function</span>()? onDone, <span class="hljs-built_in">bool?</span> cancelOnError&#125;);
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><strong>notifyChilds中的几行代码都有深意，一行行的解读下</strong></p>
<ul>
<li>
<p>final observer = RxInterface.proxy：RxInterface.proxy正常情况为空，但是，可能作为中间变量暂存对象的情况，现在暂时将他的对象取出来，存在observer变量中</p>
</li>
<li>
<p>RxInterface.proxy = _observer：将我们在 _ObxState类中实例化的 RxNotifier() 对象的地址，赋值给了RxInterface.proxy</p>
<ul>
<li>注意：这里，RxInterface.proxy中 RxNotifier() 实例，有当前Obx控件的setState() 方法</li>
</ul>
</li>
<li>
<p>final result = widget.build()：这个赋值相当重要了！调用我们在外部传进的Widget</p>
<ul>
<li>
<p>如果这个Widget中有响应式变量，那么一定会调用该变量中获取 get value</p>
</li>
<li>
<p>还记得get value的代码吗？</p>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-keyword">mixin</span> RxObjectMixin<T> <span class="hljs-keyword">on</span> NotifyManager<T> &#123;
  <span class="hljs-keyword">late</span> T _value;
    
  T <span class="hljs-keyword">get</span> value &#123;
    <span class="hljs-keyword">if</span> (RxInterface.proxy != <span class="hljs-keyword">null</span>) &#123;
      RxInterface.proxy!.addListener(subject);
    &#125;
    <span class="hljs-keyword">return</span> _value;
  &#125;
&#125;

<span class="hljs-keyword">mixin</span> NotifyManager<T> &#123;
  GetStream<T> subject = GetStream<T>();
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
</li>
<li>
<p>终于建立起联系了，将变量中 GetStream 实例，添加到了Obx中的 RxNotifier() 实例；RxNotifier() 实例中有一个 subject（GetStream ） 实例，Rx类型中数据变化会触发 subject 变化，最终刷新Obx</p>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-keyword">mixin</span> NotifyManager<T> &#123;
  GetStream<T> subject = GetStream<T>();
  <span class="hljs-keyword">final</span> _subscriptions = <GetStream, <span class="hljs-built_in">List</span><StreamSubscription>>&#123;&#125;;

  <span class="hljs-built_in">bool</span> <span class="hljs-keyword">get</span> canUpdate => _subscriptions.isNotEmpty;
    
  <span class="hljs-keyword">void</span> addListener(GetStream<T> rxGetx) &#123;
    <span class="hljs-keyword">if</span> (!_subscriptions.containsKey(rxGetx)) &#123;
      <span class="hljs-comment">//重点 GetStream中listen方法是用来添加监听方法的，add的时候会刷新监听方法</span>
      <span class="hljs-keyword">final</span> subs = rxGetx.listen((data) &#123;
        <span class="hljs-keyword">if</span> (!subject.isClosed) subject.add(data);
      &#125;);
      <span class="hljs-keyword">final</span> listSubscriptions =
          _subscriptions[rxGetx] ??= <StreamSubscription>[];
      listSubscriptions.add(subs);
    &#125;
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
</li>
</ul>
</li>
<li>
<p>if (!_observer!.canUpdate) &#123;&#125;：这个判断就很简单了，如果我们传入的Widget中没有Rx类型变量， _subscriptions数组就会为空，这个判断就会过不了</p>
</li>
<li>
<p>RxInterface.proxy = observer：将RxInterface.proxy中原来的值，重新赋给自己，至此 _ObxState 中的 _observer对象地址，进行了一番奇幻旅游后，结束了自己的使命</p>
</li>
</ul>
<blockquote>
<p>图示</p>
</blockquote>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/967390fa6b2a45e199bea2b498a65b84~tplv-k3u1fbpfcp-zoom-1.image" alt="Obx监听转移" loading="lazy" referrerpolicy="no-referrer"></p>
<h2 data-id="heading-24">总结</h2>
<p>Obx的刷新机制，还是蛮有有趣的</p>
<ul>
<li>Rx变量改变，自动刷新包裹其变量Obx控件，其它的Obx控件并不会刷新</li>
<li>使用Obx控件，不需要写泛型！牛批！</li>
</ul>
<p>但是，我认为Obx刷新机制，也是有着自身的缺陷的，从其实现原理上看，这是无法避免的</p>
<ul>
<li>因为Obx的自动刷新，必须需要每一个变量都自带监听触发机制；所以，所有的基础类型，实体以及列表，都需要重新封装，这会造成很严重的使用影响：<strong>变量的赋值，类型标定，刷新都很正常写法有差异，不熟悉该写法的人，看了后，会很难受</strong></li>
<li>因为对所有类型重新封装，经过上面的代码回溯，大家也发现，封装类型的代码相当多；封装类型占用资源肯定要比dart自带类型的大（这个问题可以避免：封装一个响应式的变量，并不一定需要很多代码，下面我给出了一个封装参考）</li>
</ul>
<h1 data-id="heading-25">手搓一个状态管理框架</h1>
<blockquote>
<p>GetX内置了俩套状态管理机制，这边也会按照其刷新机制，手搓俩套出来</p>
<p>我会用极其简单的代码，再现俩套经典的机制</p>
</blockquote>
<h2 data-id="heading-26">依赖注入</h2>
<ul>
<li>在做刷新机制前，首先必须写一个依赖注入的类，我们需要自己管理逻辑层的那些实例
<ul>
<li>我这边写了一个极其简单，仅实现三种基础功能：注入，获取，删除</li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-comment">///<span class="markdown">依赖注入，外部可将实例，注入该类中，由该类管理</span></span>
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Easy</span> </span>&#123;
  <span class="hljs-comment">///<span class="markdown">注入实例</span></span>
  <span class="hljs-keyword">static</span> T put<T>(T dependency, &#123;<span class="hljs-built_in">String?</span> tag&#125;) =>
      _EasyInstance().put(dependency, tag: tag);

  <span class="hljs-comment">///<span class="markdown">获取注入的实例</span></span>
  <span class="hljs-keyword">static</span> T find<T>(&#123;<span class="hljs-built_in">String?</span> tag, <span class="hljs-built_in">String?</span> key&#125;) =>
      _EasyInstance().find<T>(tag: tag, key: key);

  <span class="hljs-comment">///<span class="markdown">删除实例</span></span>
  <span class="hljs-keyword">static</span> <span class="hljs-built_in">bool</span> delete<T>(&#123;<span class="hljs-built_in">String?</span> tag, <span class="hljs-built_in">String?</span> key&#125;) =>
      _EasyInstance().delete<T>(tag: tag, key: key);
&#125;

<span class="hljs-comment">///<span class="markdown">具体逻辑</span></span>
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">_EasyInstance</span> </span>&#123;
  <span class="hljs-keyword">factory</span> _EasyInstance() => _instance ??= _EasyInstance._();

  <span class="hljs-keyword">static</span> _EasyInstance? _instance;

  _EasyInstance._();

  <span class="hljs-keyword">static</span> <span class="hljs-keyword">final</span> <span class="hljs-built_in">Map</span><<span class="hljs-built_in">String</span>, _InstanceInfo> _single = &#123;&#125;;

  <span class="hljs-comment">///<span class="markdown">注入实例</span></span>
  T put<T>(T dependency, &#123;<span class="hljs-built_in">String?</span> tag&#125;) &#123;
    <span class="hljs-keyword">final</span> key = _getKey(T, tag);
    <span class="hljs-comment">//多次注入会覆盖</span>
    _single[key] = _InstanceInfo<T>(dependency);
    <span class="hljs-keyword">return</span> find<T>(tag: tag);
  &#125;

  <span class="hljs-comment">///<span class="markdown">获取注入的实例</span></span>
  T find<T>(&#123;<span class="hljs-built_in">String?</span> tag, <span class="hljs-built_in">String?</span> key&#125;) &#123;
    <span class="hljs-keyword">final</span> newKey = key ?? _getKey(T, tag);
    <span class="hljs-keyword">var</span> info = _single[newKey];

    <span class="hljs-keyword">if</span> (info?.value != <span class="hljs-keyword">null</span>) &#123;
      <span class="hljs-keyword">return</span> info!.value;
    &#125; <span class="hljs-keyword">else</span> &#123;
      <span class="hljs-keyword">throw</span> <span class="hljs-string">'"<span class="hljs-subst">$T</span>" not found. You need to call "Easy.put(<span class="hljs-subst">$T</span>())""'</span>;
    &#125;
  &#125;

  <span class="hljs-comment">///<span class="markdown">删除实例</span></span>
  <span class="hljs-built_in">bool</span> delete<T>(&#123;<span class="hljs-built_in">String?</span> tag, <span class="hljs-built_in">String?</span> key&#125;) &#123;
    <span class="hljs-keyword">final</span> newKey = key ?? _getKey(T, tag);
    <span class="hljs-keyword">if</span> (!_single.containsKey(newKey)) &#123;
      <span class="hljs-built_in">print</span>(<span class="hljs-string">'Instance "<span class="hljs-subst">$newKey</span>" already removed.'</span>);
      <span class="hljs-keyword">return</span> <span class="hljs-keyword">false</span>;
    &#125;

    _single.remove(newKey);
    <span class="hljs-built_in">print</span>(<span class="hljs-string">'Instance "<span class="hljs-subst">$newKey</span>" deleted.'</span>);
    <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
  &#125;

  <span class="hljs-built_in">String</span> _getKey(<span class="hljs-built_in">Type</span> type, <span class="hljs-built_in">String?</span> name) &#123;
    <span class="hljs-keyword">return</span> name == <span class="hljs-keyword">null</span> ? type.toString() : type.toString() + name;
  &#125;
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">_InstanceInfo</span><<span class="hljs-title">T</span>> </span>&#123;
  _InstanceInfo(<span class="hljs-keyword">this</span>.value);

  T value;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>自定义一个监听类，这个类很重要，下面俩种机制都需要用到</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-comment">///<span class="markdown">自定义个监听触发类</span></span>
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">EasyXNotifier</span> </span>&#123;
  <span class="hljs-built_in">List</span><VoidCallback> _listeners = [];

  <span class="hljs-keyword">void</span> addListener(VoidCallback listener) &#123;
    _listeners.add(listener);
  &#125;

  <span class="hljs-keyword">void</span> removeListener(VoidCallback listener) &#123;
    <span class="hljs-keyword">for</span> (<span class="hljs-keyword">final</span> entry <span class="hljs-keyword">in</span> _listeners) &#123;
      <span class="hljs-keyword">if</span> (entry == listener) &#123;
        _listeners.remove(entry);
        <span class="hljs-keyword">return</span>;
      &#125;
    &#125;
  &#125;

  <span class="hljs-keyword">void</span> dispose() &#123;
    _listeners.clear();
  &#125;

  <span class="hljs-keyword">void</span> notify() &#123;
    <span class="hljs-keyword">if</span> (_listeners.isEmpty) <span class="hljs-keyword">return</span>;

    <span class="hljs-keyword">for</span> (<span class="hljs-keyword">final</span> entry <span class="hljs-keyword">in</span> _listeners) &#123;
      <span class="hljs-keyword">try</span> &#123;
        entry.call();
      &#125; <span class="hljs-keyword">catch</span> (e) &#123;
        <span class="hljs-built_in">print</span>(e.toString());
      &#125;
    &#125;
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-27">EasyBuilder</h2>
<h3 data-id="heading-28">实现</h3>
<ul>
<li>该模式需要自定义一个基类
<ul>
<li>我这地方写的极简，相关生命周期都没加，这个加起来也很容易，定义各个生命周期，在Builder控件里面触发，就可以了</li>
<li>为了代码简洁，这个暂且不表</li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">EasyXController</span> </span>&#123;
  EasyXNotifier xNotifier = EasyXNotifier();

  <span class="hljs-comment">///<span class="markdown">刷新控件</span></span>
  <span class="hljs-keyword">void</span> update() &#123;
    xNotifier.notify();
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>再来看看最核心的EasyBuilder控件：这就搞定了！
<ul>
<li>实现代码写的极其简单，希望大家思路能有所明晰</li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-comment">///<span class="markdown">刷新控件,自带回收机制</span></span>
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">EasyBuilder</span><<span class="hljs-title">T</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">EasyXController</span>> <span class="hljs-keyword">extends</span> <span class="hljs-title">StatefulWidget</span> </span>&#123;
  <span class="hljs-keyword">final</span> Widget <span class="hljs-built_in">Function</span>(T logic) builder;

  <span class="hljs-keyword">final</span> <span class="hljs-built_in">String?</span> tag;
  <span class="hljs-keyword">final</span> <span class="hljs-built_in">bool</span> autoRemove;

  <span class="hljs-keyword">const</span> EasyBuilder(&#123;
    Key? key,
    <span class="hljs-keyword">required</span> <span class="hljs-keyword">this</span>.builder,
    <span class="hljs-keyword">this</span>.autoRemove = <span class="hljs-keyword">true</span>,
    <span class="hljs-keyword">this</span>.tag,
  &#125;) : <span class="hljs-keyword">super</span>(key: key);

  <span class="hljs-meta">@override</span>
  _EasyBuilderState<T> createState() => _EasyBuilderState<T>();
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">_EasyBuilderState</span><<span class="hljs-title">T</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">EasyXController</span>>
    <span class="hljs-keyword">extends</span> <span class="hljs-title">State</span><<span class="hljs-title">EasyBuilder</span><<span class="hljs-title">T</span>>> </span>&#123;
  <span class="hljs-keyword">late</span> T controller;

  <span class="hljs-meta">@override</span>
  <span class="hljs-keyword">void</span> initState() &#123;
    <span class="hljs-keyword">super</span>.initState();

    controller = Easy.find<T>(tag: widget.tag);
    controller.xNotifier.addListener(() &#123;
      <span class="hljs-keyword">if</span> (mounted) setState(() &#123;&#125;);
    &#125;);
  &#125;

  <span class="hljs-meta">@override</span>
  <span class="hljs-keyword">void</span> dispose() &#123;
    <span class="hljs-keyword">if</span> (widget.autoRemove) &#123;
      Easy.delete<T>(tag: widget.tag);
    &#125;
    controller.xNotifier.dispose();

    <span class="hljs-keyword">super</span>.dispose();
  &#125;

  <span class="hljs-meta">@override</span>
  Widget build(BuildContext context) &#123;
    <span class="hljs-keyword">return</span> widget.builder(controller);
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-29">使用</h3>
<ul>
<li>使用很简单，先看下逻辑层</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">EasyXCounterLogic</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">EasyXController</span> </span>&#123;
  <span class="hljs-keyword">var</span> count = <span class="hljs-number">0</span>;

  <span class="hljs-keyword">void</span> increase() &#123;
    ++count;
    update();
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>界面层</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">EasyXCounterPage</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">StatelessWidget</span> </span>&#123;
  <span class="hljs-keyword">final</span> EasyXCounterLogic logic = Easy.put(EasyXCounterLogic());

  <span class="hljs-meta">@override</span>
  Widget build(BuildContext context) &#123;
    <span class="hljs-keyword">return</span> BaseScaffold(
      appBar: AppBar(title: <span class="hljs-keyword">const</span> Text(<span class="hljs-string">'EasyX-自定义EasyBuilder刷新机制'</span>)),
      body: Center(
        child: EasyBuilder<EasyXCounterLogic>(builder: (logic) &#123;
          <span class="hljs-keyword">return</span> Text(
            <span class="hljs-string">'点击了 <span class="hljs-subst">$&#123;logic.count&#125;</span> 次'</span>,
            style: TextStyle(fontSize: <span class="hljs-number">30.0</span>),
          );
        &#125;),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: () => logic.increase(),
        child: Icon(Icons.add),
      ),
    );
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>效果图</li>
</ul>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e099e20f27e94acb95edbc71650b72e7~tplv-k3u1fbpfcp-zoom-1.image" alt="easy_x_builder" loading="lazy" referrerpolicy="no-referrer"></p>
<h2 data-id="heading-30">Ebx：自动刷新机制</h2>
<blockquote>
<p>自动刷新机制，因为没加泛型，所以无法确定自己内部使用了哪个注入实例，Getx中是在路由里面去回收这些实例的，但是，如果你没使用GetX的路由，又用Obx，你会发现，GetXController居然无法自动回收！！！</p>
<p>此处针对该场景，我会给出一种解决方案</p>
</blockquote>
<h3 data-id="heading-31">实现</h3>
<ul>
<li>在自动刷新的机制中，需要将基础类型进行封装
<ul>
<li>主要逻辑在Rx中</li>
<li>set value 和 get value是关键</li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-comment">///<span class="markdown">拓展函数</span></span>
<span class="hljs-keyword">extension</span> IntExtension <span class="hljs-keyword">on</span> <span class="hljs-built_in">int</span> &#123;
  RxInt <span class="hljs-keyword">get</span> ebs => RxInt(<span class="hljs-keyword">this</span>);
&#125;

<span class="hljs-keyword">extension</span> StringExtension <span class="hljs-keyword">on</span> <span class="hljs-built_in">String</span> &#123;
  RxString <span class="hljs-keyword">get</span> ebs => RxString(<span class="hljs-keyword">this</span>);
&#125;

<span class="hljs-keyword">extension</span> DoubleExtension <span class="hljs-keyword">on</span> <span class="hljs-built_in">double</span> &#123;
  RxDouble <span class="hljs-keyword">get</span> ebs => RxDouble(<span class="hljs-keyword">this</span>);
&#125;

<span class="hljs-keyword">extension</span> BoolExtension <span class="hljs-keyword">on</span> <span class="hljs-built_in">bool</span> &#123;
  RxBool <span class="hljs-keyword">get</span> ebs => RxBool(<span class="hljs-keyword">this</span>);
&#125;

<span class="hljs-comment">///<span class="markdown">封装各类型</span></span>
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">RxInt</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Rx</span><<span class="hljs-title">int</span>> </span>&#123;
  RxInt(<span class="hljs-built_in">int</span> initial) : <span class="hljs-keyword">super</span>(initial);

  RxInt <span class="hljs-keyword">operator</span> +(<span class="hljs-built_in">int</span> other) &#123;
    value = value + other;
    <span class="hljs-keyword">return</span> <span class="hljs-keyword">this</span>;
  &#125;

  RxInt <span class="hljs-keyword">operator</span> -(<span class="hljs-built_in">int</span> other) &#123;
    value = value - other;
    <span class="hljs-keyword">return</span> <span class="hljs-keyword">this</span>;
  &#125;
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">RxDouble</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Rx</span><<span class="hljs-title">double</span>> </span>&#123;
  RxDouble(<span class="hljs-built_in">double</span> initial) : <span class="hljs-keyword">super</span>(initial);

  RxDouble <span class="hljs-keyword">operator</span> +(<span class="hljs-built_in">double</span> other) &#123;
    value = value + other;
    <span class="hljs-keyword">return</span> <span class="hljs-keyword">this</span>;
  &#125;

  RxDouble <span class="hljs-keyword">operator</span> -(<span class="hljs-built_in">double</span> other) &#123;
    value = value - other;
    <span class="hljs-keyword">return</span> <span class="hljs-keyword">this</span>;
  &#125;
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">RxString</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Rx</span><<span class="hljs-title">String</span>> </span>&#123;
  RxString(<span class="hljs-built_in">String</span> initial) : <span class="hljs-keyword">super</span>(initial);
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">RxBool</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Rx</span><<span class="hljs-title">bool</span>> </span>&#123;
  RxBool(<span class="hljs-built_in">bool</span> initial) : <span class="hljs-keyword">super</span>(initial);
&#125;

<span class="hljs-comment">///<span class="markdown">主体逻辑</span></span>
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Rx</span><<span class="hljs-title">T</span>> </span>&#123;
  EasyXNotifier subject = EasyXNotifier();

  Rx(T initial) &#123;
    _value = initial;
  &#125;

  <span class="hljs-keyword">late</span> T _value;

  <span class="hljs-built_in">bool</span> firstRebuild = <span class="hljs-keyword">true</span>;

  <span class="hljs-built_in">String</span> <span class="hljs-keyword">get</span> string => value.toString();

  <span class="hljs-meta">@override</span>
  <span class="hljs-built_in">String</span> toString() => value.toString();

  <span class="hljs-keyword">set</span> value(T val) &#123;
    <span class="hljs-keyword">if</span> (_value == val && !firstRebuild) <span class="hljs-keyword">return</span>;
    firstRebuild = <span class="hljs-keyword">false</span>;
    _value = val;

    subject.notify();
  &#125;

  T <span class="hljs-keyword">get</span> value &#123;
    <span class="hljs-keyword">if</span> (RxEasy.proxy != <span class="hljs-keyword">null</span>) &#123;
      RxEasy.proxy!.addListener(subject);
    &#125;
    <span class="hljs-keyword">return</span> _value;
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>需要写一个非常重要的中转类，这个也会储存响应式变量的监听对象
<ul>
<li>这个类是有着非常核心的逻辑：他将响应式变量和刷新控件关联起来了！</li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">RxEasy</span> </span>&#123;
  EasyXNotifier easyXNotifier = EasyXNotifier();

  <span class="hljs-built_in">Map</span><EasyXNotifier, <span class="hljs-built_in">String</span>> _listenerMap = &#123;&#125;;

  <span class="hljs-built_in">bool</span> <span class="hljs-keyword">get</span> canUpdate => _listenerMap.isNotEmpty;

  <span class="hljs-keyword">static</span> RxEasy? proxy;

  <span class="hljs-keyword">void</span> addListener(EasyXNotifier notifier) &#123;
    <span class="hljs-keyword">if</span> (!_listenerMap.containsKey(notifier)) &#123;
      <span class="hljs-comment">//重要：将Ebx中的监听对象转换到此处</span>
      easyXNotifier = proxy!.easyXNotifier;
      <span class="hljs-comment">//变量监听中刷新</span>
      notifier.addListener(() &#123;
        <span class="hljs-comment">//刷新ebx中添加的监听</span>
        easyXNotifier.notify();
      &#125;);
      <span class="hljs-comment">//添加进入map中</span>
      _listenerMap[notifier] = <span class="hljs-string">''</span>;
    &#125;
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>刷新控件Ebx</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-keyword">typedef</span> WidgetCallback = Widget <span class="hljs-built_in">Function</span>();

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Ebx</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">StatefulWidget</span> </span>&#123;
  <span class="hljs-keyword">const</span> Ebx(<span class="hljs-keyword">this</span>.builder, &#123;Key? key&#125;) : <span class="hljs-keyword">super</span>(key: key);

  <span class="hljs-keyword">final</span> WidgetCallback builder;

  <span class="hljs-meta">@override</span>
  _EbxState createState() => _EbxState();
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">_EbxState</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">State</span><<span class="hljs-title">Ebx</span>> </span>&#123;
  RxEasy _rxEasy = RxEasy();

  <span class="hljs-meta">@override</span>
  <span class="hljs-keyword">void</span> initState() &#123;
    <span class="hljs-keyword">super</span>.initState();

    _rxEasy.easyXNotifier.addListener(() &#123;
      <span class="hljs-keyword">if</span> (mounted) setState(() &#123;&#125;);
    &#125;);
  &#125;

  Widget <span class="hljs-keyword">get</span> notifyChild &#123;
    <span class="hljs-keyword">final</span> observer = RxEasy.proxy;
    RxEasy.proxy = _rxEasy;
    <span class="hljs-keyword">final</span> result = widget.builder();
    <span class="hljs-keyword">if</span> (!_rxEasy.canUpdate) &#123;
      <span class="hljs-keyword">throw</span> <span class="hljs-string">'Widget lacks Rx type variables'</span>;
    &#125;
    RxEasy.proxy = observer;
    <span class="hljs-keyword">return</span> result;
  &#125;

  <span class="hljs-meta">@override</span>
  Widget build(BuildContext context) &#123;
    <span class="hljs-keyword">return</span> notifyChild;
  &#125;

  <span class="hljs-meta">@override</span>
  <span class="hljs-keyword">void</span> dispose() &#123;
    _rxEasy.easyXNotifier.dispose();

    <span class="hljs-keyword">super</span>.dispose();
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>在上面说了，在自动刷新机制中，自动回收依赖实例是个蛋筒的问题，此处我写了一个回收控件，可以解决此问题
<ul>
<li>使用时，必须套一层了；如果大家有更好的思路，麻烦在评论里告知</li>
</ul>
</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">EasyBindWidget</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">StatefulWidget</span> </span>&#123;
  <span class="hljs-keyword">const</span> EasyBindWidget(&#123;
    Key? key,
    <span class="hljs-keyword">this</span>.bind,
    <span class="hljs-keyword">this</span>.tag,
    <span class="hljs-keyword">this</span>.binds,
    <span class="hljs-keyword">this</span>.tags,
    <span class="hljs-keyword">required</span> <span class="hljs-keyword">this</span>.child,
  &#125;)  : <span class="hljs-keyword">assert</span>(
          binds == <span class="hljs-keyword">null</span> || tags == <span class="hljs-keyword">null</span> || binds.length == tags.length,
          <span class="hljs-string">'The binds and tags arrays length should be equal\n'</span>
          <span class="hljs-string">'and the elements in the two arrays correspond one-to-one'</span>,
        ),
        <span class="hljs-keyword">super</span>(key: key);

  <span class="hljs-keyword">final</span> <span class="hljs-built_in">Object?</span> bind;
  <span class="hljs-keyword">final</span> <span class="hljs-built_in">String?</span> tag;

  <span class="hljs-keyword">final</span> <span class="hljs-built_in">List</span><<span class="hljs-built_in">Object</span>>? binds;
  <span class="hljs-keyword">final</span> <span class="hljs-built_in">List</span><<span class="hljs-built_in">String</span>>? tags;

  <span class="hljs-keyword">final</span> Widget child;

  <span class="hljs-meta">@override</span>
  _EasyBindWidgetState createState() => _EasyBindWidgetState();
&#125;

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">_EasyBindWidgetState</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">State</span><<span class="hljs-title">EasyBindWidget</span>> </span>&#123;
  <span class="hljs-meta">@override</span>
  Widget build(BuildContext context) &#123;
    <span class="hljs-keyword">return</span> widget.child;
  &#125;

  <span class="hljs-meta">@override</span>
  <span class="hljs-keyword">void</span> dispose() &#123;
    _closeController();
    _closeControllers();

    <span class="hljs-keyword">super</span>.dispose();
  &#125;

  <span class="hljs-keyword">void</span> _closeController() &#123;
    <span class="hljs-keyword">if</span> (widget.bind == <span class="hljs-keyword">null</span>) &#123;
      <span class="hljs-keyword">return</span>;
    &#125;

    <span class="hljs-keyword">var</span> key = widget.bind.runtimeType.toString() + (widget.tag ?? <span class="hljs-string">''</span>);
    Easy.delete(key: key);
  &#125;

  <span class="hljs-keyword">void</span> _closeControllers() &#123;
    <span class="hljs-keyword">if</span> (widget.binds == <span class="hljs-keyword">null</span>) &#123;
      <span class="hljs-keyword">return</span>;
    &#125;

    <span class="hljs-keyword">for</span> (<span class="hljs-keyword">var</span> i = <span class="hljs-number">0</span>; i < widget.binds!.length; i++) &#123;
      <span class="hljs-keyword">var</span> type = widget.binds![i].runtimeType.toString();

      <span class="hljs-keyword">if</span> (widget.tags == <span class="hljs-keyword">null</span>) &#123;
        Easy.delete(key: type);
      &#125; <span class="hljs-keyword">else</span> &#123;
        <span class="hljs-keyword">var</span> key = type + (widget.tags?[i] ?? <span class="hljs-string">''</span>);
        Easy.delete(key: key);
      &#125;
    &#125;
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-32">使用</h3>
<ul>
<li>逻辑层，这次，咱们连基类都不需要写</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">EasyXEbxCounterLogic</span> </span>&#123;
  RxInt count = <span class="hljs-number">0.</span>ebs;

  <span class="hljs-comment">///<span class="markdown">自增</span></span>
  <span class="hljs-keyword">void</span> increase() => ++count;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>界面层：页面顶节点套了一个EasyBindWidget，可以保证依赖注入实例可以自动回收</li>
</ul>
<pre><code class="hljs language-dart copyable" lang="dart"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">EasyXEbxCounterPage</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">StatelessWidget</span> </span>&#123;
  <span class="hljs-keyword">final</span> EasyXEbxCounterLogic logic = Easy.put(EasyXEbxCounterLogic());

  <span class="hljs-meta">@override</span>
  Widget build(BuildContext context) &#123;
    <span class="hljs-keyword">return</span> EasyBindWidget(
      bind: logic,
      child: BaseScaffold(
        appBar: AppBar(title: <span class="hljs-keyword">const</span> Text(<span class="hljs-string">'EasyX-自定义Ebx刷新机制'</span>)),
        body: Center(
          child: Ebx(() &#123;
            <span class="hljs-keyword">return</span> Text(
              <span class="hljs-string">'点击了 <span class="hljs-subst">$&#123;logic.count.value&#125;</span> 次'</span>,
              style: TextStyle(fontSize: <span class="hljs-number">30.0</span>),
            );
          &#125;),
        ),
        floatingActionButton: FloatingActionButton(
          onPressed: () => logic.increase(),
          child: Icon(Icons.add),
        ),
      ),
    );
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>效果图</li>
</ul>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a198d37322b84427a1107a8bccff591e~tplv-k3u1fbpfcp-zoom-1.image" alt="easy_x_ebx" loading="lazy" referrerpolicy="no-referrer"></p>
<h2 data-id="heading-33">总结</h2>
<p>这俩种刷新模式，含金量高的，应该还是自动刷新的机制，思路很有趣，响应式变量和刷新控件通过静态变量的形式建立起联系，cool！又是一种骚操作！</p>
<p>这俩套状态管理机制，我都给出了对依赖注入对象，自动回收的解决方案，希望对大家的思路有所启迪。</p>
<h1 data-id="heading-34">最后</h1>
<p>终于把最后一篇GetX的原理剖析写完了（只针对GetX状态管理这部分内容），了了一桩心事。。。</p>
<ul>
<li>有些流程比较绕，特地画了一些图，图文并茂总会让人心情愉悦嘛......</li>
</ul>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/60de87b1d42d42a0a9881bf40e276288~tplv-k3u1fbpfcp-zoom-1.image" alt="image-20210713163552831" loading="lazy" referrerpolicy="no-referrer"></p>
<p>如果大家认真看完了整片文章，可能会发现：状态管理+依赖注入，可以使得使用场景大大的被拓展</p>
<ul>
<li>GetBuilder的自动回收就是借助依赖注入，无缝获取注入实例，从而实现自动回收的操作</li>
<li>而且GetBuilder还无需额外传参数！</li>
</ul>
<p>整篇文章写下来，我觉得真的尽力了</p>
<ul>
<li>从InheritedWidget到路由</li>
<li>然后到依赖注入</li>
<li>再就是俩种状态框架原理剖析</li>
<li>最后依据俩种刷新机制，手搓俩套状态管理框架</li>
</ul>
<p><strong>也算是层层递进的将其中的知识，一点点的展示在大家的面前，希望可以帮到各位！！！</strong></p>
<blockquote>
<p><strong>系列文章 + 相关地址</strong></p>
</blockquote>
<ul>
<li>
<p>文章中Demo的Github地址：<a href="https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2FCNAD666%2Fflutter_use" target="_blank" rel="nofollow noopener noreferrer" title="https://github.com/CNAD666/flutter_use" ref="nofollow noopener noreferrer">flutter_use</a></p>
</li>
<li>
<p><a href="https://juejin.cn/post/6924104248275763208" target="_blank" title="https://juejin.cn/post/6924104248275763208">Flutter GetX使用---简洁的魅力！</a></p>
</li>
<li>
<p><a href="https://juejin.cn/post/6973900070358319135" target="_blank" title="https://juejin.cn/post/6973900070358319135">源码篇：Flutter Bloc背后的思想，一篇纠结的文章</a></p>
</li>
<li>
<p><a href="https://juejin.cn/post/6968272002515894303" target="_blank" title="https://juejin.cn/post/6968272002515894303">源码篇：Flutter Provider的另一面（万字图文+插件）</a></p>
</li>
</ul></div>  
</div>
            
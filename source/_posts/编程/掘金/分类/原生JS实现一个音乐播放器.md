
---
title: '原生JS实现一个音乐播放器'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a5c897f43d124478b502f7f74e187ea9~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Thu, 15 Jul 2021 22:47:51 GMT
thumbnail: 'https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a5c897f43d124478b502f7f74e187ea9~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h1 data-id="heading-0">准备工作：</h1>
<p>VScode 编辑器 设计稿 （无图不页面）</p>
<h1 data-id="heading-1">设计稿分析：</h1>
<p><img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a5c897f43d124478b502f7f74e187ea9~tplv-k3u1fbpfcp-watermark.image" alt="效果图.jpeg" loading="lazy" referrerpolicy="no-referrer"></p>
<ul>
<li>从图上首先我们可以分析出来一整个页面从上至下可以划分为 6 个区域</li>
<li>最中间的主页面我们可以考虑用两个圆环的 svg 图去撑起来，并且panel1,2,3一共三个圆环按照相反的方向转动</li>
<li>下面的按钮栏，我们用几个点赞，下载，分享，评论的 svg 来填充就好，需要考虑是否添加每个按钮的跳转效果</li>
<li>最后一行也是用播放，暂停，上一曲，下一曲等按钮组成</li>
<li>总体难度系数较低，复杂的部分主要是歌曲播放的进度条部分，注意要做进度条拖动就快进到对应的歌词</li>
</ul>
<h1 data-id="heading-2">HTML 和 SCSS 部分实现</h1>
<h2 data-id="heading-3">区域一二部分实现</h2>
<pre><code class="hljs language-javascript copyable" lang="javascript"><div <span class="hljs-class"><span class="hljs-keyword">class</span></span>=<span class="hljs-string">"header"</span>>
  <span class="xml"><span class="hljs-tag"><<span class="hljs-name">h1</span>></span>我肯定在几百年前就说过...<span class="hljs-tag"></<span class="hljs-name">h1</span>></span></span>
  <span class="xml"><span class="hljs-tag"><<span class="hljs-name">p</span>></span>告五人-爱人错过<span class="hljs-tag"></<span class="hljs-name">p</span>></span></span>
  <span class="xml"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"balls"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">span</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"current"</span>></span><span class="hljs-tag"></<span class="hljs-name">span</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">span</span>></span><span class="hljs-tag"></<span class="hljs-name">span</span>></span>
  <span class="hljs-tag"></<span class="hljs-name">div</span>></span></span>
</div>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-4">规定使用较多的颜色和区域1、2部分的 SCSS</h2>
<pre><code class="hljs language-javascript copyable" lang="javascript">$backgroundColor: #060a3d;
$color: #fff;
$color1: #868aaf;
$color2: #db3baa;
$color2-dark: darken($color2, <span class="hljs-number">10</span>%);
$color2-dark: darken($color2, <span class="hljs-number">30</span>%);
$color3: #0025f1;


html,
body &#123;
 <span class="hljs-attr">width</span>: <span class="hljs-number">100</span>%;
 height: <span class="hljs-number">100</span>%;
 overflow: hidden;
&#125;

* &#123;
 <span class="hljs-attr">margin</span>: <span class="hljs-number">0</span>;
 padding: <span class="hljs-number">0</span>;
&#125;

#player &#123;
 <span class="hljs-attr">height</span>: <span class="hljs-number">100</span>%;
 background: $backgroundColor;
 .header &#123;
   text-align: center;
   height: 110px;
   h1 &#123;
     <span class="hljs-attr">color</span>: $color;
     font-size: 20px;
     padding-top: 20px;
   &#125;
   p &#123;
     <span class="hljs-attr">color</span>: $color1;
     font-size: 12px;
   &#125;
   .balls &#123;
     <span class="hljs-attr">display</span>: flex;
     justify-content: center;
     align-items: center;
     margin-top: 20px;
     span &#123;
       <span class="hljs-attr">display</span>: block;
       width: 5px;
       height: 5px;
       border-radius: <span class="hljs-number">50</span>%;
       background: $color2-dark;
       margin: <span class="hljs-number">0</span> 4px;

       &.current &#123;
         <span class="hljs-attr">width</span>: 8px;
         height: 8px;
         background: $color2;
       &#125;
     &#125;
   &#125;
 &#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-5">区域3实现</h2>
<pre><code class="hljs language-javascript copyable" lang="javascript"><div <span class="hljs-class"><span class="hljs-keyword">class</span></span>=<span class="hljs-string">"panels panel1"</span>>
  <span class="xml"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"panel-effect"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"effect"</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"effect-1"</span>></span><span class="hljs-tag"></<span class="hljs-name">div</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"effect-2"</span>></span><span class="hljs-tag"></<span class="hljs-name">div</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"effect-3"</span>></span><span class="hljs-tag"></<span class="hljs-name">div</span>></span>
    <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"lyrics"</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">p</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"current"</span>></span><span class="hljs-tag"></<span class="hljs-name">p</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">p</span>></span><span class="hljs-tag"></<span class="hljs-name">p</span>></span>
    <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
  <span class="hljs-tag"></<span class="hljs-name">div</span>></span></span>
  <span class="xml"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"panel-lyrics"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"container"</span>></span><span class="hljs-tag"></<span class="hljs-name">div</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"maoboli"</span>></span><span class="hljs-tag"></<span class="hljs-name">div</span>></span>
  <span class="hljs-tag"></<span class="hljs-name">div</span>></span></span>
</div>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-6">区域4按钮（喜欢，下载，分享，评论）svg 引入</h2>
<pre><code class="hljs language-javascript copyable" lang="javascript"><div <span class="hljs-class"><span class="hljs-keyword">class</span></span>=<span class="hljs-string">"buttons"</span>>
  <span class="xml"><span class="hljs-tag"><<span class="hljs-name">svg</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"btn-download"</span>
           <span class="hljs-attr">id</span>=<span class="hljs-string">"icon-download"</span>
           <span class="hljs-attr">stroke</span>=<span class="hljs-string">"none"</span>
           <span class="hljs-attr">stroke-width</span>=<span class="hljs-string">"1"</span>
           <span class="hljs-attr">fill</span>=<span class="hljs-string">"none"</span>
           <span class="hljs-attr">fill-rule</span>=<span class="hljs-string">"evenodd"</span>
           <span class="hljs-attr">opacity</span>=<span class="hljs-string">"0.8"</span>></span>
  <span class="hljs-tag"></<span class="hljs-name">svg</span>></span></span>
</div>
<span class="hljs-comment">//以此类推都引入</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-7">区域5播放进度条</h2>
<pre><code class="hljs language-javascript copyable" lang="javascript"><div <span class="hljs-class"><span class="hljs-keyword">class</span></span>=<span class="hljs-string">"area-bar"</span>>
  <span class="xml"><span class="hljs-tag"><<span class="hljs-name">span</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"time-start"</span>></span>00:00<span class="hljs-tag"></<span class="hljs-name">span</span>></span></span>
  <span class="xml"><span class="hljs-tag"><<span class="hljs-name">span</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"time-end"</span>></span>00:00<span class="hljs-tag"></<span class="hljs-name">span</span>></span></span>
  <span class="xml"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"bar"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"progress"</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"progress-button"</span>></span><span class="hljs-tag"></<span class="hljs-name">div</span>></span>
    <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
  <span class="hljs-tag"></<span class="hljs-name">div</span>></span></span>
</div>
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-8">区域6播放暂停svg引入</h2>
<pre><code class="hljs language-javascript copyable" lang="javascript"> <div <span class="hljs-class"><span class="hljs-keyword">class</span></span>=<span class="hljs-string">"actions"</span>>
  <span class="xml"><span class="hljs-tag"><<span class="hljs-name">img</span> <span class="hljs-attr">src</span>=<span class="hljs-string">"./src/svg/循环模式.svg"</span> <span class="hljs-attr">alt</span>=<span class="hljs-string">""</span> /></span></span>
  <span class="xml"><span class="hljs-tag"><<span class="hljs-name">img</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"play-prev"</span> <span class="hljs-attr">src</span>=<span class="hljs-string">"./src/svg/上一首.svg"</span> <span class="hljs-attr">alt</span>=<span class="hljs-string">""</span> /></span></span>
  <span class="xml"><span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"play-pause"</span>></span><span class="hljs-tag"></<span class="hljs-name">div</span>></span></span>
  <span class="xml"><span class="hljs-tag"><<span class="hljs-name">img</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"play-next"</span> <span class="hljs-attr">src</span>=<span class="hljs-string">"./src/svg/下一首.svg"</span> <span class="hljs-attr">alt</span>=<span class="hljs-string">""</span> /></span></span>
  <span class="xml"><span class="hljs-tag"><<span class="hljs-name">img</span> <span class="hljs-attr">src</span>=<span class="hljs-string">"./src/svg/音乐.svg"</span> <span class="hljs-attr">alt</span>=<span class="hljs-string">""</span> /></span></span>
 </div>
<span class="copy-code-btn">复制代码</span></code></pre>
<h1 data-id="heading-9">CSS 部分实现</h1>
<h2 data-id="heading-10">区域3 SCSS实现</h2>
<pre><code class="hljs language-javascript copyable" lang="javascript">.panels &#123;
    <span class="hljs-attr">height</span>: calc(<span class="hljs-number">100</span>% - 270px);
    align-items: center;
    width: 100vw;
    display: flex;
    transition: transform <span class="hljs-number">0.</span>3s;
    overflow: visible;
    &.panel1 &#123; <span class="hljs-comment">//歌词左滑之后的页面</span>
      <span class="hljs-attr">transform</span>: translateX(0vw);
    &#125;
    &.panel2 &#123; <span class="hljs-comment">//歌词右滑之后的页面</span>
      <span class="hljs-attr">transform</span>: translateX(-100vw);
    &#125;
    .panel-effect &#123;
      <span class="hljs-attr">width</span>: 100vw;
      height: <span class="hljs-number">100</span>%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      flex-shrink: <span class="hljs-number">0</span>;
      .effect &#123;
        <span class="hljs-attr">position</span>: relative;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 40vh;
        > div &#123;
          <span class="hljs-attr">background</span>: contain;
          position: absolute;
        &#125;
        .effect-<span class="hljs-number">1</span> &#123; <span class="hljs-comment">//外层的大园环</span>
          <span class="hljs-attr">background</span>: url(../svg/effect-no-move.svg) <span class="hljs-number">0</span> <span class="hljs-number">0</span> no-repeat;
          width: 70vw;
          height: 70vw;
          animation: rotate 20s linear infinite;<span class="hljs-comment">//添加动效</span>
        &#125;
        .effect-<span class="hljs-number">2</span> &#123; <span class="hljs-comment">//中层的圆环</span>
          <span class="hljs-attr">background</span>: url(../svg/effect-move1.svg) <span class="hljs-number">0</span> <span class="hljs-number">0</span> no-repeat;
          width: 60vw;
          height: 60vw;
          animation: rotate 10s linear infinite reverse;<span class="hljs-comment">//添加动效</span>
        &#125;
        .effect-<span class="hljs-number">3</span> &#123; <span class="hljs-comment">//最内层的圆环</span>
          <span class="hljs-attr">background</span>: url(../svg/effect-move2.svg) <span class="hljs-number">0</span> <span class="hljs-number">0</span> no-repeat;
          width: 24vw;
          height: 24vw;
          animation: rotate 10s linear infinite;<span class="hljs-comment">//添加动效</span>
        &#125;
      &#125;
<span class="hljs-comment">// 右滑时的歌词panel实现</span>
.lyrics &#123; <span class="hljs-comment">// 歌词左滑页面，三个圆环动效下面的歌词效果</span>
        text-align: center;
        p &#123;
          font-size: 13px;
          color: $color1;
          margin-top: 8px;

          &.current &#123;
            <span class="hljs-attr">color</span>: $color;
          &#125;
        &#125;
      &#125;
    .panel-lyrics &#123; <span class="hljs-comment">//歌词右滑页面的效果</span>
      <span class="hljs-attr">position</span>: relative;
      flex-shrink: <span class="hljs-number">0</span>;
      width: 100vw;
      height: <span class="hljs-number">100</span>%;
      text-align: center;
      line-height: <span class="hljs-number">2</span>;
      overflow: hidden;
      
      .container &#123; <span class="hljs-comment">//歌词的上下滚动效果</span>
        <span class="hljs-attr">transition</span>: all .3s;
        transform: translateY(-100px);
        p &#123;
          font-size: 14px;
          color: $color1;
  
          &.current &#123;
            <span class="hljs-attr">color</span>: $color;
          &#125;
        &#125;
      &#125;
      .maoboli &#123; <span class="hljs-comment">//歌词的毛玻璃效果</span>
        <span class="hljs-attr">position</span>: absolute;
        top: <span class="hljs-number">0</span>;
        left: <span class="hljs-number">0</span>;
        width: <span class="hljs-number">100</span>%;
        height: <span class="hljs-number">100</span>%;
        background: linear-gradient(rgba(<span class="hljs-number">6</span>, <span class="hljs-number">10</span>, <span class="hljs-number">61</span>, <span class="hljs-number">0.822</span>), rgba(<span class="hljs-number">6</span>, <span class="hljs-number">10</span>, <span class="hljs-number">61</span>, <span class="hljs-number">0</span>), rgba(<span class="hljs-number">6</span>, <span class="hljs-number">10</span>, <span class="hljs-number">61</span>, <span class="hljs-number">0.829</span>));
      &#125;
    &#125;
  &#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-11">区域4 SCSS 实现</h2>
<pre><code class="hljs language-javascript copyable" lang="javascript">.buttons &#123;
      <span class="hljs-attr">display</span>: flex;
      justify-content: center;

      > svg,<span class="hljs-comment">//svg的样式</span>
      > div &#123;
        <span class="hljs-attr">width</span>: 24px;
        height: 24px;
        margin: <span class="hljs-number">0</span> 20px;
      &#125;
    &#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-12">区域5 SCSS实现</h2>
<pre><code class="hljs language-javascript copyable" lang="javascript">.area-bar &#123;
      <span class="hljs-attr">color</span>: $color1;
      font-size: 12px;
      display: flex;
      padding: <span class="hljs-number">0</span> 20px;
      margin-top: 20px;
      align-items: center;
      .time-start &#123;
        <span class="hljs-attr">order</span>: <span class="hljs-number">1</span>;
        width: 32px;
      &#125;
.time-end &#123;
        <span class="hljs-attr">order</span>: <span class="hljs-number">3</span>;
        width: 32px;
      &#125;
  .bar &#123;
        <span class="hljs-attr">order</span>: <span class="hljs-number">2</span>;
        flex: <span class="hljs-number">1</span>;
        height: 4px;
        background: $color3;
        border-radius: 2px;
        margin: <span class="hljs-number">0</span> 18px;
.progress &#123;
          <span class="hljs-attr">width</span>: <span class="hljs-number">0</span>%;
          height: <span class="hljs-number">100</span>%;
          border-radius: 2px;
          background: $color2;
          position: relative;
.progress-button &#123; <span class="hljs-comment">//拖动小球来快进</span>
            <span class="hljs-attr">position</span>: absolute;
            right: -8px;
            top: <span class="hljs-number">50</span>%;
            display: block;
            width: 20px;
            height: 20px;
            background: url(../svg/progress.svg) <span class="hljs-number">0</span> <span class="hljs-number">0</span> no-repeat;
            background-size: 12px 12px;
            background-position: center;
            transform: translateY(-<span class="hljs-number">50</span>%);
          &#125;
        &#125;
      &#125;
    &#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-13">区域6 SCSS实现</h2>
<pre><code class="hljs language-javascript copyable" lang="javascript">.actions &#123;
      <span class="hljs-attr">display</span>: flex;
      align-items: center;
      justify-content: space-between;
      margin-top: 20px;
      padding: <span class="hljs-number">0</span> 20px;
.play-pause &#123;
        <span class="hljs-attr">width</span>: 50px;
        height: 50px;
        background-size: contain;
        background-repeat: no-repeat;
        background-image: url(<span class="hljs-string">"../svg/播放.svg"</span>);
&.playing &#123;
          background-image: url(<span class="hljs-string">"../svg/暂停.svg"</span>);
        &#125;
      &#125;
  img &#123;
        <span class="hljs-attr">width</span>: 33px;
        height: 50px;
      &#125;
    &#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-14">添加动效</h2>
<pre><code class="copyable">@keyframes rotate &#123;
  0% &#123;
    transform: rotate(0);
  &#125;
  100% &#123;
    transform: rotate(360deg);
  &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h1 data-id="heading-15">JS部分</h1>
<h2 data-id="heading-16">左右滑动效果swiper</h2>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Swiper</span> </span>&#123;
  <span class="hljs-function"><span class="hljs-title">constructor</span>(<span class="hljs-params">node</span>)</span> &#123;
    <span class="hljs-keyword">if</span>(!node) <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> <span class="hljs-built_in">Error</span>(<span class="hljs-string">'需要传递需要绑定的DOM元素'</span>)
    <span class="hljs-keyword">let</span> root = <span class="hljs-keyword">typeof</span> node === <span class="hljs-string">'string'</span> ? <span class="hljs-built_in">document</span>.querySelector(node) : node
    <span class="hljs-keyword">let</span> eventHub = &#123;<span class="hljs-string">'swipLeft'</span>: [],<span class="hljs-string">'swipRight'</span>:[]&#125;

    <span class="hljs-keyword">let</span> initx
    <span class="hljs-keyword">let</span> newX
    <span class="hljs-keyword">let</span> clock
    root.ontouchstart = <span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params">e</span>) </span>&#123;
      initx = e.changedTouches[<span class="hljs-number">0</span>].pageX
    &#125;

    root.ontouchmove = <span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params">e</span>)</span>&#123;
      <span class="hljs-keyword">if</span>(clock) <span class="hljs-built_in">clearInterval</span>(clock)
      clock = <span class="hljs-built_in">setTimeout</span>(<span class="hljs-function">() =></span>&#123;
        newX = e.changedTouches[<span class="hljs-number">0</span>].pageX
        <span class="hljs-keyword">if</span>(newX - initx > <span class="hljs-number">10</span>)&#123;
          eventHub[<span class="hljs-string">'swipRight'</span>].forEach(<span class="hljs-function"><span class="hljs-params">fn</span>=></span>fn(root))
        &#125;<span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span>(initx - newX > <span class="hljs-number">10</span>)&#123;
          eventHub[<span class="hljs-string">'swipLeft'</span>].forEach(<span class="hljs-function"><span class="hljs-params">fn</span>=></span>fn(root))
        &#125;
      &#125;,<span class="hljs-number">100</span>)
    &#125;

    <span class="hljs-built_in">this</span>.on = <span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params">type, fn</span>)</span>&#123;
      <span class="hljs-keyword">if</span>(eventHub[type]) &#123;
        eventHub[type].push(fn)
      &#125;
    &#125;
    
    <span class="hljs-built_in">this</span>.off = <span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params">type,fn</span>)</span>&#123;
      <span class="hljs-keyword">let</span> index = eventHub[type].indexOf(fn)
      <span class="hljs-keyword">if</span>(index !== -<span class="hljs-number">1</span>) &#123;
        eventHub[type].splice(index,<span class="hljs-number">1</span>)
      &#125;
    &#125;
  &#125;
&#125;


<span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span> Swiper
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-17">主要JS部分</h2>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Player</span> </span>&#123;<span class="hljs-comment">//绑定事件</span>
  <span class="hljs-function"><span class="hljs-title">constructor</span>(<span class="hljs-params">node</span>)</span> &#123;
    <span class="hljs-built_in">this</span>.$ = <span class="hljs-function">(<span class="hljs-params">selector</span>) =></span> <span class="hljs-built_in">this</span>.root.querySelector(selector);
    <span class="hljs-built_in">this</span>.$$ = <span class="hljs-function">(<span class="hljs-params">selector</span>) =></span> <span class="hljs-built_in">this</span>.root.querySelectorAll(selector);
    <span class="hljs-built_in">this</span>.root = <span class="hljs-keyword">typeof</span> node === <span class="hljs-string">"string"</span> ? <span class="hljs-built_in">document</span>.querySelector(node) : node;
    <span class="hljs-built_in">this</span>.songList = [];
    <span class="hljs-built_in">this</span>.currentIndex = <span class="hljs-number">0</span>;
    <span class="hljs-built_in">this</span>.audio = <span class="hljs-keyword">new</span> Audio();
    <span class="hljs-built_in">this</span>.start();
    <span class="hljs-built_in">this</span>.bind();
  &#125;
  <span class="hljs-function"><span class="hljs-title">start</span>(<span class="hljs-params"></span>)</span> &#123;
    <span class="hljs-built_in">this</span>.songList = [
      &#123;
        <span class="hljs-attr">id</span>: <span class="hljs-string">"-1"</span>,
        <span class="hljs-attr">title</span>: <span class="hljs-string">"only my railgun"</span>,
        <span class="hljs-attr">author</span>: <span class="hljs-string">"fripside"</span>,
        <span class="hljs-attr">albumn</span>: <span class="hljs-string">"某科学的超电磁炮"</span>,
        <span class="hljs-attr">lyric</span>: onlyMyRailgun,
        <span class="hljs-attr">url</span>: mOnlyMyRailgun,
      &#125;,
      .....<span class="hljs-comment">//加入你想要的音乐</span>
                   ];
    <span class="hljs-built_in">this</span>.renderSong();
&#125;
<span class="hljs-function"><span class="hljs-title">bind</span>(<span class="hljs-params"></span>)</span> &#123;
    <span class="hljs-built_in">this</span>.audio.src = <span class="hljs-built_in">this</span>.songList[<span class="hljs-built_in">this</span>.currentIndex].url;
    <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".play-pause"</span>).onclick = <span class="hljs-function">(<span class="hljs-params">e</span>) =></span> &#123;<span class="hljs-comment">//点击播放暂停</span>
      <span class="hljs-keyword">if</span> (e.target.classList.contains(<span class="hljs-string">"playing"</span>)) &#123;
        <span class="hljs-built_in">this</span>.audio.pause();
        e.target.classList.remove(<span class="hljs-string">"playing"</span>);
      &#125; <span class="hljs-keyword">else</span> &#123;
        <span class="hljs-built_in">this</span>.audio.play();
        e.target.classList.add(<span class="hljs-string">"playing"</span>);
      &#125;
    &#125;;

    <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".play-prev"</span>).onclick = <span class="hljs-function">() =></span> &#123;<span class="hljs-comment">//播放上一首</span>
      <span class="hljs-built_in">this</span>.playPrevSong();
    &#125;;
    <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".play-next"</span>).onclick = <span class="hljs-function">() =></span> &#123;<span class="hljs-comment">//播放下一首</span>
      <span class="hljs-built_in">this</span>.playNextSong();
    &#125;;

    <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".area-bar .progress-button"</span>).ontouchstart = <span class="hljs-function">(<span class="hljs-params">e</span>) =></span> &#123;<span class="hljs-comment">//判断开始拖动小球的动作</span>
      <span class="hljs-built_in">this</span>.progressButtonTouchStart = &#123;
        <span class="hljs-attr">x</span>: e.touches[<span class="hljs-number">0</span>].clientX,
        <span class="hljs-attr">left</span>: e.target.offsetLeft,
      &#125;;
    &#125;;
    <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".area-bar .progress-button"</span>).ontouchmove = <span class="hljs-function">(<span class="hljs-params">e</span>) =></span> &#123;<span class="hljs-comment">//判断持续拖动的过程</span>
      <span class="hljs-keyword">const</span> delta = e.touches[<span class="hljs-number">0</span>].clientX - <span class="hljs-built_in">this</span>.progressButtonTouchStart.x;
      <span class="hljs-keyword">const</span> bar = <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".area-bar .bar"</span>);
      <span class="hljs-keyword">const</span> progress = <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".area-bar .progress"</span>);
      progress.style.width =
        <span class="hljs-built_in">Math</span>.min(
          <span class="hljs-built_in">Math</span>.max(<span class="hljs-comment">//</span>
            ((delta + <span class="hljs-built_in">this</span>.progressButtonTouchStart.left) / bar.offsetWidth) *
              <span class="hljs-number">100</span>,
            <span class="hljs-number">0</span>
          ),
          <span class="hljs-number">100</span>
        ) + <span class="hljs-string">"%"</span>;
    &#125;;
    <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".area-bar .progress-button"</span>).ontouchend = <span class="hljs-function">() =></span> &#123;
      <span class="hljs-built_in">this</span>.progressButtonTouchStart = <span class="hljs-literal">undefined</span>;
      <span class="hljs-keyword">const</span> progress = <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".area-bar .progress"</span>);
      <span class="hljs-built_in">this</span>.audio.currentTime =
        (<span class="hljs-built_in">this</span>.audio.duration * <span class="hljs-built_in">parseInt</span>(progress.style.width)) / <span class="hljs-number">100</span>;
    &#125;;

    <span class="hljs-built_in">this</span>.audio.ontimeupdate = <span class="hljs-function">() =></span> &#123;
      <span class="hljs-built_in">this</span>.locateLyric();
      <span class="hljs-keyword">if</span> (!<span class="hljs-built_in">this</span>.progressButtonTouchStart) &#123;
        <span class="hljs-built_in">this</span>.setProgerssBar();
      &#125;
    &#125;;

    <span class="hljs-keyword">let</span> swiper = <span class="hljs-keyword">new</span> Swiper(<span class="hljs-built_in">this</span>.$(<span class="hljs-string">".panels"</span>));
    swiper.on(<span class="hljs-string">"swipLeft"</span>, <span class="hljs-function">(<span class="hljs-params">e</span>) =></span> &#123;<span class="hljs-comment">//向左滑动</span>
      e.classList.remove(<span class="hljs-string">"panel1"</span>);
      e.classList.add(<span class="hljs-string">"panel2"</span>);
      <span class="hljs-built_in">this</span>.$$(<span class="hljs-string">".header .balls span"</span>)[<span class="hljs-number">1</span>].classList.add(<span class="hljs-string">"current"</span>);
      <span class="hljs-built_in">this</span>.$$(<span class="hljs-string">".header .balls span"</span>)[<span class="hljs-number">0</span>].classList.remove(<span class="hljs-string">"current"</span>);
      <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".footer .buttons"</span>).style.opacity = <span class="hljs-number">0</span>;
      <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".footer .buttons"</span>).style.pointerEvents = <span class="hljs-string">"none"</span>;
    &#125;);
    swiper.on(<span class="hljs-string">"swipRight"</span>, <span class="hljs-function">(<span class="hljs-params">e</span>) =></span> &#123;<span class="hljs-comment">//向右滑动</span>
      e.classList.remove(<span class="hljs-string">"panel2"</span>);
      e.classList.add(<span class="hljs-string">"panel1"</span>);
      <span class="hljs-built_in">this</span>.$$(<span class="hljs-string">".header .balls span"</span>)[<span class="hljs-number">1</span>].classList.remove(<span class="hljs-string">"current"</span>);
      <span class="hljs-built_in">this</span>.$$(<span class="hljs-string">".header .balls span"</span>)[<span class="hljs-number">0</span>].classList.add(<span class="hljs-string">"current"</span>);
      <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".footer .buttons"</span>).style.opacity = <span class="hljs-number">1</span>;
      <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".footer .buttons"</span>).style.pointerEvents = <span class="hljs-string">"auto"</span>;
    &#125;);
  &#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h2 data-id="heading-18">重新渲染歌曲</h2>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-function"><span class="hljs-title">renderSong</span>(<span class="hljs-params"></span>)</span> &#123;
    <span class="hljs-keyword">let</span> songObj = <span class="hljs-built_in">this</span>.songList[<span class="hljs-built_in">this</span>.currentIndex];
    <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".header h1"</span>).innerText = songObj.title;
    <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".header p"</span>).innerText = songObj.author + <span class="hljs-string">"-"</span> + songObj.albumn;
    <span class="hljs-built_in">this</span>.audio.onloadedmetadata = <span class="hljs-function">() =></span>
      (<span class="hljs-built_in">this</span>.$(<span class="hljs-string">".time-end"</span>).innerText = <span class="hljs-built_in">this</span>.formateTime(<span class="hljs-built_in">this</span>.audio.duration));
    <span class="hljs-built_in">this</span>.loadLyrics();
  &#125;
<span class="hljs-function"><span class="hljs-title">playPrevSong</span>(<span class="hljs-params"></span>)</span> &#123;
    <span class="hljs-built_in">this</span>.currentIndex =
      (<span class="hljs-built_in">this</span>.songList.length + <span class="hljs-built_in">this</span>.currentIndex - <span class="hljs-number">1</span>) % <span class="hljs-built_in">this</span>.songList.length;
    <span class="hljs-built_in">this</span>.audio.src = <span class="hljs-built_in">this</span>.songList[<span class="hljs-built_in">this</span>.currentIndex].url;
    <span class="hljs-built_in">this</span>.audio.play();
    <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".play-pause"</span>).classList.add(<span class="hljs-string">"playing"</span>);
    <span class="hljs-built_in">this</span>.renderSong();
  &#125;
<span class="hljs-function"><span class="hljs-title">playNextSong</span>(<span class="hljs-params"></span>)</span> &#123;
    <span class="hljs-built_in">this</span>.currentIndex = (<span class="hljs-built_in">this</span>.currentIndex + <span class="hljs-number">1</span>) % <span class="hljs-built_in">this</span>.songList.length;
    <span class="hljs-built_in">this</span>.audio.src = <span class="hljs-built_in">this</span>.songList[<span class="hljs-built_in">this</span>.currentIndex].url;
    <span class="hljs-built_in">this</span>.audio.play();
    <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".play-pause"</span>).classList.add(<span class="hljs-string">"playing"</span>);
    <span class="hljs-built_in">this</span>.renderSong();
  &#125;
<span class="hljs-function"><span class="hljs-title">loadLyrics</span>(<span class="hljs-params"></span>)</span> &#123;
    <span class="hljs-built_in">this</span>.setLyrics(<span class="hljs-built_in">this</span>.songList[<span class="hljs-built_in">this</span>.currentIndex].lyric.lrc.lyric);
  &#125;
  <span class="hljs-function"><span class="hljs-title">locateLyric</span>(<span class="hljs-params"></span>)</span> &#123;
    <span class="hljs-keyword">const</span> currentTime = (<span class="hljs-built_in">this</span>.audio?.currentTime ?? <span class="hljs-number">0</span>) * <span class="hljs-number">1000</span>;
    <span class="hljs-keyword">for</span> (<span class="hljs-keyword">let</span> index = <span class="hljs-number">0</span>; index < <span class="hljs-built_in">this</span>.lyricsArr.length; index++) &#123;
      <span class="hljs-keyword">if</span> (<span class="hljs-built_in">this</span>.lyricsArr[index][<span class="hljs-number">0</span>] < currentTime) &#123;
        <span class="hljs-built_in">this</span>.lyricIndex = index;
      &#125; <span class="hljs-keyword">else</span> &#123;
        <span class="hljs-keyword">break</span>;
      &#125;
    &#125;
    <span class="hljs-keyword">let</span> node = <span class="hljs-built_in">this</span>.$(
      <span class="hljs-string">'[data-time="'</span> + <span class="hljs-built_in">this</span>.lyricsArr[<span class="hljs-built_in">this</span>.lyricIndex][<span class="hljs-number">0</span>] + <span class="hljs-string">'"]'</span>
    );
    <span class="hljs-keyword">if</span> (node) &#123;
      <span class="hljs-built_in">this</span>.setLyricToCenter(node);
    &#125;
    <span class="hljs-built_in">this</span>.$$(<span class="hljs-string">".panel-effect .lyrics p"</span>)[<span class="hljs-number">0</span>].innerText =
      <span class="hljs-built_in">this</span>.lyricsArr[<span class="hljs-built_in">this</span>.lyricIndex][<span class="hljs-number">1</span>];
    <span class="hljs-built_in">this</span>.$$(<span class="hljs-string">".panel-effect .lyrics p"</span>)[<span class="hljs-number">1</span>].innerText = <span class="hljs-built_in">this</span>.lyricsArr[
      <span class="hljs-built_in">this</span>.lyricIndex + <span class="hljs-number">1</span>
    ]
      ? <span class="hljs-built_in">this</span>.lyricsArr[<span class="hljs-built_in">this</span>.lyricIndex + <span class="hljs-number">1</span>][<span class="hljs-number">1</span>]
      : <span class="hljs-string">""</span>;
  &#125;
<span class="hljs-function"><span class="hljs-title">setLyrics</span>(<span class="hljs-params">lyrics</span>)</span> &#123;
    <span class="hljs-built_in">this</span>.lyricIndex = <span class="hljs-number">0</span>;
    <span class="hljs-keyword">let</span> fragment = <span class="hljs-built_in">document</span>.createDocumentFragment();
    <span class="hljs-built_in">this</span>.lyricsArr = [];
    lyrics
      .split(<span class="hljs-regexp">/\n/</span>)
      .filter(<span class="hljs-function">(<span class="hljs-params">str</span>) =></span> str.match(<span class="hljs-regexp">/\[.+?\]/</span>))
      .forEach(<span class="hljs-function">(<span class="hljs-params">line</span>) =></span> &#123;
        <span class="hljs-keyword">let</span> str = line.replace(<span class="hljs-regexp">/\[.+?\]/g</span>, <span class="hljs-string">""</span>);
        line.match(<span class="hljs-regexp">/\[.+?\]/g</span>).forEach(<span class="hljs-function">(<span class="hljs-params">t</span>) =></span> &#123;
          t = t.replace(<span class="hljs-regexp">/[\[\]]/g</span>, <span class="hljs-string">""</span>);
          <span class="hljs-keyword">let</span> milliseconds =
            <span class="hljs-built_in">parseInt</span>(t.slice(<span class="hljs-number">0</span>, <span class="hljs-number">2</span>)) * <span class="hljs-number">60</span> * <span class="hljs-number">1000</span> +
            <span class="hljs-built_in">parseInt</span>(t.slice(<span class="hljs-number">3</span>, <span class="hljs-number">5</span>)) * <span class="hljs-number">1000</span> +
            <span class="hljs-built_in">parseInt</span>(t.slice(<span class="hljs-number">6</span>));
          <span class="hljs-built_in">this</span>.lyricsArr.push([milliseconds, str]);
        &#125;);
      &#125;);
<span class="hljs-built_in">this</span>.lyricsArr = <span class="hljs-built_in">this</span>.lyricsArr
      .filter(<span class="hljs-function">(<span class="hljs-params">line</span>) =></span> line[<span class="hljs-number">1</span>].trim() !== <span class="hljs-string">""</span>)
      .sort(<span class="hljs-function">(<span class="hljs-params">v1, v2</span>) =></span> &#123;
        <span class="hljs-keyword">if</span> (v1[<span class="hljs-number">0</span>] > v2[<span class="hljs-number">0</span>]) &#123;
          <span class="hljs-keyword">return</span> <span class="hljs-number">1</span>;
        &#125; <span class="hljs-keyword">else</span> &#123;
          <span class="hljs-keyword">return</span> -<span class="hljs-number">1</span>;
        &#125;
      &#125;);
<span class="hljs-built_in">this</span>.lyricsArr.forEach(<span class="hljs-function">(<span class="hljs-params">line</span>) =></span> &#123;
      <span class="hljs-keyword">let</span> node = <span class="hljs-built_in">document</span>.createElement(<span class="hljs-string">"p"</span>);
      node.setAttribute(<span class="hljs-string">"data-time"</span>, line[<span class="hljs-number">0</span>]);
      node.innerText = line[<span class="hljs-number">1</span>];
      fragment.appendChild(node);
    &#125;);
    <span class="hljs-built_in">this</span>.$$(<span class="hljs-string">".panel-effect .lyrics p"</span>)[<span class="hljs-number">0</span>].innerText =
      <span class="hljs-built_in">this</span>.lyricsArr[<span class="hljs-built_in">this</span>.lyricIndex][<span class="hljs-number">1</span>];
    <span class="hljs-built_in">this</span>.$$(<span class="hljs-string">".panel-effect .lyrics p"</span>)[<span class="hljs-number">1</span>].innerText = <span class="hljs-built_in">this</span>.lyricsArr[
      <span class="hljs-built_in">this</span>.lyricIndex + <span class="hljs-number">1</span>
    ]
      ? <span class="hljs-built_in">this</span>.lyricsArr[<span class="hljs-built_in">this</span>.lyricIndex + <span class="hljs-number">1</span>][<span class="hljs-number">1</span>]
      : <span class="hljs-string">""</span>;
    <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".panel-lyrics .container"</span>).innerHTML = <span class="hljs-string">""</span>;
    <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".panel-lyrics .container"</span>).appendChild(fragment);
  &#125;
 <span class="hljs-function"><span class="hljs-title">setLyricToCenter</span>(<span class="hljs-params">node</span>)</span> &#123;
    <span class="hljs-keyword">let</span> offset = node.offsetTop - <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".panel-lyrics"</span>).offsetHeight / <span class="hljs-number">2</span>;
    <span class="hljs-built_in">this</span>.$(
      <span class="hljs-string">".panel-lyrics .container"</span>
    ).style.transform = <span class="hljs-string">`translateY(<span class="hljs-subst">$&#123;-offset&#125;</span>px)`</span>;
    <span class="hljs-built_in">this</span>.$$(<span class="hljs-string">".panel-lyrics p"</span>).forEach(<span class="hljs-function">(<span class="hljs-params">node</span>) =></span> &#123;
      node.classList.remove(<span class="hljs-string">"current"</span>);
    &#125;);
    node.classList.add(<span class="hljs-string">"current"</span>);
  &#125;

  <span class="hljs-function"><span class="hljs-title">setProgerssBar</span>(<span class="hljs-params"></span>)</span> &#123;
    <span class="hljs-keyword">let</span> percent = (<span class="hljs-built_in">this</span>.audio.currentTime * <span class="hljs-number">100</span>) / <span class="hljs-built_in">this</span>.audio.duration + <span class="hljs-string">"%"</span>;
    <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".bar .progress"</span>).style.width = percent;
    <span class="hljs-built_in">this</span>.$(<span class="hljs-string">".time-start"</span>).innerText = <span class="hljs-built_in">this</span>.formateTime(<span class="hljs-built_in">this</span>.audio.currentTime);
  &#125;

  <span class="hljs-function"><span class="hljs-title">formateTime</span>(<span class="hljs-params">secondsTotal</span>)</span> &#123;
    <span class="hljs-keyword">let</span> minutes = <span class="hljs-built_in">parseInt</span>(secondsTotal / <span class="hljs-number">60</span>);
    minutes = minutes >= <span class="hljs-number">10</span> ? <span class="hljs-string">""</span> + minutes : <span class="hljs-string">"0"</span> + minutes;
    <span class="hljs-keyword">let</span> seconds = <span class="hljs-built_in">parseInt</span>(secondsTotal % <span class="hljs-number">60</span>);
    seconds = seconds >= <span class="hljs-number">10</span> ? <span class="hljs-string">""</span> + seconds : <span class="hljs-string">"0"</span> + seconds;
    <span class="hljs-keyword">return</span> minutes + <span class="hljs-string">":"</span> + seconds;
  &#125;
&#125;

<span class="hljs-built_in">window</span>.p = <span class="hljs-keyword">new</span> Player(<span class="hljs-string">"#player"</span>);
<span class="copy-code-btn">复制代码</span></code></pre></div>  
</div>
            
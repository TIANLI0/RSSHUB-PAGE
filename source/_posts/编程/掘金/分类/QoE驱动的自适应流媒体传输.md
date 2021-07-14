
---
title: 'QoE驱动的自适应流媒体传输'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e26c4c36c000490b856148bd3cbe865e~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Tue, 13 Jul 2021 01:59:44 GMT
thumbnail: 'https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e26c4c36c000490b856148bd3cbe865e~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h1 data-id="heading-0">背景</h1>
<p>随着科技技术发展以及人们生活娱乐方式转变，视频消费成为日常生活不可获取的一部分。在当下社会，用户可能随时随地都会观看视频，用户的网络环境会变复杂。为解决在复杂场景比如网络速度不足、弱网以及网络频繁抖动等情况下，用户观看视频不流畅的问题，自适应流媒体应运而生。自适应流媒体是一种思想，一种技术实现，能够在复杂的网络状况下为用户提供更好的播放体验。</p>
<p>举个🌰，下面是一个简单的场景，通过模拟网速变化，来观察自动挡清晰度选择的变化。限制网速情况下，播放清晰度会从1080P下调为360P清晰度，降低发生卡顿的几率，尽可能保证视频能够流畅播放；当放开网速限制后，清晰度会逐步上调，为用户播放更高清晰度的视频，提升视频观看体验。</p>
<div align="center">
<img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e26c4c36c000490b856148bd3cbe865e~tplv-k3u1fbpfcp-watermark.image" loading="lazy" referrerpolicy="no-referrer">
</div>
<h1 data-id="heading-1">自适应流媒体传输</h1>
<h2 data-id="heading-2">QoE</h2>
<p>体验质量（Quality of Experience，QoE）是指用户对设备，网络和系统，应用或业务的质量和性能的综合主观感受。在视频播放场景下，衡量用户播放体验的指标分为首开，清晰度以及流畅度。自适应码率策略追求的QoE 指标一般包括，最小化卡顿次数以及卡顿频率，最大化视频平均播放码率，最小化码率切换频率以及码率切换幅值，最小化启动延迟等。</p>
<h2 data-id="heading-3">流媒体传输技术</h2>
<h3 data-id="heading-4">流媒体</h3>
<p>流媒体是指将一连串的媒体数据压缩后，经过网上分段发送数据，在网上即时传输影音以供观赏的一种技术与过程，此技术使得数据包得以像流水一样发送；如果不使用此技术，就必须在使用前下载整个媒体文件。</p>
<p>流媒体实际指的是一种新的媒体传送方式，有声音流、视频流、文本流、图像流、动画流等，而非一种新的媒体。流媒体最主要的技术特征就是流式传输，它使得数据可以像流水一样传输。流式传输是指通过网络传送媒体技术的总称。</p>
<h3 data-id="heading-5">自适应码率</h3>
<p>什么是ABR（Adaptive Bit-Rate）</p>
<blockquote>
<p>为了适应不同用户网络带宽的变化，防止用户播放过程产生卡顿，保证用户观看质量，大部分视频相关产品采用了基于HTTP的自适应码率（ABR，Adaptive Bit-Rate）策略（如：B站、优酷、YouTube等），不同产品有不同的自适应码率（ABR）方案。简单而言，就是给用户提供「自动」档位，参考用户端播放情况，给用户实时选择最适合的播放档位。</p>
</blockquote>
<h3 data-id="heading-6">流式传输实现</h3>
<p>实现流式传输主要有两种方式：实时流式传输（Real Time Streaming）和渐进式流式传输（Progressive Streaming）</p>
<ul>
<li>实时流媒体</li>
</ul>
<p>代表：RTSP (Real Time Streaming Protocol )，RTMP (Real Time Messaging Protocol)</p>
<p>实时流媒体协议优点是 延迟低，稳定性高，编码兼容性高,安全性高等，缺点是需要额外部署流媒体服务器，存在被防火墙拦截的风险</p>
<ul>
<li>渐进式HTTP流媒体传输</li>
</ul>
<blockquote>
<p>基于HTTP协议，从服务端向客户端传输媒体数据。用户无需等到所有媒体数据下载完成，只需要获取到meta数据以及部分音视频数据，即可播放，即通常说的"边下边播"。</p>
</blockquote>
<p>优点：不需要额外部署服务器，缺点启动延迟相对高，安全性低</p>
<h3 data-id="heading-7">在线视频播放逻辑发展历程</h3>
<div align="center">
<img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/991f9439381b4e108b3491956eaa4149~tplv-k3u1fbpfcp-watermark.image" loading="lazy" referrerpolicy="no-referrer">
</div>
<h2 data-id="heading-8">自适应HTTP流媒体传输</h2>
<p>自适应多码率方案的核心，依据网络状态、播放状态等信息，动态调整请求视频流的清晰度（码率），从而在流畅度、清晰度和平滑性上取得平衡，最大化用户体验。基于HTTP的自适应工作原理是把整个流分成一个个小的基于 HTTP 的文件来下载，每次只下载一些。当媒体流正在播放时，客户端可以选择从许多不同的备用源中以不同的速率下载同样的资源，允许流媒体会话适应不同的数据速率。</p>
<p><strong>关键名词</strong></p>
<blockquote>
<p>多码率：基于同一个视频源，会生成多种清晰度的视频<br>
分片：按照固定长度对视频进行切割，生成多个小分片视频<br>
分片对齐：不同清晰度对应的同一时间的分片，内容相同</p>
</blockquote>
<p>自适应的直观效果如下图所示：</p>
<div align="center">
<img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2c9aa6f5428742fb80df72a2100882fc~tplv-k3u1fbpfcp-watermark.image" loading="lazy" referrerpolicy="no-referrer"><br>
图片来自 https://mp.weixin.qq.com/s/thnhhbw2ieFywCFSCHXyGQ
</div>
<h3 data-id="heading-9">流程</h3>
<p><img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/cc0693d0aed04bf0a9c0930f9cdee1e5~tplv-k3u1fbpfcp-watermark.image" alt="流程图 (1).jpg" loading="lazy" referrerpolicy="no-referrer"></p>
<ol>
<li>主播直播流上传/用户视频源</li>
<li>服务器的编解码封装</li>
<li>流媒体分发器
<ul>
<li>描述文件</li>
<li>切割后的媒体文件</li>
</ul>
</li>
<li>客户端
<ul>
<li>客户端加载并解析描述文件，组成文件下载链接</li>
<li>当前的网速和支持的编码加载相应的视频片段进行播放</li>
</ul>
</li>
</ol>
<h3 data-id="heading-10">基于HTTP的自适应协议对比</h3>
<p>现有的自适应协议有以下几种，HLS协议最先出现，由苹果公司提出，主要是为了解决RTMP协议存在的一些问题。比如 RTMP 协议不使用标准的 HTTP 接口传输数据，所以在一些特殊的网络环境下可能被防火墙屏蔽掉。HLS基于HTTP，容易通过 CDN（内容分发网络）来传输媒体流。后来陆续出现HDS、MSS以及DASH，其中MPEG-DASH为国际化标准。不同协议之间，基准思路相同，实现细节上有差异。</p>
<blockquote>
<p>Apple HTTP Live Streaming (HLS)<br>
Adobe HTTP Dynamic Streaming (HDS)<br>
Microsoft Smooth Streaming (MSS)<br>
MPEG Dynamic Adaptive Streaming over HTTP (MPEG-DASH)</p>
</blockquote>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7a00f0a2f0ef4b819fa0b64f732a7c5e~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h3 data-id="heading-11">DASH协议示例</h3>
<p>DASH协议中描述分片的描述文件,描述音视频时长，编码，清晰度，加密等信息。可以通过解析描述文件，获取音视频集合信息，获取地址规则，解析出具体的音视频地址。</p>
<pre><code class="hljs language-xml copyable" lang="xml"><span class="hljs-tag"><<span class="hljs-name">MPD</span> <span class="hljs-attr">xmlns</span>=<span class="hljs-string">"urn:mpeg:dash:schema:mpd:2011"</span> <span class="hljs-attr">xmlns:cenc</span>=<span class="hljs-string">"urn:mpeg:cenc:2013"</span> <span class="hljs-attr">minBufferTime</span>=<span class="hljs-string">"PT5.00S"</span> <span class="hljs-attr">type</span>=<span class="hljs-string">"static"</span> <span class="hljs-attr">mediaPresentationDuration</span>=<span class="hljs-string">"PT1H22M27.000S"</span> <span class="hljs-attr">profiles</span>=<span class="hljs-string">"urn:mpeg:dash:profile:isoff-live:2011"</span>></span>
  <span class="hljs-tag"><<span class="hljs-name">ProgramInformation</span> <span class="hljs-attr">moreInformationURL</span>=<span class="hljs-string">"http://gpac.sourceforge.net"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">Title</span>></span>Merged MPD<span class="hljs-tag"></<span class="hljs-name">Title</span>></span>
  <span class="hljs-tag"></<span class="hljs-name">ProgramInformation</span>></span>
  <span class="hljs-tag"><<span class="hljs-name">Period</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">AdaptationSet</span> <span class="hljs-attr">segmentAlignment</span>=<span class="hljs-string">"true"</span> <span class="hljs-attr">bitstreamSwitching</span>=<span class="hljs-string">"true"</span> <span class="hljs-attr">maxWidth</span>=<span class="hljs-string">"688"</span> <span class="hljs-attr">maxHeight</span>=<span class="hljs-string">"382"</span> <span class="hljs-attr">mimeType</span>=<span class="hljs-string">"video/mp4"</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">Representation</span> <span class="hljs-attr">id</span>=<span class="hljs-string">"1"</span> <span class="hljs-attr">codecs</span>=<span class="hljs-string">"avc1.640015"</span> <span class="hljs-attr">width</span>=<span class="hljs-string">"572"</span> <span class="hljs-attr">height</span>=<span class="hljs-string">"320"</span> <span class="hljs-attr">frameRate</span>=<span class="hljs-string">"25"</span> <span class="hljs-attr">bandwidth</span>=<span class="hljs-string">"1371070"</span> <span class="hljs-attr">scanType</span>=<span class="hljs-string">"progressive"</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">BaseURL</span>></span>tos-cn-vd-0026/abd43ed9655c493ab9fa7a51ef696a92/<span class="hljs-tag"></<span class="hljs-name">BaseURL</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">SegmentTemplate</span> <span class="hljs-attr">timescale</span>=<span class="hljs-string">"1000"</span> <span class="hljs-attr">media</span>=<span class="hljs-string">"1_$Number%04d$"</span> <span class="hljs-attr">startNumber</span>=<span class="hljs-string">"1"</span> <span class="hljs-attr">duration</span>=<span class="hljs-string">"5000"</span> <span class="hljs-attr">initialization</span>=<span class="hljs-string">"1_init"</span>></span><span class="hljs-tag"></<span class="hljs-name">SegmentTemplate</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">ContentProtection</span> <span class="hljs-attr">schemeIdUri</span>=<span class="hljs-string">"urn:mpeg:dash:mp4protection:2011"</span> <span class="hljs-attr">value</span>=<span class="hljs-string">"cenc"</span> <span class="hljs-attr">cenc:default_KID</span>=<span class="hljs-string">"5ef57228-d0bb-309b-c310-b6670002043b"</span>></span><span class="hljs-tag"></<span class="hljs-name">ContentProtection</span>></span>
      <span class="hljs-tag"></<span class="hljs-name">Representation</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">Representation</span> <span class="hljs-attr">id</span>=<span class="hljs-string">"2"</span> <span class="hljs-attr">codecs</span>=<span class="hljs-string">"avc1.640015"</span> <span class="hljs-attr">width</span>=<span class="hljs-string">"430"</span> <span class="hljs-attr">height</span>=<span class="hljs-string">"240"</span> <span class="hljs-attr">frameRate</span>=<span class="hljs-string">"25"</span> <span class="hljs-attr">bandwidth</span>=<span class="hljs-string">"864691"</span> <span class="hljs-attr">scanType</span>=<span class="hljs-string">"progressive"</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">BaseURL</span>></span>tos-cn-vd-0026/8970023cc97246c8861313657dd9d028/<span class="hljs-tag"></<span class="hljs-name">BaseURL</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">SegmentTemplate</span> <span class="hljs-attr">timescale</span>=<span class="hljs-string">"1000"</span> <span class="hljs-attr">media</span>=<span class="hljs-string">"1_$Number%04d$"</span> <span class="hljs-attr">startNumber</span>=<span class="hljs-string">"1"</span> <span class="hljs-attr">duration</span>=<span class="hljs-string">"5000"</span> <span class="hljs-attr">initialization</span>=<span class="hljs-string">"1_init"</span>></span><span class="hljs-tag"></<span class="hljs-name">SegmentTemplate</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">ContentProtection</span> <span class="hljs-attr">schemeIdUri</span>=<span class="hljs-string">"urn:mpeg:dash:mp4protection:2011"</span> <span class="hljs-attr">value</span>=<span class="hljs-string">"cenc"</span> <span class="hljs-attr">cenc:default_KID</span>=<span class="hljs-string">"5ef57228-d0bb-309b-c310-b6670002043b"</span>></span><span class="hljs-tag"></<span class="hljs-name">ContentProtection</span>></span>
      <span class="hljs-tag"></<span class="hljs-name">Representation</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">Representation</span> <span class="hljs-attr">id</span>=<span class="hljs-string">"3"</span> <span class="hljs-attr">codecs</span>=<span class="hljs-string">"avc1.64001E"</span> <span class="hljs-attr">width</span>=<span class="hljs-string">"688"</span> <span class="hljs-attr">height</span>=<span class="hljs-string">"382"</span> <span class="hljs-attr">frameRate</span>=<span class="hljs-string">"25"</span> <span class="hljs-attr">bandwidth</span>=<span class="hljs-string">"1973187"</span> <span class="hljs-attr">scanType</span>=<span class="hljs-string">"progressive"</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">BaseURL</span>></span>tos-cn-vd-0026/23f05dc6987c46b69c92fc21636ca748/<span class="hljs-tag"></<span class="hljs-name">BaseURL</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">SegmentTemplate</span> <span class="hljs-attr">timescale</span>=<span class="hljs-string">"1000"</span> <span class="hljs-attr">media</span>=<span class="hljs-string">"1_$Number%04d$"</span> <span class="hljs-attr">startNumber</span>=<span class="hljs-string">"1"</span> <span class="hljs-attr">duration</span>=<span class="hljs-string">"5000"</span> <span class="hljs-attr">initialization</span>=<span class="hljs-string">"1_init"</span>></span><span class="hljs-tag"></<span class="hljs-name">SegmentTemplate</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">ContentProtection</span> <span class="hljs-attr">schemeIdUri</span>=<span class="hljs-string">"urn:mpeg:dash:mp4protection:2011"</span> <span class="hljs-attr">value</span>=<span class="hljs-string">"cenc"</span> <span class="hljs-attr">cenc:default_KID</span>=<span class="hljs-string">"5ef57228-d0bb-309b-c310-b6670002043b"</span>></span><span class="hljs-tag"></<span class="hljs-name">ContentProtection</span>></span>
      <span class="hljs-tag"></<span class="hljs-name">Representation</span>></span>
    <span class="hljs-tag"></<span class="hljs-name">AdaptationSet</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">AdaptationSet</span> <span class="hljs-attr">segmentAlignment</span>=<span class="hljs-string">"true"</span> <span class="hljs-attr">mimeType</span>=<span class="hljs-string">"audio/mp4"</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">Representation</span> <span class="hljs-attr">id</span>=<span class="hljs-string">"4"</span> <span class="hljs-attr">codecs</span>=<span class="hljs-string">"mp4a.40.2"</span> <span class="hljs-attr">bandwidth</span>=<span class="hljs-string">"70947"</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">BaseURL</span>></span>tos-cn-vd-0026/abd43ed9655c493ab9fa7a51ef696a92/<span class="hljs-tag"></<span class="hljs-name">BaseURL</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">SegmentTemplate</span> <span class="hljs-attr">timescale</span>=<span class="hljs-string">"1000"</span> <span class="hljs-attr">media</span>=<span class="hljs-string">"2_$Number%04d$"</span> <span class="hljs-attr">startNumber</span>=<span class="hljs-string">"1"</span> <span class="hljs-attr">duration</span>=<span class="hljs-string">"5000"</span> <span class="hljs-attr">initialization</span>=<span class="hljs-string">"2_init"</span>></span><span class="hljs-tag"></<span class="hljs-name">SegmentTemplate</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">AudioChannelConfiguration</span> <span class="hljs-attr">schemeIdUri</span>=<span class="hljs-string">"urn:mpeg:dash:23003:3:audio_channel_configuration:2011"</span> <span class="hljs-attr">value</span>=<span class="hljs-string">"2"</span>></span><span class="hljs-tag"></<span class="hljs-name">AudioChannelConfiguration</span>></span>
      <span class="hljs-tag"></<span class="hljs-name">Representation</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">Representation</span> <span class="hljs-attr">id</span>=<span class="hljs-string">"5"</span> <span class="hljs-attr">codecs</span>=<span class="hljs-string">"mp4a.40.2"</span> <span class="hljs-attr">bandwidth</span>=<span class="hljs-string">"70947"</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">BaseURL</span>></span>tos-cn-vd-0026/8970023cc97246c8861313657dd9d028/<span class="hljs-tag"></<span class="hljs-name">BaseURL</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">SegmentTemplate</span> <span class="hljs-attr">timescale</span>=<span class="hljs-string">"1000"</span> <span class="hljs-attr">media</span>=<span class="hljs-string">"2_$Number%04d$"</span> <span class="hljs-attr">startNumber</span>=<span class="hljs-string">"1"</span> <span class="hljs-attr">duration</span>=<span class="hljs-string">"5000"</span> <span class="hljs-attr">initialization</span>=<span class="hljs-string">"2_init"</span>></span><span class="hljs-tag"></<span class="hljs-name">SegmentTemplate</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">AudioChannelConfiguration</span> <span class="hljs-attr">schemeIdUri</span>=<span class="hljs-string">"urn:mpeg:dash:23003:3:audio_channel_configuration:2011"</span> <span class="hljs-attr">value</span>=<span class="hljs-string">"2"</span>></span><span class="hljs-tag"></<span class="hljs-name">AudioChannelConfiguration</span>></span>
      <span class="hljs-tag"></<span class="hljs-name">Representation</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">Representation</span> <span class="hljs-attr">id</span>=<span class="hljs-string">"6"</span> <span class="hljs-attr">codecs</span>=<span class="hljs-string">"mp4a.40.2"</span> <span class="hljs-attr">bandwidth</span>=<span class="hljs-string">"102853"</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">BaseURL</span>></span>tos-cn-vd-0026/23f05dc6987c46b69c92fc21636ca748/<span class="hljs-tag"></<span class="hljs-name">BaseURL</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">SegmentTemplate</span> <span class="hljs-attr">timescale</span>=<span class="hljs-string">"1000"</span> <span class="hljs-attr">media</span>=<span class="hljs-string">"2_$Number%04d$"</span> <span class="hljs-attr">startNumber</span>=<span class="hljs-string">"1"</span> <span class="hljs-attr">duration</span>=<span class="hljs-string">"5000"</span> <span class="hljs-attr">initialization</span>=<span class="hljs-string">"2_init"</span>></span><span class="hljs-tag"></<span class="hljs-name">SegmentTemplate</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">AudioChannelConfiguration</span> <span class="hljs-attr">schemeIdUri</span>=<span class="hljs-string">"urn:mpeg:dash:23003:3:audio_channel_configuration:2011"</span> <span class="hljs-attr">value</span>=<span class="hljs-string">"2"</span>></span><span class="hljs-tag"></<span class="hljs-name">AudioChannelConfiguration</span>></span>
      <span class="hljs-tag"></<span class="hljs-name">Representation</span>></span>
    <span class="hljs-tag"></<span class="hljs-name">AdaptationSet</span>></span>
  <span class="hljs-tag"></<span class="hljs-name">Period</span>></span>
<span class="hljs-tag"></<span class="hljs-name">MPD</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h1 data-id="heading-12">码率自适应策略</h1>
<p>目前基于HTTP的动态自适应流媒体传输技术已经成为了网络视频传输的主要技术，从系统的角度来讲，自适应码率策略基本可以分为几类：</p>
<ol>
<li>基于客户端的自适应码率策略</li>
<li>基于服务端的自适应码率策略</li>
<li>基于网络信息的自适应码率策略（考虑网络相关的信息）</li>
<li>混合模式的自适应码率策略（可能是基于客户端、基于服务端、基于网络信息的自适应码率策略中，一种或者多种策略的组合）</li>
</ol>
<p>具体分类如下图所示：</p>
<p><img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7ffdec7a841d4b97a1e31f7b6e1b0093~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h2 data-id="heading-13">基于客户端的码率自适应策略</h2>
<p>基于客户端的自适应码率策略一般通过监测客户端可用带宽、播放器缓冲区大小等信息，来切换合适的视频码率片段，以达到适应网络带宽波动性的目的，从而提升用户QoE。</p>
<div align="center">
<img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9849d0a840e447708ebe606d2d52925f~tplv-k3u1fbpfcp-watermark.image" loading="lazy" referrerpolicy="no-referrer">
</div>
<p>基于客户端的自适应码率策略也可以分为以下几类：</p>
<ol>
<li>基于带宽预测，该类方法通过预测客户端的可用带宽，来作为下一个视频片段码率选择的依据。然而，由于带宽预测的不准确性，一般而言，基于带宽预测的方法难以提供较高的QoE，并会导致较为频繁的视播放器缓冲区抖动，从而使得用户视频观看质量不佳。通常有以下三种方式来计算客户端的可用带宽。
<ul>
<li>基于上一片段有效带宽（LSB）</li>
<li>基于 会话带宽平均 (SAB)</li>
<li>基于滑动窗口平均 (WAB)</li>
</ul>
</li>
</ol>
<p>在点播下，可以通过描述文件获取到不同清晰度的码率信息。当预测带宽高时选择高码率视频，预测带宽低时选择低码率视频。</p>
<ol start="2">
<li>基于播放器缓冲区的自适应码率方法，在该类方法中，客户端使用播放缓冲区占用多少作为标准，来选择下一特定码率的视频片段来进行播放。</li>
</ol>
<div align="center">
<img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b2feb56eefc84213ad79ada1ac78b584~tplv-k3u1fbpfcp-watermark.image" loading="lazy" referrerpolicy="no-referrer">
</div>  
基于双阈值缓冲区大小的方案，将缓冲区分为多段。当buffer数据大于Qb_max阈值，则增加码率等级，选择比当前清晰度高的一个清晰度；当数据增加至Qmax时，参考预测带宽增加码率；当数据减少至Qmin时，根据预测带宽降低码率；数据降低至Qb_min时，根据buffer降低码率。
<ol start="3">
<li>混合模式的自适应码率方法，在该类方法中，通过综合考虑可用带宽，播放器缓冲区大小，播放速度，播放器视觉窗口大小等因素，来进行自适应码率算法决策。</li>
</ol>
<div align="center">
<img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/fec9892ac33d444cb56f73b8c8be1872~tplv-k3u1fbpfcp-watermark.image" loading="lazy" referrerpolicy="no-referrer"><br>
图片来自https://zhuanlan.zhihu.com/p/160774505
</div>
<ol start="4">
<li>基于机器学习的自适应码率方法，利用大数据以及强化学习，深度学习等，计算出数据模型，通过数据模型来进行决策。相比上述通过建立各种模型或规则来控制码率选择的启发式的策略，机器学习的方式，可以“自主地”学习出一个适应当前网络状态的ABR算法。</li>
</ol>
<h2 data-id="heading-14">基于服务端的码率自适应策略</h2>
<p>基于服务端的自适应码率策略采用服务端码率主动调整策略，不需要客户端的额外支持便可以完成自适应码率。服务端驱动方法由负责媒体内容分发的HTTP服务器作出码率选择决策，根据服务器端发送缓冲区大小或客户端反馈的播放缓冲区大小，测量服务器端与客户端之间链路的网络吞吐量及客户端分辨率、处理能力等，由服务端选择特定码率媒体分片进行发送。
服务端驱动的码率自适应选择方法是一种“瘦客户端，胖服务端”的方法，该方法降低了客户端软件开发的复杂度，简化了客户端软件更新过程。然而，该类方法由于需要服务端单独控制每个客户端的发送缓冲区状态信息，收集服务端与客户端之间的网络连接状态信息等确定待发送的媒体分片码率，增大了服务器的处理负载，导致系统可扩展性较差。同时，服务端驱动的码率自适应方法需要修改Web服务器功能，需要得到网络服务提供商的支持，增大了系统部署难度。因此，当前主流的流媒体分发系统主要采用基于客户端驱动的码率自适应选择方法。</p>
<p><img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/24dcde597c31444c9d5dedc00c9ca632~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h2 data-id="heading-15">基于网络信息的码率自适应策略</h2>
<p>基于网络信息的自适应码率策略允许客户端利用网络层相关的信息来做码率选择决策。这种策略一般是在收集一些测量的网络状态信息后，通知客户端来做出合适的码率选择，但是，网络信息的收集和处理需要一些特殊的模块来完成（比如网络代理等），该方法可以通过充分利用网络信息来完成更好的码率选择决策。</p>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/99b044a1d31d4ebfa98dd94bf5cd2c9d~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h2 data-id="heading-16">混合模式的码率自适应策略</h2>
<p>混合模式的自适应码率策略可以通过收集很多网络相关的信息、客户端相关的信息、以及服务端相关的信息来帮助客户端做出更好的码率选择决策。</p>
<h1 data-id="heading-17">总结</h1>
<p>自适应流媒体技术本身可以带来更好的用户体验，在实际播放场景下，产品会对QoE有不同侧重，比如有这种场景，需要在控制卡顿次数情况下，尽可能保证用户观看高清视频，这种场景反过来会驱动自适应算法的调整来满足需求。</p></div>  
</div>
            
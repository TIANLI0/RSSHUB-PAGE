
---
title: 'react native基于react-native-image-crop-picker 实现的视频多选'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/86dc18ca59c648e983eba9ee143573a6~tplv-k3u1fbpfcp-zoom-1.image'
author: 掘金
comments: false
date: Tue, 13 Jul 2021 01:54:48 GMT
thumbnail: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/86dc18ca59c648e983eba9ee143573a6~tplv-k3u1fbpfcp-zoom-1.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h1 data-id="heading-0">1 参考</h1>
<ul>
<li><a href="https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fmarlti7%2Freact-native-image-crop-picker" target="_blank" rel="nofollow noopener noreferrer" title="https://github.com/marlti7/react-native-image-crop-picker" ref="nofollow noopener noreferrer">react-native-image-crop-picker  Github仓库地址</a></li>
</ul>
<h1 data-id="heading-1">2 效果</h1>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/86dc18ca59c648e983eba9ee143573a6~tplv-k3u1fbpfcp-zoom-1.image" alt="在这里插入图片描述" loading="lazy" referrerpolicy="no-referrer">
<img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/433696a3845d447a82441b17ff5241fb~tplv-k3u1fbpfcp-zoom-1.image" alt="在这里插入图片描述" loading="lazy" referrerpolicy="no-referrer">
<img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6a907b2d5b6044d0bb1cb51f163befd2~tplv-k3u1fbpfcp-zoom-1.image" alt="在这里插入图片描述" loading="lazy" referrerpolicy="no-referrer"></p>
<h1 data-id="heading-2">3  前言</h1>
<ul>
<li>主要是使用到了lodash 给的<a href="https://link.juejin.cn/?target=https%3A%2F%2Fwww.lodashjs.com%2Fdocs%2Flodash.chunk" target="_blank" rel="nofollow noopener noreferrer" title="https://www.lodashjs.com/docs/lodash.chunk" ref="nofollow noopener noreferrer">chunk </a> 对数组进行了处理。然后使用map嵌套循环遍历数组创建多个视频的缩略图。</li>
</ul>
<h1 data-id="heading-3">4 源码</h1>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">/**
 * 多选 图片、视频
 */</span>
<span class="hljs-keyword">import</span> React, &#123; useState, useEffect &#125; <span class="hljs-keyword">from</span> <span class="hljs-string">'react'</span>;
<span class="hljs-keyword">import</span> &#123; View, TouchableOpacity, Image &#125; <span class="hljs-keyword">from</span> <span class="hljs-string">'react-native'</span>;
<span class="hljs-keyword">import</span> &#123; pxToDp &#125; <span class="hljs-keyword">from</span> <span class="hljs-string">'../../utils/stylesKits'</span>;
<span class="hljs-keyword">import</span> Icon <span class="hljs-keyword">from</span> <span class="hljs-string">'react-native-vector-icons/FontAwesome5'</span>;
<span class="hljs-keyword">import</span> ImagePicker <span class="hljs-keyword">from</span> <span class="hljs-string">'react-native-image-crop-picker'</span>;
<span class="hljs-keyword">import</span> _ <span class="hljs-keyword">from</span> <span class="hljs-string">'lodash'</span>;

interface Props &#123;
  <span class="hljs-attr">callBackVideo</span>: any;
  style: any;
&#125;

<span class="hljs-keyword">const</span> Index = <span class="hljs-function">(<span class="hljs-params">props: Props</span>) =></span> &#123;
  <span class="hljs-keyword">const</span> [isShowColumn, setIsShowColumn] = useState(<span class="hljs-literal">true</span>);
  <span class="hljs-keyword">const</span> [videoList, setVideoList] = useState([&#123; <span class="hljs-attr">path</span>: <span class="hljs-string">'first'</span> &#125;]);

  <span class="hljs-keyword">const</span> [videoListShow, setVideoListShow] = useState([]);

  <span class="hljs-keyword">const</span> pickImage = <span class="hljs-function">() =></span> &#123;
    ImagePicker.openPicker(&#123;
      <span class="hljs-attr">multiple</span>: <span class="hljs-literal">true</span>, <span class="hljs-comment">//允许多选，在模拟器中无法多选</span>
      <span class="hljs-attr">mediaType</span>: <span class="hljs-string">'video'</span> <span class="hljs-comment">//仅选择视频</span>
    &#125;).then(<span class="hljs-function">(<span class="hljs-params">res</span>) =></span> &#123;
      <span class="hljs-keyword">let</span> vL = [...videoList, ...res];

      <span class="hljs-comment">//删除元素 https://www.cnblogs.com/yanggb/p/11464821.html</span>
      _.remove(vL, <span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params">n</span>) </span>&#123;
        <span class="hljs-keyword">return</span> n.path == <span class="hljs-string">'first'</span>;
      &#125;);

      <span class="hljs-comment">//不知道为什么只能这样过滤</span>
      <span class="hljs-keyword">const</span> backList = vL.filter(<span class="hljs-function">(<span class="hljs-params">item</span>) =></span> &#123;
        <span class="hljs-keyword">return</span> item.path != <span class="hljs-string">'first'</span>;
      &#125;);
      props.callBackVideo(backList);

      vL.push(&#123; <span class="hljs-attr">path</span>: <span class="hljs-string">'first'</span> &#125;);
      setVideoList(vL <span class="hljs-keyword">as</span> []);
      setIsShowColumn(<span class="hljs-literal">false</span>);
    &#125;);
  &#125;;

  useEffect(<span class="hljs-function">() =></span> &#123;
    <span class="hljs-comment">//处理成方便页面渲染的数据结构</span>
    <span class="hljs-keyword">const</span> tempArr = _.chunk(videoList, <span class="hljs-number">3</span>);
    setVideoListShow(tempArr <span class="hljs-keyword">as</span> []);
  &#125;, [videoList]);

  <span class="hljs-keyword">const</span> pickView = <span class="hljs-function">(<span class="hljs-params">index: number</span>) =></span> &#123;
    <span class="hljs-keyword">return</span> (
      <span class="xml"><span class="hljs-tag"><<span class="hljs-name">TouchableOpacity</span>
        <span class="hljs-attr">style</span>=<span class="hljs-string">&#123;&#123;</span>
          <span class="hljs-attr">borderStyle:</span> '<span class="hljs-attr">dashed</span>',
          <span class="hljs-attr">borderColor:</span> '<span class="hljs-attr">black</span>',
          <span class="hljs-attr">width:</span> <span class="hljs-attr">pxToDp</span>(<span class="hljs-attr">96</span>),
          <span class="hljs-attr">height:</span> <span class="hljs-attr">pxToDp</span>(<span class="hljs-attr">96</span>),
          <span class="hljs-attr">borderWidth:</span> <span class="hljs-attr">1</span>,
          <span class="hljs-attr">justifyContent:</span> '<span class="hljs-attr">center</span>',
          <span class="hljs-attr">alignItems:</span> '<span class="hljs-attr">center</span>',
          <span class="hljs-attr">borderRadius:</span> <span class="hljs-attr">0.1</span>
        &#125;&#125;
        <span class="hljs-attr">key</span>=<span class="hljs-string">&#123;index&#125;</span>
        <span class="hljs-attr">onPress</span>=<span class="hljs-string">&#123;pickImage&#125;</span>
      ></span>
        <span class="hljs-tag"><<span class="hljs-name">Icon</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"plus"</span> <span class="hljs-attr">size</span>=<span class="hljs-string">&#123;30&#125;</span> <span class="hljs-attr">color</span>=<span class="hljs-string">"#E8E8E8"</span> /></span>
      <span class="hljs-tag"></<span class="hljs-name">TouchableOpacity</span>></span></span>
    );
  &#125;;

  <span class="hljs-comment">/**
   * 缩略图展示
   * <span class="hljs-doctag">@returns</span>
   */</span>
  <span class="hljs-keyword">const</span> itemDetailView = <span class="hljs-function">(<span class="hljs-params">path: string, index: number</span>) =></span> &#123;
    <span class="hljs-keyword">return</span> (
      <span class="xml"><span class="hljs-tag"><<span class="hljs-name">View</span> <span class="hljs-attr">key</span>=<span class="hljs-string">&#123;index&#125;</span> <span class="hljs-attr">style</span>=<span class="hljs-string">&#123;&#123;</span> <span class="hljs-attr">alignItems:</span> '<span class="hljs-attr">center</span>', <span class="hljs-attr">marginRight:</span> <span class="hljs-attr">15</span> &#125;&#125;></span>
        <span class="hljs-tag"><<span class="hljs-name">Image</span>
          <span class="hljs-attr">style</span>=<span class="hljs-string">&#123;&#123;</span> <span class="hljs-attr">width:</span> <span class="hljs-attr">pxToDp</span>(<span class="hljs-attr">96</span>), <span class="hljs-attr">height:</span> <span class="hljs-attr">pxToDp</span>(<span class="hljs-attr">96</span>), <span class="hljs-attr">borderRadius:</span> <span class="hljs-attr">10</span> &#125;&#125;
          <span class="hljs-attr">source</span>=<span class="hljs-string">&#123;&#123;</span>
            <span class="hljs-attr">uri:</span> <span class="hljs-attr">path</span>
          &#125;&#125;
        /></span>
        <span class="hljs-tag"><<span class="hljs-name">TouchableOpacity</span>
          <span class="hljs-attr">style</span>=<span class="hljs-string">&#123;&#123;</span> <span class="hljs-attr">width:</span> <span class="hljs-attr">pxToDp</span>(<span class="hljs-attr">20</span>), <span class="hljs-attr">position:</span> '<span class="hljs-attr">absolute</span>', <span class="hljs-attr">top:</span> <span class="hljs-attr">pxToDp</span>(<span class="hljs-attr">-10</span>), <span class="hljs-attr">left:</span> <span class="hljs-attr">pxToDp</span>(<span class="hljs-attr">86</span>) &#125;&#125;
          <span class="hljs-attr">onPress</span>=<span class="hljs-string">&#123;()</span> =></span> &#123;
            let tempList = videoList;
            //删除元素
            _.remove(tempList, function (n) &#123;
              return n.path == path;
            &#125;);
            setVideoList(tempList);
            //处理成方便页面渲染的数据结构
            const tempArr = _.chunk(tempList, 3);
            setVideoListShow(tempArr as []);
          &#125;&#125;
        >
          <span class="hljs-tag"><<span class="hljs-name">Image</span>
            <span class="hljs-attr">style</span>=<span class="hljs-string">&#123;&#123;</span> <span class="hljs-attr">width:</span> <span class="hljs-attr">pxToDp</span>(<span class="hljs-attr">20</span>), <span class="hljs-attr">height:</span> <span class="hljs-attr">pxToDp</span>(<span class="hljs-attr">20</span>) &#125;&#125;
            <span class="hljs-attr">source</span>=<span class="hljs-string">&#123;require(</span>'@/<span class="hljs-attr">res</span>/<span class="hljs-attr">images</span>/<span class="hljs-attr">x.png</span>')&#125;
          /></span>
        <span class="hljs-tag"></<span class="hljs-name">TouchableOpacity</span>></span>
      <span class="hljs-tag"></<span class="hljs-name">View</span>></span></span>
    );
  &#125;;

  interface itemValue &#123;
    <span class="hljs-attr">path</span>: string;
  &#125;
  <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">itemView</span>(<span class="hljs-params">item: [], index: number</span>): <span class="hljs-title">JSX</span>.<span class="hljs-title">Element</span> </span>&#123;
    <span class="hljs-keyword">return</span> (
      <span class="xml"><span class="hljs-tag"><<span class="hljs-name">View</span>
        <span class="hljs-attr">style</span>=<span class="hljs-string">&#123;&#123;</span>
          <span class="hljs-attr">flexDirection:</span> '<span class="hljs-attr">row</span>',
          <span class="hljs-attr">width:</span> '<span class="hljs-attr">100</span>%',
          <span class="hljs-attr">alignItems:</span> '<span class="hljs-attr">center</span>',
          <span class="hljs-attr">marginBottom:</span> <span class="hljs-attr">15</span>
        &#125;&#125;
        <span class="hljs-attr">key</span>=<span class="hljs-string">&#123;index&#125;</span>
      ></span>
        &#123;item.map((itemValue: itemValue, index2: number) => &#123;
          if (itemValue.path == 'first') &#123;
            return pickView(index2);
          &#125; else &#123;
            return itemDetailView(itemValue.path, index2);
          &#125;
        &#125;)&#125;
      <span class="hljs-tag"></<span class="hljs-name">View</span>></span></span>
    );
  &#125;

  <span class="hljs-comment">/**
   * 被选中的视频缩略
   * <span class="hljs-doctag">@returns</span>
   */</span>
  <span class="hljs-keyword">const</span> videoLIstView = <span class="hljs-function">() =></span> &#123;
    <span class="hljs-keyword">return</span> videoListShow.map(<span class="hljs-function">(<span class="hljs-params">item: [], index</span>) =></span> &#123;
      <span class="hljs-keyword">return</span> itemView(item, index);
    &#125;);
  &#125;;

  <span class="hljs-keyword">return</span> <span class="xml"><span class="hljs-tag"><<span class="hljs-name">View</span> <span class="hljs-attr">style</span>=<span class="hljs-string">&#123;[props.style]&#125;</span>></span>&#123;videoLIstView()&#125;<span class="hljs-tag"></<span class="hljs-name">View</span>></span></span>;
&#125;;

Index.defaultProps = &#123;
  <span class="hljs-attr">callBackVideo</span>: <span class="hljs-function">() =></span> &#123;&#125;,
  <span class="hljs-attr">style</span>: &#123;&#125;
&#125;;

<span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span> Index;

<span class="copy-code-btn">复制代码</span></code></pre>
<h1 data-id="heading-4">5 使用演示</h1>
<pre><code class="hljs language-js copyable" lang="js">
  pickVideo = <span class="hljs-function">(<span class="hljs-params">videoList: any</span>) =></span> &#123;
  
    <span class="hljs-built_in">console</span>.log(videoList);
  &#125;;

      <span class="xml"><span class="hljs-tag"><<span class="hljs-name">PickVideo</span>
          <span class="hljs-attr">callBackVideo</span>=<span class="hljs-string">&#123;this.pickVideo&#125;</span>
          <span class="hljs-attr">style</span>=<span class="hljs-string">&#123;&#123;</span> <span class="hljs-attr">marginTop:</span> <span class="hljs-attr">pxToDp</span>(<span class="hljs-attr">20</span>), <span class="hljs-attr">marginLeft:</span> <span class="hljs-attr">pxToDp</span>(<span class="hljs-attr">15</span>), <span class="hljs-attr">marginRight:</span> <span class="hljs-attr">pxToDp</span>(<span class="hljs-attr">15</span>) &#125;&#125;
        /></span></span>

<span class="copy-code-btn">复制代码</span></code></pre></div>  
</div>
            
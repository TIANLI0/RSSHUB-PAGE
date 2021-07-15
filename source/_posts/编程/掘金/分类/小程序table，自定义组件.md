
---
title: '小程序table，自定义组件'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ac5a4e1a0ddf44f5846f407fbe712fc1~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 00:18:28 GMT
thumbnail: 'https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ac5a4e1a0ddf44f5846f407fbe712fc1~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><p>例图：</p>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ac5a4e1a0ddf44f5846f407fbe712fc1~tplv-k3u1fbpfcp-watermark.image" alt="2500256-4e4d13b87bdeb6d0.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p>table做成一个组件，需要的童鞋代码烤过去直接用。</p>
<p>1:table.wxml</p>
<pre><code class="copyable"><view class="table">
  <view class="thead">
    <view wx:for="&#123;&#123;thead&#125;&#125;" wx:key="index">
      <view class="th" style="width:&#123;&#123;item.width?item.width+'rpx':''&#125;&#125;">&#123;&#123;item.title&#125;&#125;</view>
    </view>
  </view>
  <view class="tbody">
    <block wx:for="&#123;&#123;dataSources&#125;&#125;" wx:for-index="indexTr" wx:key="indexTr">
      <view class="tr">
        <view class="td" wx:for="&#123;&#123;thead&#125;&#125;" wx:for-item="itemTh" wx:for-index="indexTh" wx:key="indexTh">
          <view class="td-text" style="width:&#123;&#123;itemTh.width?itemTh.width+'rpx':''&#125;&#125;">
            &#123;&#123;itemTh.key=='index'?(indexTr+1):item[itemTh.key]&#125;&#125;
          </view>
        </view>
      </view>
    </block>
    <block wx:if="&#123;&#123;dataSources.length===0&#125;&#125;">
      <view class="data-no" >
        暂无数据
      </view>
    </block>
  </view>
</view>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>2：table.wxss</p>
<pre><code class="copyable">.thead,.tr&#123;
  display: flex;
  align-items: center;
  text-align: center;
  justify-content: space-between;
&#125;
.thead&#123;
  height: 60rpx;
  background: #F4F4F4;
  border-radius: 4rpx
&#125;

.th,.td&#123;
  font-size: 20rpx;
&#125;
.th,.td,.td-text&#123;
  height: 60rpx;
  line-height: 60rpx;
&#125;
.th&#123;
  background: #F4F4F4;
&#125;
.td&#123;
  color: rgba(0, 0, 0, 0.8);
  border-bottom: 1rpx solid #EEEEEE;
  flex: auto;
&#125;
.td-text&#123;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  word-break: break-all;
&#125;
.data-no&#123;
  text-align: center;
  line-height: 200rpx;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>3:table.json</p>
<pre><code class="copyable">&#123;
  "component":true,
  "usingComponents": &#123;&#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>4:table.js</p>
<pre><code class="copyable">Component(&#123;
  properties:&#123;
    thead:&#123;
      type:Array,
      value:[],
      /*
      格式
       thead:[&#123;
          title:'', //显示表头名字
          key:'', // 对应列表字段
          width:'' //宽度
        &#125;]
      */
    &#125;,
    dataSources:&#123;
      type:Array,
      value:[],
       /*
       请求数据
      */
    &#125;
  &#125;,
  data: &#123;
   
  &#125;,
  methods:&#123;

  &#125;,
&#125;)
<span class="copy-code-btn">复制代码</span></code></pre>
<p>5:组件的引用方法
在父组件的.json中加入</p>
<pre><code class="copyable">"usingComponents": &#123;
    "table":"../components/table/table" //table组件的相对路径，找自己存的文件路径
  &#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>父组件的.wxml中加入</p>
<pre><code class="copyable">      <table thead="&#123;&#123;thead&#125;&#125;" dataSources="&#123;&#123;dataSources&#125;&#125;"></table>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>父组件的.js的data中加入</p>
<pre><code class="copyable">data: &#123;
  thead:[],
 /* 表头数据例如   thead:[&#123;
      title:'序号',
      key:'index',
      width:'66'
    &#125;] */
 dataSources:[], //接口数据
 &#125;
<span class="copy-code-btn">复制代码</span></code></pre></div>  
</div>
            
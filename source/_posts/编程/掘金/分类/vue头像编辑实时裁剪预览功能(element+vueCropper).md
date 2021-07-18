
---
title: 'vue头像编辑实时裁剪预览功能(element+vueCropper)'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/abb38f8ab9604160944e5ecb28e21abe~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Thu, 15 Jul 2021 18:42:57 GMT
thumbnail: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/abb38f8ab9604160944e5ecb28e21abe~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h2 data-id="heading-0">公司其中一个项目的需求，根据UI图实现头像修改功能，点击头像编辑，弹出头像修改框，需要裁剪及实时预览。</h2>
<ul>
<li>话不多说，先来一波效果图：</li>
</ul>
<h3 data-id="heading-1">选择图片前</h3>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/abb38f8ab9604160944e5ecb28e21abe~tplv-k3u1fbpfcp-watermark.image" alt="1.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h3 data-id="heading-2">选择图片后</h3>
<p><img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/018e77643d78493a9917432cf384a2f8~tplv-k3u1fbpfcp-watermark.image" alt="2.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h3 data-id="heading-3">实现代码：</h3>
<pre><code class="hljs language-js copyable" lang="js"><template>
  <span class="xml"><span class="hljs-tag"><<span class="hljs-name">el-dialog</span>
    <span class="hljs-attr">title</span>=<span class="hljs-string">"编辑头像"</span>
    <span class="hljs-attr">:visible.sync</span>=<span class="hljs-string">"dialogVisible"</span>
    <span class="hljs-attr">:show-close</span>=<span class="hljs-string">"false"</span>
    <span class="hljs-attr">:close-on-click-modal</span>=<span class="hljs-string">"false"</span>
    <span class="hljs-attr">:close-on-press-escape</span>=<span class="hljs-string">"false"</span>
    <span class="hljs-attr">width</span>=<span class="hljs-string">"600px"</span>
  ></span>
    <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">style</span>=<span class="hljs-string">"display: flex"</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"avatar"</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"avatar-left"</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">v-show</span>=<span class="hljs-string">"!options.img"</span>></span>
          <span class="hljs-tag"><<span class="hljs-name">el-upload</span>
            <span class="hljs-attr">ref</span>=<span class="hljs-string">"upload"</span>
            <span class="hljs-attr">action</span>=<span class="hljs-string">""</span>
            <span class="hljs-attr">style</span>=<span class="hljs-string">"text-align: center;margin-bottom: 24px"</span>
            <span class="hljs-attr">:on-change</span>=<span class="hljs-string">"uploads"</span>
            <span class="hljs-attr">accept</span>=<span class="hljs-string">"image/png, image/jpeg, image/jpg"</span>
            <span class="hljs-attr">:show-file-list</span>=<span class="hljs-string">"false"</span>
            <span class="hljs-attr">:auto-upload</span>=<span class="hljs-string">"false"</span>></span>
            <span class="hljs-tag"><<span class="hljs-name">el-button</span> <span class="hljs-attr">slot</span>=<span class="hljs-string">"trigger"</span> <span class="hljs-attr">size</span>=<span class="hljs-string">"small"</span> <span class="hljs-attr">type</span>=<span class="hljs-string">"primary"</span> <span class="hljs-attr">ref</span>=<span class="hljs-string">"uploadBtn"</span>></span>选择图片<span class="hljs-tag"></<span class="hljs-name">el-button</span>></span>
          <span class="hljs-tag"></<span class="hljs-name">el-upload</span>></span>
          <span class="hljs-tag"><<span class="hljs-name">div</span>></span>支持jpg、png格式的图片，大小不超过3M<span class="hljs-tag"></<span class="hljs-name">div</span>></span>
        <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">v-show</span>=<span class="hljs-string">"options.img"</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"avatar-left-crop"</span>></span>
          <span class="hljs-tag"><<span class="hljs-name">vueCropper</span>
            <span class="hljs-attr">class</span>=<span class="hljs-string">"crop-box"</span>
            <span class="hljs-attr">ref</span>=<span class="hljs-string">"cropper"</span>
            <span class="hljs-attr">:img</span>=<span class="hljs-string">"options.img"</span>
            <span class="hljs-attr">:autoCrop</span>=<span class="hljs-string">"options.autoCrop"</span>
            <span class="hljs-attr">:fixedBox</span>=<span class="hljs-string">"options.fixedBox"</span>
            <span class="hljs-attr">:canMoveBox</span>=<span class="hljs-string">"options.canMoveBox"</span>
            <span class="hljs-attr">:autoCropWidth</span>=<span class="hljs-string">"options.autoCropWidth"</span>
            <span class="hljs-attr">:autoCropHeight</span>=<span class="hljs-string">"options.autoCropHeight"</span>
            <span class="hljs-attr">:centerBox</span>=<span class="hljs-string">"options.centerBox"</span>
            @<span class="hljs-attr">realTime</span>=<span class="hljs-string">"realTime"</span>></span>
          <span class="hljs-tag"></<span class="hljs-name">vueCropper</span>></span>
          <span class="hljs-tag"><<span class="hljs-name">p</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"avatar-left-p"</span>></span>
            鼠标滚轮缩放控制图片显示大小，鼠标拖拽调整显示位置<span class="hljs-tag"></<span class="hljs-name">p</span>></span>
        <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
      <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
      <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"avatar-right"</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"avatar-right-div"</span> <span class="hljs-attr">v-for</span>=<span class="hljs-string">"item in previewsDiv"</span> <span class="hljs-attr">:style</span>=<span class="hljs-string">"item.style"</span>></span>
          <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">v-show</span>=<span class="hljs-string">"options.img"</span> <span class="hljs-attr">:class</span>=<span class="hljs-string">"previews.div"</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"avatar-right-previews"</span> <span class="hljs-attr">:style</span>=<span class="hljs-string">"item.zoomStyle"</span>></span>
            <span class="hljs-tag"><<span class="hljs-name">img</span> <span class="hljs-attr">:src</span>=<span class="hljs-string">"previews.url"</span> <span class="hljs-attr">:style</span>=<span class="hljs-string">"previews.img"</span>></span>
          <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
        <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
        <span class="hljs-tag"><<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"avatar-right-text"</span>></span>
          <span class="hljs-tag"><<span class="hljs-name">el-button</span> <span class="hljs-attr">v-if</span>=<span class="hljs-string">"options.img"</span> <span class="hljs-attr">type</span>=<span class="hljs-string">"text"</span> @<span class="hljs-attr">click</span>=<span class="hljs-string">"uploadPreviews"</span>></span>重新上传<span class="hljs-tag"></<span class="hljs-name">el-button</span>></span>
          <span class="hljs-tag"><<span class="hljs-name">span</span> <span class="hljs-attr">v-else</span>></span>预览<span class="hljs-tag"></<span class="hljs-name">span</span>></span>
        <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
      <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
    <span class="hljs-tag"></<span class="hljs-name">div</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">span</span> <span class="hljs-attr">slot</span>=<span class="hljs-string">"footer"</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"dialog-footer"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">el-button</span> @<span class="hljs-attr">click</span>=<span class="hljs-string">"closeDialog"</span>></span>取 消<span class="hljs-tag"></<span class="hljs-name">el-button</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">el-button</span> <span class="hljs-attr">type</span>=<span class="hljs-string">"primary"</span> @<span class="hljs-attr">click</span>=<span class="hljs-string">"getCrop"</span>></span>确 定<span class="hljs-tag"></<span class="hljs-name">el-button</span>></span>
  <span class="hljs-tag"></<span class="hljs-name">span</span>></span>
  <span class="hljs-tag"></<span class="hljs-name">el-dialog</span>></span>
<span class="hljs-tag"></<span class="hljs-name">template</span>></span></span>

<span class="xml"><span class="hljs-tag"><<span class="hljs-name">script</span>></span><span class="javascript">
  <span class="hljs-keyword">export</span> <span class="hljs-keyword">default</span> &#123;
    <span class="hljs-attr">name</span>: <span class="hljs-string">"avatarEdit"</span>,
    <span class="hljs-attr">props</span>: &#123;
      <span class="hljs-attr">dialogVisible</span>: &#123;
        <span class="hljs-attr">type</span>: <span class="hljs-built_in">Boolean</span>,
        <span class="hljs-attr">default</span>: <span class="hljs-literal">false</span>
      &#125;
    &#125;,
    <span class="hljs-function"><span class="hljs-title">data</span>(<span class="hljs-params"></span>)</span> &#123;
      <span class="hljs-keyword">return</span> &#123;
        <span class="hljs-comment">//vueCropper组件 裁剪配置信息</span>
        <span class="hljs-attr">options</span>: &#123;
          <span class="hljs-attr">img</span>: <span class="hljs-string">''</span>,  <span class="hljs-comment">//原图文件</span>
          <span class="hljs-attr">autoCrop</span>: <span class="hljs-literal">true</span>,  <span class="hljs-comment">//默认生成截图框</span>
          <span class="hljs-attr">fixedBox</span>: <span class="hljs-literal">true</span>,  <span class="hljs-comment">//固定截图框大小</span>
          <span class="hljs-attr">canMoveBox</span>: <span class="hljs-literal">false</span>,    <span class="hljs-comment">//截图框不能拖动</span>
          <span class="hljs-attr">autoCropWidth</span>: <span class="hljs-number">200</span>,  <span class="hljs-comment">//截图框宽度</span>
          <span class="hljs-attr">autoCropHeight</span>: <span class="hljs-number">200</span>, <span class="hljs-comment">//截图框高度</span>
          <span class="hljs-attr">centerBox</span>: <span class="hljs-literal">true</span>,    <span class="hljs-comment">//截图框被限制在图片里面</span>
        &#125;,
        <span class="hljs-comment">//实时预览图数据</span>
        <span class="hljs-attr">previews</span>: &#123;&#125;,
        <span class="hljs-comment">//实时预览图样式</span>
        <span class="hljs-attr">previewsDiv</span>: [
          <span class="hljs-comment">//108px 预览样式</span>
          &#123;
            <span class="hljs-attr">style</span>: &#123;
              <span class="hljs-attr">width</span>: <span class="hljs-string">'108px'</span>,
              <span class="hljs-attr">height</span>: <span class="hljs-string">'108px'</span>,
              <span class="hljs-attr">margin</span>: <span class="hljs-string">'0 auto'</span>
            &#125;,
            <span class="hljs-attr">zoomStyle</span>: &#123;
              <span class="hljs-attr">zoom</span>: <span class="hljs-number">0.54</span>
            &#125;
          &#125;,
          <span class="hljs-comment">//68px 预览样式</span>
          &#123;
            <span class="hljs-attr">style</span>: &#123;
              <span class="hljs-attr">width</span>: <span class="hljs-string">'68px'</span>,
              <span class="hljs-attr">height</span>: <span class="hljs-string">'68px'</span>,
              <span class="hljs-attr">margin</span>: <span class="hljs-string">'27px auto'</span>
            &#125;,
            <span class="hljs-attr">zoomStyle</span>: &#123;
              <span class="hljs-attr">zoom</span>: <span class="hljs-number">0.34</span>
            &#125;
          &#125;,
          <span class="hljs-comment">//48px 预览样式</span>
          &#123;
            <span class="hljs-attr">style</span>: &#123;
              <span class="hljs-attr">width</span>: <span class="hljs-string">'48px'</span>,
              <span class="hljs-attr">height</span>: <span class="hljs-string">'48px'</span>,
              <span class="hljs-attr">margin</span>: <span class="hljs-string">'0 auto'</span>
            &#125;,
            <span class="hljs-attr">zoomStyle</span>: &#123;
              <span class="hljs-attr">zoom</span>: <span class="hljs-number">0.24</span>
            &#125;
          &#125;
        ],
      &#125;
    &#125;,

    <span class="hljs-attr">methods</span>: &#123;
      <span class="hljs-comment">//读取原图</span>
      <span class="hljs-function"><span class="hljs-title">uploads</span>(<span class="hljs-params">file</span>)</span> &#123;
        <span class="hljs-keyword">const</span> isIMAGE = file.raw.type === <span class="hljs-string">'image/jpeg'</span> || file.raw.type === <span class="hljs-string">'image/png'</span>;
        <span class="hljs-keyword">const</span> isLt3M = file.raw.size / <span class="hljs-number">1024</span> / <span class="hljs-number">1024</span> < <span class="hljs-number">3</span>;
        <span class="hljs-keyword">if</span> (!isIMAGE) &#123;
          <span class="hljs-built_in">this</span>.$message(&#123;
            <span class="hljs-attr">showClose</span>: <span class="hljs-literal">true</span>,
            <span class="hljs-attr">message</span>: <span class="hljs-string">'请选择 jpg、png 格式的图片！'</span>,
            <span class="hljs-attr">type</span>: <span class="hljs-string">'error'</span>,  <span class="hljs-comment">//提示类型</span>
          &#125;);
          <span class="hljs-keyword">return</span> <span class="hljs-literal">false</span>;
        &#125;
        <span class="hljs-keyword">if</span> (!isLt3M) &#123;
          <span class="hljs-built_in">this</span>.$message(&#123;
            <span class="hljs-attr">showClose</span>: <span class="hljs-literal">true</span>,
            <span class="hljs-attr">message</span>: <span class="hljs-string">'上传图片大小不能超过 3MB'</span>,
            <span class="hljs-attr">type</span>: <span class="hljs-string">'error'</span>,  <span class="hljs-comment">//提示类型</span>
          &#125;);
          <span class="hljs-keyword">return</span> <span class="hljs-literal">false</span>;
        &#125;
        <span class="hljs-keyword">let</span> reader = <span class="hljs-keyword">new</span> FileReader();
        reader.readAsDataURL(file.raw);
        reader.onload = <span class="hljs-function"><span class="hljs-params">e</span> =></span> &#123;
          <span class="hljs-built_in">this</span>.options.img = e.target.result <span class="hljs-comment">//base64</span>
        &#125;
      &#125;,
      <span class="hljs-comment">//实时预览数据</span>
      <span class="hljs-function"><span class="hljs-title">realTime</span>(<span class="hljs-params">data</span>)</span> &#123;
        <span class="hljs-built_in">this</span>.previews = data
      &#125;,
      <span class="hljs-comment">//重新上传</span>
      <span class="hljs-function"><span class="hljs-title">uploadPreviews</span>(<span class="hljs-params"></span>)</span> &#123;
        <span class="hljs-built_in">this</span>.$refs.uploadBtn.$el.click()
      &#125;,
      <span class="hljs-comment">//获取截图信息</span>
      <span class="hljs-function"><span class="hljs-title">getCrop</span>(<span class="hljs-params"></span>)</span> &#123;
        <span class="hljs-comment">// 获取截图的 base64 数据</span>
        <span class="hljs-built_in">this</span>.$refs.cropper.getCropData(<span class="hljs-function">(<span class="hljs-params">data</span>) =></span> &#123;
          <span class="hljs-built_in">console</span>.log(data)
        &#125;)
        <span class="hljs-comment">// 获取截图的 blob 数据</span>
        <span class="hljs-built_in">this</span>.$refs.cropper.getCropBlob(<span class="hljs-function">(<span class="hljs-params">data</span>) =></span> &#123;
          <span class="hljs-built_in">console</span>.log(data)
        &#125;)
      &#125;,
      <span class="hljs-comment">//关闭弹框</span>
      <span class="hljs-function"><span class="hljs-title">closeDialog</span>(<span class="hljs-params"></span>)</span> &#123;
        <span class="hljs-comment">//调用父组件关闭弹框方法 closeAvatarEdits()</span>
        <span class="hljs-built_in">this</span>.$parent.closeAvatarEdits()
        <span class="hljs-comment">//重置 data 数据。(Object.assign是对象深复制  this.$data是组件内的数据对象 this.$options.data()是原始的数据)</span>
        <span class="hljs-built_in">Object</span>.assign(<span class="hljs-built_in">this</span>.$data, <span class="hljs-built_in">this</span>.$options.data())
      &#125;,
    &#125;
  &#125;
</span><span class="hljs-tag"></<span class="hljs-name">script</span>></span></span>

<span class="xml"><span class="hljs-tag"><<span class="hljs-name">style</span> <span class="hljs-attr">lang</span>=<span class="hljs-string">"scss"</span> <span class="hljs-attr">scoped</span>></span><span class="css">

  /deep/ <span class="hljs-selector-class">.el-dialog__header</span> &#123;
    <span class="hljs-attribute">padding</span>: <span class="hljs-number">24px</span> <span class="hljs-number">0</span> <span class="hljs-number">11px</span> <span class="hljs-number">28px</span>;
  &#125;

  /deep/ <span class="hljs-selector-class">.el-dialog__title</span> &#123;
    <span class="hljs-attribute">color</span>: <span class="hljs-number">#333333</span>;
  &#125;

  /deep/ <span class="hljs-selector-class">.el-dialog__body</span> &#123;
    <span class="hljs-attribute">padding</span>: <span class="hljs-number">0</span> <span class="hljs-number">28px</span>;
  &#125;

  /deep/ <span class="hljs-selector-class">.el-dialog__footer</span> &#123;
    <span class="hljs-attribute">padding</span>: <span class="hljs-number">20px</span> <span class="hljs-number">28px</span>;

    <span class="hljs-selector-class">.el-button</span> &#123;
      <span class="hljs-attribute">width</span>: <span class="hljs-number">145px</span>;
    &#125;
  &#125;

  <span class="hljs-selector-class">.avatar</span> &#123;
    <span class="hljs-attribute">display</span>: flex;

    <span class="hljs-selector-class">.avatar-left</span> &#123;
      <span class="hljs-attribute">display</span>: flex;
      <span class="hljs-attribute">justify-content</span>: center;
      <span class="hljs-attribute">align-items</span>: center;
      <span class="hljs-attribute">width</span>: <span class="hljs-number">400px</span>;
      <span class="hljs-attribute">height</span>: <span class="hljs-number">400px</span>;
      <span class="hljs-attribute">background-color</span>: <span class="hljs-number">#F0F2F5</span>;
      <span class="hljs-attribute">margin-right</span>: <span class="hljs-number">10px</span>;
      <span class="hljs-attribute">border-radius</span>: <span class="hljs-number">4px</span>;

      <span class="hljs-selector-class">.avatar-left-crop</span> &#123;
        <span class="hljs-attribute">width</span>: <span class="hljs-number">400px</span>;
        <span class="hljs-attribute">height</span>: <span class="hljs-number">400px</span>;
        <span class="hljs-attribute">position</span>: relative;

        <span class="hljs-selector-class">.crop-box</span> &#123;
          <span class="hljs-attribute">width</span>: <span class="hljs-number">100%</span>;
          <span class="hljs-attribute">height</span>: <span class="hljs-number">100%</span>;
          <span class="hljs-attribute">border-radius</span>: <span class="hljs-number">4px</span>;
          <span class="hljs-attribute">overflow</span>: hidden
        &#125;

      &#125;

      <span class="hljs-selector-class">.avatar-left-p</span> &#123;
        <span class="hljs-attribute">text-align</span>: center;
        <span class="hljs-attribute">width</span>: <span class="hljs-number">100%</span>;
        <span class="hljs-attribute">position</span>: absolute;
        <span class="hljs-attribute">bottom</span>: <span class="hljs-number">20px</span>;
        <span class="hljs-attribute">color</span>: <span class="hljs-number">#ffffff</span>;
        <span class="hljs-attribute">font-size</span>: <span class="hljs-number">14px</span>;
      &#125;
    &#125;

    <span class="hljs-selector-class">.avatar-right</span> &#123;
      <span class="hljs-attribute">width</span>: <span class="hljs-number">150px</span>;
      <span class="hljs-attribute">height</span>: <span class="hljs-number">400px</span>;
      <span class="hljs-attribute">background-color</span>: <span class="hljs-number">#F0F2F5</span>;
      <span class="hljs-attribute">border-radius</span>: <span class="hljs-number">4px</span>;
      <span class="hljs-attribute">padding</span>: <span class="hljs-number">16px</span> <span class="hljs-number">0</span>;
      <span class="hljs-attribute">box-sizing</span>: border-box;

      <span class="hljs-selector-class">.avatar-right-div</span> &#123;
        <span class="hljs-attribute">border</span>: <span class="hljs-number">3px</span> solid <span class="hljs-number">#ffffff</span>;
        <span class="hljs-attribute">border-radius</span>: <span class="hljs-number">50%</span>;
      &#125;

      <span class="hljs-selector-class">.avatar-right-previews</span> &#123;
        <span class="hljs-attribute">width</span>: <span class="hljs-number">200px</span>;
        <span class="hljs-attribute">height</span>: <span class="hljs-number">200px</span>;
        <span class="hljs-attribute">overflow</span>: hidden;
        <span class="hljs-attribute">border-radius</span>: <span class="hljs-number">50%</span>;
      &#125;

      <span class="hljs-selector-class">.avatar-right-text</span> &#123;
        <span class="hljs-attribute">text-align</span>: center;
        <span class="hljs-attribute">margin-top</span>: <span class="hljs-number">50px</span>;
        <span class="hljs-attribute">font-size</span>: <span class="hljs-number">14px</span>;

        /deep/ <span class="hljs-selector-class">.el-button</span> &#123;
          <span class="hljs-attribute">padding</span>: <span class="hljs-number">0</span>;
        &#125;

        <span class="hljs-selector-tag">span</span> &#123;
          <span class="hljs-attribute">color</span>: <span class="hljs-number">#666666</span>;
        &#125;
      &#125;
    &#125;
  &#125;

</span><span class="hljs-tag"></<span class="hljs-name">style</span>></span></span>

<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>UI库 <strong>element</strong></li>
<li>图片裁剪插件  <strong>vueCropper</strong></li>
<li>图片上传element ----<strong>upload</strong></li>
</ul>
<h3 data-id="heading-4"><strong><a href="https://link.juejin.cn/?target=https%3A%2F%2Fblog.csdn.net%2FXHL1314mmq" target="_blank" rel="nofollow noopener noreferrer" title="https://blog.csdn.net/XHL1314mmq" ref="nofollow noopener noreferrer">我的CSDN → 传送门</a></strong></h3>
<blockquote>
<p>每篇文章都是干货满满,绝无广告和废话！欢迎点赞 + 关注 + 收藏</p>
</blockquote></div>  
</div>
            

---
title: '表单FormData的使用'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=56'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 22:23:34 GMT
thumbnail: 'https://picsum.photos/400/300?random=56'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;color:#595959;font-size:15px;font-family:-apple-system,system-ui,BlinkMacSystemFont,Helvetica Neue,PingFang SC,Hiragino Sans GB,Microsoft YaHei,Arial,sans-serif;background-image:linear-gradient(90deg,rgba(60,10,30,.04) 3%,transparent 0),linear-gradient(1turn,rgba(60,10,30,.04) 3%,transparent 0);background-size:20px 20px;background-position:50%&#125;.markdown-body p&#123;color:#595959;font-size:15px;line-height:2;font-weight:400&#125;.markdown-body p+p&#123;margin-top:16px&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;padding:30px 0;margin:0;color:#135ce0&#125;.markdown-body h1&#123;position:relative;text-align:center;font-size:22px;margin:50px 0&#125;.markdown-body h1:before&#123;position:absolute;content:"";top:-10px;left:50%;width:32px;height:32px;transform:translateX(-50%);background-size:100% 100%;opacity:.36;background-repeat:no-repeat;background:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAABGdBTUEAALGPC/xhBQAAACBjSFJNAAB6JgAAgIQAAPoAAACA6AAAdTAAAOpgAAA6mAAAF3CculE8AAABfVBMVEX///8Ad/8AgP8AgP8AgP8Aff8AgP8Af/8AgP8AVf8Af/8Af/8AgP8AgP8Af/8Afv8AAP8Afv8Afv8Aef8AgP8AdP8Afv8AgP8AgP8Acf8Ae/8AgP8Af/8AgP8Af/8Af/8AfP8Afv8AgP8Af/8Af/8Afv8Afv8AgP8Afv8AgP8Af/8Af/8AgP8AgP8Afv8AgP8Af/8AgP8AgP8AgP8Ae/8Afv8Af/8AgP8Af/8AgP8Af/8Af/8Aff8Af/8Abf8AgP8Af/8AgP8Af/8Af/8Afv8AgP8AgP8Afv8Afv8AgP8Af/8Aff8AgP8Afv8AgP8Aff8AgP8AfP8AgP8Ae/8AgP8Af/8AgP8AgP8AgP8Afv8AgP8AgP8AgP8Afv8AgP8AgP8AgP8AgP8AgP8Af/8AgP8Af/8Af/8Aev8Af/8AgP8Aff8Afv8AgP8AgP8AgP8Af/8AgP8Af/8Af/8AgP8Afv8AgP8AgP8AgP8AgP8Af/8AeP8Af/8Af/8Af//////rzEHnAAAAfXRSTlMAD7CCAivatxIDx5EMrP19AXdLEwgLR+6iCR/M0yLRzyFF7JupSXn8cw6v60Q0QeqzKtgeG237HMne850/6Qeq7QaZ+WdydHtj+OM3qENCMRYl1B3K2U7wnlWE/mhlirjkODa9FN/BF7/iNV/2kASNZpX1Wlf03C4stRGxgUPclqoAAAABYktHRACIBR1IAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAB3RJTUUH4gEaBzgZ4yeM3AAAAT9JREFUOMvNUldbwkAQvCAqsSBoABE7asSOBRUVVBQNNuy9996789+9cMFAMHnVebmdm+/bmdtbQv4dOFOW2UjPzgFyLfo6nweKfIMOBYWwFtmMPGz2Yj2pJI0JDq3udJW6VVbmKa9I192VQFV1ktXUAl5NB0cd4KpnORqsEO2ZIRpF9gJfE9Dckqq0KuZt7UAH5+8EPF3spjsRpCeQNO/tA/qDwIDA+OCQbBoKA8NOdjMySgcZGVM6jwcgRuUiSs0nlPFNSrEpJfU0jTLD6llqbvKxei7OzvkFNQohi0vAsj81+MoqsCaoPOQFgus/1LyxichW+hS2JWCHZ7VlF9jb187pIAYcHiViHAMnp5mTjJ8B5xeEXF4B1ze/fTh/C0h398DDI9HB07O8ci+vRBdvdGnfP4gBuM8vw7X/G3wDmFhFZEdxzjMAAAAldEVYdGRhdGU6Y3JlYXRlADIwMTgtMDEtMjZUMDc6NTY6MjUrMDE6MDA67pVWAAAAJXRFWHRkYXRlOm1vZGlmeQAyMDE4LTAxLTI2VDA3OjU2OjI1KzAxOjAwS7Mt6gAAABl0RVh0U29mdHdhcmUAd3d3Lmlua3NjYXBlLm9yZ5vuPBoAAAAWdEVYdFRpdGxlAGp1ZWppbl9sb2dvIGNvcHlxapmKAAAAV3pUWHRSYXcgcHJvZmlsZSB0eXBlIGlwdGMAAHic4/IMCHFWKCjKT8vMSeVSAAMjCy5jCxMjE0uTFAMTIESANMNkAyOzVCDL2NTIxMzEHMQHy4BIoEouAOoXEXTyQjWVAAAAAElFTkSuQmCC)&#125;.markdown-body h2&#123;position:relative;font-size:20px;border-left:4px solid;padding:0 0 0 10px;margin:30px 0&#125;.markdown-body h3&#123;font-size:16px&#125;.markdown-body ul&#123;list-style:disc outside;margin-left:2em;margin-top:1em&#125;.markdown-body li&#123;line-height:2;color:#595959&#125;.markdown-body img.loaded&#123;margin:0 auto;display:block&#125;.markdown-body blockquote&#123;background:#fff9f9;margin:2em 0;padding:2px 20px;border-left:4px solid #b2aec5&#125;.markdown-body blockquote p&#123;color:#666;line-height:2&#125;.markdown-body a&#123;color:#036aca;border-bottom:1px solid rgba(3,106,202,.8);font-weight:400;text-decoration:none&#125;.markdown-body em strong,.markdown-body strong&#123;color:#036aca&#125;.markdown-body hr&#123;border-top:1px solid #135ce0&#125;.markdown-body pre&#123;overflow:auto&#125;.markdown-body code,.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body table&#123;border-collapse:collapse;margin:1rem 0;overflow-x:auto&#125;.markdown-body table td,.markdown-body table th&#123;border:1px solid #dfe2e5;padding:.6em 1em&#125;.markdown-body table tr&#123;border-top:1px solid #dfe2e5&#125;.markdown-body table tr:nth-child(2n)&#123;background-color:#f6f8fa&#125;</style><p>「本文已参与好文召集令活动，点击查看：<a href="https://juejin.cn/post/6978685539985653767" target="_blank" title="https://juejin.cn/post/6978685539985653767">后端、大前端双赛道投稿，2万元奖池等你挑战！</a>」</p>
<h3 data-id="heading-0">一、创建一个formData对象实例的方式</h3>
<h4 data-id="heading-1">1、创建一个空对象</h4>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">var</span> formData = <span class="hljs-keyword">new</span> FormData();<span class="hljs-comment">//通过append方法添加数据</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-2">2、使用已有表单来初始化对象</h4>
<pre><code class="hljs language-html copyable" lang="html">表单示例
<span class="hljs-tag"><<span class="hljs-name">form</span> <span class="hljs-attr">id</span>=<span class="hljs-string">"myForm"</span> <span class="hljs-attr">action</span>=<span class="hljs-string">""</span> <span class="hljs-attr">method</span>=<span class="hljs-string">"post"</span>></span>
    <span class="hljs-tag"><<span class="hljs-name">input</span> <span class="hljs-attr">type</span>=<span class="hljs-string">"text"</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"name"</span>></span>名字
    <span class="hljs-tag"><<span class="hljs-name">input</span> <span class="hljs-attr">type</span>=<span class="hljs-string">"password"</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"psw"</span>></span>密码
    <span class="hljs-tag"><<span class="hljs-name">input</span> <span class="hljs-attr">type</span>=<span class="hljs-string">"submit"</span> <span class="hljs-attr">value</span>=<span class="hljs-string">"提交"</span>></span>
<span class="hljs-tag"></<span class="hljs-name">form</span>></span>
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>方法示例</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-comment">// 获取页面已有的一个form表单</span>
<span class="hljs-keyword">var</span> form = <span class="hljs-built_in">document</span>.getElementById(<span class="hljs-string">"myForm"</span>);
<span class="hljs-comment">// 用表单来初始化</span>
<span class="hljs-keyword">var</span> formData = <span class="hljs-keyword">new</span> FormData(form);
<span class="hljs-comment">// 我们可以根据name来访问表单中的字段</span>
<span class="hljs-keyword">var</span> name = formData.get(<span class="hljs-string">"name"</span>); <span class="hljs-comment">// 获取名字</span>
<span class="hljs-keyword">var</span> psw = formData.get(<span class="hljs-string">"psw"</span>); <span class="hljs-comment">// 获取密码</span>
<span class="hljs-comment">// 当然也可以在此基础上，添加其他数据</span>
formData.append(<span class="hljs-string">"token"</span>,<span class="hljs-string">"kshdfiwi3rh"</span>);
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-3">二、 操作方法</h3>
<p>formData里面存储的数据是以健值对的形式存在的，key是唯一的，一个key可能对应多个value。
如果是使用表单初始化，每一个表单字段对应一条数据，它们的HTML name属性即为key值，它们value属性对应value值。</p>
<h4 data-id="heading-4">1.获取值</h4>
<ul>
<li>通过get(key)/getAll(key)来获取对应的value</li>
</ul>
<p>formData.get("name"); // 获取key为name的第一个值
formData.get("name"); // 返回一个数组，获取key为name的所有值</p>
<h4 data-id="heading-5">2 添加数据</h4>
<ul>
<li>通过append(key, value)来添加数据，如果指定的key不存在则会新增一条数据，如果key存在，则添加到数据的末尾</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js">formData.append(<span class="hljs-string">"k1"</span>, <span class="hljs-string">"v1"</span>);
formData.append(<span class="hljs-string">"k1"</span>, <span class="hljs-string">"v2"</span>);
formData.append(<span class="hljs-string">"k1"</span>, <span class="hljs-string">"v3"</span>);
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>获取值时方式及结果如下</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js">formData.get(<span class="hljs-string">"k1"</span>); <span class="hljs-comment">// "v1"</span>
formData.getAll(<span class="hljs-string">"k1"</span>); <span class="hljs-comment">// ["v1","v2","v3"]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-6">3.设置修改数据</h4>
<ul>
<li>set(key, value)来设置修改数据，如果指定的key不存在则会新增一条，如果存在，则会修改对应的value值</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js">formData.append(<span class="hljs-string">"k1"</span>, <span class="hljs-string">"v1"</span>);
formData.set(<span class="hljs-string">"k1"</span>, <span class="hljs-string">"1"</span>);
formData.getAll(<span class="hljs-string">"k1"</span>); <span class="hljs-comment">// ["1"]</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-7">4.判断是否存在对应数据</h4>
<ul>
<li>has(key)来判断是否对应的key值</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js">formData.append(<span class="hljs-string">"k1"</span>, <span class="hljs-string">"v1"</span>);
formData.append(<span class="hljs-string">"k2"</span>,<span class="hljs-literal">null</span>);

formData.has(<span class="hljs-string">"k1"</span>); <span class="hljs-comment">// true</span>
formData.has(<span class="hljs-string">"k2"</span>); <span class="hljs-comment">// true</span>
formData.has(<span class="hljs-string">"k3"</span>); <span class="hljs-comment">// false</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-8">5.删除数据</h4>
<ul>
<li>delete(key)删除数据</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js">formData.append(<span class="hljs-string">"k1"</span>, <span class="hljs-string">"v1"</span>);
formData.append(<span class="hljs-string">"k1"</span>, <span class="hljs-string">"v2"</span>);
formData.append(<span class="hljs-string">"k1"</span>, <span class="hljs-string">"v1"</span>);
formData.delete(<span class="hljs-string">"k1"</span>);

formData.getAll(<span class="hljs-string">"k1"</span>); <span class="hljs-comment">// []</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-9">三、JQuery实例</h3>
<p>添加数据方式见上二</p>
<ul>
<li>processData: false, contentType: false,多用来处理异步上传二进制文件。</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"> $.ajax(&#123;
    <span class="hljs-attr">url</span>: <span class="hljs-string">'xxx'</span>,
    <span class="hljs-attr">type</span>: <span class="hljs-string">'POST'</span>,
    <span class="hljs-attr">data</span>: formData,                    <span class="hljs-comment">// 上传formdata封装的数据</span>
    <span class="hljs-attr">dataType</span>: <span class="hljs-string">'JSON'</span>,
    <span class="hljs-attr">cache</span>: <span class="hljs-literal">false</span>,                      <span class="hljs-comment">// 不缓存</span>
    <span class="hljs-attr">processData</span>: <span class="hljs-literal">false</span>,                <span class="hljs-comment">// jQuery不要去处理发送的数据</span>
    <span class="hljs-attr">contentType</span>: <span class="hljs-literal">false</span>,                <span class="hljs-comment">// jQuery不要去设置Content-Type请求头</span>
    <span class="hljs-attr">success</span>:<span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params">data</span>) </span>&#123;           <span class="hljs-comment">//成功回调</span>
        <span class="hljs-built_in">console</span>.log(data);
    &#125;
&#125;);
<span class="copy-code-btn">复制代码</span></code></pre>
<p>附：</p>
<blockquote>
<p>将以base64的图片url数据转换为Blob文件格式
@param urlData 用url方式表示的base64图片</p>
</blockquote>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">convertBase64UrlToBlob</span>(<span class="hljs-params">urlData</span>) </span>&#123;
    <span class="hljs-keyword">var</span> bytes = <span class="hljs-built_in">window</span>.atob(urlData.split(<span class="hljs-string">','</span>)[<span class="hljs-number">1</span>]); <span class="hljs-comment">//去掉url的头，并转换为byte</span>
    <span class="hljs-comment">//处理异常,将ascii码小于0的转换为大于0</span>
    <span class="hljs-keyword">var</span> ab = <span class="hljs-keyword">new</span> <span class="hljs-built_in">ArrayBuffer</span>(bytes.length);
    <span class="hljs-keyword">var</span> ia = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Uint8Array</span>(ab);
    <span class="hljs-keyword">for</span>(<span class="hljs-keyword">var</span> i = <span class="hljs-number">0</span>; i < bytes.length; i++) &#123;
        ia[i] = bytes.charCodeAt(i);
    &#125;
    <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> Blob([ab], &#123;
        <span class="hljs-attr">type</span>: <span class="hljs-string">'image/png'</span>
    &#125;);
&#125;
<span class="copy-code-btn">复制代码</span></code></pre></div>  
</div>
            

---
title: 'TypeScript学习笔记——函数类型'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=654'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 19:34:36 GMT
thumbnail: 'https://picsum.photos/400/300?random=654'
---

<div>   
<div class="markdown-body"><style>@charset "UTF-8";.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:14px;overflow-x:hidden;color:#353535&#125;.markdown-body h1&#123;padding-bottom:4px;font-size:30px&#125;.markdown-body h1,.markdown-body h2&#123;margin-top:36px;margin-bottom:10px;line-height:1.5;color:#005bb7&#125;.markdown-body h2&#123;position:relative;padding-left:16px;padding-right:10px;padding-bottom:10px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h2:before&#123;content:"「";position:absolute;top:-6px;left:-10px&#125;.markdown-body h2:after&#123;content:"」";position:absolute;top:6px;right:auto&#125;.markdown-body h3&#123;position:relative;padding-bottom:0;margin-top:30px;margin-bottom:10px;font-size:20px;line-height:1.5;color:#005bb7;padding-left:6px&#125;.markdown-body h3:before&#123;content:"»";padding-right:6px;color:#2196f3&#125;.markdown-body h4&#123;margin-top:24px;font-size:16px&#125;.markdown-body h4,.markdown-body h5&#123;padding-bottom:0;margin-bottom:10px;line-height:1.5;color:#005bb7;padding-left:6px&#125;.markdown-body h5&#123;margin-top:18px;font-size:14px&#125;.markdown-body h6&#123;padding-bottom:0;margin-top:12px;margin-bottom:10px;font-size:12px;line-height:1.5;color:#005bb7;padding-left:6px&#125;.markdown-body p&#123;line-height:inherit;margin-top:16px;margin-bottom:16px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;position:relative;width:98%;height:1px;margin-top:32px;margin-bottom:32px;background-image:linear-gradient(90deg,#007fff,rgba(255,0,0,.3),hsla(0,0%,100%,.1),rgba(255,0,0,.3),#007fff);border-width:0;overflow:visible&#125;.markdown-body hr:after&#123;content:"";position:absolute;margin:auto;left:0;right:0;bottom:0;top:0;display:inline-block;width:60px;height:20px;background:#fff;background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACgAAAAgCAYAAABgrToAAAADoklEQVRYR82XTYgcRRTHf2933Q1RjAa9eFO8JHoJ8RQVBQ2iBwXBET0YEUTXNVmNQtTpmeqaWV0XNRq/o4KoECSCEPSg4CF+BYUkIIiCoCJCPIhC/Ihh2Z0nVV27VnZnenumW9i6ddV7//frV69fVQurfMgq56NawFTPAU6QyomqXrw6wIZeyhCPebA5buNR+akKyGoAjd6BshthnYdSjqNcRVuOlIUsD2j0SuA94IwuMHdh5ZUykOUBXfSGbmKI54EtAeYIHSZoy5dl4JxvNYBOKdW1KE8BQ8AkVk6WhasWsAiN0TX9gveXQaPP+Aytpc4u+bMI06JNohsYYYYOR2lJWtS3OKDRfcAtQfgDoI6Vo4UCGb0OmAEuDvZvYmVbEd/igC3dzDz7gQu8sPA9kJDK27mBmjqBeLjTg90PDFOjWawFFQd06kZHEfaj3LAIpTRpSXsZ5E06zEYP9sDimnAApYaV2SLZG/wjMeqAkijwW4xQJ5Gf/ZzRC8OW3hiBTGGlURRswW55Bh/Ssxljrwew8l1PQaM14GngvGDzBUKdDsMeTtgU5o8B92PFlUf3YXUrHa7Fys6lBqcCGnX15YQ2A18FyPd7Crd1A3M8C1wdbH4DD3hWeP6IEXbQkG97ajR1HPFnuPP5jFFq1OWX7hl8WM9l1AO648uNfwLk7tytMeogty+xeQ4rO3r6bdcx1nuwOGsHmaXGtPzae4uzGnLH1kQkvpdZGrHjssBZJrL+pqS05KWc8tgITAPXRzYvYOXe/C2OV43eDcRBDtIhoS2f9wzc0Cv8Wls+zoFzUC5zF0U241h5uZtPfptp6OUM8wbK+cH5GEpCS17P3fJei0Z3+npTxryJ8CPzbKMtn/ZyWbkPGl0PuFPkmkjkcb4h4R2ZLwRq1H0ALmvjkf2HwK1Y+T1PY2XABe/sHJ6MxN5lnoSpnC/UGbsTaI5phK2R7x6s3Ffk5YoDOrWm3onwJHBmEP86bPmBrsGaenNoIdnxCH+gPEhLXi0Cl1VBvyPVLSh7gEuC62yAfOIUqabWEaaiucMIk6RyqJ+Q/QM69V26jjW86Gvov/EaoyT8zRCn+Xq7PVrbx0nuYUaO9wM3WAbjCE1NEUw09Um4UV+2OKfYfu5/S19gsAzGKqm6LE5FrShbdS0ku465DjDwKA/oQht19ejqbaEVuRbiLhuHByYLjtUAZpDutzP7cYdHsPJXWbjyNVgFwQoa1WXwf4Jd9YD/Ap80+yE7+u9aAAAAAElFTkSuQmCC);background-repeat:no-repeat;background-size:auto 100%;background-position-x:center&#125;.markdown-body code&#123;padding:.065em .4em;font-size:.87em;color:#c2185b;word-break:break-word;overflow-x:auto;background-color:#fff4f4;border-radius:2px&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;display:block;padding:16px 12px;margin:0;font-size:12px;color:#333;word-break:normal;overflow-x:auto;background:#f8f8f8&#125;.markdown-body pre>code::-webkit-scrollbar&#123;width:4px;height:4px&#125;.markdown-body pre>code::-webkit-scrollbar-track&#123;background-color:#bedcff&#125;.markdown-body pre>code::-webkit-scrollbar-thumb&#123;background-color:#2196f3;border-radius:10px&#125;.markdown-body a&#123;position:relative;text-decoration:none;color:#3da8f5;border-bottom:1px solid #bedcff&#125;.markdown-body a:hover&#123;color:#007fff;border-bottom-color:#007fff&#125;.markdown-body a:active&#123;color:#007fff&#125;.markdown-body a:after&#123;position:absolute;content:"";top:100%;left:0;width:100%;opacity:0;border-bottom:1px solid #bedcff;transition:top .3s,opacity .3s;transform:translateZ(0)&#125;.markdown-body a:hover:after&#123;top:0;opacity:1;border-bottom-color:#007fff&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #c3e0fd;border-spacing:0;border-collapse:collapse&#125;.markdown-body table thead&#123;color:#000;text-align:left;font-size:14px;background:#f6f6f6&#125;.markdown-body table tr:nth-child(2n)&#123;background-color:#f7fbff&#125;.markdown-body table tr:hover&#123;background-color:#e0edf7&#125;.markdown-body table td,.markdown-body table th&#123;padding:12px 8px;line-height:24px;border:1px solid #c3e0fd&#125;.markdown-body table th&#123;color:#005bb7;background-color:#dff0ff&#125;.markdown-body table td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#8c8c8c;border-left:4px solid #2196f3;background-color:#f0fdff;padding:1px 20px;margin:22px 0&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body b,.markdown-body blockquote>b,.markdown-body blockquote>strong,.markdown-body strong&#123;color:#2196f3&#125;.markdown-body em,.markdown-body i&#123;color:#4fc3f7&#125;.markdown-body del&#123;color:#ccc&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:4px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body details>summary&#123;outline:none;color:#005bb7;font-size:20px;font-weight:bolder;border-bottom:1px solid #bedcff;cursor:pointer&#125;.markdown-body details>p&#123;padding:10px 20px;margin:10px 0 0;color:#666;background-color:#f0fdff;border:2px dashed #2196f3&#125;.markdown-body h1::selection,.markdown-body h2::selection,.markdown-body h3::selection,.markdown-body h4::selection,.markdown-body h5::selection,.markdown-body h6::selection&#123;color:#005bb7;background-color:rgba(160,200,255,.15)&#125;.markdown-body p::selection&#123;color:#c80000&#125;.markdown-body a::selection,.markdown-body b::selection,.markdown-body del::selection,.markdown-body em::selection,.markdown-body i::selection,.markdown-body strong::selection&#123;background-color:transparent&#125;.markdown-body code::selection&#123;background-color:#ffeaeb&#125;.markdown-body pre>code::selection&#123;background-color:rgba(160,200,255,.25)&#125;.markdown-body ol ::selection,.markdown-body ul ::selection&#123;background-color:rgba(160,200,255,.15)&#125;.markdown-body .contains-task-list&#123;padding-left:14px;list-style:none&#125;.markdown-body .contains-task-list input[type=checkbox]&#123;position:relative&#125;.markdown-body .contains-task-list input[type=checkbox]:before&#123;content:"";position:absolute;top:0;left:0;right:0;bottom:0;width:inherit;height:inherit;background:#f0f8ff;border:1px solid #add6ff;border-radius:2px;box-sizing:border-box;z-index:1&#125;.markdown-body .contains-task-list input[type=checkbox]:checked:after&#123;content:"✓";position:absolute;top:-12px;left:0;right:0;bottom:0;width:0;height:0;color:#f55;font-size:20px;font-weight:700;z-index:2&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h2 data-id="heading-0">函数类型</h2>
在JavaScript中，有两种常见的定义函数的方式——函数声明和函数表达式。
<p>在TypeScript中定义函数类型 包含两部分：参数类型和返回值类型。</p>
<h3 data-id="heading-1">函数类型定义</h3>
<h4 data-id="heading-2">函数声明的类型定义</h4>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">sum</span>(<span class="hljs-params">x: <span class="hljs-built_in">number</span>, y: <span class="hljs-built_in">number</span></span>): <span class="hljs-title">number</span> </span>&#123;
  <span class="hljs-keyword">return</span> x + y;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p><strong>注意，输入多余的或者少于要求的参数，是不被允许的</strong></p>
</blockquote>
<pre><code class="hljs language-js copyable" lang="js">sum(<span class="hljs-number">1</span>,<span class="hljs-number">2</span>,<span class="hljs-number">3</span>); <span class="hljs-comment">// Error: Supplied parameters do not match any signature of call target.</span>
sum(<span class="hljs-number">1</span>); <span class="hljs-comment">// Error: Supplied parameters do not match any signature of call target.</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<h4 data-id="heading-3">函数表达式的类型定义</h4>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">let</span> sum = <span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params">x: number, y: number</span>): <span class="hljs-title">number</span> </span>&#123;
  <span class="hljs-keyword">return</span> x + y
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>事实上，上面的代码只对等号右侧的匿名函数进行了类型定义，而等号左边的<code>sum</code>是通过类型推论而推断出来的。</p>
<p>如果我们手动给<code>sum</code>添加类型，则应该是这样：</p>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-keyword">let</span> sum: <span class="hljs-function">(<span class="hljs-params">x: <span class="hljs-built_in">number</span>, y: <span class="hljs-built_in">number</span></span>) =></span> <span class="hljs-built_in">number</span> = <span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params">x: <span class="hljs-built_in">number</span>, y: <span class="hljs-built_in">number</span></span>): <span class="hljs-title">number</span> </span>&#123;
  <span class="hljs-keyword">return</span> x + y
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>注意不要混淆了TypeScript中的<code>=></code>和ES6中的<code>=></code>。
在TypeScript的类型定义中，<code>=></code>用来表示函数的定义，左边是输入类型，需要用括号括起来，右边是输出类型。</p>
<p>在ES6中，<code>=></code>代表箭头函数。</p>
<h3 data-id="heading-4">可选参数</h3>
<p>与接口中的可选属性类似，我们用<code>?</code>表示可选的参数：</p>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">buildName</span>(<span class="hljs-params">firstName: <span class="hljs-built_in">string</span>, lastName?: <span class="hljs-built_in">string</span></span>) </span>&#123;
  <span class="hljs-keyword">if</span>(lastName) &#123;
    <span class="hljs-keyword">return</span> firstName + <span class="hljs-string">' '</span> + lastName;
  &#125;
  <span class="hljs-keyword">return</span> firstName;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<blockquote>
<p>注意：可选参数必须接在必需参数后面，换句话说<strong>可选参数后面不允许再出现必需参数了</strong></p>
</blockquote>
<h3 data-id="heading-5">参数默认值</h3>
<p>在ES6中，允许给函数的参数添加默认值，<strong>TypeScript会将添加了默认值的参数识别为可选参数</strong></p>
<p>此时就不受「可选参数必须接在必需参数后面」的限制了：</p>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">buildName</span>(<span class="hljs-params">firstName: <span class="hljs-built_in">string</span> = <span class="hljs-string">'Zed'</span>, lastName?: <span class="hljs-built_in">string</span></span>) </span>&#123;
  <span class="hljs-keyword">return</span>  firstName + <span class="hljs-string">' '</span> + lastName;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-6">剩余参数</h3>
<p>ES6中，可以使用<code>...rest</code>的方式获取函数中的剩余参数<br>
剩余参数会被当做个数不限的可选参数，类型是数组。</p>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">buildName</span>(<span class="hljs-params">firstName: <span class="hljs-built_in">string</span>, ...restName: <span class="hljs-built_in">string</span>[]</span>) </span>&#123;
  <span class="hljs-keyword">return</span> firstName + <span class="hljs-string">' '</span> + restName.join(<span class="hljs-string">" "</span>);
&#125;
<span class="hljs-keyword">let</span> employeeName = buildName(<span class="hljs-string">"Joseph"</span>, <span class="hljs-string">"Samuel"</span>, <span class="hljs-string">"Lucas"</span>, <span class="hljs-string">"MacKinzie"</span>);

<span class="hljs-keyword">let</span> buildNameFn: <span class="hljs-function">(<span class="hljs-params">fname: <span class="hljs-built_in">string</span>, ...rest: <span class="hljs-built_in">string</span>[]</span>) =></span> <span class="hljs-built_in">string</span> = buildName;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-7">函数重载(overload)</h3>
<p>重载允许一个函数接受不同数量或类型的参数时，做出不同的处理。<br>
方法是为同一个函数提供多个函数类型定义来进行函数重载。</p>
<pre><code class="hljs language-ts copyable" lang="ts"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">getInfo</span>(<span class="hljs-params">name: <span class="hljs-built_in">string</span></span>): <span class="hljs-title">string</span></span>;
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">getInfo</span>(<span class="hljs-params">age: <span class="hljs-built_in">number</span></span>): <span class="hljs-title">number</span></span>;
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">getInfo</span>(<span class="hljs-params">str: <span class="hljs-built_in">number</span> | <span class="hljs-built_in">string</span></span>): <span class="hljs-title">number</span>|<span class="hljs-title">string</span>|<span class="hljs-title">void</span> </span>&#123;
  <span class="hljs-keyword">if</span>(<span class="hljs-keyword">typeof</span> str === <span class="hljs-string">'string'</span>) &#123;
    <span class="hljs-keyword">return</span> <span class="hljs-string">'名字：'</span> + str;
  &#125;
  <span class="hljs-keyword">if</span>(<span class="hljs-keyword">typeof</span> str === <span class="hljs-string">'number'</span>) &#123;
    <span class="hljs-keyword">return</span> <span class="hljs-string">'年龄：'</span> + str;
  &#125;
&#125;
<span class="hljs-built_in">console</span>.log(getInfo(<span class="hljs-string">'zhang san'</span>)) <span class="hljs-comment">// 名字：zhang san</span>
<span class="hljs-built_in">console</span>.log(getInfo(<span class="hljs-number">23</span>)) <span class="hljs-comment">// 年龄：23</span>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>上例中，我们重复定义了多次<code>getInfo</code>函数，前两次都是函数定义，最后一次是函数实现。
因此这里只有两个重载：一个是接受字符串另一个接受数字。</p>
<p>为了让编译器能够选择正确的检查类型，它与JavaScript里的处理流程相似。 它查找重载列表，尝试使用第一个重载定义。 如果匹配的话就使用这个。</p>
<p>因此，在定义重载的时候，一定要把最精确的定义放在最前面。</p></div>  
</div>
            
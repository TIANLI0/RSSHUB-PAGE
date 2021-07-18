
---
title: '基于Vue实现页面的引导操作'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8f7c9bb3c2014cbc97bc7d3ca40bbfaa~tplv-k3u1fbpfcp-zoom-1.image'
author: 掘金
comments: false
date: Sat, 17 Jul 2021 01:13:18 GMT
thumbnail: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8f7c9bb3c2014cbc97bc7d3ca40bbfaa~tplv-k3u1fbpfcp-zoom-1.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><blockquote>
<p>引导操作是一个非必须的功能，但是有这个功能的话，对第一次进入系统的人来说，是一个比较友好的体验，能快速的介绍自己系统的一些简单功能，我们可以基于<a href="https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fkamranahmedse%2Fdriver.js" target="_blank" rel="nofollow noopener noreferrer" title="https://github.com/kamranahmedse/driver.js" ref="nofollow noopener noreferrer">driver.js</a>很轻松的实现这个效果。</p>
</blockquote>
<p><strong>看看效果</strong></p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8f7c9bb3c2014cbc97bc7d3ca40bbfaa~tplv-k3u1fbpfcp-zoom-1.image" alt="图片丢失" loading="lazy" referrerpolicy="no-referrer"></p>
<h2 data-id="heading-0">安装</h2>
<p>首先，我们需要通过<code>npm</code>或者<code>yarn</code>安装<code>driver.js</code>：</p>
<p><strong>npm</strong></p>
<p><code>npm install --save driver.js</code></p>
<p><strong>yarn</strong></p>
<p><code>yarn add driver.js</code></p>
<h2 data-id="heading-1">开始</h2>
<p>因为<code>driver.js</code>是需要操作<code>dom</code>节点的，所以使用的时候需要等到节点渲染完成，需要在<code>onMounted</code>里面使用：</p>
<pre><code class="copyable">setup() &#123;
    const driver = new Driver()
    const show = () => &#123;
        driver.highlight(
            &#123;
                element: '#logo',
                popover: &#123;
                    title: 'Title for the Popover',
                    description: 'Description for it',
                    position: 'bottom',
                    offset: 20,
                &#125;
            &#125;
        )
    &#125;
​
    onMounted(() => &#123;
        setTimeout(() => &#123;
            show()
        &#125;)
    &#125;)
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><strong>这里我也不知道为啥，在<code>onMounted</code>里面直接调用<code>driver.js</code>的方法没用，甚至加了<code>nextTick</code>也不会有效果，只有在<code>setTimeout</code>里面才会有效果，有大佬指教？</strong></p>
<p><code>highlight</code>就是<code>driver.js</code>提供的高亮效果，但是我们的引导操作并会只有一个，一般会有许多个这样的操作，所以这样一个一个设置就不大现实了。</p>
<p><code>driver.js</code>提供了<code>defineSteps</code>这个方法，来实现一系列的引导操作：</p>
<pre><code class="copyable">setup() &#123;
    const driver = new Driver()
    const show = () => &#123;
      driver.defineSteps([
        &#123;
          element: '#logo',
          popover: &#123;
            title: '图标',
            description: '这是Vue的图标',
            position: 'bottom',
            offset: 20,
          &#125;
        &#125;
      ])
​
      driver.start()
    &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>通过<code>defineSteps</code>定义之后，需要使用<code>start</code>方法来开始引导。</p>
<h2 data-id="heading-2">公共配置</h2>
<p>我们可以在实例化<code>Driver</code>的时候，传入一些公共配置，这样的话，就很方便了，例如下一步，上一步的文案原来是英文的，我们可以在实例化时直接传入：</p>
<pre><code class="copyable">setup() &#123;
    const driver = new Driver(&#123;
      doneBtnText: '完成',
      closeBtnText: '关闭',
      nextBtnText: '下一步',
      prevBtnText: '上一步'
    &#125;)
    const show = () => &#123;
      driver.defineSteps([
        &#123;
          element: '#logo',
          popover: &#123;
            title: '图标',
            description: '这是Vue的图标',
            position: 'bottom',
            offset: 20
          &#125;
        &#125;
      ])
​
      driver.start()
    &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>当然，这个配置也<em><strong>可以在<code>options</code>里面覆盖掉</strong></em>，<code>driver.js</code>还提供了许多的内置配置：</p>
<pre><code class="copyable">const driver = new Driver(&#123;
  className: 'scoped-class',        // className to wrap driver.js popover
  animate: true,                    // Whether to animate or not
  opacity: 0.75,                    // Background opacity (0 means only popovers and without overlay)
  padding: 10,                      // Distance of element from around the edges
  allowClose: true,                 // Whether the click on overlay should close or not
  overlayClickNext: false,          // Whether the click on overlay should move next
  doneBtnText: 'Done',              // Text on the final button
  closeBtnText: 'Close',            // Text on the close button for this step
  stageBackground: '#ffffff',       // Background color for the staged behind highlighted element
  nextBtnText: 'Next',              // Next button text for this step
  prevBtnText: 'Previous',          // Previous button text for this step
  showButtons: false,               // Do not show control buttons in footer
  keyboardControl: true,            // Allow controlling through keyboard (escape to close, arrow keys to move)
  scrollIntoViewOptions: &#123;&#125;,        // We use `scrollIntoView()` when possible, pass here the options for it if you want any
  onHighlightStarted: (Element) => &#123;&#125;, // Called when element is about to be highlighted
  onHighlighted: (Element) => &#123;&#125;,      // Called when element is fully highlighted
  onDeselected: (Element) => &#123;&#125;,       // Called when element has been deselected
  onReset: (Element) => &#123;&#125;,            // Called when overlay is about to be cleared
  onNext: (Element) => &#123;&#125;,                    // Called when moving to next step on any step
  onPrevious: (Element) => &#123;&#125;,                // Called when moving to previous step on any step
&#125;);
<span class="copy-code-btn">复制代码</span></code></pre>
<p><em><strong><code>driver.js</code>生成的<code>popover</code>，会根据目标节点的大小生成的，所以如果<code>popover</code>过不合适的话，可以看看原来的<code>dom</code>节点是什么样子的。</strong></em></p>
<h2 data-id="heading-3">内置方法和属性</h2>
<p><code>driver.js</code>还内置了一些比较方便的方法，像<code>defineSteps</code>和<code>start</code>就是内置的方法：</p>
<ul>
<li>isActivated：是否正在引导过程中；</li>
</ul>

<ul>
<li>defineSteps： 定义引导步骤；</li>
<li>start(step = 0)：开始引导，可以传入一个<code>number</code>参数，表示从第几步开始，比如步骤过多的情况，我们可以做一个记录，下次用户点进来就可以从中间开始查看引导了。</li>
<li>moveNext：移动到下一个步骤的引导；</li>
<li>movePrevious：移动到上一个步骤的引导；</li>
<li>hasNextStep：是否有下一个步骤的引导；</li>
<li>hasPreviousStep：是否有上一个步骤的引导；</li>
</ul>
<p>其他的还有很多方法，可以查看官网</p></div>  
</div>
            
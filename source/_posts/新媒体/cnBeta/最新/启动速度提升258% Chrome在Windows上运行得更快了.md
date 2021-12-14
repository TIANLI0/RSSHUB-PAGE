
---
title: '启动速度提升25.8% Chrome在Windows上运行得更快了'
categories: 
 - 新媒体
 - cnBeta
 - 最新
headimg: 'https://static.cnbetacdn.com/article/2021/1210/d5ae678505e15ae.webp'
author: cnBeta
comments: false
date: Tue, 14 Dec 2021 00:31:44 GMT
thumbnail: 'https://static.cnbetacdn.com/article/2021/1210/d5ae678505e15ae.webp'
---

<div>   
<strong>由于全新的后台优化，适用于 Windows 10/11 平台的 Chrome 浏览器运行速度更快了。</strong>在 Google 和微软的共同努力下，双方一直试图通过节制 JavaScript 来减少后台标签的优先级。到目前为止，这些努力已经减少了基于 Chromium 的浏览器的 CPU、GPU 和内存的使用，从而让你更加积极的使用浏览器。<br>
 <p style="text-align:center"><a href="https://static.cnbetacdn.com/article/2021/1210/d5ae678505e15ae.webp" target="_blank"><img src="https://static.cnbetacdn.com/article/2021/1210/d5ae678505e15ae.webp" referrerpolicy="no-referrer"></a></p><p style="text-align: left;">如上文所述，Google 的解决方案一直仅限于后台标签，但并未对后台窗口进行相应的处理。现在当 Chrome 浏览器窗口最小化到任务栏、移出屏幕等情况下，这些窗口也会像后台标签一样处理，这明显有助于提高 Chrome 浏览器的性能。</p><p style="text-align: left;">基于这项假设，Google 开始研究名为“Native Window Occlusion”的项目，以减少被遮蔽窗口（用户无法主动看到）中标签的后台使用。</p><p style="text-align: left;">Google已经在这个项目上工作了三年多，它解决了与多显示器设置、虚拟桌面等的兼容性问题。作为优化项目的一部分，Google忽略了最小化的窗口（用户不可见）、虚拟桌面等场景。</p><p style="text-align:center"><a href="https://static.cnbetacdn.com/article/2021/1210/37f94ed829f8729.webp" target="_blank"><img src="https://static.cnbetacdn.com/article/2021/1210/37f94ed829f8729.webp" referrerpolicy="no-referrer"></a></p><p style="text-align: left;">Google在一篇博文中指出：“occlusion 线程告诉 <a data-link="1" href="https://microsoft.pvxt.net/x9Vg1" target="_blank">Windows</a>，它想知道各种 Windows 事件。UI 线程告诉 Windows，它想知道什么时候有重大的状态变化，例如，显示器关闭电源，或者用户锁定屏幕”。Google已经对该功能进行了一段时间的测试，现在已经向Windows上的每个人开放。</p><p style="text-align: left;">按照Google的说法，现在Chrome浏览器的启动速度提高了25.8%，它观察到GPU内存的使用减少了3.1%。同样，Google报告说，渲染器框架减少了20.4%，渲染崩溃减少了4.5%。</p>   
</div>
            
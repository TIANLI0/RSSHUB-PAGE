
---
title: 'Windows 8系统曾有一只_ASCII猫_ 帮助识别黑屏错误'
categories: 
 - 新媒体
 - cnBeta
 - 最新
headimg: 'https://static.cnbetacdn.com/article/2022/0225/1c12386f9b4fe72.webp'
author: cnBeta
comments: false
date: Fri, 25 Feb 2022 00:58:11 GMT
thumbnail: 'https://static.cnbetacdn.com/article/2022/0225/1c12386f9b4fe72.webp'
---

<div>   
Windows 开发者对猫真的是情有独钟。<strong>除了 Windows 10 系统就出现的非官方吉祥物 NinjaCat 之外，事实上在 Windows 8 系统中开发人员就引入了一只 ASCII 码的猫图。</strong>只是因为绘制 ASCII 猫图像需要耗费时间和内存，Windows 性能团队最后要求开发团队移除了猫图像。<br>
 <p style="text-align:center"><img src="https://static.cnbetacdn.com/article/2022/0225/1c12386f9b4fe72.webp" alt="Screenshot 2022-02-25 at 08-54-38 The cats sitting on a fence in early builds of Windows 8.webp" referrerpolicy="no-referrer"></p><p style="text-align: left;">在 <a data-link="1" href="https://microsoft.pvxt.net/x9Vg1" target="_blank">Windows</a> 8 平板体验中，对各种组件的组织和管理可以认为是层的集合，每个层都堆叠在下一个层的上面。鉴于今天讨论的话题，重要的层是开始层（Start layer）和应用层（Apps layer）。如果你正在使用一个应用程序，那么应用层会是全屏的。如果你已经打开了开始从菜单，那么开始层会覆盖应用层。如果最后一个应用退出了，那么开始层就会自动打开。任何时候都应该有一个全屏层。</p><p style="text-align: left;">当然，在开发过程中，不可避免的会出现错误，如果开始层和应用层都不显示，那么就会导致黑屏。</p><p style="text-align: left;">导致黑屏的原因有很多种，例如显卡驱动不兼容导致的崩溃；或者显卡驱动正常工作，但是合成器崩溃，导致没有给显卡驱动提供任何东西；或者合成器正常工作，但是 Shell 崩溃了，所以合成器没有东西可以渲染；又或者 Shell 可以正常工作，但它忘记在屏幕上放点东西。</p><p style="text-align: left;">针对最后一种情况，Windows 8 Shell 创建了一个支持窗口（backstop window），位于所有其他层的下面。如果其他层都不存在，那么至少你有一个后背窗口。在早期的调试版本中，该支持窗口包含一个 ASCII 码的猫咪图。这样，如果你看到猫，你就知道你是在最后的失败案例中。shell 正在运行，但是忘记在屏幕上显示一些东西。</p><p style="text-align: left;"><strong>为什么是猫？</strong></p><p style="text-align: left;">写支持窗口的开发者非常喜欢猫，他们使用了一系列猫的图像。在系统启动的时候，他们将第一幅猫的图像画在支持窗口上，每次支持窗口被要求重新绘制的时候，他们就循环到下一幅图片。这就像一个故事，每次都是一句话，每句话都在下一次出现灾难性故障时被揭示出来。</p><p style="text-align: left;"><a href="https://devblogs.microsoft.com/oldnewthing/20220208-00/?p=106232" target="_blank">根据</a><a data-link="1" href="https://c.duomai.com/track.php?site_id=242986&euid=&t=https://www.microsoftstore.com.cn/" target="_blank">微软</a>博客发布的博文，事实上该支持页面共有 9 个画面，均用 ASCII 进行绘制。</p><p style="text-align: center;"><a href="https://static.cnbetacdn.com/article/2022/0225/03683decaf96a36.gif" target="_blank"><img src="https://static.cnbetacdn.com/article/2022/0225/03683decaf96a36.gif" alt="firefox_JeoGw1P0V1.gif" width="100%/" referrerpolicy="no-referrer"></a></p>   
</div>
            
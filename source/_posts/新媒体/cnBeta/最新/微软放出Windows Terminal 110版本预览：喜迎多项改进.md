
---
title: '微软放出Windows Terminal 1.10版本预览：喜迎多项改进'
categories: 
 - 新媒体
 - cnBeta
 - 最新
headimg: 'https://static.cnbetacdn.com/article/2021/0715/05d0ab8cd8fef13.png'
author: cnBeta
comments: false
date: Thu, 15 Jul 2021 06:54:13 GMT
thumbnail: 'https://static.cnbetacdn.com/article/2021/0715/05d0ab8cd8fef13.png'
---

<div>   
随着今日 1.10 预览版本的发布，Windows 终端工具也迎来了一些功能上的升级和改进。<strong>比如在下拉菜单中引入了命令面板（Command Palette）按钮，还有在系统托盘中引入了 Quake 模式。</strong><br>
 <p><img src="https://static.cnbetacdn.com/article/2021/0715/05d0ab8cd8fef13.png" alt="0.png" referrerpolicy="no-referrer"></p><p style="text-align: center;">（来自：Microsoft <a href="https://devblogs.microsoft.com/commandline/windows-terminal-preview-1-10-release/" target="_self">Dev Blog</a>）</p><p>几天后，Windows Terminal 也将升级到 1.9 版本，但不会带来默认的终端设置和 UI 编辑操作功能，因为<a data-link="1" href="https://c.duomai.com/track.php?site_id=242986&euid=&t=https://www.microsoftstore.com.cn/" target="_blank">微软</a>正在努力修复预览功能的剩余 bug 。</p><p><img src="https://static.cnbetacdn.com/article/2021/0715/2b5276a301737bf.gif" alt="3.gif" referrerpolicy="no-referrer"></p><p>鉴于许多人认为下拉菜单中的“反馈”项目几乎没啥用，于是开发团队决定将之变更为 Command Palette 按钮。此外，你仍可使用 Ctrl + Shift + P 组合键来召唤它。</p><p><img src="https://static.cnbetacdn.com/article/2021/0715/e937dec9a70a8ce.png" alt="2.png" referrerpolicy="no-referrer"></p><p style="text-align: center;">系统托盘中的 Quake 模式</p><p>在 Quake 模式的窗口关闭时，系统托盘仍会保留其图标。除了使用 WinKey + ` 组合键，你也可以通过托盘来打开 Quake 窗口。</p><p>启动之后，你将无需在任务栏中运行父终端实例来再次打开。或者关闭任务栏上的终端实例，并继续访问 Quake 窗口。</p><p><a href="https://static.cnbetacdn.com/article/2021/0715/1441481fb56574d.png" target="_blank"><img src="https://static.cnbetacdn.com/thumb/article/2021/0715/1441481fb56574d.png" alt="1.png" referrerpolicy="no-referrer"></a></p><p>有趣的是，Windows Terminal 现可在文本渲染器中显示粗体字。微软会在后续引入设置项，以便用户进行配置。</p><p><a href="https://static.cnbetacdn.com/article/2021/0715/65415c97971d122.png" target="_blank"><img src="https://static.cnbetacdn.com/thumb/article/2021/0715/65415c97971d122.png" alt="4.png" referrerpolicy="no-referrer"></a></p><p style="text-align: center;">设置 UI 的体验方面，微软也带来了一些改进。</p><p>在 1.8 版本中，开发团队从设置 UI 中剔除了基础层，其相当于 settings.json 文件的“默认”（Default）部分，适用于所有配置文件。</p><p>但因为它和 JSON 片段扩展的架构产生了冲突，开发团队最终还是在 Windows Terminal 的 1.10 预览版本中予以移除。</p><p>目前微软正在为终端设计一套新 UI，并且广泛听取了大家的反馈，首先是将“Default”重新添加到设置 UI 中，却新命名与 settings.json 文件中使用的语法相匹配。</p><p>下一步，他们将设计一个扩展页面，来帮助用户更好地管理 JSON 片段扩展（fragment extensions）。</p><p><a href="https://static.cnbetacdn.com/article/2021/0715/b59c5761f52d5b5.png" target="_blank"><img src="https://static.cnbetacdn.com/thumb/article/2021/0715/b59c5761f52d5b5.png" alt="5.png" referrerpolicy="no-referrer"></a></p><p style="text-align: center;">引入新的操作（Actions）</p><p>Windows Terminal 提供了大量不同的操作，以供用户选用，且其中大多数默认支持快捷键。现在，用户还能够添加自定义的按键组合，而无需通过设置 UI 来实现。</p><p><strong>其它改进：</strong></p><blockquote><p>● 可明确设置终端的语言首选项，在设置 UI 的外观页面上找到此设置。</p><p>● 所有透明度滑块的数值，都已经加上了百分比符号。</p><p>● 能够根据索引来关闭标签页。</p><p>● 字体设置现可表示为 settings.json 文件中的一个对象。</p></blockquote><p><strong>Bug 修复：</strong></p><blockquote><p>● 打开设置 UI 时，不大可能再崩溃了。</p><p>● 关闭选项卡时，终端不再容易崩溃。</p><p>● 可使用命令行打开一个新选项卡。</p><p>● 1.10 预览版本的默认终端，在 22000.65 中更加可靠（1.10 默认终端与 22000.51 不兼容 / 1.9 与 22000.65 不兼容）。</p><p>● 其它与性能和可靠性相关的改进。</p></blockquote>   
</div>
            
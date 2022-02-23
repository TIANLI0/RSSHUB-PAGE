
---
title: 'Linux内核开发者正在讨论弃用ReiserFS文件系统'
categories: 
 - 新媒体
 - cnBeta
 - 最新
headimg: 'https://static.cnbetacdn.com/article/2022/0223/e6f79b1a8e4a3c8.jpg'
author: cnBeta
comments: false
date: Wed, 23 Feb 2022 07:18:34 GMT
thumbnail: 'https://static.cnbetacdn.com/article/2022/0223/e6f79b1a8e4a3c8.jpg'
---

<div>   
<strong>在多年未考虑将 Reiser4 上游化、也未提出任何有关将 Reiser5 主线化的尝试之后，功能丰富的 FeriserFS 文件系统或在 2022 年被正式踢出 Linux 内核。</strong>Phoronix 指出：21 年前，ReiserFS 被作为 Linux 内核的首个日志文件系统被引入。在推出的早期，这一开源文件系统提供了相当多的创新功能，甚至一度被 SuSE Linux 默认使用。在 Namesys 时代，我们继续看到了积极的功能开发。<br>
 <p><img src="https://static.cnbetacdn.com/article/2022/0223/e6f79b1a8e4a3c8.jpg" alt="1.jpg" referrerpolicy="no-referrer"></p><p style="text-align: center;">（图 via <a href="https://www.phoronix.com/scan.php?page=news_item&px=ReiserFS-2022-Linux-Deprecation" target="_self">Phoronix</a>）</p><p>然而自从 ReiserFS 主要开发者 Hans Reiser 在 15 年前因杀妻而入狱迎来，除了前 Namesys 开发者 Edward Shishkin 的相关工作，ReiserFS / Reiser4 已停滞相当长一段时间。</p><p>即使 Shishkin 一直在推进 Reiser4 / Reiser5，随着用户兴趣的减少，ReiserFS 文件系统的代码已基本腐烂。更别提因为 Hans 恶名在前，大家都不愿与 ReiserFS 再摊上关系。</p><p><img src="https://static.cnbetacdn.com/article/2022/0223/ed507bcb70b1e69.png" alt="2.png" referrerpolicy="no-referrer"></p><p>在被 EXT4、XFS、Btrfs、甚至 OpenZFS 吸引走了越来越多的份额之后，长期内核开发人员 Matthew Wilcox 终于在本周发起了“是否要将 ReiserFS 剔出 Linux 内核支持”的大讨论。</p><blockquote><p>目前其正在追求针对内核基础架构的更改，而 ReiserFS 留下的烂摊子，就是其中一个相当难搞的地方。</p><p>此外他指出，除了 Syzbot 修复和其它树范围内的代码变更，近年来已几乎看不到与之相关的新工作。</p><p>至少自 2019 年以来，似乎就没有任何用户上报的 ReiserFS bug 被修复。</p></blockquote><p><img src="https://static.cnbetacdn.com/article/2022/0223/1451501b06babeb.png" referrerpolicy="no-referrer"></p><p>在该讨论帖的下方，Edward Shishkin 有为 ReiserFS 发布一个补丁，以摆脱 AOP_FLAG_CONT_EXPAND 标记 —— 这也是 Wilcox 发起这个话题的一个主要原因。</p><p>目前已有不少其他内核开发者对弃用 ReiserFS 文件系统提供表达出了浓厚的兴趣。如果一切顺利，它应该会在经历后续几个内核版本后，被 Linux 内核给正式剔除。</p>   
</div>
            
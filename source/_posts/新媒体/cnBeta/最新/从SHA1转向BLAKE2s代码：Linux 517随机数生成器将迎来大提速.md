
---
title: '从SHA1转向BLAKE2s代码：Linux 5.17随机数生成器将迎来大提速'
categories: 
 - 新媒体
 - cnBeta
 - 最新
headimg: 'https://static.cnbetacdn.com/article/2022/0107/ef2d464625997a8.png'
author: cnBeta
comments: false
date: Fri, 07 Jan 2022 08:30:14 GMT
thumbnail: 'https://static.cnbetacdn.com/article/2022/0107/ef2d464625997a8.png'
---

<div>   
<strong>在下周的 Linux 5.17 合并窗口正式开启前，random（RNG）子系统维护者 Jason Donenfeld 已经为下一个内核周期提交了一批激动人心的更新。</strong>正如 2021 年 12 月底所述，作为 entropy extractor 代码的一部分，Linux 正从 SHA1 向 BLAKE2s 过渡。Phoronix 指出，BLAKE2s 代码不仅比 SHA1 更安全，且速度也更快（+131%）。<br>
 <p><img src="https://static.cnbetacdn.com/article/2022/0107/ef2d464625997a8.png" alt="1.png" referrerpolicy="no-referrer"></p><p style="text-align: center;">研究配图（来自：<a href="https://shattered.io/static/shattered.pdf" target="_self">Shattered.io</a>）</p><p>除了在随机数生成器（RNG）代码中逐步淘汰 SHA1，新提交还避免了在热路径中不必要的 RdRand 调用。通过绕过慢吞吞的 RdRand 额外调用，RNG 性能大举提升了 370% 。</p><p><img src="https://static.cnbetacdn.com/article/2022/0107/f21d7979569e36a.png" alt="3.png" referrerpolicy="no-referrer"></p><p style="text-align: center;">（图 via <a href="https://research.kudelskisecurity.com/2017/03/06/why-replace-sha-1-with-blake2/" target="_self">Kudelski Security</a>）</p><p><a href="https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.17-RNG" target="_self">Phoronix</a> 补充道，该系列提交主要针对各种不同错误 / 问题的修复、围绕 PREEMPT_RT 变更的小一些准备工作、以及其它改进而展开。</p><p><img src="https://static.cnbetacdn.com/article/2022/0107/4ec76f3bda4cda4.png" alt="2.png" referrerpolicy="no-referrer"></p><p>感兴趣的朋友，还请移步至 Kernel.org 查看完整的<a href="https://lore.kernel.org/lkml/20220106235920.995517-1-Jason@zx2c4.com/" target="_self">查询请求</a>。</p>   
</div>
            

---
title: 'Linux 5.17内核将持续引入I_O优化：NVMe性能有望提升5~6%'
categories: 
 - 新媒体
 - cnBeta
 - 最新
headimg: 'https://static.cnbetacdn.com/article/2021/1118/f0a28bc1263e4aa.jpg'
author: cnBeta
comments: false
date: Thu, 18 Nov 2021 06:34:08 GMT
thumbnail: 'https://static.cnbetacdn.com/article/2021/1118/f0a28bc1263e4aa.jpg'
---

<div>   
在最近结束的 Linux 5.16 内核合并窗口期间，我们已经见证了重大的 I/O 改进。<strong>以 Jens Axboe 为代表的维护者，专注于坚持不懈地优化块和 IO_uring 代码，以达成更高的 IOPS 操作效率。</strong>展望 Linux 5.17，这方面的工作也不会原地踏步。毕竟 Linux 5.16 开发周期内，还有不少未决的工作等待开发者去完成。<br>
 <p><img src="https://static.cnbetacdn.com/article/2021/1118/f0a28bc1263e4aa.jpg" alt="1.jpg" referrerpolicy="no-referrer"></p><p>据悉，在 Linux 5.16 合并窗口中，Jens Axboe 的大部分工作都围绕 I/O 优化而展开，以期最大限度地提升 <a data-link="1" href="https://c.duomai.com/track.php?site_id=242986&euid=&t=https://amd-cpu.jd.com/" target="_blank">AMD</a> 锐龙 R9-5950X 平台上的<a data-link="1" href="https://c.duomai.com/track.php?site_id=242986&euid=&t=https://intel.jd.com/" target="_blank">英特尔</a>傲腾 NVMe <a data-link="1" href="https://c.duomai.com/track.php?site_id=242986&euid=&t=https://list.jd.com/list.html?cat=670,677,11303" target="_blank">SSD</a> 的每核 IOPS 性能。</p><p>就在 5.16 合并窗口关闭几天后，Axboe 现又提交了四个 NVMe 代码补丁，以充分利用 Linux 5.16 中关于分配和完成 I/O 批次的新钩子。</p><p><img src="https://static.cnbetacdn.com/article/2021/1118/f022c5c1d3cfbb1.jpg" alt="2.jpg" referrerpolicy="no-referrer"></p><p>对于 NVMe 驱动器来说，这也意味着它们能够一次复制多个命令。测试表明，新修订带来了每核大约 500k IOPS 的改进、或 5~6% 的效率提升。</p><p>至于其它 I/O 优化工作，将继续在 perf-wip 分支中收集。截至目前，我们已在 Linux 5.16 合并窗口关闭后，看到了 38 个添加至该存储库的新补丁。</p><p>最后，Jens Axboe 透露自己正在搭建英特尔酷睿 i9-12900K 平台，以便和 AMD 锐龙 R9-5850X 平台开展比较、并且展望在将来为 Alder Lake 前端带来更多存储性能优化。</p>   
</div>
            
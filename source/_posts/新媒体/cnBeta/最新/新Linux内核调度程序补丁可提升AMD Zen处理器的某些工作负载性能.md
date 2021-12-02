
---
title: '新Linux内核调度程序补丁可提升AMD Zen处理器的某些工作负载性能'
categories: 
 - 新媒体
 - cnBeta
 - 最新
headimg: 'https://static.cnbetacdn.com/thumb/article/2021/1202/46c8964b80ec990.png'
author: cnBeta
comments: false
date: Thu, 02 Dec 2021 05:13:40 GMT
thumbnail: 'https://static.cnbetacdn.com/thumb/article/2021/1202/46c8964b80ec990.png'
---

<div>   
由 Linux 内核邮件列表可知，开发人员正在审查一组两个补丁，以调节内核调度程序的某些行为。<strong>对于 AMD 霄龙（EPYC）/ 锐龙（Ryzen）处理器的用户来说，新补丁有望带来显著的性能提升。</strong>其实去年，Linux 内核调度程序的代码已迎来部分调整，以允许 NUMA 节点之间的非均衡浮动，除非 1/4 的 CPU 内核占用率高于正常水平。<br>
 <p><a href="https://static.cnbetacdn.com/article/2021/1202/46c8964b80ec990.png" target="_blank"><img src="https://static.cnbetacdn.com/thumb/article/2021/1202/46c8964b80ec990.png" alt="4.png" referrerpolicy="no-referrer"></a></p><p style="text-align: center;">资料图（来自：<a data-link="1" href="https://c.duomai.com/track.php?site_id=242986&euid=&t=https://amd-cpu.jd.com/" target="_blank">AMD</a> | PDF）</p><p>此前，仅当目标节点有效空闲时，Linux 内核才允许 NUMA 节点之间的非均衡调用。长期从事相关工作的 Linux 内核开发者 Mel Gorman 去年写道，他们已经重新审视了内核 NUMA 节点之间的非均衡变化。</p><p><a href="https://static.cnbetacdn.com/article/2021/1202/1ba3ab6b7c26f9a.png" target="_blank"><img src="https://static.cnbetacdn.com/thumb/article/2021/1202/1ba3ab6b7c26f9a.png" alt="1.png" referrerpolicy="no-referrer"></a></p><p>在最后一级缓存（LLC）和节点之间未构成 1：1 关系的情况下 —— 以拥有多个 LLC 的 AMD Zen 处理器为例 —— 这么做可能并不是充分发挥其性能的最优解。</p><p>好消息是，随着新内核调度补丁的到来，Linux 将能够考虑到多个 LLC 的 NUMA 不平衡，从而带来性能体验的进一步提升。</p><p><a href="https://static.cnbetacdn.com/article/2021/1202/44e256b093b2ebd.png" target="_blank"><img src="https://static.cnbetacdn.com/thumb/article/2021/1202/44e256b093b2ebd.png" alt="3.png" referrerpolicy="no-referrer"></a></p><p>由 Mel Gorman 分享的跑分成绩可知，AMD Zen 3 平台可在 Stream OpenMP 内存基准测试项目中，迎来高达 180 ~ 268% 的改进。</p><p><img src="https://static.cnbetacdn.com/article/2021/1202/5b160080489bfd8.jpg" alt="2.jpg" referrerpolicy="no-referrer"></p><p style="text-align: center;">截图（来自：<a href="https://lore.kernel.org/lkml/20211201151844.20488-1-mgorman@techsingularity.net/" target="_self">LKML</a>）</p><p>在 CoreMark CPU 综合基准测试项目中，最大提升也达到了 15%（至少也有将近 10 % 的提升），此外 SPECjbb Java 工作负载的性能也有所改进。</p>   
</div>
            
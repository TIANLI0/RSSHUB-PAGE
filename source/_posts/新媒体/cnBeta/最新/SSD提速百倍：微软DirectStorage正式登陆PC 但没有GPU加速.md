
---
title: 'SSD提速百倍：微软DirectStorage正式登陆PC 但没有GPU加速'
categories: 
 - 新媒体
 - cnBeta
 - 最新
headimg: 'https://static.cnbetacdn.com/thumb/article/2022/0315/8670c6735fdfd38.jpg'
author: cnBeta
comments: false
date: Tue, 15 Mar 2022 07:17:03 GMT
thumbnail: 'https://static.cnbetacdn.com/thumb/article/2022/0315/8670c6735fdfd38.jpg'
---

<div>   
宣布两年多之后，微软终于把DirectStorage API带到了PC平台(此前用于Xbox X/S游戏机)，但却是个不完全体。简单地说，DirectStorage是一项存储子系统加速技术，<strong>可以让GPU计算着色器直接访问NVMe SSD，直接处理游戏资源的解压缩，而不再需要绕过CPU</strong>，从而大大提升游戏加载速度、降低延迟，同时也能节省CPU资源。<br>
 <p style="text-align: center;"><a href="https://img1.mydrivers.com/img/20220315/0914f91f3a2f4fe9b0c25a4eee36da4a.jpg" style="text-align: -webkit-center;" target="_blank"></a><a target="_blank" href="https://static.cnbetacdn.com/article/2022/0315/8670c6735fdfd38.jpg"><img data-original="https://static.cnbetacdn.com/article/2022/0315/8670c6735fdfd38.jpg" src="https://static.cnbetacdn.com/thumb/article/2022/0315/8670c6735fdfd38.jpg" referrerpolicy="no-referrer"></a></p><p style="text-align: center;">技术原理</p><p>NVIDIA RTX 30系列显卡的RTX IO技术，其实就是脱胎于DirectStorage API(类似NVIDIA RT光追与<a data-link="1" href="https://c.duomai.com/track.php?site_id=242986&euid=&t=https://www.microsoftstore.com.cn/" target="_blank">微软</a>DXR API)，相当于该技术在N卡上的一种实现方式，官方宣称<strong>输入/输出性能是传统硬盘存储的最高达100倍，CPU占用率则可以降低20倍</strong></p><p style="text-align: center;"><a href="https://img1.mydrivers.com/img/20220315/e47ed7f7903944f1bb23056771376f4f.jpg" target="_blank"></a><a target="_blank" href="https://static.cnbetacdn.com/article/2022/0315/cf5d6f9d411ab7a.jpg"><img data-original="https://static.cnbetacdn.com/article/2022/0315/cf5d6f9d411ab7a.jpg" src="https://static.cnbetacdn.com/thumb/article/2022/0315/cf5d6f9d411ab7a.jpg" referrerpolicy="no-referrer"></a></p><p style="text-align: center;">传统IO</p><p style="text-align: center;"><a href="https://img1.mydrivers.com/img/20220315/07a47f1f3ae34622a1d6460a17fde8ce.jpg" target="_blank"></a><a target="_blank" href="https://static.cnbetacdn.com/article/2022/0315/fcde95063e047b2.jpg"><img data-original="https://static.cnbetacdn.com/article/2022/0315/fcde95063e047b2.jpg" src="https://static.cnbetacdn.com/thumb/article/2022/0315/fcde95063e047b2.jpg" referrerpolicy="no-referrer"></a></p><p style="text-align: center;">RTX IO</p><p>DirectStorage API系统<strong>支持<a data-link="1" href="https://microsoft.pvxt.net/x9Vg1" target="_blank">Windows</a> 10/11，当然微软推荐Windows 11</strong>，因为其内置存储优化机制。</p><p>硬件上，<a data-link="1" href="https://c.duomai.com/track.php?site_id=242986&euid=&t=https://list.jd.com/list.html?cat=670,677,11303" target="_blank">SSD</a>此前的要求是必须支持NVMe，并支持PCIe 3.0或者PCIe 4.0，但是现在不强制要求NVMe，<strong>不仅仅是M.2/PCIe SSD可以用，甚至支持SATA SSD。</strong></p><p>显卡上需要<strong>支持DX12</strong>，推荐最新的DX12 Ultimate，包括NVIDIA RTX 30系列、<a data-link="1" href="https://c.duomai.com/track.php?site_id=242986&euid=&t=https://amd-cpu.jd.com/" target="_blank">AMD</a> RX 6000系列。</p><p><strong>不过目前，DirectStorage在PC上还不支持GPU加速，效果会大打折扣，微软只是承诺GPU加速就在路线图上，下一步就会实现。</strong></p><p>至于具体什么时候才支持GPU加速，微软没有明确的时间表，慢慢等吧。DirectStorage可是最初说去年就会登陆PC的……</p><p><a href="https://img1.mydrivers.com/img/20220315/6cf5722ec8d14a72a01519cff9ef8618.jpg" style="text-align: -webkit-center;" target="_blank"></a><a target="_blank" href="https://static.cnbetacdn.com/article/2022/0315/8848b7ee202addf.jpg"><img data-original="https://static.cnbetacdn.com/article/2022/0315/8848b7ee202addf.jpg" src="https://static.cnbetacdn.com/thumb/article/2022/0315/8848b7ee202addf.jpg" referrerpolicy="no-referrer"></a></p>   
</div>
            
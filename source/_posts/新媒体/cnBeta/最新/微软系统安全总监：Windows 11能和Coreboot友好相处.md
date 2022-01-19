
---
title: '微软系统安全总监：Windows 11能和Coreboot友好相处'
categories: 
 - 新媒体
 - cnBeta
 - 最新
headimg: 'https://static.cnbetacdn.com/article/2022/0119/a1eaa57e613f145.webp'
author: cnBeta
comments: false
date: Wed, 19 Jan 2022 00:35:47 GMT
thumbnail: 'https://static.cnbetacdn.com/article/2022/0119/a1eaa57e613f145.webp'
---

<div>   
即使保持 UEFI SecureBoot 处于启用状态，并满足 TPM 门槛和其他安全要求，<strong>通过相关操作也能让 Windows 11 系统很好的在开源的 Coreboot 上运行。<br></strong><br>
 <p>coreboot，原名LinuxBIOS，是一个旨在取代计算机中专有固件的软件项目，它采用轻量级固件设计，只执行加载和运行现代32位或64位操作系统所需的最少量任务。</p><p style="text-align:center"><img src="https://static.cnbetacdn.com/article/2022/0119/a1eaa57e613f145.webp" referrerpolicy="no-referrer"></p><p style="text-align: left;">在刚刚过去的圣诞假期中，<a data-link="1" href="https://c.duomai.com/track.php?site_id=242986&euid=&t=https://www.microsoftstore.com.cn/" target="_blank">微软</a>企业和操作系统安全总监大卫·韦斯顿（David Weston）用业余和休息时间，成功让 <a data-link="1" href="https://microsoft.pvxt.net/x9Vg1" target="_blank">Windows</a> 11 运行在具有开源固件栈的设备上。在这次冒险中，他使用了 Coreboot 移植到 Supermicro X11SCH 主板（<a data-link="1" href="https://c.duomai.com/track.php?site_id=242986&euid=&t=https://intel.jd.com/" target="_blank">英特尔</a> Coffee Lake 时代），该移植由 9elements security 进行。</p><p style="text-align:center"><img src="https://static.cnbetacdn.com/article/2022/0119/f58f508d8ce79ed.webp" referrerpolicy="no-referrer"></p><p style="text-align: left;">TianoCore EDK II UEFI 实现使用的是微软的 Project Mu。昨天 David Weston 分享了他的项目是成功的。他能够让 Windows 11 在开源固件堆栈上运行，包括 UEFI SecureBoot、独立 TPM2 和其他相关的安全功能，以满足 Windows 11 的硬件要求。反过来，Weston 也一直在跟进，对 Coreboot 项目大加赞赏。</p><p style="text-align: left;">目前支持的主板和其他相关资源都可以在 Coreboot.org 上找到。不幸的是，除了Google Chromebooks，大多数支持 Coreboot 的主板，能够买到和不太昂贵的最终是几代老英特尔的硬件和一些 System76 笔记本电脑。英特尔的 FSP 仍然需要 blobs，而对于那些想要一个真正的自由软件系统的人来说，最大的赢家仍然是 Raptor Computing Systems 和他们的 POWER9 平台。</p>   
</div>
            
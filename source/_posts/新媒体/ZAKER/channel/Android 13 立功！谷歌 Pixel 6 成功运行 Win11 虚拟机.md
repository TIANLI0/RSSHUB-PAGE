
---
title: 'Android 13 立功！谷歌 Pixel 6 成功运行 Win11 虚拟机'
categories: 
 - 新媒体
 - ZAKER
 - channel
headimg: 'https://cors.zfour.workers.dev/?http://zkres2.myzaker.com/202202/620a63d48e9f091d2d41d884_1024.jpg'
author: ZAKER
comments: false
date: Mon, 14 Feb 2022 16:35:59 GMT
thumbnail: 'https://cors.zfour.workers.dev/?http://zkres2.myzaker.com/202202/620a63d48e9f091d2d41d884_1024.jpg'
---

<div>   
<p>IT 之家 2 月 14 日消息，微软在 Win11 中推出了安卓子系统 WSA，基于 Hyper-V 虚拟化平台，这个大家都不陌生。而谷歌在 Chrome OS 中也采用了类似的技术运行 Linux 程序，名为 Linux 内核虚拟机 KVM。Android 系统也是基于 Linux 内核构建的，因此在 Android 中使用 KVM 运行其他操作系统在理论上也是可行的。</p><p>据 XDA 高级成员 kdrag0n 最新测试，谷歌 Pixel 6 在安装 Android 13 首个开发者预览版后，成功运行了 Win11 Arm 虚拟机。</p><p></p><div class="img_box" id="id_imagebox_0" onclick><div class="content_img_div perview_img_div"><img class="lazy opacity_0 " id="img_0" data-original="http://zkres2.myzaker.com/202202/620a63d48e9f091d2d41d884_1024.jpg" data-height="375" data-width="600" src="https://cors.zfour.workers.dev/?http://zkres2.myzaker.com/202202/620a63d48e9f091d2d41d884_1024.jpg" referrerpolicy="no-referrer"></div></div>该技术的原理是，在用于 Tensor 平台的 Android 13 引导加载程序和固件中，谷歌添加了向内核公开异常级别 2（Exception Level 2）管理程序权限级别的功能，以实现其受保护的 KVM ( pKVM ) ，从而可以轻松地在未受保护的 VM 上利用完整的 KVM 功能。<p></p><p>IT 之家了解到，根据测试，该功能可以在虚拟机上实现近乎原生的性能，但目前还不支持 GPU 硬件加速。</p><p></p><div class="img_box" id="id_imagebox_1" onclick><div class="content_img_div perview_img_div"><img class="lazy opacity_0 " id="img_1" data-original="http://zkres1.myzaker.com/202202/620a63d48e9f091d2d41d885_1024.jpg" data-height="608" data-width="671" src="https://cors.zfour.workers.dev/?http://zkres1.myzaker.com/202202/620a63d48e9f091d2d41d885_1024.jpg" referrerpolicy="no-referrer"></div></div><div class="img_box" id="id_imagebox_2" onclick><div class="content_img_div perview_img_div"><img class="lazy opacity_0 " id="img_2" data-original="http://zkres2.myzaker.com/202202/620a63d48e9f091d2d41d886_1024.jpg" data-height="1333" data-width="600" src="https://cors.zfour.workers.dev/?http://zkres2.myzaker.com/202202/620a63d48e9f091d2d41d886_1024.jpg" referrerpolicy="no-referrer"></div></div>kdrag0n 甚至在手机上玩起了《毁灭战士》，这款 1993 年的老游戏运行起来毫无压力。<p></p><p></p><div class="img_box" id="id_imagebox_3" onclick><div class="content_img_div perview_img_div"><img class="lazy opacity_0 " id="img_3" data-original="http://zkres2.myzaker.com/202202/620a63d48e9f091d2d41d887_1024.jpg" data-height="596" data-width="681" src="https://cors.zfour.workers.dev/?http://zkres2.myzaker.com/202202/620a63d48e9f091d2d41d887_1024.jpg" referrerpolicy="no-referrer"></div></div>谷歌将在 Android 13 正式版中支持 pKVM，到时候我们就可以看到 Win11 虚拟机在手机上的实际表现究竟如何了。<p></p><div id="recommend_bottom"></div><div id="article_bottom"></div>  
</div>
            

---
title: '未达到系统要求，微软 Win11 Beta _ Release 预览版也出现水印了'
categories: 
 - 新媒体
 - ZAKER
 - channel
headimg: 'https://cors.zfour.workers.dev/?http://zkres2.myzaker.com/202202/62143bf5b15ec07b4b2a4611_1024.jpg'
author: ZAKER
comments: false
date: Wed, 16 Mar 2022 05:30:00 GMT
thumbnail: 'https://cors.zfour.workers.dev/?http://zkres2.myzaker.com/202202/62143bf5b15ec07b4b2a4611_1024.jpg'
---

<div>   
<p>IT 之家 3 月 16 日消息，微软今日向 Win11 Beta / Release 预览版用户推送了 Build 22000.588 ( KB5011563 ) 更新，带来了多项 Bug 修复。</p><p>然而更新日志中没有提到，在更新到该版本后，不受支持的电脑也将出现类似 Dev 预览版的水印，右下角提醒用户 "System requirements not met"（未达到系统要求）。</p><p></p><div class="img_box" id="id_imagebox_0" onclick><div class="content_img_div perview_img_div"><img class="lazy opacity_0 " id="img_0" data-original="http://zkres2.myzaker.com/202202/62143bf5b15ec07b4b2a4611_1024.jpg" data-height="152" data-width="402" src="https://cors.zfour.workers.dev/?http://zkres2.myzaker.com/202202/62143bf5b15ec07b4b2a4611_1024.jpg" referrerpolicy="no-referrer"></div></div>此外，Beta / Release 预览版 Build 22000.588 上的新水印会引导用户进行设置，提醒用户 " 转到设置以了解更多信息 "。<p></p><p></p><div class="img_box" id="id_imagebox_1" onclick><div class="content_img_div perview_img_div"><img class="lazy opacity_0 " id="img_1" data-original="http://zkres2.myzaker.com/202203/62319c6c8e9f0904b27863de_1024.jpg" data-height="625" data-width="1119" src="https://cors.zfour.workers.dev/?http://zkres2.myzaker.com/202203/62319c6c8e9f0904b27863de_1024.jpg" referrerpolicy="no-referrer"></div></div>IT 之家了解到，目前已经有了解决方法，通过修改注册表，可以轻松去除水印。<p></p><p>去除水印方法：</p><p>Win+R 运行 "Regedit"，打开注册表编辑器</p><p>导航到以下项：</p><p>HKEY_CURRENT_USERControl PanelUnsupportedHardwareNotificationCache</p><p>将其中的 SV2 DWORD 值从 1 修改为 0</p><p>保存后重启电脑</p><p></p><div class="img_box" id="id_imagebox_2" onclick><div class="content_img_div perview_img_div"><img class="lazy opacity_0 " id="img_2" data-original="http://zkres1.myzaker.com/202202/62161ac1b15ec06ec34fc000_1024.jpg" data-height="800" data-width="1380" src="https://cors.zfour.workers.dev/?http://zkres1.myzaker.com/202202/62161ac1b15ec06ec34fc000_1024.jpg" referrerpolicy="no-referrer"></div></div>如果你的注册表编辑器中没有 UnsupportedHardwareNotificationCache 项：<p></p><p>在以下目录新建 UnsupportedHardwareNotificationCache 项：</p><p>HKEY_CURRENT_USERControl Panel</p><p>在 UnsupportedHardwareNotificationCache 项下新建 SV2 DWORD 值，并将其修改为 0</p><div id="recommend_bottom"></div><div id="article_bottom"></div>  
</div>
            
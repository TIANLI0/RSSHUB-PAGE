
---
title: '微软正式禁用 Win11_10 MSIX AppX 安装器协议链接'
categories: 
 - 新媒体
 - ZAKER
 - channel
headimg: 'https://cors.zfour.workers.dev/?http://zkres2.myzaker.com/202202/61fe317bb15ec077a77c4dde_1024.jpg'
author: ZAKER
comments: false
date: Sat, 05 Feb 2022 00:16:12 GMT
thumbnail: 'https://cors.zfour.workers.dev/?http://zkres2.myzaker.com/202202/61fe317bb15ec077a77c4dde_1024.jpg'
---

<div>   
<p>IT 之家 2 月 5 日消息，微软今天正式宣布，为了防止恶意攻击，它已经禁用了 MSIX 应用程序安装器（installer）协议链接。该协议允许用户直接从网络服务器上安装各种应用程序，而无需先将其下载到本地存储。当时的想法是，这种方法将为用户节省空间，因为整个 MSIX 包不需要下载。</p><p></p><div class="img_box" id="id_imagebox_0" onclick><div class="content_img_div perview_img_div"><img class="lazy opacity_0 " id="img_0" data-original="http://zkres2.myzaker.com/202202/61fe317bb15ec077a77c4dde_1024.jpg" data-height="428" data-width="760" src="https://cors.zfour.workers.dev/?http://zkres2.myzaker.com/202202/61fe317bb15ec077a77c4dde_1024.jpg" referrerpolicy="no-referrer"></div></div>然而，人们注意到，这种 Windows 应用程序安装包被用来分发恶意的 PDF 文件，如 Emotet 和 BazarLoader 恶意软件。因此，该协议在去年被禁用，今天才正式宣布。这个 Windows AppX 安装程序的欺骗漏洞被分配了 ID CVE-2021-43890。<p></p><p></p><div class="img_box" id="id_imagebox_1" onclick><div class="content_img_div perview_img_div"><img class="lazy opacity_0 " id="img_1" data-original="http://zkres2.myzaker.com/202202/61fe317bb15ec077a77c4ddf_1024.jpg" data-height="620" data-width="977" src="https://cors.zfour.workers.dev/?http://zkres2.myzaker.com/202202/61fe317bb15ec077a77c4ddf_1024.jpg" referrerpolicy="no-referrer"></div></div>公告的帖子说，<p></p><p>" 我们最近被告知，MSIX 的 ms-appinstaller 协议可以被恶意使用。具体来说，攻击者可以欺骗 App Installer 来安装一个用户不打算安装的软件包。</p><p> [ ... ] 目前，我们已经禁用了 ms-appinstaller 方案（协议）。这意味着 App Installer 将不能直接从网络服务器上安装一个应用程序。相反，用户将需要首先将应用程序下载到他们的设备上，然后用 App Installer 安装该软件包。这可能会增加一些软件包的下载大小。"</p><p>以下是你如何在你的网站上禁用该协议的方法。</p><p>" 如果你在网站上利用 ms-appinstaller 协议，我们建议你更新应用程序的链接，删除 'ms-appinstaller:?source=' ，这样 MSIX 包或 App Installer 文件就会下载到用户的设备上。"</p><p>微软还表示，它正在研究如何在未来某个时候以安全的方式重新启用该协议，比如添加某些组策略。但就目前而言，上述的变通方法是防止恶意攻击的临时解决方案。该公司指出，</p><p>" 我们正在花时间进行彻底的测试，以确保能够以安全的方式重新启用该协议。我们正在研究引入一个组策略，允许 IT 管理员重新启用该协议并控制其在组织内的使用。"</p><div id="recommend_bottom"></div><div id="article_bottom"></div>  
</div>
            

---
title: 'NVIDIA拒绝支付赎金后 威胁者利用代码签署恶意软件 可在Windows中加载'
categories: 
 - 新媒体
 - cnBeta
 - 最新
headimg: 'https://static.cnbetacdn.com/article/2022/0307/c3ef61672d7b8ca.webp'
author: cnBeta
comments: false
date: Mon, 07 Mar 2022 01:06:41 GMT
thumbnail: 'https://static.cnbetacdn.com/article/2022/0307/c3ef61672d7b8ca.webp'
---

<div>   
<strong>利用窃取过来的 NVIDIA 代码，威胁者利用签名证书来签署恶意软件，使其看起来值得信赖，并允许在 Windows 中加载恶意驱动程序。</strong>本周，NVIDIA 公司证实，他们遭受了一次网络攻击，使威胁者得以窃取员工的证书和专有数据。<br>
 <p style="text-align:center"><img src="https://static.cnbetacdn.com/article/2022/0307/c3ef61672d7b8ca.webp" referrerpolicy="no-referrer"></p><p style="text-align: left;">对本次泄露事件负责的勒索集团 Lapsus$ 表示，他们已经窃取了 1TB 的数据，并在 NVIDIA 拒绝与他们谈判后开始在网上泄露这些数据。泄漏的数据包括 2 份被盗的代码签名证书，这些证书是 NVIDIA 开发人员用来签署其驱动程序和可执行文件的。</p><p style="text-align:center"><img src="https://static.cnbetacdn.com/article/2022/0307/2fafec9efa2f4be.png" referrerpolicy="no-referrer"></p><p style="text-align: left;">代码签名证书允许开发人员对可执行文件和驱动程序进行数字签名，以便 <a data-link="1" href="https://microsoft.pvxt.net/x9Vg1" target="_blank">Windows</a> 和终端用户能够验证文件的所有者，以及它们是否被第三方篡改过。为了提高 Windows 的安全性，<a data-link="1" href="https://c.duomai.com/track.php?site_id=242986&euid=&t=https://www.microsoftstore.com.cn/" target="_blank">微软</a>还要求内核模式的驱动程序在操作系统加载之前必须进行代码签名。</p><p style="text-align:center"><img src="https://static.cnbetacdn.com/article/2022/0307/1311c77010d8f30.webp" referrerpolicy="no-referrer"></p><p style="text-align:center"><img src="https://static.cnbetacdn.com/article/2022/0307/0c9cf30f741474d.webp" referrerpolicy="no-referrer"></p><p style="text-align: left;">在 Lapsus$ 泄露了英伟达的代码签名证书后，安全研究人员很快发现，这些证书被用来签署恶意软件和威胁者使用的其他工具。根据上传到 VirusTotal 恶意软件扫描服务的样本，被盗的证书被用来签署各种恶意软件和黑客工具，如 Cobalt Strike 信标、Mimikatz、后门和远程访问木马。</p><p style="text-align: left;">例如，一个威胁者用该证书签署了一个 Quasar 远程访问特洛伊木马[VirusTotal]，而另一个人用该证书签署了一个 Windows 驱动程序[VirusTotal]。虽然这 2 个被盗的英伟达证书都已过期，但Windows仍然允许在操作系统中加载用这些证书签名的驱动程序。</p>   
</div>
            
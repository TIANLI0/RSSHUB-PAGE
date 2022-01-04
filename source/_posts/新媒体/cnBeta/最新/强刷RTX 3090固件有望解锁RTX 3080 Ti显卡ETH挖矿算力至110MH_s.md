
---
title: '强刷RTX 3090固件有望解锁RTX 3080 Ti显卡ETH挖矿算力至110MH_s'
categories: 
 - 新媒体
 - cnBeta
 - 最新
headimg: 'https://static.cnbetacdn.com/thumb/article/2022/0104/432ee31274ac7b1.jpg'
author: cnBeta
comments: false
date: Tue, 04 Jan 2022 00:24:46 GMT
thumbnail: 'https://static.cnbetacdn.com/thumb/article/2022/0104/432ee31274ac7b1.jpg'
---

<div>   
早些时候，加密货币挖矿专家 CryptoDonkeyMiner 在油管上分享了一段视频，介绍了为 EVGA RTX 3080 Ti 显卡刷入 RTX 3090 vBIOS 的可行性。<strong>据说其它厂牌的 RTX 3080 Ti（LHR）显卡亦可尝试刷入相同的固件，从而获得高达 21% 的加密货币挖矿性能提升。</strong>但其实早在 2021 年 12 月 13 日，外媒就已报道过针对 RTX 3080 Ti 的算力破解操作。<br>
 <p><a href="https://static.cnbetacdn.com/article/2022/0104/432ee31274ac7b1.jpg" target="_blank"><img src="https://static.cnbetacdn.com/thumb/article/2022/0104/432ee31274ac7b1.jpg" referrerpolicy="no-referrer"></a></p><p>以<a data-link="1" href="http://www.anrdoezrs.net/links/9019719/type/dlg/sid//https://www.dell.com/zh-cn/shop/deals" target="_blank">戴尔</a>和 Alienware 的 RTX 3080 Ti 显卡为例，据说强刷 vBIOS 后的 ETH 挖矿算力可提升 20 MH/s 左右（至 110 MH/S）。</p><p>早前，Red Panda Mining 也借鉴过 CryptoDonkeyMiner 的技术方案，而后映众（Inno3D）3080 Ti iChill 3 也被尝试调用 EVGA XC3 的固件，结果发现可解锁算力至 91 MH/s 。</p><p style="text-align: center;"><iframe src="//tv.sohu.com/s/sohuplayer/iplay.html?bid=315813063&autoplay=false&disablePlaylist=true" width="640" height="480" frameborder="0"></iframe></p><p style="text-align: center;">RTX 3080 TI HASHRATE FIX - CryptoDonkeyMiner（<a href="https://tv.sohu.com/v/dXMvODIyMjQwNTMvMzE1ODEzMDYzLnNodG1s.html" target="_self">via</a>）</p><p>在 <a href="https://wccftech.com/nvidia-geforce-rtx-3080-ti-flashed-with-dell-rtx-3090-bios-to-achieve-a-staggering-110-mh-s-mining-ethereum/" target="_self">WCCFTech</a> 最新收到的电子邮件中，CryptoMiningDonkey 提到他通过刷入戴尔的 RTX 3090 vBIOS，成功地将手头的 RTX 3080 Ti 显卡解锁至 110 MH/s 。</p><p>周一早些时候，其在 YouTube <a href="https://www.youtube.com/c/CryptoDonkeyMiner/community" target="_self">社区</a>页面上发帖证实了适用的戴尔 / Alienware GPU 固件（<a href="https://www.techpowerup.com/vgabios/236871/dell-rtx3090-24576-210726" target="_self">传送门</a>）。感兴趣的朋友，可通过 GPU-Z 工具软件，查阅其设备 ID 是否包含“2204”字段。</p><p><img src="https://static.cnbetacdn.com/article/2022/0104/7761bdfcd6f8aba.png" referrerpolicy="no-referrer"></p><p style="text-align: center;"><a href="https://www.reddit.com/r/gpumining/comments/ruflz2/dell_and_alienware_rtx_3080_ti_to_rtx_3090_bios/" target="_self">Reddit</a> 上亦有讨论帖</p><p><em><strong>【警告】通过 nvflash / HiveOS flash 强刷 vBIOS 或导致显卡变砖 / 损坏（风险请自负）。</strong></em></p><p>以下是参考命令行：</p><blockquote><p>nvflash64 -b backup.rom</p><p>nvflash64 --list</p><p>nvflash64 --index=5 --protectoff</p><p>nvflash64 --index=5 <a data-link="1" href="http://www.anrdoezrs.net/links/9019719/type/dlg/sid//https://www.dell.com/zh-cn/shop/deals" target="_blank">DELL</a>.RTX3090.24576.210726.rom</p></blockquote><p>如果你并未使用 64-bit 版本的 nvflash，请移除命令中的“64”字样，然后参考输入对应的 --list 中的索引编号。</p>   
</div>
            
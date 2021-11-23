
---
title: '微软赏金太抠门：安全研究人员怒而曝光Windows提权零日漏洞'
categories: 
 - 新媒体
 - cnBeta
 - 最新
headimg: 'https://static.cnbetacdn.com/thumb/article/2021/1123/4165c22ea970e68.jpg'
author: cnBeta
comments: false
date: Tue, 23 Nov 2021 07:12:38 GMT
thumbnail: 'https://static.cnbetacdn.com/thumb/article/2021/1123/4165c22ea970e68.jpg'
---

<div>   
安全研究人员 @MalwareTechBlog 在推特上吐槽道：由于微软调整了漏洞赏金计划，其原本想提交的一个影响所有受支持 Windows 操作系统版本的提权漏洞的“认定价值”，也从 10000 美元瞬间跌到了 1000 美元。<strong>Abdelhamid Naceri 在接受 Bleeping Computer 采访时称，大家对微软的新漏洞赏金政策感到十分沮丧。</strong><br>
 <p><a href="https://static.cnbetacdn.com/article/2021/1123/4165c22ea970e68.jpg" target="_blank"><img src="https://static.cnbetacdn.com/thumb/article/2021/1123/4165c22ea970e68.jpg" referrerpolicy="no-referrer"></a></p><p style="text-align: center;">Windows 提权漏洞的简易演示</p><p>据悉，自 2020 年 4 月以来，<a data-link="1" href="https://c.duomai.com/track.php?site_id=242986&euid=&t=https://www.microsoftstore.com.cn/" target="_blank">微软</a>的漏洞赏金计划就已经变得“一文不值”。如果这家软件巨头没有下调赏金价值，以 Abdelhamid Naceri 为代表的安全研究人员，也不会怒而曝光零日漏洞。</p><p>其他安全研究人员附和道：Naceri 披露的漏洞，很容易让普通用户提取并获得 SYSTEM 系统权限。更让人感到震惊的是，该漏洞利用是基于微软的补丁而开发的。</p><p><img src="https://static.cnbetacdn.com/article/2021/1123/66ec62be220d482.png" referrerpolicy="no-referrer"></p><p style="text-align: center;">（概念验证：<a href="https://github.com/klinix5/InstallerFileTakeOver" target="_self">GitHub</a>）</p><p>具体说来是，Naceri 在分析 <a href="https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-41379" target="_self">CVE-2021-41379</a> 补丁时发现了这个漏洞。然而微软并未正确修复相关错误、或选择另一条技术路线，结果导致变种漏洞的危害性比之前更强。</p><p>Naceri 在文章中解释称，“安装器文件接管”（InstallerFileTakeOver）漏洞影响 Windows 10、Windows 11 和 Windows Server 等多个仍受支持的操作系统版本。</p><p style="text-align: center;"><iframe src="//tv.sohu.com/s/sohuplayer/iplay.html?bid=305429876&autoplay=false&disablePlaylist=true" width="640" height="480" frameborder="0"></iframe></p><p style="text-align: center;">New Windows zero-day local privilege elevation vulnerability（<a href="https://tv.sohu.com/v/dXMvODIyMjQwNTMvMzA1NDI5ODc2LnNodG1s.html" target="_self">via</a>）</p><p>虽然漏洞本身“并不完整”，但别有用心的攻击者还是可以结合其它漏洞利用路径，来实现对计算机网络的完全接管。</p><p>遗憾的是，截止 Bleeping Computer 发稿时，微软官方都没有就此事给出任何回应。</p>   
</div>
            
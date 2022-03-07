
---
title: 'NVIDIA数字签名被盗：病毒浑水摸鱼 杀毒软件也没用'
categories: 
 - 新媒体
 - 快科技（原驱动之家）
 - 最新新闻
headimg: 'https://img1.mydrivers.com/img/20220307/s_b83e6ee5d7bb498a953eb5141c08fa91.jpg'
author: 快科技（原驱动之家）
comments: false
date: Mon, 07 Mar 2022 16:49:10 GMT
thumbnail: 'https://img1.mydrivers.com/img/20220307/s_b83e6ee5d7bb498a953eb5141c08fa91.jpg'
---

<div>   
<p>上周，攻陷了NVIDIA服务器的南美黑客组织LAPSUS$发出最后通牒，要求NVIDIA彻底开源显卡驱动，并解锁RTX 30系列挖矿限制，否则就会放出所盗取的全部资料。</p>
<p><strong>结果时至今日，黑客依然没有付诸行动，不知道是和NVIDIA谈妥了条件，还是别的什么原因。</strong></p>
<p>即便如此，黑客仍然泄露了NVIDIA的不少机密信息，包括未来GPU开发规划、DLSS源代码、71355条员工信息等等，<a class="f14_link" href="https://news.mydrivers.com/1/818/818457.htm" target="_blank">还有两个看似微不足道的数字签名证书。</a></p>
<p>这两个数字签名其实分别早在2014年9月1日、2018年7月26日就过期了，但是Windows系统下依然有效可用，结果很快就被恶意软件、病毒盯上了。</p>
<p align="center"><a href="https://img1.mydrivers.com/img/20220307/b83e6ee5d7bb498a953eb5141c08fa91.jpg" target="_blank"><img alt="NVIDIA数字签名被盗：病毒浑水摸鱼 杀毒软件也没用" h="345" src="https://img1.mydrivers.com/img/20220307/s_b83e6ee5d7bb498a953eb5141c08fa91.jpg" style="border: black 1px solid;" w="368" referrerpolicy="no-referrer"></a></p>
<p align="center"><a href="https://img1.mydrivers.com/img/20220307/d1d44adeaec74255b181ad201e41f9ff.jpg" target="_blank"><img alt="NVIDIA数字签名被盗：病毒浑水摸鱼 杀毒软件也没用" h="642" src="https://img1.mydrivers.com/img/20220307/s_d1d44adeaec74255b181ad201e41f9ff.jpg" style="border: 1px solid black;" w="536" referrerpolicy="no-referrer"></a></p>
<p>安全研究人员发现，<strong>mimikatz.exe、hamakaze.exe两个恶意程序都已经挂上了泄露的NVIDIA数字签名，伪装成驱动程序，通过了Windows系统的检查，也让杀毒软件无能为力。</strong></p>
<p>目前唯一可以防范他们的方法，就是<strong>在杀毒软件中手动添加过滤规则。</strong></p>
<p>按理说，NVIDIA应该已经联系微软，作废这两个数字签名，但可能需要一点时间，近期如果有看到这两个签名的不明文件，一定要小心。</p>
<p align="center"><a href="https://img1.mydrivers.com/img/20220307/b6ad9102e9c3484ea43266fc1ef4062c.png" target="_blank"><img alt="NVIDIA数字签名被盗：病毒浑水摸鱼 杀毒软件也没用" h="416" src="https://img1.mydrivers.com/img/20220307/s_b6ad9102e9c3484ea43266fc1ef4062c.png" style="border: black 1px solid;" w="600" referrerpolicy="no-referrer"></a></p>
<p align="center"><a href="https://img1.mydrivers.com/img/20220307/2a397f56c3bb40a7a3b175d75f6eebfc.png" target="_blank"><img alt="NVIDIA数字签名被盗：病毒浑水摸鱼 杀毒软件也没用" h="415" src="https://img1.mydrivers.com/img/20220307/s_2a397f56c3bb40a7a3b175d75f6eebfc.png" style="border: black 1px solid;" w="600" referrerpolicy="no-referrer"></a></p>
<p align="center"><a href="https://img1.mydrivers.com/img/20220307/15952d04f38d4e80995b1975234443a9.jpg" target="_blank"><img alt="NVIDIA数字签名被盗：病毒浑水摸鱼 杀毒软件也没用" h="404" src="https://img1.mydrivers.com/img/20220307/s_15952d04f38d4e80995b1975234443a9.jpg" style="border: 1px solid black;" w="600" referrerpolicy="no-referrer"></a></p>
<p align="center"><a href="https://img1.mydrivers.com/img/20220307/6dfc3bb323e44c67ac1be58e0a50a722.jpg" target="_blank"><img alt="NVIDIA数字签名被盗：病毒浑水摸鱼 杀毒软件也没用" h="362" src="https://img1.mydrivers.com/img/20220307/s_6dfc3bb323e44c67ac1be58e0a50a722.jpg" style="border: 1px solid black;" w="600" referrerpolicy="no-referrer"></a></p>

           
           
<p class="end"><img src="https://icons.mydrivers.com/news/end_article.png" referrerpolicy="no-referrer"></p> 
<div style="overflow: hidden;font-size:14px;">
           <p class="zhuanzai"><strong>如需转载请务必注明出处：快科技</strong></p>  
          <p class="url"><span style="color:#666">责任编辑：上方文Q</span><a href="javascript:;" class="jiucuo" id="leftjiucuo">文章纠错</a></p>
        </div>
        <div class="page_article" id="bnext">
 
</div>
<p class="bqian">话题标签：<a href="https://news.mydrivers.com/tag/nvidia.htm">NVIDIA</a><a href="https://news.mydrivers.com/tag/heike.htm">黑客</a><a href="https://news.mydrivers.com/tag/bingdu.htm">病毒</a>  </p>
        
</div>
            
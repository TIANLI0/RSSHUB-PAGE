
---
title: '不到400行代码 AMD工程师神优化Linux内核：性能提升多达15%'
categories: 
 - 新媒体
 - ZAKER
 - channel
headimg: 'https://cors.zfour.workers.dev/?http://zkres2.myzaker.com/202201/61f7e468b15ec04b714d9a4a_1024.jpg'
author: ZAKER
comments: false
date: Mon, 31 Jan 2022 20:18:20 GMT
thumbnail: 'https://cors.zfour.workers.dev/?http://zkres2.myzaker.com/202201/61f7e468b15ec04b714d9a4a_1024.jpg'
---

<div>   
<p>AMD 在优化 Linux 内核上取得重要一步，开源工程师提出了一种名为 PAN（Process Adaptive autoNUMA）的新功能，代码不到 400 行，但可以让 Linux 性能提升多达 15%。</p><p>据悉，PAN 是计算 AutoNUMA 扫描周期的自适应算法，该算法根据远程故障率学习和调整扫描率，通过不坚持静态阈值，该算法可以更好地响应不同的工作负载行为。</p><p>PAN 的代码不到 400 行，可以在一定程度上帮助其最新服务器硬件上的某些工作负载提高性能，而且效果很明显。</p><p>根据 AMD 提供的初步数据测试，与默认的 Linux 内核构建相比，使用 PAN 的 Linux 内核构建在 Graph500 互连 HPC 基准测试中受益高达 14.93%，NAS 基准测试速度提高了 8%，PageRank 提高了约 0.37%，以及其他一些不到 1% 的提升。</p><p>到目前为止，还没有其他内核开发人员对 Process Adaptive autoNUMA 提案发表评论。</p><p></p><div class="img_box" id="id_imagebox_0" onclick><div class="content_img_div perview_img_div"><img class="lazy opacity_0 " id="img_0" data-original="http://zkres2.myzaker.com/202201/61f7e468b15ec04b714d9a4a_1024.jpg" data-height="401" data-width="600" src="https://cors.zfour.workers.dev/?http://zkres2.myzaker.com/202201/61f7e468b15ec04b714d9a4a_1024.jpg" referrerpolicy="no-referrer"></div></div><p></p><div id="recommend_bottom"></div><div id="article_bottom"></div>  
</div>
            
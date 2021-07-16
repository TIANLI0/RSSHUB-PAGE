
---
title: '早期基准性能测试表明PHP 8.1有带来持续的改进'
categories: 
 - 新媒体
 - cnBeta
 - 最新
headimg: 'https://static.cnbetacdn.com/article/2021/0716/5ee7c809d07bfb1.png'
author: cnBeta
comments: false
date: Fri, 16 Jul 2021 06:28:56 GMT
thumbnail: 'https://static.cnbetacdn.com/article/2021/0716/5ee7c809d07bfb1.png'
---

<div>   
每次大版本更新，PHP 都会为广大开发者带来相当大的惊喜。<strong>而在 PHP 7 性能优化、以及使用新 JIT 的基础上，早期基准性能测试又揭示了 PHP 8.1 带来的持续性能优化。</strong>尽管距离 PHP 8.1 的正式发布还有几个月的时间，但我们已经见到了两大版本之间的 CLI 性能横向比较。<br>
 <p><img src="https://static.cnbetacdn.com/article/2021/0716/5ee7c809d07bfb1.png" alt="1.png" referrerpolicy="no-referrer"></p><p style="text-align: center;">截图（来自：<a href="https://www.phoronix.com/scan.php?page=news_item&px=PHP-8.1-Benchmarks-Perf-Early" target="_self">Phoronix</a>）</p><p>为初步了解 PHP 8.1 的性能改进，Phoronix 于本周早些时候，在基于 <a data-link="1" href="https://c.duomai.com/track.php?site_id=242986&euid=&t=https://amd-cpu.jd.com/" target="_blank">AMD</a> 霄龙（EPYC）7543 处理器、以及 Ubuntu Linux 操作系统的 TYAN S8036GM2NE-LE 服务器平台上展开了一番测试。</p><p><img src="https://static.cnbetacdn.com/article/2021/0716/5a36e2ba90d6a43.png" alt="2.png" referrerpolicy="no-referrer"></p><p style="text-align: center;">PHPBench 0.8.1</p><p>测试期间，Michael Larabel 选用了 7 月 14 日的 Git 代码，然后以相同的方式、从源代码展开构建，以横向比较多个不同版本的基准性能。</p><p><img src="https://static.cnbetacdn.com/article/2021/0716/b0d99548bbb9e5e.png" alt="3.png" referrerpolicy="no-referrer"></p><p style="text-align: center;">Zend bench</p><p>实测表明，在从 PHP 7 升级到 8.1 版本之后，相关基准测试项目的表现确实很是亮眼。</p><p><img src="https://static.cnbetacdn.com/article/2021/0716/cf9365a435a1541.png" alt="4.png" referrerpolicy="no-referrer"></p><p style="text-align: center;">Zend micro_bench</p><p>即使从 8.0 到 8.1，PHPBench 的基准性能也提升约 3% 。与几年前的 PHP 7.1 相比，更是有将近 33% 的领先优势。</p><p><img src="https://static.cnbetacdn.com/article/2021/0716/9942532fdaa7a0f.png" alt="5.png" referrerpolicy="no-referrer"></p><p style="text-align: center;">Total Time</p><p>在 Phoronix 自建的测试项目中，PHP 8 较 PHP 7 的改进很是明显。若加入更加缓慢的 PHP 5，8.1 版本的性能增涨就更加夸张了。</p><p><img src="https://static.cnbetacdn.com/article/2021/0716/b1599c53024a2b8.png" alt="6.png" referrerpolicy="no-referrer"></p><p style="text-align: center;">Render Test</p><p>除了性能，PHP 8.1 还带来了许多新的语言特性，从而进一步增强了这款流行脚本语言对广大开发者的吸引力。</p><p><img src="https://static.cnbetacdn.com/article/2021/0716/dca73f4ba0562d3.png" alt="7.png" referrerpolicy="no-referrer"></p><p style="text-align: center;">综合对比</p>   
</div>
            

---
title: '龙芯中科发布补丁系列 以在GCC中启用对LoongArch处理器的支持'
categories: 
 - 新媒体
 - cnBeta
 - 最新
headimg: 'https://static.cnbetacdn.com/article/2021/1129/6d870affc28ebdf.webp'
author: cnBeta
comments: false
date: Mon, 29 Nov 2021 00:58:13 GMT
thumbnail: 'https://static.cnbetacdn.com/article/2021/1129/6d870affc28ebdf.webp'
---

<div>   
<strong>龙芯中科（Loongson）不断为 LoongArch 处理器添加对 Linux 系统的支持。</strong>这个基于 MIPS64 的 ISA 现在获得了完整的补丁系列，以提交审查以便于在 GNU 编译器集合（GCC）中启用对 LoongArch 处理器的支持。<br>
 <p style="text-align:center"><img src="https://static.cnbetacdn.com/article/2021/1129/6d870affc28ebdf.webp" alt="c6s71smd.webp" referrerpolicy="no-referrer"></p><p style="text-align: left;">几个月来，Loongson 一直致力于为 Linux 内核提供 LoongArch 支持，从新的 CPU ISA 功能到复制大量现有的 MIPS64 代码并加入新的 ID，程度不一。对 Linux 内核的支持仍在进行中。</p><p style="text-align: left;">同时，他们也一直在编译器/工具链方面工作。最近，LoongArch 对 GNU Binutils 的支持被合并了，而今天发出的是一组12个补丁，用于连接GCC编译器支持。</p><p style="text-align: left;">Loongson 工程师的这个补丁系列得到了初步的支持。最初的目标是 loongarch64-linux-gnu，用于 Linux 上的 64 位 LoongArch。</p><p style="text-align: left;">尽管由于 GCC 12 最近进入了第三阶段的开发，重点是修复错误，因此 LoongArch 出现在 GCC 12 中可能已经太晚了。在这种情况下，LoongArch的支持要到2023年的GCC 13才会出现在 mainline 上。</p>   
</div>
            
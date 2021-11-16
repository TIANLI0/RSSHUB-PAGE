
---
title: 'Windows SubSystem for Linux 0.50.2发布：启用全新图标'
categories: 
 - 新媒体
 - cnBeta
 - 最新
headimg: 'https://static.cnbetacdn.com/article/2021/1116/248dcf28ccace6c.webp'
author: cnBeta
comments: false
date: Tue, 16 Nov 2021 02:30:50 GMT
thumbnail: 'https://static.cnbetacdn.com/article/2021/1116/248dcf28ccace6c.webp'
---

<div>   
Windows SubSystem for Linux（WSL2）已成为微软拥抱开源、拥抱 Linux 的重要旗帜，赢得了不少开发者和管理人员的认可和赞誉。微软定期会对 WSL2 进行更新，<strong>今天在 <a href="https://github.com/microsoft/WSL/releases/tag/0.50.2" target="_blank">GitHub</a> 和 <a href="https://www.microsoft.com/en-us/p/app/9p9tqf7mrm4r#activetab=pivot:overviewtab" target="_blank">Microsoft Store</a> 发布了 0.50.2 新版本，并启用了全新的图标。</strong><br>
 <p style="text-align:center"><img src="https://static.cnbetacdn.com/article/2021/1116/248dcf28ccace6c.webp" alt="qvtox0cx.webp" referrerpolicy="no-referrer"></p><p style="text-align: left;">Windows SubSystem for Linux 0.50.2 主要内容如下</p><blockquote style="text-align: left;"><p style="text-align: left;">● 为 Windows SubSystem for Linux 添加新的 LOGO 图标</p><p style="text-align: left;">● 在硬件支持的情况下启用硬件性能计数器[GH 4678]，增加了 USERPROFILE%\.wslconfig 选项来选择退出。</p><p style="text-align: left;">● 修复打印包含插入物的系统错误信息时的问题。</p><p style="text-align: left;">● 更新用户 tile，使其在用户的主目录而不是 C:\WINDOWS\System32 中启动。</p><p style="text-align: left;">● 恢复 /etc/wsl.conf boot.command 进程的默认信号处置，防止僵尸进程 [GH 7575]</p><p style="text-align: left;">● 对Windows 安装文件改用静态CRT</p><p style="text-align: left;">● 使用存储 API 通过 wsl.exe --install 下载发行版。</p><p style="text-align: left;">● 在 wsl.exe --install 中添加 --no-launch 选项</p><p style="text-align: left;">● 对本地化字符串的许多更新。</p><p style="text-align: left;">● 改用更新的 tar 来导入/导出WSL2发行版。</p><p style="text-align: left;">● 更新到官方的22000 sdk</p><p style="text-align: left;">● 剥离用于发布构建的Linux符号</p><p style="text-align: left;">● 更新 Linux 内核到 5.10.74.3</p><p style="text-align: left;">  ○ 更新到上游稳定内核版本 5.10.74</p><p style="text-align: left;">  ○ 启用 BPF 类型格式（CONFIG_DEBUG_INFO_BTF），供eBPF工具使用 [GH 7437]</p><p style="text-align: left;">  ○ 将Dxgkrnl版本改为2110</p><p style="text-align: left;">     → 实现了 D3DKMTShareObjectWithHost</p><p style="text-align: left;">     → 修正了结果的QueryStatistics VM总线对齐问题</p><p style="text-align: left;">     → 实现了D3DKMTCreateSyncFile</p><p style="text-align: left;">     → 解决上游提交的反馈问题</p><p style="text-align: left;">     → 将 d3dkmthk 移至 include/uapi/misc。</p><p style="text-align: left;">     → 用 __u32 替换了 u32，用 __u64 替换了 u64</p><p style="text-align: left;">     → 在枚举器值前面添加了"_"，以支持包括 WDK 和 Linux 头文件。</p><p style="text-align: left;">     → 删除了用户模式可见结构中的孔，以便与 32 位应用程序兼容</p><p style="text-align: left;">     → 在用户模式可见结构中用定义的u64取代了用户模式应用的指针</p><p style="text-align: left;">     → 修复GCC版本超过8.1时的构建失败 [GH 7558]</p><p style="text-align: left;">  ○ 为Dxgkrnl的使用启用缓冲区共享和同步文件框架（CONFIG_DMA_SHARED_BUFFER, CONFIG_SYNC_FILE）。</p></blockquote>   
</div>
            

---
title: '适用于苹果 M1 的 Asahi Linux 发布首个 Alpha 版本'
categories: 
 - 编程
 - 开源中国
 - 资讯
headimg: 'https://oscimg.oschina.net/oscnet/up-3df4924a34d4efdb6843ada5a08059037c3.png'
author: 开源中国
comments: false
date: Tue, 22 Mar 2022 07:03:00 GMT
thumbnail: 'https://oscimg.oschina.net/oscnet/up-3df4924a34d4efdb6843ada5a08059037c3.png'
---

<div>   
<div class="content">
                                                                                            <p>Asahi Linux 宣布推出首个公开 Alpha 版本，“请记住，这仍然是一个非常早期的 alpha 版本。它适用于开发人员和高级用户；如果你决定安装它，我们希望你能够通过提交详细的错误报告和帮助调试问题来帮助我们。也就是说，我们欢迎大家试一试 - 只是可能会有点粗糙。”</p> 
<p>此版本带来了一些未来的兼容性功能。这意味着安装它的用户将能够通过简单地升级他们的包来跟上所有未来的改进，而无需重新安装。确保将你的 macOS 更新到 12.3 或更高版本，然后只需在 macOS 中打开终端并粘贴以下命令：</p> 
<div> 
 <pre>curl https://alx.sh | sh</pre> 
</div> 
<p style="margin-left:0px; margin-right:0px; text-align:start"><img height="272" src="https://oscimg.oschina.net/oscnet/up-3df4924a34d4efdb6843ada5a08059037c3.png" width="700" referrerpolicy="no-referrer"></p> 
<p style="margin-left:0px; margin-right:0px; text-align:start"><strong><span style="color:#000000">系统要求</span></strong></p> 
<ul> 
 <li>M1、M1 Pro 或 M1 Max 机器（Mac Studio 除外）</li> 
 <li>macOS 12.3 或更高版本，以管理员用户身份登录</li> 
 <li>至少 53GB 的可用磁盘空间（桌面安装） 
  <ul> 
   <li>Asahi Linux Desktop 需要 15GB，但安装程序会在 macOS 中保留额外的 38GB 磁盘空间，以避免破坏 macOS 更新。如果要禁用此检查，可在出现提示时启用 expert mode。</li> 
  </ul> </li> 
 <li>有效的互联网连接 
  <ul> 
   <li>安装程序将下载 700MB ~ 4GB 的数据，具体取决于你选择的操作系统。</li> 
  </ul> </li> 
</ul> 
<p>值得注意的是，此版本没有提供 GPU 支持，也没有 DisplayPort、Thunderbolt 或 HDMI 端口；未使用 M1 芯片上的神经引擎；并且不支持 Camera 和 Touch Bar。即将全面支持 USB3、扬声器和显示控制器。 </p> 
<p style="margin-left:0px; margin-right:0px; text-align:start"><strong>Known bugs</strong></p> 
<ul> 
 <li>如果 Wi-Fi 不起作用，看尝试在网络管理菜单中将其关闭再打开</li> 
 <li>如果耳机插孔不工作或只有一个通道工作，可尝试重新启动。有一个 flakiness issue。</li> 
</ul> 
<p style="margin-left:0px; margin-right:0px; text-align:start"><strong>Known broken applications</strong></p> 
<p>Asahi Linux 内核被编译为使用 16K pages，但一些 Linux 软件在<a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2FAsahiLinux%2Fdocs%2Fwiki%2FSoftware-known-to-have-issues-with-16k-page-size" target="_blank">运行 16K pages 时会出现问题</a>。最为显着的是：</p> 
<ul> 
 <li>Chromium（needs volunteer to fix）</li> 
 <li>Emacs（fix committed, not released）</li> 
 <li>任何使用 jemalloc 的东西（例如 Arch Linux ARM 中的 Rust）</li> 
 <li>使用 libunwind 的任何东西（fix committed, not released）</li> 
</ul> 
<blockquote> 
 <p>“<span style="color:#2c2c2c">希望此版本将有助于激励上游项目解决这些问题并正确支持所有 ARM64 page sizes（64K、16K 和 4K）。16K 在某些工作负载下提供了高达 20% 左右的显着性能提升，所以这是很值得的。</span></p> 
 <p><span style="color:#2c2c2c">有一类软件可能永远不会支持 16K page size：某些仿真器和兼容层，包括 <a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2FFEX-Emu%2FFEX" target="_blank">FEX</a>。Android 也会受到影响，以防有一天有人想尝试原生地运行它。对于这些工具的用户，我们将在未来提供 4K page size 的内核，一旦使之成为可能的内核更改准备好用于上游。</span>”</p> 
</blockquote> 
<p>公告还指出，Apple Silicon 机器上安装的所有操作系统都需要 Apple 提供的某些组件。由于 Asahi Linux 开发团队不能自己重新分发这些，安装程序将从 Apple 的公共 CDN 下载它们。“将来，我们将提供一个选项，允许将其缓存到本地或 USB 驱动器，这样你就可以进行离线安装。 ”</p> 
<p>更多详情可查看：<a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fasahilinux.org%2F2022%2F03%2Fasahi-linux-alpha-release%2F" target="_blank">https://asahilinux.org/2022/03/asahi-linux-alpha-release/</a></p> 
<p> </p>
                                        </div>
                                      
</div>
            
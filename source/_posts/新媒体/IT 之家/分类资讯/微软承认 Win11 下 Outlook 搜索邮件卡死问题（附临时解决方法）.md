
---
title: '微软承认 Win11 下 Outlook 搜索邮件卡死问题（附临时解决方法）'
categories: 
 - 新媒体
 - IT 之家
 - 分类资讯
headimg: 'https://img.ithome.com/newsuploadfiles/2021/8/01a945e1-116d-410f-b845-41d54b165daf.png'
author: IT 之家
comments: false
date: Sun, 05 Dec 2021 13:58:03 GMT
thumbnail: 'https://img.ithome.com/newsuploadfiles/2021/8/01a945e1-116d-410f-b845-41d54b165daf.png'
---

<div>   
<p data-vmark="36c4"><a class="s_tag" href="https://www.ithome.com/" target="_blank">IT之家</a> 12 月 5 日消息，据 mspoweruser 报道，最近<span class="accentTextColor">升级到 <a class="s_tag" href="https://win11.ithome.com/" target="_blank">Windows 11</a> 的 Outlook 用户遇到了无法搜索旧电子邮件的问题</span>，在执行搜索时客户端有时会冻结。</p><p data-vmark="f3cf"><img src="https://img.ithome.com/newsuploadfiles/2021/8/01a945e1-116d-410f-b845-41d54b165daf.png" title="微软承认 Win11 下 Outlook 搜索邮件卡死问题（附临时解决方法）" referrerpolicy="no-referrer"></p><p data-vmark="4392">微软已经承认了这个问题，并表示：电子邮件和其他项目本地存储在 PST 或 OST 文件（如 POP 和 IMAP 账户）中的任何账户都会出现此问题，对于 Exchange 和 Microsoft 365 托管账户，此问题将影响离线搜索本地存储的 OST 文件中的数据。</p><p data-vmark="bbac"><img src="https://img.ithome.com/newsuploadfiles/2021/12/ba7bbcbc-73f3-40d8-97e1-25f88a51b276.png" w="1056" h="318" title="微软承认 Win11 下 Outlook 搜索邮件卡死问题（附临时解决方法）" width="1056" height="247" referrerpolicy="no-referrer"></p><p data-vmark="8af2">IT之家了解到，这个问题似乎是微软在升级到 Windows 11 时删除了 Windows 搜索索引文件。<span class="accentTextColor">受影响的客户端包括 Outlook for Microsoft 365、Outlook 2019 和 Outlook 2016</span>。</p><p data-vmark="7734">Windows 将自动重建索引，但可能需要一些时间。要查看该进程的状态，可以在 Outlook 中选择“搜索”框。

在功能区上，选择搜索工具，然后选择索引状态。</p><p data-vmark="7d8b"><img src="https://img.ithome.com/newsuploadfiles/2021/12/396b01ca-8075-4045-a2a2-46cf6e5ca77f.png" w="322" h="130" alt="Outlook has finished indexing all of your items" title="微软承认 Win11 下 Outlook 搜索邮件卡死问题（附临时解决方法）" width="322" height="130" referrerpolicy="no-referrer"></p><p data-vmark="b4e9">如果想完全绕过这个问题，临时的解决方案是告诉 Outlook 你想使用 Outlook 的内部搜索而不是使用 Windows 搜索索引。</p><h2 data-vmark="8495">临时解决方案：</h2><ul class=" list-paddingleft-2"><li><p data-vmark="3c3a">Win + R 打开“运行”，输入 regedit 进入注册表编辑器。</p></li><li><p data-vmark="df8c">在注册表中找到这一子项：</p></li></ul><pre class="brush:javascript;toolbar:false ai-word-checked">HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows</pre><ul class=" list-paddingleft-2"><li><p data-vmark="6df4">编辑 > 新建 > 项（K），将其重命名为 Windows Search。</p></li><li><p data-vmark="607d">在 Windows Search 项下新建 DWORD 值，命名为 PreventIndexingOutlook。</p></li><li><p data-vmark="9324">打开 PreventIndexingOutlook，将其数值修改为 1。</p></li><li><p data-vmark="79f1">关闭注册表，重新启动 Outlook 以使其生效。</p></li></ul><p data-vmark="51b0">如果想重新让 Outlook 搜索使用 Windows 搜索索引，则将 PreventIndexingOutlook 的值改为 0 即可。</p>
          
</div>
            
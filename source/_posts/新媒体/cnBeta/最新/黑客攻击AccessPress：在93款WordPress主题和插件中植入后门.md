
---
title: '黑客攻击AccessPress：在93款WordPress主题和插件中植入后门'
categories: 
 - 新媒体
 - cnBeta
 - 最新
headimg: 'https://static.cnbetacdn.com/article/2022/0122/4bb2607d5d55e5c.webp'
author: cnBeta
comments: false
date: Sat, 22 Jan 2022 02:24:42 GMT
thumbnail: 'https://static.cnbetacdn.com/article/2022/0122/4bb2607d5d55e5c.webp'
---

<div>   
<strong>通过庞大的供应链攻击，黑客成功利用后门破坏了 93 个 WordPress 主题和插件，使其能够完全访问网站。</strong>黑客总共破坏了属于 AccessPress 的 40 个主题和 53 个插件，AccessPress 是一家 WordPress 插件开发商，在超过 36 万个活跃网站中使用。<br>
 <p style="text-align:center"><img src="https://static.cnbetacdn.com/article/2022/0122/4bb2607d5d55e5c.webp" alt="r9ofcdfk.webp" referrerpolicy="no-referrer"></p><p style="text-align: left;">Jetpack 的研究人员率先发现了这次攻击，该公司是 WordPress 网站安全和优化工具的创建者，他们发现主题和插件中被添加了一个 PHP 后门。Jetpack 认为，一个外部威胁者攻破了 AccessPress 网站，破坏了该软件并感染了更多的 WordPress 网站。</p><p style="text-align: left;">一旦管理员在他们的网站上安装了被入侵的 AccessPress 产品，行为者就会在主主题目录中添加一个新的“initial.php”文件，并将其纳入主“function.php”文件。这个文件包含一个 base64 编码的有效载荷，将 webshell 写入“./wp-includes/vars.php”文件中。</p><p style="text-align: left;">恶意代码通过解码有效载荷并将其注入“vars.php”文件来完成后门的安装，本质上是让威胁者对受感染网站进行远程控制。检测这种威胁的唯一方法是使用核心文件完整性监控解决方案，因为恶意软件会删除“initial.php”文件的投放器以掩盖其踪迹。</p>   
</div>
            

---
title: 'Python安装库太慢？配置好这个速度飞起'
categories: 
 - 社交媒体
 - 简书
 - 首页
headimg: 'https://upload-images.jianshu.io/upload_images/13723999-e5b71766a56d689e.png'
author: 简书
comments: false
date: Invalid Date
thumbnail: 'https://upload-images.jianshu.io/upload_images/13723999-e5b71766a56d689e.png'
---

<div>   
<p>经常听到初学python的小伙伴在抱怨，python安装第三方库太慢，很容易失败报错，如果安装pandas、tensorflow这种体积大的库，简直龟速。</p>
<h3>为什么pip会很慢？</h3>
<p>先来了解下pip，pip是一个非常流行的python包管理工具，在命令行中只需要输入pip install package_name，就可以自动安装第三方库。然而pip是从pypi中下载库文件的，pypi是python官方第三方库的仓库，它用的是国外的服务器，下载速度自然很慢。</p>
<p>所以不是pip慢，而是pypi慢。</p>
<p>有一种方法可以解决安装慢的问题，那就是通过国内镜像网站下载。镜像网站完整复制pypi的内容，放到国内的服务器上。这样你只需要把pip的下载源修改为镜像站，就能享受流畅快速的pip安装功能了。</p>
<h3>临时配置</h3>
<p>简单的举个例子，用清华镜像源来安装第三方库，在命令行输入：</p>
<pre><code class="python">pip install -i https://pypi.tuna.tsinghua.edu.cn/simple package_name
</code></pre>
<p>以安装pandas来说明一下，不替换镜像源情况下：</p>
<pre><code class="python">pip install pandas
</code></pre>
<p>替换为清华镜像源：</p>
<pre><code class="python">pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pandas
</code></pre>
<p>清华pypi的镜像源每五分钟更新一次，大而全，推荐大家使用，下面是网址：</p>
<pre><code class="python">https://pypi.tuna.tsinghua.edu.cn/simple
</code></pre>
<p>国内还有其他镜像源可供选择：</p>
<pre><code class="python">豆瓣
http://pypi.douban.com/simple/
阿里　　 
http://mirrors.aliyun.com/pypi/simple/ 　　
中国科学技术大学
http://pypi.mirrors.ustc.edu.cn/simple/ 　　
</code></pre>
<h3>永久配置</h3>
<p>上面的用法是临时配置，也就是说每次安装库时必须带上镜像源的网址。其实这样不太方便，若想省力气，那就要永久配置镜像源，配置好后只要输入<code>pip install package_name</code>，就可以快速安装库了。</p>
<p>永久配置镜像源也简单，分为两种方法，自动和手动。</p>
<p>自动配置，以配置清华源为例，在命令行输入：</p>
<pre><code class="python">pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
</code></pre>
<p>执行后就配置好了。</p>
<p>手动配置，windows下，直接在user目录中创建一个pip目录，再新建文件pip.ini。（例如：C:\Users\zhu\pip\pip.ini）<br>
接着打开pip.ini文件，复制粘贴以下内容并保存。</p>
<pre><code class="python">[global]
 index-url = https://pypi.tuna.tsinghua.edu.cn/simple
</code></pre>
<p>配置成功。</p>
<h3>镜像网站的好处</h3>
<p>国内的这些镜像网站拥有非常多的开源工具，不光是pypi，你还可以在里面下载mysql、anaconda、ubuntu、nodejs等主流软件，速度杠杠的。<br>
以下是中科大镜像站：<a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmirrors.ustc.edu.cn%2F" target="_blank">https://mirrors.ustc.edu.cn/</a></p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1867" data-height="888"><img data-original-src="//upload-images.jianshu.io/upload_images/13723999-e5b71766a56d689e.png" data-original-width="1867" data-original-height="888" data-original-format="image/png" data-original-filesize="202704" src="https://upload-images.jianshu.io/upload_images/13723999-e5b71766a56d689e.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
  
</div>
            
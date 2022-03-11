
---
title: '写给工程师的 Ubuntu 20.04 最佳配置指南'
categories: 
 - 社交媒体
 - 简书
 - 首页
headimg: 'https://upload-images.jianshu.io/upload_images/1167421-f5376e319539bdf6.png'
author: 简书
comments: false
date: Invalid Date
thumbnail: 'https://upload-images.jianshu.io/upload_images/1167421-f5376e319539bdf6.png'
---

<div>   
<p>最近 Ubuntu 发布了 20.04 LTS 版本，我也在第一时间安装体验。由于各种 Linux 发行版本并不像 MacOS、Windows 一样开箱即用，因此需要做很多配置。每次配置都需要查阅各种资料，虽然网络上有很多配置文章，但基本上都会存在一些问题：</p>
<ol>
<li>只教怎么做，不说为什么；</li>
<li>文档陈旧，不更新；</li>
<li>内容缺失，不丰富；......</li>
</ol>
<p>因此我希望整理一份最佳配置指南，除了记录需要做什么，还会说明背后的原理和技术背景。一方面方便自己今后查阅，另一方面也想将这份指南分享给大家，并和大家一起逐步完善它。<strong>所以，这是一份会持续更新的、有实操有原理、内容丰富的最佳配置指南。</strong></p>
<blockquote>
<p>关注公众号 <strong>BaronTalk</strong>，回复 Ubuntu 即可下载最新的 PDF 版本配置文档。</p>
</blockquote>
<h2>一. 系统配置</h2>
<h3>1. 关闭 sudo 密码</h3>
<p>为了避免每次使用 sudo 命令时都输入密码，我们可以将密码关闭。操作方法：</p>
<p>第一步：终端输入命令<code>sudo visudo</code>，打开 visudo；</p>
<p>第二步：找到 <code>%sudo ALL=(ALL:ALL) ALL</code> 这一行修改为<code>%sudo ALL=(ALL:ALL) NOPASSWD:ALL</code></p>
<h3>2. 修改软件源</h3>
<p>Ubuntu 默认的软件源是境外的，速度上会有些问题，我们可以在「Software & Updates」(软件和更新)中选择国内的镜像。</p>
<br>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="2000" data-height="944"><img data-original-src="//upload-images.jianshu.io/upload_images/1167421-f5376e319539bdf6.png" data-original-width="2000" data-original-height="944" data-original-format="image/png" data-original-filesize="352632" src="https://upload-images.jianshu.io/upload_images/1167421-f5376e319539bdf6.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<h3>3. 更新系统</h3>
<pre><code class="Bash"># 更新本地报数据库
sudo apt update

# 更新所有已安装的包（也可以使用 full-upgrade）
sudo apt upgrade

# 自动移除不需要的包
sudo apt autoremove
</code></pre>
<p>这里补充几个常用的清理命令：</p>
<table>
<thead>
<tr>
<th>命令</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr>
<td>apt autoclean</td>
<td>将已删除软件包的.deb安装文件从硬盘中删除</td>
</tr>
<tr>
<td>apt clean</td>
<td>同上，但会把已安装的软件包的安装包也删除掉</td>
</tr>
<tr>
<td>apt autoremove</td>
<td>删除为了满足其他软件包的依赖而安装，但现在不再需要的软件包</td>
</tr>
<tr>
<td>apt remove [软件包名]</td>
<td>删除已安装的软件包（保留配置文件）</td>
</tr>
<tr>
<td>apt --purge remove [软件包名]</td>
<td>删除已安装包（不保留配置文件）</td>
</tr>
</tbody>
</table>
<h3>4. 高分屏适配</h3>
<p>默认情况高分屏下 UI 元素显得过小，因此需要调整界面的缩放比例。Ubuntu20.04 默认是 GNOME 桌面，GNOME 可以在 <strong>Settings>Displays（设置>显示）</strong>中开启 HiDPI 支持，以整数倍来调整屏幕比例。也可以通过如下命令的来设置：</p>
<pre><code class="Bash"># scaling-factor 仅能设置为整数 1=100%，2=200% 3=300% ......
gsettings set org.gnome.desktop.interface scaling-factor 2
</code></pre>
<p>整数倍的缩放设置，在部分设备上 UI 元素要么显得过大，要么显得过小，因此我们需要进一步调整。</p>
<p>使用下面的命令查看你 Linux 设备上的 Window System（图形接口协议），通常是 Wayland/X11</p>
<pre><code class="Bash">echo $XDG_SESSION_TYPE
</code></pre>
<p><strong>Wayland</strong></p>
<p>如果是 wayland，使用下面的命令启动实验性的非整数倍缩放功能。</p>
<pre><code class="Bash">gsettings set org.gnome.mutter experimental-features "['scale-monitor-framebuffer']"
</code></pre>
<p>之后再次打开 <strong>Settings>Displays</strong>，就可以选择非整数倍缩放（125%、150%、175%）。Ubuntu20.04 已经在 <strong>Settings>Displays</strong> 中提供了图形化的界面来开启实验性的非整数倍的缩放功能，因此无需通过上面的命令来开启。</p>
<blockquote>
<p>我试验下来，这种方式无法在我的设备上正常设置非整数倍缩放。我判断是因为 Ubuntu20.04 默认的 Window System 是 X11 而不是 Wayland，如果你的设备上是 Wayland，应该是可以正常设置的。或者你在登陆桌面系统时选择 Ubuntu On Wayland 理论上也是可以的。</p>
</blockquote>
<p><strong>X11</strong></p>
<p>对于 X11，我们可以同时使用 scaling-factor 和 xrandr 来实现非整数倍缩放，这可以使 TTF 字体被正确缩放，防止单独使用 xrandr 时出现的模糊现象。你可以使用 gsettings 或者在 <strong>Settings>Displays</strong> 中来指定放大系数，并用 xrandr 指定缩小系数。</p>
<p>首先将界面缩放系数设置为「UI看起来太大」的最小系数，通常是 2（200%），如果不够大就继续尝试 3 甚至更大的系数。然后使用 xrandr 来设置缩小系数，我自己设置的是 1.25，如果 UI 看起来太大就提高系数，反之就降低系数。命令如下：</p>
<pre><code class="Bash">xrandr --output DP-4 --scale 1.25x1.25
</code></pre>
<p><strong>使用上述命令你可能会遇到 <code>warning: output DP-4 not founnd; gnoring</code>的提示，或者执行命令后界面无任何变化。此时你需要执行 <code>xrandr</code> 命令来查看你的 output 参数（也就是当前显示接口的名称，日志中显示 connected 的就是），比如我设备上的是 DP-4。</strong></p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1536" data-height="1040"><img data-original-src="//upload-images.jianshu.io/upload_images/1167421-88c748c8a956c9ec.png" data-original-width="1536" data-original-height="1040" data-original-format="image/png" data-original-filesize="235727" src="https://upload-images.jianshu.io/upload_images/1167421-88c748c8a956c9ec.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<p>正确执行完命令后可能会出现 UI 元素过小的情况，回去 <strong>Settings>Displays</strong> 中看看，是不是整数倍缩放被还原成了 100%，如果是重新选择合适的缩放比例即可（比如 200%）。</p>
<p>重启后 xrandr 的设置会失效，我们可以设置个启动自动执行的脚本，比如 start-service.sh ：</p>
<pre><code class="Bash"># start-service.sh
#!/bin/bash
xrandr --output DP-4 --scale 1.25x1.25
exit 0
</code></pre>
<p>接着给 start-service.sh 授予执行权限</p>
<pre><code class="Bash">sudo chmod +x start-service.sh
</code></pre>
<p>然后在 Ubuntu 中搜索「sartup Applications」(启动应用程序) ，将脚本添加进去：</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1114" data-height="716"><img data-original-src="//upload-images.jianshu.io/upload_images/1167421-22a8ada6c2727187.png" data-original-width="1114" data-original-height="716" data-original-format="image/png" data-original-filesize="93608" src="https://upload-images.jianshu.io/upload_images/1167421-22a8ada6c2727187.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<p>至此就能完美的支持 4K 屏显示了。</p>
<h3>5. 安装 Python2</h3>
<p>Ubuntu20.04 自带了 python3，但是某些第三方工具或者脚本还是用的 python2，因此我们需要自行安装</p>
<pre><code class="Bash">apt install python
</code></pre>
<h3>6. 安装 Git</h3>
<pre><code class="Bash">apt install git
</code></pre>
<h3>7. 中文输入法</h3>
<p>由于搜狗输入法目前还不支持Ubuntu20.04，加之其对高分屏支持不太友好，因此不再折腾选择了 ibus-libpinyin。</p>
<pre><code class="Bash"># 安装
sudo apt install ibus-libpinyin 
sudo apt install ibus-clutter
</code></pre>
<p>接着在应用程序中找到「Language Support」(语言支持)，更改「Keyboard input method system」(键盘输入法系统)为「IBUS」。重启系统，然后在<strong>Settings>Region & Language>Input Sources（设置>区域与语言>输入源）</strong>中新增「Chinese(Intelligent Pinyin)」(中文(智能拼音))就可以使用中文输入法了。</p>
<h2>二. 打造你的命令行工具(Terminator && ZSH)</h2>
<h4>1. 安装 Terminnator</h4>
<p>如果你用惯了 Mac 平台下的 iTerm2，一定会对它的分屏功能恋恋不忘，然而 Ubuntu 自带的 Terminal 并不好用。好在 Linux 下有各种开源 Terminal，个人比较推荐 Terminator，强大如 iTerm2，一样支持分屏。</p>
<pre><code class="Bash"># 安装
sudo add-apt-repository ppa:gnome-terminator
sudo apt update
sudo apt install terminator
</code></pre>
<p>Terminator 默认的界面比较丑，不过配置灵活，大家可以根据喜好自行调整。</p>
<h4>2. 配置 Shell（安装 zsh 和 oh-my-zsh）</h4>
<p>搞定了 Terminal，接下来配置 Shell。执行下面的命令：</p>
<pre><code class="Bash">cat /etc/shells
</code></pre>
<p>可以看到 Ubuntu 已经内置了各种 Shell：</p>
<pre><code class="Bash">/bin/bash
/bin/csh
/bin/dash
/bin/ksh
/bin/sh
/bin/tcsh
</code></pre>
<p>市面上常用的 Linux 发行版本通常默认使用的 Shell 都是 bash，但 zsh 要远比 bash 强大的多。</p>
<pre><code class="Bash"># 安装 zsh
apt install zsh

# 将 zsh 设置为系统默认 shell
sudo chsh -s /bin/zsh
</code></pre>
<p>不过 zsh 的配置太复杂，好在有人开发了 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Frobbyrussell%2Foh-my-zsh" target="_blank">oh-my-zsh</a>，可以让我们更方便的配置 zsh。</p>
<pre><code class="Bash"># 自动安装，如果你没安装 git 需要先安装 git
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh

# 或者也可以选择手动安装
git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
</code></pre>
<p>重启 Terminal 你就能发现变化。</p>
<h4>3. ZSH 配置</h4>
<p>zsh 的配置主要集中在 ~/.zshrc 文件里，比如我们可以给常用命令配置别名：</p>
<pre><code class="Bash">alias cls='clear'
alias ll='ls -l'
alias la='ls -a'
alias vi='vim'
alias grep="grep --color=auto"
</code></pre>
<p>或者选择 zsh 的主题</p>
<pre><code class="Bash">ZSH_THEME="robbyrussell"
</code></pre>
<p>oh-my-zsh 内置了很多主题，对应的主题文件存放在 ~/.oh-my-zsh/themes 目录下，你可以根据自己的喜好选择或者编辑主题。</p>
<h4>4. ZSH 插件安装</h4>
<p>oh-my-zsh 还支持各种插件，存放在 ~/.oh-my-zsh/plugins 目录下。这里推荐几款：</p>
<p><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Fwting%2Fautojump" target="_blank">autojump</a>：快速切换目录插件</p>
<pre><code class="Bash"># 安装
apt install autojump

# 使用
j Document/
</code></pre>
<p><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Fzsh-users%2Fzsh-autosuggestions" target="_blank">zsh-autosuggestions</a>：命令行命令键入时的历史命令建议插件</p>
<pre><code class="Bash"># 安装
git clone https://github.com/zsh-users/zsh-autosuggestions $&#123;ZSH_CUSTOM:-~/.oh-my-zsh/custom&#125;/plugins/zsh-autosuggestions
</code></pre>
<p><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Fzsh-users%2Fzsh-syntax-highlighting" target="_blank">zsh-syntax-highlighting</a>：命令行语法高亮插件</p>
<pre><code class="Bash"># 安装
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $&#123;ZSH_CUSTOM:-~/.oh-my-zsh/custom&#125;/plugins/zsh-syntax-highlighting
</code></pre>
<p>插件安装好后需要在 ~/.zshrc 文件里配置后方可使用，配置如下：</p>
<pre><code class="Bash"># 打开 ~/.zshrc 文件，找到如下这行配置代码，在后面追加插件名
plugins=(其他插件名 autojump zsh-autosuggestions zsh-syntax-highlighting)
</code></pre>
<h4>5. 有趣的命令行小玩具</h4>
<p>配置好Terminator 和 ZSH 后，我们还可以为命令行添加些有趣的小玩具。</p>
<h5>CMatrix(<a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Fabishekvashok%2Fcmatrix" target="_blank">https://github.com/abishekvashok/cmatrix</a>)</h5>
<blockquote>
<p>终端黑客帝国屏保</p>
</blockquote>
<pre><code class="Bash"># 安装
sudo apt install cmatrix

# 运行（加上 -lba 参数看起来更像电影，加上 -ol 参数起来更像 Win/Mac 的屏保）
cmatrix
</code></pre>
<p>效果图：</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="564" data-height="340"><img data-original-src="//upload-images.jianshu.io/upload_images/1167421-0554d1a7c3067c03.png" data-original-width="564" data-original-height="340" data-original-format="image/png" data-original-filesize="22279" src="https://upload-images.jianshu.io/upload_images/1167421-0554d1a7c3067c03.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<h5>Steam Locomotive(<a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Fmtoyoda%2Fsl" target="_blank">https://github.com/mtoyoda/sl</a>)</h5>
<blockquote>
<p>终端小火车动效</p>
</blockquote>
<pre><code class="Bash"># 安装
sudo apt install sl

# 运行
sl
</code></pre>
<p>效果图：</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="688" data-height="472"><img data-original-src="//upload-images.jianshu.io/upload_images/1167421-9f0defe77bad2e40.png" data-original-width="688" data-original-height="472" data-original-format="image/png" data-original-filesize="56615" src="https://upload-images.jianshu.io/upload_images/1167421-9f0defe77bad2e40.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<h5>Screenfetch(<a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2FKittyKatt%2FscreenFetch" target="_blank">https://github.com/KittyKatt/screenFetch</a>)</h5>
<blockquote>
<p>The Bash Screenshot Information Tool，用于在终端显示系统信息及 ASCII 化的 Linux 发行版图标</p>
</blockquote>
<pre><code class="Bash"># 安装
sudo apt install screenfetch

# 运行
screenfetch
</code></pre>
<p>效果图：</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1364" data-height="680"><img data-original-src="//upload-images.jianshu.io/upload_images/1167421-16779837e38eadf0.png" data-original-width="1364" data-original-height="680" data-original-format="image/png" data-original-filesize="172907" src="https://upload-images.jianshu.io/upload_images/1167421-16779837e38eadf0.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<h2>三. 软件安装</h2>
<h3>1. 安装Clash(搭个tizi，你懂的)</h3>
<p>第一步：到 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2FDreamacro%2Fclash%2Freleases" target="_blank">https://github.com/Dreamacro/clash/releases</a> 下载最新的 Linux 版 Clash，例如：<a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2FDreamacro%2Fclash%2Freleases%2Fdownload%2Fv0.19.0%2Fclash-linux-amd64-v0.19.0.gz" target="_blank">clash-linux-amd64-v0.19.0.gz</a>。解压后得到一个可执行文件 clash-linux-amd64-v0.19.0：</p>
<pre><code class="Bash">tar -zxvf clash-linux-amd64-v0.19.0.gz
</code></pre>
<p>第二步：使用 mv 命令移动到  /usr/local/bin/clash：</p>
<pre><code class="Bash">sudo mv clash-linux-amd64-v0.19.0 /usr/local/bin/clash
</code></pre>
<p>第三步：终端输入 sudo chmod +x /usr/local/bin/clash 添加执行权限；</p>
<pre><code class="Bash">sudo chmod +x /usr/local/bin/clash
</code></pre>
<p>第四步：终端执行 clash 命令，运行 clash；</p>
<pre><code class="Bash"># 运行 clash
clash
</code></pre>
<p>此时会在 /home/&#123;用户ID&#125;/.config/clash 目录下生成两个文件：config.yaml 和 Country.mmdb；编辑 config.yaml 文件，配置代理服务器信息和规则，部分商家会提供yaml文件，下载后 copy 过来即可；</p>
<p>重启 clash（关闭并重新打开终端，执行 clash 命令）以加载更新后的配置文件；</p>
<p>保持 clash 运行，打开浏览器访问 clash.razord.top 进行策略配置、选择代理线路等等（可能需要根据提示输入IP、端口和口令，具体内容可在 config.yaml 中查看；</p>
<p>继续保持 clash 运行，在系统网络设置中设置手动代理 <strong>Settings>Network>Network Proxy>Manual（设置>网络>代理>手动）</strong>，配置信息参考 config.yaml 或者启动 clash 时终端输出的日志。此时就可以通过 clash 访问网络了。</p>
<blockquote>
<p>按照前面的方式配置好后，每次系统启动时都需要打开终端，执行 clash 命令，并且终端不可以关闭，否则整个 clash 进程就结束了。如果不想一直保持终端打开，可使用 nohup clash 命令启动后台运行。或者希望开机自启动 clash，可将 <code>nohup clash</code> 这段命令加入到前面提到的 start-service.sh 脚本的<strong>最后</strong>。</p>
</blockquote>
<h3>2. 安装<a href="https://links.jianshu.com/go?to=https%3A%2F%2Ftypora.io%2F" target="_blank">Typroa</a>(开源MarkDown编辑器)</h3>
<pre><code class="Bash"># or run:
# sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -

# add Typora's repository
sudo add-apt-repository 'deb https://typora.io/linux ./'
sudo apt update

# install typora
sudo apt install typora
</code></pre>
<h3>3. JetBrains 全家桶</h3>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="812" data-height="1278"><img data-original-src="//upload-images.jianshu.io/upload_images/1167421-7e13d0fa9089e998.png" data-original-width="812" data-original-height="1278" data-original-format="image/png" data-original-filesize="233652" src="https://upload-images.jianshu.io/upload_images/1167421-7e13d0fa9089e998.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<p>安装 JetBrains 的 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fwww.jetbrains.com%2Ftoolbox-app%2F" target="_blank">ToolBox App</a> 后可以无脑一键安装旗下各种 IDE，包括 Android Studio。</p>
<h3>4. 其它应用程序安装</h3>
<p>对于官网已经提供了 Ubuntu 版本 .deb 安装文件的，可在官网下载 .deb 安装文件后，执行下面的命令安装：</p>
<pre><code class="Bash"># 安装
sudo apt install ./<file>.deb
</code></pre>
<p>如果你是较早的 Linux 发行版本，需要使用下面的命令安装（下同）：</p>
<pre><code class="Bash">sudo dpkg -i <file>.deb
sudo apt-get install -f # Install dependencies
</code></pre>
<table>
<thead>
<tr>
<th>应用</th>
<th>下载地址</th>
</tr>
</thead>
<tbody>
<tr>
<td>Chrome</td>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fwww.google.com%2Fchrome" target="_blank">https://www.google.com/chrome</a></td>
</tr>
<tr>
<td>VS Code</td>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fcode.visualstudio.com" target="_blank">https://code.visualstudio.com</a></td>
</tr>
<tr>
<td>ZOOM</td>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fzoom.us%2Fdownload%23client_4meeting" target="_blank">https://zoom.us/download#client_4meeting</a></td>
</tr>
<tr>
<td>WPS</td>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fwww.wps.cn%2Fproduct%2Fwpslinux" target="_blank">https://www.wps.cn/product/wpslinux</a></td>
</tr>
<tr>
<td>网易云音乐</td>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmusic.163.com%2F%23%2Fdownload" target="_blank">https://music.163.com/#/download</a></td>
</tr>
<tr>
<td>百度网盘</td>
<td>百度网盘...？ 这垃圾玩意儿你装它干啥！！！</td>
</tr>
<tr>
<td>...</td>
<td>...</td>
</tr>
</tbody>
</table>
<p>注：部分应用程序并不受 Scale 缩放系数的控制，因此即使在 <strong>Settings>Displays（设置>显示）</strong>中将 Scale 设置为了 200% 后，UI 元素在高分屏下依旧显示过小。比如：ZOOM、网易云音乐等，为了解决这一问题可使用下面的命令来启动，即可正常显示。</p>
<pre><code class="Bash"># 启动zoom，缩放倍数可根据需要自行调整
QT_SCALE_FACTOR=2 zoom

# 启动网易云音乐
QT_SCALE_FACTOR=2 netease-cloud-music
</code></pre>
<h3>5. 使用 Deepin-Wine 安装 QQ/TIM/微信/Office/...</h3>
<p>对于官网未提供了 Ubuntu 版本 .deb 安装文件，但 deepin 中有的应用程序，可以使用 Deepin-Wine 来安装。</p>
<p>wine 是一种在 Linux 平台实现了部分 Windows 系统 API 的技术，可以让用户在 Linux 平台无缝使用 Windows 平台的应用程序。</p>
<p>deepin-wine 是国内的深度社区在 deepin linux 上经过改造的 wine 程序，并且社区在 deepin-wine 之上移植了很多的 Windows 软件，比如微信、QQ、TIM等。</p>
<p>github 上有人开发了一个项目 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Fwszqkzqk%2Fdeepin-wine-ubuntu" target="_blank">deepin-wine-ubuntu</a>，将 deepin-wine 及其之上适配好的各种 deb 软件包迁移到了 Ubuntu 上。要安装微信、QQ等软件，我们需要先安装 deep-wine-ubuntu。方法如下：</p>
<pre><code class="Bash"># 首先 clone deepin-wine-ubuntu 源码到本地
git clone git@github.com:wszqkzqk/deepin-wine-ubuntu.git

# 切换到源码目录
cd deepin-wine-ubuntu

# 安装脚本授权
sudo chmod +x install_2.8.22.sh

# 安装 deep-wine-ubuntu
./install_2.8.22.sh  
</code></pre>
<p>deep-wine-ubuntu 安装完成之后，我们就可以下载深度社区提供的各种 deb 软件，具体安装方同第 4 小节的安装方式：</p>
<pre><code class="Bash"># 安装
sudo apt install ./<file>.deb
</code></pre>
<p>深度社区提供的各种 deb 软件下载地址：</p>
<table>
<thead>
<tr>
<th>软件</th>
<th>下载地址</th>
</tr>
</thead>
<tbody>
<tr>
<td>QQ</td>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmirrors.aliyun.com%2Fdeepin%2Fpool%2Fnon-free%2Fd%2Fdeepin.com.qq.im" target="_blank">https://mirrors.aliyun.com/deepin/pool/non-free/d/deepin.com.qq.im</a></td>
</tr>
<tr>
<td>TIM</td>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmirrors.aliyun.com%2Fdeepin%2Fpool%2Fnon-free%2Fd%2Fdeepin.com.qq.office" target="_blank">https://mirrors.aliyun.com/deepin/pool/non-free/d/deepin.com.qq.office</a></td>
</tr>
<tr>
<td>微信</td>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmirrors.aliyun.com%2Fdeepin%2Fpool%2Fnon-free%2Fd%2Fdeepin.com.wechat" target="_blank">https://mirrors.aliyun.com/deepin/pool/non-free/d/deepin.com.wechat</a></td>
</tr>
<tr>
<td>...</td>
<td>...</td>
</tr>
</tbody>
</table>
<p>更多安装方法及软件地址可以参考 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Fwszqkzqk%2Fdeepin-wine-ubuntu" target="_blank">https://github.com/wszqkzqk/deepin-wine-ubuntu</a></p>
<blockquote>
<p>如果你的系统语言非中文，通过 deepin-wine 启动的软件中文会出现乱码。你需要将 /opt/deepinwine/tools/run.sh 文件中 WINE_CMD 这一行修改为：</p>
<p><code>WINE_CMD="LC_ALL=zh_CN.UTF-8 deepin-wine"</code></p>
</blockquote>
<h3>6. 安装 rmp 格式的软件</h3>
<p>很多软件只提供了 rmp 格式的安装包，并未提供 deb 格式的安装包，比如：<a href="https://links.jianshu.com/go?to=https%3A%2F%2Fwww.xmind.net%2Fdownload%2F" target="_blank">xmind</a>。因此我们需要将其转为 deb 安装包在再进行安装。这里我们拿 xmind 来举例，看看如何操作。</p>
<p>比如我们下载了 xmind 安装包 XMind-2020.rpm：</p>
<pre><code class="Bash"># 添加 Universe 仓库（如果未添加）
sudo add-apt-repository universe

# 更新
sudo apt update

# 安装 Alien
sudo apt install alien

# 将.rpm 包转换为.deb 包（当前目录下会生成一个 deb 安装包，比如：XMind-2020.deb）
sudo alien XMind-2020.rpm

# 安装
sudo dpkg -i XMind-2020.deb
</code></pre>
<h2>四. 桌面美化</h2>
<h3>1. 安装 tweek</h3>
<pre><code class="Bash">sudo apt install gnome-tweak-tool
</code></pre>
<h3>2. 安装插件扩展支持</h3>
<pre><code class="Bash"># 让 gnome 支持插件扩展
sudo apt install gnome-shell-extensions 

# chrome 浏览器扩展支持，可以使用浏览器安装插件
sudo apt install chrome-gnome-shell
</code></pre>
<h3>3. 常用插件清单</h3>
<table>
<thead>
<tr>
<th>插件名</th>
<th style="text-align:left">说明</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fextensions.gnome.org%2Fextension%2F307%2Fdash-to-dock%2F" target="_blank">Dash to Dock</a></td>
<td style="text-align:left">自定义 dock</td>
</tr>
<tr>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fextensions.gnome.org%2Fextension%2F1112%2Fscreenshot-tool%2F" target="_blank">Screenshot Tool</a></td>
<td style="text-align:left">截图插件</td>
</tr>
<tr>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fextensions.gnome.org%2Fextension%2F779%2Fclipboard-indicator%2F" target="_blank">Clipboard Indicator</a></td>
<td style="text-align:left">扩展粘贴板，可以看到历史粘贴内容</td>
</tr>
<tr>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fextensions.gnome.org%2Fextension%2F97%2Fcoverflow-alt-tab%2F" target="_blank">Coverflow Alt-Tab</a></td>
<td style="text-align:left">修改 Alt-Tab 应用切换效果</td>
</tr>
<tr>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fextensions.gnome.org%2Fextension%2F6%2Fapplications-menu%2F" target="_blank">Applications Menu</a></td>
<td style="text-align:left">在顶部状态栏添加应用程序入口</td>
</tr>
<tr>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fextensions.gnome.org%2Fextension%2F750%2Fopenweather%2F" target="_blank">OpenWeather</a></td>
<td style="text-align:left">顶部状态栏显示天气数据</td>
</tr>
<tr>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fextensions.gnome.org%2Fextension%2F8%2Fplaces-status-indicator%2F" target="_blank">Places Status Indicator</a></td>
<td style="text-align:left">顶部状态栏增加文件目录访问入口</td>
</tr>
<tr>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fextensions.gnome.org%2Fextension%2F59%2Fstatus-title-bar%2F" target="_blank">Status Title Bar</a></td>
<td style="text-align:left">在顶部状态栏中显示当前窗口的标题</td>
</tr>
<tr>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fextensions.gnome.org%2Fextension%2F1732%2Fgtk-title-bar%2F" target="_blank">GTK Title Bar</a></td>
<td style="text-align:left">移除非 gtk 应用程序的标题栏</td>
</tr>
<tr>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fextensions.gnome.org%2Fextension%2F545%2Fhide-top-bar" target="_blank">Hide Top Bar</a></td>
<td style="text-align:left">自动隐藏状态栏</td>
</tr>
<tr>
<td><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fextensions.gnome.org%2Fextension%2F1708%2Ftransparent-top-bar" target="_blank">Transparent Top Bar</a></td>
<td style="text-align:left">透明状态栏</td>
</tr>
<tr>
<td>...</td>
<td style="text-align:left">...</td>
</tr>
</tbody>
</table>
<p>更多扩展插件大家自行在<a href="https://links.jianshu.com/go?to=https%3A%2F%2Fextensions.gnome.org" target="_blank">https://extensions.gnome.org</a>上探索吧。</p>
<h3>4. 主题</h3>
<p>可在 <a href="https://links.jianshu.com/go?to=gnome-look.org" target="_blank">GNOME-LOOK</a> 上下载各种桌面主题、Shell 主题、图标（icon）主题</p>
<p><strong>安装桌面或者 shell 主题</strong></p>
<pre><code class="Bash"># 解压下载的主题文件
tar -xvf FileName.tar //解压

# 将解压后的主题文件拷贝到 /usr/share/themes
sudo cp -r FileName /usr/share/themes
</code></pre>
<p><strong>安装 icon 主题</strong></p>
<pre><code class="Bash"># 解压下载的主题文件
tar -xvf FileName.tar //解压

# 将解压后的主题文件拷贝到 /usr/share/icons
sudo cp -r FileName /usr/share/icons
</code></pre>
<p>之后打开 Tweeks 选择安装的主题即可</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="2006" data-height="1400"><img data-original-src="//upload-images.jianshu.io/upload_images/1167421-4c430d2d445f6353.png" data-original-width="2006" data-original-height="1400" data-original-format="image/png" data-original-filesize="230523" src="https://upload-images.jianshu.io/upload_images/1167421-4c430d2d445f6353.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<h3>5. 壁纸</h3>
<p>推荐几个下载 4K 8K 超高清壁纸的网站：</p>
<p><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fpixabay.com" target="_blank">https://pixabay.com</a></p>
<p><a href="https://links.jianshu.com/go?to=https%3A%2F%2Funsplash.com" target="_blank">https://unsplash.com</a></p>
<p><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fwallpapersite.com" target="_blank">https://wallpapersite.com</a></p>
<p><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fwallpapershome.com" target="_blank">https://wallpapershome.com</a></p>
<p>最后贴一张美化后的桌面（Applications Theme: SURU++; Icons Theme: Reversal）</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1280" data-height="720"><img data-original-src="//upload-images.jianshu.io/upload_images/1167421-b9a9b05c680a170f.png" data-original-width="1280" data-original-height="720" data-original-format="image/png" data-original-filesize="1205607" src="https://upload-images.jianshu.io/upload_images/1167421-b9a9b05c680a170f.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">我的桌面</div>
</div>
<h2>五. 使用问题记录</h2>
<h3>问题一：Windows、Ubuntu 双系统时间不统一</h3>
<p>如果你是双系统，安装完 Ubuntu 设置好系统时间后，回到 Windows 会发现时间不统一。为了理解为什么，我们得先了解点基础知识：</p>
<ul>
<li><p><strong>UTC</strong>(Coordinated Universal Time)，协调世界时（世界统一时间)；</p></li>
<li><p><strong>GMT</strong>(Greenwich Mean Time)，格林威治标准时间。</p></li>
</ul>
<p>Windows 与类 Unix 系统(Unix/Linux/Mac)看待系统硬件时间的方式是不一样的：</p>
<ul>
<li><p>Windows 把计算机硬件时间当作本地时间(local time)，所以在 Windows 系统中显示的时间跟 BIOS 中显示的时间是一样的。</p></li>
<li><p>类 Unix 系统把计算机硬件时间当作 UTC， 所以系统启动后会在该时间的基础上，加上电脑设置的时区数(比中国就加8)，因此 Ubuntu 中显示的时间总是比 Windows 中显示的时间快 8 小时。</p></li>
</ul>
<p>当你在 Ubuntu 中把系统显示的时间设置正确后，计算机硬件时间就变成了在这个时间上减去 8 小时，所以当你切换成 Windows 系统后慢了8小时，就是这个原因。</p>
<p><strong>解决方案</strong>：在 Ubuntu 中把计算机硬件的时间改成系统显示时间，即禁用 Ubuntu 中的 UTC</p>
<pre><code class="Bash">timedatectl set-local-rtc 1 --adjust-system-clock
</code></pre>
<h3>问题二：Ubuntu 循环登陆</h3>
<blockquote>
<p>这个问题是我在 Ubuntu19.10 版本遇到的，20.04 版本中我没做验证，不确定是否有同样的问题。</p>
</blockquote>
<p>在解决问题之前，先补充一个关键知识点：显示管理器（Display Manager），它用来提供图形化登陆，向用户显示图形化登陆界面，并处理用户身份验证。Linux 中常见的显示管理器包括 gdm3、kdm、LightDM等：</p>
<ul>
<li>gdm3: gdm3 是 gdm 的继承者，它是 GNOME 的显示管理器；</li>
<li>kdm: kdm 是 KDE 的显示管理器；</li>
<li>LightDM: LightDM 是一个轻量级的显示管理器，他是显示管理器的规范解决方案。</li>
</ul>
<p><strong>原因：</strong></p>
<p>实操验证，初步断定是因为设置中开启了自动登陆，触发了 dgm3 的某种 bug 导致的。（Ubuntu19.10 默认使用的是 GNOME 桌面系统， 而 gdm3 是 GNOME 的显示管理器）</p>
<p><strong>解决方案</strong>：使用 LightDM 替换 gdm3</p>
<p>第一步：安装 LightDM（由于你现在无法进入图形化桌面，因此需要你在登陆页面使用 ctl + alt + F2 快捷键进入命令行模式，输入账号密码登陆，然后使用下面的命令安装）</p>
<pre><code class="Bash">sudo apt-get install lightdm
</code></pre>
<p>安装完成后，系统会自动弹框要求你选择当前系统中已安装的显示管理器，选择 lightdm。</p>
<p>第二步：重启</p>
<pre><code class="Bash">sudo reboot
</code></pre>
<p>重启完就能正常登陆了。</p>
<p>这时候你会发现登陆界面变了，如果你想切回之前的登陆界面，在进入系统后把自动登陆关闭，然后实现下面的命令重新选择 gdm3 显示管理器即可（需重启生效）</p>
<pre><code class="Bash">sudo dpkg-reconfigure gdm3
</code></pre>
<blockquote>
<p>并不是把自动登陆关闭后 gdm3 的 bug 就一定能规避掉，这一点可能只适用于我安装的 Ubuntu19.10；我这里说的原因也不一定适用所有人。但有一点可以肯定的是，如果出现循环登陆的情况，更换显示管理器通常是能解决问题的。</p>
</blockquote>
<p>如果你想查看当前系统正在运行的显示管理器，可以使用下面的命令：</p>
<pre><code class="Bash">cat /etc/X11/default-display-manager
</code></pre>
<h3>问题三：NVIDIA 驱动修复</h3>
<p>Ubuntu 20.04 自带了 nvidia 显卡驱动，但是被我不小心玩坏了。主要表现在：</p>
<ol>
<li>前面提到的 xrandr 命令失效，无法实现小数倍缩放；</li>
<li>NVIDIA X Server Settings 客户端打开空白；</li>
<li>命令行执行 <code>nvidia-settings</code> 命令出错；</li>
<li>
<strong>Settings>Displays（设置>显示）</strong>中无法设置多种分辨率等等。</li>
</ol>
<p>如果你也和我遇到同样的问题，或者希望手动安装显卡驱动，可以按照下面的方式操作。(需要首先到 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fwww.nvidia.com" target="_blank">NVIDIA 官网</a>下载你设备对应的显卡驱动)</p>
<pre><code class="Bash"># 先安装一些依赖库
sudo apt install build-essential libglvnd-dev pkg-config

# 停止桌面管理器，进入命令行摸索
sudo telinit 3

# 删除已安装的 nvidia 驱动
sudo apt purge "nvidia*"

# 手动安装显卡驱动
sudo bash NVIDIA-Linux-x86_64-440.82.run 

# 重启
sudo reboot
</code></pre>
<p>更多显卡驱动方式可参考：<a href="https://links.jianshu.com/go?to=https%3A%2F%2Flinuxconfig.org%2Fhow-to-install-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux" target="_blank">https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux</a></p>
<hr>
<p><strong>参考文档：</strong></p>
<ul>
<li><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fwiki.archlinux.org%2Findex.php%2FHiDPI_%28%25E7%25AE%2580%25E4%25BD%2593%25E4%25B8%25AD%25E6%2596%2587%29%23%25E9%259D%259E%25E6%2595%25B4%25E6%2595%25B0%25E5%2580%258D%25E7%25BC%25A9%25E6%2594%25BE" target="_blank">HiDPI#非整数倍缩放</a></li>
<li><a href="https://links.jianshu.com/go?to=http%3A%2F%2Fmacshuo.com%2F%3Fp%3D676" target="_blank">终极 Shell</a></li>
<li><a href="https://links.jianshu.com/go?to=https%3A%2F%2Flinuxconfig.org%2Fhow-to-install-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux" target="_blank">How to install the NVIDIA drivers on Ubuntu 20.04 Focal Fossa Linux</a></li>
</ul>
<p>本文档会持续更新，关注公众号 <strong>BaronTalk</strong>，回复 Ubuntu 即可下载最新的 PDF 版本配置文档。</p>
  
</div>
            
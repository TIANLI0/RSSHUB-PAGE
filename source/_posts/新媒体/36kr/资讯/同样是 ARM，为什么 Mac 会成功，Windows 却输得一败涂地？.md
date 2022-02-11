
---
title: '同样是 ARM，为什么 Mac 会成功，Windows 却输得一败涂地？'
categories: 
 - 新媒体
 - 36kr
 - 资讯
headimg: 'https://picsum.photos/400/300?random=1190'
author: 36kr
comments: false
date: Fri, 11 Feb 2022 11:15:43 GMT
thumbnail: 'https://picsum.photos/400/300?random=1190'
---

<div>   
<p>由于联邦贸易委员会在去年对于反垄断严加打击，在上个月彭博社发布一篇报道后，有传言称<a class="project-link" data-id="3969182" data-name="英伟达" data-logo="https://img.36krcdn.com/20200916/v2_811751a081924fa9af8741ce120bd7bf_img_png" data-refer-type="2" href="https://36kr.com/projectDetails/3969182" target="_blank">英伟达</a>正准备放弃以400亿美元收购Arm。</p> 
<p>本周英伟达正式官宣终止收购 Arm。事实上，倘若彼时英伟达和Arm合并，预期将创造出仅次于<a class="project-link" data-id="3968654" data-name="英特尔" data-logo="https://img.36krcdn.com/20200916/v2_811751a081924fa9af8741ce120bd7bf_img_png" data-refer-type="2" href="https://36kr.com/projectDetails/3968654" target="_blank">英特尔</a>的第二个半导体巨头，并在移动和嵌入式处理器领域成为高通和三星的强力对手。除此之外，两者合并后还可能成为<a class="project-link" data-id="3967413" data-name="微软" data-logo="https://img.36krcdn.com/20200916/v2_811751a081924fa9af8741ce120bd7bf_img_png" data-refer-type="2" href="https://36kr.com/projectDetails/3967413" target="_blank">微软</a>下一代基于ARM的Windows笔记本电脑的硅供应商等。</p> 
<p>因此，许多行业观察家可能想知道：ARM在桌面计算领域的未来是否全是苹果？就目前而言，只有苹果公司通过将其Mac平台过渡到M1 ，在自己设计的基于ARM的芯片上取得了成功。</p> 
<h2 label="一级标题">1 Windows on ARM却成绩平平，这是为何？</h2> 
<p>苹果M1 Mac的成功证明，ARM在PC上同样很有前景，可是在此之前的微软也就是Windows on ARM却成绩平平，这是为何？</p> 
<p>对此，很多人认为Windows on ARM的主要障碍在于硬件，因为软件以及开发工具都是现成的。然而真正的问题在于开发者工具的兼容问题。例如Visual Studio、VS构建工具和RISC-V等等。倘若不能解决兼容问题，那么Windows on ARM永远无法实现。</p> 
<p>微软的开发者工具链在ARM中表现非常糟糕，微软并未提供ARM版本的Visual Studio、VS构建工具、甚至没有Microsoft Visual C++，他们希望ARM开发者能够在x86主机上交叉编译C++软件或模拟x86。</p> 
<p>即使ARM可原生支持.NET以及VS Code，但这对于C++开发者来说意义不大。因为MSVC是封闭源代码，ARM要想获得对MSVC的本机支持只能靠微软。</p> 
<p>除此之外，开源问题同样不容乐观。由于MinGV或是MSYS开发环境中无法搭建ARM，因此Windows上无法使用Arm GCC或Arm Clange工具链。尽管有部分功能能够添加原生ARM支持，但目前还无法使用。Arm官网中可以下载用于x86的MinGV GCC，并为Arm设备进行交叉编译。如果只有用竞品才能在Windows上编译自己的产品，那么这的确能够说明一些问题。</p> 
<p>另一个在Windows中流行的C++编译器是英特尔C++编译器（ICC），但它并不能在ARM上使用，并且必须要安装Visual Studio。也就是说，4个流行的C++编译器均不能用于ARM Windows。</p> 
<p>可能许多人都不了解为编译器提供原生ARM支持的意义所在。在为手机或游戏开发软件时，有许多开发者已经从自己的电脑交叉编译到其他设备中，那为什么不能交叉编译到ARM Windows设备上呢？其实这是可行的，但是不好用。</p> 
<p>如果Windows电脑不能原生支持编译器，并且需要其他电脑交叉编译二进制文件/可执行文件，那么这就和手机没什么区别，因为开发者不能在同一设备上进行开发测试。不同之处在于手机和游戏机并不是开发平台。虽然手机可以写代码，但这种情况并不多见。</p> 
<p>除此之外，Windows for ARM的另外一个缺点在于它不支持OpenGL以及Vulkan。如果你用的是Vulkan，就算你设置了交叉编译工具链也不方便。如果你使用的是OpenGL程序，你最好转为DirectX。</p> 
<p>微软的要求很明确，如果要用到新的ARM Windows平台，就必须要用他们的专业API。同样，PlayStation、Xbox、Switch 和 iPhone 要求开发者使用专有的图形 API，但他们都不能运行编译器，因此开发者必须从另一台设备进行交叉编译。开发者应当清楚：Windows for ARM不能运行专业的图形API或是编译器，不能用作专业的开发平台。</p> 
<h2 label="一级标题">2 用户：微软逼我选择x86</h2> 
<p>由于开发者在ARM Windows上的体验较差，他们会选择使用x86，如此反复，Arm Windows永远不会达到和x86相同级别的支持，而使用ARM Windows的人也会越来越少。打破这一循环的方法就是让Visual Studio等主要开发者工具能够支持ARM。</p> 
<p>相比之下，ARM对于macOS以及Linux上的开发者工具的支持要好得多。GCC、Clang和 Python可完美支持ARM。开发者可以下载这些开发工具的本地版本并进行本地编译，与传统的模式没有任何不同。</p> 
<p>但如果苹果在没有移植Clang并且不支持OpenGL的情况下就发布ARM macOS同样是个灾难。在这种情况下，开发者必须使用旧的x86 Mac进行开发并为ARM Mac进行交叉编译。而这势必会引起轩然大波，开发者会担心苹果是在把macOS转变为iOS，如果不能编译自己的软件，也就不能运行自己的软件。这样和Windows没什么区别。</p> 
<p>从C++开发者的角度来看，可能Linux对于RISC-V的支持比Windows对于ARM的支持更好。RISC-V是一种全新的开源CPU架构，但目前还无法使用。RISC-V上的Linux体验一般，不过仍有一个可用的编译器，因此开发者可以在另一台设备上使用本机软件进行开发，而无需交叉编译。从这一点来说Windows for ARM是更为逊色的。</p> 
<p>微软在ARM设备上的首次尝试是在2012年发布的Surface平板电脑中，它运行的是Windows RT（Windows 8 for Arm）。如果微软全力支持ARM，他们应该早在2012年就将MSVC和Visual Studio移植到ARM，类似于苹果在发布第一批ARM Mac时对Xcode和Clang的支持。</p> 
<p>回顾过去，微软似乎将Visual Studio移植到ARM上没什么想法。直到今年，微软才将Visual Studio移植到同一架构的64位版本。这是2003年发布的第一个64位x86 CPU，即Athlon 64，而这距离现在已经19年了。不过微软的确在2005年左右将MSVC移植到了64 位 x86上，因此ARM并不是一点希望也没有，但是为了让开发者获得更好的体验，微软需要将整个Visual Studio堆栈移植到Arm。</p> 
<h3 label="二级标题">参考资料</h3> 
<ul class=" list-paddingleft-2"> 
 <li><p>https://www.zdnet.com/article/does-windows-on-arm-have-a-future/</p></li> 
 <li><p>https://www.zdnet.com/article/op-ed-windows-isnt-ready-for-arm-developers/</p></li> 
 <li><p>https://www.zdnet.com/article/future-of-desktop-computing-is-it-all-in-apples-hands-with-arm/</p></li> 
</ul> 
<p>本文来自<a class="project-link" data-id="3968527" data-name="微信" data-logo="https://img.36krcdn.com/20200916/v2_811751a081924fa9af8741ce120bd7bf_img_png" data-refer-type="2" href="https://36kr.com/projectDetails/3968527" target="_blank">微信</a>公众号<a href="https://mp.weixin.qq.com/s/uIh-LSKYZYEZDbz6E4ji5g">“CSDN”（ID:CSDNnews）</a>，整理：郭露，36氪经授权发布。</p>  
</div>
            
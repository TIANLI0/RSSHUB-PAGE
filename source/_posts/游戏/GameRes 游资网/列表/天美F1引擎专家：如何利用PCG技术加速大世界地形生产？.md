
---
title: '天美F1引擎专家：如何利用PCG技术加速大世界地形生产？'
categories: 
 - 游戏
 - GameRes 游资网
 - 列表
headimg: 'https://di.gameres.com/attachment/forum/202112/06/102822delze5uej6uh8ee2.jpg'
author: GameRes 游资网
comments: false
date: Mon, 06 Dec 2021 00:00:00 GMT
thumbnail: 'https://di.gameres.com/attachment/forum/202112/06/102822delze5uej6uh8ee2.jpg'
---

<div>   
<table cellspacing="0" cellpadding="0"><tbody><tr><td class="t_f" id="postmessage_2519684">
<div class="quote"><blockquote>导语：天美十三周年，天美联合知乎游戏，举办“游戏未来十三问”主题圆桌，邀请游戏从业者、玩家和广大朋友们，一同探讨和展望游戏的未来。本文为圆桌议题“2021年，游戏行业有哪些能提升开发效率的“黑科技”，前景如何？”下的回答，希望对大家有所帮助。</blockquote></div>
<br><strong>答者：潜龙旭，天美 F1 工作室技术中台引擎程序团队负责人</strong><br><br>
不知不觉在游戏开发行业已过十年，从刚入行的技术小白，到现在依然什么都不懂的技术搬砖工，见证了一个时代的游戏技术变革。我本人先后做过游戏开发 SDK，端游 MMO，休闲手游，重度手游，大世界手游，大世界端游等各品类产品，现在是天美 F1 工作室技术中台引擎程序团队负责人。<br><br>
游戏行业发展很快，玩家对游戏的要求越来越高，游戏对技术的要求也越来越高，开发量也越来越大。我现在所在的天美 F1 工作室正在开发 AAA 级全平台的大世界游戏，这是一件非常具有挑战的事情。<br><br>
本人作为游戏引擎程序，深知技术更新之快，需要不断的学习才能接受这个挑战。所幸我们已经提前在多个方向积累了对标国际 AAA 大厂的技术能力，并且还在全球招募了不少具有 AAA 项目研发背景的各方面人才。通过不断的夯实技术基础，我们有能力也有信心接受新的挑战。在我们储备的技术中，PCG 的技术是目前大世界游戏必不可少的一种技术，现在做一些简单介绍。<br><br><strong>PCG（Procedural Content Generation,过程化内容生成）技术是最近比较热的提升游戏生产效率的一类技术。</strong>它是什么意思呢？<br><br>
网络百科给出的答案：过程生成（英语：Procedural Generation）是计算机科学中一种使计算机自动制造一类数据的算法。在计算机图形学中，它也被称为随机生成，常用于制作材质贴图和三维模型资源，并在电子游戏领域中用于自动制造大量游戏内容。过程化生成有着减小文件体积、扩大内容量、增强游戏随机性等优点。<br><br>
我个人的理解：如果在游戏中应用，简单说，过程化内容生成就是利用算法来自动生成游戏内容。原有的游戏内容需要美术和策划花费大量的精力制作，过程化的方式可以大大降低人工成本，除了可以节省一些重复的人工劳动之外，甚至可以自动创作出一些新的设计内容。试想如果有一个程序可以自动生产游戏，那是多么有意思的一件事情，也许那天到来，游戏开发者都下岗了。<br><br>
地形是大世界的基础，大世界没有地形，就没有玩家可立足之地。大世界有多大，地形就有多大，如果能用 PCG 技术加速大世界地形生产，就可以大大减少美术和策划的人力消耗。<br><br>
这里有两个难点，一：如何生成真实自然的地形？真实世界的地形并不是一些杂乱无章的形状，他是自然的造化，往往具有赏心悦目的美感。利用算法来生成具有美感的地形是我们面临的第一大挑战。二：大世界巨大，内容繁杂，涉及制作人员众多，如何让制作人员高效的协作是我们面临的第二大挑战。<br><br>
今天简单谈一谈如何利用 PCG 技术加速大世界游戏里的地形生产的一些基本思路。<br><br><strong><font color="#de5650">1. 传统的地形工作流</font></strong><br><br>
传统的地形工作流，大家应该很熟悉，美术先找到一些参考的高度图，导入到游戏引擎编辑器中，随后根据自己的需求，通过地形编辑工具来编辑地形。比如 UE 的地形编辑器提供了各种各样的刷子来给美术去手刷和雕刻地形。显而易见，这种方式对美术来说工作量是巨大的。<br><br><strong><font color="#de5650">2. 过程化地形</font></strong><br><br><div align="center"><font size="2">
<img id="aimg_1023487" aid="1023487" zoomfile="https://di.gameres.com/attachment/forum/202112/06/102822delze5uej6uh8ee2.jpg" data-original="https://di.gameres.com/attachment/forum/202112/06/102822delze5uej6uh8ee2.jpg" width="200" inpost="1" src="https://di.gameres.com/attachment/forum/202112/06/102822delze5uej6uh8ee2.jpg" referrerpolicy="no-referrer"></font></div>
<div align="center"><font size="2">一些可用的地形噪声</font></div>
<br>
过程化地形可以利用算法自动地生成地形。常用的有随机噪声地形，这类方法是一类构造式的算法，通过设计一些噪声函数来随机生成地形高度信息，比如常见的 Perlin Noise，Worley Noise，Voronoi Noise，Flow Noise等等。<br><br>
另外还有一类是侵蚀算法。通常真实世界的地形，是大自然常年累月对地形进行影响的结果。这类算法会通过对侵蚀过程进行数学建模，然后仿真得到一个拟真的自然的地形效果。比如热侵蚀，水力侵蚀等 ......<br><br>
我们来看几个过程化地形的例子。比如如何用噪声表达丘陵地形？就像图中连绵起伏的小山包。其实很简单，我们对噪声函数取一个绝对值就好了，这时噪声的形状会发生一个凸起达到表达丘陵的效果。<br><br><div align="center"><font size="2">
<img id="aimg_1023488" aid="1023488" zoomfile="https://di.gameres.com/attachment/forum/202112/06/102823ey329r2zrr2q2i72.jpg" data-original="https://di.gameres.com/attachment/forum/202112/06/102823ey329r2zrr2q2i72.jpg" width="532" inpost="1" src="https://di.gameres.com/attachment/forum/202112/06/102823ey329r2zrr2q2i72.jpg" referrerpolicy="no-referrer"></font></div>
<div align="center"><font size="2">无人深空中的丘陵地形</font></div>
<div align="center"><font size="2"><br></font></div>
<div align="center"><font size="2">
<img id="aimg_1023489" aid="1023489" zoomfile="https://di.gameres.com/attachment/forum/202112/06/102823ns7iwmc44snms44q.jpg" data-original="https://di.gameres.com/attachment/forum/202112/06/102823ns7iwmc44snms44q.jpg" width="192" inpost="1" src="https://di.gameres.com/attachment/forum/202112/06/102823ns7iwmc44snms44q.jpg" referrerpolicy="no-referrer"></font></div>
<br>
那如何利用噪声表达山脊线呢？很多大的山脉会有一条条山脊线，就像图中的阿尔卑斯山。我们可以把噪声先取绝对值再取反，翻转后抬高。<br><br>
可以观察到在波形相交的地方形成了一个尖点，图里的是二维的情况，如果在三维中就会形成一条条局部最高点的线，这样就可以模拟这种山脊的形状。<br><br><div align="center"><font size="2">
<img id="aimg_1023490" aid="1023490" zoomfile="https://di.gameres.com/attachment/forum/202112/06/102823e88tjttr18n97j5w.jpg" data-original="https://di.gameres.com/attachment/forum/202112/06/102823e88tjttr18n97j5w.jpg" width="476" inpost="1" src="https://di.gameres.com/attachment/forum/202112/06/102823e88tjttr18n97j5w.jpg" referrerpolicy="no-referrer"></font></div>
<div align="center"><font size="2">阿尔卑斯山脉</font></div>
<div align="center"><font size="2"><br></font></div>
<div align="center"><font size="2">
<img id="aimg_1023491" aid="1023491" zoomfile="https://di.gameres.com/attachment/forum/202112/06/102823djvsj8qnvv13qpj3.jpg" data-original="https://di.gameres.com/attachment/forum/202112/06/102823djvsj8qnvv13qpj3.jpg" width="296" inpost="1" src="https://di.gameres.com/attachment/forum/202112/06/102823djvsj8qnvv13qpj3.jpg" referrerpolicy="no-referrer"></font></div>
<br>
那如何用噪声表达河流呢？我们可以通过域扭曲的方法来做。这种方法很简单，就是对噪声函数的定义域做一次变换，比如这里的例子，简单的对变量做一个位置的偏移，经过多次的位置扭曲，形成一些很特别的效果。可以看到图中高度数据的变化过程，最后形成像河流一样的效果。<br><br><div align="center">
<img id="aimg_1023492" aid="1023492" zoomfile="https://di.gameres.com/attachment/forum/202112/06/102823m5qn3gl9ql3a0p33.jpg" data-original="https://di.gameres.com/attachment/forum/202112/06/102823m5qn3gl9ql3a0p33.jpg" width="600" inpost="1" src="https://di.gameres.com/attachment/forum/202112/06/102823m5qn3gl9ql3a0p33.jpg" referrerpolicy="no-referrer">
</div>
<div align="center">
<img id="aimg_1023493" aid="1023493" zoomfile="https://di.gameres.com/attachment/forum/202112/06/102824sjbxvuwjjbeesrt9.jpg" data-original="https://di.gameres.com/attachment/forum/202112/06/102824sjbxvuwjjbeesrt9.jpg" width="600" inpost="1" src="https://di.gameres.com/attachment/forum/202112/06/102824sjbxvuwjjbeesrt9.jpg" referrerpolicy="no-referrer">
</div>
</td></tr></tbody></table>
  
</div>
            
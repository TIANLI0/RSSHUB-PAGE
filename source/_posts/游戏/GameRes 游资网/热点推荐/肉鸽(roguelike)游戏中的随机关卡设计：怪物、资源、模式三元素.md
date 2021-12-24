
---
title: '肉鸽(roguelike)游戏中的随机关卡设计：怪物、资源、模式三元素'
categories: 
 - 游戏
 - GameRes 游资网
 - 热点推荐
headimg: 'https://di.gameres.com/attachment/forum/202112/24/092713xm6b9n3ni6mnh92m.jpg'
author: GameRes 游资网
comments: false
date: Fri, 24 Dec 2021 00:00:00 GMT
thumbnail: 'https://di.gameres.com/attachment/forum/202112/24/092713xm6b9n3ni6mnh92m.jpg'
---

<div>   
<div align="center">
<img id="aimg_1025791" aid="1025791" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092713xm6b9n3ni6mnh92m.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092713xm6b9n3ni6mnh92m.jpg" width="600" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092713xm6b9n3ni6mnh92m.jpg" referrerpolicy="no-referrer">
</div><br>
<font color="#808080">本文首发知乎：https://zhuanlan.zhihu.com/p/441943889</font><br>
<br>
<strong><font color="#de5650">结论</font></strong><br>
<br>
为了方便各位快速了解，本文结论在这里先放上。<br>
<br>
<ul><li>肉鸽（roguelike）关卡的随机感受来源于怪物，资源，模式三元素的随机组合；</li><li>随机关卡的实际提供了条件随机，有限随机，真随机三类随机感受；</li><li>目前的随机关卡是按照资源随机自始至终，中期辅以模式随机，长线怪物随机持续刷新体验的节奏推送给玩家；</li><li>随机关卡的内核是提供了一种持续的挑战心流，这源自核心博弈能力的上下波动与节奏点下的高频抉择。<br>
</li></ul><br>
<br>
<strong><font color="#de5650">1. 随机关卡的构成元素</font></strong><br>
<br>
<strong>1.1 类比定义</strong><br>
<br>
游戏关卡在百度百科上的定义为，玩家（游戏人物）基于某个目的在一个场景区域内进行活动。借用这个概念，我尝试对常见肉鸽游戏中的随机关卡进行拆解，这里最为明显的是大部分肉鸽游戏的目的，均是与场景内的怪物进行作战，同时不断收集各式各样的资源，而游戏人物与场景区域基于游戏本身玩法（横板跳跃/射击等），在3C与具体关卡设计上各有不同，但是其在过程上有共通之处，即游戏人物从初始相对较弱至通过时远超游戏强度（组合各类BD实现，本文暂不对此进行讨论），而场景区域上均有明确的起点与终点，中间以不同模式的房间进行组成（如商人房，隐藏房）。<br>
<br>
*这里房间的概念有作抽象，如死亡细胞中的不同功能区域我也是将其抽象为房间<br>
<br>
这样，我们大致可以给肉鸽的随机关卡下个定义：<br>
<br>
玩家操作游戏人物在固定起点进入一系列随机模式组成的有限区域，不断决策行进方向，与区域内的怪物发生战斗并收集资源强化自己直至行走到终点以远超常规游戏的强度通关，而肉鸽游戏正是由怪物，资源，模式三个模块的随机构成了游戏的随机关卡体验。<br>
<br>
<strong>1.2 随机怪物</strong><br>
<br>
当你进入一款肉鸽游戏时，形色各异的怪物肯定是第一时间招呼你的那个，当然每一次不同的刷新点也时刻考验着你对战场信息的获取-分析能力。<br>
<br>
——在怪物的随机上，我将其总结为基于近战/远程怪，buff/召唤怪，机制怪三类怪物形成的随机怪物组合。<br>
<br>
<font color="#de5650">近战/远程怪</font><br>
<br>
游戏的基础怪，实际代表在单一机制下与玩家对战的不同攻击形态，我们可以将它看作由AI控制的能力不对等的玩家。比如hades里的胖子-大锤两兄弟就是基础的近战怪，而法师-炸弹哥就是基础的远程怪。<br>
<br>
<div align="center">
<img id="aimg_1025792" aid="1025792" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092714wiqzw7qpw60q63ah.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092714wiqzw7qpw60q63ah.jpg" width="366" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092714wiqzw7qpw60q63ah.jpg" referrerpolicy="no-referrer">
</div><br>
<div align="center">
<img id="aimg_1025793" aid="1025793" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092714z20vxz0711741cc4.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092714z20vxz0711741cc4.jpg" width="493" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092714z20vxz0711741cc4.jpg" referrerpolicy="no-referrer">
</div><br>
他们通过不同的数值配置（常见的如移速、范围、攻防血、攻击欲望、弹幕形制-出手前摇&频次等核心博弈点等），轮番验证玩家在游戏中的精准操作。<br>
<br>
<font color="#de5650">buff/召唤怪</font><br>
<br>
游戏的节奏怪，他们带来了明确的击杀次序变化以验证玩家游戏理解，比如hades里的骷髅头（无限召唤）-蓝水晶（buff无敌）就是此类怪。<br>
<br>
<div align="center">
<img id="aimg_1025794" aid="1025794" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092714ao0kvdog4gs00g4h.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092714ao0kvdog4gs00g4h.jpg" width="361" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092714ao0kvdog4gs00g4h.jpg" referrerpolicy="no-referrer">
</div><br>
<font color="#de5650">机制怪</font><br>
<br>
不同于基础怪，这类怪物主要在战斗策略上进行丰富以提供策略制定的空间（如控血-转火等输出策略、距离策略、协作策略） ，比如hades里的窝瓜（腾空落地-储备两次闪避，利用落点预判作陷阱击杀等）<br>
<br>
<div align="center">
<img id="aimg_1025795" aid="1025795" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092714n00ef1vyqmeo4mm4.png" data-original="https://di.gameres.com/attachment/forum/202112/24/092714n00ef1vyqmeo4mm4.png" width="161" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092714n00ef1vyqmeo4mm4.png" referrerpolicy="no-referrer">
</div><br>
-枪火重生里的强盗隐士（隐身+破甲-拉开距离，等待其现身攻击）。<br>
<br>
<div align="center">
<img id="aimg_1025796" aid="1025796" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092714zpparhrhshrfrrm5.png" data-original="https://di.gameres.com/attachment/forum/202112/24/092714zpparhrhshrfrrm5.png" width="180" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092714zpparhrhshrfrrm5.png" referrerpolicy="no-referrer">
</div><br>
——在怪物刷新点的随机上，肉鸽通过刷新坐标，刷新速率两者形成随机组合。<br>
<br>
<font color="#de5650">刷新坐标</font><br>
<br>
相较于传统关卡种怪，肉鸽的种怪并非一个个固定生成。它主要是在多个固定点/固定范围内随机，基于刷新坐标点距来调节怪物的疏密。当然在在hades与死亡细胞等强调动作战斗的肉鸽中还存在角色视野内外的随机。<br>
<br>
<font color="#de5650">刷新速率</font><br>
<br>
速率这里大部分肉鸽并不存在随机，与传统游戏类似，都是在定时（怪物/怪物组死亡一定时间后重生）或定量（范围内怪物少于x数后重生），以提供战中的小节奏点。玩的比较花的类似死亡细胞，引入了类求生之路的AI管理器，基于玩家表现来调节关卡怪物的刷新数量与速率。<br>
<br>
那么问题来了，随机怪物体验是否像做东北大乱炖一样，把上述的元素做一个随机生成就可以了呢？<br>
<br>
<strong>并不是</strong>，经过仔细琢磨各大肉鸽游戏，其怪物在上述元素随机生成之外，还需要在怪物职能限制下进行随机。即怪物不是随机一个点刷出来形色各异的组合（比如hades一进入房间，一堆炸弹车已经在你面前刷出），而是基于怪物的职能-抑或是给玩家带来的交战体验进行随机生成。<br>
<br>
这里我们先把怪物做一个职能拆分。无论怪物的数值-机制是怎样，他们大致可以拆分为3类职能。<br>
<br>
<ul><li><strong>埋伏职能</strong>，他们通常藏在你观察不到的地方，等待着给你来上一记摸头杀。</li><li><strong>防御职能</strong>，他们经常在你看得见但不是那么容易摸着的地方，让你有足够的机会准备好给他迎头痛击。</li><li><strong>追击职能</strong>，他们特别喜欢对着你死命追杀直到海角天涯，一招秦王绕柱是你屡试不爽的保命技能。<br>
</li></ul><br>
大致看完职能，我们来想下如下图的场景，看排出的阵型是不是有点熟悉。即A类怪通常在视野外或障碍遮挡处刷新，B类怪通常在最远交战距离处进行刷新，C类怪按照作战距离在你身旁刷出。<br>
<br>
<div align="center">
<img id="aimg_1025797" aid="1025797" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092715u55amd8o0d38k2x5.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092715u55amd8o0d38k2x5.jpg" width="600" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092715u55amd8o0d38k2x5.jpg" referrerpolicy="no-referrer">
</div><br>
<strong>1.3 随机资源</strong><br>
<br>
肉鸽游戏内能够获取的资源大概为3类，帮助你以远超常规游戏强度通关的BD资源，决定你生死的血量资源，持续考验资源管理能力的局内资源。当然随着roguelite（弱化死亡惩罚，增加局外循环）的兴起，局外资源也加入了局内资源的随机队列中。<br>
<br>
<font color="#de5650">BD资源</font><br>
<br>
从较早的弱bd组件到目前琳琅满目的无限组件叠加，bd带来的探索（涌现与协同）与成长感受越来越被肉鸽游戏看重并持续加强，这个话题展开会很大我们先不在本篇随机关卡中讨论。<br>
<br>
<font color="#de5650">血量资源</font><br>
<br>
血量资源在常规游戏中更多做警示作用，而在ROG中他高频变化，决定了你前行的随机关卡数。随之带来的算血玩法，本质上类似于魔塔带来的策略，当然这其中更多会分散到多个房间下的战斗-回复大节奏，而非单一房间内的精确计算。<br>
<br>
<font color="#de5650">局内资源</font><br>
<br>
局内资源提供了游戏的基础成长体验，比如持续获得的金币（购买其他资源）与经验，开启更多房间进入可能的key，bd加速类道具（比如重置房间奖励）。<br>
<br>
<font color="#de5650">*局外资源</font><br>
<br>
肉鸽越硬核其存在感越弱，目前主要为两种，一种是直接的局外带入局内的属性加成，一种是收敛局内bd方向（组成bd或干涉bd刷新概率）。<br>
<br>
当然，上述三类资源不是单独存在的，在游戏内也存在互相转换；大致如下图所示，局内资源是其他两个资源的中转站，血量资源对其他资源的置换也被较多肉鸽游戏采用，这带来了更紧张-极限的通关体验。抛开局外资源，对三类资源的投放侧重则受到游戏体验影响，比如侧重成长体验的hades-雨中冒险，就会去更多投放bd资源，而弱成长体验的以撒-贪婪洞窟，就会去强化血量与局内资源的投放。<br>
<br>
<div align="center">
<img id="aimg_1025798" aid="1025798" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092715w0o32n3oe9w89gzj.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092715w0o32n3oe9w89gzj.jpg" width="261" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092715w0o32n3oe9w89gzj.jpg" referrerpolicy="no-referrer">
</div><br>
<div align="center">
<img id="aimg_1025799" aid="1025799" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092715canlvplnv2plun3g.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092715canlvplnv2plun3g.jpg" width="249" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092715canlvplnv2plun3g.jpg" referrerpolicy="no-referrer">
</div><br>
<div align="center">
<img id="aimg_1025800" aid="1025800" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092715fqrktriinrqyzr7t.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092715fqrktriinrqyzr7t.jpg" width="600" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092715fqrktriinrqyzr7t.jpg" referrerpolicy="no-referrer">
</div><br>
那么问题又来了，上述三类资源的投放是否也是一场纯随机的结果呢？<br>
<br>
<strong>的确是</strong>，肉鸽在保障各类资源的最小需求下尽量做了随机。这给玩家带来了很有趣的体验，即你的获得顺序在三类资源中兜兜转转，这要求你要做到随机应变。这里随机应变的点大致有三种，我们用?代表bd资源，▲代表血量资源，█ 代表局内资源来看下：<br>
<br>
<div align="center">
<img id="aimg_1025801" aid="1025801" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092715s00ee0aaeg000a1z.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092715s00ee0aaeg000a1z.jpg" width="600" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092715s00ee0aaeg000a1z.jpg" referrerpolicy="no-referrer">
</div><br>
当然如上只是一个简化的说法，在大多数情况下资源投放的倾向性不会像所示的这么强，同时单纯BD资源内的循环已经产生较多变化。而在类似杀戮尖塔这类肉鸽游戏中中资源信息被充分展示的情况下，玩家的决策会更多关注在选分支的全局策略内。<br>
<br>
<strong>1.4 随机模式</strong><br>
<br>
这里先明确下模式的定义，模式我在这里定义为一个场景区域内的独特体验，没有到大家常见的如大乱斗、匹配、排位模式区隔度这么大。肉鸽中大概有8类体验节奏与目的不同的房间模式，主要在进入方式、战斗方式和奖励内容上明显不同，具体如下图所示：<br>
<br>
<div align="center">
<img id="aimg_1025802" aid="1025802" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092716p57sm71b5e5ww1je.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092716p57sm71b5e5ww1je.jpg" width="600" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092716p57sm71b5e5ww1je.jpg" referrerpolicy="no-referrer">
</div><br>
这些不同模式的房间进行随机组合，形成了玩家在通关过程中的各异体验。当然这些房间的随机组合也有其背后的规则，我总结为三步法，而目的是为了达成平滑BD成型速度的同时鼓励玩家更多进行探索。<br>
<br>
<ul><li>第一步，基于游戏想为玩家呈现的bd成长频次（比如以撒核心组件2-3个成型）&通关时长（如大部分的PC肉鸽单局45min+，手机端20min+），确定一个小范围浮动的房间总数(*如hades是固定房间总数，以撒是3.33 × 楼层 + random（5~6))。</li><li>第二步，按照起点到终点的最短行进路线-分支路线拆分房间总数，分支路线一般在一个小范围波动，在分支路线投放相对奖励&难度更高的房间以鼓励玩家探索。</li><li>第三步，将挑战-神秘-隐藏等房间按照概率计算刷新量，放置在分支路线上（如未达上限则填充其他房间，如达上限则放置在最短行进路线上刷新），再填充商店作为节奏点投入，最后将与bd&局内资源强关联的小怪-回复-宝箱房按照按照一定概率填充余下房间。<br>
</li></ul><br>
<div align="center">
<img id="aimg_1025803" aid="1025803" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092716kb2kffar8fbaa8pf.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092716kb2kffar8fbaa8pf.jpg" width="600" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092716kb2kffar8fbaa8pf.jpg" referrerpolicy="no-referrer">
</div><br>
*商店一般设定为1层1个 ，毕竟需要一段时间的金币资源积累<br>
<br>
似乎看起来，我们已经可以组成好这些各异的模式了，不过还有一些补丁要打一打以防止极端情况：<br>
<br>
<ul><li>过早遇见挑战房导致战斗受挫（前8个房间不出现）。</li><li>过晚遇见商店房导致资源积累无释放（第10-20个房间至少刷新1个），持续遇到商店缺少积累（遇到商店后5个房间内不再刷新商店）。</li><li>核心bd资源过早全部拿到（对应核心bd资源的核心宝箱房前20个房间最多刷新1个）。</li><li>恢复房间在满血情况下出现（无分支类游戏一般通过房间选择或条件判定避免）。<br>
</li></ul><br>
<strong><font color="#de5650">2. 不一样的随机感受</font></strong><br>
<br>
现在我们已经可以大致搭好随机关卡了，那么接下来让我们看看这些随机内容会带来怎样的随机感受呢。更形象的说，都是随机，砸金蛋和买彩票的随机感受绝对有明显差别，玩酒馆战旗和金铲铲的随机感受也是各有各的体验。让我们先来认识下这些不同的随机感受，条件随机、有限随机和真随机。<br>
<br>
<strong>2.1 条件随机</strong><br>
<br>
出现/达成A的情况下，必定触发B或提升B的概率。这句话看起来有些复杂，借用金铲铲来说，各星英雄的刷新概率在每级的本均有不同，玩家如果要D4星的英雄，那么他可以更多考虑将本提升至7本后再追。这种随机在肉鸽中较多出现在资源+模式两类上，这鼓励玩家更多成为一个计算家，让玩家更容易得出游戏的限定解。<br>
<br>
<div align="center">
<img id="aimg_1025804" aid="1025804" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092716t33fi6mzs0smm0im.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092716t33fi6mzs0smm0im.jpg" width="600" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092716t33fi6mzs0smm0im.jpg" referrerpolicy="no-referrer">
</div><br>
<strong>2.2 有限随机</strong><br>
<br>
之前做抽卡游戏时，有模拟过随机池子。当整个池子的卡数低于20时，十连抽卡出现的结果就容易出现重复导致没了随机感受，在整个卡池数量相对少的时候，实际抽卡的结果就容易猜中甚至让你有种掌握在手中的感觉。受此启发，我把大量肉鸽中出现的【小于5的池子内随机的情况】定位有限随机，即这里的结果让你感觉可以预测，成为一个随机应变者。<br>
<br>
*池子虽然多但是给到了足够多的刷新机会，也可以视为有限随机<br>
<br>
<div align="center">
<img id="aimg_1025805" aid="1025805" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092716wltkhjvgfetw6lv0.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092716wltkhjvgfetw6lv0.jpg" width="600" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092716wltkhjvgfetw6lv0.jpg" referrerpolicy="no-referrer">
</div><br>
<strong>2.3 真随机</strong><br>
<br>
有了上面有限随机的概念，真随机就很容易理解了。一般其是在一个超过8以上的池子内随机选择，由于你难以捉摸结果，这会明显鼓励那些脸好的幸运儿。<br>
<br>
<div align="center">
<img id="aimg_1025806" aid="1025806" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092717cghoydiokxj4jae1.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092717cghoydiokxj4jae1.jpg" width="600" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092717cghoydiokxj4jae1.jpg" referrerpolicy="no-referrer">
</div><br>
了解了这些随机感受，我们现在可以好好回顾下现有的肉鸽游戏了，比如总是期待自己能起步吐根的以撒，熟能生巧后低热乱杀的hades，思考10min操作10s的陷阵之志，正是在这三种随机感受上的侧重形成了不同的随机关卡体验。<br>
<br>
<div align="center">
<img id="aimg_1025807" aid="1025807" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092717etaa2msxobsr2yir.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092717etaa2msxobsr2yir.jpg" width="600" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092717etaa2msxobsr2yir.jpg" referrerpolicy="no-referrer">
</div><br>
<strong><font color="#de5650">3. 持续演变的推送节奏</font></strong><br>
<br>
有了上述对于随机内容、随机感受的了解，自然我们就来到推送节奏部分。类似传统游戏的功能开启节奏，内容不是一上来全部开给玩家的，对于肉鸽这种单一玩法大内容量的游戏，怎么在随机内容种找到一个合适的节奏值得来聊一聊。<br>
<br>
<strong>全随机的以撒</strong><br>
<br>
以撒作为一款大成的肉鸽游戏至今已经有10年，其在随机内容的推送节奏上遵循了全随机的设定，即怪物（含关卡内地形）、资源与模式每次开局均有不同，这也带来了至今仅30%的通关率（steam通关妈心）。大部分玩家在初期就被各种bd组件下的攻击弹道，不同的怪物与地形，key资源的不稳定夹杂复杂的慎密房弄昏了头脑，难以坚持下来。<br>
<br>
<div align="center">
<img id="aimg_1025808" aid="1025808" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092717oyshooo6mformng6.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092717oyshooo6mformng6.jpg" width="577" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092717oyshooo6mformng6.jpg" referrerpolicy="no-referrer">
</div><br>
<strong>随机逐步解锁的hades</strong><br>
<br>
hades在随机内容的开启上做了明确的控制，如其开局要轮番先见到不同的神，一定对局次数后才会刷新双神祝福帮助玩家在单一时间段内聚焦对特定bd的了解。当然其在关卡模式上极弱随机，如锤子房在第一章2-3与第三张2-3投放，宝箱房在首领前2内投放；甚至于怪物基本不随机，大部分的构型与刷新点是直接固定的。我们可以把hades的模式总结为初期仅资源随机，中期辅以关卡模式弱随机，长线以一定池子内的怪物随机推送给玩家，其通关率受其影响目前也来到了64%（首次完成逃离）。<br>
<br>
<div align="center">
<img id="aimg_1025809" aid="1025809" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092717wcoc2p2ec6qoyfce.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092717wcoc2p2ec6qoyfce.jpg" width="569" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092717wcoc2p2ec6qoyfce.jpg" referrerpolicy="no-referrer">
</div><br>
<strong>随机池也要逐步解锁的枪火重生</strong><br>
<br>
而国产的枪火重生也有自己的路子，其bd-怪物-关卡均挂钩击杀现有怪物x次后解锁，如精英盾兵在击杀[普通盾兵]20次刷新，bd组件穿甲子弹在击败 [马贼军师] 20次后加入随机池，更贴近玩家的游戏进程以展开随机内容。<br>
<br>
<div align="center">
<img id="aimg_1025810" aid="1025810" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092717ked762bmq7i7d6mx.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092717ked762bmq7i7d6mx.jpg" width="579" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092717ked762bmq7i7d6mx.jpg" referrerpolicy="no-referrer">
</div><br>
从上述游戏的过往我们可以发现，肉鸽游戏整体在往玩家更容易上手的方向演进，以资源特别是bd资源随机推进玩家持续体验其他随机内容。<br>
<br>
<strong><font color="#de5650">4. 随机关卡的内核——持续的挑战感</font></strong><br>
<br>
在玩肉鸽游戏时，我们会发现这与其他游戏的感觉有明显不同，比如经常秒躺，更加紧张刺激。我也在尝试去分析这背后的原因，后续看到一篇王者关卡大佬从情绪曲线出发看关卡的核心设计理念时找到了一条拆解思路，仿照大佬在其中提到的情绪曲线，我也尝试对自己体验hades时的情绪曲线进行了感性记录进行对比。<br>
<br>
<div align="center">
<img id="aimg_1025811" aid="1025811" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092718mo6l9mrsd0h606ar.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092718mo6l9mrsd0h606ar.jpg" width="600" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092718mo6l9mrsd0h606ar.jpg" referrerpolicy="no-referrer">
</div><br>
抛开单局时长，两者对比可以更明显的看到相较moba来说，在hades体验过程中：<br>
<br>
<ul><li>心流更多呈现上下波动，即通关的keypoint更加散。</li><li>玩家单个阶段到达心流峰值时的曲线更陡，更爽但也更加紧张，相对来说积累感更弱。<br>
</li></ul><br>
* 从我自己来说，曲线的陡峭更来自于单个关卡奖励不可预测的感受<br>
<br>
<ul><li>通关前不存在释放期，相较于MOBA后期龙团-高低团定出胜负（即对应moba的胜利方，非碾压局）肉鸽依然频繁提供挑战，受限于血量压力持续紧绷。<br>
</li></ul><br>
由这种持续的挑战感，我尝试对体验过程再进行一步下挖。作为ACT游戏，其核心战斗博弈围绕攻击节奏进行构建（即玩家穿插好躲避敌方攻击，进行我方攻击的节奏）。在hades的体验过程中，锤子与祝福两对节奏点持续改变玩家的攻击节奏（上下浮动而非一直上扬），进而影响玩家挑战关卡的情绪曲线。<br>
<br>
<ul><li>超前期较为平滑的挑战感主要由数值放长辅以固定怪物下的差异组合带来。</li><li>基于数值难度与boss机制会快速将玩家重新拉回初始水平，在此时段如发生了祝福-普攻buff多次强化，锤子-多段汇总一段等节奏点将重新抬高容错直至成型；即玩家始终在持续强的挑战中进行发育，直至以远超初期的强度通关释放。<br>
</li></ul><br>
<div align="center">
<img id="aimg_1025812" aid="1025812" zoomfile="https://di.gameres.com/attachment/forum/202112/24/092718drks1h444qyvy843.jpg" data-original="https://di.gameres.com/attachment/forum/202112/24/092718drks1h444qyvy843.jpg" width="600" inpost="1" src="https://di.gameres.com/attachment/forum/202112/24/092718drks1h444qyvy843.jpg" referrerpolicy="no-referrer">
</div><br>
<font size="2"><font color="#808080"></font></font><br>
<br>
  
</div>
            
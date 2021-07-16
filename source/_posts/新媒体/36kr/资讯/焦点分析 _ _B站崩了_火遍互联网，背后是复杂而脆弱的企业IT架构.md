
---
title: '焦点分析 _ _B站崩了_火遍互联网，背后是复杂而脆弱的企业IT架构'
categories: 
 - 新媒体
 - 36kr
 - 资讯
headimg: 'https://img.36krcdn.com/20210714/v2_2f1349764b0f4c5fa407d1f50b9aeeb8_img_jpeg'
author: 36kr
comments: false
date: Fri, 16 Jul 2021 00:40:00 GMT
thumbnail: 'https://img.36krcdn.com/20210714/v2_2f1349764b0f4c5fa407d1f50b9aeeb8_img_jpeg'
---

<div>   
<p>作者 | 咏仪</p> 
<p>编辑 | 苏建勋</p> 
<p>万万没想到，B站崩了，让全互联网经历了一次深夜狂欢。</p> 
<p>7月13日23时左右，B站主站、App、小程序均出现访问故障，无法正常使用，页面提示“正在玩命加载数据”。而B站的邻居A站，以及晋江、<a class="project-link" data-id="26593" data-name="豆瓣" data-logo="https://img.36krcdn.com/20210302/v2_946928fde01e4e3593c57a055ed2b258_img_000" data-refer-type="2" href="https://36kr.com/projectDetails/26593" target="_blank">豆瓣</a>也出现不同程度的故障，加载显示404、502等。</p> 
<p>B站崩了，才让大家发现原来“小破站”的流量如此惊人。上不了网站、没得看视频直播的“B站难民”冲向<a class="project-link" data-id="26201" data-name="知乎" data-logo="https://img.36krcdn.com/20210601/v2_18c28a54e2804ba7a33a63bd90d24aae_img_000" data-refer-type="1" href="https://www.36dianping.com/space/4688601213" target="_blank">知乎</a>、<a class="project-link" data-id="38685" data-name="微博" data-logo="https://img.36krcdn.com/20210302/v2_f2cb7018ead34f4f9712a4e4fe4fc982_img_000" data-refer-type="2" href="https://36kr.com/projectDetails/38685" target="_blank">微博</a>以及著名游戏网站NGA。“b站崩了”“陈睿”“豆瓣崩了”等词迅速走红，甚至连B站名梗“蒙古上单”也一同霸榜微博热搜，传遍全网，颇为壮观。</p> 
<p class="image-wrapper"><img data-img-size-val="1170,741" src="https://img.36krcdn.com/20210714/v2_2f1349764b0f4c5fa407d1f50b9aeeb8_img_jpeg" referrerpolicy="no-referrer"></p> 
<p class="img-desc">微博热搜</p> 
<p>23时45分，B站网页端和App才初步恢复正常访问，但像直播、会员购等板块，以及一些站内互动、评论、投币功能，还无法正常使用。</p> 
<p>B站崩溃后，许多故障页面截图在网上流传。但具体是什么导致服务器故障，多种说法迅速出现。不过，无论是最初的停电说，还是后面的B站大楼/上海云海服务器中心着火说，都被迅速辟谣。</p> 
<p class="image-wrapper"><img data-img-size-val="1246,832" src="https://img.36krcdn.com/20210714/v2_eb554cb6f65c406e8fdb58ed252fe542_img_png" referrerpolicy="no-referrer"></p> 
<p class="img-desc">上海消防对B站总部大楼着火一事辟谣</p> 
<p>直到凌晨2点20分，B站正式发布声明，表示因部分服务器机房发生故障，造成无法访问，经过排查修复后，现已陆续恢复正常。不过，更具体的原因是什么，B站还未披露。</p> 
<h3>服务器崩溃数小时，灾备没做好？</h3> 
<p>企业IT架构越来越复杂，这也意味着故障原因往往是系统性问题，难以单一归因。<strong>此次B站崩溃，除了服务器出问题，补救的备份方案大概率也没有快速应用到位。</strong></p> 
<p>故障通常可从硬件故障和软件故障两方面来分析——硬件故障即是机房、服务器等物理因素；而软件故障则有可能来自版本升级、代码bug等带来的影响。</p> 
<p>尽管不同行业有差异，但大互联网平台的技术架构，核心组件基本不会少。最简单的访问路径就是客户端和网站直接交互，比如一个视频访问请求从用户端发出，经过一系列处理后到达B站的前端、后端服务器、分布式存储等多个组件，B站处理完请求后再返回。</p> 
<p><strong>而当晚的情况是，B站崩溃，网友们收到的页面大多显示502，基本可以确定是服务器故障导致。</strong></p> 
<p>但具体是哪些服务器故障，目前还不清楚。B站这般体量的视频平台，上云是肯定的，也都会采用公有云+私有<a class="project-link" data-id="441713" data-name="云架构" data-logo="https://img.36krcdn.com/20201106/v2_8a06a6a4a6e84a44871a0bff30dc94c8_img_000" data-refer-type="2" href="https://36kr.com/projectDetails/441713" target="_blank">云架构</a>。也就是说，出故障的服务器有可能在B站自己或托管的机房，也有可能在公有云服务商的机房。</p> 
<p>若自家机房出问题，一个可能原因是，版本升级、网站维护失败，导致用版本回滚紧急解决。若没上云的刚好是核心业务，还需要运维人员手动修复，耗时就很长了。知乎答主“k8seasy”就认为，B站核心业务恢复时间在30分钟左右，并且几乎100%恢复，说明应是B站某个核心组件崩溃，导致核心服务不可用。有可能的原因是B站上线新版本时有bug，不可用后，紧急回滚到老版本也没扛住访问压力，最后网站环境崩溃。</p> 
<p><strong>若公有云厂商出问题，那么同一个服务器集群服务的其他企业，也会出现类似问题。</strong>但当晚的A站、晋江、豆瓣等大流量app都很快恢复了服务，故障程度和B站也不是同一个量级。再者，为B站提供云服务的厂商囊括了<a class="project-link" data-id="8432" data-name="阿里云" data-logo="https://img.36krcdn.com/20210714/v2_7a12d63dcfc34d72b15c799eb4320e74_img_000" data-refer-type="1" href="https://www.36dianping.com/space/4469601233" target="_blank">阿里云</a>、<a class="project-link" data-id="24961" data-name="腾讯" data-logo="https://img.36krcdn.com/20201201/v2_016524a9a477434cb3584e1558f3257a_img_000" data-refer-type="2" href="https://36kr.com/projectDetails/24961" target="_blank">腾讯</a>云、<a class="project-link" data-id="27570" data-name="京东" data-logo="https://img.36krcdn.com/20210326/v2_db3fecea1d71451684d4e5294b883fe5_img_000" data-refer-type="2" href="https://36kr.com/projectDetails/27570" target="_blank">京东</a>云、<a class="project-link" data-id="5856" data-name="金山云" data-logo="https://img.36krcdn.com/20210714/v2_9820cb0ea39f4cfc8bba19ba6872fc8d_img_000" data-refer-type="1" href="https://www.36dianping.com/space/4876401230" target="_blank">金山云</a>，公有云厂商<a class="project-link" data-id="81906" data-name="一起" data-logo="https://img.36krcdn.com/20210709/v2_647b9860d6f7437caf1be2501d37698a_img_000" data-refer-type="1" href="https://www.36dianping.com/space/4772100123" target="_blank">一起</a>出问题的概率是极小的。</p> 
<p>分析完原因，再来看补救措施。服务器崩溃后的第一道防线，是企业的容灾和备份，这能够保证核心业务尽快恢复，最大程度减少损失。</p> 
<p><strong>B站当晚故障数小时也没完全恢复，显然灾备起的作用不太大，这道防线没能好好守住。</strong></p> 
<p>灾备等级一般可按同城/异地、备份中心数量等划分等级高低，选择不同备份方式（如热备/冷备/温备份，成本均不同），也会对恢复时间有所影响。一位云计算从业者对36氪表示：“类似B站这种体量的平台，灾备肯定有做，但就是没经受住考验。比如数据备了但机器没备，或者机器备了但链路没备，差一个环节，就难以在短时间内恢复。”</p> 
<p>作为视频直播平台，B站对高可用/高并发的要求是很高的。企业灾备服务商、<a class="project-link" data-id="50855" data-name="英方软件" data-logo="https://img.36krcdn.com/20210714/v2_7480b61cf349491abf6add480f35c57e_img_000" data-refer-type="1" href="https://www.36dianping.com/space/4366001034" target="_blank">英方软件</a>市场总监黄亮对36氪表示，高可用架构主要有异地容灾、负载均衡两种，<strong>此次故障很有可能是B站只重点做了负载均衡，但没有做太多异地容灾。</strong>“当前企业做负载均衡，通常是采用同城数据中心的架构，如在上海的同一个数据中心里进行。”他表示。</p> 
<p><strong>灾备没及时起作用，可能是出于成本考虑。</strong>黄亮表示，负载均衡对实时性要求高，如果要上异地灾备，成本是很高的。比如，A企业在上海有数据中心，同时在贵州设立异地灾备中心。当上海机房宕机，贵州可以接管。对稳定性要求较高的行业，如银行、医院等，监管会有强制要求，其他企业一般是量力而行。</p> 
<h3>脆弱的企业IT架构，未来要如何演变？</h3> 
<p>B站此次故障，从虽然恢复时间达数小时，但幸运的是，故障发生在深夜的流量低谷，网友们的助推则让B站再次出圈：一个网站崩溃，其巨大流量竟能让其他网站也跟着出现故障。</p> 
<p>这让市场看到了B站用户可怕的冲浪能力。7月13日，B站股价经历短线走低，盘中一度涨幅收窄，最低至3.26%。截至收盘还能保持涨幅3.18%，报110.38美元/股。截至发稿，B站市值为424亿美元。</p> 
<p class="image-wrapper"><img data-img-size-val="1322,762" src="https://img.36krcdn.com/20210714/v2_b526e2b6f89c48f1b06c793d825adfa0_img_png" referrerpolicy="no-referrer"></p> 
<p class="img-desc">B站股价走势 来源：富途牛牛</p> 
<p><strong>类似这样的宕机事件，突显出当下企业IT架构的脆弱。</strong>随着数字社会越来越成熟，企业IT架构一环扣一环，一个环节出现问题，就有可能一发而动全身，造成巨大损失。</p> 
<p>信息安全问题也是防不胜防。2020年，<a class="project-link" data-id="8390" data-name="微盟" data-logo="https://img.36krcdn.com/20210518/v2_c2c5d4791a584f3cb1200e2960da3f98_img_000" data-refer-type="1" href="https://www.36dianping.com/space/4731201232" target="_blank">微盟</a>一核心运维员工对核心生产环境和数据进行删除，最后微盟公司花费超过2260万元用于支付数据恢复、商务赔偿、员工加班费用等。因删库事件，微盟股价跌幅超过8%，一夜损失将近11亿元。而2019年3月，<a class="project-link" data-id="3968996" data-name="谷歌" data-logo="https://img.36krcdn.com/20200916/v2_811751a081924fa9af8741ce120bd7bf_img_png" data-refer-type="2" href="https://36kr.com/projectDetails/3968996" target="_blank">谷歌</a>云、阿里云、腾讯云就相继发生大规模宕机，腾讯云宕机的4小时内，仅腾讯游戏就损失高达千万元。</p> 
<p>企业安全是实战出来的。经过微盟删库一事后，恐怕当前国内企业安全不会再给运维人员如此核心的权限。阿里云也是在经历<a class="project-link" data-id="594793" data-name="支付宝" data-logo="https://img.36krcdn.com/20200729/v2_1009568d151d4277b0b1becfabe54a2f_img_000" data-refer-type="2" href="https://36kr.com/projectDetails/594793" target="_blank">支付宝</a>527光纤挖断事件后，痛定思痛将可用性再提升一个数量级。</p> 
<p>而如何考虑放在灾备中的运维成本？企业首先需要根据自身条件开始计算——哪些物理威胁或灾难企业无法承受，并对资产价值进行分析，确定恢复的优先级顺序，确定灾备方案。</p> 
<p>灾备演练也很重要。以B站事件为例，数据和系统的恢复进度和灾备预案熟悉程度息息相关。黄亮表示，如银行、证券、医院等关键单位，基本定期做容灾演练，才能保证服务的稳定性。随着网络安全法、数据安全法的进一步推动实施，以后企业的IT架构合规要求只会越来越严，企业要想偷懒也不太可能了。</p> 
<p>企业与各种故障和威胁搏斗的故事无止境。灾备一事，丰俭由人，本质还是看公司如何算账，愿意投入多少。B站崩了对各大企业的最大启示，也就是把“重视企业IT安全”写在明面上了。</p>  
</div>
            
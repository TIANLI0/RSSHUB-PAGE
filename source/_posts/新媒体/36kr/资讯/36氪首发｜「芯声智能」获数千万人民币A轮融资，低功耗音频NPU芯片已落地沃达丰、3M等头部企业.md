
---
title: '36氪首发｜「芯声智能」获数千万人民币A轮融资，低功耗音频NPU芯片已落地沃达丰、3M等头部企业'
categories: 
 - 新媒体
 - 36kr
 - 资讯
headimg: 'https://img.36krcdn.com/20220106/v2_e998d171d06a4148b809d717f38a262e_img_jpeg'
author: 36kr
comments: false
date: Fri, 07 Jan 2022 01:00:36 GMT
thumbnail: 'https://img.36krcdn.com/20220106/v2_e998d171d06a4148b809d717f38a262e_img_jpeg'
---

<div>   
<p>作者｜韦世玮</p> 
<p>编辑｜石亚琼</p> 
<p>**</p> 
<p>36氪获悉，近日音频NPU芯片及算法公司「<a class="project-link" data-id="436726" data-name="芯声智能" data-logo="https://img.36krcdn.com/20210812/v2_ae65498c9f8e47508cb8feb4b4210008_img_000" data-refer-type="2" href="https://36kr.com/projectDetails/436726" target="_blank">芯声智能</a>」宣布完成数千万人民币A轮融资，由光远资本独家投资，戈杨资本担任本轮独家财务顾问。该轮资金将主要用于扩充研发人员和技术支撑团队，以及芯片迭代的研发投入。</p> 
<p>芯声智能成立于2018年9月，主要基于自主研发的可重构神经网络引擎，开发面向智能语音识别领域的AI芯片及算法，具有高性能、超低功耗、高识别率、低成本、算法扩展性强等特点，适用于智能手机、耳机、白色家电等品类。</p> 
<p>声学赛道的覆盖面十分广泛，人们日常使用的智能手机、蓝牙耳机、智能音箱等设备，在听歌、通话、语音交互等一切和声音有关的应用背后，都需要对声音信号进行环环相扣的处理，同时也有着<a class="project-link" data-id="3969340" data-name="一条" data-logo="https://img.36krcdn.com/20200916/v2_811751a081924fa9af8741ce120bd7bf_img_png" data-refer-type="2" href="https://36kr.com/projectDetails/3969340" target="_blank">一条</a>长长的元器件供应链。</p> 
<p>例如，语音识别、语音助手、通话降噪应用主要涉及声音的前处理，与麦克风有关，设备的音质、主动降噪、音效，主要涉及声音的后处理，则与喇叭有关。</p> 
<p>但芯声智能CEO汤健告诉36氪，他发现目前业内许多玩家设计语音芯片时，大多侧重在前处理应用的技术创新，而后处理环节仍是传统方法。因此，公司的初衷是能设计出一款同时兼顾声音前处理和后处理的语音芯片。</p> 
<p>那么，公司为何选择从NPU（嵌入式神经网络处理器）切入？一方面，大型SoC的研发周期长、成本高，对初创公司来说落地门槛较大；另一方面，产品主要面向低功耗、锂电供电的场景，主控芯片跑算法的功耗太高，因此比较适合开发一款NPU芯片，作为协处理器与主控芯片进行配合。</p> 
<p>目前，芯声智能的低功耗语音芯片XS200X已实现量产出货，这是一款专用的语音识别前端芯片，基于RISC-V架构，采用小型化神经网络设计，突破了超低功耗ADC、低功耗PLL系统设计、低功耗数字系统设计、小型化封装等多个难点。</p> 
<p>具体来看，XS200X芯片拥有四大特点：一是采用超低功耗设计，支持Always on唤醒模式，唤醒功耗小于1mW；二是具有远场识别高强度计算能力，支持AGC、AEC、波速成型、去混响、复杂降噪、多命令词识别等14种算法，其中KWS唤醒率在无噪达98%以上；三是基于DNN+CNN神经网络降噪算法，能较好实现通话降噪（ENC）和主动降噪（ANC）效果；四是配置了4麦克风接口，支持多路模拟MIC输入或多路数字MIC输入，支持多通道TDM（I2S）输入和输出。</p> 
<p class="image-wrapper"><img data-img-size-val="1080,1440" src="https://img.36krcdn.com/20220106/v2_e998d171d06a4148b809d717f38a262e_img_jpeg" referrerpolicy="no-referrer"></p> 
<p class="img-desc">芯声智能的超低功耗语音唤醒识别芯片</p> 
<p>基于这些特点，芯声智能的语音降噪方案能很好地解决大风噪场景下的降噪问题，这也是现在许多音频产品主要面临的难题。汤健举例，在摩托车车速为120码情况下，公司的单麦克风降噪解决方案能大幅度地过滤风噪和路噪，实现清晰通话，而业内知名厂商的蓝牙芯片方案最多只能实现30码车速的通话。</p> 
<p>在这背后，正是芯声智能采用神经网络降噪技术，通过对大风噪、马路、地铁、广场舞等场景下的6000多种噪音进行训练，大幅度地解决了各类噪声问题。</p> 
<p>从市场层面看，目前芯声智能主要对标美国DSP Group，后者为全球领先的通信语音<a class="project-link" data-id="604947" data-name="和无线" data-logo="https://img.36krcdn.com/20210814/v2_34569069b1494d338e6359a9909975e7_img_000" data-refer-type="2" href="https://36kr.com/projectDetails/604947" target="_blank">和无线</a>芯片组解决方案提供商，在音频数字信号处理器、AI内核、音频物联网无线芯片等方面有丰富技术经验。同时，该公司已于2021年8月被Synaptics公司宣布以5.28亿美元收购。</p> 
<p>汤健谈到，芯声智能核心团队从四年前就开始基于RISC-V架构开发芯片方案，积累下不少成本控制和技术开发经验，这恰恰是公司和其他玩家相比的差异化优势。</p> 
<p>一方面，市场上的玩家多采用Arm Cortex-M4F架构或Cadence的架构，产品开发需要支付IP专利费用，而芯声智能采用开源的RISC-V架构，所有模拟IP均为独立自主研发，能大大减少产品开发的成本；另一方面，市场上产品的同质化现象严重，而公司基于RISC-V架构开发芯片，能在实现产品差异化的同时，保证产品的功耗、算力、性能的一致性。</p> 
<p>业务方面，芯声智能拥有出行、对讲、声纹解锁、声源定位四个业务板块，每个版块相互结合实现落地。例如，出行<a class="project-link" data-id="236269" data-name="和对讲" data-logo="https://img.36krcdn.com/20210809/v2_2749555b14304d2e95f45e6e50f078db_img_000" data-refer-type="2" href="https://36kr.com/projectDetails/236269" target="_blank">和对讲</a>主要面向智能头盔市场，公司与<a class="project-link" data-id="27390" data-name="饿了么" data-logo="https://img.36krcdn.com/20210806/v2_7452bdcc09f64b6fad147c9681b0af5c_img_000" data-refer-type="2" href="https://36kr.com/projectDetails/27390" target="_blank">饿了么</a>合作为骑手开发智能头盔，让骑手可直接通过语音交互完成订单处理、打电话等工作；声源定位则主要瞄准直播、视频电话会议领域。</p> 
<p>现阶段，公司的XS200X芯片已完成多家芯片/软件平台商的联合调优和参考设计，并在智能手机、智能耳机、智能头盔、车载音频、低延时直播、电话会议等市场均有落地，其中合作伙伴不乏沃达丰、3M、哈曼、五菱科技、饿了么等国内外头部企业。</p> 
<p class="image-wrapper"><img data-img-size-val="1080,556" src="https://img.36krcdn.com/20220106/v2_d31f549a69b040dfb741842b4fcdc896_img_jpeg" referrerpolicy="no-referrer"></p> 
<p class="img-desc">公司与饿了么合作开发的智能头盔</p> 
<p>成立至今，芯声智能的累计研发投入已超3000万人民币，目前有芯片销售和算法销售两种盈利模式。其中，2021年芯片出货量规模数十万颗，主要落地智能头盔、对讲机/会议音箱、耳机领域；算法则销售单麦神经网络降噪算法和双麦降噪算法，现阶段该模式仅适合恒玄科技和诺达的蓝牙芯片平台。</p> 
<p>接下来一年，芯声智能将重点推广离线声纹识别功能，覆盖身份认证、辅助解锁等应用。同时，公司预计今年在智能头盔、对讲机领域的芯片出货量，将分别实现数百万颗出货规模。</p> 
<p>团队方面，芯声智能的核心团队具备从芯片到算法多领域的关键技术能力和量产经历，以及丰富的技术和销售经验，平均从业经历超15年。其中，公司董事长姜黎为东京工业大学工科博士，拥有20 年以上芯片开发经验，曾任<a class="project-link" data-id="151482" data-name="富士通" data-logo="https://img.36krcdn.com/20200916/v2_811751a081924fa9af8741ce120bd7bf_img_png" data-refer-type="2" href="https://36kr.com/projectDetails/151482" target="_blank">富士通</a>半导体GM和国科微CTO兼董事，以及国家相关重大科技项目负责人，至今累计申请专利100余项，累计开发并量产芯片超20款；公司创始人、CEO汤健曾任国科微CMO，并曾在<a class="project-link" data-id="28245" data-name="创毅视讯" data-logo="https://img.36krcdn.com/20210806/v2_ec5297b977c44573b55fa39e5d295e8e_img_000" data-refer-type="2" href="https://36kr.com/projectDetails/28245" target="_blank">创毅视讯</a>、中普微、天津诺思担任销售总监，拥有十余年芯片销售经历和团队、渠道管理经验。</p>  
</div>
            

---
title: '7个步骤，学懂APP客户端数据埋点'
categories: 
 - 新媒体
 - 人人都是产品经理
 - 热门文章
headimg: 'https://cors.zfour.workers.dev/?http://image.woshipm.com/wp-files/img/55.jpg'
author: 人人都是产品经理
comments: false
date: Tue, 13 Jun 2017 00:00:00 GMT
thumbnail: 'https://cors.zfour.workers.dev/?http://image.woshipm.com/wp-files/img/55.jpg'
---

<div>   
<img data-action="zoom" src="https://cors.zfour.workers.dev/?http://image.woshipm.com/wp-files/img/55.jpg" referrerpolicy="no-referrer"><blockquote><p>文章为大家分析了数据分析的第一步：数据埋点的实操方法。希望大家可以有所收获。</p></blockquote>
<p style="text-align: center;">
</p><p>如果你遇到了下面这些问题，那么看这篇就对了。</p>
<ol>
<li><strong>领导说，APP需要加一下统计，你负责搞定</strong></li>
<li><strong>研发说，APP需要统计哪些地方，你列一下埋点需求</strong></li>
<li><strong>研发说，APP的数据统计SDK用哪家的？你选好了注册一下</strong><strong>、运营说，咱们的APP都能看哪些数据？平台在哪？怎么查首页的UV？</strong></li>
</ol>
<p>作为一名产品经理，数据分析是一个基本能力，在各大学习社群和论坛，经常会遇到各种各样类似的问题和数据分析的教程贴。</p>
<p>数据分析是一个很复杂的工作，很多人在谈如何挖掘数据，做用户画像，设计数据漏斗，如何负责用户生命周期管理，但发现很多人却卡在了数据分析的第一步，那就是如何做数据埋点。</p>
<p>我今天和大家谈下数据埋点的实操方法，我们花<strong>10</strong>分钟时间，学会如何走出第一步。</p>
<p><strong>我们分3个部分来谈：</strong></p>
<ol>
<li>什么是数据埋点</li>
<li>如何埋点</li>
<li>埋点后能看到什么数据</li>
</ol>
<h2 id="toc-1">一、什么是数据埋点</h2>
<p><strong>一款APP在开发完成后， 一定需要看数据，来分析用户量，访问量，点击量，转化率等等这些指标。</strong></p>
<p>想看数据，就需要先做好数据埋点。</p>
<p>每个公司的情况不同，大的公司有自己的数据分析系统，很多公司都会采用第三方的数据分析平台来进行数据收集和分析。所以我们需要先了解都有哪些数据分析的网站。</p>
<p><strong>HTML</strong>网站和<strong>APP</strong>的数据分析平台和埋点方式是不同的，所以大家不要混淆。</p>
<p>我们今天谈<strong>APP</strong>的数据分析网站和方法。</p>
<p><strong>常用的APP数据分析网站:</strong></p>
<ol>
<li><strong>百度移动统计</strong></li>
<li><strong>友盟</strong></li>
<li><strong>诸葛IO</strong></li>
</ol>
<h2 id="toc-2">二、如何埋点</h2>
<p>埋点不管是用那家的平台，基本思路都是一样的，我们今天给大家一个通用的思路和方法。可以让大家快速的试验和动起来。</p>
<p>首页降峰老师先明确下完成一个<strong>APP</strong>数据埋点的几个步骤：</p>
<ol>
<li><strong>注册一家统计网站</strong></li>
<li><strong>新建应用</strong></li>
<li><strong>获取KEY和SDK代码包</strong></li>
<li><strong>将埋点需求和SDK包发给研发</strong></li>
<li><strong>自定义埋点需求完善</strong></li>
<li><strong>研发开发并完成APP上线</strong></li>
<li><strong>在后台查看数据</strong></li>
</ol>
<p>每一步有些细节和注意事项和大家说下，让大家避免一些坑：</p>
<h3><strong>1、注册账号</strong></h3>
<p>建议用公司邮箱或者公用邮箱注册，别用自己的私人邮箱和手机号码，后续一旦有交接和工作变动时会比较麻烦。</p>
<h3><strong>2、新建应用</strong></h3>
<p>登录后一般都有“新建应用”，可以选标准统计，大部分APP都选这个。游戏的app另说。</p>
<p>名称写自己app的名称，分类自己选1个。选错了也不影响。</p>
<p>平台根据情况自己选。后期我们看数据和埋点都是ios和安卓分开的，所以你如果2个端都做，就一起都选上。</p>
<p>描述可选，不用填。</p>
<p><img data-action="zoom" class="aligncenter" src="https://cors.zfour.workers.dev/?http://image.woshipm.com/wp-files/2017/06/e95eIckvJn4wX7MelEnR.png" alt width="430" height="328" referrerpolicy="no-referrer"></p>
<p>点击创建应用，完成。</p>
<h3><strong>3、获取KEY和SDK代码包</strong></h3>
<p>完成后可以得到2个APPKEY。分别是ios和安卓的。</p>
<p>这里的appkey很重要，你可以下载了给研发，也可以稍后让研发自己登录进来自己下载。</p>
<p>ios和安卓是分开2个独立的，后续埋点和看数据都是分开的。这个切记。</p>
<p>这时候，重点来了。</p>
<p>此时，如果我们只想看 APP的活跃用户，留存用户，下载量。用户地域分布，渠道分布，那么其实就够了。</p>
<h3><strong>4、将埋点需求和SDK包发给研发</strong></h3>
<p>你这时候，就把刚才获得的appkey和sdk包的下载地址，发给研发。或者直接把账号和密码发给研发。然后告诉研发，集成下百度移动统计的SDK包。这样发版后，就可以看到大部分数据了。</p>
<p><strong>如下的数据都可以看到：</strong></p>
<p style="text-align: center;"><img data-action="zoom" class="aligncenter" src="https://cors.zfour.workers.dev/?http://image.woshipm.com/wp-files/2017/06/kVMeuelxkN1JQxXySKXW.png" alt width="158" height="408" referrerpolicy="no-referrer"></p>
<p>但是，其实往往我们的数据需求远远不局限这些，我们还需要看每个页面的转化率，页面里面的行为按钮的点击次数，弹层的展示次数等更细节的数据。这样才能更好的知道用户的行为和操作流程的后期改进优化。</p>
<p>那么我们还需要进行第5步。自定义事件完善。 不做这步，这些数据是看不到的。</p>
<h3><strong>5、自定义事件完善</strong></h3>
<p><strong>比如我们想看页面里面 注册 搜索按钮，顶部banner，底部 首页和 我的 2个导航条的点击量。</strong></p>
<p>一个埋点事件对应1个按钮或者一个页面或者一个弹层。 你来定义。</p>
<p>如果埋点比较多，你也可以批量添加。批量添加的时候，您需要下载excel模板，按照要求填写好，上传进来即可。具体一看便知。</p>
<p>添加完成后就可以把这个列表导出或者人肉复制出来一个表格。发给研发。并附上你的原型图。做好对应关系标注。</p>
<h3><strong>6、研发开发并完成APP上线</strong></h3>
<p>完成上面几步后，研发哥哥就可以看懂进入第7步研发阶段了。</p>
<h3><strong>7、在后台查看数据</strong></h3>
<p>上线后就可以看到数据了。大部分数据一般隔天更新。</p>
<h2 id="toc-3"> 三、埋点后能看到什么数据</h2>
<p>上面提到，按照步骤完成数据分析<strong>sdk</strong>集成和自定义事件后，就可以看到数据了。</p>
<p>不添加自定义事件，可以看到基础数据，添加后，可以看到更细节的按钮，页面等点击数据。</p>
<p>查看自定义事件埋点数据，还是进入刚才的“事件分析”页面，点击对应埋点即可看到数据。</p>
<p>可以筛选时间段。</p>
<p><strong>下图就是 app首页的banner图的分析结果页面。</strong></p>
<p>（教程的事件是新建的，所以暂无数据）</p>
<p><img data-action="zoom" class="aligncenter" src="https://cors.zfour.workers.dev/?http://image.woshipm.com/wp-files/2017/06/WCIGG2qdsBwE5InunDuS.png" alt width="748" height="300" referrerpolicy="no-referrer"></p>
<p>除了这些外，如果你还想看 几个页面之间的转化路径和数据漏斗。那还需要添加“转化分析”。</p>
<p>添加转化分析后，可以看到例如: 进入首页-点击注册按钮-进入注册成功页 这几步的转化率和流失率。会自动生成一个转化分析图。当然你也可以分别看这几个页面的数据，自己去分析汇总。</p>
<p>进阶的方法还有把事件埋点配合转化分析、访问路径、转化漏斗等工具使用，从点到面地了解用户的使用行为、APP存在的问题。</p>
<p>更多深入的数据分析，还需要大家自己在数据的基础上，进行深加工和分析。数据只是基础，更多的还需要我们人肉去洞察背后的原因和分析结论。</p>
<p>好了，希望大家学会了。</p>
<p>欢迎交流。</p>
<p> </p>
<p>作者：降峰，十年产品人，百度金融资深产品经理。</p>
<p>本文由@降峰 原创发布于人人都是产品经理，未经许可，禁止转载。</p>
<div class="support-author"><div class="support-title">给作者打赏，鼓励TA抓紧创作！</div><button class="button--pay" data-post-id="689019" data-author="150790" data-avatar="http://image.woshipm.com/wp-files/2019/03/YzYDqd3lfMVAzIqb0as9.png"><svg width="13" height="16" class="svgIcon--use" viewBox="0 0 13 16"><path d="M9.113,4.571 C9.951,3.771 10.895,2.742 10.685,2.057 C10.475,1.485 10.056,0.799 9.427,0.571 C8.903,0.342 8.379,0.456 7.750,0.799 C7.540,0.342 7.016,0.114 6.596,-0.001 C5.863,-0.001 5.234,0.228 4.814,0.914 C4.080,0.571 3.451,0.685 2.927,1.028 C2.613,1.256 2.298,1.713 2.298,2.628 C2.298,3.542 3.137,4.228 3.766,4.685 C2.508,5.599 -0.218,7.885 -0.008,12.228 C-0.218,15.656 2.613,15.999 2.613,15.999 L10.371,15.999 C11.314,15.885 12.991,14.971 12.991,12.571 L12.991,12.228 C13.201,7.771 10.371,5.371 9.113,4.571 L9.113,4.571 ZM8.932,11.835 L6.940,11.835 L6.940,13.207 C6.940,13.435 6.731,13.549 6.521,13.549 C6.311,13.549 6.102,13.435 6.102,13.207 L6.102,11.835 L4.110,11.835 C3.900,11.835 3.795,11.606 3.795,11.378 C3.795,11.149 3.900,10.921 4.110,10.921 L6.102,10.921 L6.102,10.121 L4.949,10.121 C4.739,10.121 4.634,9.892 4.634,9.664 C4.634,9.435 4.739,9.206 4.949,9.206 L5.892,9.206 L4.739,7.950 C4.634,7.835 4.739,7.606 4.949,7.492 C5.158,7.378 5.368,7.264 5.473,7.378 L6.521,8.635 L7.674,7.264 C7.779,7.149 7.989,7.264 8.198,7.378 C8.408,7.492 8.408,7.721 8.408,7.835 L7.150,9.321 L8.094,9.321 C8.303,9.321 8.408,9.549 8.408,9.778 C8.408,10.007 8.303,10.235 8.094,10.235 L6.940,10.235 L6.940,11.035 L8.932,11.035 C9.142,11.035 9.247,11.264 9.247,11.493 C9.247,11.606 9.037,11.835 8.932,11.835 L8.932,11.835 Z"/></svg>
赞赏</button><div class="pay-num">10人打赏</div><div class="donation-list"><div class="donation-item"><img class="avatar" src="https://static.woshipm.com/APP_U_201708_20170817190934_5525.jpeg?imageView2/1/w/80" height="32" width="32" referrerpolicy="no-referrer"></div><div class="donation-item"><img class="avatar" src="https://static.woshipm.com/APP_U_201708_20170817190934_5525.jpeg?imageView2/1/w/80" height="32" width="32" referrerpolicy="no-referrer"></div><div class="donation-item"><img class="avatar" src="https://image.woshipm.com/wp-files/2018/01/e0v3qcAMHIHxrAoUiJmq.jpg!/both/80x80" height="32" width="32" referrerpolicy="no-referrer"></div><div class="donation-item"><img class="avatar" src="https://static.woshipm.com/TTW_USER_R_201706_20170602175204_3348.png?imageView2/1/w/80" height="32" width="32" referrerpolicy="no-referrer"></div><div class="donation-item"><img class="avatar" src="https://static.woshipm.com/TTW_USER_R_201706_20170602183237_2514.jpg?imageView2/1/w/80" height="32" width="32" referrerpolicy="no-referrer"></div><div class="donation-item"><img class="avatar" src="https://static.woshipm.com/TTW_USER_R_201706_20170602175118_4439.jpg?imageView2/1/w/80" height="32" width="32" referrerpolicy="no-referrer"></div><div class="donation-item"><img class="avatar" src="https://static.woshipm.com/TTW_USER_R_201706_20170602182956_5421.jpg?imageView2/1/w/80" height="32" width="32" referrerpolicy="no-referrer"></div><div class="donation-item"><img class="avatar" src="https://static.woshipm.com/TTW_USER_R_201706_20170602182743_2431.jpg?imageView2/1/w/80" height="32" width="32" referrerpolicy="no-referrer"></div><div class="donation-item"><img class="avatar" src="https://static.qidianla.com/woshipm_def_head_1.jpg" height="32" width="32" referrerpolicy="no-referrer"></div><div class="donation-item"><img class="avatar" src="https://static.woshipm.com/TTW_USER_R_201706_20170602175055_4275.jpg?imageView2/1/w/80" height="32" width="32" referrerpolicy="no-referrer"></div></div></div>                      
</div>
            
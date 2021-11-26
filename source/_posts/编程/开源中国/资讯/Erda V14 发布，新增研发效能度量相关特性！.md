
---
title: 'Erda V1.4 发布，新增研发效能度量相关特性！'
categories: 
 - 编程
 - 开源中国
 - 资讯
headimg: 'https://static.oschina.net/uploads/space/2021/1126/181417_Qogf_5430600.png'
author: 开源中国
comments: false
date: Fri, 26 Nov 2021 10:16:00 GMT
thumbnail: 'https://static.oschina.net/uploads/space/2021/1126/181417_Qogf_5430600.png'
---

<div>   
<div class="content">
                                                                    
                                                        <p style="color:#333333; margin-left:0; margin-right:0; text-align:justify"><span style="color:#474444">近期，Erda 正式发布 1.4 版本，新增特性及改善事项共计 47 项，本次重点发布了研发效能度量统计相关特性，通过项目协同事项的度量分析，让团队或个人能够及时发现问题和风险，再通过问题下钻分析来帮助开发者高效解决问题，更多的内容欢迎广大开发者使用、体验 Erda v1.4！再次感谢为新版本做出贡献的社区小伙伴们，我们也会持续关注和采纳社区的建议，推动 Erda 项目的进一步发展，期待听到大家更多的反馈！</span></p> 
<p style="color:#333333; margin-left:0; margin-right:0; text-align:justify"><span style="color:#474444">下文是新版本中重点提升特性的进一步解读。</span></p> 
<h2>研发效能度量 - 缺陷统计分析</h2> 
<p style="color:#333333; margin-left:0; margin-right:0; text-align:justify"><span style="color:#474444">在产研全链路中，除了主线围绕应用研发持续高效迭代发布外，还有一条将产研过程中各角色串到同一平台进行高效协作的线也非常重要，为此，Erda 也在一直精研项目管理中各角色协同管理的产品特性。在以往版本中也陆续上线了项目需求目标规划、迭代和需求任务等事项的功能，但是这些功能特性仅仅算是完成基础特性。</span></p> 
<p style="color:#333333; margin-left:0; margin-right:0; text-align:justify"><span style="color:#474444">如何通过线上协同事项统计分析来帮助我们提高团队研发效率、提高产品质量等，即我们常说的研发效能度量分析，目前已成为业界热议话题。1.4 版本中，我们针对缺陷发布了研发效能度量 - 缺陷维度的统计分析特性。该特性主要围绕两个视角进行展开：团队和个人的视角。不管对于团队和个人，通过度量分析的目的都是为了发现问题和解决问题，最终达到高效生产的同时提升自身的能力。本次的缺陷统计分析，我们主要从四个维度进行分析：</span></p> 
<ul style="margin-left:0; margin-right:0"> 
 <li> <p style="margin-left:0; margin-right:0"><strong><span style="color:#474444">质量趋势</span></strong><span style="color:#474444">：通过一段时间内的缺陷新增、关闭的趋势，帮助团队或个人分析整理质量趋势；</span></p> </li> 
 <li> <p style="margin-left:0; margin-right:0"><strong><span style="color:#474444">缺陷属性分布</span></strong><span style="color:#474444">：通过质量趋势的判断，可以下钻到缺陷属性分布，利用多维度的分布来分析缺陷的分布情况，维度包含迭代缺陷状态、复杂度、引入源、优先级、缺陷标签等；</span></p> </li> 
 <li> <p style="margin-left:0; margin-right:0"><strong><span style="color:#474444">人员分布</span></strong><span style="color:#474444">：接下来进一步通过团队标签维度的分析下钻，让每个模块团队能够通过团队成员筛选的方式又从上到下进行团队质量的统计分析；</span></p> </li> 
 <li> <p style="margin-left:0; margin-right:0"><strong><span style="color:#474444">缺陷分析</span></strong><span style="color:#474444">：最后通过缺陷的响应时间和解决时间来评估缺陷解决的效率。</span></p> </li> 
</ul> 
<h2><strong>研发效能度量 - 测试统计分析</strong></h2> 
<p style="color:#333333; margin-left:0; margin-right:0; text-align:justify"><span style="color:#474444">与此同时，新版本还发布了测试统计分析。在做这个之前，测试同学都是单点去查看单个执行计划的情况，没有一个全局视角去关注测试计划的执行率、通过率等信息，更不能发现提炼哪些测试用例的耗时是最需要优化的、哪些测试用例是最容易出错的。为了解决上述问题，我们做了以下三个维度的统计分析：</span></p> 
<ol style="margin-left:0; margin-right:0"> 
 <li> <p style="margin-left:0; margin-right:0"><strong><span style="color:#474444">整体质量提炼归纳总分</span></strong><span style="color:#474444">：质量分由自动化测试、手动测试、缺陷重开率、遗留缺陷、代码覆盖率的 DI 值 5 个维度构成综合计算的一个得分，代表产品在某个迭代或版本的综合质量情况。</span></p> </li> 
 <li> <p style="margin-left:0; margin-right:0"><strong><span style="color:#474444">测试通过率的趋势</span></strong><span style="color:#474444">：测试包含手动测试和自动化测试。</span></p> </li> 
</ol> 
<ol style="margin-left:0; margin-right:0"> 
 <li> 
  <ol style="list-style-type:lower-alpha; margin-left:0; margin-right:0"> 
   <li> <p style="margin-left:0; margin-right:0"><span style="color:#474444">手动测试计划的进展分布能够直观展示冒烟提测、手动测试等阶段的时间分布和测试用例的执行、通过情况，方便及时发现测试风险并对其进行改善。</span></p> </li> 
   <li> <p style="margin-left:0; margin-right:0"><span style="color:#474444">自动化测试主要是自动化测试用例通过率和执行率的走势分析，针对执行耗时的计划，可以通过计划中各节点执行时间瀑布图进行分析耗时分布点及需要改善的空间。</span></p> </li> 
  </ol> </li> 
</ol> 
<ol start="3" style="margin-left:0; margin-right:0"> 
 <li> <p style="margin-left:0; margin-right:0"><strong><span style="color:#474444">自动化测试用例通过率、失败率、平均耗时分布</span></strong><span style="color:#474444">：主要是帮助用例的编写维护人员发现用例的不足之处，及时改善相关问题。</span></p> </li> 
</ol> 
<h2><strong>研发效能度量 - 代码覆盖率</strong></h2> 
<p style="color:#333333; margin-left:0; margin-right:0; text-align:justify"><span style="color:#474444">在研发效能度量中，大家对于代码覆盖率的统计往往存在褒贬不一的声音，过度单一追求代码覆盖率可能会造成很多无效刷代码覆盖率的测试用例。但在效能度量指标覆盖时，往往会多个指标相互制约确认，就像生态圈中食物链一样，只有网状循环的才是良性生态系统，效能度量指标其实也是一样的道理，为此我们再结合缺陷质量分析和代码覆盖率能形成相互制约和呼应。</span></p> 
<p style="color:#333333; margin-left:0; margin-right:0; text-align:justify"><span style="color:#474444">在 Erda 代码覆盖率统计特性的产品全流程化中，完全通过中间件服务的方式引入，真正让用户按需使用，可以在 Erda.yml 编排中便捷引入，具体引入步骤如下：</span></p> 
<ul style="list-style-type:disc; margin-left:0; margin-right:0"> 
 <li> <p style="margin-left:0; margin-right:0"><strong><span style="color:#474444">Step1</span></strong><span style="color:#474444">：</span><span style="color:#474444">在应用的 erda.yml 中引用选择 sourcecov addon。</span></p> </li> 
</ul> 
<ul style="list-style-type:disc; margin-left:0; margin-right:0"> 
 <li> <p style="margin-left:0; margin-right:0"><strong><span style="color:#474444">Step2</span></strong><span style="color:#474444">：执行应用流水线进行部署，部署完成后检查代码覆盖率 Addon 的部署情况。</span></p> </li> 
</ul> 
<p style="margin-left:0; margin-right:0"><img alt height="336" src="https://static.oschina.net/uploads/space/2021/1126/181417_Qogf_5430600.png" width="700" referrerpolicy="no-referrer"></p> 
<ul style="list-style-type:disc; margin-left:0; margin-right:0"> 
 <li> <p style="margin-left:0; margin-right:0"><strong><span style="color:#474444">Step3</span></strong><span style="color:#474444">：开始执行代码覆盖率统计计划，并且查看统计结果。</span></p> </li> 
</ul> 
<p><img alt height="366" src="https://static.oschina.net/uploads/space/2021/1126/181429_sGir_5430600.png" width="700" referrerpolicy="no-referrer"></p> 
<p><span style="color:#474444">操作详情请查看：</span></p> 
<p><span style="color:#7d71f1"><em><span style="color:#7d71f1">https://docs.erda.cloud/1.4/manual/dop/examples/deploy/e2e-code-coverage.html</span></em></span></p> 
<h2><strong>组织资源使用统计分析</strong></h2> 
<p style="color:#333333; margin-left:0; margin-right:0; text-align:justify"><span style="color:#474444">在多云管理平台中，组织资源通过 K8s 集群完成资源统一调度和管理，但组织内哪个项目使用资源最多，对组织 IT 主管分析当下资源投入及后续 IT 预算而言及其重要，所以此次我们针对组织中的资源统计分析提供了相应的解决方案，欢迎大家体验使用！</span></p> 
<p style="color:#333333; margin-left:0; margin-right:0; text-align:justify"><img alt height="366" src="https://static.oschina.net/uploads/space/2021/1126/181542_qm1g_5430600.png" width="700" referrerpolicy="no-referrer"></p> 
<p><span style="color:#474444">我们致力于决社区用户在实际生产环境中反馈的问题和需求，如果您有任何疑问或建议，欢迎添加小助手微信：</span><strong><span style="color:#7d71f1">Erda202106</span></strong><span style="color:#474444">，加入 Erda 用户群参与交流或在 Github 上与我们讨论！</span></p> 
<ul style="list-style-type:disc; margin-left:8px; margin-right:8px"> 
 <li> <p><strong><span style="color:#474444">Erda Github 地址</span></strong><span style="color:#474444">：</span></p> <p><span style="color:#7d71f1"><em><span style="color:#7d71f1">https://github.com/erda-project/erda</span></em></span></p> </li> 
 <li> <p><strong><span style="color:#474444">Erda Cloud 官网</span></strong><span style="color:#474444">：</span></p> <p><span style="color:#7d71f1"><em><span style="color:#7d71f1">https://www.erda.cloud/</span></em></span></p> </li> 
</ul>
                                        </div>
                                      
</div>
            
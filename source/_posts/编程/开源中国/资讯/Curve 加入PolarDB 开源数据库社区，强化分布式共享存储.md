
---
title: 'Curve 加入PolarDB 开源数据库社区，强化分布式共享存储'
categories: 
 - 编程
 - 开源中国
 - 资讯
headimg: 'https://oscimg.oschina.net/oscnet/up-e9117fdc5a3d2b76cb655809419f3062291.png'
author: 开源中国
comments: false
date: Wed, 02 Mar 2022 08:57:00 GMT
thumbnail: 'https://oscimg.oschina.net/oscnet/up-e9117fdc5a3d2b76cb655809419f3062291.png'
---

<div>   
<div class="content">
                                                                                            <p><span>Curve社区签署阿里巴巴开源CLA(Contribution License Agreement, 贡献许可协议), 正式与阿里云PolarDB 开源数据库社区牵手，成为继 </span><span>CurveFS 发布<span>之</span></span><span><span>后，</span>Curve 开源项目发展的又一里程碑。</span></p> 
<p style="margin-left:0; margin-right:0; text-align:center"><img height="143" src="https://oscimg.oschina.net/oscnet/up-e9117fdc5a3d2b76cb655809419f3062291.png" width="554" referrerpolicy="no-referrer"></p> 
<p><span>在3月2日的开源 PolarDB 企业级架构发布会上，阿里云对 PolarDB for PostgreSQL 的存储计算分离等架构设计进行了全面解读，作为 PolarDB 技术合作伙伴，Curve 为 PolarDB for PostgreSQL 提供分布式共享存储，其强大的性能表现引发了社区的注意。</span></p> 
<p><span>这也表明，作为网易数帆自研开源的第二款基础软件产品，Curve 正朝着高性能、易运维、全场景支持的云原生软件定义存储系统这一目标稳步演进。</span></p> 
<h2 style="margin-left:0px; margin-right:0px"><span><strong><span>打造性能最强开源分布式共享存储</span></strong></span></h2> 
<p><span>作为一款云原生分布式数据库产品，PolarDB for PostgreSQL 采用基于共享存储（Shared-Storage）的存算分离架构，以大幅提升资源利用率与性能，实现快速弹性应对突发业务负载的场景。数据存于“远端存储”的 Shared-Storage 共享方式，利于弹性的同时，也带来了网络和共享存储的挑战，因而必须突破 I/O 限制以确保业务所需的性能。</span></p> 
<p style="margin-left:0; margin-right:0; text-align:center"><img alt height="1055" src="https://oscimg.oschina.net/oscnet/up-72c8586967f27d0fc5618d16e760fb6085a.png" width="1901" referrerpolicy="no-referrer"></p> 
<p><span><span><span>在 </span>On-Premise（本地部署）环境下，开源存储是首选，然而能满足数据库性能需求的开源存储并不多。“我们尝试过多款（开源存储）软件作为分布式共享存储，Curve 的测试结果让我们眼前一亮。”</span><span style="color:#000000">PolarDB for PostgreSQL <span>研发负责人明虚</span>表示。</span></span></p> 
<p><span>Curve 当前由 CurveBS 和 CurveFS 两个子项目构成，分别提供块存储和文件存储两种能力。用做共享存储的正是 CurveBS，开源之初 CurveBS 就提供了远优于 某主流开源分布式块存储 的性能，经过社区一年多的的迭代，CurveBS 性能和稳定性愈发成熟。</span></p> 
<p><span>在 Curve 社区和 PolarDB 社区针对 PolarDB for PostgreSQL 场景的联合测试中，无论 benchmarkSQL 还是pgbench，Curve 再次全面领先于 该开源分布式块存储。同等硬件配置及数据库负载压力下，benchmarkSQL 测试中 Curve tpmC （每分钟事务数）领先高达 39%，pgbench 测试中 Curve 延迟降低多达 21%，TPS 领先高达 26%。</span></p> 
<p><span>Curve 的高性能得益于其采用了 chunkfilepool、条带化设计<span>、</span>Raft <span>等先进的技术架</span>构。</span><span style="color:#002bec"><strong><span>chunkfilepool</span></strong></span><span> <span>支持集群初始化时创建指定大小的文件，降低</span><span> </span>I/O 过程中文件元数据更新的开销，从而降低 I/O 延迟。</span><span style="color:#002bec"><strong><span>条带化设计</span></strong></span><span><span>则支持在</span><span> </span>Curve 客户端进行分片，以提高 I/O 的并发度和打散度，让更多节点参与 I/O 处理，提升 I/O 带宽。<span>而</span></span><span style="color:#002bec"><strong><span>Raft</span></strong></span><span> 一致性实现相对前述开源存储系统的强一致性来说，也缩短了长尾效应，因而缩短了 I/O 时延。</span></p> 
<p><span>此外，Curve 通过支持 PFS（PolarDB的分布式文件系统），使得云原生数据库更容易使用 Curve 分布式存储，并获取更好的性能。</span></p> 
<p><span>未来，Curve 社区还将从 braft 的 multi raft 改进、大 I/O 的性能优化、RDMA、io_uring 等方面着手，继续性能优化的工作。</span></p> 
<h2 style="margin-left:0px; margin-right:0px"><span><strong><span>践行开源云原生软件定义存储</span></strong></span></h2> 
<p><span>对 PolarDB for PostgreSQL 的良好支持，也体现了 Curve 对承载云原生工作负载的态度和进展。在当前数字化转型背景下，越来越多的企业通过软件重新定义了自己，云原生则是强化企业软件能力的重要武器——根据 CNCF 2020 全球云原生市场调查，该项技术已被 92% 受访者在生产中使用。</span></p> 
<p><span>在存储基础设施层，Curve 社区认为，不同于传统云存储资源的黑盒，云原生存储上一切存储资源应该都是白盒，所有云原生应用都可以不做修改无缝使用。</span></p> 
<p><span>基于此，云原生存储对上层云原生应用提供无缝的业务接口（POSIX接口、块存储接口、对象存储接口、HDFS接口等等），对下层云操作系统屏蔽云存储资源细节，对云原生应用的开发运维人员提供自定义存储类型、存储资源池（跨云）、数据生命周期管理、数据可靠性可用性策略等等。</span></p> 
<p><span>在 Curve Roadmap 中可以看到，这个开源社区正往这些方向努力。例如，支持云原生部署、运维、使用，已经是 Curve 的一个关键特性。事实上，Curve 架构简单、运维部署灵活的特点，也是其吸引 PolarDB 的又一重要因素。</span></p> 
<p><span style="color:#002bec"><strong><span style="color:#002bec">了解更多</span></strong></span></p> 
<ul style="list-style-type:disc; margin-left:0; margin-right:0"> 
 <li> <p style="margin-left:0; margin-right:0; text-align:left"><span>Curve 项目主页：</span></p> <p style="margin-left:0; margin-right:0; text-align:left"><span style="color:#003884">http://www.opencurve.io/</span></p> </li> 
 <li> <p style="margin-left:0; margin-right:0; text-align:left"><span>Curve 源码&文档：</span></p> <p style="margin-left:0; margin-right:0; text-align:left"><span><span style="color:#003884">https://github.com/opencurve/curve</span></span></p> </li> 
 <li> <p style="margin-left:0; margin-right:0; text-align:left"><span><span>Curve Roadmap：</span></span></p> <p style="margin-left:0; margin-right:0; text-align:left"><span><span style="color:#003884">https://github.com/opencurve/curve/wiki/Roadmap_CN</span></span></p> </li> 
 <li> <p style="margin-left:0; margin-right:0; text-align:left"><span>Curve 技术专栏：</span></p> <p style="margin-left:0; margin-right:0; text-align:left"><span style="color:#003884">https://zhuanlan.zhihu.com/p/311590077 </span></p> </li> 
 <li style="text-align:left"> <p style="margin-left:0; margin-right:0; text-align:left"><span>PolarDB for PostgreSQL 开源项目主页：</span></p> <p style="margin-left:0; margin-right:0; text-align:left"><span style="color:#003884">https://github.com/ApsaraDB/PolarDB-for-PostgreSQL</span></p> </li> 
</ul>
                                        </div>
                                      
</div>
            
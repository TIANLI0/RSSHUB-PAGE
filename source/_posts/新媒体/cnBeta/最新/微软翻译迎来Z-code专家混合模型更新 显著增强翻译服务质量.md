
---
title: '微软翻译迎来Z-code专家混合模型更新 显著增强翻译服务质量'
categories: 
 - 新媒体
 - cnBeta
 - 最新
headimg: 'https://static.cnbetacdn.com/article/2022/0323/71e591496dbdf4d.jpg'
author: cnBeta
comments: false
date: Wed, 23 Mar 2022 02:30:00 GMT
thumbnail: 'https://static.cnbetacdn.com/article/2022/0323/71e591496dbdf4d.jpg'
---

<div>   
<strong>微软刚刚宣布了自家翻译服务的一项更新，为用户引入了新的机器学习技术，有望显著改善多语种之间的翻译质量。</strong>具体说来是，基于“备用专家混合”（spare Mixture of Experts）方案的 Project Z-Code 项目，可让新模型在盲测评估中的得分较以往提升 3~15% 。<br>
 <p><img src="https://static.cnbetacdn.com/article/2022/0323/71e591496dbdf4d.jpg" alt="0.jpg" referrerpolicy="no-referrer"></p><p style="text-align: center;">（来自：Microsoft <a href="https://www.microsoft.com/en-us/research/blog/microsoft-translator-enhanced-with-z-code-mixture-of-experts-models/" target="_self">Research Blog</a>）</p><p>据悉，Z-code 是微软更广泛的 XYZ-Code 计划的一部分，着眼于结合多种语言的文本、视觉和音频模型，以创建更强大、实用的 AI 系统。</p><p>虽然“专家组合”并不是一套新颖的技术，但它在翻译环境中还是相当实用。该系统的核心，本质上是将任务分解为多个子任务，然后将之委托给更小、更专业的所谓“专家”模型。</p><p><img src="https://static.cnbetacdn.com/article/2022/0323/c645534bd1db8c0.gif" alt="1.gif" referrerpolicy="no-referrer"></p><p style="text-align: center;">Z-code MoE 模型示例：从英语翻译成法语时，可为每个输入动态选择其参数的子集。</p><p>各个模型会根据自身特性来预测、并决定将哪个任务委派给哪个专家，从而极大地简化了开发思路。对于普通用户来说，你可将之视作包含多个更专业模型的大模型集合。</p><blockquote><p>微软技术研究员兼 Azure AI 首席技术官黄学东表示：借助 Z-code，我们确实取得了惊人的进步。</p><p>我们正在利用迁移学习和多任务学习，以从单语言和多语种数据中创建一个极具质量和性能的最佳组合。</p><p>最终带来一个最先进的语言模型，并为客户带来高效的体验。</p></blockquote><p><a href="https://static.cnbetacdn.com/article/2022/0323/21cceac1f9fce10.jpg" target="_blank"><img src="https://static.cnbetacdn.com/thumb/article/2022/0323/21cceac1f9fce10.jpg" alt="2.jpg" referrerpolicy="no-referrer"></a></p><p>结果是，我们看到了一套全新的系统，现能够直接在 10 种语言之间进行翻译，从而消除了对多个系统的需求。</p><p>此外微软最近还开始使用 Z-code 模型来改进其 AI 系统的其它功能，包括实体识别、文本摘要、自定义文本分类、以及关键词提取，但将其用到自家翻译服务上还是首次。</p><p>传统意义上的翻译模型相当笨拙，因而很难将其带入生产环境。不过微软团队选择了一套“稀疏”方案 —— 仅激活每个任务的少量模型参数、而不是动辄调用整个系统。</p><p>这使得模型的运行更具成本效益，就像仅在冬日里为最常用的时段和空间提供室内加热一样经济高效，而无需让暖炉一直保持全速运转。</p>   
</div>
            
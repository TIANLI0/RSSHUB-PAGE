
---
title: 'CrateDB 4.7.1 发布，分布式 SQL 数据库'
categories: 
 - 编程
 - 开源中国
 - 资讯
headimg: 'https://picsum.photos/400/300?random=1247'
author: 开源中国
comments: false
date: Thu, 17 Mar 2022 07:06:00 GMT
thumbnail: 'https://picsum.photos/400/300?random=1247'
---

<div>   
<div class="content">
                                                                    
                                                        <p>CrateDB 是一个分布式的 SQL 数据库，使得实时存储和分析大量的机器数据变得简单。CrateDB 提供了通常与 NoSQL 数据库相关的可扩展性和灵活性，最小的 CrateDB 集群可以轻松地每秒摄取数万条记录。这些数据可以在整个集群中实时地、临时地、并行地进行查询。</p> 
<p style="color:#333333; margin-left:0; margin-right:0; text-align:left">CrateDB 4.7.1 正式发布，该版本更新内容如下：</p> 
<h3>修复</h3> 
<ul> 
 <li><span><span>修复了来自<code><span><span><span>COPY</span></span></span> <span><span><span>FROM</span></span></span></code>的一个问题，该问题导致表的默认表达式仅计算一次，从而导致整个表使用一个单一的值而不是每一行。这仅影响 non-deterministic 函数，例如，<code><span><span><span>gen_random_text_uuid()</span></span></span></code>、<code><span><span><span>random()</span></span></span></code>等。</span></span></li> 
 <li><span><span>修复了从 CrateDB 版本 < 4.0 读取 translog 文件时可能导致错误的问题。</span></span></li> 
 <li><span><span>修复了在使用引用多个其他关系的连接条件时可能导致<code><span><span><span>Couldn't</span></span></span> <span><span><span>create</span></span></span> <span><span><span>execution</span></span></span> <span><span><span>plan</span></span></span></code>的错误问题。</span></span></li> 
 <li><span><span>修复了当在文件系统中不存在父目录的 globbed URI 下执行<code><span><span><span>COPY</span></span></span> <span><span><span>FROM</span></span></span></code>时导致 NPE 的问题。</span></span></li> 
 <li><span><span>修复了在<code><span><span><span>CREATE</span></span></span> <span><span><span>VIEW</span></span></span></code>语句的查询部分使用标量子查询时，会导致在<code><span><span><span>CREATE</span></span></span> <span><span><span>VIEW</span></span></span></code>中使用<code><span><span><span>Invalid</span></span></span> <span><span><span>query</span></span></span></code>错误。</span></span></li> 
 <li><span><span>修复了在上层查询中未使用分区上的 window function 时导致失败的问题。例如： <code><span><span><span>select</span></span></span> <span><span><span>x</span></span></span> <span><span><span>from</span></span></span> <span><span><span>(select</span></span></span> <span><span><span>x,</span></span></span> <span><span><span>ROW_NUMBER()</span></span></span> <span><span><span>OVER</span></span></span> <span><span><span>(PARTITION</span></span></span> <span><span><span>BY</span></span></span> <span><span><span>y)</span></span></span> <span><span><span>from</span></span></span> <span><span><span>t)</span></span></span> <span><span><span>t1</span></span></span></code></span></span></li> 
 <li><span><span>修复了导致错误结果集的显式转换参数的比较函数参数的不正确优化。例如： <code><span><span><span>`WHERE</span></span></span> <span><span><span>strCol::bigint</span></span></span> <span><span><span>></span></span></span> <span><span><span>3`</span></span></span></code></span></span></li> 
 <li><span><span>将捆绑的 JDK 更新为 17.0.2+8</span></span></li> 
</ul> 
<p><span style="background-color:#ffffff; color:#333333">更多详情可查看：</span> <a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2Fcrate%2Fcrate%2Freleases%2Ftag%2F4.7.1" target="_blank">https://github.com/crate/crate/releases/tag/4.7.1</a></p>
                                        </div>
                                      
</div>
            
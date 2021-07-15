
---
title: 'js校验日期是否正确'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=5258'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 02:22:58 GMT
thumbnail: 'https://picsum.photos/400/300?random=5258'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><p><strong>思路：</strong></p>
<p>1.先用正则校验日期格式是否正确。</p>
<p>2.校验闰/平年时，二月天数是否正确。</p>
<p>3.校验某些月份的天数是否超过了30。</p>
<p><strong>代码如下：</strong></p>
<pre><code class="copyable">/**
 * @description 日期校验函数
 * @param &#123;string&#125; date 日期字符串
 * @returns 正确的日期返回true，反之false
 */
function verifyDate(date)&#123;
  if (typeof date !== 'string') &#123;
    return false;
  &#125;

  // 先校验日期字符串的格式
  const regExp = /^\d&#123;4&#125;[-./]((0?[0-9])|(1[012]))[-./](([1-9])|([012][0-9])|(3[01]))$/;

  if (!regExp.test(date)) &#123;
    return false;
  &#125;

  const dates = date.match(/\d+/g);

  // dates[0] | 0 隐式转换数据类型，例如：099 | 0 => 99
  const year = dates[0] | 0;
  const month = dates[1] | 0;
  const day = dates[2] | 0;

  // 平年天数不能大于28，闰年不能大于29
  if (month === 2) &#123;
    if (day > 29) &#123;
      return false;
    &#125; else if (day === 29) &#123;
      if (!(year % 4 === 0 && year % 100 !== 0) && !(year % 400 === 0)) &#123;
        return false;
      &#125;
    &#125;
  &#125;

  // 这些月份天数不能大于30
  if (day > 30 && [4, 6, 9, 11].indexOf(month) !== -1) &#123;
    return false;
  &#125;

  return true;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><a href="https://link.juejin.cn/?target=http%3A%2F%2Fwww.wansongtao.com%2Fblog%2Fdetails%3FarticleId%3D10084%26articleTitle%3Djs%2525E6%2525A0%2525A1%2525E9%2525AA%25258C%2525E6%252597%2525A5%2525E6%25259C%25259F%2525E6%252598%2525AF%2525E5%252590%2525A6%2525E6%2525AD%2525A3%2525E7%2525A1%2525AE" target="_blank" rel="nofollow noopener noreferrer" title="http://www.wansongtao.com/blog/details?articleId=10084&articleTitle=js%25E6%25A0%25A1%25E9%25AA%258C%25E6%2597%25A5%25E6%259C%259F%25E6%2598%25AF%25E5%2590%25A6%25E6%25AD%25A3%25E7%25A1%25AE" ref="nofollow noopener noreferrer">原文链接，点这里。</a></p></div>  
</div>
            
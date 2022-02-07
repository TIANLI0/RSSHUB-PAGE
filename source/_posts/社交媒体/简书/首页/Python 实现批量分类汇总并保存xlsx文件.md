
---
title: 'Python 实现批量分类汇总并保存xlsx文件'
categories: 
 - 社交媒体
 - 简书
 - 首页
headimg: 'https://www.jianshu.com/p/undefined'
author: 简书
comments: false
date: Invalid Date
thumbnail: 'https://www.jianshu.com/p/undefined'
---

<div>   
<div class="image-package  ">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="746" data-height="425"><img data-original-src="//upload-images.jianshu.io/upload_images/10358591-ceeaa499a620b19f" data-original-width="746" data-original-height="425" data-original-format="image/png" data-original-filesize="65944" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
              
              
            <div class="image-caption"></div>
</div><p></p><p>上一篇文件用VBA介绍了如何实现一键按列分类汇总并保存单独文件，<strong>代码有几十行，而且一旦数据量多了，效果可能不尽如人意。</strong><br></p><p>文章可以参见这里：</p><p>vba实例（27）-一键按列分类汇总并保存单独文件</p><p>今天就来给大家说说如何用python来实现这个效果，先给大家看看效果：</p><div class="image-package  ">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="639" data-height="351"><img data-original-src="//upload-images.jianshu.io/upload_images/10358591-a6cde4cf27b67c44" data-original-width="639" data-original-height="351" data-original-format="image/gif" data-original-filesize="253680" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
              
              
            <div class="image-caption"></div>
</div><p>代码只有十几行，效果要提升好多倍，这也是使用python的优势所在。<br></p><h3>思路与代码详解</h3><p>核心思路基本和VBA的一致：读取excel数据 - 获取“归属事业部”列中事业部种类数 - 按每个事业部进行整行提取 - 保存xlsx文件。</p><p>1、这里使用的是python中的pandas数据处理库，这个是在数据处理界非常牛逼的一个工具库，使用之前需要导入库。</p><pre><code>import pandas as pd <br></code></pre><p>2、读取excel的数据。读取"拆分实例.xlsx"这个excel中,sheet名字为"全国客户明细"的数据，将读取的内容赋值给df。</p><pre><code>df = pd.read_excel("拆分实例.xlsx",sheet_name="全国客户明细")<br></code></pre><p>3、获取“归属事业部”列的种类数，使用pandas库的unique方法，将所有事业部的名字赋值给变量group_names。</p><pre><code>group_names=df["归属事业部"].unique()<br></code></pre><p>4、将某个事业部的数据整行提取出来保存成xlsx文件，并按事业部的名字进行命名。</p><pre><code>df_group=df.groupby(by=['归属事业部']).get_group(group_name).reset_index(drop=True)<br>df_group.to_excel(".\拆分结果\\"+group_name+".xlsx")<br></code></pre><p>5、遍历每一个事业部，进行同样的操作。</p><pre><code>for group_name in group_names:<br></code></pre><p>完整代码如下：</p><pre><code>import pandas as pd<br>import time<br><br>start = time.time()<br><br>df = pd.read_excel("拆分实例.xlsx",sheet_name="全国客户明细")<br>group_names=df["归属事业部"].unique()<br>for group_name in group_names:<br>    df_group=df.groupby(by=['归属事业部']).get_group(group_name).reset_index(drop=True)<br>    df_group.to_excel(".\拆分结果\\"+group_name+".xlsx")<br><br>elapsed = (time.time() - start)<br><br>print("完成，共花费时间为：",elapsed)<br></code></pre><h3>优化</h3><p>上面这个代码生成的excel，数据是没有任何问题，但是单元格格式比较简陋，甚至可以说“丑”。</p><div class="image-package  ">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="633" data-height="311"><img data-original-src="//upload-images.jianshu.io/upload_images/10358591-9344eb0d6e8f0256" data-original-width="633" data-original-height="311" data-original-format="image/png" data-original-filesize="18950" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
              
              
            <div class="image-caption"></div>
</div><p>如果需要如下图像生成VBA的比较美观的样式，要怎么弄呢？需要做一些格式上的处理。</p><div class="image-package  ">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="620" data-height="161"><img data-original-src="//upload-images.jianshu.io/upload_images/10358591-1d2626302f9e047e" data-original-width="620" data-original-height="161" data-original-format="image/png" data-original-filesize="34486" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
              
              
            <div class="image-caption"></div>
</div><p>可以新建一个“模板”文件，</p><div class="image-package  ">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="776" data-height="244"><img data-original-src="//upload-images.jianshu.io/upload_images/10358591-a2859dcb0637362a" data-original-width="776" data-original-height="244" data-original-format="image/png" data-original-filesize="15548" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
              
              
            <div class="image-caption"></div>
</div><p>然后调用openpyxl库将分类的数据dataframe写入到模板文件中，设置边框等格式，另存为xlsx文件即可。</p><div class="image-package  ">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1080" data-height="387"><img data-original-src="//upload-images.jianshu.io/upload_images/10358591-9abf530464a12856" data-original-width="1080" data-original-height="387" data-original-format="image/png" data-original-filesize="168191" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
              
              
            <div class="image-caption"></div>
</div><p>效果如下：<br></p><div class="image-package  ">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="639" data-height="351"><img data-original-src="//upload-images.jianshu.io/upload_images/10358591-24ca14d03b5f2848" data-original-width="639" data-original-height="351" data-original-format="image/gif" data-original-filesize="264478" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
              
              
            <div class="image-caption"></div>
</div><p></p><p><br></p><p><br></p><p>如果你对上面的内容感兴趣，可以在公号内回复「<strong>python处理</strong>」自取试用，尽快吧！</p><p><br></p><p>欢迎交流！</p>  
</div>
            
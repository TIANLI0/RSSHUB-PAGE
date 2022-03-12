
---
title: 'Android 线程池全解析'
categories: 
 - 社交媒体
 - 简书
 - 首页
headimg: 'https://upload-images.jianshu.io/upload_images/6038844-aa27250fac2a8080.png'
author: 简书
comments: false
date: Invalid Date
thumbnail: 'https://upload-images.jianshu.io/upload_images/6038844-aa27250fac2a8080.png'
---

<div>   
<h4>什么是线程池</h4>
<ul>
<li><p>我们都知道线程是什么，但是一提到线程池，给人的第一个感觉就是一堆线程，这样的理解其实不太对，线程池可以只有一个线程，也可以有多个线程，而线程池最大的作用是管理和复用线程。一提到管理线程，我们都知道线程池可以帮我们创建线程，也可以帮我们销毁线程。但是一提到复用线程，相信大多数人都愣了，要知道 Thread.start 执行完 Runnable.run 方法之后线程就自动停止了，也就是说 Thread 对象只能调用一次 start 方法，那么在这种情况下线程池是如何复用线程的呢？</p></li>
<li><p>都说源码是最好的老师，接下来让我们通过源码来看看这葫芦里面卖的什么药</p></li>
</ul>
<h4>线程池的原理</h4>
<ul>
<li>我们还是从线程池的写法入手源码</li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1086" data-height="302"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-aa27250fac2a8080.png" data-original-width="1086" data-original-height="302" data-original-format="image/png" data-original-filesize="101451" src="https://upload-images.jianshu.io/upload_images/6038844-aa27250fac2a8080.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1554" data-height="1394"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-fa917126c69de1d0.png" data-original-width="1554" data-original-height="1394" data-original-format="image/png" data-original-filesize="1448420" src="https://upload-images.jianshu.io/upload_images/6038844-fa917126c69de1d0.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1374" data-height="1628"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-466340c1b82366a4.png" data-original-width="1374" data-original-height="1628" data-original-format="image/png" data-original-filesize="999468" src="https://upload-images.jianshu.io/upload_images/6038844-466340c1b82366a4.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<ul>
<li>在线程池的执行方法中，我们发现了一个出现频率很高的 API，接下来让我们看看这句代码干了什么事</li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1482" data-height="1602"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-fe23773c98fdc37c.png" data-original-width="1482" data-original-height="1602" data-original-format="image/png" data-original-filesize="1015890" src="https://upload-images.jianshu.io/upload_images/6038844-fe23773c98fdc37c.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<ul>
<li>我们可以看到，线程池拿到任务之后丢给了 Worker 类处理</li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1454" data-height="1388"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-7b7145819d145355.png" data-original-width="1454" data-original-height="1388" data-original-format="image/png" data-original-filesize="1106221" src="https://upload-images.jianshu.io/upload_images/6038844-7b7145819d145355.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<ul>
<li>进 Worker 类一看，不看不知道，一看吓一跳，这个类还创建了 Thread 对象</li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1444" data-height="1396"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-e22b65dd622eb5a0.png" data-original-width="1444" data-original-height="1396" data-original-format="image/png" data-original-filesize="1135694" src="https://upload-images.jianshu.io/upload_images/6038844-e22b65dd622eb5a0.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<ul>
<li>有一个非常重要细节，就是创建线程的时候，传入的并不是我们给线程池的那个 Runnable 对象，而是 Worker 对象本身，也就是说线程 start 的时候，Worker 类的 run 方法会被执行</li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1342" data-height="1634"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-cd09b3a81a781d91.png" data-original-width="1342" data-original-height="1634" data-original-format="image/png" data-original-filesize="1044884" src="https://upload-images.jianshu.io/upload_images/6038844-cd09b3a81a781d91.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<ul>
<li><p>在这里可以看到我们刚刚传入 Runnable 对象，然后开启了一个 while 循环，循环的意思是：只要 task 对象不为空，那么就会一直调用 task = getTask()，直到获取到的 task 对象为空了才会停止循环</p></li>
<li><p>那么 getTask 方法里面到底干了什么，让我们接着看</p></li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1430" data-height="1624"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-4b1fdaff70d4be94.png" data-original-width="1430" data-original-height="1624" data-original-format="image/png" data-original-filesize="1001338" src="https://upload-images.jianshu.io/upload_images/6038844-4b1fdaff70d4be94.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1316" data-height="604"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-fd46b783cf7388e6.png" data-original-width="1316" data-original-height="604" data-original-format="image/png" data-original-filesize="585643" src="https://upload-images.jianshu.io/upload_images/6038844-fd46b783cf7388e6.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<ul>
<li>通过这两段代码，我们可以得知，getTask 其实就是往阻塞队列中取出 Runnable 对象</li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1324" data-height="1630"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-f084a8bd8e7197a8.png" data-original-width="1324" data-original-height="1630" data-original-format="image/png" data-original-filesize="1031218" src="https://upload-images.jianshu.io/upload_images/6038844-f084a8bd8e7197a8.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<ul>
<li>通过这些，我们可以得出，线程池复用线程的原理，创建 Thread 对象的时候传入的不是我们的 Runnable 对象，而是通过线程池自定义的 Runnable 类，这个类主要的作用不仅是执行我们的 Runnable 对象，当我们传入的任务被某个线程执行完毕之后，它还会遍历阻塞队列中其他未执行的任务，这样就能达到一个线程执行多个 Runnable 对象的效果，这个就是线程池复用线程的原理。</li>
</ul>
<h4>什么时候该用线程池</h4>
<ul>
<li><p>通过源码我们了解到了线程池的工作机制，那么问题来了，什么情况下该用线程池，什么情况下不该用线程池？</p></li>
<li><p>这个问题其实很简单，源码已经告诉我们答案了，当线程池中只有一个线程并且只执行一次任务的时候，我们可以考虑不用线程池，直接创建 Thread 对象来执行这个任务。</p></li>
<li><p>也就是说线程池的生命周期只有单个任务的情况下，没有任何优势可言，但是如果在多任务同时并发的情况下，线程池是可以帮我们减少线程数量的，用一句最简单的话来理解就是，用最少的人力干完所有的活，人太少活太多不行，人太多活太少也不行。</p></li>
</ul>
<h4>线程池核心参数</h4>
<ul>
<li>接下来让我们讲讲创建线程池的几个核心参数</li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1462" data-height="1440"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-71b059a21be95a84.png" data-original-width="1462" data-original-height="1440" data-original-format="image/png" data-original-filesize="1732736" src="https://upload-images.jianshu.io/upload_images/6038844-71b059a21be95a84.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1416" data-height="952"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-5c3e48a401dd5999.png" data-original-width="1416" data-original-height="952" data-original-format="image/png" data-original-filesize="805333" src="https://upload-images.jianshu.io/upload_images/6038844-5c3e48a401dd5999.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1470" data-height="358"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-f10268e577f1ac11.png" data-original-width="1470" data-original-height="358" data-original-format="image/png" data-original-filesize="315231" src="https://upload-images.jianshu.io/upload_images/6038844-f10268e577f1ac11.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<ul>
<li>corePoolSize 是核心线程数，何为核心线程数？源码注释已经写得很明白了，也就是最小线程数，规定线程池里面最少必须有几个线程在工作，这些核心线程在没有任务可以执行的时候还必须存活着，除非我们设定了核心线程的存活时间，否则这些核心线程永远不会停止工作。</li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1656" data-height="302"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-f598efb373f286e3.png" data-original-width="1656" data-original-height="302" data-original-format="image/png" data-original-filesize="243867" src="https://upload-images.jianshu.io/upload_images/6038844-f598efb373f286e3.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<ul>
<li><p>maximumPoolSize 是最大线程数，这里面不仅包含了核心线程数，还包含了非核心线程数，那么问题来了，何为非核心线程？</p></li>
<li><p>这不得不来场比较了，核心线程和非核心线程最大的区别是：核心线程在没有任务的情况下不会被回收，而非核心线程一旦没有了任务就会被回收。</p></li>
<li><p>举一个生活中最常见的例子，我们如果把核心线程比作一个正式工，那么非核心线程就是一个外包工。正式工没活干没事，但如果外包工没活干了的话是要面临被裁员的。</p></li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1336" data-height="610"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-15f92a4e2ab4df2b.png" data-original-width="1336" data-original-height="610" data-original-format="image/png" data-original-filesize="430976" src="https://upload-images.jianshu.io/upload_images/6038844-15f92a4e2ab4df2b.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<ul>
<li><p>workQueue 是阻塞队列，为什么要用队列（Queue），因为队列是先进先出，先进来的任务先取出，最终先进来的任务最先执行完毕的可能性就大，但这还得考虑任务具体的耗时情况而定，在耗时相同的情况下，先进来的任务就先执行完毕。当然这个队列还有其他用处，那就是存放一些未执行的任务，具体有什么作用，可以让我们来一场实验。</p></li>
<li>
<p>实验场景：核心线程数 = 1 ，最大线程数 = 3，开启 for 循环执行 10 个任务，任务内容：sleep 1 秒并打印当前线程名</p>
<ul>
<li><p>当阻塞队列容量无限大时，10 个任务只出现 1 个线程在排队执行</p></li>
<li><p>当阻塞队列容量设置为 10 个或者 9 个时，10 个任务也是只出现 1 个线程在排队执行</p></li>
<li><p>当阻塞队列容量设置为 8 个时，10 个任务出现了 2 个线程在并发执行</p></li>
<li><p>当阻塞队列容量设置为 7 个时，10 个任务出现了 3 个线程在并发执行</p></li>
<li><p>当阻塞队列容量设置为 6 个时，线程池抛出异常，表示拒绝执行任务</p></li>
</ul>
</li>
<li><p>实验结论：往线程池添加一个新的任务时，如果核心线程处于空闲状态，任务会直接交由核心线程处理，否则任务会存放到阻塞队列中，当阻塞队列中的任务数量超过设定的最大值时，才会开启非核心线程去执行，如果<strong>当前任务总量 > 阻塞队列的最大容量 + 最大线程数</strong>时，线程池则会拒绝执行该任务。</p></li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1330" data-height="372"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-9921d09b920d3d64.png" data-original-width="1330" data-original-height="372" data-original-format="image/png" data-original-filesize="296749" src="https://upload-images.jianshu.io/upload_images/6038844-9921d09b920d3d64.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="2132" data-height="1040"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-e351d8a60b557742.png" data-original-width="2132" data-original-height="1040" data-original-format="image/png" data-original-filesize="460336" src="https://upload-images.jianshu.io/upload_images/6038844-e351d8a60b557742.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<ul>
<li><p>keepAliveTime 是非核心线程的存活时间，当线程池中的非核心线程没有任务执行的时候，如果超过了指定的时间还是没有执行任何任务的时候，那么这个非核心线程会在超时后被回收掉，如果我们不指定这个时间，那么这些非核心线程将永远不会被回收。</p></li>
<li><p>其他参数不是那么重要，这里直接略过不讲，接下来简单介绍一下系统 API 给我们提供的四种线程池。</p></li>
</ul>
<h4>系统提供的四种线程池</h4>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="602" data-height="48"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-7090de3b66800c57.png" data-original-width="602" data-original-height="48" data-original-format="image/png" data-original-filesize="35056" src="https://upload-images.jianshu.io/upload_images/6038844-7090de3b66800c57.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1388" data-height="342"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-541b82773a919287.png" data-original-width="1388" data-original-height="342" data-original-format="image/png" data-original-filesize="283200" src="https://upload-images.jianshu.io/upload_images/6038844-541b82773a919287.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<ul>
<li>这里创建了一个核心线程数和最大线程数都为 1 的线程池，简单理解这个线程池只有一个线程，正如它的方法名一样（new Single Thread Executor）</li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="694" data-height="48"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-49038c3e7be66bde.png" data-original-width="694" data-original-height="48" data-original-format="image/png" data-original-filesize="38143" src="https://upload-images.jianshu.io/upload_images/6038844-49038c3e7be66bde.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1420" data-height="924"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-338a39457d9b67a8.png" data-original-width="1420" data-original-height="924" data-original-format="image/png" data-original-filesize="1017946" src="https://upload-images.jianshu.io/upload_images/6038844-338a39457d9b67a8.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<ul>
<li>这个线程池跟上一个线程池非常像，核心线程数和最大线程数都是用同一个数值，只不过上一个线程池是写死的 1，而这个线程池可以自定义这个数值。</li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="532" data-height="46"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-6e69f53af53a525b.png" data-original-width="532" data-original-height="46" data-original-format="image/png" data-original-filesize="31094" src="https://upload-images.jianshu.io/upload_images/6038844-6e69f53af53a525b.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1374" data-height="974"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-7e297b0598ac56fb.png" data-original-width="1374" data-original-height="974" data-original-format="image/png" data-original-filesize="1019776" src="https://upload-images.jianshu.io/upload_images/6038844-7e297b0598ac56fb.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<ul>
<li>这个线程池没有核心线程数，也没有限制最大线程数，那么可以得出这个线程池里面的线程都是非核心线程，并且还规定了非核心线程的存活时间不能超过 60 秒。</li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="790" data-height="48"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-41d3696c4ec57787.png" data-original-width="790" data-original-height="48" data-original-format="image/png" data-original-filesize="36486" src="https://upload-images.jianshu.io/upload_images/6038844-41d3696c4ec57787.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1700" data-height="582"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-5a9be591abf56911.png" data-original-width="1700" data-original-height="582" data-original-format="image/png" data-original-filesize="417677" src="https://upload-images.jianshu.io/upload_images/6038844-5a9be591abf56911.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1448" data-height="646"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-3d148cf20003b197.png" data-original-width="1448" data-original-height="646" data-original-format="image/png" data-original-filesize="562610" src="https://upload-images.jianshu.io/upload_images/6038844-3d148cf20003b197.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1358" data-height="746"><img data-original-src="//upload-images.jianshu.io/upload_images/6038844-2738926933f0959c.png" data-original-width="1358" data-original-height="746" data-original-format="image/png" data-original-filesize="820617" src="https://upload-images.jianshu.io/upload_images/6038844-2738926933f0959c.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<ul>
<li><p>最后一个线程池的特点是：核心线程数是固定的，但不限制最大线程数，非核心线程的闲置时间不能超过 10 毫秒。</p></li>
<li><p>了解过后才发现，这四种线程池无非是核心线程数、最大线程数、非核心线程的存活时间这几个参数的定义上徘徊</p></li>
</ul>
<h4>Android 技术讨论 Q 群：10047167</h4>
  
</div>
            
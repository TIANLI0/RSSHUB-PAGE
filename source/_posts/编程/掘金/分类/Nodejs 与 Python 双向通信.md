
---
title: 'Nodejs 与 Python 双向通信'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=7413'
author: 掘金
comments: false
date: Thu, 08 Jul 2021 07:32:30 GMT
thumbnail: 'https://picsum.photos/400/300?random=7413'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><p>第三方<code>数据供应商</code>把数据和Python<code>封装</code>到一起，只能通过<code>调用 Python方法</code>来实现数据查询，如果可以通过Node 简单封装下实现 Python 方法调用可以<code>快速</code>上线并<code>节省开发成本</code>。</p>
<p>最<code>简单粗暴</code>的通信方式是 Nodejs调用一下 Python 脚本，然后获取子进程的输出，但是由于每次 Python <code>启动并加载</code>数据包的过程比较<code>漫长</code>，所以对该过程<code>优化</code>。</p>
<h2 data-id="heading-0">进程通信</h2>
<p>index.py</p>
<pre><code class="copyable"># 封装的 Python 包， 体积巨大
from mb import MB
# 从数据包中查询
mbe.get('1.0.1.0')
<span class="copy-code-btn">复制代码</span></code></pre>
<p>index.js</p>
<pre><code class="copyable">const &#123; spawn &#125; = require('child_process');
const ls = spawn('python3', ['index.py']);

ls.stdout.on('data', (data) => &#123;
  console.log(`stdout: $&#123;data&#125;`);
&#125;);

ls.stderr.on('data', (data) => &#123;
  console.error(`stderr: $&#123;data&#125;`);
&#125;);

ls.on('close', (code) => &#123;
  console.log(`child process exited with code $&#123;code&#125;`);
&#125;);
<span class="copy-code-btn">复制代码</span></code></pre>
<p>通过<code>child_process.spawn</code>来派生 Python 子进程，监听 <code>stdout</code> 输出。上述方式也是官方文档中的示例，目前该示例存在两个问题:</p>
<ol>
<li>Nodejs 没有向 Python 发送数据</li>
<li>Nodejs 调用完毕后，Python 子进程会<code>退出</code>；下次查询需要<code>再次</code>调用Python命令进行加载文件，查询数据；无法实现<code>一次内存加载，多次使用</code>。</li>
</ol>
<h2 data-id="heading-1">进程双向通信</h2>
<p>保证一次数据加载，多次使用的前提是 Python 进程启动后<code>不能退出</code>。Python 进程之所以退出是因为<code>无事可做</code>，所以常见的手段有<code>循环</code>，<code>sleep</code>，<code>监听端口</code>，这些手段可以翻译成<code>同步阻塞任务</code>，<code>同步非阻塞任务</code>，其中<code>代价最小</code>的就是同步非阻塞任务，然后可以想到 Linux 的 <code>select</code>，<code>epoll</code>，简单搜索了下 Python 的 epoll，好像还有原生的包。</p>
<p>index.py - 通过 epoll 监听 stdin</p>
<pre><code class="copyable">import sys
import fcntl
import select
from mb import MB
import json

mbe = MB('./data')

# epoll 模型
fd = sys.stdin.fileno()
epoll = select.epoll()
epoll.register(fd, select.EPOLLIN)

try:
    while True:
        events = epoll.poll(10) # 同步非阻塞
        data = ''
        for fileno, event in events:
            data += sys.stdin.readline() # 通过标准输入获取数据
            if data == '' or data == '\n':
                continue
            items = xxx # 数处理过程
            for item in items:
                result = mbe.get(item)
                sys.stdout.write(json.dumps(result, ensure_ascii=False) +'\n') # 写入到标准输出
                sys.stdout.flush() # 缓冲区刷新
finally:
    epoll.unregister(fd)
    epoll.close()
<span class="copy-code-btn">复制代码</span></code></pre>
<p>index.js - 通过 stdin 发送数据</p>
<pre><code class="copyable">const child_process = require('child_process');
const child = child_process.spawn('python3', ['./base.py']);

let callbacks =  [], 
    chunks=Buffer.alloc(0), 
    chunkArr = [], 
    data = '', 
    onwork = false; // buffer 无法动态扩容
    
child.stdout.on('data', (chunk) => &#123;
    chunkArr.push(chunk)
    if (onwork) return;
    onwork = true;
    while(chunkArr.length) &#123;
        chunks = Buffer.concat([chunks, chunkArr.pop()]);
        const length = chunks.length;
        let trunkAt = -1;
        for(const [k, d] of chunks.entries()) &#123;
            if (d == '0x0a') &#123; // 0a 结尾
                data += chunks.slice(trunkAt+1, trunkAt=k);
                const cb = callbacks.shift();
                cb(null, data === 'null' ? null : data )
                data = '';
            &#125;
        &#125;
        if (trunkAt < length) &#123;
            chunks = chunks.slice(trunkAt+1)
        &#125;
    &#125;
    onwork = false;
&#125;)

setInterval(() => &#123;
    if (callbacks.length) child.stdin.write(`\n`); // Nodejs端的标准输入输出没有flush方法，只能 hack， 写入后python无法及时获取到最新
&#125;, 500)

exports.getMsg = function getMsg(ip, cb) &#123;
    callbacks.push(cb)
    child.stdin.write(`$&#123;ip&#125;\n`); // 把数据写入到子进程的标准输入
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p><code>Python 与 Nodejs 通过 stdio 实现通信； Python 通过 epoll 监听 stdin 实现驻留内存，长时间运行</code>。</p>
<h2 data-id="heading-2">存在问题</h2>
<ol>
<li>Nodejs 把标准输出作为执行结果，故 Python 端只能把执行结果写入标准输出，不能有<code>额外的打印</code>信息</li>
<li>Nodejs 端标准输入<code>没有 flush 方法</code>，所以 Python 端事件触发不够及时，目前通过在Nodejs端定时发送空信息来 <code>hack</code> 实现</li>
<li>Buffer 没法<code>动态扩容</code>，没有C语言的指针好用，在解析 stdout 时写<code>丑</code></li>
</ol>
<h2 data-id="heading-3">总结</h2>
<p>虽然可以实现 Nodejs 和 Python 的双向通信，然后由于上述种种问题，在这里并<code>不推荐</code>使用这种方式，通过 HTTP 或 Socket 方式比这个<code>香</code>多了。</p>
<p>关注我的微信公众号"SUNTOPO WLOG"，欢迎留言讨论，我会尽可能回复，感谢您的阅读。</p></div>  
</div>
            
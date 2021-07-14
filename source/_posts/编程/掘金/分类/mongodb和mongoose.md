
---
title: 'mongodb和mongoose'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f3819bee4beb4359ae0b81f57d5327a3~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Tue, 13 Jul 2021 05:08:01 GMT
thumbnail: 'https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f3819bee4beb4359ae0b81f57d5327a3~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h2 data-id="heading-0">前言</h2>
<p>如果一个网站需要存储大量的信息，那么就需要用到数据库。数据库的CRUD（增删改查）操作是后端服务器的一项重要的操作。在这篇文章中，我们就来聊一聊数据库。数据库就是一个存放数据的仓库，这个仓库按照一定的数据结构来组织存储数据。按照早期的数据库理论，比较流行的数据库模型有三种，分别是层次式数据库、网络式数据库和关系型数据库(前两者已经基本消失)。当今的互联网中，最常见的数据库模型有两种关系型数据库(RDBMS,Relational Database Management System)和非关系型数据库(noSQL)。关系型数据库，比较著名的有Oracle、MySQL；非关系型数据库，即NoSQL，其含义不是"no sql"，而是"not only SQL",不仅仅是SQL。SQL的全称是"Structured Query Language(结构化查询语言)"，是专门为数据库而建立的造作命令集，是一种功能齐全的数据库语言。类似JavaScript的声明式编程，在使用时只需要考虑"做什么",而不需要考虑"怎么做"。常见的非关系型数据库有Redis，还有我们今天的主角MongoDB。</p>
<h2 data-id="heading-1">mongoDB</h2>
<h3 data-id="heading-2">mongoDB基本概念</h3>
<p>MongoDB是面向文档的数据库，其中有三个重要的概念：数据库(database)、集合(collection)、文档(document).</p>
<ul>
<li>数据库(database)：和SQL中的数据库相对应，表示数据库，可以理解为所有的数据都存在这个空间中</li>
<li>集合(collection)：和SQL中的tabel相对应，表示数据表/集合，可以理解为存储的某一类数据</li>
<li>文档(document)：和SQL中的row相对应，表示数据记录行/文档，可以理解为存储的某一条数据</li>
</ul>
<p>显然，这三个概念之间存在一种包含关系，数据库中包含很多个集合，集合中包含很多文档。从数学集合的观点来看，<strong>数据库是集合的集合，集合是文档的集合</strong>。下图是三者关系的直观表示。<br>
<img src="https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f3819bee4beb4359ae0b81f57d5327a3~tplv-k3u1fbpfcp-watermark.image" alt="mongoDB三个概念关系.png" loading="lazy" referrerpolicy="no-referrer"><br>
除此之外，MongoDB中还有三个关键概念：字段(field)、索引(index)、主键(primaryy key).</p>
<ul>
<li>字段(field)：如果说document代表的是SQL语言中的row的话，那么字段这个概念代表的就是SQL中的column。也可以理解为键值对(key-value)中的“键”.</li>
<li>索引(index)：这个概念看名称就知道了，无需多言</li>
<li>主键(primary key)：MongoDB数据库中的数据的唯一标识，默认主键为<code>_id</code>字段</li>
</ul>
<p>到此，mongoDB中的基本概念就介绍完了。接下来，我们看一条真实存储在mongoDB数据库中的数据：</p>
<ul>
<li>在数据库中的样子：</li>
</ul>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c0e750b183ee4e039ccf48733d9cf7d3~tplv-k3u1fbpfcp-watermark.image" alt="mongoDB数据.png" loading="lazy" referrerpolicy="no-referrer">
可以看到，该条数据，或者可以说这个文档，有七个字段，主键是<code>_id</code>。当数据通过被查询到之后就会以如下的json的格式返回</p>
<pre><code class="hljs language-javascript copyable" lang="javascript">&#123;
  <span class="hljs-string">"_id"</span> : ObjectId(<span class="hljs-string">"60d571d606d8634c18cf2338"</span>),
  <span class="hljs-string">"agreeArticle"</span> : [],
  <span class="hljs-string">"username"</span> : <span class="hljs-string">"ggg"</span>,
  <span class="hljs-string">"password"</span> : <span class="hljs-string">"202cb962ac59075b964b07152d234b70"</span>,
  <span class="hljs-string">"type"</span> : <span class="hljs-string">"normal"</span>,
  <span class="hljs-string">"agreeCount"</span> : <span class="hljs-number">0</span>,
  <span class="hljs-string">"__v"</span> : <span class="hljs-number">0</span>
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-3">使用</h3>
<p>在javascript中关于mongoDB的使用，主要是通过中间库mongoose来实现的。因此，很多操作都只需要调用mongoose即可，这些操作将在下一部分进行介绍。在这里，主要介绍mongoDB中文档的CRUD(增删改查)操作。在执行文档的CRUD操作之前，应该现有现有数据库和集合这两个要素。而在所有的操作之前，应该先安装和启动mongoDB，并且建立数据库的连接</p>
<h4 data-id="heading-4">安装和启动mongoDB</h4>
<ul>
<li>安装和启动mongoDB，请戳下面的链接：<a href="https://link.juejin.cn/?target=https%3A%2F%2Fwww.runoob.com%2Fmongodb%2Fmongodb-window-install.html" target="_blank" rel="nofollow noopener noreferrer" title="https://www.runoob.com/mongodb/mongodb-window-install.html" ref="nofollow noopener noreferrer">www.runoob.com/mongodb/mon…</a></li>
<li>mongoDB启动数据库服务，请戳下面的链接：<a href="https://link.juejin.cn/?target=https%3A%2F%2Fwww.runoob.com%2Fmongodb%2Fmongodb-connections.html" target="_blank" rel="nofollow noopener noreferrer" title="https://www.runoob.com/mongodb/mongodb-connections.html" ref="nofollow noopener noreferrer">www.runoob.com/mongodb/mon…</a></li>
</ul>
<h4 data-id="heading-5">数据库</h4>
<p>关于数据库的操作的关键命令如下：</p>
<ul>
<li>创建数据库：<code>use DATABASE_NAME</code></li>
<li>显示数据库列表：<code>show dbs</code></li>
<li>显示当前数据库：<code>db</code></li>
<li>删除数据库：<code>db.dropDatabase()</code></li>
</ul>
<blockquote>
<p>注意：删除数据库的操作需要谨慎使用！！！</p>
</blockquote>
<h4 data-id="heading-6">集合</h4>
<p>关于集合操作的几条关键命令如下：</p>
<ul>
<li>创建集合：<code>db.createCollection("COLLECTION_NAME")</code></li>
<li>显示当前数据库中的集合：<code>show collections</code></li>
<li>删除集合：<code>db.COLLECTION_NAME.drop()</code></li>
</ul>
<h4 data-id="heading-7">文档</h4>
<ul>
<li>增(create)：<br>
在mongoDB中，我们需要将document插入到collection中。每一个document的数据结构和JSON基本一样。但是这种数据结构在mongoDB中不叫作JSON，而是叫做BSON，是Binary JSON的简称。接下来，我们来关注在collection中插入document的语法。
<ul>
<li><code>db.COLLECTION_NAME.insert(document)</code>：若插入的数据主键已经存在，则会抛出<code>org.springframework.dao.DuplicateKeyException</code>异常，提示主键重复，不保存当前数据</li>
<li><code>db.COLLECTION_NAME.save(document)</code>：如果<code>_id</code>主键存在则更新数据，如果不存在就插入数据。该方法在新版本中已废弃，可以用<code>db.collection.insertOne()</code>或<code>db.collection.replaceOne()</code>来代替。</li>
<li><code>db.COLLECTION_NAME.insertOne(<document>,&#123;writeConcern:<document>&#125;)</code>: 3.2版本之后新增的插入方法。其中，<code><document></code>表示要写入的文档；<code>writeConcern</code>表示写入策略，默认为 1，即要求写入操作，0 是不要求。</li>
<li><code>db.COLLECTION_NAME.insertMany([<document 1>, <document 2>, ... ],&#123;writeConcern: <document>, orderd: <boolean>&#125;)</code>：3.2版本之后新增的插入方法。其中，<code><document></code>和<code>writeConcern</code>的含义与之前相同，<code>ordered</code>表示是否按顺序写入，默认为<code>true</code>，按顺序写入。</li>
</ul>
</li>
</ul>
<blockquote>
<p><code>writeConcern</code>字段的含义，相关文档是这样表述的： Write concern describes the level of acknowledgment requested from MongoDB for write operations to a standalone mongod or to replica sets or to sharded clusters. In sharded clusters, mongos instances will pass the write concern on to the shards.</p>
</blockquote>
<p>write Concern 包含下列字段：</p>
<pre><code class="hljs language-javaScript copyable" lang="javaScript">&#123;
    <span class="hljs-attr">w</span>: <value>,           
    j: <boolean>,
    wtimeout: <number>
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>详情请参考相关文档，相关文档链接如下：<a href="https://link.juejin.cn/?target=https%3A%2F%2Fdocs.mongodb.com%2Fmanual%2Freference%2Fwrite-concern%2F%23write-concern" target="_blank" rel="nofollow noopener noreferrer" title="https://docs.mongodb.com/manual/reference/write-concern/#write-concern" ref="nofollow noopener noreferrer">docs.mongodb.com/manual/refe…</a></p>
<ul>
<li>删(delete)<br>
删除文档的语法如下：
<pre><code class="hljs language-javascript copyable" lang="javascript">db.collection.remove(
    <query>,
    &#123;
        <span class="hljs-attr">justOne</span>: <boolean>,
        writeConcern: <<span class="hljs-built_in">document</span>>
    &#125;
)
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li><code><query></code>：可选参数，表示删除文档的条件</li>
<li><code>justOne</code>：可选参数，如果设为<code>true 或 1 </code>，则只删除一个文档；如果不设置该参数，或者使用默认值<code>false</code>，则删除所有匹配条件的文档。</li>
<li><code>writeConcern</code>：可选参数，表示抛出异常的级别。</li>
</ul>
</li>
<li>改(update)
更新文档的语法如下：
<pre><code class="hljs language-javascript copyable" lang="javascript">db.collection.update(
    <query>,
    <update>,
    &#123;
        <span class="hljs-attr">upsert</span>: <boolean>,
        multi: <boolean>,
        writeConcern: <<span class="hljs-built_in">document</span>>
    &#125;
)
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li><code>query</code>：update的查询条件</li>
<li><code>update</code>：update的对象和一些更新的操作符</li>
<li><code>upsert</code>：可选参数，如果不存在update记录，是否插入objNew，true为插入，false为不插入，默认值。</li>
<li><code>multi</code>：可选参数，默认为false，只更新找到的第一条记录；如果设置为true，则更新符合条件的全部数据</li>
<li><code>writeConcern</code>：可选参数，表示抛出异常的级别</li>
</ul>
</li>
<li>查(retrieve)<br>
mongoDB的查询操作，可以参考下面的文章，此处不再赘述：
<a href="https://juejin.cn/post/6844903974055706638" target="_blank" title="https://juejin.cn/post/6844903974055706638">juejin.cn/post/684490…</a></li>
</ul>
<h2 data-id="heading-8">mongoose</h2>
<p>mongoose是一个使用nodeJS来操作mongoDB数据库的开源库。mongoose里面封装了连接数据库、创建collection和document CRUD的操作。</p>
<h3 data-id="heading-9">安装mongoose</h3>
<p>在自己的项目中运行：<code>npm install mongoose --save</code></p>
<h3 data-id="heading-10">连接数据库</h3>
<p>废话不多说，直接贴代码：</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-keyword">const</span> mongoose = <span class="hljs-built_in">require</span>(<span class="hljs-string">'mongoose'</span>)
mongoose.connect(<span class="hljs-string">'mongodb://localhost:27017/test'</span>,
            &#123;<span class="hljs-attr">useNewUrlParser</span>: <span class="hljs-literal">true</span>, <span class="hljs-attr">useUnifiedTopology</span>: <span class="hljs-literal">true</span>&#125;)
<span class="hljs-keyword">const</span> db = mongoose.connection;
db.on(<span class="hljs-string">'open'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span>(<span class="hljs-params"></span>) </span>&#123;
  <span class="hljs-comment">// 数据库连接成功的回调函数</span>
&#125;);
<span class="copy-code-btn">复制代码</span></code></pre>
<h3 data-id="heading-11">Schema 和 Model</h3>
<p>在mongoose中，Schema是起点，它与mongoDB中的collection相对应，并且定义了collection中每一个document的数据结构。下面是一个Schema的使用实例：</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-keyword">import</span> mongoose <span class="hljs-keyword">from</span> <span class="hljs-string">'mongoose'</span>;
<span class="hljs-keyword">const</span> &#123; Schema &#125; = mongoose;

<span class="hljs-keyword">const</span> blogSchema = <span class="hljs-keyword">new</span> Schema(&#123;
    <span class="hljs-attr">title</span>:  <span class="hljs-built_in">String</span>, <span class="hljs-comment">// String is shorthand for &#123;type: String&#125;</span>
    <span class="hljs-attr">author</span>: <span class="hljs-built_in">String</span>,
    <span class="hljs-attr">body</span>:   <span class="hljs-built_in">String</span>,
    <span class="hljs-attr">comments</span>: [&#123; <span class="hljs-attr">body</span>: <span class="hljs-built_in">String</span>, <span class="hljs-attr">date</span>: <span class="hljs-built_in">Date</span> &#125;],
    <span class="hljs-attr">date</span>: &#123; <span class="hljs-attr">type</span>: <span class="hljs-built_in">Date</span>, <span class="hljs-attr">default</span>: <span class="hljs-built_in">Date</span>.now &#125;,
    <span class="hljs-attr">hidden</span>: <span class="hljs-built_in">Boolean</span>,
    <span class="hljs-attr">meta</span>: &#123;
      <span class="hljs-attr">votes</span>: <span class="hljs-built_in">Number</span>,
      <span class="hljs-attr">favs</span>:  <span class="hljs-built_in">Number</span>
    &#125;
&#125;);
<span class="copy-code-btn">复制代码</span></code></pre>
<p>在这段代码中，规定了<code>blogSchema</code>的字段，以及每一个字段的数据类型。在mongoDB中，collection是document的集合，而Schema对应的是mongoDB的collection。那么，另一个与document对应的概念就是<code>model</code>。一个model的实例就是一个document。因此，mongoDB数据库中数据的增删改查在mongoose中都是利用<code>Model</code>来进行的。使用model的第一步是调用<code>mongoose.model</code>方法：</p>
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-keyword">const</span> Blog = mongoose.model(<span class="hljs-string">'Blog'</span>,blogSchema)
<span class="copy-code-btn">复制代码</span></code></pre>
<p>容易看到，这个方法需要传入两个参数，一个是集合的名称，另一个是<code>schema</code>对象。在调用了这个方法之后，可以进行数据的增删改查操作了：</p>
<ul>
<li>增<br>
向数据库中添加数据的操作，首先需要实例化一个<code>model</code>对象，这个很容易理解，要向数据库添加数据，首先需要有数据才能够添加。然后，调用<code>model.save()</code>方法即可。例子如下：
<pre><code class="hljs language-javascript copyable" lang="javascript"><span class="hljs-keyword">new</span> Blog(&#123;
    <span class="hljs-attr">title</span>:  <span class="hljs-string">'xxx'</span>, <span class="hljs-comment">// String is shorthand for &#123;type: String&#125;</span>
    <span class="hljs-attr">author</span>: <span class="hljs-string">'xxx'</span>,
    <span class="hljs-attr">body</span>:   <span class="hljs-string">'xxx'</span>,
    <span class="hljs-attr">comments</span>: [],
    <span class="hljs-attr">date</span>: <span class="hljs-built_in">Date</span>.now,
    <span class="hljs-attr">hidden</span>: <span class="hljs-literal">true</span>,
    <span class="hljs-attr">meta</span>: &#123;
      <span class="hljs-attr">votes</span>: <span class="hljs-number">0</span>,
      <span class="hljs-attr">favs</span>:  <span class="hljs-number">0</span>
    &#125;
&#125;).save(<span class="hljs-function">(<span class="hljs-params">err</span>) =></span> &#123;
    <span class="hljs-comment">// 这是一个回调函数，处理该条数据保存之后的操作</span>
&#125;)
<span class="copy-code-btn">复制代码</span></code></pre>
<code>model.save()</code>返回的是一个<code>promise</code>对象。因此，回调函数也可以携程链式调用的形式。</li>
<li>删<br>
删除操作有两个方法可以调用：<code>deleteOne()</code>和<code>deleteMany()</code>。使用这两个方法，需要传入需要删除的数据的条件
<pre><code class="hljs language-javascript copyable" lang="javascript">Tank.deleteOne(&#123; <span class="hljs-attr">size</span>: <span class="hljs-string">'large'</span> &#125;, <span class="hljs-function"><span class="hljs-keyword">function</span> (<span class="hljs-params">err</span>) </span>&#123;
  <span class="hljs-keyword">if</span> (err) <span class="hljs-keyword">return</span> handleError(err);
  <span class="hljs-comment">// deleted at most one tank document</span>
&#125;);
<span class="copy-code-btn">复制代码</span></code></pre>
还可以采用<code>Model.findOneAndDelete()</code>,使用方法和前面的一样</li>
<li>改<br>
更新数据的操作可以采用的方法有：
<ul>
<li><code>Model.findOneAndUpdate()</code></li>
<li><code>Model.update()</code></li>
<li><code>Model.updateMany()</code></li>
<li><code>Model.updateOne()</code></li>
</ul>
需要的参数如下：
<ul>
<li>conditions：需要更新的数据的筛选条件</li>
<li>update：更新之后大数据</li>
<li>options：可选参数，该方法的一些配置选项</li>
<li>callback：执行完更新操作之后的回调函数，这里需要注意一个问题：回调函数有两个参数err和data，这里的data表示的是原始数据，而不是更新完之后的数据。</li>
</ul>
</li>
<li>查<br>
查询数据库中数据的方法有：
<ul>
<li><code>Model.find()</code></li>
<li><code>Model.findOne()</code></li>
<li><code>Model.findMany()</code></li>
</ul>
需要的参数仅仅是更新操作除掉第二个参数，其余都相同。</li>
</ul>
<h3 data-id="heading-12">Query</h3>
<p>关于<code>query</code>对象的特性，有很多。但是，似乎在简单的应用里都不怎么能够用得到。但是，可以拿它当<code>promise</code>对象来用。当然，用的时候可以这么用，还是要记住他俩是有区别的。</p>
<h2 data-id="heading-13">写在后面的话</h2>
<p>这篇文章是我第一次使用mongoDB和mongoose做项目之后总结的一些内容，因此原则是够用就好。显然，它们还有很多很多重要的特性。如果需要用到，必须要参考官方的文档了。<br>
官方文档存档：</p>
<ul>
<li><a href="https://link.juejin.cn/?target=https%3A%2F%2Fdocs.mongodb.com%2Fmanual%2Ftutorial%2Fgetting-started%2F" target="_blank" rel="nofollow noopener noreferrer" title="https://docs.mongodb.com/manual/tutorial/getting-started/" ref="nofollow noopener noreferrer">mongoDB官方文档</a></li>
<li><a href="https://link.juejin.cn/?target=https%3A%2F%2Fmongoosejs.com%2Fdocs%2Findex.html" target="_blank" rel="nofollow noopener noreferrer" title="https://mongoosejs.com/docs/index.html" ref="nofollow noopener noreferrer">mongoose官方文档</a></li>
<li><a href="https://link.juejin.cn/?target=https%3A%2F%2Fwww.runoob.com%2Fmongodb%2Fmongodb-tutorial.html" target="_blank" rel="nofollow noopener noreferrer" title="https://www.runoob.com/mongodb/mongodb-tutorial.html" ref="nofollow noopener noreferrer">mongoDB菜鸟教程</a></li>
</ul></div>  
</div>
            
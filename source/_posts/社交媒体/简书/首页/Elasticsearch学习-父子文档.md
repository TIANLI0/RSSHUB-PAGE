
---
title: 'Elasticsearch学习-父子文档'
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
<blockquote>
<p>本文以Elasticsearch 6.8.4版本为例，介绍Elasticsearch父子文档的使用。</p>
</blockquote>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1848" data-height="756"><img data-original-src="//upload-images.jianshu.io/upload_images/9953332-83789c2cbf02976c" data-original-width="1848" data-original-height="756" data-original-format="image/png" data-original-filesize="290039" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">image</div>
</div>
<p>上一篇文章介绍了Elasticsearch的嵌套文档，这一篇来介绍另外一种关系文档，父子文档。</p>
<h2>1、父子文档</h2>
<p>父子文档在理解上来说，可以理解为一个关联查询，有些类似MySQL中的JOIN查询，通过某个字段关系来关联。</p>
<p>父子文档与嵌套文档主要的区别在于，父子文档的父对象和子对象都是独立的文档，而嵌套文档中都在同一个文档中存储，如下图所示：</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="685" data-height="363"><img data-original-src="//upload-images.jianshu.io/upload_images/9953332-e2ba644dfa940f2f" data-original-width="685" data-original-height="363" data-original-format="image/png" data-original-filesize="20248" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">image</div>
</div>
<p>这里引用官网的话，对比嵌套文档来说，父-子关系的主要优势有：</p>
<ul>
<li>更新父文档时，不会重新索引子文档。</li>
<li>创建，修改或删除子文档时，不会影响父文档或其他子文档。这一点在这种场景下尤其有用：子文档数量较多，并且子文档创建和修改的频率高时。</li>
<li>子文档可以作为搜索结果独立返回。</li>
</ul>
<h3>1.1 创建索引</h3>
<p>这里还是以嵌套文档的数据为例，假设数据如下：</p>
<pre><code>[
    &#123;
        "title":"这是一篇文章",
        "body":"这是一篇文章，从哪里说起呢？ ... ..."
    &#125;,
    &#123;
        "name":"张三",
        "comment":"写的不错",
        "age":28,
        "date":"2020-05-04"
    &#125;,
    &#123;
        "name":"李四",
        "comment":"写的很好",
        "age":20,
        "date":"2020-05-04"
    &#125;,
    &#123;
        "name":"王五",
        "comment":"这是一篇非常棒的文章",
        "age":31,
        "date":"2020-05-01"
    &#125;
]
</code></pre>
<p>创建索引名和type均为blog的索引，从上面数据可以看出，其实父文档（博客内容）与子文档分别用不同的字段来存储对应的数据，不过在创建索引文档的时候需要指定父子文档的关系，即文章为parent，留言为child，创建索引语句如下：</p>
<p>PUT <a href="https://links.jianshu.com/go?to=http%3A%2F%2Flocalhost%3A9200%2Fblog%2F" target="_blank">http://localhost:9200/blog/</a></p>
<pre><code>&#123;
  "mappings": &#123;
    "blog": &#123;
      "properties": &#123;
        "date": &#123;
          "type": "date"
        &#125;,
        "name": &#123;
          "type": "text",
          "fields": &#123;
            "keyword": &#123;
              "type": "keyword"
            &#125;
          &#125;
        &#125;,
        "comment": &#123;
          "type": "text",
          "fields": &#123;
            "keyword": &#123;
              "type": "keyword"
            &#125;
          &#125;
        &#125;,
        "age": &#123;
          "type": "long"
        &#125;,
        "body": &#123;
          "type": "text",
          "fields": &#123;
            "keyword": &#123;
              "type": "keyword"
            &#125;
          &#125;
        &#125;,
        "title": &#123;
          "type": "text",
          "fields": &#123;
            "keyword": &#123;
              "type": "keyword"
            &#125;
          &#125;
        &#125;,
        "relation": &#123;
          "type": "join",
          "relations": &#123;
            "parent": "child"
          &#125;
        &#125;
      &#125;
    &#125;
  &#125;
&#125;
</code></pre>
<p>如下图所示</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1109" data-height="591"><img data-original-src="//upload-images.jianshu.io/upload_images/9953332-89e6ff5efbb89f17" data-original-width="1109" data-original-height="591" data-original-format="image/png" data-original-filesize="107189" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">image</div>
</div>
<h3>1.2 插入数据</h3>
<p>插入父文档数据，需要指定上文索引结构中的relation为parent，如下：</p>
<p>POST <a href="https://links.jianshu.com/go?to=http%3A%2F%2Flocalhost%3A9200%2Fblog%2Fblog%2F1%2F" target="_blank">http://localhost:9200/blog/blog/1/</a></p>
<pre><code>&#123;
    "title":"这是一篇文章",
    "body":"这是一篇文章，从哪里说起呢？ ... ...",
    "relation":"parent"
&#125;
</code></pre>
<p>插入子文档，需要在请求地址上使用routing参数指定是谁的子文档，并且指定索引结构中的relation关系，如下：</p>
<p>POST <a href="https://links.jianshu.com/go?to=http%3A%2F%2Flocalhost%3A9200%2Fblog%2Fblog%2F2%3Frouting%3D1" target="_blank">http://localhost:9200/blog/blog/2?routing=1</a></p>
<pre><code>&#123;
    "name":"张三",
    "comment":"写的不错",
    "age":28,
    "date":"2020-05-04",
    "relation":&#123;
        "name":"child",
        "parent":1
    &#125;
&#125;
</code></pre>
<p>POST <a href="https://links.jianshu.com/go?to=http%3A%2F%2Flocalhost%3A9200%2Fblog%2Fblog%2F3%3Frouting%3D1" target="_blank">http://localhost:9200/blog/blog/3?routing=1</a></p>
<pre><code>&#123;
    "name":"李四",
    "comment":"写的很好",
    "age":20,
    "date":"2020-05-04",
    "relation":&#123;
        "name":"child",
        "parent":1
    &#125;
&#125;
</code></pre>
<p>POST <a href="https://links.jianshu.com/go?to=http%3A%2F%2Flocalhost%3A9200%2Fblog%2Fblog%2F4%3Frouting%3D1" target="_blank">http://localhost:9200/blog/blog/4?routing=1</a></p>
<pre><code>&#123;
    "name":"王五",
    "comment":"这是一篇非常棒的文章",
    "age":31,
    "date":"2020-05-01",
    "relation":&#123;
        "name":"child",
        "parent":1
    &#125;
&#125;
</code></pre>
<p>插入完成后，如下图所示。</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1439" data-height="345"><img data-original-src="//upload-images.jianshu.io/upload_images/9953332-37665a6eb0d8d0bb" data-original-width="1439" data-original-height="345" data-original-format="image/png" data-original-filesize="106951" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">image</div>
</div>
<p>从这里其实可以很明显的看出与嵌套文档的区别了，嵌套文档只有一个文档，而这里是有四个文档。</p>
<h3>1.3 查询</h3>
<p>普通查询这里不进行赘述，关系查询的话其实很好理解，大致分为两种特殊情况：</p>
<ol>
<li>根据父文档查询子文档 has_child</li>
<li>根据子文档查询父文档 has_parent</li>
</ol>
<p>接下来我们来看如何进行关系查询，首先看一下通过子文档查询父文档，比如这样的场景，查询名称是张三的人留言的文章，查询语句如下：</p>
<pre><code>&#123;
  "query": &#123;
    "has_child": &#123;
      "type":"child",
      "query": &#123;
        "match": &#123;
          "name": "张三"
        &#125;
      &#125;
    &#125;
  &#125;
&#125;
</code></pre>
<p>查询结果如下：</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1099" data-height="558"><img data-original-src="//upload-images.jianshu.io/upload_images/9953332-6e1b0542cf53a026" data-original-width="1099" data-original-height="558" data-original-format="image/png" data-original-filesize="99932" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">image</div>
</div>
<p>使用has_child来根据子文档内容查询父文档，其实type就是创建文档时，子文档的标识。</p>
<p>在使用子查父的时候，可以添加一些筛选条件来增强匹配的结果，比如最大匹配max_children和最小匹配min_children，这里有点类似should查询的minimum_should_match，感兴趣的可以去官网了解更多的细节。</p>
<p>到这里，其实对Elasticsearch特性了解的读者就会知道如何根据父文档查询子文档了，只需要注意一点，父查子type需要修改成parent_type，其余都与自查父类似，比如查询标题为“这是一篇文章”的数据的留言内容，查询语句如下：</p>
<pre><code>&#123;
  "query": &#123;
    "has_parent": &#123;
      "parent_type":"parent",
      "query": &#123;
        "match": &#123;
          "title": "这是一篇文章"
        &#125;
      &#125;
    &#125;
  &#125;
&#125;
</code></pre>
<p>查询结果如下：</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1435" data-height="954"><img data-original-src="//upload-images.jianshu.io/upload_images/9953332-1084af70f80db8a3" data-original-width="1435" data-original-height="954" data-original-format="image/png" data-original-filesize="161770" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">image</div>
</div>
<blockquote>
<p>由于只有一组父子文档，效果不是很明显，感兴趣可以多造一些数据去体验</p>
</blockquote>
<p>聚合查询与嵌套文档类似，比较简单，这里在说明另外一种场景：祖辈和孙辈可以创建吗？比如本文中的留言如果它也有子文档，那么可以根据文章查询孙辈吗？答案是可以的，只需要在has_child里面在嵌套一层has_child查询即可。</p>
<h3>1.4 使用建议</h3>
<ol>
<li>父子文档都可以独立返回，对于某些场景很适用，比如主表信息是一些基本不变的数据，而子表信息经常增删改，并且子表信息经常有查询场景，这样就很适合使用父子文档。</li>
<li>父子文档需要在同一分片上，当然，我们无需做特殊处理，默认就会为我放入同一个分片，其实原理是这样的，Elasticsearch会根据routing中的参数去看父文档所在分片在哪，然后将对应文档存储进去。</li>
<li>父子文档查询效率相对嵌套文档较低，官网说是5-10倍左右。</li>
</ol>
<blockquote>
<p>其余官网也给定了一些建议，具体可以查看官方文档，地址：<a href="https://links.jianshu.com/go?to=https%3A%2F%2Fwww.elastic.co%2Fguide%2Fcn%2Felasticsearch%2Fguide%2Fcurrent%2Fparent-child-performance.html" target="_blank">https://www.elastic.co/guide/cn/elasticsearch/guide/current/parent-child-performance.html</a></p>
</blockquote>
  
</div>
            
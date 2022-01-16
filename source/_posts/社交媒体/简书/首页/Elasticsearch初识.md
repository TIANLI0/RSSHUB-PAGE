
---
title: 'Elasticsearch初识'
categories: 
 - 社交媒体
 - 简书
 - 首页
headimg: 'https://upload-images.jianshu.io/upload_images/4807654-88eb68a1a94a5e4d.png'
author: 简书
comments: false
date: Invalid Date
thumbnail: 'https://upload-images.jianshu.io/upload_images/4807654-88eb68a1a94a5e4d.png'
---

<div>   
<h2>一、安装和配置</h2>
<h4>1.安装</h4>
<p>elasticsearch默认不允许以root账号运行，所以创建一个用户<br>
创建用户：<code>useradd tracy</code><br>
设置密码：<code>passwd xxx</code><br>
此时可能由于密码过于简单提示，直接再输入一次回车即可</p>
<p>切换用户：<code>su - tracy</code><br>
上传安装包</p>
<p>切回root用户，分配tracy用户权限：<br>
<code>chown tracy:tracy elasticsearch-6.3.0.tar.gz</code><br>
<code>chmod 755 elasticsearch-6.3.0.tar.gz</code><br>
</p><div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="524" data-height="145"><img data-original-src="//upload-images.jianshu.io/upload_images/4807654-88eb68a1a94a5e4d.png" data-original-width="524" data-original-height="145" data-original-format="image/png" data-original-filesize="17019" src="https://upload-images.jianshu.io/upload_images/4807654-88eb68a1a94a5e4d.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">image.png</div>
</div><p></p>
<p>解压之后的目录：</p>
<br>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="450" data-height="160"><img data-original-src="//upload-images.jianshu.io/upload_images/4807654-04cb44340b27a16a.png" data-original-width="450" data-original-height="160" data-original-format="image/png" data-original-filesize="15703" src="https://upload-images.jianshu.io/upload_images/4807654-04cb44340b27a16a.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">image.png</div>
</div>
<h4>2.配置</h4>
<p>如果服务器内存不够，修改config目录下的jvm.options文件：</p>
<br>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="70" data-height="75"><img data-original-src="//upload-images.jianshu.io/upload_images/4807654-0b6ff1586f14e740.png" data-original-width="70" data-original-height="75" data-original-format="image/png" data-original-filesize="1876" src="https://upload-images.jianshu.io/upload_images/4807654-0b6ff1586f14e740.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">image.png</div>
</div>
<p>指定索引库和日志文件、设置允许所有ip访问（默认不允许远程服务器访问）：</p>
<br>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="583" data-height="370"><img data-original-src="//upload-images.jianshu.io/upload_images/4807654-4135b17da1a5f4f0.png" data-original-width="583" data-original-height="370" data-original-format="image/png" data-original-filesize="33108" src="https://upload-images.jianshu.io/upload_images/4807654-4135b17da1a5f4f0.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">image.png</div>
</div>
<p>建立对应的文件夹</p>
<br>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="439" data-height="200"><img data-original-src="//upload-images.jianshu.io/upload_images/4807654-256e60020b00ef3a.png" data-original-width="439" data-original-height="200" data-original-format="image/png" data-original-filesize="19566" src="https://upload-images.jianshu.io/upload_images/4807654-256e60020b00ef3a.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">image.png</div>
</div>
<h4>3.启动</h4>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="608" data-height="614"><img data-original-src="//upload-images.jianshu.io/upload_images/4807654-069d9dad8e4070b4.png" data-original-width="608" data-original-height="614" data-original-format="image/png" data-original-filesize="106295" src="https://upload-images.jianshu.io/upload_images/4807654-069d9dad8e4070b4.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">image.png</div>
</div>
<p>启动中出现以下两个错误：</p>
<br>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="737" data-height="46"><img data-original-src="//upload-images.jianshu.io/upload_images/4807654-5025e7b8bbf77df9.png" data-original-width="737" data-original-height="46" data-original-format="image/png" data-original-filesize="8235" src="https://upload-images.jianshu.io/upload_images/4807654-5025e7b8bbf77df9.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">image.png</div>
</div>
<p>解决：<br>
线程数不够<br>
修改文件 <code>vim /etc/security/limits.d/90-nproc.conf</code><br>
<code>* soft nproc 1024</code>---><code>* soft nproc 4096</code></p>
<p>文件权限不足<br>
切换回root用户，修改文件<code>/etc/security/limits.conf</code><br>
添加内容：</p>
<pre><code>soft nofile 65536
hard nofile 131072
soft nproc 4096
hard nproc 4096
</code></pre>
<p>进程虚拟内存<br>
vm.max_map_count：限制一个进程可以拥有的VMA(虚拟内存区域)的数量，继续修改配置文件:<br>
<code>vim /etc/sysctl.conf</code><br>
添加内容：<code>vm.max_map_count=655360</code><br>
执行命令：<code>sysctl -p</code></p>
<p>安装分词器到elasticsearch/plugins目录下<br>
unzip elasticsearch-analysis-ik-6.3.0.zip -d ik-analyzer</p>
<h2>二、客户端</h2>
<p>Low Level Rest Client是低级别封装，提供一些基础功能，但更灵活</p>
<p>High Level Rest Client，是在Low  Level Rest Client基础上进行的高级别封装，功能更丰富和完善，而且API会变的简单</p>
<h2>三、Spring Data Elasticsearch</h2>
<p>application.yml</p>
<pre><code class="yml">spring:
  data:
    elasticsearch:
      cluster-name: elasticsearch
      cluster-nodes: 120.111.61.110:9300
</code></pre>
<p>pom.xml</p>
<pre><code class="xml"><?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.0.6.RELEASE</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>
    <groupId>com.hcx</groupId>
    <artifactId>elasticsearch</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>elasticsearch</name>
    <description>Demo project for Spring Boot</description>

    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
        <java.version>1.8</java.version>
    </properties>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-elasticsearch</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter</artifactId>
        </dependency>

        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <version>1.18.6</version>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
            <exclusions>
                <exclusion>
                    <groupId>org.junit.vintage</groupId>
                    <artifactId>junit-vintage-engine</artifactId>
                </exclusion>
            </exclusions>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
</project>
</code></pre>
<p>Item:</p>
<pre><code class="java">package com.hcx.pojo;

import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;
import org.springframework.data.annotation.Id;
import org.springframework.data.elasticsearch.annotations.Document;
import org.springframework.data.elasticsearch.annotations.Field;
import org.springframework.data.elasticsearch.annotations.FieldType;

/**
 * Created by hongcaixia on 2020/2/27.
 */
@Data
@Document(indexName = "item",type = "docs",shards = 1,replicas = 0)
@NoArgsConstructor
@AllArgsConstructor
public class Item &#123;
    @Id
    Long id;
    @Field(type = FieldType.Text,analyzer = "ik_max_word")
    String title; //标题
    @Field(type = FieldType.Keyword)
    String category;// 分类
    @Field(type = FieldType.Keyword)
    String brand; // 品牌
    @Field(type = FieldType.Double)
    Double price; // 价格
    @Field(type = FieldType.Keyword,index = false)
    String images; // 图片地址
&#125;
</code></pre>
<p>ItemRepository:</p>
<pre><code class="java">package com.hcx.repository;

import com.hcx.pojo.Item;
import org.springframework.data.elasticsearch.repository.ElasticsearchRepository;

import java.util.List;

/**
 * Created by hongcaixia on 2020/2/28.
 */
public interface ItemRepository extends ElasticsearchRepository<Item,Long>&#123;
    List<Item> findByTitle(String title);
    List<Item> findByPriceBetween(Double d1,Double d2);
&#125;
</code></pre>
<p>ElasticsearchTest:</p>
<pre><code class="java">package com.hcx.elasticsearch;

import com.hcx.pojo.Item;
import com.hcx.repository.ItemRepository;
import org.elasticsearch.index.query.MatchQueryBuilder;
import org.elasticsearch.index.query.QueryBuilders;
import org.elasticsearch.search.aggregations.Aggregation;
import org.elasticsearch.search.aggregations.AggregationBuilders;
import org.elasticsearch.search.aggregations.bucket.terms.StringTerms;
import org.elasticsearch.search.aggregations.metrics.avg.InternalAvg;
import org.elasticsearch.search.sort.SortBuilders;
import org.elasticsearch.search.sort.SortOrder;
import org.junit.Test;
import org.junit.runner.RunWith;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.data.domain.Page;
import org.springframework.data.domain.PageRequest;
import org.springframework.data.domain.Sort;
import org.springframework.data.elasticsearch.core.ElasticsearchTemplate;
import org.springframework.data.elasticsearch.core.aggregation.AggregatedPage;
import org.springframework.data.elasticsearch.core.query.FetchSourceFilter;
import org.springframework.data.elasticsearch.core.query.NativeSearchQueryBuilder;
import org.springframework.test.context.junit4.SpringRunner;

import java.util.*;

/**
 * Created by hongcaixia on 2020/2/27.
 */
@SpringBootTest
@RunWith(SpringRunner.class)
public class ElasticsearchTest &#123;

    @Autowired
    private ElasticsearchTemplate elasticsearchTemplate;

    @Autowired
    private ItemRepository itemRepository;

    @Test
    public void testIndex() &#123;
        elasticsearchTemplate.createIndex(Item.class);
        elasticsearchTemplate.putMapping(Item.class);
    &#125;

    /**
     * 新增/更新
     */
    @Test
    public void testCreate() &#123;
        Item item = new Item(1L, "小米10", "手机", "小米", 3999.00,
                "http:/image.myshoppingmall.com/1.jpg");
        itemRepository.save(item);
    &#125;

    /**
     * 批量新增
     */
    @Test
    public void indexList() &#123;
        List<Item> list = new ArrayList<>();
        list.add(new Item(2L, "坚果pro2", " 手机", "锤子", 3099.00, "http://image.myshoppingmall.com/2.jpg"));
        list.add(new Item(3L, "华为META20", " 手机", "华为", 4399.00, "http://image.myshoppingmall.com/3.jpg"));
        // 接收对象集合，实现批量新增
        itemRepository.saveAll(list);
    &#125;

    /**
     * 删除
     */
    @Test
    public void testDelete() &#123;
        Item item = new Item(1L, "小米10", "手机", "小米", 3999.00,
                "http:/image.myshoppingmall.com/1.jpg");
        itemRepository.delete(item);
    &#125;

    /**
     * 根据id查找单条
     */
    @Test
    public void testFind() &#123;
        Optional<Item> item = itemRepository.findById(1l);
        System.out.println(item.get());
    &#125;

    /**
     * 查询多条并排序
     */
    @Test
    public void testFindAll() &#123;
        Iterable<Item> items = itemRepository.findAll(Sort.by("price").descending());
        items.forEach(System.out::println);
    &#125;

    /**
     * 根据某个字段查询
     */
    @Test
    public void testFindByTitle() &#123;
        List<Item> items = itemRepository.findByTitle("手机");
        items.forEach(System.out::println);
    &#125;

    @Test
    public void testFindByPriceBetween() &#123;
        List<Item> items = itemRepository.findByPriceBetween(3099d, 4999d);
        items.forEach(System.out::println);
    &#125;

    /**
     * 使用查询构建器查询
     */
    @Test
    public void testSearch() &#123;
        //使用查询构建器工具构建查询条件
        MatchQueryBuilder queryBuilder = QueryBuilders.matchQuery("title", "手机");
        Iterable<Item> items = itemRepository.search(queryBuilder);
        items.forEach(System.out::println);
    &#125;

    /**
     * 使用自定义查询构建器
     */
    @Test
    public void testNative() &#123;
        //构建自定义查询构建器
        NativeSearchQueryBuilder queryBuilder = new NativeSearchQueryBuilder();
        //添加基本的查询条件
        queryBuilder.withQuery(QueryBuilders.matchQuery("title", "手机"));
        //执行查询获取分页结果集
        Page<Item> itemPage = itemRepository.search(queryBuilder.build());
        System.out.println(itemPage.getTotalPages());
        System.out.println(itemPage.getTotalElements());
        itemPage.getContent().forEach(System.out::println);
    &#125;

    /**
     * 分页
     */
    @Test
    public void testPage() &#123;
        //构建自定义查询构建器
        NativeSearchQueryBuilder queryBuilder = new NativeSearchQueryBuilder();
        //添加基本的查询条件
        queryBuilder.withQuery(QueryBuilders.matchQuery("title", "手机"));
        //添加分页条件，页码从零开始
        queryBuilder.withPageable(PageRequest.of(0, 2));
        //执行查询获取分页结果集
        Page<Item> itemPage = itemRepository.search(queryBuilder.build());
        System.out.println(itemPage.getTotalPages());
        System.out.println(itemPage.getTotalElements());
        itemPage.getContent().forEach(System.out::println);
    &#125;

    /**
     * 排序
     */
    @Test
    public void testSort() &#123;
        //构建自定义查询构建器
        NativeSearchQueryBuilder queryBuilder = new NativeSearchQueryBuilder();
        //添加基本的查询条件
        queryBuilder.withQuery(QueryBuilders.matchQuery("title", "手机"));
        //根据价格降序
        queryBuilder.withSort(SortBuilders.fieldSort("price").order(SortOrder.DESC));
        //执行查询获取分页结果集
        Page<Item> itemPage = itemRepository.search(queryBuilder.build());
        System.out.println(itemPage.getTotalPages());
        System.out.println(itemPage.getTotalElements());
        itemPage.getContent().forEach(System.out::println);
    &#125;

    @Test
    public void testAggregation() &#123;
        //构建自定义查询构建器
        NativeSearchQueryBuilder queryBuilder = new NativeSearchQueryBuilder();
        //添加聚合
        queryBuilder.addAggregation(AggregationBuilders.terms("brandAgg").field("brand"));
        //添加结果集过滤，不包含任何字段
        queryBuilder.withSourceFilter(new FetchSourceFilter(new String[]&#123;&#125;, null));
        //执行聚合查询
        AggregatedPage<Item> itemPage = (AggregatedPage<Item>) itemRepository.search(queryBuilder.build());
        //解析聚合结果集,根据聚合的类型及字段类型强转 brand:字符串类型；聚合类型：词条聚合
        //通过聚合名称brandAgg 获取聚合对象
        StringTerms brandAgg = (StringTerms) itemPage.getAggregation("brandAgg");
        List<StringTerms.Bucket> buckets = brandAgg.getBuckets();
        buckets.forEach(bucket -> &#123;
            //聚合名称
            System.out.println(bucket.getKeyAsString());
            //记录数
            System.out.println(bucket.getDocCount());
        &#125;);
    &#125;

    @Test
    public void testSubAggregation() &#123;
        //构建自定义查询构建器
        NativeSearchQueryBuilder queryBuilder = new NativeSearchQueryBuilder();
        //添加聚合
        queryBuilder.addAggregation(AggregationBuilders.terms("brandAgg").field("brand")
                .subAggregation(AggregationBuilders.avg("price_avg").field("price")));

        //添加结果集过滤，不包含任何字段
        queryBuilder.withSourceFilter(new FetchSourceFilter(new String[]&#123;&#125;, null));
        //执行聚合查询
        AggregatedPage<Item> itemPage = (AggregatedPage<Item>) itemRepository.search(queryBuilder.build());
        //解析聚合结果集,根据聚合的类型及字段类型强转 brand:字符串类型；聚合类型：词条聚合
        //通过聚合名称brandAgg 获取聚合对象
        StringTerms brandAgg = (StringTerms) itemPage.getAggregation("brandAgg");
        List<StringTerms.Bucket> buckets = brandAgg.getBuckets();
        buckets.forEach(bucket -> &#123;
            //聚合名称
            System.out.println(bucket.getKeyAsString());
            //记录数
            System.out.println(bucket.getDocCount());
            //子聚合map集合：key：聚合名称  value：子聚合对象
            Map<String, Aggregation> stringAggregationMap = bucket.getAggregations().asMap();
            InternalAvg priceAvg = (InternalAvg) stringAggregationMap.get("price_avg");
            System.out.println(priceAvg.getValue());
        &#125;);
    &#125;
&#125;

</code></pre>
  
</div>
            
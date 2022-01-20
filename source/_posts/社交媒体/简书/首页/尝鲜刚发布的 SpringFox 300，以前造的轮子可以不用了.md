
---
title: '尝鲜刚发布的 SpringFox 3.0.0，以前造的轮子可以不用了...'
categories: 
 - 社交媒体
 - 简书
 - 首页
headimg: 'https://upload-images.jianshu.io/upload_images/1447174-b115ca78f4a672fb.png'
author: 简书
comments: false
date: Invalid Date
thumbnail: 'https://upload-images.jianshu.io/upload_images/1447174-b115ca78f4a672fb.png'
---

<div>   
<p>最近 SpringFox 3.0.0 发布了，距离上一次大版本2.9.2足足有2年多时间了。可能看到这个名字，很多读者会有点陌生。但是，只要给大家看一下这两个依赖，你就知道了！</p>
<pre><code class="xml"><dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger2</artifactId>
    <version>3.0.0</version>
    <scope>compile</scope>
</dependency>
<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger-ui</artifactId>
    <version>3.0.0</version>
    <scope>compile</scope>
</dependency>
</code></pre>
<p>当我们在使用Spring MVC写接口的时候，为了生成API文档，为了方便整合Swagger，都是用这个SpringFox的这套封装。但是，自从2.9.2版本更新之后，就一直没有什么动静，也没有更上Spring Boot的大潮流，有一段时间还一直都是写个配置类来为项目添加文档配置的。为此，之前就造了这么个轮子：</p>
<ul>
<li><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2FSpringForAll%2Fspring-boot-starter-swagger" target="_blank">https://github.com/SpringForAll/spring-boot-starter-swagger</a></li>
</ul>
<p>也没什么难度，就是造的早，所以得到了不少Star。现在SpringFox出了一个starter，看了一下功能，虽然还不完美，但相较于之前我们自己的轮子来说还是好蛮多的。来看看这个版本有些什么亮点：</p>
<ul>
<li>Spring 5，Webflux 支持（仅请求映射支持，尚不支持功能端点）</li>
<li>Spring Integration 支持</li>
<li>Spring Boot 支持 springfox-boot-starter 依赖性（零配置，自动配置支持）</li>
<li>具有自动完成功能的文档化配置属性</li>
<li>更好的规范兼容性</li>
<li>支持 OpenApi 3.0.3</li>
<li>几乎零依赖性（唯一需要的库是 spring-plugin、pswagger-core）</li>
<li>现有的 swagger2 注释将继续有效，并丰富 open API 3.0 规范</li>
</ul>
<p>对于这次的更新，我觉得比较突出的几点：Webflux的支持，目前的轮子就没有做到；对OpenApi 3的支持；以及对Swagger 2的兼容（可以比较方便的做升级了）。</p>
<h2>上手尝鲜</h2>
<p>说那么多，不如来一发程序实验下更直接！</p>
<p><strong>第一步</strong>：创建一个Spring Boot项目，这里不展开，不会的看以前的教程：<a href="https://links.jianshu.com/go?to=http%3A%2F%2Fblog.didispace.com%2Fspring-boot-learning-21-1-1%2F" target="_blank">快速入门</a></p>
<p><strong>第二步</strong>：<code>pom.xml</code>中添加依赖：</p>
<pre><code class="xml"><dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-boot-starter</artifactId>
    <version>3.0.0</version>
<dependency>
</code></pre>
<p>现在简洁了不少，一个依赖搞定！</p>
<p><strong>第三步</strong>：应用主类增加注解<code>@EnableOpenApi</code>。</p>
<pre><code class="java">@EnableOpenApi
@SpringBootApplication
public class DemoApplication &#123;

    public static void main(String[] args) &#123;
        SpringApplication.run(DemoApplication.class, args);
    &#125;

&#125;
</code></pre>
<p><strong>第四步</strong>：配置一些接口例子，比如：</p>
<pre><code class="java">@Api(tags="用户管理")
@RestController
public class UserController &#123;

    @ApiOperation("创建用户")
    @PostMapping("/users")
    public User create(@RequestBody @Valid User user) &#123;
        return user;
    &#125;

    @ApiOperation("用户详情")
    @GetMapping("/users/&#123;id&#125;")
    public User findById(@PathVariable Long id) &#123;
        return new User("bbb", 21, "上海", "aaa@bbb.com");
    &#125;

    @ApiOperation("用户列表")
    @GetMapping("/users")
    public List<User> list(@ApiParam("查看第几页") @RequestParam int pageIndex,
                           @ApiParam("每页多少条") @RequestParam int pageSize) &#123;
        List<User> result = new ArrayList<>();
        result.add(new User("aaa", 50, "北京", "aaa@ccc.com"));
        result.add(new User("bbb", 21, "广州", "aaa@ddd.com"));
        return result;
    &#125;

    @ApiIgnore
    @DeleteMapping("/users/&#123;id&#125;")
    public String deleteById(@PathVariable Long id) &#123;
        return "delete user : " + id;
    &#125;

&#125;

@Data
@NoArgsConstructor
@AllArgsConstructor
@ApiModel("用户基本信息")
public class User &#123;

    @ApiModelProperty("姓名")
    @Size(max = 20)
    private String name;
    @ApiModelProperty("年龄")
    @Max(150)
    @Min(1)
    private Integer age;
    @NotNull
    private String address;
    @Pattern(regexp = "^[a-zA-Z0-9_-]+@[a-zA-Z0-9_-]+(\\.[a-zA-Z0-9_-]+)+$")
    private String email;

&#125;
</code></pre>
<p><strong>第五步</strong>：启动应用！访问swagger页面：<code>http://localhost:8080/swagger-ui/index.html</code></p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="2848" data-height="2440"><img data-original-src="//upload-images.jianshu.io/upload_images/1447174-b115ca78f4a672fb.png" data-original-width="2848" data-original-height="2440" data-original-format="image/png" data-original-filesize="313167" src="https://upload-images.jianshu.io/upload_images/1447174-b115ca78f4a672fb.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<blockquote>
<p>注意：</p>
<ol>
<li>这次更新，移除了原来默认的swagger页面路径：<code>http://host/context-path/swagger-ui.html</code>，新增了两个可访问路径：<code>http://host/context-path/swagger-ui/index.html</code>和<code>http://host/context-path/swagger-ui/</code>
</li>
<li>通过调整日志级别，还可以看到新版本的swagger文档接口也有新增，除了以前老版本的文档接口<code>/v2/api-docs</code>之外，还多了一个新版本的<code>/v3/api-docs</code>接口。</li>
</ol>
</blockquote>
<p>本系列教程<a href="https://links.jianshu.com/go?to=http%3A%2F%2Fblog.didispace.com%2Fspring-boot-learning-2x%2F" target="_blank">《Spring Boot 2.x基础教程》点击直达！</a></p>
<h2>代码示例</h2>
<p>本文的相关例子可以查看下面仓库中的<code>chapter2-7</code>目录：</p>
<ul>
<li>Github：<a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Fdyc87112%2FSpringBoot-Learning%2Ftree%2Fmaster%2F2.1.x" target="_blank">https://github.com/dyc87112/SpringBoot-Learning/</a>
</li>
<li>Gitee：<a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgitee.com%2Fdidispace%2FSpringBoot-Learning%2Ftree%2Fmaster%2F2.1.x" target="_blank">https://gitee.com/didispace/SpringBoot-Learning/</a>
</li>
</ul>
<p><strong>如果您觉得本文不错，欢迎<code>Star</code>支持，您的关注是我坚持的动力！</strong></p>
<blockquote>
<p>本文首发：<a href="https://links.jianshu.com/go?to=http%3A%2F%2Fblog.didispace.com%2Fspring-boot-learning-21-2-7%2F" target="_blank">尝鲜刚发布的 SpringFox 3.0.0，以前造的轮子可以不用了...</a>，转载请注明出处。<br>
欢迎关注我的公众号：程序猿DD，获得独家整理的学习资源和日常干货推送。<a href="https://links.jianshu.com/go?to=http%3A%2F%2Fblog.didispace.com%2Fspring-boot-learning-2x%2F" target="_blank">点击直达本系列教程目录</a>。</p>
</blockquote>
  
</div>
            
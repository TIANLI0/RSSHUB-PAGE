
---
title: 'Flutter 完整页面Widget：Material App、Scaffold、AppBar'
categories: 
 - 社交媒体
 - 简书
 - 首页
headimg: 'https://upload-images.jianshu.io/upload_images/944365-207a738cb165a2da.png'
author: 简书
comments: false
date: Invalid Date
thumbnail: 'https://upload-images.jianshu.io/upload_images/944365-207a738cb165a2da.png'
---

<div>   
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="840" data-height="860"><img data-original-src="//upload-images.jianshu.io/upload_images/944365-207a738cb165a2da.png" data-original-width="840" data-original-height="860" data-original-format data-original-filesize="528657" src="https://upload-images.jianshu.io/upload_images/944365-207a738cb165a2da.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<hr>
<h1>前言</h1>
<ul>
<li>
<p>Flutter 作为Google出品的一个<strong>新兴的跨平台移动客户端UI开发框架</strong>，正在被越来越多的开发者和组织使用，包括阿里的咸鱼、腾讯的微信等。<br>
</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="696" data-height="356"><img data-original-src="//upload-images.jianshu.io/upload_images/944365-1662841bfd1efe67.png" data-original-width="696" data-original-height="356" data-original-format="image/png" data-original-filesize="51729" src="https://upload-images.jianshu.io/upload_images/944365-1662841bfd1efe67.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">示意图</div>
</div>
<p></p>
</li>
<li><p>今天，我主要讲解Flutter中完整页面方面的Widget，包括<code>Material App</code>、<code>Scaffold</code>、<code>AppBar</code>，希望你们会喜欢。</p></li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="526" data-height="442"><img data-original-src="//upload-images.jianshu.io/upload_images/944365-398161831814d7c3.png" data-original-width="526" data-original-height="442" data-original-format="image/png" data-original-filesize="45613" src="https://upload-images.jianshu.io/upload_images/944365-398161831814d7c3.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">示意图</div>
</div>
<hr>
<h1>1. Material App</h1>
<ul>
<li>定义：使用Material Design设计风格的应用的顶层主界面入口，包含主题颜色、标题、主颜色等。</li>
<li>作用：包含了Material Design设计风格的应用所需要的基本控件</li>
<li>常用属性：</li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="940" data-height="594"><img data-original-src="//upload-images.jianshu.io/upload_images/944365-a4c2fd56f9562ce1.png" data-original-width="940" data-original-height="594" data-original-format="image/png" data-original-filesize="102146" src="https://upload-images.jianshu.io/upload_images/944365-a4c2fd56f9562ce1.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">示意图</div>
</div>
<p>此处详细列出主题（Theme）的设置</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="800" data-height="490"><img data-original-src="//upload-images.jianshu.io/upload_images/944365-170a1157aab7a5c2.png" data-original-width="800" data-original-height="490" data-original-format="image/png" data-original-filesize="154288" src="https://upload-images.jianshu.io/upload_images/944365-170a1157aab7a5c2.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">示意图</div>
</div>
<ul>
<li>代码演示</li>
</ul>
<pre><code>import 'package:flutter/material.dart'; // Material UI组件库

void main() => runApp(MyApp());

// 无状态控件显示
class MyApp extends StatelessWidget&#123;

  @override
  Widget build(BuildContext context)&#123;
// 主界面入口返回的组件 = MaterialApp
    return MaterialApp(
      title:'Widget_Demo',//标题
      theme:ThemeData(primarySwatch: Colors.blue),//主题色
      home:MyHomePage(),// 返回一个Widget对象，用来定义当前应用打开的时候，所显示的界面
    );
  &#125;
&#125;

// 返回的Widget对象
class MyHomePage extends StatelessWidget&#123;

  @override
  Widget build(BuildContext context)&#123;
    return Scaffold(
      //设置appbar
      appBar:new AppBar(
        title:new Text('Flutter Demo'),
      ),
      //主体
      body:new Center(
        //在屏幕中央显示一个文本
        child:new Text('carsonho demo'),
      ),
    );
  &#125;
&#125;
</code></pre>
<ul>
<li>效果</li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="271" data-height="399"><img data-original-src="//upload-images.jianshu.io/upload_images/944365-c2b7f4be4d631e0a.png" data-original-width="271" data-original-height="399" data-original-format="image/png" data-original-filesize="9288" src="https://upload-images.jianshu.io/upload_images/944365-c2b7f4be4d631e0a.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">示意图</div>
</div>
<hr>
<h1>2. Scaffold</h1>
<p>实现了基本的 Material Dsign布局，含AppBar、Body主题内容等。</p>
<ul>
<li>设置属性</li>
</ul>
<pre><code>Scaffold(&#123;
    Key key,
    this.appBar,// 设置应用栏，显示在脚手架顶部
    this.body,// 设置脚手架内容区域控件
    this.floatingActionButton,//设置显示在上层区域的按钮，默认位置位于右下角
    this.floatingActionButtonLocation,// 设置floatingActionButton的位置
    this.floatingActionButtonAnimator,// floatingActionButtonAnimator 动画
    this.persistentFooterButtons,// 一组显示在脚手架底部的按钮(在bottomNavigationBar底部导航栏的上面)
    this.drawer,// 设置左边侧边栏
    this.endDrawer,// 设置右边侧边栏
    this.bottomNavigationBar,// 设置底部导航栏
    this.bottomSheet,// 底部抽屉栏
    this.backgroundColor,// 设置脚手架内容区域的颜色
    this.resizeToAvoidBottomPadding = true,// 控制界面内容 body 是否重新布局来避免底部被覆盖，比如当键盘显示的时候，重新布局避免被键盘盖住内容。
  &#125;)
</code></pre>
<ul>
<li>具体使用</li>
</ul>
<pre><code>void main() => runApp(MyApp());

//用无状态控件显示
class MyApp extends StatelessWidget&#123;

  @override
  Widget build(BuildContext context)&#123;
    return MaterialApp(
      title:'Widget_Demo',//标题
      theme:ThemeData(primarySwatch: Colors.blue),//主题色
      home:MyHomePage(),// 返回一个Widget对象，用来定义当前应用打开的时候，所显示的界面
    );
  &#125;
&#125;

// 返回的Widget对象
class MyHomePage extends StatelessWidget&#123;

  @override
  Widget build(BuildContext context)&#123;
    return Scaffold(
      //设置appbar
      appBar:new AppBar(
        title:new Text('Flutter Demo'),
      ),
      //主体
      body:new Center(
        //在屏幕中央显示一个文本
        child:new Text('carsonho demo'),
      ),
      // 设置左侧抽屉，添加一个空的ListView
      drawer:Drawer(
        child:new Center(
          //在屏幕中央显示一个文本
          child:new Text('Scafflod Drawer'),
        ),
      ),
    );
  &#125;
&#125;
</code></pre>
<ul>
<li>示意图</li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="274" data-height="396"><img data-original-src="//upload-images.jianshu.io/upload_images/944365-f2293582bc027bb0.gif" data-original-width="274" data-original-height="396" data-original-format="image/gif" data-original-filesize="500831" src="https://upload-images.jianshu.io/upload_images/944365-f2293582bc027bb0.gif" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">示意图</div>
</div>
<hr>
<h1>3. AppBar</h1>
<ul>
<li><p>定义：Material风格应用栏，具备工具栏 & 其他小型Widget</p></li>
<li><p>应用场景：用于Scaffold.appBar属性</p></li>
<li><p>属性设置</p></li>
</ul>
<pre><code>AppBar(&#123;
    Key key,
    this.leading, // Widget，title前面的组件，一般是图标按钮
    this.automaticallyImplyLeading = true, // 配合leading使用，取决于automaticallyImplyLeading == true && leading ==null
    this.title, // Widget，AppBar的标题，类型为Widget，一般显示文本
    this.actions, // Widget List，一个 Widget 列表，代表 Toolbar 中所显示的菜单，对于常用的菜单，通常使用 IconButton 来表示；对于不常用的菜单通常使用 PopupMenuButton 来显示为三个点，点击后弹出二级菜单。
    this.flexibleSpace, //  Widget，一个显示在 AppBar 下方的控件，高度和 AppBar 高度一样，可以实现一些特殊的效果，该属性通常在 SliverAppBar 中使用。
    this.bottom, // PreferredSizeWidget，出现在应用程序栏底部的组件，通常是一个标签栏（TarBar）
    this.elevation, // 控制下方阴影栏的坐标
    this.backgroundColor, // 背景颜色
    this.brightness, // Brightness，亮度，有白色和黑色两种主题，默认值为 ThemeData.primaryColorBrightness。
    this.iconTheme, // IconThemeData - Appbar 上图标的颜色、透明度、和尺寸信息。默认值为 ThemeData.primaryIconTheme。
    this.textTheme, // TextTheme，Appbar 上的文字样式。
    this.primary = true, // appbar是否显示在任务栏顶部
    this.centerTitle, // bool，标题是否居中显示，默认值根据不同的操作系统，显示方式不一样。
    this.titleSpacing = NavigationToolbar.kMiddleSpacing,
    this.toolbarOpacity = 1.0, // 顶部栏的透明度：值1.0 = 完全不透明，值0.0 = 完全透明
    this.bottomOpacity = 1.0, // 底部栏的透明度：值1.0 = 完全不透明，值0.0 = 完全透明
  &#125;)

</code></pre>
<ul>
<li>代码演示</li>
</ul>
<pre><code>void main() => runApp(MyApp());

//用无状态控件显示
class MyApp extends StatelessWidget&#123;

  @override
  Widget build(BuildContext context)&#123;
    return MaterialApp(
      title:'Widget_Demo',//标题
      theme:ThemeData(primarySwatch: Colors.blue),//主题色
      home:MyHomePage(),// 返回一个Widget对象，用来定义当前应用打开的时候，所显示的界面
    );
  &#125;
&#125;

// 返回的Widget对象
class MyHomePage extends StatelessWidget&#123;

  @override
  Widget build(BuildContext context)&#123;
    return Scaffold(
      //设置appbar
      appBar:new AppBar(
        title: new Text('首页'),
        leading: new Icon(Icons.home),
        backgroundColor: Colors.blue,
        centerTitle: true,
        actions: <Widget>[ // 设置title后的WidgetList
          // 非隐藏的菜单
          new IconButton(
              icon: new Icon(Icons.add_alarm),
              tooltip: 'Add Alarm',
              onPressed: () &#123;&#125;
          ),
          // 隐藏的菜单
          new PopupMenuButton<String>(
            itemBuilder: (BuildContext context) => <PopupMenuItem<String>>[
              gethideItem(Icons.message, '聊天', '1'),
              gethideItem(Icons.group_add, '添加', '2'),
              gethideItem(Icons.cast_connected, '连接', '3'),
            ],
            onSelected: (String action) &#123;
              // 点击选项的时候
              switch (action) &#123;
                case '1':
                  print(1);
                  break;
                case '2':
                  print(2);
                  break;
                case '3':
                  print(3);
                  break;
              &#125;
            &#125;,
          ),
        ],
      ),
      //主体
      body:new Center(
        //在屏幕中央显示一个文本
        child:new Text('carsonho demo'),
      ),
      // 设置左侧抽屉，添加一个空的ListView
    );
  &#125;

// 方便返回每个隐藏的菜单项
  gethideItem(IconData icon, String text, String id) &#123;
    return new PopupMenuItem<String>(
        value: id,
        child: new Row(
          mainAxisAlignment: MainAxisAlignment.spaceEvenly,
          children: <Widget>[
            new Icon(icon, color: Colors.blue),
            new Text(text),
          ],
        )
    );
  &#125;
&#125;
</code></pre>
<ul>
<li>示意图</li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="274" data-height="396"><img data-original-src="//upload-images.jianshu.io/upload_images/944365-03db05aa18a8c9a4.gif" data-original-width="274" data-original-height="396" data-original-format="image/gif" data-original-filesize="519193" src="https://upload-images.jianshu.io/upload_images/944365-03db05aa18a8c9a4.gif" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<hr>
<h1>4. 总结</h1>
<ul>
<li>本文主要讲解了Flutter中完整页面方面的Widget，包括<code>Material App</code>、<code>Scaffold</code>、<code>AppBar</code>
</li>
<li>接下来推出的文章，我将继续讲解Flutter的相关知识，包括更多的Widget用法、实例应用等，感兴趣的读者可以继续关注我的博客哦：<a href="https://www.jianshu.com/users/383970bef0a0/latest_articles" target="_blank">Carson_Ho的Android博客</a>
</li>
</ul>
<hr>
<h1>请点赞！因为你们的赞同/鼓励是我写作的最大动力！</h1>
<blockquote>
<p><strong>相关文章阅读</strong><br>
<a href="https://www.jianshu.com/p/ec5a1a30694b" target="_blank">Android开发：最全面、最易懂的Android屏幕适配解决方案</a><br>
<a href="https://www.jianshu.com/p/b61a49e0279f" target="_blank">Android开发：史上最全的Android消息推送解决方案</a><br>
<a href="https://www.jianshu.com/p/3c94ae673e2a" target="_blank">Android开发：最全面、最易懂的Webview详解</a><br>
<a href="https://www.jianshu.com/p/b87fee2f7a23" target="_blank">Android开发：JSON简介及最全面解析方法!</a><br>
<a href="https://www.jianshu.com/p/d963c55c3ab9" target="_blank">Android四大组件：Service服务史上最全面解析</a><br>
<a href="https://www.jianshu.com/p/ca3d87a4cdf3" target="_blank">Android四大组件：BroadcastReceiver史上最全面解析</a></p>
</blockquote>
<hr>
<h3>欢迎关注<a href="https://www.jianshu.com/users/383970bef0a0/latest_articles" target="_blank">Carson_Ho</a>的简书！</h3>
<p>不定期分享关于<strong>安卓开发</strong>的干货，追求<strong>短、平、快</strong>，但<strong>却不缺深度</strong>。</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="840" data-height="860"><img data-original-src="//upload-images.jianshu.io/upload_images/944365-9b76fa3c52d478a7.png" data-original-width="840" data-original-height="860" data-original-format data-original-filesize="537233" src="https://upload-images.jianshu.io/upload_images/944365-9b76fa3c52d478a7.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
  
</div>
            
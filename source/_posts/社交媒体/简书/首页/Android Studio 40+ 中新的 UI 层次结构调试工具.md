
---
title: 'Android Studio 4.0+ 中新的 UI 层次结构调试工具'
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
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="640" data-height="480"><img data-original-src="//upload-images.jianshu.io/upload_images/7095626-8f66d8d6720457fb" data-original-width="640" data-original-height="480" data-original-format="image/gif" data-original-filesize="842322" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<p>调试 UI 的问题有时很棘手，Android Studio 4.0 内置了全新的布局检查器 (Layout Inspector)，它的使用效果类似 Chrome 开发者工具，可以帮助开发者调试 Android 应用的 UI (用户界面)。布局检查器可用于设备和 Android 模拟器，它可以展示视图的层次结构。该工具有助于定位由根节点引起的问题。和上一个版本不同的是，新版本的布局检查器可以以三维的视角来展现视图层次结构，您可以直观地看到视图的布局方式。通过该工具您可以逐层来检查视图层次结构，同时它还会展示所有视图的属性，包括继承自视图父类的属性。</p>
<p>接下来我们一起了解一下最新版本的布局检查器是如何发挥作用的。首先点击窗口的 <strong>View</strong> 菜单，找到 Tool Window 子菜单，然后选择<strong>Layout Inspector</strong>，这样就打开了布局检查器窗口。</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="640" data-height="462"><img data-original-src="//upload-images.jianshu.io/upload_images/7095626-4e4f217b34f5fef0" data-original-width="640" data-original-height="462" data-original-format="image/gif" data-original-filesize="351343" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<p>布局检查器仅显示正在运行的进程的 UI 层次结构。也就是说您需要连接到设备或者模拟器上的一个正在运行的可调试应用，有两种方式可以满足该条件:</p>
<ul>
<li><p>如果您没有正在运行的进程，那么需要首先连接到一台设备或者启动一个 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fdeveloper.android.google.cn%2Fstudio%2Frun%2Femulator" target="_blank">Android 模拟器实例</a>，并且点击窗口的 <strong>Run</strong> 按钮来启动应用；</p></li>
<li>
<p>如果您的应用进程已经运行，点击 <strong>select process</strong>，选择正在运行的设备，然后从设备右侧的列表来选择一个已运行的应用。<br>
</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="640" data-height="480"><img data-original-src="//upload-images.jianshu.io/upload_images/7095626-dbe22c65a8b8f895" data-original-width="640" data-original-height="480" data-original-format="image/gif" data-original-filesize="212422" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<p></p>
</li>
</ul>
<p>选择所需的应用进程后，布局检查器会基于当前 UI 层次结构创建一个快照。如果您启用了 <strong>Live Updates</strong> 选项，那么当您在设备上操作界面时，快照会动态更新。</p>
<p>该版本的布局检查器延续了之前版本的功能并且更加多样化。首先，布局检查器可以用两种方式显示 UI 层次结构: 以二维的轮廓格式，或者以一种称为旋转模式 (rotation mode) 的三维视图形式。</p>
<br>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="62" data-height="66"><img data-original-src="//upload-images.jianshu.io/upload_images/7095626-7787d7351e780a67" data-original-width="62" data-original-height="66" data-original-format="image/png" data-original-filesize="467" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<p>点击 rotation 按钮会在二维和三维视图之间进行切换。当处于旋转模式时，您可以旋转 UI 层次结构。旋转操作可以帮助您更直观地了解视图的组织结构。请注意，旋转仅在 Android 10 或以上的设备上才可以使用。</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="640" data-height="480"><img data-original-src="//upload-images.jianshu.io/upload_images/7095626-d3fcbb9f23ca8ea9" data-original-width="640" data-original-height="480" data-original-format="image/gif" data-original-filesize="842322" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">您也可以选中一个视图，然后右键点击它后，窗口仅显示它的子视图。</div>
</div>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="640" data-height="480"><img data-original-src="//upload-images.jianshu.io/upload_images/7095626-3bea980d948dd86f" data-original-width="640" data-original-height="480" data-original-format="image/gif" data-original-filesize="1945274" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">同样，您可以仅显示一个所选视图的父视图。</div>
</div><br>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="640" data-height="480"><img data-original-src="//upload-images.jianshu.io/upload_images/7095626-e6255f9c29185833" data-original-width="640" data-original-height="480" data-original-format="image/gif" data-original-filesize="2357717" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<p>右侧的窗格会显示所选视图的所有已声明的属性和继承的属性。您可以通过点击任何已声明的属性来打开布局相关的 xml 文件。和旋转特性一样，这个功能也仅适用于 Android 10 以上的设备。</p>
<br>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="640" data-height="480"><img data-original-src="//upload-images.jianshu.io/upload_images/7095626-08f4e71c08a6d959" data-original-width="640" data-original-height="480" data-original-format="image/gif" data-original-filesize="440056" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<p>通过布局检查器您还可以将新设计的界面和现有 UI 进行比较。要加载布局设计，点击 Load Overlay，然后选择一个布局设计。图片成功加载后，您可以改变它的半透明值 (alpha) 来比较现有布局与所选的设计布局之间的区别。</p>
<h2>布局检查器示例</h2>
<p>现在大家已经了解了布局检查器的使用方式。那么接下来我们通过实例来看一下如何使用它来解决应用的问题。这里我们有一个简单的示例应用，它包含一个 fragment，其中有一些静态文本和一个图片。如果您在阅读文章时想同步进行操作，可以先按照下面步骤操作创建工程。</p>
<ol>
<li>打开 Android Studio 4.0，然后在 File 菜单里选择 New Project；</li>
<li>选择 Bottom Navigation Activity，点击 Next 然后点击 Finish；</li>
<li>替换 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgist.github.com%2Fyenerm%2F9a07014e71a9a9df4c0c72bd615d0671" target="_blank">activity_main.xml</a> 和 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgist.github.com%2Fyenerm%2Fb0b84304fa57e8c9f99433eb489eba26" target="_blank">fragment_home.xml</a> 的内容；</li>
<li>替换 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgist.github.com%2Fyenerm%2F7418d98137118d1e96f2e655346c54b4" target="_blank">HomeFragment.kt</a> 的内容。</li>
</ol>
<p>当您运行应用的时候，您会看到一个可爱的 android，但是里面少了一些东西: 底部的导航标签。看一下布局文件，我们可以看到底部的导航视图是存在的，但是屏幕却没有显示它。</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1080" data-height="1283"><img data-original-src="//upload-images.jianshu.io/upload_images/7095626-8a68090460a1b4c0" data-original-width="1080" data-original-height="1283" data-original-format="image/png" data-original-filesize="77286" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<p>看来布局检查器大显身手的时候到了: 我们运行一下程序并检查一下这个问题，成功连接应用进程后，切换到旋转视图会看到应用的 UI 出现了问题。</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1080" data-height="694"><img data-original-src="//upload-images.jianshu.io/upload_images/7095626-b0b06de69d10f6bc" data-original-width="1080" data-original-height="694" data-original-format="image/png" data-original-filesize="68564" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<p>首先我们可以看到 LinearLayout 里布局了一个工具栏 (toolbar)，然后是 navigation host。在它下面，您可以看到导航栏位于最下方——看来底部的导航栏被挤出了屏幕。</p>
<p>有可能是 navigation host 的尺寸设置错了，我们尝试把它的高度设置为 'wrap_content':</p>
<pre><code>
<!-- Copyright 2019 Google LLC.
SPDX-License-Identifier: Apache-2.0 -->

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/container"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent" >

    <fragment
        android:id="@+id/nav_host_fragment"
        android:name="androidx.navigation.fragment.NavHostFragment"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:defaultNavHost="true"
        android:layout_weight="9"
        app:navGraph="@navigation/mobile_navigation" />
    <com.google.android.material.bottomnavigation.BottomNavigationView
        android:id="@+id/nav_view"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_weight="1"
        android:background="?android:attr/windowBackground"
        app:menu="@menu/bottom_nav_menu" />
</LinearLayout>
</code></pre>
<p>回到布局检查器，您可以看到 LinearLayout 的尺寸正常了，但是底部的导航栏的位置不对:</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="706" data-height="676"><img data-original-src="//upload-images.jianshu.io/upload_images/7095626-bfc2193ca7fdc905" data-original-width="706" data-original-height="676" data-original-format="image/png" data-original-filesize="64245" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<p>有很多方法可以解决这个问题: 我们可以设置 navigation host 和底部导航栏的 layout_weight 参数，或者我们可以将 LinearLayout 换成 ConstraintLayout，但是切换布局不是本文的重点，所以我们设置一下 layout_weights 参数:</p>
<pre><code>
<!-- Copyright 2019 Google LLC.
SPDX-License-Identifier: Apache-2.0 -->

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/container"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent" >

    <fragment
        android:id="@+id/nav_host_fragment"
        android:name="androidx.navigation.fragment.NavHostFragment"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:defaultNavHost="true"
        android:layout_weight="9"
        app:navGraph="@navigation/mobile_navigation" />
    <com.google.android.material.bottomnavigation.BottomNavigationView
        android:id="@+id/nav_view"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_weight="1"
        android:background="?android:attr/windowBackground"
        app:menu="@menu/bottom_nav_menu" />
</LinearLayout>
</code></pre>
<p>然后得到如下结果:</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="622" data-height="433"><img data-original-src="//upload-images.jianshu.io/upload_images/7095626-9ad0f4442ad5ce07" data-original-width="622" data-original-height="433" data-original-format="image/png" data-original-filesize="33944" src="https://www.jianshu.com/p/undefined" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<p>再运行应用的时候，布局就正常了。</p>
<p>快快尝试一下布局检查器的新特性，然后和我们分享您的使用体验吧。欢迎大家向我们反馈问题，或者告诉我们新的特性需求。<br>
<strong><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fdeveloper.android.google.cn%2Fstudio%2Fdebug%2Flayout-inspector" target="_blank">点击这里</a>查看 Android 官方中文文档 —— 使用布局检查器调试布局</strong><br>
</p><div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="836" data-height="345"><img data-original-src="//upload-images.jianshu.io/upload_images/7095626-6e2e468963e67c76.jpg" data-original-width="836" data-original-height="345" data-original-format="image/png" data-original-filesize="19070" src="https://upload-images.jianshu.io/upload_images/7095626-6e2e468963e67c76.jpg" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div><p></p>
  
</div>
            
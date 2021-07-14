
---
title: 'three.js 入门第一天'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e9384c18f24b481fa452aaeb45e0a5b1~tplv-k3u1fbpfcp-zoom-1.image'
author: 掘金
comments: false
date: Tue, 13 Jul 2021 05:08:26 GMT
thumbnail: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e9384c18f24b481fa452aaeb45e0a5b1~tplv-k3u1fbpfcp-zoom-1.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><h5 data-id="heading-0">一、three.js和webGL</h5>
<ul>
<li>引用官方的说法：</li>
</ul>
<p>three.js是使用WebGL来绘制三维效果的，three.js封装了诸如场景、灯光、阴影、材质、贴图、空间运算等一系列功能，让你不必要再从底层WebGL开始写起。
three官网</p>
<h5 data-id="heading-1">二、官网说明</h5>
<p>1.打开官网看到下图，右边是一些3d样例，对初学没什么用。
<img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e9384c18f24b481fa452aaeb45e0a5b1~tplv-k3u1fbpfcp-zoom-1.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p>左边r130代表的版本号，这边建议大家去看的是文档说明(documentation)和resources的第一个学习资源(Three.js Fundamentals),他们都有对应的中文翻译，讲的比较基础适合入门。
<img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f0220f2cbf394439a947e7cd3125212c~tplv-k3u1fbpfcp-zoom-1.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h5 data-id="heading-2">三、three.js版本选择</h5>
<ol>
<li>three.js版本更新的很快，今天你下载了一个新版本，明天可能又更新了。很多旧版的方法在新版中被删除，一些方法的引用文件也有所改变，在网上搜索到的很多教程都是r6-r9版本，方法的使用看起来也是各异，学习起来挺混乱的。这里我使用r130版本（编写这边文章时候的最新版本）。各版本官方<a href="https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fmrdoob%2Fthree.js%2Ftags" target="_blank" rel="nofollow noopener noreferrer" title="https://github.com/mrdoob/three.js/tags" ref="nofollow noopener noreferrer">下载地址</a></li>
</ol>
<p>2.下载完之后解压得到three.js-master文件夹。这边将build里面的three.js拿出来，在自己项目做练习，examples里面有各种样例的代码包括了素材和对应的js依赖，之后可以拿来做练习（毕竟3d素材自己不好弄）
<img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/36d4e6b770f941b5821c3dd4cf60fb65~tplv-k3u1fbpfcp-zoom-1.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<h5 data-id="heading-3">四、开发工具</h5>
<p>我使用的vscode ，安装live Server插件，可以跑本地服务，解决了图片等素材引用的跨域安全问题，当然你也可以直接使用官方的脚手架来练习。官方脚手架需要node环境，如果不了解的建议使用vscode。</p>
<h5 data-id="heading-4">五、第一个3d程序</h5>
<pre><code class="copyable"><html>
<head>
    <meta charset="utf-8">
    <title>My first three.js app</title>
    <style>
        body &#123;
            margin: 0;
            padding:0;
        &#125;
    </style>
</head>

<body>
    <script src="js/three.js"></script>
    <script>
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, 
        window.innerWidth / window.innerHeight, 0.1, 1000);

        const renderer = new THREE.WebGLRenderer();
        renderer.setSize(window.innerWidth, window.innerHeight);
        document.body.appendChild(renderer.domElement);

        const geometry = new THREE.BoxGeometry();
        const material = new THREE.MeshBasicMaterial(&#123;
            color: 0x00ff00
        &#125;);
        const cube = new THREE.Mesh(geometry, material);
        scene.add(cube);

         camera.position.z = 5;
            const animate = function () &#123;
                requestAnimationFrame(animate);
                cube.rotation.x += 0.01;
                cube.rotation.y += 0.01;
                renderer.render(scene, camera);
            &#125;;
            animate();
      
    </script>
</body>
</html>
<span class="copy-code-btn">复制代码</span></code></pre>
<p>1.创建了一个场景，也就是3d模型等展示的舞台</p>
<pre><code class="copyable">const scene = new THREE.Scene();
<span class="copy-code-btn">复制代码</span></code></pre>
<p>2.创建一个相机，他拍到的地方就是我们看到的内容，这里创建的是透视相PerspectiveCamera</p>
<pre><code class="copyable">const camera = new THREE.PerspectiveCamera(50, window.innerWidth /
 window.innerHeight, 0.1, 1000);
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>第一个参数：是角度表示看到的范围</li>
<li>第二个表示：长宽比，作用是展示的物体可以正常比例显示</li>
<li>三四参数表示：近截面（near）和远截面（far），当物体某些部分比摄像机的远截面远或者比近截面近的时候，该这些部分将不会被渲染到场景中。如下图（图片源自官网）</li>
</ul>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/16f15b2a59b74b6f88ff3d7480feae42~tplv-k3u1fbpfcp-zoom-1.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p>3.创建一个渲染器，将场景和相机放入，渲染画面，设置渲染范围，并添加到页面中</p>
<pre><code class="copyable">const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);
<span class="copy-code-btn">复制代码</span></code></pre>
<p>4.创建简单的3d模型</p>
<pre><code class="copyable">
// 创建一个正方体
const geometry = new THREE.BoxGeometry();
// 创建网格基础材质 可以理解为外表样子，材质有很多种，详细可以查文档
const material = new THREE.MeshBasicMaterial(&#123;
    color: 0x00ff00
&#125;);
 // 创建网格 将他们加入网格中在添加到场景，
 // 网格包含一个几何体以及作用在此几何体上的材质
const cube = new THREE.Mesh(geometry, material);
scene.add(cube);
<span class="copy-code-btn">复制代码</span></code></pre>
<p>5.渲染</p>
<pre><code class="copyable">
// 这边是将相机拉远了，便于观察。如下图所示
camera.position.z = 5;
// 添加动画，渲染
const animate = function () &#123;
  requestAnimationFrame( animate );
  cube.rotation.x += 0.01;
  cube.rotation.y += 0.01;
  renderer.render( scene, camera );
 &#125;;
  animate();
<span class="copy-code-btn">复制代码</span></code></pre>
<p>5.效果图
<img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/bf50901c8c134d52827f416056a86d9f~tplv-k3u1fbpfcp-zoom-1.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p></div>  
</div>
            
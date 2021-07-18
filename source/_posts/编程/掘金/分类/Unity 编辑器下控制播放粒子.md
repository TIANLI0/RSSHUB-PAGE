
---
title: 'Unity 编辑器下控制播放粒子'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/204e1a7f9a3b45e7addf7c68264cd80b~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Sat, 17 Jul 2021 05:37:24 GMT
thumbnail: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/204e1a7f9a3b45e7addf7c68264cd80b~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><p>在Unity编辑器的Scene视图进行控制播放粒子ParticleSystem，可以借助方法Simulate，具体可以参照以下例子：</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/204e1a7f9a3b45e7addf7c68264cd80b~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<p>创建一个空对象ParticleAll，在这个对象下添加一个粒子（要添加多个粒子的话，添加到这个粒子之下），此时选中粒子， 可以看到 Scene视图预览播放粒子效果。附上新脚本 EditParticleSystem ，此为空脚本，如下：</p>
<pre><code class="hljs language-csharp copyable" lang="csharp"><span class="hljs-keyword">using</span> UnityEngine;

<span class="hljs-keyword">public</span>  <span class="hljs-keyword">class</span> <span class="hljs-title">EditParticleSystem</span> : <span class="hljs-title">MonoBehaviour</span>
&#123;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>创建一个这个脚本的编辑器类 <strong>EditParticleSystemInspector</strong>，代码如下：</p>
<pre><code class="hljs language-csharp copyable" lang="csharp"><span class="hljs-keyword">using</span> UnityEditor;
<span class="hljs-keyword">using</span> UnityEngine;

[<span class="hljs-meta">CustomEditor( typeof(EditParticleSystem))</span>]
<span class="hljs-keyword">public</span>  <span class="hljs-keyword">class</span> <span class="hljs-title">EditParticleSystemInspector</span> : <span class="hljs-title">Editor</span>
&#123;
     <span class="hljs-comment"><span class="hljs-doctag">///</span> <span class="hljs-doctag"><summary></span></span>
     <span class="hljs-comment"><span class="hljs-doctag">///</span> 滑动杆的当前时间</span>
     <span class="hljs-comment"><span class="hljs-doctag">///</span> <span class="hljs-doctag"></summary></span></span>
     <span class="hljs-keyword">private</span>  <span class="hljs-built_in">float</span> m_CurTime;
    
     <span class="hljs-comment"><span class="hljs-doctag">///</span> <span class="hljs-doctag"><summary></span></span>
     <span class="hljs-comment"><span class="hljs-doctag">///</span> 当前是否是预览播放状态</span>
     <span class="hljs-comment"><span class="hljs-doctag">///</span> <span class="hljs-doctag"></summary></span></span>
     <span class="hljs-keyword">private</span>  <span class="hljs-built_in">bool</span> m_Playing;

     <span class="hljs-comment"><span class="hljs-doctag">///</span> <span class="hljs-doctag"><summary></span></span>
     <span class="hljs-comment"><span class="hljs-doctag">///</span> 当前运行时间</span>
     <span class="hljs-comment"><span class="hljs-doctag">///</span> <span class="hljs-doctag"></summary></span></span>
     <span class="hljs-keyword">private</span>  <span class="hljs-built_in">float</span> m_RunningTime;
    
     <span class="hljs-comment"><span class="hljs-doctag">///</span> <span class="hljs-doctag"><summary></span></span>
     <span class="hljs-comment"><span class="hljs-doctag">///</span> 上一次系统时间</span>
     <span class="hljs-comment"><span class="hljs-doctag">///</span> <span class="hljs-doctag"></summary></span></span>
     <span class="hljs-keyword">private</span>  <span class="hljs-built_in">double</span> m_PreviousTime;

     <span class="hljs-comment"><span class="hljs-doctag">///</span> <span class="hljs-doctag"><summary></span></span>
     <span class="hljs-comment"><span class="hljs-doctag">///</span> 滑动杆总长度</span>
     <span class="hljs-comment"><span class="hljs-doctag">///</span> <span class="hljs-doctag"></summary></span></span>
     <span class="hljs-keyword">private</span>  <span class="hljs-keyword">const</span>  <span class="hljs-built_in">float</span> kDuration = <span class="hljs-number">30f</span>;

     <span class="hljs-keyword">private</span> ParticleSystem m_ParticleSystem;

     <span class="hljs-keyword">private</span> EditParticleSystem editAnimator &#123; <span class="hljs-keyword">get</span> &#123;  <span class="hljs-keyword">return</span> target  <span class="hljs-keyword">as</span> EditParticleSystem; &#125; &#125;

     <span class="hljs-keyword">private</span> ParticleSystem particleSystem
    &#123;
        <span class="hljs-keyword">get</span> &#123;  <span class="hljs-keyword">return</span> m_ParticleSystem ?? (m_ParticleSystem = editAnimator.GetComponentInChildren<ParticleSystem>()); &#125;
    &#125;

     <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">OnEnable</span>(<span class="hljs-params"></span>)</span>
    &#123;
        m_PreviousTime = EditorApplication.timeSinceStartup;
        EditorApplication.update += inspectorUpdate;
    &#125;

     <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">OnDisable</span>(<span class="hljs-params"></span>)</span>
    &#123;
        EditorApplication.update -= inspectorUpdate;
    &#125;

     <span class="hljs-function"><span class="hljs-keyword">public</span>  <span class="hljs-keyword">override</span>  <span class="hljs-keyword">void</span> <span class="hljs-title">OnInspectorGUI</span>(<span class="hljs-params"></span>)</span>
    &#123;
        EditorGUILayout.BeginHorizontal();
         <span class="hljs-keyword">if</span> (GUILayout.Button( <span class="hljs-string">"Play"</span>))
        &#123;
            play();
        &#125;
         <span class="hljs-keyword">if</span> (GUILayout.Button( <span class="hljs-string">"Stop"</span>))
        &#123;
            stop();
        &#125;
        EditorGUILayout.EndHorizontal();
        m_CurTime = EditorGUILayout.Slider( <span class="hljs-string">"Time:"</span>, m_CurTime, <span class="hljs-number">0f</span>, kDuration);
        manualUpdate();
    &#125;

     <span class="hljs-comment"><span class="hljs-doctag">///</span> <span class="hljs-doctag"><summary></span></span>
     <span class="hljs-comment"><span class="hljs-doctag">///</span> 进行预览播放</span>
     <span class="hljs-comment"><span class="hljs-doctag">///</span> <span class="hljs-doctag"></summary></span></span>
     <span class="hljs-function"><span class="hljs-keyword">private</span>  <span class="hljs-keyword">void</span> <span class="hljs-title">play</span>(<span class="hljs-params"></span>)</span>
    &#123;
         <span class="hljs-keyword">if</span> (Application.isPlaying || particleSystem ==  <span class="hljs-literal">null</span>)
        &#123;
             <span class="hljs-keyword">return</span>;
        &#125;

        m_RunningTime = <span class="hljs-number">0f</span>;
        m_Playing =  <span class="hljs-literal">true</span>;
    &#125;

     <span class="hljs-comment"><span class="hljs-doctag">///</span> <span class="hljs-doctag"><summary></span></span>
     <span class="hljs-comment"><span class="hljs-doctag">///</span> 停止预览播放</span>
     <span class="hljs-comment"><span class="hljs-doctag">///</span> <span class="hljs-doctag"></summary></span></span>
     <span class="hljs-function"><span class="hljs-keyword">private</span>  <span class="hljs-keyword">void</span> <span class="hljs-title">stop</span>(<span class="hljs-params"></span>)</span>
    &#123;
         <span class="hljs-keyword">if</span> (Application.isPlaying || particleSystem ==  <span class="hljs-literal">null</span>)
        &#123;
             <span class="hljs-keyword">return</span>;
        &#125;

        m_Playing =  <span class="hljs-literal">false</span>;
        m_CurTime = <span class="hljs-number">0f</span>;
    &#125;

     <span class="hljs-comment"><span class="hljs-doctag">///</span> <span class="hljs-doctag"><summary></span></span>
     <span class="hljs-comment"><span class="hljs-doctag">///</span> 预览播放状态下的更新</span>
     <span class="hljs-comment"><span class="hljs-doctag">///</span> <span class="hljs-doctag"></summary></span></span>
     <span class="hljs-function"><span class="hljs-keyword">private</span>  <span class="hljs-keyword">void</span> <span class="hljs-title">update</span>(<span class="hljs-params"></span>)</span>
    &#123;
         <span class="hljs-keyword">if</span> (Application.isPlaying || particleSystem ==  <span class="hljs-literal">null</span>)
        &#123;
             <span class="hljs-keyword">return</span>;
        &#125;

         <span class="hljs-keyword">if</span> (m_RunningTime >= kDuration)
        &#123;
            m_Playing =  <span class="hljs-literal">false</span>;
             <span class="hljs-keyword">return</span>;
        &#125;

        particleSystem.Simulate(m_RunningTime,  <span class="hljs-literal">true</span>);
        SceneView.RepaintAll();
        Repaint();

        m_CurTime = m_RunningTime;
    &#125;

     <span class="hljs-comment"><span class="hljs-doctag">///</span> <span class="hljs-doctag"><summary></span></span>
     <span class="hljs-comment"><span class="hljs-doctag">///</span> 非预览播放状态下，通过滑杆来播放当前动画帧</span>
     <span class="hljs-comment"><span class="hljs-doctag">///</span> <span class="hljs-doctag"></summary></span></span>
     <span class="hljs-function"><span class="hljs-keyword">private</span>  <span class="hljs-keyword">void</span> <span class="hljs-title">manualUpdate</span>(<span class="hljs-params"></span>)</span>
    &#123;
         <span class="hljs-keyword">if</span> (particleSystem && !m_Playing)
        &#123;
            particleSystem.Simulate(m_CurTime,  <span class="hljs-literal">true</span>);
            SceneView.RepaintAll();
        &#125;
    &#125;

     <span class="hljs-function"><span class="hljs-keyword">private</span>  <span class="hljs-keyword">void</span> <span class="hljs-title">inspectorUpdate</span>(<span class="hljs-params"></span>)</span>
    &#123;
        <span class="hljs-keyword">var</span> delta = EditorApplication.timeSinceStartup - m_PreviousTime;
        m_PreviousTime = EditorApplication.timeSinceStartup;

         <span class="hljs-keyword">if</span> (!Application.isPlaying && m_Playing)
        &#123;
            m_RunningTime = Mathf.Clamp(m_RunningTime + ( <span class="hljs-built_in">float</span>)delta, <span class="hljs-number">0f</span>, kDuration);
            update();
        &#125;
    &#125;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>检视器效果如下：</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/22ad671706204c91907ce75e77b27af1~tplv-k3u1fbpfcp-zoom-1.image" alt loading="lazy" referrerpolicy="no-referrer">\</p>
<p>拖动滑杆，即可播放当前时间的那一帧，如下所示：\</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a76a26cc26044a1293c412a6bce5ebe7~tplv-k3u1fbpfcp-zoom-1.image" alt loading="lazy" referrerpolicy="no-referrer">\</p>
<p>点击" <strong>Play</strong>"，即可以自动播放整个粒子，如下所示：</p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0e5ee8bb02d847bf9e22280390e8a876~tplv-k3u1fbpfcp-zoom-1.image" alt loading="lazy" referrerpolicy="no-referrer"></p></div>  
</div>
            
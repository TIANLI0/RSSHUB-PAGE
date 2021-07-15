
---
title: 'ThreeJS Example webgl_depth_texture 深度贴图'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/851cabdf1b324368bf95a63b3bcb773d~tplv-k3u1fbpfcp-watermark.image'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 09:11:34 GMT
thumbnail: 'https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/851cabdf1b324368bf95a63b3bcb773d~tplv-k3u1fbpfcp-watermark.image'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><p><a href="https://link.juejin.cn/?target=https%3A%2F%2Fthreejs.org%2Fexamples%2F%23webgl_depth_texture" target="_blank" rel="nofollow noopener noreferrer" title="https://threejs.org/examples/#webgl_depth_texture" ref="nofollow noopener noreferrer">threejs.org/examples/#w…</a></p>
<p><img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/851cabdf1b324368bf95a63b3bcb773d~tplv-k3u1fbpfcp-watermark.image" alt="image.png" loading="lazy" referrerpolicy="no-referrer"></p>
<ul>
<li>RenderTarget的texture会放在这个面板上</li>
</ul>
<pre><code class="hljs language-glsl copyable" lang="glsl"><span class="hljs-keyword">varying</span> <span class="hljs-type">vec2</span> vUv;

<span class="hljs-type">void</span> main() &#123;
        vUv = uv;
        <span class="hljs-built_in">gl_Position</span> = projectionMatrix * modelViewMatrix * <span class="hljs-type">vec4</span>(position, <span class="hljs-number">1.0</span>);
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-glsl copyable" lang="glsl"><span class="hljs-meta">#include <packing></span>

<span class="hljs-keyword">varying</span> <span class="hljs-type">vec2</span> vUv;
<span class="hljs-keyword">uniform</span> <span class="hljs-type">sampler2D</span> tDiffuse;
<span class="hljs-keyword">uniform</span> <span class="hljs-type">sampler2D</span> tDepth; <span class="hljs-comment">//深度图</span>
<span class="hljs-keyword">uniform</span> <span class="hljs-type">float</span> cameraNear;
<span class="hljs-keyword">uniform</span> <span class="hljs-type">float</span> cameraFar;


<span class="hljs-type">float</span> readDepth( <span class="hljs-type">sampler2D</span> depthSampler, <span class="hljs-type">vec2</span> coord ) &#123;
        <span class="hljs-type">float</span> fragCoordZ = <span class="hljs-built_in">texture2D</span>( depthSampler, coord ).x;
        <span class="hljs-type">float</span> viewZ = perspectiveDepthToViewZ( fragCoordZ, cameraNear, cameraFar ); <span class="hljs-comment">//near和far 还原真实的深度值</span>
        <span class="hljs-keyword">return</span> viewZToOrthographicDepth( viewZ, cameraNear, cameraFar ); <span class="hljs-comment">//真实的深度值转0-1</span>
        
&#125;
<span class="hljs-type">float</span> perspectiveDepthToViewZ(<span class="hljs-keyword">const</span> <span class="hljs-keyword">in</span> <span class="hljs-type">float</span> invClipZ, <span class="hljs-keyword">const</span> <span class="hljs-keyword">in</span> <span class="hljs-type">float</span> near, <span class="hljs-keyword">const</span> <span class="hljs-keyword">in</span> <span class="hljs-type">float</span> far) &#123;
    <span class="hljs-keyword">return</span> (near * far) / ((far - near) * invClipZ - far);
&#125;
<span class="hljs-type">float</span> viewZToOrthographicDepth(<span class="hljs-keyword">const</span> <span class="hljs-keyword">in</span> <span class="hljs-type">float</span> viewZ, <span class="hljs-keyword">const</span> <span class="hljs-keyword">in</span> <span class="hljs-type">float</span> near, <span class="hljs-keyword">const</span> <span class="hljs-keyword">in</span> <span class="hljs-type">float</span> far) &#123;
    <span class="hljs-keyword">return</span> (viewZ + near) / (near - far); <span class="hljs-comment">//</span>
&#125;

<span class="hljs-type">void</span> main() &#123;
        <span class="hljs-comment">//vec3 diffuse = texture2D( tDiffuse, vUv ).rgb;</span>
        <span class="hljs-type">float</span> depth = readDepth( tDepth, vUv );

        <span class="hljs-built_in">gl_FragColor</span>.rgb = <span class="hljs-number">1.0</span> - <span class="hljs-type">vec3</span>( depth );
        <span class="hljs-built_in">gl_FragColor</span>.a = <span class="hljs-number">1.0</span>;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">setupPost</span>(<span class="hljs-params"></span>) </span>&#123;
        <span class="hljs-comment">// Setup post processing stage</span>
        postCamera = <span class="hljs-keyword">new</span> THREE.OrthographicCamera( - <span class="hljs-number">1</span>, <span class="hljs-number">1</span>, <span class="hljs-number">1</span>, - <span class="hljs-number">1</span>, <span class="hljs-number">0</span>, <span class="hljs-number">1</span> );
        postMaterial = <span class="hljs-keyword">new</span> THREE.ShaderMaterial( &#123;
                <span class="hljs-attr">vertexShader</span>: <span class="hljs-built_in">document</span>.querySelector( <span class="hljs-string">'#post-vert'</span> ).textContent.trim(),
                <span class="hljs-attr">fragmentShader</span>: <span class="hljs-built_in">document</span>.querySelector( <span class="hljs-string">'#post-frag'</span> ).textContent.trim(),
                <span class="hljs-attr">uniforms</span>: &#123;
                        <span class="hljs-attr">cameraNear</span>: &#123; <span class="hljs-attr">value</span>: camera.near &#125;,
                        <span class="hljs-attr">cameraFar</span>: &#123; <span class="hljs-attr">value</span>: camera.far &#125;,
                        <span class="hljs-attr">tDiffuse</span>: &#123; <span class="hljs-attr">value</span>: <span class="hljs-literal">null</span> &#125;,
                        <span class="hljs-attr">tDepth</span>: &#123; <span class="hljs-attr">value</span>: <span class="hljs-literal">null</span> &#125;
                &#125;
        &#125; );
        <span class="hljs-keyword">const</span> postPlane = <span class="hljs-keyword">new</span> THREE.PlaneGeometry( <span class="hljs-number">2</span>, <span class="hljs-number">2</span> );
        <span class="hljs-keyword">const</span> postQuad = <span class="hljs-keyword">new</span> THREE.Mesh( postPlane, postMaterial );
        postScene = <span class="hljs-keyword">new</span> THREE.Scene();
        postScene.add( postQuad );
&#125;

<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>format和type的类型</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js"><span class="hljs-keyword">const</span> formats = &#123; <span class="hljs-attr">DepthFormat</span>: THREE.DepthFormat, <span class="hljs-attr">DepthStencilFormat</span>: THREE.DepthStencilFormat &#125;;
<span class="hljs-keyword">const</span> types = &#123; <span class="hljs-attr">UnsignedShortType</span>: THREE.UnsignedShortType, <span class="hljs-attr">UnsignedIntType</span>: THREE.UnsignedIntType, <span class="hljs-attr">UnsignedInt248Type</span>: THREE.UnsignedInt248Type &#125;;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>生成WebGLRenderTarget</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js">scene = <span class="hljs-keyword">new</span> THREE.Scene();
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">setupRenderTarget</span>(<span class="hljs-params"></span>) </span>&#123;
        <span class="hljs-keyword">if</span> ( target ) target.dispose();

        <span class="hljs-keyword">const</span> format = <span class="hljs-built_in">parseFloat</span>( params.format );
        <span class="hljs-keyword">const</span> type = <span class="hljs-built_in">parseFloat</span>( params.type );

        target = <span class="hljs-keyword">new</span> THREE.WebGLRenderTarget( <span class="hljs-built_in">window</span>.innerWidth, <span class="hljs-built_in">window</span>.innerHeight );
        target.texture.format = THREE.RGBFormat;
        target.texture.minFilter = THREE.NearestFilter;
        target.texture.magFilter = THREE.NearestFilter;
        target.texture.generateMipmaps = <span class="hljs-literal">false</span>;
        
        target.stencilBuffer = ( format === THREE.DepthStencilFormat ) ? <span class="hljs-literal">true</span> : <span class="hljs-literal">false</span>;
        target.depthBuffer = <span class="hljs-literal">true</span>;
        target.depthTexture = <span class="hljs-keyword">new</span> THREE.DepthTexture();
        target.depthTexture.format = format;
        target.depthTexture.type = type;
&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<ul>
<li>render</li>
</ul>
<pre><code class="hljs language-js copyable" lang="js">renderer.setRenderTarget( target );
renderer.render( scene, camera );

<span class="hljs-comment">// render post FX</span>
postMaterial.uniforms.tDiffuse.value = target.texture;
postMaterial.uniforms.tDepth.value = target.depthTexture;

renderer.setRenderTarget( <span class="hljs-literal">null</span> );
renderer.render( postScene, postCamera );
<span class="copy-code-btn">复制代码</span></code></pre></div>  
</div>
            
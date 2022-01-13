
---
title: 'vue中使用节流函数踩坑记录'
categories: 
 - 社交媒体
 - 简书
 - 首页
headimg: 'https://upload-images.jianshu.io/upload_images/5703029-4823912f4fa7b8ba.jpg'
author: 简书
comments: false
date: Invalid Date
thumbnail: 'https://upload-images.jianshu.io/upload_images/5703029-4823912f4fa7b8ba.jpg'
---

<div>   
<h3>前言</h3>
<p>一个常见的业务场景，我们要在input搜索框输入结束后，发送相关请求，获取搜索数据。频繁的事件触发会导致接口请求过于频繁。所以需要我们对此加以限制，来禁止不必要的请求，以免资源的浪费~</p>
<h4>举一个🌰   业务场景</h4>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="365" data-height="375"><img data-original-src="//upload-images.jianshu.io/upload_images/5703029-4823912f4fa7b8ba.jpg" data-original-width="365" data-original-height="375" data-original-format="image/jpeg" data-original-filesize="17528" src="https://upload-images.jianshu.io/upload_images/5703029-4823912f4fa7b8ba.jpg" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">image</div>
</div>
<h3>概念：</h3>
<p><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmajunchang.github.io%2Ffe-improve-deploy%2Fmoveforward%2Fjs%2F%25E9%2598%25B2%25E6%258A%2596%25E5%2592%258C%25E8%258A%2582%25E6%25B5%2581.html%23%25E4%25BB%2580%25E4%25B9%2588%25E6%2598%25AF%25E9%2598%25B2%25E6%258A%2596%25E5%2592%258C%25E8%258A%2582%25E6%25B5%2581%25EF%25BC%259F" target="_blank">关于防抖函数的介绍</a></p>
<p><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2Fdocs%2FWeb%2FAPI%2FEventTarget%2FaddEventListener" target="_blank">关于addEventListener</a></p>
<p>使用示例：</p>
<pre><code class="js">    function debounce(fn) &#123;
        let timeout = null; // 创建一个标记用来存放定时器的返回值
        return function () &#123;
            clearTimeout(timeout); // 每当用户输入的时候把前一个 setTimeout clear 掉
            timeout = setTimeout(() => &#123;
                // 然后又创建一个新的 setTimeout, 这样就能保证输入字符后的
                // interval 间隔内如果还有字符输入的话，就不会执行 fn 函数
                fn.apply(this, arguments);
            &#125;, 500);
        &#125;;
    &#125;
    function sayHi() &#123;
        console.log('防抖成功');
    &#125;

    var inp = document.getElementById('inp');
    inp.addEventListener('input', debounce(sayHi)); // 防抖
</code></pre>
<h4>在vue中使用？</h4>
<blockquote>
<p>首先说一下之前的踩坑行为</p>
</blockquote>
<p>下面的代码为简易版的一个场景</p>
<pre><code class="js">function debounce(fn) &#123;
        let timeout = null; // 创建一个标记用来存放定时器的返回值
        return function () &#123;
            clearTimeout(timeout); // 每当用户输入的时候把前一个 setTimeout clear 掉
            timeout = setTimeout(() => &#123;
                // 然后又创建一个新的 setTimeout, 这样就能保证输入字符后的
                // interval 间隔内如果还有字符输入的话，就不会执行 fn 函数
                fn.apply(this, arguments);
            &#125;, 500);
        &#125;;
   &#125;
</code></pre>
<h3>错误的使用方式</h3>
<pre><code class="js"><template>
    <div class="search-view">
        <div class="header">
            <Search 
                class="search-box" 
                v-model='searchValue' 
                @input='getSearchResult' 
                placeholder='搜索想要的好物' />
            <span @click="goBack" class="cancel">取消</span>
        </div>
        <div class="serach-view-content" />
    </div>

</template>

<script>
import Search from './components/Search';
import debounce from './config';

export default &#123;
    name: 'SearchView',
    components: &#123;
        Search
    &#125;,
    data() &#123;
        return &#123;
            searchValue: ''
        &#125;;
    &#125;,
    methods: &#123;
        getSearchResult() &#123;
            debounce(function() &#123;
                console.log(this.searchValue);
            &#125;)();
        &#125;
    &#125;
&#125;;
</script>
</code></pre>
<h3>为什么错误？</h3>
<h5>源码层级分析</h5>
<h5>vue模板编译 的解析事件</h5>
<pre><code class="js">export const onRE = /^@|^v-on:/
export const dirRE = /^v-|^@|^:/

function processAttrs (el) &#123;
  const list = el.attrsList
  let i, l, name, value, modifiers
  for (i = 0, l = list.length; i < l; i++) &#123;
    name  = list[i].name
    value = list[i].value
    if (dirRE.test(name)) &#123;
      // 解析修饰符
      modifiers = parseModifiers(name)
      if (modifiers) &#123;
        name = name.replace(modifierRE, '')
      &#125;
      if (onRE.test(name)) &#123; // v-on
        name = name.replace(onRE, '')
        addHandler(el, name, value, modifiers, false, warn)
      &#125;
    &#125;
  &#125;
&#125;
</code></pre>
<p><strong>总结</strong>: 实例初始化阶段调用的初始化事件函数<code>initEvents</code>实际上初始化的是父组件在模板中使用v-on或@注册的监听子组件内触发的事件</p>
<h5>vue的事件机制</h5>
<pre><code class="js">Vue.prototype.$on = function(event, fn) &#123;
    const vm = this;
    if (Array.isArray(event)) &#123;
        for (let i = 0; i < event.length; i++) &#123;
            this.$on(event[i], fn);
        &#125;
    &#125; else &#123;
        //这个_events属性就是用来作为当前实例的事件中心，所有绑定在这个实例上的事件都会存储在事件中心_events属性中。
        (vm._events[event] || (vm._events[event] = [])).push(fn);
    &#125;
    return vm;
&#125;;

Vue.prototype.$emit = function(event) &#123;
    const vm = this;
    let cbs = vm._events[event];
    if (cbs) &#123;
        cbs = cbs.length > 1 ? toArray(cbs) : cbs;
        let args = toArray(arguments, 1);
        for (let i = 0; i < cbs.length; i++) &#123;
            try &#123;
                cbs[i].apply(vm, args);
            &#125; catch (e) &#123;
                handleError(e, vm, `event handler for "$&#123;event&#125;"`);
            &#125;
        &#125;
    &#125;
    return vm;
&#125;;
</code></pre>
<p><strong>vue的initState中 调用了initMethods方法</strong></p>
<h5>initMethods中挂在methods方法到this上</h5>
<pre><code class="js">for (const key in methods) &#123;
        if (process.env.NODE_ENV !== 'production') &#123;
            if (methods[key] == null) &#123;
                warn(
                    `Method "$&#123;key&#125;" has an undefined value in the component definition. ` +
                        `Did you reference the function correctly?`,
                    vm
                );
            &#125;
            // 如果和props中某个属性名重名了 抛出异常
            if (props && hasOwn(props, key)) &#123;
                warn(`Method "$&#123;key&#125;" has already been defined as a prop.`, vm);
            &#125;
            /*
            如果methods中某个方法名如果在实例vm中已经存在并且方法名是以_或$开头的，就抛出异常：
            提示用户方法名命名不规范
            */
            if (key in vm && isReserved(key)) &#123;
                warn(
                    `Method "$&#123;key&#125;" conflicts with an existing Vue instance method. ` +
                        `Avoid defining component methods that start with _ or $.`
                );
            &#125;
            // 将method绑定到实例 vm上  这样我们就可以通过this.xxx 来访问了
            // 同时如果在vue中  let m1 = this.xxx  m1() this也指向vue
            vm[key] = methods[key] == null ? noop : bind(methods[key], vm);
        &#125;

</code></pre>
<h4>划重点：</h4>
<ul>
<li>子组件$emit('input事件')</li>
<li>父组件接收事件</li>
</ul>
<pre><code class="js">getSearchResult.apply(this, agrs)
<===>  apply的调用可以写成下面的形式
this.getSearchResult(args)

// 进而变成这种执行
debounce(function() &#123;
      console.log(this.searchValue);
&#125;)();

// 这里的debounce 返回了一个函数 于是变成
(function (fn) &#123;
      clearTimeout(timeout); // 每当用户输入的时候把前一个 setTimeout clear 掉
      timeout = setTimeout(() => &#123;
          // 然后又创建一个新的 setTimeout, 这样就能保证输入字符后的
          // interval 间隔内如果还有字符输入的话，就不会执行 fn 函数
          fn.apply(this, arguments);
      &#125;, 500);
&#125;)()
// 到这里  其实就变成了匿名函数的自执行
// 由于每次触发input都会返回一个新的匿名函数  生成一个新的函数执行栈  所以防抖失效~

</code></pre>
<h5>那么应该如何调用</h5>
<pre><code class="js"><template>
    <div class="search-view">
        <div class="header">
            <Search
                class="search-box"
                v-model='searchValue'
                @input='getSearchResult()'
                placeholder='搜索想要的好物'
            />
            <span
                @click="goBack"
                class="cancel">取消</span>
        </div>
        <div class="serach-view-content">
            
        </div>
    </div>

</template>

<script>
import debounce from 'lodash.debounce';
export default &#123;
    name: 'SearchView',
    components: &#123;
        Search,
    &#125;,
    data() &#123;
        return &#123;
            searchValue: '',
        &#125;;
    &#125;,
    methods: &#123;
        getSearchResult: debounce(function () &#123;
            console.log(this.searchValue);
        &#125;, 500),
    &#125;,

&#125;;
</script>

</code></pre>
<h5>分析执行过程</h5>
<pre><code class="js">getSearchResult().apply(this, args)
<===> 忽略参数行为 只关注执行栈

let func = function () &#123;
    clearTimeout(timeout); // 每当用户输入的时候把前一个 setTimeout clear 掉
    timeout = setTimeout(() => &#123;
        // 然后又创建一个新的 setTimeout, 这样就能保证输入字符后的
        // interval 间隔内如果还有字符输入的话，就不会执行 fn 函数
        fn.apply(this, arguments);
    &#125;, 500);
&#125;;

this.func(args)

<===>
子组件触发input的行为  返回的始终是一个同一个函数体  防抖成功 
类比于文章开始时介绍的addEventListener


</code></pre>
  
</div>
            
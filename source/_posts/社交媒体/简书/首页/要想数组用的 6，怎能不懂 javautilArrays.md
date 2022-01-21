
---
title: '要想数组用的 6，怎能不懂 java.util.Arrays'
categories: 
 - 社交媒体
 - 简书
 - 首页
headimg: 'https://picsum.photos/400/300?random=7389'
author: 简书
comments: false
date: Invalid Date
thumbnail: 'https://picsum.photos/400/300?random=7389'
---

<div>   
<p><code>java.util.Arrays</code> 类就是为数组而生的专用工具类，基本上常见的对数组的操作，Arrays 类都考虑到了，这让我由衷地觉得，是时候给该类的作者 Josh Bloch、Neal Gafter、John Rose 点个赞了。</p>
<p>（我是怎么知道作者名的？看源码就可以，小伙伴们，装逼吧）</p>
<p>Arrays 都可以干嘛呢？常见的有：</p>
<ul>
<li>创建数组</li>
<li>比较数组</li>
<li>数组排序</li>
<li>数组检索</li>
<li>数组转流</li>
<li>打印数组</li>
<li>数组转 List</li>
<li>setAll（没想好中文名）</li>
<li>parallelPrefix（没想好中文名）</li>
</ul>
<p>那接下来，小伙伴们是不是已经迫不及待想要和二哥一起来打怪进阶了。走你。</p>
<h3>01、创建数组</h3>
<p>使用 Arrays 类创建数组可以通过以下三个方法：</p>
<ul>
<li>copyOf，复制指定的数组，截取或用 null 填充</li>
<li>copyOfRange，复制指定范围内的数组到一个新的数组</li>
<li>fill，对数组进行填充</li>
</ul>
<p>1）copyOf，直接来看例子：</p>
<pre><code class="java">String[] intro = new String[] &#123; "沉", "默", "王", "二" &#125;;
String[] revised = Arrays.copyOf(intro, 3);
String[] expanded = Arrays.copyOf(intro, 5);
System.out.println(Arrays.toString(revised));
System.out.println(Arrays.toString(expanded));
</code></pre>
<p>revised 和 expanded 是复制后的新数组，长度分别是 3 和 5，指定的数组长度是 4。来看一下输出结果：</p>
<pre><code>[沉, 默, 王]
[沉, 默, 王, 二, null]
</code></pre>
<p>看到没？revised 截取了最后一位，因为长度是 3 嘛；expanded 用 null 填充了一位，因为长度是 5。</p>
<p>2）copyOfRange，直接来看例子：</p>
<pre><code class="java">String[] intro = new String[] &#123; "沉", "默", "王", "二" &#125;;
String[] abridgement = Arrays.copyOfRange(intro, 0, 3);
System.out.println(Arrays.toString(abridgement));
</code></pre>
<p><code>copyOfRange()</code> 方法需要三个参数，第一个是指定的数组，第二个是起始位置（包含），第三个是截止位置（不包含）。来看一下输出结果：</p>
<pre><code class="java">[沉, 默, 王]
</code></pre>
<p>0 的位置是“沉”，3 的位置是“二”，也就是说截取了从 0 位（包含）到 3 位（不包含）的数组元素。那假如说下标超出了数组的长度，会发生什么呢？</p>
<pre><code class="java">String[] abridgementExpanded = Arrays.copyOfRange(intro, 0, 6);
System.out.println(Arrays.toString(abridgementExpanded));
</code></pre>
<p>结束位置此时为 6，超出了指定数组的长度 4，来看一下输出结果：</p>
<pre><code>[沉, 默, 王, 二, null, null]
</code></pre>
<p>仍然使用了 null 进行填充。为什么要这么做呢？小伙伴们思考一下，我想是作者考虑到了数组越界的问题，不然每次调用 Arrays 类就要先判断很多次长度，很麻烦。</p>
<p>3）fill，直接来看例子：</p>
<pre><code class="java">String[] stutter = new String[4];
Arrays.fill(stutter, "沉默王二");
System.out.println(Arrays.toString(stutter));
</code></pre>
<p>使用 new 关键字创建了一个长度为 4 的数组，然后使用 <code>fill()</code> 方法将 4 个位置填充为“沉默王二”，来看一下输出结果：</p>
<pre><code>[沉默王二, 沉默王二, 沉默王二, 沉默王二]
</code></pre>
<p>如果想要一个元素完全相同的数组时， <code>fill()</code> 方法就派上用场了。</p>
<h3>02、比较数组</h3>
<p>Arrays 类的 <code>equals()</code> 方法用来判断两个数组是否相等，来看下面这个例子：</p>
<pre><code class="java">String[] intro = new String[] &#123; "沉", "默", "王", "二" &#125;;
boolean result = Arrays.equals(new String[] &#123; "沉", "默", "王", "二" &#125;, intro);
System.out.println(result);
boolean result1 = Arrays.equals(new String[] &#123; "沉", "默", "王", "三" &#125;, intro);
System.out.println(result1);
</code></pre>
<p>输出结果如下所示：</p>
<pre><code>true
false
</code></pre>
<p>指定的数组为沉默王二四个字，比较的数组一个是沉默王二，一个是沉默王三，所以 result 为 true，result1 为 false。</p>
<p>简单看一下 <code>equals()</code> 方法的源码：</p>
<pre><code class="java">public static boolean equals(Object[] a, Object[] a2) &#123;
    if (a==a2)
        return true;
    if (a==null || a2==null)
        return false;

    int length = a.length;
    if (a2.length != length)
        return false;

    for (int i=0; i<length; i++) &#123;
        if (!Objects.equals(a[i], a2[i]))
            return false;
    &#125;

    return true;
&#125;
</code></pre>
<p>因为数组是一个对象，所以先使用“==”操作符进行判断，如果不相等，再判断是否为 null，两个都为 null，返回 false；紧接着判断 length，不等的话，返回 false；否则的话，依次调用 <code>Objects.equals()</code> 比较相同位置上的元素是否相等。</p>
<p>感觉非常严谨，这也就是学习源码的意义，鉴赏的同时，学习。</p>
<p>除了 <code>equals()</code> 方法，还有另外一个诀窍可以判断两个数组是否相等，尽管可能会出现误差（概率非常小）。那就是 <code>Arrays.hashCode()</code> 方法，先来看一下该方法的源码：</p>
<pre><code class="java">public static int hashCode(Object a[]) &#123;
    if (a == null)
        return 0;

    int result = 1;

    for (Object element : a)
        result = 31 * result + (element == null ? 0 : element.hashCode());

    return result;
&#125;
</code></pre>
<p>哈希算法本身是非常严谨的，所以如果两个数组的哈希值相等，那几乎可以判断两个数组是相等的。</p>
<pre><code class="java">String[] intro = new String[] &#123; "沉", "默", "王", "二" &#125;;

System.out.println(Arrays.hashCode(intro));
System.out.println(Arrays.hashCode(new String[] &#123; "沉", "默", "王", "二" &#125;));
</code></pre>
<p>来看一下输出结果：</p>
<pre><code>868681617
868681617
</code></pre>
<p>两个数组的哈希值相等，毕竟元素是一样的。但这样确实不够严谨，优先使用 <code>Objects.equals()</code> 方法。</p>
<h3>03、数组排序</h3>
<p>Arrays 类的 <code>sort()</code> 方法用来判断两个数组是否相等，来看下面这个例子：</p>
<pre><code class="java">String[] intro1 = new String[] &#123; "chen", "mo", "wang", "er" &#125;;
String[] sorted = Arrays.copyOf(intro1, 4);
Arrays.sort(sorted);
System.out.println(Arrays.toString(sorted));
</code></pre>
<p>由于排序会改变原有的数组，所以我们使用了 <code>copyOf()</code> 方法重新复制了一份。来看一下输出结果：</p>
<pre><code>[chen, er, mo, wang]
</code></pre>
<p>可以看得出，按照的是首字母的升序进行排列的。基本数据类型是按照双轴快速排序的，引用数据类型是按照 TimSort 排序的，使用了 Peter McIlroy 的“乐观排序和信息理论复杂性”中的技术。</p>
<h3>04、数组检索</h3>
<p>数组排序后就可以使用 Arrays 类的 <code>binarySearch()</code> 方法进行二分查找了。否则的话，只能线性检索，效率就会低很多。</p>
<pre><code class="java">String[] intro1 = new String[] &#123; "chen", "mo", "wang", "er" &#125;;
String[] sorted = Arrays.copyOf(intro1, 4);
Arrays.sort(sorted);
int exact = Arrays.binarySearch(sorted, "wang");
System.out.println(exact);
int caseInsensitive = Arrays.binarySearch(sorted, "Wang", String::compareToIgnoreCase);
System.out.println(caseInsensitive);
</code></pre>
<p><code>binarySearch()</code> 方法既可以精确检索，也可以模糊检索，比如说忽略大小写。来看一下输出结果：</p>
<pre><code>3
3
</code></pre>
<p>排序后的结果是 <code>[chen, er, mo, wang]</code>，所以检索出来的下标是 3。</p>
<h3>05、数组转流</h3>
<p>Stream 流非常强大，需要入门的小伙伴可以查看我之前写的一篇文章：</p>
<p><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmp.weixin.qq.com%2Fs%2F7hNUjjmqKcHDtymsfG_Gtw" target="_blank">一文带你入门Java Stream流，太强了</a></p>
<p>Arrays 类的 <code>stream()</code> 方法可以将数组转换成流：</p>
<pre><code class="java">String[] intro = new String[] &#123; "沉", "默", "王", "二" &#125;;
System.out.println(Arrays.stream(intro).count());
</code></pre>
<p>还可以为 <code>stream()</code> 方法指定起始下标和结束下标：</p>
<pre><code class="java">System.out.println(Arrays.stream(intro, 1, 2).count());
</code></pre>
<p>如果下标的范围有误的时候，比如说从 2 到 1 结束，则程序会抛出 ArrayIndexOutOfBoundsException 异常：</p>
<pre><code>Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: origin(2) > fence(1)
    at java.base/java.util.Spliterators.checkFromToBounds(Spliterators.java:387)
</code></pre>
<h3>06、打印数组</h3>
<p>关于数组的打印方式，我之前单独写过一篇文章：</p>
<p><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmp.weixin.qq.com%2Fs%2FudUi8ee8lA412aqpqFBcmw" target="_blank">打印Java数组最优雅的方式是什么？</a></p>
<p>里面谈了很多种数组打印的方式，因为数组是一个对象，直接 <code>System.out.println</code> 的话，结果是这样的：</p>
<pre><code>[Ljava.lang.String;@3d075dc0
</code></pre>
<p>那最优雅的方式，其实文章里面已经出现过很多次了，就是 <code>Arrays.toString()</code>：</p>
<pre><code class="java">public static String toString(Object[] a) &#123;
    if (a == null)
        return "null";

    int iMax = a.length - 1;
    if (iMax == -1)
        return "[]";

    StringBuilder b = new StringBuilder();
    b.append('[');
    for (int i = 0; ; i++) &#123;
        b.append(String.valueOf(a[i]));
        if (i == iMax)
            return b.append(']').toString();
        b.append(", ");
    &#125;
&#125;
</code></pre>
<p>小伙伴可以好好欣赏一下这段源码，感觉考虑得非常周到。</p>
<h3>07、数组转 List</h3>
<p>尽管数组非常强大，但它自身可以操作的工具方法很少，比如说判断数组中是否包含某个值。转成 List 的话，就简便多了。</p>
<pre><code class="java">String[] intro = new String[] &#123; "沉", "默", "王", "二" &#125;;
List<String> rets = Arrays.asList(intro);
System.out.println(rets.contains("二"));
</code></pre>
<p>不过需要注意的是，<code>Arrays.asList()</code> 返回的是 <code>java.util.Arrays.ArrayList</code>，并不是  <code>java.util.ArrayList</code>，它的长度是固定的，无法进行元素的删除或者添加。</p>
<pre><code class="java">rets.add("三");
rets.remove("二");
</code></pre>
<p>执行这两个方法的时候，会抛出异常：</p>
<pre><code>Exception in thread "main" java.lang.UnsupportedOperationException
    at java.base/java.util.AbstractList.add(AbstractList.java:153)
    at java.base/java.util.AbstractList.add(AbstractList.java:111)
</code></pre>
<p>要想操作元素的话，需要多一步转化：</p>
<pre><code class="java">List<String> rets1 = new ArrayList<>(Arrays.asList(intro));
rets1.add("三");
rets1.remove("二");
</code></pre>
<h3>08、setAll</h3>
<p>Java 8 新增了 <code>setAll()</code> 方法，它提供了一个函数式编程的入口，可以对数组的元素进行填充：</p>
<pre><code class="java">int[] array = new int[10];
Arrays.setAll(array, i -> i * 10);
System.out.println(Arrays.toString(array));
</code></pre>
<p>这段代码什么意思呢？i 就相当于是数组的下标，值从 0 开始，到 9 结束，那么 <code>i * 10</code> 就意味着 0 * 10 开始，到 9 * 10 结束，来看一下输出结果：</p>
<pre><code>[0, 10, 20, 30, 40, 50, 60, 70, 80, 90]
</code></pre>
<p>比之前的 <code>fill()</code> 方法强大多了，对吧？不再填充的是相同的元素。</p>
<h3>09、parallelPrefix</h3>
<p><code>parallelPrefix()</code> 方法和 <code>setAll()</code> 方法一样，也是 Java 8 之后提供的，提供了一个函数式编程的入口，通过遍历数组中的元素，将当前下标位置上的元素与它之前下标的元素进行操作，然后将操作后的结果覆盖当前下标位置上的元素。</p>
<pre><code class="java">int[] arr = new int[] &#123; 1, 2, 3, 4&#125;;
Arrays.parallelPrefix(arr, (left, right) -> left + right);
System.out.println(Arrays.toString(arr));
</code></pre>
<p>上面代码中有一个 Lambda 表达式（<code>(left, right) -> left + right</code>），需要入门的小伙伴可以查看我之前写的一篇文章：</p>
<p><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmp.weixin.qq.com%2Fs%2Fozr0jYHIc12WSTmmd_vEjw" target="_blank">Lambda 表达式入门，看这篇就够了</a></p>
<p>那为了让小伙伴看得更明白一些，我们把上面这段代码稍微改造一下：</p>
<pre><code class="java">int[] arr = new int[]&#123;1, 2, 3, 4&#125;;
Arrays.parallelPrefix(arr, (left, right) -> &#123;
    System.out.println(left + "，" + right);
    return left + right;
&#125;);
System.out.println(Arrays.toString(arr));
</code></pre>
<p>先来看一下输出结果：</p>
<pre><code>1，2
3，3
6，4
[1, 3, 6, 10]
</code></pre>
<p>也就是说， Lambda 表达式执行了三次：</p>
<ul>
<li>第一次是 1 和 2 相加，结果是 3，替换下标为 1 的位置</li>
<li>第二次是 3 和 3 相加，结果是 6，也就是第一次的结果和下标为 2 的元素相加的结果</li>
<li>第三次是 6 和 4 相加，结果是 10，也就是第二次的结果和下标为 3 的元素相加的结果</li>
</ul>
<p>有点强大，对吧？</p>
<h3>10、总结</h3>
<p>好了，我亲爱的小伙伴们，以上就是本文的全部内容了，能看到这里的都是最优秀的程序员，二哥必须要为你点个赞。</p>
<p>我是沉默王二，一枚有趣的程序员。如果觉得文章对你有点帮助，请微信搜索「 <strong>沉默王二</strong> 」第一时间阅读，回复【<strong>666</strong>】更有我为你精心准备的 500G 高清教学视频（已分门别类）。</p>
<blockquote>
<p>本文 <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Fqinggee%2Fitwanger.github.io" target="_blank">GitHub</a> 已经收录，有大厂面试完整考点，欢迎 Star。</p>
</blockquote>
<p><strong>原创不易，莫要白票，请你为本文点个赞吧</strong>，这将是我写作更多优质文章的最强动力。</p>
  
</div>
            
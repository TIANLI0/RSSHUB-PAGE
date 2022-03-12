
---
title: 'Numpy笔记（NumPy ndarray）'
categories: 
 - 社交媒体
 - 简书
 - 首页
headimg: 'https://upload-images.jianshu.io/upload_images/18922188-223f62da488b6e5f.png'
author: 简书
comments: false
date: Invalid Date
thumbnail: 'https://upload-images.jianshu.io/upload_images/18922188-223f62da488b6e5f.png'
---

<div>   
<p>本篇笔记是根据学习《Python for data analysis》这本英文教程里的Numpy这一部分来记录的。这本书在网上的评价还是很高的，里面讲的东西也比较细，鉴于是英文的，所以我就打算只挑部分来看，时间充裕的同学可以从头到尾的细看一遍。</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="772" data-height="1016"><img data-original-src="//upload-images.jianshu.io/upload_images/18922188-223f62da488b6e5f.png" data-original-width="772" data-original-height="1016" data-original-format="image/png" data-original-filesize="440769" src="https://upload-images.jianshu.io/upload_images/18922188-223f62da488b6e5f.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption">书的封面长这样</div>
</div>
<p>Numpy,是Numerical Python的简写，它是Python里数字计算的最重要的一个基础包。</p>
<h4>The NumPy ndarray: A Multidimensional Array Object</h4>
<p>Numpy ndarray：一个多维数组对象<br>
Numpy 的一个关键的特点是其N-维数组对象，或者叫做ndarray，它是一个快速的，灵活的大数据python“容器”。Arrays使得你可以对整个block使用简单的语法来进行数学计算。举个例子，导入Numpy并且生成一个小的随机数组：</p>
<pre><code>#首先进入ipython，具体方法请见我前一篇文章
#这里你可以使用shell，或者web界面，根据你喜好来
$ ipython
Python 3.7.6 (default, Jan  8 2020, 19:59:22)
Type 'copyright', 'credits' or 'license' for more information
IPython 7.12.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: import numpy as np #导入Numpy

In [2]: data = np.random.randn(2,3) #生成随机数组，2个数组，每个里面3个元素

In [3]: data
Out[3]:
array([[ 0.01738749, -0.05367916,  0.72654692],
       [ 1.45506185, -0.71293169,  1.35346708]])
</code></pre>
<p>对数组进行数学运算：</p>
<pre><code>In [4]: data*10
Out[4]:
array([[ 0.17387488, -0.53679156,  7.26546924],
       [14.55061854, -7.12931685, 13.53467077]])

In [5]: data+data
Out[5]:
array([[ 0.03477498, -0.10735831,  1.45309385],
       [ 2.91012371, -1.42586337,  2.70693415]])
</code></pre>
<p>ndarray是用于存放同种数据的多维“容器”，也就是说，所有的元素必须是同样的类型。每一个数组都有自己的shape，用<code>shape</code>可以查看每一个维度的大小；使用<code>dtype</code>可以查看数组内的数据类型：</p>
<pre><code>In [6]: data.shape
Out[6]: (2, 3)

In [7]: data.dtype
Out[7]: dtype('float64')
</code></pre>
<blockquote>
<p>NOTE: Whenever you see “array,” “NumPy array,” or “ndarray” in the text,<br>
with few exceptions they all refer to the same thing: the ndarray object.</p>
</blockquote>
<h5>Creating ndarrays</h5>
<p>创建一个ndarray的最简单的方法就是使用<code>array</code>功能。比如说：</p>
<pre><code>In [8]: data1 = [6, 7.5, 8, 0, 1]

In [9]: arr1 = np.array(data1)

In [10]: arr1
Out[10]: array([6. , 7.5, 8. , 0. , 1. ])
</code></pre>
<p>或者你想创建嵌套序列，比如等长列表，将会被转换为多维数组:</p>
<pre><code>In [11]: data2 = [[1, 2, 3, 4], [5, 6, 7, 8]]

In [12]: arr2 = np.array(data2)

In [13]: arr2
Out[13]:
array([[1, 2, 3, 4],
       [5, 6, 7, 8]])
</code></pre>
<p>因为data2是一个由list组成的list，所以arr2的shape是一个二维的数组。你可以用<code>ndim</code>和<code>shape</code>来检查：</p>
<pre><code>In [14]: arr2.ndim #看维度
Out[14]: 2

In [15]: arr2.shape
Out[15]: (2, 4)

In [16]: arr2.dtype
Out[16]: dtype('int64') #数组内数据类型是int整数
</code></pre>
<p>另外，<code>np.array</code>还有很多其他的功能来创建新的arrays。比如说，它可以创建全是1或者全是0的array。还可以创建一个空的array，即没有确定值：</p>
<pre><code>In [17]: np.zeros(10) #创建全是0的一维数组
Out[17]: array([0., 0., 0., 0., 0., 0., 0., 0., 0., 0.])

In [18]: np.zeros((3,6)) #创建全是0的二维数组
Out[18]:
array([[0., 0., 0., 0., 0., 0.],
       [0., 0., 0., 0., 0., 0.],
       [0., 0., 0., 0., 0., 0.]])

In [19]: np.empty((2,3,2)) #创建空数组
Out[19]:
array([[[6.95334423e-310, 0.00000000e+000],
        [0.00000000e+000, 0.00000000e+000],
        [0.00000000e+000, 0.00000000e+000]],

       [[0.00000000e+000, 0.00000000e+000],
        [0.00000000e+000, 0.00000000e+000],
        [0.00000000e+000, 0.00000000e+000]]])
</code></pre>
<blockquote>
<p>有的时候，<code>np.empty</code>创建的空数组，返回值不是0，而是一堆乱七八糟的值，也就是“garbage” values。</p>
</blockquote>
<h5>Data Types for ndarrays</h5>
<p>在你创建一个ndarray的时候，你可以指定这个ndarray里的数据类型是什么，比如说：</p>
<pre><code>In [20]: arr1 = np.array([1, 2, 3], dtype=np.float64)

In [21]: arr1
Out[21]: array([1., 2., 3.])

In [22]: arr2 = np.array([1, 2, 3], dtype=np.int32)

In [23]: arr2
Out[23]: array([1, 2, 3], dtype=int32)

In [24]: arr1.dtype
Out[24]: dtype('float64')

In [25]: arr2.dtype
Out[25]: dtype('int32')
</code></pre>
<p>此外，你也可以更改一个数组的数据类型：</p>
<pre><code>In [26]: arr = np.array([1, 2, 3, 4, 5])

In [27]: arr.dtype
Out[27]: dtype('int64')

In [28]: float_arr = arr.astype(np.float64) #把整数类型改成浮点类型

In [29]: float_arr.dtype
Out[29]: dtype('float64')
</code></pre>
<p>相反，你也可以把浮点类型改成整数，但是小数部分就会被截掉：</p>
<pre><code>In [30]: arr = np.array([3.7, -1.2, -2.6, 0.5, 12.9, 10.1])

In [31]: arr
Out[31]: array([ 3.7, -1.2, -2.6,  0.5, 12.9, 10.1])

In [32]: arr.astype(np.int32)
Out[32]: array([ 3, -1, -2,  0, 12, 10], dtype=int32)
</code></pre>
<p>如果你的数组内是字符串类型，也可以使用这种方法进行转换：</p>
<pre><code>In [33]: numeric_strings = np.array(['1.25', '-9.6', '42'], dtype=np.string_)

In [34]: numeric_strings.astype(float)
Out[34]: array([ 1.25, -9.6 , 42.  ])
</code></pre>
<blockquote>
<p>在使用<code>numpy.string_</code>进行数据类型转换的时候需要注意，有的时候会在没有任何提示下截断你的数据。</p>
</blockquote>
<h5>Arithmetic（运算） with NumPy Arrays</h5>
<p>array很重要，因为它们使你能够对数据批量处理操作，而不需要编写任何for循环。NumPy用户称之为向量化。任何算术必须在相同大小数组之间进行操作:</p>
<pre><code>In [35]: arr = np.array([[1., 2., 3.], [4., 5., 6.]])

In [36]: arr
Out[36]:
array([[1., 2., 3.],
       [4., 5., 6.]])

In [37]: arr*arr
Out[37]:
array([[ 1.,  4.,  9.],
       [16., 25., 36.]])

In [38]: 1/arr
Out[38]:
array([[1.        , 0.5       , 0.33333333],
       [0.25      , 0.2       , 0.16666667]])

In [39]: arr**0.5
Out[39]:
array([[1.        , 1.41421356, 1.73205081],
       [2.        , 2.23606798, 2.44948974]])
</code></pre>
<p>你还可以比较两个不同的array的大小，这里比较的时候是数组之间相同位置进行比较：</p>
<pre><code>In [40]: arr2 = np.array([[0., 4., 1.], [7., 2., 12.]])

In [41]: arr2
Out[41]:
array([[ 0.,  4.,  1.],
       [ 7.,  2., 12.]])

In [42]: arr2>arr
Out[42]:
array([[False,  True, False],
       [ True, False,  True]])
</code></pre>
<h5>Basic Indexing（索引） and Slicing（切片）</h5>
<p>在Numpy里，你有很多种方法可以在data里选择一个subset，或者选择出某一个元素。对于一维数组来说是非常简单的：</p>
<pre><code>In [43]: arr=np.arange(10)

In [44]: arr
Out[44]: array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])

In [45]: arr[5]
Out[45]: 5

In [46]: arr[5:8]
Out[46]: array([5, 6, 7])

In [47]: arr[5:8]=12 #从索引的第5位到第7位改成12（这里涉及python的索引规则）

In [48]: arr
Out[48]: array([ 0,  1,  2,  3,  4, 12, 12, 12,  8,  9])
</code></pre>
<p>对数组进行“切片”：</p>
<pre><code>In [49]: arr_slice=arr[5:8]

In [50]: arr_slice
Out[50]: array([12, 12, 12])
</code></pre>
<p>对切出来的“片段”进行修改：</p>
<pre><code>In [51]: arr_slice[1]=12345

In [52]: arr #对切片的修改会影响整个原始数组
Out[52]:
array([    0,     1,     2,     3,     4,    12, 12345,    12,     8,
           9])
</code></pre>
<p>对于二维数组来说：</p>
<pre><code>In [53]: arr2d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])

In [54]: arr2d[2]
Out[54]: array([7, 8, 9])

In [55]: arr2d[0][2]
Out[55]: 3

In [56]: arr2d[0,2] #这样的表示方法可以参考下面的示意图来进行理解
Out[56]: 3
</code></pre>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1213" data-height="583"><img data-original-src="//upload-images.jianshu.io/upload_images/18922188-e67c1faa16ae02db.png" data-original-width="1213" data-original-height="583" data-original-format="image/png" data-original-filesize="54329" src="https://upload-images.jianshu.io/upload_images/18922188-e67c1faa16ae02db.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<p>那如果是多维数组呢？比如现在有一个2 × 2 × 3 array：</p>
<pre><code>In [57]: arr3d = np.array([[[1, 2, 3], [4, 5, 6]], [[7, 8, 9], [10, 11, 12]]])

In [58]: arr3d
Out[58]:
array([[[ 1,  2,  3],
        [ 4,  5,  6]],

       [[ 7,  8,  9],
        [10, 11, 12]]])

In [59]: arr3d[0]
Out[59]:
array([[1, 2, 3],
       [4, 5, 6]])
</code></pre>
<p>更改多维数组里的数据：</p>
<pre><code>In [60]: old_values=arr3d[0].copy()

In [61]: arr3d[0]=42 #更改其中一个元素，使得这个元素里的所有值都变成42

In [62]: arr3d
Out[62]:
array([[[42, 42, 42],
        [42, 42, 42]],

       [[ 7,  8,  9],
        [10, 11, 12]]])

In [63]: arr3d[0]=old_values #再改回来

In [64]: arr3d
Out[64]:
array([[[ 1,  2,  3],
        [ 4,  5,  6]],

       [[ 7,  8,  9],
        [10, 11, 12]]])
</code></pre>
<p>对多维数组切片：</p>
<pre><code>In [65]: arr3d[1,0]
Out[65]: array([7, 8, 9])
</code></pre>
<pre><code>In [66]: arr2d
Out[66]:
array([[1, 2, 3],
       [4, 5, 6],
       [7, 8, 9]])

In [67]: arr2d[:2]
Out[67]:
array([[1, 2, 3],
       [4, 5, 6]])
</code></pre>
<pre><code>In [68]: arr2d[:2,1:] #在二维数组里取第0和1个索引对应的list，然后在这两个list里取从索引1开始，到最后的元素
Out[68]:
array([[2, 3],
       [5, 6]])

In [69]: arr2d[1,:2] #取索引是1的list，然后在这个list里取从开始到索引为2（不包括2）的元素
Out[69]: array([4, 5])
</code></pre>
<p>有关二维数组的切片的索引位置，可以参考下图：</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="1211" data-height="933"><img data-original-src="//upload-images.jianshu.io/upload_images/18922188-862e4153476e5bef.png" data-original-width="1211" data-original-height="933" data-original-format="image/png" data-original-filesize="93683" src="https://upload-images.jianshu.io/upload_images/18922188-862e4153476e5bef.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<p>将数组里小于0的数都设置为0：</p>
<pre><code>In [70]: data = np.random.randn(7, 4)

In [71]: data
Out[71]:
array([[ 1.07484753, -1.37075898, -1.76641029,  1.39686773],
       [ 1.12808743,  0.38325471,  2.26384631,  1.21861537],
       [-0.37522887, -1.2066686 , -0.07729884,  1.76493675],
       [ 0.51771666,  0.14024697,  0.91802525,  0.88580838],
       [-0.17494945, -0.14744639,  0.82242766, -0.060019  ],
       [ 1.11820368, -1.18942934,  1.34140358, -0.9074736 ],
       [ 0.01312651, -2.17228966,  0.97890648,  1.51395293]])

In [72]: data[data<0]=0

In [73]: data
Out[73]:
array([[1.07484753, 0.        , 0.        , 1.39686773],
       [1.12808743, 0.38325471, 2.26384631, 1.21861537],
       [0.        , 0.        , 0.        , 1.76493675],
       [0.51771666, 0.14024697, 0.91802525, 0.88580838],
       [0.        , 0.        , 0.82242766, 0.        ],
       [1.11820368, 0.        , 1.34140358, 0.        ],
       [0.01312651, 0.        , 0.97890648, 1.51395293]])
</code></pre>
<h5>Fancy Indexing</h5>
<p>花式索引是NumPy采用的术语，用于描述对整数数组进行索引：</p>
<pre><code>In [74]: arr=np.empty((8,4)) #比如先创建一个8*4的空数组

In [75]: arr #这就是上面说到的，有时候你创建的空数组不是每次都会是0
Out[75]:
array([[ 6.95334381e-310,  0.00000000e+000,  6.93002310e-310,
         4.34669976e-118],
       [ 6.93002307e-310,  6.93002310e-310,  1.04440620e+181,
         6.93002307e-310],
       [ 6.93002310e-310, -1.76250980e-304,  6.93002307e-310,
         6.93002310e-310],
       [ 8.10582968e-283,  6.93002307e-310,  6.93002310e-310,
         2.58280046e+280],
       [ 6.93002308e-310,  6.93002461e-310,  1.20122413e+036,
         6.93002307e-310],
       [ 6.93002461e-310,  6.39556658e-245,  6.93002307e-310,
         6.93002461e-310],
       [ 9.69473502e+012,  6.93002307e-310,  6.93002461e-310,
         2.99497312e+029],
       [ 6.93002307e-310,  6.93002461e-310, -2.36433447e+212,
         6.93002307e-310]])

In [76]: for i in range(8): #给这个空数组赋值
    ...:     arr[i]=i
    ...:

In [77]: arr
Out[77]:
array([[0., 0., 0., 0.],
       [1., 1., 1., 1.],
       [2., 2., 2., 2.],
       [3., 3., 3., 3.],
       [4., 4., 4., 4.],
       [5., 5., 5., 5.],
       [6., 6., 6., 6.],
       [7., 7., 7., 7.]])
</code></pre>
<p>选择你想提取的subset，并按照特定顺序排列：</p>
<pre><code>In [78]: arr[[4,3,0,6]]
Out[78]:
array([[4., 4., 4., 4.],
       [3., 3., 3., 3.],
       [0., 0., 0., 0.],
       [6., 6., 6., 6.]])

In [79]: arr[[-3,-5,-7]] #负数表示从倒数顺序来取subset
Out[79]:
array([[5., 5., 5., 5.],
       [3., 3., 3., 3.],
       [1., 1., 1., 1.]])
</code></pre>
<h5>通用函数</h5>
<pre><code>In [1]: import numpy as np

In [2]: arr = np.arange(10)

In [3]: arr
Out[3]: array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])

In [4]: np.sqrt(arr)   #计算每一个元素的开方
Out[4]:
array([0.        , 1.        , 1.41421356, 1.73205081, 2.        ,
       2.23606798, 2.44948974, 2.64575131, 2.82842712, 3.        ])

In [5]: np.exp(arr)     #numpy.exp()：返回e的幂次方，e是一个常数为2.71828
Out[5]:
array([1.00000000e+00, 2.71828183e+00, 7.38905610e+00, 2.00855369e+01,
       5.45981500e+01, 1.48413159e+02, 4.03428793e+02, 1.09663316e+03,
       2.98095799e+03, 8.10308393e+03])
</code></pre>
<h5>Unique</h5>
<p>针对一维数组，这个函数是把数组里“不重复的”元素挑选出来。</p>
<pre><code>In [11]: names = np.array(['Bob', 'Joe', 'Will', 'Bob', 'Will', 'Joe', 'Joe'])

In [12]: np.unique(names)
Out[12]: array(['Bob', 'Joe', 'Will'], dtype='<U4')

In [13]: ints = np.array([3, 3, 3, 2, 2, 1, 1, 4, 4])

In [14]: np.unique(ints)
Out[14]: array([1, 2, 3, 4])
</code></pre>
  
</div>
            
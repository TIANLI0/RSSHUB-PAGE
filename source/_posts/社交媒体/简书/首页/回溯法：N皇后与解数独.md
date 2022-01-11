
---
title: '回溯法：N皇后与解数独'
categories: 
 - 社交媒体
 - 简书
 - 首页
headimg: 'https://upload-images.jianshu.io/upload_images/6963391-9e19e2ad6bcacc56.png'
author: 简书
comments: false
date: Invalid Date
thumbnail: 'https://upload-images.jianshu.io/upload_images/6963391-9e19e2ad6bcacc56.png'
---

<div>   
<p>好久没写博客了，最近比较忙，在系统学习一些知识，没学完之前不太容易输出高质量文章，等过段时间学完了再整理一下写几篇文章出来。</p>
<p>但中间也在用零碎的时间学学别的，今天写总结一下回溯法。</p>
<h1>概念</h1>
<p><a href="https://links.jianshu.com/go?to=https%3A%2F%2Fzh.wikipedia.org%2Fwiki%2F%25E5%259B%259E%25E6%25BA%25AF%25E6%25B3%2595" target="_blank">回溯法</a>作为一种搜索算法，可以找出所有或一部分解的一般性算法，尤其适用于约束满足问题，例如今天要讲的N皇后、解数独等等。<br>
回溯法采用<a href="https://links.jianshu.com/go?to=https%3A%2F%2Fzh.wikipedia.org%2Fwiki%2F%25E8%25AF%2595%25E9%2594%2599" target="_blank">试错</a>的思想，它尝试分步的去解决一个问题。在分步解决问题的过程中，当它通过尝试发现现有的分步答案不能得到有效的正确的解答的时候，它将取消上一步甚至是上几步的计算，再通过其它的可能的分步解答再次尝试寻找问题的答案。回溯法通常用最简单的<a href="https://links.jianshu.com/go?to=https%3A%2F%2Fzh.wikipedia.org%2Fwiki%2F%25E9%2580%2592%25E5%25BD%2592" target="_blank">递归</a>方法来实现，在反复重复上述的步骤后可能出现两种情况：</p>
<ul>
<li>找到一个可能存在的正确的答案</li>
<li>在尝试了所有可能的分步方法后宣告该问题没有答案</li>
</ul>
<p>在最坏的情况下，回溯法会导致一次复杂度为指数时间的计算。</p>
<p>回溯法实际上是一种 DFS(深度优先搜索算法)的一种，不同的是，回溯法具备剪枝的能力，下面通过两个例子来具体分析回溯算法。</p>
<h1>N 皇后</h1>
<p>N 皇后问题是基于<a href="https://links.jianshu.com/go?to=https%3A%2F%2Fzh.wikipedia.org%2Fwiki%2F%25E5%2585%25AB%25E7%259A%2587%25E5%2590%258E%25E9%2597%25AE%25E9%25A2%2598" target="_blank">八皇后问题</a>的进一步发展，如何能够在 n * n 大小的国际象棋棋盘上摆放 n 个皇后，使得任何一个皇后都无法直接吃掉其他的皇后？为了达到此目的，任两个皇后都不能处于同一条横行、纵行或斜线上。下图为八皇后问题的其中一个解。<br>
</p><div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="258" data-height="276"><img data-original-src="//upload-images.jianshu.io/upload_images/6963391-9e19e2ad6bcacc56.png" data-original-width="258" data-original-height="276" data-original-format="image/png" data-original-filesize="8439" src="https://upload-images.jianshu.io/upload_images/6963391-9e19e2ad6bcacc56.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div><p></p>
<p>下面来分析下这个问题。<br>
棋盘上每个位置包含两种状态：有皇后以及没有皇后。在不考虑约束条件的情况下，列出所有组合，我们将得到一个深度为 N * N 的二叉树。</p>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="541" data-height="181"><img data-original-src="//upload-images.jianshu.io/upload_images/6963391-fcf37251674e37c3.png" data-original-width="541" data-original-height="181" data-original-format="image/png" data-original-filesize="18561" src="https://upload-images.jianshu.io/upload_images/6963391-fcf37251674e37c3.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<p>上图描述了棋盘前两个位置的可能性。<br>
最简单的办法是穷举出所有可能性，然后筛选出符合的解。可以通过 DFS 算法遍历这个二叉树，对于 N * N 的棋盘将有 2 的 N * N 次方种可能，这显然是不可接受的。<br>
但我们可以通过规则来进行剪枝，可以使用的规则如下：</p>
<ul>
<li>共需要摆放 N 个皇后</li>
<li>每行只能有一个皇后</li>
<li>每列只能有一个皇后</li>
<li>每斜线上只能有一个皇后</li>
</ul>
<p>通过上述四个条件，我们可以减掉大部分的路径。<br>
现在回到回溯法上来看这道题，回溯法使用试错的思想，分步解决问题，我们可以先假设第一个位置放置皇后，然后根据规则，找到第二个合法的位置再放置第二个皇后，如果找不到合适的位置则表示该路径错误，回溯到上一个位置继续。<br>
回溯法特征之一就是会使用数组或其他数据结构保存遍历信息，从而跳过不合法的路径。<br>
本题使用三个数组分别存储列、左上至右下斜边、右上至坐下斜边的皇后摆放数据。<br>
因为每行只能摆放一个皇后，所以我们按行遍历，尝试在当前行每一个位置放置皇后。然后跳到下一行继续。<br>
下面直接放上代码：</p>
<pre><code class="java">public List<List<String>> solveNQueens(int n) &#123;
    //当前列中是否已有皇后
    boolean[] column = new boolean[n];
    //右上到左下列中是否有皇后
    boolean[] rl = new boolean[2 * n - 1];
    //左上到右下列中是否有皇后
    boolean[] lr = new boolean[2 * n - 1];
    //每行皇后的位置
    int[] board = new int[n];
    List<List<String>> result = new ArrayList<>(n);
    backtrace(n, 0, column, rl, lr, board, result);
    return result;
&#125;

private void backtrace(int n, int row, boolean[] column, boolean[] rl, boolean[] lr, int[] board, List<List<String>> result) &#123;
    if (row >= n) &#123;
        //遍历结束，此时 board 数组中存放的就是解
        List<String> boardList = new ArrayList<>(n);
        for (int i = 0; i < n; i++) &#123;
            StringBuilder rowBuilder = new StringBuilder();
            for (int j = 0; j < n; j++) &#123;
                rowBuilder.append(board[i] == j ? "Q" : ".");
            &#125;
            boardList.add(rowBuilder.toString());
        &#125;
        result.add(boardList);
    &#125;
    //
    for (int columnIndex = 0; columnIndex < n; columnIndex++) &#123;
        if (!column[columnIndex] && !rl[row + columnIndex] && !lr[n - 1 - row + columnIndex]) &#123;
            //无皇后
            column[columnIndex] = rl[row + columnIndex] = lr[n - 1 - row + columnIndex] = true;
            board[row] = columnIndex;
            backtrace(n, row + 1, column, rl, lr, board, result);
            column[columnIndex] = rl[row + columnIndex] = lr[n - 1 - row + columnIndex] = false;
        &#125;
    &#125;
&#125;
</code></pre>
<h2>复杂性分析</h2>
<ul>
<li>时间复杂度：O(N!)<br>
第一个皇后有 N 中摆放方式，第二个皇后必须不能跟第一个在一列以及斜角，所以第二个皇后有 N-1 种可能，以此类推，时间复杂度为 O(N!)。</li>
<li>控件复杂度：O(N)<br>
需要使用数组保存信息。</li>
</ul>
<h1>解数独</h1>
<p>数独游戏就是我们常见的那个解数独的游戏。</p>
<ul>
<li>数字 1-9 在每一行只能出现一次。</li>
<li>数字 1-9 在每一列只能出现一次。</li>
<li>数字 1-9 在每一个以粗实线分隔的 3x3 宫内只能出现一次。</li>
</ul>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="431" data-height="462"><img data-original-src="//upload-images.jianshu.io/upload_images/6963391-3db331c222a56b9b.png" data-original-width="431" data-original-height="462" data-original-format="image/png" data-original-filesize="74123" src="https://upload-images.jianshu.io/upload_images/6963391-3db331c222a56b9b.png" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
<p>思路跟 N 皇后一样，遍历所有空格，逐个将 1-9 数组放置空格内，通过规则判断是否合法，最终找到解。<br>
这里同样需要定义三个数组用于存放遍历数据：每行、每列、每 3x3 宫格内的数据。<br>
另外，如果 Sn 表示 第 n 个 3x3 宫格，那么 Sn = (row / 3) * 3 + column / 3；</p>
<pre><code class="java">public void solveSudoku(char[][] board) &#123;
    List<Character>[] rowRecord = new ArrayList[9];
    List<Character>[] columnRecord = new ArrayList[9];
    List<Character>[] boxRecord = new ArrayList[9];
    //初始化数据
    for (int row = 0; row < 9; row++) &#123;
        for (int column = 0; column < 9; column++) &#123;
            Character c = board[row][column];
            if (rowRecord[row] == null) &#123;
                rowRecord[row] = new ArrayList<>(9);
            &#125;
            if (columnRecord[column] == null) &#123;
                columnRecord[column] = new ArrayList<>(9);
            &#125;
            int boxIndex = (row / 3) * 3 + column / 3;
            if (boxRecord[boxIndex] == null) &#123;
                boxRecord[boxIndex] = new ArrayList<>(9);
            &#125;
            if (c != '.') &#123;
                rowRecord[row].add(c);
                columnRecord[column].add(c);
                boxRecord[boxIndex].add(c);
            &#125;
        &#125;
    &#125;
    backtrack(board, 0, 0, rowRecord, columnRecord, boxRecord);
&#125;

private boolean backtrack(char[][] board,
                          int row, int column,
                          List<Character>[] rowRecord,
                          List<Character>[] columnRecord,
                          List<Character>[] boxRecord) &#123;
    if (row == 9) &#123;
        return true;
    &#125;
    int nextRow = column < 8 ? row : row + 1;
    int nextColumn = column < 8 ? column + 1 : 0;
    int boxIndex = (row / 3) * 3 + column / 3;
    Character currentChar = board[row][column];
    if (currentChar == '.') &#123;
        //逐个尝试把 1-9 放入空格中
        for (int i = 1; i < 10; i++) &#123;
            Character c = (char) (i + 48);
            //判断当前行、列、3x3 矩阵中是否包含改数字
            if (!rowRecord[row].contains(c) &&
                    !columnRecord[column].contains(c) &&
                    !boxRecord[boxIndex].contains(c)) &#123;
                //不包含则把数据放入该空格进行尝试
                board[row][column] = c;
                rowRecord[row].add(c);
                columnRecord[column].add(c);
                boxRecord[boxIndex].add(c);
                //跳转到下一个空格继续
                if (!backtrack(board, nextRow, nextColumn, rowRecord, columnRecord, boxRecord)) &#123;
                    //改路径无法得出解，回溯到上一个状态
                    board[row][column] = currentChar;
                    rowRecord[row].remove(c);
                    columnRecord[column].remove(c);
                    boxRecord[boxIndex].remove(c);
                &#125; else &#123;
                    return true;
                &#125;
            &#125;
        &#125;
    &#125; else &#123;
        return backtrack(board, nextRow, nextColumn, rowRecord, columnRecord, boxRecord);
    &#125;
    return false;
&#125;
</code></pre>
<h2>复杂性分析</h2>
<ul>
<li><p>时间复杂度<br>
本题的输入是固定的九宫格，所以直接计算实际次数。<br>
第一行有不多于 9 个空格要填数字，由于不能重复，所以共有 9! 种方式，总共有 9 行，所以最多需要(9!)^9 次。</p></li>
<li><p>空间复杂度<br>
我们定义了三个数组，每个数组有 81 个元素，共有 3x81=243 个元素。</p></li>
</ul>
<p>上面的代码我放在 Github 上了，里面还有很多其他数据结构与算法相关的代码，需要的可以看看：<br>
<a href="https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2F0xZhangKe%2FAlgorithms%2Ftree%2Fmaster%2Fsrc%2Fcom%2Fzhangke%2Falgorithms%2Fleetcode" target="_blank">https://github.com/0xZhangKe/Algorithms/tree/master/src/com/zhangke/algorithms/leetcode</a></p>
<p>欢迎关注我的公众号，还有更多干货。</p>
<p>微信扫描二维码或者搜索：zhangke_blog</p>
<br>
<div class="image-package">
<div class="image-container">
<div class="image-container-fill"></div>
<div class="image-view" data-width="258" data-height="258"><img data-original-src="//upload-images.jianshu.io/upload_images/6963391-e38980ba75b09b87.jpg" data-original-width="258" data-original-height="258" data-original-format="image/jpeg" data-original-filesize="28159" src="https://upload-images.jianshu.io/upload_images/6963391-e38980ba75b09b87.jpg" referrerpolicy="no-referrer"></div>
</div>
<div class="image-caption"></div>
</div>
  
</div>
            
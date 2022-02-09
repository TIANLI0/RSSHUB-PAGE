
---
title: '数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了'
categories: 
 - 新媒体
 - 快科技（原驱动之家）
 - 最新新闻
headimg: 'https://img1.mydrivers.com/img/20220209/Sa21dcea1-7e4d-4658-8c21-9b3b920fa86f.png'
author: 快科技（原驱动之家）
comments: false
date: Wed, 09 Feb 2022 21:08:32 GMT
thumbnail: 'https://img1.mydrivers.com/img/20220209/Sa21dcea1-7e4d-4658-8c21-9b3b920fa86f.png'
---

<div>   
<p>免费猜字小游戏Wordle正在席卷全球，火到以数百万美元的价格被收购，全球玩家数量也突破了200万。</p>
<p>如果你在微博、微信等地方看到这些神神秘秘的方块，那就是Wordle玩家在分享自己当日的战绩了。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/a21dcea1-7e4d-4658-8c21-9b3b920fa86f.png" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="1083" src="https://img1.mydrivers.com/img/20220209/Sa21dcea1-7e4d-4658-8c21-9b3b920fa86f.png" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>根据统计，大多数人类玩家需要猜测4次或以上才能取得胜利。</p>
<p>比如，2月5日的题目在当天30多万份晒出战绩的玩家中，只有27%能在三次以内猜中。</p>
<p>这个游戏自然也成了程序员们的新竞技场，他们写出各种算法来比拼谁用的步数最少。</p>
<p>这其中，百万粉数学科普大神3Blue1Brown的玩法更为硬核——</p>
<p>他不光写出了求解算法，还用数学知识一步步优化至逼近理论极限，最终成绩平均3.138次猜测就能获胜。</p>
<p>并且他用统计办法找出了与人类常见策略不同的最佳开局单词crane。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/5ef5e365-188e-4bb7-8f6d-e368850f8d0d.png" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="387" src="https://img1.mydrivers.com/img/20220209/S5ef5e365-188e-4bb7-8f6d-e368850f8d0d.png" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>他像往常一样把这个过程整理成视频分享出来，不仅展示了算法，还把其中涉及的信息论、统计学知识讲得明明白白。</p>
<p>视频发布一天之内就有上百万播放，围观的网友也纷纷在评论区表达了赞叹。</p>
<p>为了游戏点进来，为了精彩的信息论知识留下，太酷了！</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/0fbbe9c8-5678-4f1d-a23b-d746c0756210.png" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="164" src="https://img1.mydrivers.com/img/20220209/S0fbbe9c8-5678-4f1d-a23b-d746c0756210.png" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>他用了什么样的算法，理论极限又是怎么算出来的？下面一起来看看。</p>
<p>从每一次猜测中获得最多信息</p>
<p>Wordle的游戏规则很简单，玩家需要猜出程序每天指定的一个5位英语单词谜底。</p>
<p>玩家可以随意提交一个英语单词，但必须是字典里有的，不能胡乱拼写。</p>
<p>如果字母在谜底中出现且位置对了就显示绿色，字母出现了但位置不对就显示黄色，字母在答案的单词中没出现就显示灰色。</p>
<p>根据反馈信息再进行下一轮猜测，在6次尝试之内猜出就算赢。</p>
<p style="text-align: center"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="552" src="https://img1.mydrivers.com/img/20220209/789cfa8c-4c63-496d-93e0-a91ac04da24f.png" style="border: black 1px solid" w="374" referrerpolicy="no-referrer"></p>
<p>如何让步数尽量少？</p>
<p>3Blue1Brown的总体思路是尽量从每一次猜测中获得最多的信息。</p>
<p>他先是找来了26个字母在英语文本中出现频率的统计数据，尝试在前两次尝试中覆盖最多高频字母。</p>
<p>比如other+nails的组合，就可以覆盖出现频率最高的11个字母中的10个，如果运气好就能确定下来一些字母。</p>
<p>即使这些字母都没出现依然是一种信息量很大的反馈，10个常用字母都没出现的单词数量就大大减少了，让下一步猜测更简单。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/570669eb-fdc6-4127-aca5-dc3edaef105e.png" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="324" src="https://img1.mydrivers.com/img/20220209/S570669eb-fdc6-4127-aca5-dc3edaef105e.png" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>不过在尝试过程中，又出现了新的问题。</p>
<p>同样用nails这几个字母，也可以拼成snail ，这两种拼写顺序之间的差异，仅依据字母频率数据是无法衡量的。</p>
<p>下面需要一种新的计算方法。</p>
<p>如何计算信息量？</p>
<p>原版Wordle游戏里有一个数量12972的总单词列表，都能作为猜测词使用。</p>
<p>另外有一个2315个单词的列表，只有这些单词会出现在答案里(据说是游戏作者的女朋友挑选的)。</p>
<p>因为游戏是用Javascript写的，数据都在客户端，这些数据直接可以从源码里找到。</p>
<p>不过3Blue1Brown觉得让程序利用答案列表的话有点像作弊了，他果断给自己加大难度，只考虑总单词列表。</p>
<p>游戏中，每一次猜测都能从12972个单词中排除一些结果。</p>
<p>比如猜测weary，如果W位置正确同时A出现了，那么剩下的可选单词只剩58个。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/0b12e585-5a7d-4ca9-bed7-58cfdd2cd93d.png" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="313" src="https://img1.mydrivers.com/img/20220209/S0b12e585-5a7d-4ca9-bed7-58cfdd2cd93d.png" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>这样对同一个猜测，从5个字母全没出现到5个字母全对的各种反馈的概率都可以计算出来。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/044685cd-b342-4c1c-a518-564aeb426d07.jpg" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="337" src="https://img1.mydrivers.com/img/20220209/S044685cd-b342-4c1c-a518-564aeb426d07.jpg" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>这样，问题就变成了如何评估各种反馈情况包含的信息量。</p>
<p>3Blue1Brown选择的办法，就是利用信息论祖师爷香农提出的信息熵概念。</p>
<p>信息熵描述的是事件的不确定性，单位就是大家知道的比特。</p>
<p>理解起来也不难，可以用扔硬币来解释。</p>
<p>扔1枚硬币只会出现正、反两种结果，而且概率相等。</p>
<p>扔2枚硬币就有正正、正反、反正、反反这4种结果，扔3枚有8种情况等等，也就是扔n次有2的n次方种结果。</p>
<p>当一个事件有两种结果且概率都是1/2，其不确定性相当于扔1枚硬币，此时信息熵定义为1比特。</p>
<p>如果一个事件有8种结果且概率都是1/8，就相当于扔3枚硬币，此时信息熵就是3比特。</p>
<p>信息量和信息熵的数量相等、意义相反，相当于衡量一则信息能消除多少不确定性。</p>
<p>设每种结果的概率为p，信息量为I，有如下等式。</p>
<p style="text-align: center"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="218" src="https://img1.mydrivers.com/img/20220209/44ce3de2-2ba5-4093-bec2-4d81e9d29af7.png" style="border: black 1px solid" w="318" referrerpolicy="no-referrer"></p>
<p>稍作变换，可以得到信息量的计算公式。</p>
<p style="text-align: center"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="668" src="https://img1.mydrivers.com/img/20220209/2d3eebe3-a442-4bd2-8f85-b11475e07aed.png" style="border: black 1px solid" w="382" referrerpolicy="no-referrer"></p>
<p>回到Wordle游戏上，一次猜测获得的信息量可以用每种可能情况的概率与对应信息量相乘、再把结果相加来计算，也就是求数学期望。</p>
<p>以猜测weary为例，计算出获得的信息量为4.9比特。</p>
<p>代表这则信息消除的不确定性比扔5个硬币的不确定性少一点。</p>
<p style="text-align: center"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="94" src="https://img1.mydrivers.com/img/20220209/ab167e60-493a-45c9-9d61-2246fe07ed78.png" style="border: black 1px solid" w="536" referrerpolicy="no-referrer"></p>
<p>算法思路有了，接下来就可以交给程序，计算出所有12972个单词的能消除的信息熵。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/8ed77275-d209-43ad-a433-a8096e3f62fa.jpg" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="337" src="https://img1.mydrivers.com/img/20220209/S8ed77275-d209-43ad-a433-a8096e3f62fa.jpg" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>用同样的方法，可以再计算第二步、第三步猜测能消除的信息熵。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/6ff7ef74-664c-4d61-a782-8ee73631d1ea.jpg" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="337" src="https://img1.mydrivers.com/img/20220209/S6ff7ef74-664c-4d61-a782-8ee73631d1ea.jpg" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>根据这些计算结果，程序就可以在每一次猜测时，选择所有可能单词里能消除信息熵最多的那个。</p>
<p>比如第一次猜slate获得一次反馈，此时还剩下578个单词可选，其中选ramin能消除最多的信息熵，这样一步一步猜直到猜出正确答案。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/3a529a94-a7d4-460a-b1f9-3712fd31bb0d.png" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="336" src="https://img1.mydrivers.com/img/20220209/S3a529a94-a7d4-460a-b1f9-3712fd31bb0d.png" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>接下来，拿这个程序在所有2135种可能的答案上跑一遍，平均用了4.124步猜出正确答案。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/9c48dd52-b1cb-4d67-8ef5-c8f533f3907c.png" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="417" src="https://img1.mydrivers.com/img/20220209/S9c48dd52-b1cb-4d67-8ef5-c8f533f3907c.png" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>3Blue1Brown觉得这个成绩还不够好，至少没有超过普通人类玩家水平，还需要继续优化。</p>
<p>最终成绩逼近理论极限</p>
<p>成绩不够好的一个问题出在每个单词作为答案的可能性其实并不相同。</p>
<p>像aahed aalii aargh这种偏门单词虽然在允许猜测的总单词列表里，但并不在答案列表的2315个单词里。</p>
<p>找一个典型的例子，当遇到abbas（人名，阿巴斯）和abyss（深渊）二选一时，如果程序能知道abyss是常用词，就可以省下一步。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/689ce975-c4b3-4e30-b277-f79730f3d2bf.png" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="383" src="https://img1.mydrivers.com/img/20220209/S689ce975-c4b3-4e30-b277-f79730f3d2bf.png" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>下一步改进方向就是引入词频统计数据，这样的数据集可以从Wolfram上找到。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/09d73a38-394f-4cb2-8479-830afdfcfd2a.png" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="280" src="https://img1.mydrivers.com/img/20220209/S09d73a38-394f-4cb2-8479-830afdfcfd2a.png" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>这里还遇到一个问题，比如which和braid的出现频率相差1000倍，但都可以算是常见单词，出现在答案列表里的可能性相差不大。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/7366995e-a352-4edc-8581-bbbcf50ab954.png" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="400" src="https://img1.mydrivers.com/img/20220209/S7366995e-a352-4edc-8581-bbbcf50ab954.png" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>解决办法就是用Sigmoid函数做处理，让更多数据靠近0或1。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/72706ccb-e48d-4f2e-99c3-7301290846a0.png" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="329" src="https://img1.mydrivers.com/img/20220209/S72706ccb-e48d-4f2e-99c3-7301290846a0.png" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>将处理后的词频数据与前面的信息量计算结果相结合，得到优化后的信息量计算方法。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/cd7c778b-2816-4d57-b7f8-75ed2f78c9a8.png" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="341" src="https://img1.mydrivers.com/img/20220209/Scd7c778b-2816-4d57-b7f8-75ed2f78c9a8.png" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>在实际游戏中，也把信息量与词频结合考虑，就能让程序更倾向于选择常见单词。</p>
<p>比如在下面的情况中，words和dorms的信息量并不是最高的，但因为词频较高所以优先考虑。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/24cadb22-a76d-4e36-b5ce-84f9de9922db.png" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="343" src="https://img1.mydrivers.com/img/20220209/S24cadb22-a76d-4e36-b5ce-84f9de9922db.png" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>优化后的成绩到了3.601，平均节省了半步。</p>
<p>如果加大计算量，每次根据两步搜索的结果选择单词可以进一步提高成绩。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/e6bd1bbf-9828-4ee0-a648-958a974a39f1.jpg" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="337" src="https://img1.mydrivers.com/img/20220209/Se6bd1bbf-9828-4ee0-a648-958a974a39f1.jpg" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>而且根据两步搜索的计算结果，3Blue1Brown认为能获得最大信息量的开局单词是crane。</p>
<p>此外还可以让程序知道具体哪2315个单词真的是在答案列表里的，用上所有这些技巧后，成绩再次提升到3.438。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/07e3d39e-6233-45da-b099-316ecd0b6f8a.png" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="280" src="https://img1.mydrivers.com/img/20220209/S07e3d39e-6233-45da-b099-316ecd0b6f8a.png" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>实际上这个成绩的理论极限就不可能低于3。</p>
<p>2315种答案意味着有11.17比特的不确定性，而暴力搜索后，前两步能获得的最大信息量在10.01比特，还剩下1.16。</p>
<p>也就是说第三步的难度比二选一还要难一点，没有算法能保证每次都正确。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/6edb9e80-80a0-44de-8aff-e0007fd6aa75.png" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="340" src="https://img1.mydrivers.com/img/20220209/S6edb9e80-80a0-44de-8aff-e0007fd6aa75.png" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>不过3Blue1Brown还是找到了新办法进一步提升成绩。</p>
<p>让程序记住每个正确答案，并在下一局中把猜过的单词排除出去，最终成绩到达3.138，逼近了理论极限。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/ca384fd9-b636-4c17-9b23-f44676b83ef2.png" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="383" src="https://img1.mydrivers.com/img/20220209/Sca384fd9-b636-4c17-9b23-f44676b83ef2.png" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>看完整个视频后，有网友表示学到的信息论知识比上课学到的还多。</p>
<p>也有很多人对到底哪个单词才是最佳开局展开了讨论。</p>
<p>虽然两步搜索的结果是crane，不过3Blue1Brown也不确定对于人类玩家来说是不是最佳开局单词。</p>
<p>毕竟实际游戏中人类很难像程序一样算出第二步的情况。</p>
<p>对于人类来说，soare和tares都是很好的开局。</p>
<p>还能挑战变态模式</p>
<p>程序写好后，3Blue1Brown还做了更多尝试，比如原版Wordle的困难难度，成绩是3.562，</p>
<p>还有一个Wordle变态版Absurdle，这个版本不再限制尝试次数，但变态之处在于游戏AI会与玩家对抗。</p>
<p>玩家猜测一次后正确答案就会变化，在所有反馈可能性中挑选信息熵最大的那个，就像是在躲避玩家的猜测。</p>
<p>Absurdle的作者之前还开发过一个变态版俄罗斯方块，每次都给你最不需要的方块。</p>
<p>对于这个变态版Wordle，结果3Blue1Brown的程序也挑战成功。</p>
<p style="text-align: center"><a href="https://img1.mydrivers.com/img/20220209/c170fa16-0a77-4251-a3fe-9576727abfde.png" target="_blank"><img alt="数学大神攻克猜字游戏Wordle：求解算法成绩逼近理论极限 连信息论都用上了" h="421" src="https://img1.mydrivers.com/img/20220209/Sc170fa16-0a77-4251-a3fe-9576727abfde.png" style="border: black 1px solid" w="600" referrerpolicy="no-referrer"></a></p>
<p>如果你看到这里也想挑战这个变态版试试，可以点下方链接。</p>
<p>原版游戏地址：<a class="f14_link" href="https://www.powerlanguage.co.uk/wordle" target="_blank">点此跳转</a></p>
<p>变态版游戏地址：<a class="f14_link" href="https://qntm.org/files/absurdle/absurdle.html" target="_blank">点此跳转</a></p>

           
           
<p class="end"> - THE END -</p> 
            
 <p class="bqian"><a href="https://news.mydrivers.com/tag/kejikepu.htm"><i>#</i>科技科普</a><a href="https://news.mydrivers.com/tag/kejiqianyan.htm"><i>#</i>科技前沿</a><a href="https://news.mydrivers.com/tag/kepu.htm"><i>#</i>科普</a></p>
<p class="url">
     <span>原文链接：<a href="https://mp.weixin.qq.com/s/iddHGL4IaibPq_A59efuyg">量子位</a></span>
<span>责任编辑：祥云</span>
</p>
        
</div>
            
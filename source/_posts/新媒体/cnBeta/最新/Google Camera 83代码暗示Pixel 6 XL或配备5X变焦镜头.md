
---
title: 'Google Camera 8.3代码暗示Pixel 6 XL或配备5X变焦镜头'
categories: 
 - 新媒体
 - cnBeta
 - 最新
headimg: 'https://static.cnbetacdn.com/article/2021/0713/37a9344fd9e47b1.jpg'
author: cnBeta
comments: false
date: Thu, 15 Jul 2021 06:10:18 GMT
thumbnail: 'https://static.cnbetacdn.com/article/2021/0713/37a9344fd9e47b1.jpg'
---

<div>   
今天早些时候，谷歌向 Pixel 智能机用户推送了 Android 12 的第三个测试版本。<strong>除了滚动截屏、智能旋转等体验改进，我们还看到了全新的壁纸选择器（WallpaterPicker）和拍照应用（Google Camera）。</strong>随着版本号从 8.2.400 升至 8.3.252，原生相机应用似乎仅引入了对 Android 12 动态主题系统的支持。<br>
 <p><img src="https://static.cnbetacdn.com/article/2021/0713/37a9344fd9e47b1.jpg" referrerpolicy="no-referrer"></p><p style="text-align: center;">渲染图（来自 @OnLeaks x 91Mobiles）</p><p>但在深入 APK 安装包后，XDA-Developers 又揭示了有关即将到来的“Pixel 6 XL”的一些信息，比如该机可能配备“超长焦”（Ultra Tele）摄像头。</p><p><img src="https://static.cnbetacdn.com/article/2021/0715/c560d4d8bb0dc19.png" alt="2.png" referrerpolicy="no-referrer"></p><p><strong>据悉，catark27 在布局（layout）文件中发现了有关相机 App 缩放 UI 的新代码行：</strong></p><blockquote><p><TextView android:textSize="@dimen/zoom_toggle_button_text_size" android:textColor="@color/zoom_toggle_bar_text_color" android:gravity="center" android:layout_gravity="right|center_vertical|center_horizontal|center" android:id="@+id/zoom_toggle_ultratele" android:clickable="false" android:layout_width="@dimen/zoom_toggle_unselected_button_size" android:layout_height="@dimen/zoom_toggle_unselected_button_size" android:text="5x" android:includeFontPadding="false" android:fontFamily="@font/google_sans_text_medium" android:textAlignment="center"/></p></blockquote><p>仔细观察的话，你会在其中看到 id "zoom_toggle_ultratele" 和“5x”的文本，意味着相机 App 中将支持 5 倍变焦取景。再深入一些的话，你会看到对“ultratele”变焦切换功能的一些引用。</p><p><img src="https://static.cnbetacdn.com/article/2021/0715/5d8de5a6d3b7f0e.jpg" alt="3.jpg" referrerpolicy="no-referrer"></p><p>尽管尚无直接证据将变焦开关与传说中代号为“raven”的 Pixel 6 XL 联系起来，但开发者 cstark27 还是认为有证据表明“真实”的边角倍数或为 4.3X 。</p><p>作为参考，Pixel 4 的“真实”变焦倍率为 16.X，而 Google Camera 相机应用还是将它简单显示为 2X 。</p><p>此外与 Pixel 4a 5G 和 Pixel 5 机型相比，超广角相机的变焦水平也可能有些不同（当前看似为 0.615X 和 0.670X）。</p><p><img src="https://static.cnbetacdn.com/article/2021/0715/c12f942723c954c.png" alt="4.png" referrerpolicy="no-referrer"></p><p>上周，知名爆料人 Jon Prosser 也揭示了 Pixel 6 系列智能机的一些规格。其中较小的 Pixel 6 配备了 50MP 广角 + 12MP 超广角镜头组成的后置双摄。</p><p><img src="https://static.cnbetacdn.com/article/2021/0715/700b03bc6bfe8c1.jpg" alt="5-1.jpg" referrerpolicy="no-referrer"></p><p>之前曾有传闻称，谷歌将为 Pixel 6 机型引入潜望式长焦镜头，泄露的 CAD 渲染图似乎也证实了这种可能性。</p><p><img src="https://static.cnbetacdn.com/article/2021/0715/d3f386261090b65.jpg" alt="5-2.jpg" referrerpolicy="no-referrer"></p><p>另外还有一些人联想到了谷歌在 I/O 2021 上分享的视频片段中的原生相机 UI 的静态图像，但直到今天披露的代码片段，才首次证实了 5X“超长焦”特性的存在。</p><p><img src="https://static.cnbetacdn.com/article/2021/0715/51c1a4f8a5b57c7.jpg" alt="5-3.jpg" referrerpolicy="no-referrer"></p><p>至于真相究竟如何，仍有待谷歌在今秋的硬件发布会上揭晓。</p>   
</div>
            
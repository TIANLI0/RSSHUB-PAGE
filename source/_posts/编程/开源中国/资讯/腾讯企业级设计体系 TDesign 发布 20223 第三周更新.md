
---
title: '腾讯企业级设计体系 TDesign 发布 2022.3 第三周更新'
categories: 
 - 编程
 - 开源中国
 - 资讯
headimg: 'https://picsum.photos/400/300?random=8170'
author: 开源中国
comments: false
date: Tue, 22 Mar 2022 07:02:00 GMT
thumbnail: 'https://picsum.photos/400/300?random=8170'
---

<div>   
<div class="content">
                                                                                            <div> 
 <div> 
  <p>TDesign 是一款诞生于腾讯内部、拥有完整的设计价值观和视觉风格指南的企业级设计体系，同时提供了丰富的设计资源，在设计体系基础上产出基于 Vue、React、小程序等业界主流技术栈的组件库解决方案，适合用于构建设计统一/多端覆盖/跨技术栈的企业级前端应用。</p> 
  <p>目前，TDesign 发布了 2022 年 3 月的第三周更新，带来如下变更：</p> 
  <h2><strong>组件库</strong></h2> 
  <h3><strong>Vue2 for Web 发布 </strong><a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2FTencent%2Ftdesign-vue%2Freleases%2Ftag%2F0.37.2" target="_blank"><strong>0.37.2 版</strong></a></h3> 
  <ul> 
   <li><code>Button:</code> 修复 <code>disabled </code>不生效的问题</li> 
   <li><code>Cascader</code>: 修复文字过长时不显示 <code>tooltip</code> 的问题</li> 
   <li><code>Datepicker</code>: 修复 <code>Form</code> 中使用时，触发校验时机错误的问题</li> 
   <li><code>InputNumber</code>: 修复小数计算错误的问题</li> 
   <li><code>Popup</code>: <code>trigger</code> 为 <code>hover</code> 时点击引用元素保持开启状态，防止菜单消失</li> 
   <li><code>TagInput</code> ：修复相关样式问题</li> 
   <li><code>TreeSelect</code>: 修复异步加载数据的情况下，<code>label</code> 展示错误的问题</li> 
   <li><code>Timepicker</code>: <code>close</code>、<code>open</code> 事件回调增加参数</li> 
  </ul> 
  <p>详情见：<a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2FTencent%2Ftdesign-vue%2Freleases%2Ftag%2F0.37.2" target="_blank">https://github.com/Tencent/tdesign-vue/releases/tag/0.37.2</a></p> 
  <h3><strong>Vue3 for Web 发布 </strong><a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2FTencent%2Ftdesign-vue-next%2Freleases%2Ftag%2F0.10.2" target="_blank"><strong>0.10.2 版</strong></a></h3> 
  <ul> 
   <li><code>Upload</code>: 增加合并上传,支持国际化配置</li> 
   <li><code>Select</code>:支持单选 <code>valueDisplay</code> 插槽</li> 
   <li><code>Popup</code>: 新增 <code>enter</code>、<code>leave</code> 事件，支持鼠标进入、移出的事件</li> 
   <li><code>Input</code>: 新增 <code>autoWidth</code>、<code>align</code>、<code>tips</code> 的支持，统一 <code>InputNumber</code> 中的 <code>Input</code> 使用 <code>Input</code> 组件减少重复实现</li> 
   <li><code>Notification</code>: 优化完善回收时的动画效果</li> 
   <li><code>DatePicker</code>:打开时间面板重置时间</li> 
   <li><code>Menu</code>:修复在没 <code>overflow</code> 时，仍出现滚动条的问题</li> 
   <li><code>Input</code>: 修复组件<code>keypress</code> 事件未触发,修复在 <code>readonly</code> 模式下的聚焦样式</li> 
   <li><code>TagInput</code>: 修复 <code>breakline</code> 模式下的 <code>clearIcon</code> 样式重叠, 修复 <code>autowidth</code> 模式下的 <code>padding</code> 不对称,修复超出滚动失效</li> 
  </ul> 
  <p>详情见：<a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2FTencent%2Ftdesign-vue-next%2Freleases%2Ftag%2F0.10.2" target="_blank">https://github.com/Tencent/tdesign-vue-next/releases/tag/0.10.2</a></p> 
  <h3><strong>React for Web 发布 </strong><a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2FTencent%2Ftdesign-react%2Freleases%2Ftag%2F0.28.0" target="_blank"><strong>0.28.0 版</strong></a></h3> 
  <ul> 
   <li><code>Swiper</code>: 交互、设计、<code>API</code> 全部重构，如有使用老的 <code>Swiper</code> 组件需重新接入，⚠️存在不兼容更新</li> 
   <li><code>Swiper</code>: 重构 <code>swiper</code> 组件</li> 
   <li><code>Table</code>: 支持 <code>onChange API </code></li> 
   <li><code>InputNumber</code>: 支持 <code>autoWidth</code>、<code>tips</code>、<code>status</code>、<code>align API</code></li> 
   <li><code>Dialog</code>: 修复 <code>DialogPlugin</code> 关闭后滚动问题</li> 
   <li><code>Cascader</code>: 修复 <code>multiple</code> 模式点击后关闭 <code>popup</code> 问题</li> 
   <li><code>Table</code>: 修复 <code>key</code> 有 <code>0</code> 的数据时的排序问题</li> 
   <li><code>Cascader</code>: 修复 <code>children boolean</code> 类型问题</li> 
   <li><code>Grid</code>: 支持获取 <code>css vars</code> 做响应式判断</li> 
   <li><code>Icon</code>: 支持自定义 <code>Url</code></li> 
   <li><code>Slider</code>: <code>label</code> 支持 <code>function</code> 自定义渲染</li> 
   <li><code>Form</code>: 支持 <code>showErrorMessage API </code> & help 支持 <code>Tnode</code> 类型</li> 
   <li><code>FormItem</code>: 兼容包裹 <code>upload</code> 组件时未传入 <code>initialData</code> 场景</li> 
  </ul> 
  <p>详情见：<a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2FTencent%2Ftdesign-react%2Freleases%2Ftag%2F0.28.0" target="_blank">https://github.com/Tencent/tdesign-react/releases/tag/0.28.0</a></p> 
  <h3><strong>Miniprogram for WeChat 发布 </strong><a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2FTencent%2Ftdesign-miniprogram%2Freleases%2Ftag%2F0.6.2" target="_blank"><strong>0.6.2 版</strong></a></h3> 
  <ul> 
   <li><code>Button</code>:兼容不支持 <code>wx://form-field-button</code> 的版本、修正 <code>type</code> 属性的正确实现</li> 
   <li>修复在 <code>form</code> 下无法获取值的问题</li> 
   <li><code>Upload</code>: 修复关闭按钮层级过低的问题</li> 
   <li><code>Toast</code>: 修复层级过低的问题</li> 
   <li><code>Rate</code>: 修复 <code>iOS</code> 下颜色失效的问题</li> 
   <li><code>Button</code>: 新增 <code>customDataset</code> 属性，可通过 <code>event.currentTarget.dataset.custom</code> 获取</li> 
   <li><code>Upload</code>: 支持对图片和视频的同时上传</li> 
  </ul> 
  <p>详情见：<a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2FTencent%2Ftdesign-miniprogram%2Freleases%2Ftag%2F0.6.2" target="_blank">https://github.com/Tencent/tdesign-miniprogram/releases/tag/0.6.2</a></p> 
  <h3><strong>Miniprogram for WeChat 发布 </strong><a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2FTencent%2Ftdesign-miniprogram%2Freleases%2Ftag%2F0.7.0" target="_blank"><strong>0.7.0 版</strong></a></h3> 
  <ul> 
   <li><code>Image</code>:属性 <code>load-failed</code> 变更为 <code>error</code>；属性 <code>lazy-load</code> 变更为 <code>lazy</code>，⚠️存在不兼容更新</li> 
   <li><code>Button</code>: 样式调整</li> 
   <li><code>Tag</code>: 修复样式文件冗余的问题</li> 
   <li><code>Steps</code>: 修复样式文件冗余的问题</li> 
   <li><code>Image</code>: 新增 <code>shape</code> 属性</li> 
  </ul> 
  <p>详情见：<a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2FTencent%2Ftdesign-miniprogram%2Freleases%2Ftag%2F0.7.0" target="_blank">https://github.com/Tencent/tdesign-miniprogram/releases/tag/0.7.0</a></p> 
  <h3><strong>Vue3 for Mobile 发布 </strong><a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2FTencent%2Ftdesign-mobile-vue%2Freleases%2Ftag%2F0.8.0" target="_blank"><strong>0.8.0 版</strong></a></h3> 
  <ul> 
   <li><code>dropdown-menu</code>: 移除冗余的 <code>dom</code> 结构</li> 
   <li><code>search</code>: 修复样式丢失问题</li> 
   <li><code>input</code>：修复输入框样式丢失问题</li> 
   <li><code>grid</code>： 修复 <code>grid-item</code> 样式丢失问题</li> 
   <li>新增 <code>pull-down-refresh</code> 组件</li> 
  </ul> 
  <p>详情见：<a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2FTencent%2Ftdesign-mobile-vue%2Freleases%2Ftag%2F0.8.0" target="_blank">https://github.com/Tencent/tdesign-mobile-vue/releases/tag/0.8.0</a></p> 
  <h2><strong>设计资源</strong></h2> 
  <h3><strong>Figma 组件库优化 </strong><a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Ftdesign.tencent.com%2Fsource" target="_blank"><strong>1.0.6 版</strong></a></h3> 
  <ul> 
   <li><code>InputNumber</code>：修复递增递减按钮位置问题</li> 
   <li><code>Icon</code>：修复<code>star-filled </code>倒角问题</li> 
  </ul> 
  <p>详情见：<a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Ftdesign.tencent.com%2Fsource" target="_blank">https://tdesign.tencent.com/source</a></p> 
  <h3><strong>Axure 组件库优化 </strong><a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Ftdesign.tencent.com%2Fsource" target="_blank"><strong>1.0.3 版</strong></a></h3> 
  <ul> 
   <li>新增常用小工具，方便用户编辑交互标记与说明</li> 
   <li>优化列表呈现方式，重新编组</li> 
   <li>优化<code>Table</code> 实现逻辑，使用 <code>Axure</code> 原生表格和矩形两种方式实现，方便修改和编辑</li> 
  </ul> 
  <p>详情见：<a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Ftdesign.tencent.com%2Fsource" target="_blank">https://tdesign.tencent.com/source</a></p> 
  <p>更新公告：<a href="https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2FTencent%2Ftdesign%2Freleases%2Ftag%2Fv.2022.3.20" target="_blank">https://github.com/Tencent/tdesign/releases/tag/v.2022.3.20</a></p> 
 </div> 
</div>
                                        </div>
                                      
</div>
            
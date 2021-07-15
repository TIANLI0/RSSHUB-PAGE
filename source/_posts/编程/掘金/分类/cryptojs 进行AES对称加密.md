
---
title: 'cryptojs 进行AES对称加密'
categories: 
 - 编程
 - 掘金
 - 分类
headimg: 'https://picsum.photos/400/300?random=3622'
author: 掘金
comments: false
date: Wed, 14 Jul 2021 22:25:13 GMT
thumbnail: 'https://picsum.photos/400/300?random=3622'
---

<div>   
<div class="markdown-body"><style>.markdown-body&#123;word-break:break-word;line-height:1.75;font-weight:400;font-size:15px;overflow-x:hidden;color:#333&#125;.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6&#123;line-height:1.5;margin-top:35px;margin-bottom:10px;padding-bottom:5px&#125;.markdown-body h1&#123;font-size:30px;margin-bottom:5px&#125;.markdown-body h2&#123;padding-bottom:12px;font-size:24px;border-bottom:1px solid #ececec&#125;.markdown-body h3&#123;font-size:18px;padding-bottom:0&#125;.markdown-body h4&#123;font-size:16px&#125;.markdown-body h5&#123;font-size:15px&#125;.markdown-body h6&#123;margin-top:5px&#125;.markdown-body p&#123;line-height:inherit;margin-top:22px;margin-bottom:22px&#125;.markdown-body img&#123;max-width:100%&#125;.markdown-body hr&#123;border:none;border-top:1px solid #ddd;margin-top:32px;margin-bottom:32px&#125;.markdown-body code&#123;word-break:break-word;border-radius:2px;overflow-x:auto;background-color:#fff5f5;color:#ff502c;font-size:.87em;padding:.065em .4em&#125;.markdown-body code,.markdown-body pre&#123;font-family:Menlo,Monaco,Consolas,Courier New,monospace&#125;.markdown-body pre&#123;overflow:auto;position:relative;line-height:1.75&#125;.markdown-body pre>code&#123;font-size:12px;padding:15px 12px;margin:0;word-break:normal;display:block;overflow-x:auto;color:#333;background:#f8f8f8&#125;.markdown-body a&#123;text-decoration:none;color:#0269c8;border-bottom:1px solid #d1e9ff&#125;.markdown-body a:active,.markdown-body a:hover&#123;color:#275b8c&#125;.markdown-body table&#123;display:inline-block!important;font-size:12px;width:auto;max-width:100%;overflow:auto;border:1px solid #f6f6f6&#125;.markdown-body thead&#123;background:#f6f6f6;color:#000;text-align:left&#125;.markdown-body tr:nth-child(2n)&#123;background-color:#fcfcfc&#125;.markdown-body td,.markdown-body th&#123;padding:12px 7px;line-height:24px&#125;.markdown-body td&#123;min-width:120px&#125;.markdown-body blockquote&#123;color:#666;padding:1px 23px;margin:22px 0;border-left:4px solid #cbcbcb;background-color:#f8f8f8&#125;.markdown-body blockquote:after&#123;display:block;content:""&#125;.markdown-body blockquote>p&#123;margin:10px 0&#125;.markdown-body ol,.markdown-body ul&#123;padding-left:28px&#125;.markdown-body ol li,.markdown-body ul li&#123;margin-bottom:0;list-style:inherit&#125;.markdown-body ol li .task-list-item,.markdown-body ul li .task-list-item&#123;list-style:none&#125;.markdown-body ol li .task-list-item ol,.markdown-body ol li .task-list-item ul,.markdown-body ul li .task-list-item ol,.markdown-body ul li .task-list-item ul&#123;margin-top:0&#125;.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul&#123;margin-top:3px&#125;.markdown-body ol li&#123;padding-left:6px&#125;.markdown-body .contains-task-list&#123;padding-left:0&#125;.markdown-body .task-list-item&#123;list-style:none&#125;@media (max-width:720px)&#123;.markdown-body h1&#123;font-size:24px&#125;.markdown-body h2&#123;font-size:20px&#125;.markdown-body h3&#123;font-size:18px&#125;&#125;</style><p><strong>加解密的双方使用同一个密钥，密钥不能在网络中传输，避免被拦截。 如果要传输，必须要对密钥进行非对称加密再加密一次。</strong></p>
<p>1、npm install crypto-js
2、新建util工具类</p>
<pre><code class="copyable">//引用AES源码js
import CryptoJS from 'crypto-js'

const key = CryptoJS.enc.Utf8.parse("1234123412ABCDEF");//十六位十六进制数作为密钥
const iv = CryptoJS.enc.Utf8.parse('ABCDEF1234123412');//十六位十六进制数作为密钥偏移量

//解密方法
function Decrypt(word) &#123;
   //返回的是解密后的对象
   let decrypt = CryptoJS.AES.decrypt(restoreBase64,key,&#123;
        iv:iv,
        mode:CryptoJS.mode.CBC,
        padding:CryptoJS.pad.Pkcs7
   &#125;);

   //将解密对象转换成UTF8的字符串
   let decryptedStr = decrypt.toString(CryptoJS.enc.Utf8);
   //返回解密结果
   return decryptedStr.toString();
&#125;

//加密方法
function Encrypt(word)&#123;
    let srcs = CryptoJS.enc.Utf8.parse(word);
    //CipherOption,加密的一些选项：
    //mode:加密模式，可取值（CBC,CFB,CTR,CTRGladman,OFB,ECB),都在CryptoJS.mode对象下
    //padding:填充方式，可取值（Pkcs7,Ansix923,Iso10126,ZeroPadding,NoPadding),都在CryptoJS.pad对象下
    //iv:偏移量，mode===ECB时，不需要iv
    //返回的是一个加密对象
    let encrypted = CryptoJS.AES.encrypt(srcs,key,&#123;
        iv:iv,
        mode:CryptoJS.mode.CBC,
        padding:CryptoJS.pad.Pkcs7
    &#125;);
    //将结果进行base64加密
    return encrypted.ciphertext.toString(CryptoJS.enc.Base64);
&#125;

export &#123;Decrypt,Encrypt&#125;
<span class="copy-code-btn">复制代码</span></code></pre>
<p>3、</p>
<pre><code class="copyable">import &#123;Encrypt&#125; from "../../utils/secret";
var userName = Encrypt(this.userName)//加密用户名
var userPassword = Encrypt(this.password)//加密用户密码
console.log('加密后：',userName)
console.log('加密后：',userPassword)
<span class="copy-code-btn">复制代码</span></code></pre></div>  
</div>
            
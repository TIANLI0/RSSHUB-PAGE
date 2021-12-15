
---
title: '【sudoswap发布漏洞事件分析：与0x合约无关，原因在于transferFrom函数漏洞】12月15日消息，NFT交易平台sudoswap针对昨日的漏洞事件发布故障分析，称此次漏洞事...'
categories: 
 - 新媒体
 - 金色财经
 - 快讯
headimg: 'https://picsum.photos/400/300?random=4089'
author: 金色财经
comments: false
date: Invalid Date
thumbnail: 'https://picsum.photos/400/300?random=4089'
---

<div>   
【sudoswap发布漏洞事件分析：与0x合约无关，原因在于transferFrom函数漏洞】12月15日消息，NFT交易平台sudoswap针对昨日的漏洞事件发布故障分析，称此次漏洞事件与0x合约无关，原因在于EtherOrcNFT合约未完全遵守ERC721标准，在调用transferFrom(addressfrom,addressto,uint256id)函数时，from参数对应地址不会被系统检查是否拥有指定的NFTid，而该漏洞可被部分机器人程序利用。sudoswap表示，部分用户尝试将自己的EtherOrcNFT换成WETH时遭到机器人程序利用函数漏洞领跑，未能及时收到WETH，sudoswap已其进行补偿。同时，该事件与0x没有关联，昨日对0x合约的停用实属误会。 
此前报道，北京时间12月14日12:30，NFT交易平台sudoswap宣布发现漏洞，称用户在sudoswap调用0x交易平台的swap功能时可能出现问题。对此，sudoswap暂时将与0x相关的swap功能停用，并提醒用户解除对0x平台的合约授权。  
</div>
            
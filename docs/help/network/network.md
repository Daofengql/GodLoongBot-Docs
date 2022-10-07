## 指令一览

本功能核心命令前缀 `net `

指令和各个参数之间以空格分离，部分指令严格遵从空格分离机制

举几个正确的例子：

1. net -ping 127.0.0.1
2. net -tcping 127.0.0.1 80
3. net -dns www.baidu.com

下面是目前已经开放的所有参数

使用时请使用 `net + 功能参数（+可选参数）` 的方式来调用神麟

|功能参数|效果|是否有子参数|子参数内容|说明|
|---|-------------|----|----|-----------------------|
|[-ping](#ping)|返回一张图片，包含目标地址的延迟信息，物理位置|是| 目标地址 |为了缓解服务器压力，每次查询的结果都将缓存五分钟，五分钟内显示的均为同一图片|
|[-tcping](#tcping)|返回一张图片，包含以TCP链接目标地址端口的延迟信息，物理位置|是| 目标地址 + 空格 + 目标端口 |为了缓解服务器压力，每次查询的结果都将缓存五分钟，五分钟内显示的均为同一图片|
|[-dns](#dns)|返回一张图片，包含目标地址的解析信息|是| 目标地址 + (可选)客户端ip |为了缓解服务器压力，每次查询的结果都将缓存五分钟，5分钟内显示的均为同一图片|
|[-whois](#whois)|返回一张图片，包含目标域名的whois信息|是| 目标域名 |为了缓解服务器压力，每次查询的结果都将缓存十个小时，十个小时内显示的均为同一图片|


### ping { #ping }

指令和各个参数之间以空格分离，部分指令严格遵从空格分离机制

举几个正确的例子：

1. net -ping 127.0.0.1
2. net -ping baidu.com

错误例子

1. net -ping 288.888.888.888   `非标准IPv4划分`
2. net -ping https://baidu.com/  `不需要使用协议头以及URI`
3. net -ping fe80::d553:16d2:f59e:558e%16  `暂不支持IPv6协议栈`

=== ":octicons-check-circle-fill-16: ping成功效果"

    如图，如果神麟不存在服务异常或账号临时被风控的情况下，默认返回一张ping信息
    [![content.tabs.link success_ping]][content.tabs.link success_ping]

=== ":octicons-skip-16: ping失败效果"
    
    如图，如果神麟不存在服务异常或账号临时被风控的情况下，默认返回一张ping信息
    [![content.tabs.link faild_ping]][content.tabs.link faild_ping]

  [content.tabs.link success_ping]: ../../assets/images/success_ping.jpg
  [content.tabs.link faild_ping]: ../../assets/images/faild_ping.jpg

  
### tcping { #tcping }

指令和各个参数之间以空格分离，部分指令严格遵从空格分离机制

举几个正确的例子：

1. net -tcping 127.0.0.1 80
2. net -tcping baidu.com 443

错误例子

1. net -tcping 288.888.888.888 80   `非标准IPv4划分`
2. net -tcping https://baidu.com/  80 `不需要使用协议头以及URI`
3. net -tcping fe80::d553:16d2:f59e:558e%16  80`暂不支持IPv6协议栈`
4. net -tcping 127.0.0.1 11111111   `非规定1-65535端口范围`



=== ":octicons-check-circle-fill-16: tcping成功效果"

    如图，如果神麟不存在服务异常或账号临时被风控的情况下，默认返回一张tcping信息
    [![content.tabs.link success_tcping]][content.tabs.link success_tcping]

=== ":octicons-skip-16: tcping失败效果"
    
    如图，如果神麟不存在服务异常或账号临时被风控的情况下，默认返回一张tcping信息
    [![content.tabs.link faild_tcping]][content.tabs.link faild_tcping]

  [content.tabs.link success_tcping]: ../../assets/images/success_tcping.jpg
  [content.tabs.link faild_tcping]: ../../assets/images/faild_tcping.jpg


### dns { #dns }

指令和各个参数之间以空格分离，部分指令严格遵从空格分离机制

举几个正确的例子：

1. net -dns www.baidu.com
2. net -dns www.baidu.com 114.114.114.114

错误例子

1. net -dns 1.0.0.0   `无法查询ip`
2. net -dns https://baidu.com/`不需要使用协议头以及URI`



=== ":octicons-check-circle-fill-16: dns查询成功效果"

    如图，如果神麟不存在服务异常或账号临时被风控的情况下，默认返回一张dns信息
    [![content.tabs.link success_dns]][content.tabs.link success_dns]

=== ":octicons-skip-16: dns查询失败效果"
    
    如图，如果神麟不存在服务异常或账号临时被风控的情况下，默认返回一张dns信息
    [![content.tabs.link faild_dns]][content.tabs.link faild_dns]

  [content.tabs.link success_dns]: ../../assets/images/success_dns.jpg
  [content.tabs.link faild_dns]: ../../assets/images/faild_dns.jpg



### whois { #whois }

指令和各个参数之间以空格分离，部分指令严格遵从空格分离机制

举几个正确的例子：

1. net -whois baidu.com
2. net -whois qq.com

错误例子

1. net -whois www.baidu.com   `无法查询子域名`
2. net -whois https://baidu.com/`不需要使用协议头以及URI`



=== ":octicons-check-circle-fill-16: whois查询成功效果"

    如图，如果神麟不存在服务异常或账号临时被风控的情况下，默认返回一张whois信息
    [![content.tabs.link success_whois]][content.tabs.link success_whois]

=== ":octicons-skip-16: whois查询失败效果"
    
    如图，如果神麟不存在服务异常或账号临时被风控的情况下，默认返回一张whois信息
    [![content.tabs.link faild_whois]][content.tabs.link faild_whois]

  [content.tabs.link success_whois]: ../../assets/images/success_whois.jpg
  [content.tabs.link faild_whois]: ../../assets/images/faild_whois.jpg

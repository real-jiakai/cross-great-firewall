# 🤲 GFW的相关介绍

### 什么是墙

GFW(Great Firewall)：防火长城

### 设立墙的目的

* 分析和过滤境外咨询和互相访问。
* 过滤国外反动信息，维护国家统一和稳定。

视频参考

[B站张维为教授的视频讲解](https://www.bilibili.com/video/BV1ZS4y1g7dM?spm\_id\_from=333.1007.top\_right\_bar\_window\_custom\_collection.content.click)

油管张维为教授的视频讲解：

{% embed url="https://www.youtube.com/watch?t=0s&v=eLJ4Wyuk-ug" %}

### 设立GFW的导火索

08年前奥运会前夕，恐怖组织在脸书上策划、协调，并实施了对我国西部地区的一个恐怖袭击。中国政府要求脸书配合审查，以防再次出现此类事件。但是被脸书以尊重、保护用户隐私给拒绝了。与此同时，谷歌也以同样的理由拒绝了中国政府的审查要求【注：脸书和谷歌也有难言之隐】。于是，中国大陆政府不让这些不愿意配合的外国公司在中国开展业务。

### GFW的工作原理

* 1\)关键词阻断【TLS出现后，这种阻断方式失效】
* 2\)DNS污染【DNS解析通过加密方式传输后，此阻断方式也可以被避免】
* 3\)IP地址黑名单
* 4\)SNI检测
* 5\)端口阻断

GFW的探测，大多都是在过墙的加密流量中探测到的。

GFW的探测原理，简单来说分为两种，被动式和主动式。

被动式指的是GFW观察连接中传输的内容是不是符合某种特征，如果是的话，就把连接中断，或者把你的服务器IP地址列入黑名单。

采用主动式的探测手段，主动地发起一个去往你服务器的连接，然后通过一些编造出来的数据来判断返回的信息，就知道你的这个服务器是不是在跑Shadowsocks服务。

GFW封锁网络，不会去解密你的加密流量，而是通过各种方式去判断你流量的意图。

> TLS是什么？
>
> 传输层安全协议【Transport Layer Security】
>
> 如何证明TLS是否开启？
>
> 判断网址前缀是以https开头还是以http开头，如果网址前缀是以https开头，则证明TLS开启。

cf文档：

[什么是TLS？](https://www.cloudflare.com/zh-cn/learning/ssl/transport-layer-security-tls/)

[什么是SNI？](https://www.cloudflare.com/zh-cn/learning/ssl/what-is-sni/)

### 设立GFW的好处

* 保护我国互联网企业的发展
* 保护我国的社会和谐【维稳】
* 降低了国民被外界消息洗脑的可能性
* 维护国家利益

### 设立GFW的弊端

* 愚化民众【非精英群体成为井底之蛙】
* 不符合WTO和相关法律法规的要求

# ☝ 协议分析

### Shadowsocks协议

继VPN这种曾经的主流翻墙手段被确认能被GFW精准识别和封锁后 ，后面的一切代理服务器中转的这种翻墙方式，包括SSR、V2ray、Trojan这些的始祖。

Shadowsocks协议目前拥有着最快的RTT，也就是通讯延迟，因为数据包在握手的时候用时最短。V2ray、Trojan在机制的限制下，RTT次数一定比Shadowsocks要多。

Shadowsocks协议因其机制问题，目前还是体验最好、最简单、最快速、极度体现暴力美学的中转代理方式。

Shadowsocks的安全性存在一定风险，但目前依然是翻墙的主流方式。依然适合绝大多数机场用户使用。

### ShadowsocksR协议

Shadowsocks的优化版，并非是由同一个作者开发。

### V2ray【VPS用户优先选择】

V2ray的安全性综合来看更高，部署复杂。因为机制的问题，导致握手的次数相比Shadowsocks更多。

加解密的性能方面，由于V2ray原创的Vmess协议+TLS两次加密，CPU占用对比Shadowsocks更高，不太适合部署在路由器和一些老旧的CPU型号的手机上，但适合软路由。

虽然流量没有明显的特征，但如果GFW主动探测就会发现，流量的目的是没有任何一个网站，这反而成了其明显的特征。很多人在V2ray服务外面加一层真的网站作为掩护，伪装流量，这就是V2ray+Websocket+TLS+Web的原理。

相比Shadowsocks，V2ray的确在安全性和对抗GFW的封锁的能力上要强一些，但依然不是绝对的安全。

优点

* 弹性大
* 功能多
* 支持的协议和算法多

缺点

* 部署起来难度大
* 多次加密解密延迟相对较高
* 对设备算力要求高

### Trojan

解决V2ray的一些缺点【复杂部署难度大，加密解密延迟高】，但是翻墙的核心原理还是借鉴了Websocket+TLS，

Trojan走的是轻量化的解决方案，Trojan在V2ray的Vmess和TLS的两层加密结构里，剥离了一层Vmess的加密协议，只用到了TLS。

优点

* 速度较V2ray快

缺点

* 弹性差
* 多平台兼容性较V2ray差
* 不支持反代理

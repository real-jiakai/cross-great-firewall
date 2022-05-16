# 👋 内网线路

### 什么是内网？

数据通过内部网络传输，不转到公网。

### 内网线路【仅仅是跨境这一段】的介绍

内网线路包括IPLC（International Private Leased Circuit）、IEPL（International Ethernet Private Line）线路。

IPLC是通过物理层把两个点互相连接组成的局域网；IEPL是通过数据链路层连接点对点或者是多点对多点连接起来的局域网。

IPLC和IEPL组的都是内网。通过内网想要连接互联网还需要一个额外的步骤—把数据转发到公网。

IPLC是纯粹的物理层传输电路，技术实现上是通过【TDM，Time Division Multiplexing，时分复用】实现的数据传输，通过极低的时间差来区分不同的用户和业务数据。本质上是需要依赖一个路由器的。

IEPL是纯粹的以太网电路，通过设备间的MAC地址通讯，少了一层路由设备，相比IPLC，延迟能做到更低，由TDM导致的抖动也会减小。

### 内网线路的优点和缺点

优点

* 延迟低【没有额外的跳发】
* 稳定性和可靠性高【专线用的人少，不受公网影响】
* 不受到审查【不一定安全】

缺点

* 价格

内网线路在过境时，可以理解为近乎零跳发。比163和CN2线路强很多。

<mark style="background-color:purple;">内网的优点仅仅体现在过境的那一段而已。</mark>

IPLC对我们而言最大的意义是出境方式稳定可靠。

### 如何甄别一个机场的好坏

区别机场好坏的一个重点就是机场有没有技术能力，能把客户的数据在送入内网线路之前的这条通道优化好。

### AK视频中提及的机场和VPS厂商【不是推荐】

薯条、Rixcloud、魅影、BlinkLoad、海豚湾、佩奇、Boslife、AAEX

Bandwagon、DigitalOcean、Linode

挑选机场可以参照duyao大佬的[博客](https://www.duyaoss.com/)

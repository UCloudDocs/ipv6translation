# 原理架构

{{indexmenu_n>1}}

![](/images/introduction/nat64架构.png)

POP点即UCloud的互联网接入点，IPv6流量通过POP点进入UCloud内部网络并发送至NAT64网关集群。NAT64网关集群是一组基于VPP开发的，实现IPv6流量到IPv4流量转换的高性能服务集群，并利用ECMP+BGP实现高可用。NAT64网关集群完成转换后，将IPv4流量送至UCloud边界路由器。所有IPv4流量将由UCloud边界路由器分发给各可用区的云资源。NAT64网关集群维护一张IPv6连接至IPv4连接的映射表，云资源的回包通过映射重新转换为IPv6流量并回送至客户端。

但该服务仅支持入向流量转换，不支持云资源主动访问外部IPv6服务。

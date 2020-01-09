### 抓包

* 捕获过滤器
  * host xx.xx.xx.xx
  * tcp(或udp) port xxx
    * 特殊：port http
  * port xxx
  * ip
  * ip6
* 显示过滤器
  * ip.addr == xx.xx.xx.xx
  * tcp.port == xxx
  * not arp
  * http
  * tcp(或udp)
  * ip
  * ipv6

### 交换机

* 设置ip地址：ip address 地址 掩码
* 配置为镜像端口：monitor session 1 destination interface 端口(如fa0/1)
  * 关闭：no monitor session 1 destination interface 端口
* 增加vlan2：config terminal，vlan 2
* 端口加入vlan2：interface xxx, switchport access vlan 2
* 端口配置为VLAN Trunk 模式：(config-if) switchport mode trunk
* 打开、关闭VLAN 的STP：(no) spanning-tree vlan ID
* 设置优先级：interface 端口, spanning-tree vlan 1 port-priority 16

### 三层交换机

* 创建子接口：例如 interface e0/1**.1**
* 配置子接口所属的VLAN：encapsulation dot1q VLAN 编号
* 查看路由表：show ip route
* 给VLAN 接口配置IP 地址：interface vlan 编号, ip address IP MASK
* 在三层交换机上启用路由功能：ip routing

### 静态路由配置

* DHCP服务
  * 定义子网的DHCP 地址池：ip dhcp pool 地址池编号
  * 定义DHCP 网络地址：network IP地址/子网掩码长度 (如network 172.16.1.0/24)
  * 定义DHCP 默认网关：default-router 默认路由器IP 地址
  * 启动DHCP 服务：service dhcp
  * 动态分配IP地址：ip addess dhcp
* 配置静态路由：ip route 目标网络 子网掩码 下一跳地址
  * 设置距离：ip route 目标网络 子网掩码 下一跳地址 距离
  * 测试连通性：ping 目标IP地址 source 源IP地址
  * 持续ping：ping IP -t
  * 默认路由设置：ip route 0.0.0.0 0.0.0.0 默认路由器IP地址
* NAT服务
  * 定义内部接口：interface fa0/1, ip nat inside
  * 定义外部接口：interface fa0/0，ip nat outside
  * 设置访问控制列表：access-list 1 permit 192.168.0.0 0.0.0.255 (允许192.168.0.0/24向外访问)

### OSPF

##### RIP命令

* 启用RIP：`Router(config)# router rip`
* 将路由器各接口（子网）加入路由宣告：`Router(config-router)# network <ip_net>`

##### OSPF命令

* 给路由器的回环接口配置地址

  ```
  Router(config)# interface loopback 0
  Router(config-if)# ip address <ip> <mask>
  ```

* 在路由器上启用OSPF 协议：`Router(config)# router ospf <process-id>`
* 配置路由器接口（子网）所属Area ID：
  `Router(config-router)# network <ip_net> <mask(反过来)> area <area-id>`
  e.g. `network 20.3.0.0 0.0.255.255 area 1`
* 查看路由器的OSPF 数据库（可以查看Router ID）：`Router# show ip ospf database`
* 手工指定Router ID：`Router(config-router)# router-id x.x.x.x`
  * 需要重启路由器：`Router# reload`
  * 或清除OSPF状态：`Router# clear ip ospf process`
* 观察各路由器的OSPF 邻居关系，在广播网络中，为减少通信量，会自动选出一个DR（Designated Router）和一个BDR（Backup Designated Router）,其他路由器只与DR、BDR 成为邻接关系，查看：`Router# show ip ospf neighbor detail`
* 观察路由器的OSPF 接口状态：`Router# show ip ospf interface`
* 在两个区域边界路由器之间建立虚链路，\<area-id>填写用于传递数据的区域ID，\<router ID>分别设为对方的Router ID：
  `Router(config-router)# area <area-id> virtual-link <router ID>`
* 在区域边界路由器上手工进行路由合并：
  `Router(config-router)# area <area-id> range <ip_net> <mask>`
* Cost: 100M / 接口带宽
  * 选路：cost最小的

### BGP

* 在路由器 R1 上启用 BGP 协议 , 设置 AS 号，并宣告直连网络： 

  ```
  R1(config)# router bgp <AS-Number>
  R1(config-router)# network x.x.x.x mask x.x.x.x (不反)
  ```

  * 如`router bgp 65003; network 192.168.34.0 mask 255.255.255.0 `

* 把对方增加为AS内部的邻居（AS-Number设置为相同的AS号）
  `R1(config-router)# neighbor <IP-Address> remote-as <AS-Number>`

* 对方增加为AS间的邻居（IP-Address为对方IP (如回环口IP)，AS-Number设置为对方的AS号）
  `R1(config-router)# neighbor <IP-Address> remote-as <AS-Number>`

* 查看邻居关系：`R1# show ip bgp neighbor`

* 查看BGP数据库：`R1# show ip bgp`

* 启用BGP同步功能：`R1(config-router)# synchronization`

* 设置BGP更新源为回环接口（IP-Addr设置为对方的回环口IP）:
  `R1(config-router)# neighbor <IP-Addr> update-source loopback 0`

* 在BGP中启用路由重分发功能，从OSPF中重分发路由信息：

  ```
  R1(config)# router ospf <process-id> 
  R1(config-router)# redistribute bgp <AS-Number> subnets
  ```

* 聚合路由（summary-only参数的含义是只传递聚合后的路由，as-set参数的含义是在传播网络时加上AS属性，避免出现循环路由）：
  `R1(config-route)# aggregate-address <ip network> <subnet mask> summary-only as-set`

* 设置允许多条路径：`R1(config-route)# maximum-paths 2`

* 选路：过AS最少的




# VMware 中的三种网路连接模式
> [Understanding Virtual Networking Components](https://docs.vmware.com/en/VMware-Workstation-Pro/16.0/com.vmware.ws.using.doc/GUID-8FDE7881-C31F-487F-BEF3-B2107A21D0CE.html)
> [What is the difference between NAT / Bridged / Host-Only networking?](https://superuser.com/questions/227505/what-is-the-difference-between-nat-bridged-host-only-networking)
> [VMware Virtual Networking Concepts](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/techpaper/virtual_networking_concepts.pdf)
> [理解 VMware 网络模式：桥接、仅主机和 NAT](https://www.junmajinlong.com/virtual/network/vmware_net/)
> [Vmware—桥接、NAT以及仅主机模式的详细介绍和区别](https://zhuanlan.zhihu.com/p/532535216)


![](img/2023-03-28-15-16-40.png)



vmware 三种网络模型对应的三种虚拟交换机

|Network Type|Switch Name|
|:--:|:--:|
|Bridged|VMnet0|
|NAT|VMnet8|
|Host-only|VMnet1|


![](img/2023-03-28-15-32-54.png)
![](img/2023-03-28-15-33-36.png)


## 桥接模式（Bridged）
> [Configuring Bridged Networking](https://docs.vmware.com/en/VMware-Workstation-Pro/17/com.vmware.ws.using.doc/GUID-BAFA66C3-81F0-4FCA-84C4-D9F7D258A60A.html)


- 默认模式，在自己物理主机上的虚拟网卡名为 VMnet0
- DHCP 服务会自动识别 VM 并分配一个和物理主机在同一个子网的 IP 地址

## NAT
> [Configuring Network Address Translation](https://docs.vmware.com/en/VMware-Workstation-Pro/17/com.vmware.ws.using.doc/GUID-89311E3D-CCA9-4ECC-AF5C-C52BE6A89A95.html)


- NAT 是网络地址转换（network address translation），物理主机上的虚拟网卡名为 VMnet8
- 使用 VMnet8 的虚拟机通过 NAT 连接到主机的网络适配器，可以通过物理主机连接到外部互联网

## 仅主机（host-only）
> [Configuring Host-Only Networking](https://docs.vmware.com/en/VMware-Workstation-Pro/17/com.vmware.ws.using.doc/GUID-93BDF7F1-D2E4-42CE-80EA-4E305337D2FC.html)


- 物理主机上的虚拟网卡名为 VMnet1
- 构建一个孤立的网络环境，即虚拟机仅能和物理主机通信，不能和外部网络通信
- 虚拟机用的是专用网络地址，因此和外部无法通信，仅对主机可见
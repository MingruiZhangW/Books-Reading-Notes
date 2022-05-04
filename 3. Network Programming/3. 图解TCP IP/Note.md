# 图解 TCP/IP

## 1. Basics

- WAN / LAN - page. 20

> The difference between internet and ethernet is that the internet is a wide area network (WAN) while the **ethernet (以太网)** is a local area network (LAN). Internet is a worldwide large network that connects a large number of devices around the world while ethernet is a network that covers a small geographical area.

- Ethernet - page. 106

- OSI (Open Systems Interconnection model) - page. 37

- General cast type (e.g. unicast) - page. 49

> IP 地址 比 MAC 地址 更有***层次性***, 可以更加快速的定位

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/1.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/2.png?raw=true" />
</p>

> Network hardware (e.g. router, switch) - page. 54

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/3.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/4.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/5.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/6.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/7.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/8.png?raw=true" />
</p>

> Bandwidth

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/9.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/10.png?raw=true" />
</p>

## 2. TCP/IP Basics

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/11.png?raw=true" />
</p>

> The structure of Internet

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/12.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/13.png?raw=true" />
</p>

- General info for TCP/IP protocols - page. 81

1. FTP

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/14.png?raw=true" />
</p>

2. SSH

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/15.png?raw=true" />
</p>

3. SNMP

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/16.png?raw=true" />
</p>

- TCP/IP simple flow - page. 87

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/17.png?raw=true" />
</p>

## 3. Data-Link

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/18.png?raw=true" />
</p>

> MAC address

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/19.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/20.png?raw=true" />
</p>

> Full Duplex vs Half Duplex

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/21.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/22.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/23.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/24.png?raw=true" />
</p>

- Switch Forwarding (Forwarding Table) - page. 101

- VLAN - page. 104

## 4. IP - Internet Protocol

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/25.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/26.png?raw=true" />
</p>

### **IP Basics - page. 135**

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/27.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/28.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/29.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/30.png?raw=true" />
</p>

> IP is connectionless

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/31.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/32.png?raw=true" />
</p>

### **IP Address** - page. 141

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/33.png?raw=true" />
</p>

> Broadcast and Multicast Address

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/34.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/35.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/36.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/37.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/38.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/39.png?raw=true" />
</p>

> Subnet & Subnet Mask

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/40.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/41.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/42.png?raw=true" />
</p>

> Public IP vs Private IP Address

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/43.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/44.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/45.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/46.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/47.png?raw=true" />
</p>

### Routing - page. 154

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/48.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/49.png?raw=true" />
</p>

> Loopback Address

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/50.png?raw=true" />
</p>

- IP Fragmentation - page. 157 (Path MTU Discovery) (MTU - Maximum Transmission Unit) 

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/51.png?raw=true" />
</p>

### IPV6 - page. 144

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/52.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/53.png?raw=true" />
</p>

### IPV4 Header - page. 165

### IPV6 Header - page. 170

## 5. IP Related Protocols and Techs

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/54.png?raw=true" />
</p>

### **DNS** - page. 176

- [Note from another source](https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/3.%20Network%20Programming/Note.md#dns)

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/55.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/56.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/57.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/58.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/59.png?raw=true" />
</p>

### **ARP** - page. 182

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/60.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/61.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/62.png?raw=true" />
</p>

### **ICMP** (Internet Control Message Protocol) - page. 182

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/63.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/64.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/65.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/66.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/67.png?raw=true" />
</p>

- **ICMPv6**

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/68.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/69.png?raw=true" />
</p>

### **DHCP** - page. 193

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/70.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/71.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/72.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/73.png?raw=true" />
</p>
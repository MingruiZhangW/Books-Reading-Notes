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

### **NAT** - page. 196

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/74.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/75.png?raw=true" />
</p>

#### **NAPT**

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/76.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/77.png?raw=true" />
</p>

#### **NAT-PT**

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/78.png?raw=true" />
</p>

#### **Problems and Limitations for NAT**

- NAT devices allow the use of private IP addresses on private networks behind routers with a single public IP address facing the Internet. The internal network devices communicate with hosts on the external network by changing the source address of outgoing requests to that of the NAT device and relaying replies back to the originating device.

- This leaves the internal network ill-suited for hosting servers, as the NAT device has no automatic method of determining the internal host for which incoming packets are destined. This is not a problem for general web access and email. However, applications such as **peer-to-peer** file sharing, **VoIP** services, and **video game consoles** ***require clients to be servers as well***. <ins>Incoming requests cannot be easily correlated to the proper internal host.</ins> Furthermore, many of these types of services carry IP address and port number information in the application data, potentially requiring substitution with deep packet inspection.

- Network address translation technologies are not standardized. As a result, the methods used for NAT traversal are often proprietary and poorly documented. Many traversal techniques require assistance from servers outside of the masqueraded network. Some methods use the server only when establishing the connection, while others are based on relaying all data through it, which increases the bandwidth requirements and latency, detrimental to real-time voice and video communications.

- NAT traversal techniques usually bypass enterprise security policies. Enterprise security experts prefer techniques that explicitly cooperate with NAT and firewalls, allowing NAT traversal while still enabling marshalling at the NAT to enforce enterprise security policies. IETF standards based on this security model are Realm-Specific IP (RSIP) and middlebox communications (MIDCOM).

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/79.png?raw=true" />
</p>

#### **NAT traversal**

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/80.png?raw=true" />
</p>

> The following NAT traversal techniques are available:

- ```Socket Secure (SOCKS)``` is a technology created in the early 1990s that uses proxy servers to relay traffic between networks or systems.
- ```Traversal Using Relays around NAT (TURN)``` is a relay protocol designed specifically for NAT traversal.
- ```NAT hole punching``` is a general technique that exploits how NATs handle some protocols (for example, UDP, TCP, or ICMP) to allow previously blocked packets through the NAT.

```
  UDP hole punching
  TCP hole punching
  ICMP hole punching
```

- ```Session Traversal Utilities for NAT (STUN)``` is a standardized set of methods and a network protocol for NAT hole punching. It was designed for UDP but was also extended to TCP.
- ```Interactive Connectivity Establishment (ICE)``` is a complete protocol for using STUN and/or TURN to do NAT traversal while picking the best network route available. It fills in some of the missing pieces and deficiencies that were not mentioned by STUN specification.
- ```UPnP``` ```Internet Gateway Device Protocol (IGDP)``` is supported by many small NAT gateways in home or small office settings. It allows a device on a network to ask the router to open a port.
- ```NAT-PMP``` is a protocol introduced by Apple as an alternative to IGDP.
- ```PCP``` is a successor of NAT-PMP.
- ```Application-level gateway (ALG)``` is a component of a firewall or NAT that allows for configuring NAT traversal filters. It is claimed by numerous people that this technique creates more problems than it solves.

> One solution for NAT traversal, called the ```Internet Gateway Device Protocol (IGD Protocol)```, is ***implemented via UPnP***. Many routers and firewalls expose themselves as Internet Gateway Devices, allowing any local UPnP control point to perform a variety of actions, including retrieving the external IP address of the device, enumerating existing port mappings, and adding or removing port mappings. By adding a port mapping, a UPnP controller behind the IGD can enable traversal of the IGD from an external address to an internal client.

### **IP Tunnel** - page. 200

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/81.png?raw=true" />
</p>

### **IP AnyCast**

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/82.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/83.png?raw=true" />
</p>

- [911](https://en.wikipedia.org/wiki/Enhanced_9-1-1#Wireless_routing])

### **Mobile IP** - page. 207

## 6. TCP and UDP

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/84.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/85.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/86.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/87.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/88.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/89.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/90.png?raw=true" />
</p>

### **UDP**

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/91.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/92.png?raw=true" />
</p>

### **TCP**

- [Note from another source](https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/3.%20Network%20Programming/Note.md#dns)
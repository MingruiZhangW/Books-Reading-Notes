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

- ***NAT does not usually allow connections to be initiated from outside the network***, although you can manually configure the NAT device to set up server connections. The practical result is that some TCP and UDP protocols that require a connection be initiated from the server machine do not work automatically and some might not work at all.

- NAT provides some **firewall protection**. A standard NAT configuration provides basic-level firewall protection because the NAT device can initiate connections from the private NAT network, but devices on the external network usually cannot initiate connections to the private NAT network.

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

- [Note from another source](https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/3.%20Network%20Programming/Note.md#tcp-in-details)

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/93.png?raw=true" />
</p>

### **UDP & TCP Pseudo Header**

- https://www.omnisecu.com/tcpip/udp-pseudo-header.php

**UDP** uses a concept called as **"pseudo header"**. Pseudo header helps to find transfer bit errors and also to protect against other types of network errors like the possibility of IP datagram reaching a wrong host.

Below image contains the UDP header format.

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/94.jpg?raw=true" />
</p>

**Checksum** value is calculated after prepending a pseudo header to actual UDP header and data. "Pseudo header" has many fields from IP header also.

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/95.jpg?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/96.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/97.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/98.png?raw=true" />
</p>

## 7. Routing Protocols

- **Routing protocols** are mechansims by which **routing information is exchanged between routers** so that routing decisions can be made.

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/99.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/100.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/101.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/102.png?raw=true" />
</p>

### **Range of Routing**

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/103.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/104.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/105.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/106.png?raw=true" />
</p>

### **Routing Algorithm and Protocols**

- Routing Algorithms - page. 232

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/107.png?raw=true" />
</p>

- RIP (Routing Infomation Protocol) (IGP) - page. 234

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/108.png?raw=true" />
</p>

- OSPF (Open Shortest Path First) (IGP) - page. 257

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/109.png?raw=true" />
</p>

- BGP (Border Gateway Protocol) (EGP) - page. 262

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/110.png?raw=true" />
</p>

> Routing Protocols are based on Routing Algorithms

## 8. Application Layer Protocols

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/111.png?raw=true" />
</p>

### **SSH**

> The **Secure Shell Protocol (SSH)** is a secure protocol and the most common way of safely administering remote servers. Using a number of encryption technologies, SSH provides a mechanism for establishing a cryptographically secured connection between two parties, authenticating each side to the other, and **passing commands and output back and forth**.

<p align="center" style="font-size: 16px;">
    <b>Understanding Symmetric Encryption, Asymmetric Encryption, and Hashes</b>
</p>

In order to secure the transmission of information, **SSH employs a number of different types of data manipulation techniques at various points in the transaction**. These include forms of **symmetrical encryption**, **asymmetrical encryption**, and **hashing**.

- Symmetrical Encryption

The relationship of the components that encrypt and decrypt data determines whether an encryption scheme is symmetrical or asymmetrical.

***Symmetrical encryption is a type of encryption where one key can be used to encrypt messages to the opposite party, and also to decrypt the messages received from the other participant.*** This means that anyone who holds the key can encrypt and decrypt messages to anyone else holding the key.

This type of encryption scheme is often called **“shared secret” encryption**, or “secret key” encryption. There is typically only a single key that is used for all operations or a pair of keys where the relationship is discoverable and it’s trivial to derive the opposite key.

**Symmetric keys are used by SSH in order to encrypt the entire connection. Contrary to what some users assume, public/private asymmetrical key pairs that can be created are only used for authentication (and set up the symmetrical encryption), not encrypting the connection. The symmetrical encryption allows even password authentication to be protected against snooping.**

The client and server both contribute toward establishing this key, and the resulting secret is never known to outside parties. The secret key is created through a process known as a *key exchange algorithm*. This exchange results in the server and client both arriving at the same key independently by sharing certain pieces of public data and manipulating them with certain secret data. This process is explained in greater detail later on.

The symmetrical encryption key created by this procedure is session-based and constitutes the actual encryption for the data sent between server and client. Once this is established, the rest of the data must be encrypted with this shared secret. **This is done prior to authenticating a client.**

SSH can be configured to use a variety of different symmetrical cipher systems, including ***Advanced Encryption Standard (AES)***, Blowfish, 3DES, CAST128, and Arcfour. The server and client can both decide on a list of their supported ciphers, ordered by preference. The first option from the client’s list that is available on the server is used as the cipher algorithm in both directions.

On Ubuntu 20.04, both the client and the server are defaulted like the following:

```
chacha20-poly1305@openssh.com
aes128-ctr
aes192-ctr
aes256-ctr
aes128-gcm@openssh.com
aes256-gcm@openssh.com
```
This means that if two Ubuntu 20.04 machines are connecting to each other (without overriding the default ciphers through configuration options), they will always default to using the chacha20-poly1305@openssh.com cipher to encrypt their connection. (ChaCha)

- Asymmetrical Encryption

Asymmetrical encryption is different from symmetrical encryption because to send data in a single direction, *two associated keys are needed*. **One of these keys is known as the private key, while the other is called the public key.**

**The public key can be freely shared with any party.** It is associated with its paired key, *but the private key cannot be derived from the public key*. The mathematical relationship between the public key and the private key allows the **public key to encrypt messages that can only be decrypted by the private key.** This is a one-way ability, meaning that the public key has no ability to decrypt the messages it writes, nor can it decrypt anything the private key may send it.

**The private key should be kept entirely secret and should never be shared with another party.** This is a key requirement for the public key paradigm to work. The private key is the only component capable of decrypting messages that were encrypted using the associated public key. By virtue of this fact, any entity capable of decrypting these messages has demonstrated that they are in control of the private key.

**SSH uses asymmetric encryption in a few different places.** During the ***initial key exchange process*** used to ***set up the symmetrical encryption*** (used to encrypt the session), asymmetrical encryption is used. In this stage, both parties produce *temporary key pairs* and exchange the public key in order to produce the shared secret that will be used for symmetrical encryption.

The more well-discussed use of asymmetrical encryption with SSH comes from ***SSH key-based authentication***. **SSH key pairs can be used to authenticate a client to a server.** ***The client creates a key pair and then uploads the public key to any remote server it wishes to access***. This is placed in a file called authorized_keys within the ~/.ssh directory in the user account’s home directory on the remote server.

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/112.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/113.png?raw=true" />
</p>

***After the symmetrical encryption is established to secure communications between the server and client, the client must authenticate to be allowed access. The server can use the public key in this file to encrypt a challenge message to the client. If the client can prove that it was able to decrypt this message, it has demonstrated that it owns the associated private key. Then the server can set up the environment for the client.***

- Hashing

Another form of data manipulation that SSH takes advantage of is **cryptographic hashing**. Cryptographic hash functions are methods of creating a succinct “signature” or summary of a set of information. **Their main distinguishing attributes are that they are never meant to be reversed**, they are virtually impossible to influence predictably, and they are practically unique.

*Using the same hashing function and message should produce the same hash;* modifying any portion of the data should produce an entirely different hash. A user should not be able to produce the original message from a given hash, but they should be able to tell if a given message produced a given hash.

Given these properties, **hashes are mainly used for data integrity purposes and to verify the authenticity of communication**. The main use in SSH is with **HMAC**, or hash-based message authentication codes. These are used to ensure the message text that’s received is intact and unmodified.

As part of the symmetrical encryption negotiation outlined previously, a **message authentication code (MAC) algorithm** is selected. The algorithm is chosen by working through the client’s list of acceptable MAC choices. The first one on this list that the server supports will be used.

Each message sent after the encryption is negotiated must contain a MAC so that the other party can verify the packet integrity. ***The MAC is calculated from the symmetrical shared secret, the packet sequence number of the message, and the actual message content***.

The MAC itself is sent outside of the symmetrically encrypted area as the final part of the packet. Researchers generally recommend this method of encrypting the data first and then calculating the MAC.

<p align="center" style="font-size: 16px;">
    <b>Understanding How SSH Works</b>
</p>

You probably already have a basic understanding of how SSH works. The SSH protocol employs a client-server model to authenticate two parties and encrypt the data between them.

The server component listens on a designated port for connections. It is responsible for negotiating the secure connection, authenticating the connecting party, and spawning the correct environment if the credentials are accepted.

*The client is responsible for beginning the initial transmission control protocol (TCP) handshake with the server, negotiating the secure connection, verifying that the server’s identity matches previously recorded information, and providing credentials to authenticate.*

An SSH session is established in two separate stages.** The first is to agree upon and establish encryption to protect future communication.** **The second stage is to authenticate the user and discover whether access to the server should be granted.**

<p align="center" style="font-size: 16px;">
    <b>Negotiating Encryption for the Session</b>
</p>

When a *TCP connection is made by a client*, the server responds with the protocol versions it supports. If the client can match one of the acceptable protocol versions, the connection continues. **The server also provides its public host key, which the client can use to check whether this was the intended host.**

At this point, both parties negotiate a **session key** using a version of something called the ***Diffie-Hellman algorithm***. This algorithm (and its variants) make it possible for each party to combine their own private data with public data from the other system to arrive at an identical secret session key.

***The session key will be used to encrypt the entire session.*** **The public and private key pairs used for this part of the procedure are completely separate from the SSH keys used to authenticate a client to the server.**

The basis of this procedure for classic Diffie-Hellman are:

- Both parties agree on a large prime number, which will serve as a seed value.
- Both parties agree on an encryption generator (typically AES), which will be used to manipulate the values in a predefined way.
- Independently, each party comes up with another prime number which is kept secret from the other party. This number is used as the private key for this interaction (**different from the private SSH key used for authentication**).
- The generated private key, the encryption generator, and the shared prime number are used to generate a public key that is derived from the private key, but which can be shared with the other party.
- Both participants then exchange their generated public keys.
- The receiving entity uses their own private key, the other party’s public key, and the original shared prime number to ***compute a shared secret key***. Although this is independently computed by each party, using opposite private and public keys, **it will result in the same shared secret key**.
- The **shared secret is then used to encrypt all communication that follows**.

This process allows each party to equally participate in generating the shared secret, which does not allow one end to control the secret. It also accomplishes the task of generating an identical shared secret without ever having to send that information over insecure channels. The shared secret encryption that is used for the rest of the connection is called binary packet protocol.

***The generated secret is a symmetric key***, meaning that the same key used to encrypt a message can be used to decrypt it on the other side. The purpose of this is to wrap all further communication in an encrypted tunnel that cannot be deciphered by outsiders.

**After the session encryption is established, the user authentication stage begins.**

[Key Exchange](https://en.wikipedia.org/wiki/Key_exchange)

<p align="center" style="font-size: 16px;">
    <b>Authenticating the User’s Access to the Server</b>
</p>

The next step involves authenticating the user and deciding on access. There are a few methods that can be used for authentication, based on what the server accepts.

The general method is *password authentication*, which is when the server prompts the client for the password of the account they are attempting to log in with. The password is sent through the negotiated encryption, so it is secure from outside parties.

Even though the password will be encrypted, this method is not generally recommended due to the limitations on the complexity of the password. Automated scripts can break passwords of normal lengths very easily compared to other authentication methods.

The most popular and recommended alternative is the use of ***SSH key pairs***. **SSH key pairs are asymmetric keys, meaning that the two associated keys serve different functions.**

**The public key is used to encrypt data that can only be decrypted with the private key.** The public key can be freely shared, because, although it can encrypt for the private key, there is no method of deriving the private key from the public key.

***Authentication using SSH key pairs begins after the symmetric encryption has been established*** as described in the previous section. The procedure happens as follows:

- The client begins by sending an ID for the key pair it would like to authenticate with to the server.
- The server checks the ```authorized_keys``` file of the account that the client is attempting to log into for the key ID.
- If a public key with a matching ID is found in the file, the server generates a random number and uses the public key to encrypt the number.
- The server sends the client this encrypted message.
- If **the client actually has the associated private key, it will be able to decrypt the message using that key, revealing the original number**.
- The client combines the decrypted number with the shared session key that is being used to encrypt the communication, and calculates the MD5 hash of this value. MD5 is a message-digest algorithm that uses the hash function to generate a 128-bit hash value.
- The client then sends this MD5 hash back to the server as an answer to the encrypted number message.
- The server uses the same shared session key and the original number that it sent to the client to calculate the MD5 value on its own. It compares its own calculation to the one that the client sent back. If these two values match, it proves that the client was in possession of the private key and the client is authenticated.

In sum, the asymmetry of the keys allows the server to encrypt messages to the client using the public key. The client can then prove that it holds the private key by decrypting the message correctly. The two types of encryption that are used (symmetric shared secret and asymmetric public/private keys) are each able to leverage their specific strengths in this model.

From: https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process

### **FTP** - page. 273

### **E-mail** - page. 277

### **WWW** - page. 277

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/114.png?raw=true" />
</p>

- **URI**

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/115.png?raw=true" />
</p>

- **HTML**

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/116.png?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/117.png?raw=true" />
</p>

- **HTTP**

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/118.png?raw=true" />
</p>
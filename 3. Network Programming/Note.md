# NetWork Programming Knowledge

## **基础Flow**

<p align="center" style="color: rgb(2, 30, 170);letter-spacing: 0px;">
    你是一台电脑，你的名字叫 <b><i>A</i></b>
</p>

很久很久之前，你不与任何其他电脑相连接，孤苦伶仃。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_1.png?raw=true" />
</p>

直到有一天，你希望与另一台电脑 ***B*** 建立通信，于是你们各开了一个网口，用一根网线连接了起来。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_2.png?raw=true" />
</p>

用一根网线连接起来怎么就能"通信"了呢？我可以给你讲 IO、讲中断、讲缓冲区，但这不是研究网络时该关心的问题。

如果你纠结，要么去研究一下*操作系统是如何处理网络 IO* 的，要么去研究一下包是如何被网卡转换成电信号发送出去的，要么就仅仅把它当做电脑里有个小人在开枪吧~

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_3.gif?raw=true" />
</p>

反正，你们就是连起来了，并且可以通信。

<p align="center" style="font-size: 16px;color: #83AD9B">
    <b>第一层</b>
</p>

有一天，一个新伙伴***C***加入了，但聪明的你们很快发现，可以每个人开**两个网口**，用一共**三根网线**，彼此相连。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_4.png?raw=true" />
</p>

随着越来越多的人加入，你发现身上开的网口实在太多了，而且网线密密麻麻，混乱不堪。*（而实际上一台电脑根本开不了这么多网口，所以这种连线只在理论上可行，所以连不上的我就用红色虚线表示了，就是这么严谨哈哈~）*

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_5.png?raw=true" />
</p>

于是你们发明了一个中间设备，你们将网线都插到这个设备上，由这个设备做转发，就可以彼此之间通信了，本质上和原来一样，只不过网口的数量和网线的数量减少了，不再那么混乱。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_6.png?raw=true" />
</p>

你给它取名叫**集线器**，它仅仅是无脑将电信号转发到所有**出口（广播）**，不做任何处理，你觉得它是没有智商的，因此把人家定性在了***物理层***。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_7.gif?raw=true" />
</p>

由于转发到了所有出口，那 **BCDE** 四台机器怎么知道数据包是不是发给自己的呢？

首先，你要给所有的连接到集线器的设备，都起个名字。原来你们叫 ABCD，但现在需要一个更专业的，全局唯一的名字作为标识，你把这个更高端的名字称为 ***MAC*** 地址。

你的 ***MAC*** 地址是 aa-aa-aa-aa-aa-aa，你的伙伴 b 的 ***MAC*** 地址是 bb-bb-bb-bb-bb-bb，以此类推，不重复就好。

这样，**A** 在发送数据包给 **B** 时，只要在头部拼接一个这样结构的数据，就可以了。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_8.png?raw=true" />
</p>

**B** 在收到数据包后，根据头部的目标 **MAC** 地址信息，判断这个数据包的确是发给自己的，于是便收下。

其他的 **CDE** 收到数据包后，根据头部的目标 **MAC** 地址信息，判断这个数据包并不是发给自己的，于是便丢弃。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_9.gif?raw=true" />
</p>

虽然集线器使整个布局干净不少，但原来我只要发给电脑 B 的消息，现在却要发给连接到集线器中的所有电脑，这样既不安全，又不节省网络资源。

<p align="center" style="font-size: 16px;color: #83AD9B">
    <b>第二层</b>
</p>

> 如果把这个集线器弄得更智能一些，**只发给目标 *MAC* 地址指向的那台电脑**，就好了。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_10.gif?raw=true" />
</p>

虽然只比集线器多了这一点点区别，但看起来似乎有智能了，你把这东西叫做***交换机***。也正因为这一点点智能，你把它放在了另一个层级，***数据链路层***。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_11.png?raw=true" />
</p>

如上图所示，你是这样设计的。

**交换机**内部维护一张 **MAC 地址表**，记录着每一个 **MAC** 地址的设备，连接在其哪一个端口上。

<center>

|  MAC 地址 |  端口  |
|---|---|
| bb-bb-bb-bb-bb-bb	  |  1  |
| cc-cc-cc-cc-cc-cc	  |  3  |
| aa-aa-aa-aa-aa-aa   |  4  |
| dd-dd-dd-dd-dd-dd   |  5  |

</center>

假如你仍然要发给 **B** 一个数据包，构造了如下的数据结构从网口出去。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_12.png?raw=true" />
</p>

到达交换机时，交换机内部通过自己维护的 **MAC 地址表**，发现目标机器 **B** 的 **MAC** 地址 **bb-bb-bb-bb-bb-bb** 映射到了**端口 1** 上，于是把数据从 **1 号端口**发给了 **B**，完事~

你给这个通过这样传输方式而组成的小范围的网络，叫做以太网。

当然最开始的时候，**MAC** 地址表是空的，是怎么逐步建立起来的呢？

假如在 **MAC** 地址表为空是，你给 **B** 发送了如下数据

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_13.png?raw=true" />
</p>

由于这个包从**端口 4** 进入的交换机，所以此时交换机就可以在 **MAC地址表**记录第一条数据：

```
    MAC：aa-aa-aa-aa-aa-aa-aa
    端口：4
```

**交换机**看目标 **MAC** 地址 **（bb-bb-bb-bb-bb-bb）** 在地址表中并没有映射关系，于是将此包发给了**所有端口**，也即发给了所有机器。

之后，只有机器 **B** 收到了确实是发给自己的包，于是做出了响应，响应数据从**端口 1** 进入交换机，于是**交换机**此时在地址表中更新了第二条数据：

```
    MAC：bb-bb-bb-bb-bb-bb
    端口：1
```

过程如下

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_14.gif?raw=true" />
</p>

经过该网络中的机器不断地通信，交换机最终将 **MAC 地址表**建立完毕~

随着机器数量越多，**交换机**的端口也不够了，但聪明的你发现，只要将**多个交换机连接起来**，这个问题就轻而易举搞定~

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_15.png?raw=true" />
</p>

你完全不需要设计额外的东西，只需要按照之前的设计和规矩来，按照上述的接线方式即可完成所有电脑的互联，所以**交换机**设计的这种规则，真的很巧妙。你想想看为什么（比如 **A** 要发数据给 **F**）。

但是你要注意，上面那根***红色***的线，最终在 **MAC 地址表**中可不是一条记录呀，而是要把 **EFGH** 这四台机器与该端口 **（端口6）** 的映射全部记录在表中。

最终，**两个交换机将分别记录 A ~ H 所有机器的映射记录**。

**左边的交换机**

<center>

|  MAC 地址 |  端口  |
|---|---|
| bb-bb-bb-bb-bb-bb	  |  1  |
| cc-cc-cc-cc-cc-cc	  |  3  |
| aa-aa-aa-aa-aa-aa   |  4  |
| dd-dd-dd-dd-dd-dd   |  5  |
| **ee-ee-ee-ee-ee-ee**   |  **6**  |
| **ff-ff-ff-ff-ff-ff**   |  **6**  |
| **gg-gg-gg-gg-gg-gg**   |  **6**  |
| **hh-hh-hh-hh-hh-hh**   |  **6**  |

</center>

**右边的交换机**

<center>

|  MAC 地址 |  端口  |
|---|---|
| **bb-bb-bb-bb-bb-bb**	  |  **1**  |
| **cc-cc-cc-cc-cc-cc**	  |  **1**  |
| **aa-aa-aa-aa-aa-aa**   |  **1**  |
| **dd-dd-dd-dd-dd-dd**   |  **1** |
| ee-ee-ee-ee-ee-ee   |  2  |
| ff-ff-ff-ff-ff-ff   |  3  |
| gg-gg-gg-gg-gg-gg   |  4  |
| hh-hh-hh-hh-hh-hh   |  6  |

</center>

这在只有 8 台电脑的时候还好，甚至在只有几百台电脑的时候，都还好，所以这种交换机的设计方式，已经足足支撑一阵子了。

但很遗憾，人是贪婪的动物，很快，电脑的数量就发展到几千、几万、几十万。

<p align="center" style="font-size: 16px;color: #83AD9B">
    <b>第三层</b>
</p>

**交换机**已经无法记录如此庞大的映射关系了。

此时你动了歪脑筋，你发现了问题的根本在于，连出去的那根**红色的网线**，后面不知道有多少个设备不断地连接进来，从而使得地址表越来越大。

那我可不可以让那根**红色的网线**，接入一个新的设备，这个设备就跟电脑一样有**自己独立的 MAC 地址**，而且同时还能帮我把**数据包做一次转发**呢？

这个设备就是***路由器***，它的功能就是，作为**一台独立的拥有 MAC 地址的设备**，并且可以**帮我把数据包做一次转发**，你把它定在了***网络层***。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_16.png?raw=true" />
</p>

> **注意，路由器的每一个端口，都有独立的 MAC 地址**

好了，现在交换机的 **MAC 地址表**中，只需要多出一条 **MAC** 地址 **ABAB** 与其端口的映射关系，就可以成功把数据包转交给**路由器**了，这条搞定。

那如何做到，把发送给 **C** 和 **D**，甚至是把发送给 **DEFGH....** 的数据包，统统先发送给路由器呢？

不难想到这样一个点子，假如电脑 **C** 和 **D** 的 **MAC** 地址拥有共同的前缀，比如分别是

```
    C 的 MAC 地址：FFFF-FFFF-CCCC
    D 的 MAC 地址：FFFF-FFFF-DDDD
```

那我们就可以说，将目标 **MAC** 地址为 **FFFF-FFFF-**？开头的，统统先发送给**路由器**。

这样是否可行呢？答案是**否定**的。

我们先从现实中 **MAC** 地址的结构入手，***MAC地址也叫物理地址、硬件地址***，长度为 48 位，一般这样来表示

> ```00-16-EA-AE-3C-40```

它是由网络设备制造商生产时烧录在网卡的EPROM（一种闪存芯片，通常可以通过程序擦写）。**其中前 24 位（00-16-EA）代表网络硬件制造商的编号，后 24 位（AE-3C-40）是该厂家自己分配的，一般表示系列号**。只要不更改自己的 MAC 地址，MAC 地址在世界是唯一的。形象地说，MAC地址就如同身份证上的身份证号码，具有唯一性。

那如果你希望向上面那样表示将目标 **MAC** 地址为 **FFFF-FFFF-？开头的**，统一从路由器出去发给某一群设备（后面会提到这其实是子网的概念），那你就需要要求某一子网下统统买一个厂商制造的设备，要么你就需要要求厂商在生产网络设备烧录 **MAC** 地址时，提前按照你规划好的子网结构来定 **MAC** 地址，并且日后这个网络的结构都不能轻易改变。

这显然是不现实的。

于是你发明了一个新的地址，给每一台机器一个 32 位的编号，如：

> ```11000000101010000000000000000001```

你觉得有些不清晰，于是把它分成四个部分，中间用点相连。

> ```11000000.10101000.00000000.00000001```

你还觉得不清晰，于是把它转换成 10 进制。

> ```192.168.0.1```

最后你给了这个地址一个响亮的名字，**IP 地址**。现在每一台电脑，*同时有自己的 **MAC** 地址，又有自己的 **IP** 地址*，只不过 ***IP** 地址是软件层面上的*，可以随时修改，**MAC** 地址一般是无法修改的。

这样一个***可以随时修改的 **IP** 地址***，就可以根据你规划的网络拓扑结构，来调整了。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_17.png?raw=true" />
</p>

如上图所示，假如我想要发送数据包给 **ABCD** 其中一台设备，不论哪一台，我都可以这样描述，**"将 IP 地址为 192.168.0 开头的全部发送给到路由器，之后再怎么转发，交给它！"**，巧妙吧。

那交给**路由器**之后，路由器又是怎么把*数据包准确转发给指定设备*的呢？

别急我们慢慢来。

我们先给上面的组网方式中的每一台设备，加上自己的 **IP** 地址

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_18.png?raw=true" />
</p>

现在两个设备之间传输，除了加上数据链路层的头部之外，还要再增加一个网络层的头部。

假如 **A** 给 **B** 发送数据，由于它们直接连着**交换机**，所以 **A** 直接发出如下数据包即可，其实网络层没有体现出作用。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_19.png?raw=true" />
</p>

但假如 **A** 给 **C** 发送数据，**A** 就需要先转交给路由器，然后再由路由器转交给 **C**。由于最底层的传输仍然需要依赖以太网，所以数据包是分成两段的。

- A ~ 路由器这段的包如下：

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_20.png?raw=true" />
</p>

- 路由器到 C 这段的包如下：

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_21.png?raw=true" />
</p>

好了，上面说的两种情况（A->B，A->C），相信细心的读者应该会有不少疑问，下面我们一个个来展开

> **A** 给 **C** 发数据包，怎么知道是否要通过路由器转发呢？

- **答案：子网**

如果源 IP 与目的 IP 处于一个子网，直接将包通过交换机发出去。

如果源 IP 与目的 IP 不处于一个子网，就交给路由器去处理。

好，那现在只需要解决，什么叫处于一个子网就好了。

- 192.168.0.1 和 192.168.0.2 处于同一个子网

- 192.168.0.1 和 192.168.1.1 处于不同子网

这两个是我们人为规定的，即我们想表示，对于 192.168.0.1 来说：

**192.168.0.xxx 开头的，就算是在一个子网，否则就是在不同的子网。**

那对于计算机来说，怎么表达这个意思呢？于是人们发明了***子网掩码***的概念

假如某台机器的子网掩码定为 255.255.255.0

这表示，将**源 IP** 与目的 **IP** 分别同这个**子网掩码**进行***与运算***，*相等则是在一个子网，不相等就是在不同子网，就这么简单*。

- 比如

```

    A电脑：192.168.0.1 & 255.255.255.0 = 192.168.0.0

    B电脑：192.168.0.2 & 255.255.255.0 = 192.168.0.0

    C电脑：192.168.1.1 & 255.255.255.0 = 192.168.1.0

    D电脑：192.168.1.2 & 255.255.255.0 = 192.168.1.0

```

那么 **A** 与 **B** 在同一个子网，**C** 与 **D** 在同一个子网，但是 **A** 与 **C** 就不在同一个子网，与 **D** 也不在同一个子网，以此类推。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_22.png?raw=true" />
</p>

所以如果 **A** 给 **C** 发消息，**A** 和 **C** 的 **IP** 地址分别 & **A** 机器配置的子网掩码，发现不相等，则 **A** 认为 **C** 和自己不在同一个子网，于是把包发给**路由器**，就不管了，*之后怎么转发，A 不关心*

> **A** 如何知道，哪个设备是路由器？

- **答案：在 A 上要设置*默认网关***

上一步 **A** 通过是否与 **C** 在同一个子网内，判断出自己应该把包发给路由器，那路由器的 **IP** 是多少呢？

其实说发给路由器不准确，应该说 **A** 会把包发给默认网关。

对 **A** 来说，**A** *只能直接把包发给同处于一个子网下的某个 **IP** 上*，所以发给路由器还是发给某个电脑，对 **A** 来说也不关心，只要这个设备有个 **IP** 地址就行。

所以**默认网关**，*就是 **A** 在自己电脑里配置的一个 IP 地址*，以便在发给不同子网的机器时，发给这个 **IP** 地址。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_23.png?raw=true" />
</p>

> 路由器如何知道**C**在哪里？

- **答案：路由表**

现在 **A** 要给 **C** 发数据包，已经可以成功发到路由器这里了，最后一个问题就是，***路由器怎么知道，收到的这个数据包，该从自己的哪个端口出去***，才能直接（或间接）地最终到达目的地 **C** 呢。

路由器收到的数据包有*目的 **IP*** 也就是 **C** 的 **IP** 地址，需要转化成从自己的哪个端口出去，很容易想到，应该有个表，*就像 **MAC 地址表***一样。

这个表就叫**路由表**。

- 至于这个路由表是怎么出来的，有很多路由算法，本文不展开，因为我也不会哈哈~

不同于 **MAC 地址表**的是，*路由表并不是一对一这种明确关系*，我们下面看一个路由表的结构。

<center>

| 目的地址 |  子网掩码  |  下一跳  |  端口  |
|---|---|---|---|
| 192.168.0.0   |  255.255.255.0   |   | 0 |
| 192.168.0.254 |  255.255.255.255 |   | 0 |
| 192.168.1.0   |  255.255.255.0   |   | 1 |
| 192.168.1.254 |  255.255.255.255 |   | 1 |

</center>

我们学习一种新的表示方法，由于***子网掩码其实就表示前多少位表示子网的网段***，所以如 ```192.168.0.0（255.255.255.0）``` 也可以简写为 ```192.168.0.0/24```

<center>

| 目的地址 |  下一跳  |  端口  |
|---|---|---|
| 192.168.0.0/24   |   | 0 |
| 192.168.0.254/32 |   | 0 |
| 192.168.1.0/24   |   | 1 |
| 192.168.1.254/32 |   | 1 |

</center>

这就很好理解了，**路由表**就表示，***192.168.0.xxx 这个子网下的，都转发到 0 号端口，192.168.1.xxx 这个子网下的，都转发到 1 号端口***。下一跳列还没有值，我们先不管

配合着结构图来看（这里把子网掩码和默认网关都补齐了）

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_24.gif?raw=true" />
</p>

> 刚才说的都是 **IP** 层，但发送数据包的数据链路层需要知道 **MAC** 地址，可是我只知道 **IP** 地址该怎么办呢？

- **答案：*arp***

假如你（**A**）此时***不知道***你同伴 **B** 的 **MAC** 地址（现实中就是不知道的，刚刚我们只是假设已知），你只知道它的 **IP** 地址，你该怎么把数据包准确传给 **B** 呢？

答案很简单，在网络层，我需要把 **IP** 地址对应的 **MAC** 地址找到，也就是通过某种方式，找到 ```192.168.0.2``` 对应的 **MAC** 地址 **BBBB**。

这种方式就是 ***arp 协议***，同时电脑 **A** 和 **B** 里面也会有***一张 arp 缓存表***，表中记录着 **IP** 与 **MAC** 地址的对应关系。

<center>

| IP 地址  | MAC 地址  |
|---|---|
| 192.168.0.2  | BBBB |

</center>

一开始的时候这个表是**空的**，电脑 **A** 为了知道电脑 **B**（```192.168.0.2```）的 **MAC** 地址，将会***广播***一条 **arp** 请求，**B** 收到请求后，*带上自己的 **MAC** 地址给 **A** 一个响应*。此时 **A** 便更新了自己的 **arp** 表。

这样通过大家不断**广播 arp 请求**，最终所有电脑里面都将 **arp** 缓存表更新完整。

<p align="center" style="font-size: 16px;color: #FFFFFF">
    <b>总结一下</b>
</p>

1. 从各个节点的视角来看:

> 电脑视角：

- 首先我要知道我的 ***IP*** 以及对方的 ***IP***

- 通过***子网掩码***判断我们是否在同一个**子网**

- *在同一个子网*就通过 **arp** 获取对方 **MAC** 地址直接扔出去

- *不在同一个子网*就通过 **arp** 获取默认网关的 **MAC** 地址直接扔出去

> 交换机视角：

- 我收到的数据包必须有目标 **MAC** 地址

- 通过 **MAC** 地址表查映射关系

- 查到了就按照映射关系从我的指定端口发出去

- 查不到就所有端口都发出去

> 路由器视角：

- 我*收到的数据包*必须有目标 **IP** 地址

- 通过路由表查映射关系

- 查到了就按照映射关系从我的指定端口发出去（*不在任何一个子网范围，走其路由器的默认网关也是查到了*）

- 查不到则返回一个路由不可达的数据包

如果你嗅觉足够敏锐，你应该可以感受到下面这句话：

> 网络层（IP协议）本身没有传输包的功能，包的实际传输是委托给数据链路层（以太网中的交换机）来实现的。

2. 涉及到的三张表分别是

- **交换机**中有 **MAC 地址表**用于*映射 **MAC** 地址和它的端口*

- **路由器**中有**路由表**用于*映射 **IP** 地址(段)和它的端口*

- **电脑**和**路由器**中*都有 **arp** 缓存表*用于缓存 **IP** 和 **MAC** 地址的映射关系

3. 这三张表是怎么来的

- **MAC 地址表**是通过以太网内各节点之间不断通过交换机通信，不断完善起来的。

- **路由表**是各种路由算法 + 人工配置逐步完善起来的。

- **arp 缓存表**是不断通过 **arp** 协议的请求逐步完善起来的。

知道了以上这些，目前网络上两个节点是如何发送数据包的这个过程，就完全可以解释通了！

> 那接下来我们就放上本章 最后一个**网络拓扑图**

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_25.png?raw=true" />
</p>

这时路由器 1 连接了路由器 2，所以其***路由表有了下一条地址***这一个概念，所以它的路由表就变成了这个样子。如果匹配到了有下一跳地址的一项，则需要再次匹配，找到其端口，并找到下一跳 **IP** 的 **MAC** 地址。

也就是说找来找去，最终必须能映射到一个端口号，然后从这个端口号把数据包发出去。

<center>

| 目的地址 |  下一跳  |  端口  |
|---|---|---|
| 192.168.0.0/24   |               | 0 |
| 192.168.0.254/32 |               | 0 |
| 192.168.1.0/24   |               | 1 |
| 192.168.1.254/32 |               | 1 |
| 192.168.2.0/24   | 192.168.100.5 |   |
| 192.168.100.0/24 |               | 2 |
| 192.168.100.4/32 |               | 2 |

</center>

> **这时如果 A 给 F 发送一个数据包，能不能通呢？如果通的话整个过程是怎样的呢？**

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_26.png?raw=true" />
</p>

> **详细过程动画描述：**

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_27.gif?raw=true" />
</p>

> **详细过程文字描述：**

1. 首先 **A**（```192.168.0.1```）通过*子网掩码*（```255.255.255.0```）计算出自己与 **F**（```192.168.2.2```）并不在同一个子网内，于是决定发送给*默认网关*（```192.168.0.254```）
2. **A** 通过 **ARP** 找到 *默认网关* ```192.168.0.254``` 的 **MAC** 地址。
3. **A** 将源 **MAC** 地址（**AAAA**）与网关 **MAC** 地址（**ABAB**）封装在数据链路层头部，又将源 **IP** 地址（```192.168.0.1```）和目的 **IP** 地址（```192.168.2.2```）（*注意这里千万不要以为填写的是默认网关的 IP 地址，从始至终这个数据包的两个 IP 地址都是不变的，只有 MAC 地址在不断变化*）封装在网络层头部，然后发包

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_28.png?raw=true" />
</p>

4. *交换机 1* 收到数据包后，发现目标 **MAC** 地址是 **ABAB**，转发给*路由器1*
5. 数据包来到了*路由器 1*，发现其目标 **IP** 地址是 ```192.168.2.2```，查看其路由表，发现了*下一跳*的地址是 ```192.168.100.5```
6. 所以此时*路由器 1* 需要做两件事，第一件是再次匹配路由表，发现匹配到了端口为 2，于是将其封装到数据链路层，最后把包从 2 号口发出去。 ***（同时路由器根据路由表中路由器2的IP地址做ARP更新MAC地址）***
7. 此时*路由器 2* 收到了数据包，看到其目的地址是 ```192.168.2.2```，查询其路由表，匹配到端口号为 1，准备从 1 号口把数据包送出去。
8. 但此时*路由器 2* 需要知道 ```192.168.2.2``` 的 **MAC** 地址了，于是查看其 **arp 缓存**，找到其 **MAC** 地址为 **FFFF**，将其封装在数据链路层头部，并从 1 号端口把包发出去。
9. *交换机 3* 收到了数据包，发现目的 **MAC** 地址为 **FFFF**，查询其 **MAC** 地址表，发现应该从其 6 号端口出去，于是从 6 号端口把数据包发出去。
10. **F** 最终收到了数据包！并且发现目的 **MAC** 地址就是自己，于是收下了这个包

- 详情可参考 Resources/pkt

> 至此，经过*物理层、数据链路层、网络层*这前三层的协议，以及根据这些协议设计的各种网络设备（*网线、集线器、交换机、路由器*），理论上只要拥有对方的 IP 地址，就已经将地球上任意位置的两个节点连通了。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_31.png?raw=true" />
</p>

From：https://mp.weixin.qq.com/s/rGX7jTHLrXg4Qikls_deDg

## **TCP in Details**

经过《[你管这破玩意儿叫网络？](https://mp.weixin.qq.com/s/rGX7jTHLrXg4Qikls_deDg)》这篇文章中的一番折腾，只要你知道另一位伙伴 **B** 的 **IP** 地址，且你们之间的网络是通的，无论多远，你都可以将一个数据包发送给你的伙伴 **B**

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/basic_flow_31.png?raw=true" />
</p>

这就是物理层、数据链路层、网络层这三层所做的事情。

站在第四层的你，就可以不要脸地利用下三层所做的铺垫，随心所欲地发送数据，而不必担心找不到对方了

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_1.gif?raw=true" />
</p>

虽然你此时还什么都没干，但你还是给自己这一层起了个响亮的名字，叫做**传输层**。

你本以为自己所在的第四层万事大吉，啥事没有，但很快问题就接踵而至。

<p align="center" style="font-size: 16px;color: #83AD9B">
    <b>问题来了</b>
</p>

前三层协议只能把数据包从一个主机搬到另外一台主机，但是，到了目的地以后，数据包*具体交给*哪个 **程序（进程）** 呢？

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_2.png?raw=true" />
</p>

所以，你需要把通信的进程区分开来，于是就给每个进程分配一个数字编号，你给它起了一个响亮的名字：**端口号**。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_3.png?raw=true" />
</p>

然后你在要发送的数据包上，增加了传输层的头部，**源端口号**与**目标端口号**。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_4.png?raw=true" />
</p>

OK，这样你将原本主机到主机的通信，升级为了*进程和进程之间*的通信。

你没有意识到，你不知不觉实现了 ***UDP*** 协议！

> (当然 UDP 协议中不光有源端口和目标端口，还有数据包长度和校验值，我们暂且略过)

就这样，你用 **UDP** 协议无忧无虑地同 **B** 进行着通信，一直没发生什么问题。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_5.gif?raw=true" />
</p>

但很快，你发现事情变得非常复杂......

<p align="center" style="font-size: 16px;color: #83AD9B">
    <b>丢包问题</b>
</p>

由于网络的不可靠，数据包可能在半路丢失，而 **A** 和 **B** 却无法察觉。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_6.gif?raw=true" />
</p>

对于丢包问题，只要解决两个事就好了。

- 第一个，**A** 怎么知道包丢了？
> 答案：让 **B** 告诉 **A**
- 第二个，丢了的包怎么办？
> 答案：重传

于是你设计了如下方案，**A** 每发一个包，都必须收到来自 **B** 的确认（**ACK**），再发下一个，否则在一定时间内没有收到确认，就**重传**这个包

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_7.gif?raw=true" />
</p>

你管它叫**停止等待协议**。只要按照这个协议来，虽然 **A** 无法保证 **B** 一定能收到包，但 **A** 能够确认 **B** 是否收到了包，收不到就**重试**，尽最大努力让这个通信过程变得可靠，于是你们现在的通信过程又有了一个新的特征，**可靠交付**。

<p align="center" style="font-size: 16px;color: #83AD9B">
    <b>效率问题</b>
</p>

停止等待虽然能解决问题，但是效率太低了，**A** 原本可以在发完第一个数据包之后立刻开始发第二个数据包，但由于停止等待协议，**A** 必须等数据包到达了 **B** ，且 **B** 的 **ACK** 包又回到了 **A**，才可以继续发第二个数据包，这效率慢得可不是一点两点。

于是你对这个过程进行了改进，采用**流水线**的方式，不再傻傻地等。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_8.gif?raw=true" />
</p>

<p align="center" style="font-size: 16px;color: #83AD9B">
    <b>顺序问题</b>
</p>

但是网路是复杂的、不可靠的。

有的时候 **A** 发出去的数据包，分别走了不同的路由到达 **B**，*可能无法保证和发送数据包时一样的顺序*。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_9.gif?raw=true" />
</p>

在流水线中有多个数据包和**ACK**包在乱序流动，他们之间对应关系就乱掉了。

难道还回到停止等待协议？**A** 每收到一个包的确认（**ACK**）再发下一个包，那就根本不存在顺序问题。应该有更好的办法！

**A** 在发送的数据包中增加一个**序号（seq）**，同时 **B** 要在 **ACK** 包上增加一个确认号（**ack**），这样不但解决了停止等待协议的效率问题，也通过这样标序号的方式解决了顺序问题。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_10.gif?raw=true" />
</p>

而 **B** 这个确认号意味深长：比如 **B** 发了一个确认号为 **ack = 3**，它不仅仅表示 **A** 发送的序号为 **2** 的包收到了，还表示 **2** 之前的数据包都收到了。这种方式叫**累计确认**或**累计应答**。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_11.gif?raw=true" />
</p>

> 注意，实际上 **ack** 的号是收到的最后一个数据包的序号 **seq + 1**，也就是*告诉对方下一个应该发的序号是多少*。但图中为了便于理解，**ack** 就表示收到的那个序号，不必纠结。

<p align="center" style="font-size: 16px;color: #83AD9B">
    <b>流量问题</b>
</p>

有的时候，**A** 发送数据包的速度太快，而 **B** 的接收能力不够，但 **B** 却没有告知 **A** 这个情况。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_12.gif?raw=true" />
</p>

怎么解决呢？

很简单，**B** 告诉 **A** 自己的**接收能力**，**A** 根据 **B** 的**接收能力**，相应控制自己的**发送速率**，就好了。

B 怎么告诉 A 呢？B 跟 A 说"我很强"这三个字么？那肯定不行，得有一个严谨的规范。

于是 **B** 决定，每次发送数据包给 **A** 时，顺带传过来一个值，叫**窗口大小（win)**，这个值就表示 **B** 的**接收能力**。同理，每次 **A** 给 **B** 发包时也带上*自己的窗口大小*，表示 **A** 的**接收能力**。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_13.gif?raw=true" />
</p>

**B** 告诉了 **A** 自己的窗口大小值，**A** 怎么利用它去做 **A** 这边发包的流量控制呢？

很简单，假如 **B** 给 **A** 传过来的窗口大小 **win = 5**，那 **A** 根据这个值，把自己要发送的数据分成这么几类。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_14.png?raw=true" />
</p>

当 **A** 不断发送数据包时，*已发送的最后一个序号就往右移动*，直到碰到了*窗口的上边界*，此时 **A** 就无法继续发包，达到了**流量控制**。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_15.gif?raw=true" />
</p>

但是当 **A** 不断发包的同时，**A** 也会收到来自 **B** 的*确认包*，此时**整个窗口会往右移动**，因此**上边界也往右移动**，**A** 就能发更多的数据包了。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_16.gif?raw=true" />
</p>

以上都是在窗口大小不变的情况下，而 **B** 在发给 **A** 的 **ACK** 包中，**每一个都可以重新设置一个新的窗口大小**，如果 **A** 收到了一个新的窗口大小值，**A** 会随之调整。

如果 **A** 收到了比原窗口值**更大的窗口大小**，比如 **win = 6**，则 **A** 会**直接将窗口上边界向右移动 1 个单位**。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_17.gif?raw=true" />
</p>

如果 **A** 收到了**比原窗口值小的**窗口大小，比如 **win = 4**，则 **A** **暂时不会改变窗口大小**，**更不会将窗口上边界向左移动**，而是**等着 ACK 的到来**，**不断将左边界向右移动**，直到窗口大小值**收缩**到新大小为止。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_18.gif?raw=true" />
</p>

OK，终于将流量控制问题解决得差不多了，你看着上面一个个小动图，给这个窗口起了一个更生动的名字，**滑动窗口**

<p align="center" style="font-size: 16px;color: #83AD9B">
    <b>拥塞问题</b>
</p>

但有的时候，不是 **B** 的接受能力不够，而是网络不太好，造成了**网络拥塞**。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_19.gif?raw=true" />
</p>

拥塞控制与流量控制有些像，但流量控制是受 **B** 的接收能力影响，而拥塞控制是受**网络环境**的影响。

**拥塞控制的解决办法依然是通过设置一定的窗口大小**，只不过，**流量控制**的窗口大小是 **B** 直接告诉 **A** 的，而**拥塞控制**的窗口大小按理说就应该是网络环境主动告诉 **A**。

但网络环境怎么可能主动告诉 **A** 呢？只能 **A** **单方面通过试探**，**不断感知网络环境的好坏，进而确定自己的拥塞窗口的大小**。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_20.gif?raw=true" />
</p>

拥塞窗口大小的计算有很多复杂的算法，就不在本文中展开了，假如**拥塞窗口的大小为 cwnd**，上一部分**流量控制的滑动窗口的大小为 rwnd**，那么窗口的右边界受这两个值共同的影响，需要取它俩的最小值。

<p align="center" style="font-size: 16px;">
    <b>窗口大小 = min(cwnd, rwnd)</b>
</p>

含义很容易理解，当 **B** 的接受能力比较差时，即使网络非常通畅，**A** 也需要根据 **B** 的接收能力限制自己的发送窗口。当网络环境比较差时，即使 **B** 有很强的接收能力，**A** 也要根据网络的拥塞情况来限制自己的发送窗口。正所谓受其短板的影响嘛~

> 窗口大小为流量窗口和拥塞窗口之中的最小值

<p align="center" style="font-size: 16px;color: #83AD9B">
    <b>连接问题</b>
</p>

有的时候，**B** 主机的相应进程还没有准备好或是挂掉了，**A** 就开始发送数据包，导致了浪费。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_21.gif?raw=true" />
</p>

这个问题在于，**A** 在跟 **B** 通信之前，没有事先确认 **B** 是否已经准备好，就开始发了一连串的信息。就好比你和另一个人打电话，你还没有"喂"一下确认对方有没有在听，你就巴拉巴拉说了一堆。

这个问题该怎么解决呢？

地球人都知道，**三次握手**嘛！

```
  A：我准备好了(SYN)

  B：我知道了(ACK)，我也准备好了(SYN) (ACK + SYN)

  A：我知道了(ACK)
```

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_22.gif?raw=true" />
</p>

**A** 与 **B** 各自在内存中维护着自己的状态变量，三次握手之后，双方的状态都变成了连接已建立（**ESTABLISHED**）。

虽然就只是发了三次数据包，并且在各自的内存中维护了状态变量，但这么说总觉得太 low，你看这个过程相当于双方建立连接的过程，于是你灵机一动，就叫它**面向连接**吧。

注意：这个连接是虚拟的，是由 **A** 和 **B** 这两个终端共同维护的，在网络中的设备根本就不知道连接这回事儿！

但凡事有始就有终，有了建立连接的过程，就要**考虑释放连接**的过程，又是地球人都知道，**四次挥手**嘛！

```
  A：再见，我要关闭了(FIN)

  B：我知道了(ACK)

    给 B 一段时间把自己的事情处理完...

  B：再见，我要关闭了(FIN)

  A：我知道了(ACK)
```

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_23.gif?raw=true" />
</p>

<p align="center" style="font-size: 16px;color: #83AD9B">
    <b>总结</b>
</p>

以上讲述的，就是 TCP 协议的核心思想，上面过程中需要传输的信息，就体现在 TCP 协议的头部，这里放上最常见的 TCP 协议头解读的图

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_24.png?raw=true" />
</p>

- **TCP** 是 ```面向连接```的、```可靠```的、```基于字节流```的 传输层通信协议

面向连接、可靠，这两个词通过上面的讲述很容易理解，那什么叫做基于字节流呢？

很简单，**TCP** 在建立连接时，需要告诉对方 **MSS（最大报文段大小)**。

也就是说，如果要发送的数据很大，在 **TCP** 层是需要按照 **MSS** 来切割成一个个的 **TCP 报文段** 的。

切割的时候我才不管你原来的数据表示什么意思，需要在哪里断句啥的，我就把它当成一串毫无意义的字节，在我想要切割的地方咔嚓就来一刀，标上序号，只要接收方再根据这个序号拼成最终想要的完整数据就行了。

在我 TCP 传输这里，我就把它当做一个个的字节，也就是基于字节流的含义了。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_25.jpg?raw=true" />
</p>

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tu_jie_tcp_ip/93.png?raw=true" />
</p>

From: https://mp.weixin.qq.com/s/h89R86KhWiQKsBvfZpyF5Q

## **从单个服务器扩展到百万用户的系统**

> 你开发了一个网站（例如网上商店、社交网站或者其他任何东西），之后你把它发布到了网上，网站运行良好，每天有几百的访问量，能快速地相响应用户的请求。

> 但是有一天，不知道什么原因，你的网站出名了！ 

> 每分每秒都有成千上万的用户蜂拥而至，你的网站变得越来越慢……

> 对你来讲，这是个好消息，但是对你的Web应用来说这是个坏消息。因为现在它需要扩展了，你的应用需要为全球用户提供7*24不宕机服务。

### **如何进行扩展?**

> 几年前，我讨论过*水平扩展与垂直扩展*。简而言之, *垂直扩展*意味着在性能更强的计算机上运行同样的服务，而*水平扩展*是并行地运行多个服务。

> 如今，几乎没有人说*垂直扩展*了。原因很简单：

- 随着计算机性能的增长，其价格会成倍增长
- 单台计算机的性能是有上限的，不可能无限制地垂直扩展
- 多核CPU意味着即使是单台计算机也可以并行的。那么，为什么不一开始就并行化呢？

> 现在我们*水平扩展*服务。需要哪些步骤呢？

### **1. 单台服务器 + 数据库**

![Alt text](/resources/img/network_programming_note/web_system_expand_1.jfif)

> 上图可能是你后端服务最初的样子。有一个执行业务逻辑的应用服务器```（Application Server）```和保存数据的数据库。

> 看上去很不错。但是这样的配置，满足更高要求的唯一方法是在性能更强的计算机上运行，这点不是很好。

### **2. 增加一个反向代理**

![Alt text](/resources/img/network_programming_note/web_system_expand_2.jfif)

> 成为大规模服务架构的第一步是添加反向代理。类似于酒店大堂的接待处。你也可以让客人直接去他们的客房。但是实际上，你需要一个中间人他去检查是否允许客人进入， 如果客房没有开放，得有人告诉客人，而不是让客人处于尴尬的境地。这些事情正是反向代理需要做的。

> 通常，代理是一个接收和转发请求的过程。正常情况下，「正向代理」代理的对象是客户端，「反向代理」代理的对象是服务端，它完成这些功能：

- 健康检查功能，确保我们的服务器是一直处于运行状态的
- 路由转发功能，把请求转发到正确的服务路径上
- 认证功能,确保用户有权限访问后端服务器
- 防火墙功能，确保用户只能访问允许使用的网络部分等等

### **3. 引入负载均衡器**

![Alt text](/resources/img/network_programming_note/web_system_expand_3.jfif)

> 大多数反向代理还有另外一个功能：他们也可以充当负载均衡器。

> 负载均衡器是个简单概念，想象下有一百个用户在一分钟之内在你的网店里付款。遗憾的是，你的付款服务器在一分钟内只能处理50笔付款。这怎么办呢？同时运行两个付款服务器就行了。

> 负载均衡器的功能就是把付款请求分发到两台付款服务器上。用户1往左，用户2往右，用户3再往左。。。以此类推。

> 如果一次有500个用户需要立刻付款，这该怎么解决呢？确切地说，你可以扩展到十台付款服务器，之后让负载均衡器分发请求到这十台服务器上。



### **4. 扩展数据库**

![Alt text](/resources/img/network_programming_note/web_system_expand_4.jfif)

> 负载均衡器的使用使得我们可以在多个服务器之间分配负载。但是你发现问题了吗？尽管我们可以用成百上千台服务器处理请求，但是他们都是用同一个数据库存储和检索数据。

> 那么，我们不能以同样的方式来扩展数据库吗？很遗憾，这里有个一致性的问题。

> 系统使用的所有服务需要就他们使用的数据达成一致。数据不一致会导致各种问题，如订单被多次处理，从一个余额只有100元的账户中扣除两笔90元的付款等等......那么我们在扩展数据库的时候如何确保一致性呢？

> 我们需要做的第一件事是把数据库分成多个部分。一部分专门负责接收并存储数据，其他部分负责检索数据。这个方案有时称为主从模式或者单实例写多副本读。这里假设是从数据库读的频率高于写的频率。这个方案的好处是保证了一致性，因为数据只能被单实例写入，之后把写入数据同步到其他部分即可。缺点是我们仍然只有一个写数据库实例。

> 这对于中小型的Web应用来说没问题， 但是像Facebook这样的则不会这样做了。我们会在第九节中研究扩展数据库的步骤。



### **5. 微服务**

![Alt text](/resources/img/network_programming_note/web_system_expand_5.jfif)

> 到目前为止，我们的付款、订单、库存、用户管理等等这些功能都在一台服务器上。

> 这也不是坏事，单个服务器同时意味着更低的复杂性。随着规模的增加，事情会变得复杂和低效：

> 开发团队随着应用的发展而增长。但是随着越来越多的开发人员工作在同一台服务器上，发生冲突的可能性很大。

> 仅有一台服务器，意味着每当我们发布新版本时，必须要等所有工作完成后才能发布。当一个团队想快速地发布而另外一个团队只完成了一半工作的时候，这种互相依赖性很危险。

> 对于这些问题的解决方案是一个新的架构范式：微服务， 它已经在开发人员中掀起了风暴。

> 每个服务都可以单独扩展，更好地适应需求

> 开发团队之间相互独立，每个团队都负责自己的微服务生命周期(创建，部署，更新等)

> 每个微服务都有自己的资源，比如数据库，进一步缓解了第4节中的问题。



### **6. 缓存和内容分发网络(CDN)**

![Alt text](/resources/img/network_programming_note/web_system_expand_6.jfif)

> 有什么方式能使服务更高效? 网络应用的很大一部由静态资源构成,如图片、CSS样式文件、JavaScript脚本以及一些针对特定产品提前渲染好的页面等等。

> 我们使用缓存而不是对每个请求都重新处理，缓存用于记住最后一次的结果并交由其他服务或者客户端，这样就不用每次都请求后端服务了。

> 缓存的加强版叫```内容分发网络（Content Delivery Network）```，遍布全球的大量缓存。 这使得用户可以从物理上靠近他们的地方来获取网页内容，而不是每次都把数据从源头搬到用户那里。

#### **Note:**
- What is a CDN?
> A CDN is a Content Delivery Network. These are file hosting services for multiple versions of common libraries. They are usually highly performant and offer location cached files so no matter where your users are, they receive the files from geo locations close to them. This can make your application faster than hosting files yourself.

> CDN's also have the advantage that if you are using libraries common to multiple sites then your users may already have the file cached in their browser. This speeds up your site because the browser doesn't need to download the library again.

> For example, JQuery has an official JQuery CDN. If most JQuery applications import the JQuery library from this CDN, then users are more likely to have JQuery in their cache already.

### **7. 消息队列**

![Alt text](/resources/img/network_programming_note/web_system_expand_7.jfif)

> 你去过游乐园吗？你是否走到售票柜台去买票？也许不是这样，可能是排队等候。政府机构、邮局、游乐园入口都属于并行概念的例子，多个售票亭同时售票，但似乎也永远不足以为每个人立即服务，于是队列形成了。

> 队列同样也是用于大型Web应用。每分钟都有成千上万的图片上传到Instagram、Facebook每个图片都需要处理，调整大小，分析与打标签，这些都是耗时的处理过程。

> 因此，不要让用户等到完成所有步骤，图片接收服务只需要做以下三件事：

- 存储原始的、未处理的图片
- 向用户确认图片已经上传
- 创建一个待办的任务

> 这个待办事项列表中的任务可以被其他任意数量服务接收，每个服务完成其中一个任务，直到所有的待办事项完成。管理这些“待办事项列表”的称为消息队列。使用这样的队列有许多优点：

- 解耦了任务和处理过程。有时需要处理大量的图片，有时很少。有时有大量服务可用，有时很少可用。简单地把任务添加到待办事项而不是直接处理它们，这确保了系统保持响应并且任务也不会丢失。
- 可以按需扩展。启动大量的服务比较耗时，所以当有大量用户上传图片时再去启动服务，这已经太晚了。我们把任务添加到队列中，我们可以推迟提供额外的处理能力。

> 好了，如果按照我们上面的所有步骤操作下来，我们的系统已经做好提供大流量服务的准备了。但是如果还想提供更大量的，该怎么做呢？还有一些可以做：

### **8. 分片，分片，还是分片**

![Alt text](/resources/img/network_programming_note/web_system_expand_8.jfif)

> 什么是分片？好吧，深呼吸一下，准备好了吗？我们看下定义：

- ```"Sharding is a technique of parallelizing an application's stacks by separating them into multiple units, each responsible for a certain key or namespace"```

> 哎呦...... 分片究竟是是什么意思呢？

> 其实也很简单：Facebook上需要为20亿用户提供个人资料, 可以把你的应用架构分解为 26个mini-Facebook, 用户名如果以A开头，会被mini-facebook A处理， 用户名如果以B开头，会被mini-facebook B来处理……

> 分片不一定按字母顺序，根据业务需要，你可以基于任何数量的因素，比如位置、使用频率(特权用户被路由到好的硬件)等等。你可以根据需要以这种方式切分服务器、数据库或其他方面。



### **9. 对负载均衡器进行负载均衡**

![Alt text](/resources/img/network_programming_note/web_system_expand_9.jfif)

> 到目前为止，我们一直使用一个负载均衡器，即使你购买的一些功能强悍(且其价格极其昂贵)的硬件负载均衡器，但是他们可以处理的请求量也存在硬件限制。

> 幸运地是，我们可以有一个全球性、分散且稳定的层，用于在请求达到负载均衡器之前对请求负载均衡。最棒的地方是免费，这是域名系统或简称DNS。```DNS将域名(如arcentry.com)映射到IP，143.204.47.77。DNS允许我们为域名指定多个IP，每个IP都会解析到不同的负载均衡器```。

> 你看，扩展Web应用确实需要考虑很多东西，感谢你和我们一起待了这么久。我希望这篇文章能给你一些有用的东西。但是如果你做任何IT领域相关的工作，你在阅读本文的时候，可能有个问题一直萦绕在你的脑海：*"云服务是怎样的呢？"*

## **Cloud Computing / Serverless**

> 但是云服务如何呢？确实，它是上面许多问题最有效的解决方案。

> 你无需解决这些难题。相反，这些难题留给了云厂商，他们为我们提供一个系统，可以根据需求进行扩展，而不用担心错综复杂的问题。

> 例如。Arcentry网站不会执行上述讨论的任何操作(除了数据库的读写分离)，而只是把这些难题留给Amazon Web Service Lambda函数处理了，用户省去了烦恼。

> 但是,并不是说你使用了云服务以后(如 Amazon Web Service Lambda)，所有的问题都解决了,它随之而来的是一系列挑战和权衡。

From: https://mp.weixin.qq.com/s/wSCeO8QVYniMIGcBFDZyjw

## **Serverless**

From: https://mp.weixin.qq.com/s/Kv0L83E_wj3be5DTt2LfZA

## **Kafka**

From: https://mp.weixin.qq.com/s/ghFDVMCacgYuTcG5klxTiw

## **分布式系统的负载均衡**

From: https://mp.weixin.qq.com/s/H3nj_6mR1XCyi6uBboVIhA <br/>
From: https://mp.weixin.qq.com/s/kD95oe03-EDBIOx7KLehdA

## **HTTP && HTTP/2 && HTTP/3**

```HTTP/2``` 相比于 ```HTTP/1.1```，可以说是*大幅度提高了网页的性能*，只需要升级到该协议就可以减少很多之前需要做的性能优化工作，当然兼容问题以及如何优雅降级应该是国内还不普遍使用的原因之一。

虽然 ```HTTP/2``` 提高了网页的性能，但是并不代表它已经是完美的了，```HTTP/3``` 就是为了解决 ```HTTP/2``` 所存在的一些问题而被推出来的。

### **HTTP/1.1发明以来发生了哪些变化？**

如果仔细观察打开那些最流行的网站首页所需要下载的资源的话，会发现一个非常明显的趋势。近年来加载网站首页需要的下载的数据量在逐渐增加，并已经超过了2100K。但在这里我们更应该关心的是：平均每个页面为了完成显示与渲染所需要下载的资源数已经超过了100个。

正如下图所示，从2011年以来,传输数据大小与平均请求资源数量不断持续增长，并没有减缓的迹象。该图表中绿色直线展示了传输数据大小的增长，红色直线展示了平均请求资源数量的增长。

```HTTP/1.1```自从1997年发布以来，我们已经使用```HTTP/1.x``` 相当长一段时间了，但是随着近十年互联网的爆炸式发展，***从当初网页内容以文本为主,到现在以富媒体（如图片、声音、视频）为主,而且对页面内容实时性高要求的应用越来越多(比如聊天、视频直播),于是当时协议规定的某些特性，已经无法满足现代网络的需求了***。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/http_1.png?raw=true" />
</p>

### ```HTTP/1.1```的缺陷

- **高延迟**--带来页面加载速度的降低

虽然近几年来网络带宽增长非常快，然而我们却并没有看到网络延迟有对应程度的降低。网络延迟问题主要由于 ***队头阻塞(Head-Of-Line Blocking)*** ,导致带宽无法被充分利用。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/http_2.png?raw=true" />
</p>

**队头阻塞是指当顺序发送的请求序列中的一个请求因为某种原因被阻塞时，在后面排队的所有请求也一并被阻塞，会导致客户端迟迟收不到数据。**

针对队头阻塞,人们尝试过以下办法来解决:

> 将同一页面的资源分散到不同域名下，提升连接上限。 Chrome有个机制，对于同一个域名，默认允许同时建立 6 个 TCP持久连接，使用持久连接时，虽然能公用一个TCP管道，但是在一个管道中同一时刻只能处理一个请求，在当前的请求没有结束之前，其他的请求只能处于阻塞状态。另外如果在同一个域名下同时有10个请求发生，那么其中4个请求会进入排队等待状态，直至进行中的请求完成。

> Spriting 合并多张小图为一张大图,再用JavaScript或者CSS将小图重新“切割”出来的技术。

> 内联(Inlining)是另外一种防止发送很多小图请求的技巧，将图片的原始数据嵌入在CSS文件里面的URL里，减少网络请求次数。

```
.icon1 {background: url(data:image/png;base64,<data>) no-repeat;}
.icon2 {background: url(data:image/png;base64,<data>) no-repeat;}
```
> 拼接(Concatenation)将多个体积较小的JavaScript使用webpack等工具打包成1个体积更大的JavaScript文件,但如果其中1个文件的改动就会导致大量数据被重新下载多个文件。

- 无状态特性--带来的**巨大HTTP头部**

由于报文Header一般会携带"User Agent""Cookie""Accept""Server"等许多固定的头字段（如下图），多达几百字节甚至上千字节，但**Body却经常只有几十字节（比如GET请求、
204/301/304响应）**，成了不折不扣的“大头儿子”。**Header里携带的内容过大**，在一定程度上增加了传输的成本。更要命的是，成千上万的请求响应报文里有很多字段值都是重复的，非常浪费。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/http_3.png?raw=true" />
</p>

- **明文传输**--带来的不安全性

```HTTP/1.1```在传输数据时，*所有传输的内容都是明文，客户端和服务器端都无法验证对方的身份，这在一定程度上无法保证数据的安全性*。

你有没有听说过"免费WiFi陷阱”之类的新闻呢？黑客就是利用了HTTP明文传输的缺点，在公共场所架设一个WiFi热点开始“钓鱼”，诱骗网民上网。一旦你连上了这个WiFi热点，所有的流量都会被截获保存，里面如果有银行卡号、网站密码等敏感信息的话那就危险了，黑客拿到了这些数据就可以冒充你为所欲为。

- **不支持服务器推送消息**

### ```SPDY``` 协议与 ```HTTP/2``` 简介

- ```SPDY``` 协议

上面我们提到,由于```HTTP/1.x```的缺陷，我们会引入雪碧图、将小图内联、使用多个域名等等的方式来提高性能。不过这些优化都绕开了协议，直到2009年，**谷歌公开了自行研发的** ```SPDY``` 协议，主要**解决HTTP/1.1效率不高**的问题。谷歌推出SPDY，才算是正式改造HTTP协议本身。降低延迟，压缩header等等，SPDY的实践证明了这些优化的效果，也最终带来```HTTP/2```的诞生。

```HTTP/1.1```有两个主要的缺点：安全不足和性能不高，***由于背负着 ```HTTP/1.x``` 庞大的历史包袱,所以协议的修改,兼容性是首要考虑的目标***，否则就会破坏互联网上无数现有的资产。**```SPDY```位于```HTTP```之下，```TCP```和```SSL```之上**，这样可以*轻松兼容老版本的```HTTP```协议*(将```HTTP1.x```的内容封装成一种新的frame格式)，同时可以使用已有的```SSL```功能。

```SPDY``` 协议在Chrome浏览器上证明可行以后，就被**当作 ```HTTP/2``` 的基础**，主要特性都在 ```HTTP/2``` 之中得到继承。

- ```HTTP/2``` 简介

2015年，```HTTP/2``` 发布。```HTTP/2```是现行```HTTP```协议（```HTTP/1.x```）的替代，但它不是重写，```HTTP```方法/状态码/语义都与```HTTP/1.x```一样。***```HTTP/2```基于```SPDY```，专注于性能，最大的一个目标是在用户和网站间只用一个连接（connection）***。从目前的情况来看，国内外一些排名靠前的站点基本都实现了```HTTP/2```的部署，使用```HTTP/2```能带来20%~60%的效率提升。

```HTTP/2```由两个规范（Specification）组成：

```
  Hypertext Transfer Protocol version 2 - RFC7540
  HPACK - Header Compression for HTTP/2 - RFC7541
```

### ```HTTP/2``` 新特性

- **1. 二进制传输**

***```HTTP/2```传输数据量的大幅减少,主要有两个原因:以二进制方式传输和Header 压缩***。我们先来介绍二进制传输,```HTTP/2``` 采用二进制格式传输数据，而非```HTTP/1.x``` 里纯文本形式的报文 ，二进制协议解析起来更高效。```HTTP/2``` 将请求和响应数据分割为更小的帧，并且它们采用二进制编码。

它把```TCP```协议的部分特性挪到了应用层，*把原来的"Header+Body"的消息"打散"为数个小片的二进制"帧"(Frame),用"HEADERS"帧存放头数据、"DATA"帧存放实体数据。* ```HTTP/2```数据分帧后"Header+Body"的报文结构就完全消失了，协议看到的只是一个个的"碎片"。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/http_4.png?raw=true" />
</p>

```HTTP/2``` 中，同域名下所有通信都在单个连接上完成，该连接可以承载任意数量的双向数据流。每个数据流都以消息的形式发送，而消息又由一个或多个帧组成。***多个帧之间可以乱序发送，根据帧首部的流标识可以重新组装。***

- **2. Header 压缩**

```HTTP/2```并没有使用传统的压缩算法，而是开发了专门的 **"HPACK”算法**，在客户端和服务器两端建立“字典”，用索引号表示重复的字符串，还采用哈夫曼编码来压缩整数和字符串，可以达到50%~90%的高压缩率

具体来说:

```

1. 在客户端和服务器端使用“首部表”来跟踪和存储之前发送的键-值对，对于相同的数据，不再通过每次请求和响应发送；

2. 首部表在HTTP/2的连接存续期内始终存在，由客户端和服务器共同渐进地更新;

3. 每个新的首部键-值对要么被追加到当前表的末尾，要么替换表中之前的值

```

例如下图中的两个请求， 请求一发送了所有的头部字段，第二个请求则只需要发送差异数据，这样可以减少冗余数据，降低开销

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/http_5.jpg?raw=true" />
</p>

- **3. 多路复用 (Multiplexing)**

在 ```HTTP/2``` 中引入了多路复用的技术。*多路复用很好的解决了浏览器限制同一个域名下的请求数量的问题*，同时也接更容易实现全速传输，毕竟新开一个 TCP 连接都需要慢慢提升传输速度。

大家可以通过 该链接 直观感受下 ```HTTP/2``` 比 ```HTTP/1``` 到底快了多少。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/http_6.gif?raw=true" />
</p>

在 ```HTTP/2``` 中，有了二进制分帧之后，```HTTP /2``` 不再依赖 ```TCP``` 链接去实现多流并行了，在 ```HTTP/2```中,

```
1. 同域名下所有通信都在单个连接上完成。

2. 单个连接可以承载任意数量的双向数据流。

3. 数据流以消息的形式发送，而消息又由一个或多个帧组成，多个帧之间可以乱序发送，因为根据帧首部的流标识可以重新组装。
```

这一特性，使性能有了极大提升：

```
1. 同个域名只需要占用一个 TCP 连接，使用一个连接并行发送多个请求和响应,这样整个页面资源的下载过程只需要一次慢启动，同时也避免了多个TCP连接竞争带宽所带来的问题。

2. 并行交错地发送多个请求/响应，请求/响应之间互不影响。

3. 在HTTP/2中，每个请求都可以带一个31bit的优先值，0表示最高优先级， 数值越大优先级越低。有了这个优先值，客户端和服务器就可以在处理不同的流时采取不同的策略，以最优的方式发送流、消息和帧。
```

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/http_7.png?raw=true" />
</p>

如上图所示，多路复用的技术可以只通过一个 TCP 连接就可以传输所有的请求数据。

> ***多路复用的原理解析***

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/http_8.webp?raw=true" />
</p>

```HTTP/1.1```协议的请求-响应模型大家都是熟悉的，我们用```“HTTP消息”```来表示一个请求-响应的过程，那么```HTTP/1.1```中的消息是“管道串形化”的：**只有等一个消息完成之后，才能进行下一条消息**；而```HTTP/2```中**多个消息交织在了一起**，这无疑提高了“通信”的效率。这就是多路复用：在一个```HTTP```的连接上，多路“HTTP消息”同时工作。

- ***为什么```HTTP/1.1```不能实现“多路复用”？***

简单回答就是：```HTTP/2```是**基于二进制“帧”的协议**，``HTTP/1.1``是基于“**文本分割”解析**的协议。

看一个```HTTP/1.1```简单的```GET```请求例子：

```
GET / HTTP/1.1
Accept:text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8
Accept-Encoding:gzip, deflate, br
Accept-Language:zh-CN,zh;q=0.9,en;q=0.8
Cache-Control:max-age=0
Connection:keep-alive
Cookie:imooc_uuid=b2076a1d-6a14-4cd5-91b0-17a9a2461cf4; imooc_isnew_ct=1517447702; imooc_isnew=2; zg_did=%7B%22did%22%3A%20%221662d799f3f17d-0afe8166871b85-454c092b-100200-1662d799f4015b%22%7D; loginstate=1; apsid=Y4ZmEwNGY3OTUwMTdjZTk0ZTc4YzBmYThmMDBmZDYAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAANDEwNzI4OQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA5NTMzNjIzNjVAcXEuY29tAAAAAAAAAAAAAAAAAAAAADBmNmM5MzczZTVjMTk3Y2VhMDE2ZjUxNmQ0NDUwY2IxIDPdWyAz3Vs%3DYj; Hm_lvt_fb538fdd5bd62072b6a984ddbc658a16=1541222935,1541224845; Hm_lvt_f0cfcccd7b1393990c78efdeebff3968=1540010199,1541222930,1541234759; zg_f375fe2f71e542a4b890d9a620f9fb32=%7B%22sid%22%3A%201541297212384%2C%22updated%22%3A%201541297753524%2C%22info%22%3A%201541222929083%2C%22superProperty%22%3A%20%22%7B%5C%22%E5%BA%94%E7%94%A8%E5%90%8D%E7%A7%B0%5C%22%3A%20%5C%22%E6%85%95%E8%AF%BE%E7%BD%91%E6%95%B0%E6%8D%AE%E7%BB%9F%E8%AE%A1%5C%22%2C%5C%22%E5%B9%B3%E5%8F%B0%5C%22%3A%20%5C%22web%5C%22%7D%22%2C%22platform%22%3A%20%22%7B%7D%22%2C%22utm%22%3A%20%22%7B%7D%22%2C%22referrerDomain%22%3A%20%22%22%2C%22cuid%22%3A%20%22Jph3DQ809OQ%2C%22%7D; PHPSESSID=h5jn68k1fcaadn61bpoqa9hch2; cvde=5be7a057c314b-1; IMCDNS=1
Host:www.imooc.com
Referer:https://www.imooc.com/
Upgrade-Insecure-Requests:1
User-Agent:Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/63.0.3239.132 Safari/537.36
```

以上就是```HTTP/1.1```发送请求消息的文本格式：**以换行符分割每一条key:value的内容**，解析这种数据用不着什么高科技，相反的，***解析这种数据往往速度慢且容易出错***。*“服务端”需要不断的读入字节，直到遇到分隔符（这里指换行符，代码中可能使用/n或者/r/n表示）*，这种解析方式是可行的，并且```HTTP/1.1```已经被广泛使用了二十多年，这事已经做过无数次了，问题一直都是存在的：

```
  1. 一次只能处理一个请求或响应，因为这种以分隔符分割消息的数据，在完成之前不能停止解析。
  2. 解析这种数据无法预知需要多少内存，这会带给“服务端”很大的压力，因为它不知道要把一行要解析的内容读到多大的“缓冲区”中，在保证解析效率和速度的前提下：内存该如何分配？
```

- ***```HTTP/2```帧结构设计和多路复用实现***
前边提到：```HTTP/2```设计是基于“二进制帧”进行设计的，这种设计无疑是一种“高超的艺术”，因为它实现了一个目的：**一切可预知，一切可控**。

帧是一个数据单元，实现了对消息的封装。下面是```HTTP/2```的帧结构：

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/http_9.webp?raw=true" />
</p>

帧的字节中保存了不同的信息，前9个字节对于每个帧都是一致的，**“服务器”解析```HTTP/2```的数据帧时只需要解析这些字节，就能准确的知道整个帧期望多少字节数来进行处理信息**。

***如果使用```HTTP/1.1```的话，你需要发送完上一个请求，才能发送下一个；由于```HTTP/2```是分帧的，请求和响应可以交错甚至可以复用。***

- **4. Server Push**

```HTTP2```还在一定程度上改变了传统的“请求-应答”工作模式，服务器不再是完全被动地响应请求，也可以新建“流”主动向客户端发送消息。比如，在浏览器刚请求HTML的时候就提前把可能会用到的JS、CSS文件发给客户端，减少等待的延迟，这被称为"服务器推送"（ Server Push，也叫 Cache push）

例如下图所示,**服务端主动把JS和CSS文件推送给客户端，而不需要客户端解析HTML时再发送这些请求**。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/http_10.png?raw=true" />
</p>

另外需要补充的是,服务端可以主动推送，客户端也有权利选择是否接收。如果服务端推送的资源已经被浏览器缓存过，**浏览器可以通过发送RST_STREAM帧来拒收**。主动推送也遵守同源策略，换句话说，服务器不能随便将第三方资源推送给客户端，而必须是经过双方确认才行。

- **5. 提高安全性**

出于兼容的考虑，```HTTP/2```延续了```HTTP/1```的“明文”特点，可以像以前一样使用明文传输数据，不强制使用加密通信，不过格式还是二进制，只是不需要解密。

但由于```HTTPS```已经是大势所趋，而且主流的浏览器Chrome、Firefox等都公开宣布只支持加密的```HTTP/2```，所以“事实上”的```HTTP/2```是加密的。也就是说，**互联网上通常所能见到的```HTTP/2```都是使用"https”协议名**，**跑在```TLS```上面**。```HTTP/2```协议定义了两个字符串标识符：“h2"表示加密的```HTTP/2```，“h2c”表示明文的```HTTP/2```。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/http_11.png?raw=true" />
</p>

### ```HTTP/3``` 新特性

- **```HTTP/2``` 的缺点**

虽然 ```HTTP/2``` 解决了很多之前旧版本的问题，但是它还是存在一个巨大的问题，主要是底层支撑的 ```TCP``` 协议造成的。

HTTP/2的缺点主要有以下几点：

1. **```TCP``` 以及 ```TCP+TLS```建立连接的延时**

```HTTP/2```都是使用```TCP```协议来传输的，而如果使用```HTTPS```的话，还需要使用```TLS```协议进行安全传输，而使用```TLS```也需要一个握手过程，这样就需要有两个握手延迟过程：

```
1. 在建立TCP连接的时候，需要和服务器进行三次握手来确认连接成功，也就是说需要在消耗完1.5个RTT之后才能进行数据传输。

2. 进行TLS连接，TLS有两个版本——TLS1.2和TLS1.3，每个版本建立连接所花的时间不同，大致是需要1~2个RTT。
```

总之，在传输数据之前，我们需要花掉 3～4 个 RTT。

2. **```TCP```的队头阻塞并没有彻底解决**

上文我们提到在```HTTP/2```中，多个请求是跑在一个```TCP```管道中的。**但当出现了丢包时，```HTTP/2``` 的表现反倒不如 ```HTTP/1``` 了**。***因为```TCP```为了保证可靠传输，有个特别的“丢包重传”机制，丢失的包必须要等待重新传输确认，```HTTP/2```出现丢包时，整个 ```TCP``` 都要开始等待重传***，那么就会**阻塞该```TCP```连接中的所有请求**（如下图）。而对于 ```HTTP/1.1``` 来说，可以开启多个 ```TCP``` 连接，出现这种情况反到只会影响其中一个连接，剩余的 ```TCP``` 连接还可以正常传输数据。

> ***队头阻塞问题***

**队头阻塞 Head-of-line blocking（缩写为HOL blocking）** 是计算机网络中是一种性能受限的现象，通俗来说就是：*一个数据包影响了一堆数据包，它不来大家都走不了*。

队头阻塞问题 ***可能存在于HTTP层和TCP层***，在```HTTP1.x```时两个层次都存在该问题。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/http_12.png?raw=true" />
</p>

**```HTTP2.0```协议的多路复用机制解决了```HTTP```层的队头阻塞问题，但是在```TCP```层仍然存在队头阻塞问题。**

**```TCP```协议在收到数据包之后，这部分数据可能是乱序到达的，但是```TCP```必须将所有数据收集排序整合后给上层使用，如果其中某个包丢失了，就必须等待重传，从而出现某个丢包数据阻塞整个连接的数据使用**

- **```HTTP/3```简介**

Google 在推```SPDY```的时候就已经意识到了这些问题，于是就另起炉灶搞了一个**基于 ```UDP``` 协议的```“QUIC”```协议**，让```HTTP```跑在```QUIC```上而不是```TCP```上。而这个 **“HTTP over QUIC”就是```HTTP```协议的下一个大版本，```HTTP/3```**。它在```HTTP/2```的基础上又实现了质的飞跃，真正“完美”地解决了“队头阻塞”问题。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/http_13.png?raw=true" />
</p>

```QUIC``` 虽然基于 ```UDP```，但是在原本的基础上新增了很多功能，接下来我们重点介绍几个```QUIC```新功能。不过```HTTP/3```目前还处于草案阶段，正式发布前可能会有变动，所以本文尽量不涉及那些不稳定的细节

- **```QUIC```新功能**

上面我们提到```QUIC```基于```UDP```，而```UDP```是“无连接”的，根本就不需要“握手”和“挥手”，所以就比```TCP```来得快。**此外QUIC也实现了可靠传输**，保证数据一定能够抵达目的地。它还引入了类似```HTTP/2```的“流”和“多路复用”，单个“流"是有序的，可能会因为丢包而阻塞，但其他“流”不会受到影响。具体来说QUIC协议有以下特点：

1. 实现了类似TCP的流量控制、传输可靠性的功能。

虽然```UDP```不提供可靠性的传输，但 **```QUIC```在```UDP```的基础之上增加了一层来保证数据可靠性传输**。它提供了数据包重传、拥塞控制以及其他一些```TCP```中存在的特性。

2. 实现了快速握手功能。

由于```QUIC```是基于```UDP```的，所以```QUIC```可以实现使用```0-RTT```或者```1-RTT```来建立连接，这意味着```QUIC```可以用最快的速度来发送和接收数据，这样可以大大提升首次打开页面的速度。```0RTT``` 建连可以说是 ```QUIC``` 相比 ```HTTP2``` 最大的性能优势。

3. 集成了```TLS```加密功能。

目前```QUIC```使用的是```TLS1.3```，相较于早期版本```TLS1.3```有更多的优点，其中最重要的一点是减少了握手所花费的```RTT```个数。

4. 多路复用，彻底解决```TCP```中队头阻塞的问题

和TCP不同，**```QUIC```实现了在同一物理连接上可以有多个独立的逻辑数据流**（如下图）。实现了数据流的单独传输，就解决了```TCP```中队头阻塞的问题。

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/http_14.png?raw=true" />
</p>

> [**Some ```QUIC``` details**](https://mp.weixin.qq.com/s/TU36OLc5pE-vbsEo0aHZGA)

### **总结**

- ```HTTP/1.1```有两个主要的缺点：安全不足和性能不高。

- ```HTTP/2```完全兼容```HTTP/1```，是“更安全的HTTP、更快的HTTPS"，头部压缩、多路复用等技术可以充分利用带宽，降低延迟，从而大幅度提高上网体验；

- ```QUIC``` 基于 ```UDP``` 实现，是 **```HTTP/3``` 中的底层支撑协议**，该协议基于 ```UDP```，又取了 ```TCP``` 中的精华，实现了即快又可靠的协议。

From: https://mp.weixin.qq.com/s/n8HBG9LuzQjOT__M4pxKwA

## **HTTPS**

**```HTTPS``` - A way of encrypting ```HTTP```. It basically wraps ```HTTP``` messages up in an encrypted format using ```SSL/TLS```.**

- [How an ```SSL``` connection is established](https://robertheaton.com/2014/03/27/how-does-https-actually-work/)

An ```SSL``` connection between a client and server is set up by a handshake, the goals of which are:

```
  1. To satisfy the client that it is talking to the right server (and optionally visa versa)
  2. For the parties to have agreed on a “cipher suite”, which includes which encryption algorithm they will use to exchange data
  3. For the parties to have agreed on any necessary keys for this algorithm
```
Once the connection is established, both parties can use the agreed algorithm and keys to securely send messages to each other. We will break the handshake up into 3 main phases - Hello, Certificate Exchange and Key Exchange.

1. Hello - The handshake begins with the client sending a ClientHello message. This contains all the information the server needs in order to connect to the client via SSL, including the various cipher suites and maximum SSL version that it supports. The server responds with a ServerHello, which contains similar information required by the client, including a decision based on the client’s preferences about which cipher suite and version of SSL will be used.

2. Certificate Exchange - Now that contact has been established, the server has to prove its identity to the client. This is achieved using its SSL certificate, which is a very tiny bit like its passport. An SSL certificate contains various pieces of data, including the name of the owner, the property (eg. domain) it is attached to, the certificate’s public key, the digital signature and information about the certificate’s validity dates. The client checks that it either implicitly trusts the certificate, or that it is verified and trusted by one of several Certificate Authorities (CAs) that it also implicitly trusts. Much more about this shortly. Note that the server is also allowed to require a certificate to prove the client’s identity, but this typically only happens in very sensitive applications.

3. Key Exchange - The encryption of the actual message data exchanged by the client and server will be done using a symmetric algorithm, the exact nature of which was already agreed during the Hello phase. A symmetric algorithm uses a single key for both encryption and decryption, in contrast to asymmetric algorithms that require a public/private key pair. Both parties need to agree on this single, symmetric key, a process that is accomplished securely using asymmetric encryption and the server’s public/private keys.

- **Key Exchange algorithm**

> **Anonymous Diffie-Hellman** uses Diffie-Hellman, but without authentication. Because the keys used in the exchange are not authenticated, the protocol is susceptible to Man-in-the-Middle attacks. Note: if you use this scheme, a call to SSL_get_peer_certificate will return NULL because you have selected an anonymous protocol. This is the only time SSL_get_peer_certificate is allowed to return NULL under normal circumstances.

You should not use Anonymous Diffie-Hellman. You can prohibit its use in your code by using "!ADH" in your call to SSL_set_cipher_list.

> **Fixed Diffie-Hellman** embeds the server's public parameter in the certificate, and the CA then signs the certificate. That is, the certificate contains the Diffie-Hellman public-key parameters, and those parameters never change. ***(with RSA as public key in certificate, but fixed Diffie-Hellman key pairs)***

> **Ephemeral Diffie-Hellman** uses temporary, public keys. Each instance or run of the protocol uses a different public key. The authenticity of the server's temporary key can be verified by checking the signature on the key. **Because the public keys are temporary, a compromise of the server's long term signing key does not jeopardize the privacy of past sessions.** This is known as Perfect Forward Secrecy (PFS). ***(with RSA as public key in certificate, but radom Diffie-Hellman key pairs)***

### **Forward secrecy**

- ***Forward secrecy allows today information to be kept secret even if the private key is compromised in the future.*** Achieving this property is usually costly and therefore, most web servers do not enable it on purpose. Google recently announced support of forward secrecy on their HTTPS sites. Adam Langley wrote a post with more details on what was achieved to increase efficiency of such a mechanism: with a few fellow people, he wrote an efficient implementation of some elliptic curve cryptography for OpenSSL.

1. **Without forward secrecy**

To understand the problem when forward secrecy is absent, let’s look at the classic ```TLS``` handshake when using a cipher suite like ```AES128-SHA```. During this handshake, the server will present its certificate and both the client and the server will agree on a master secret.

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/ssl_1.svg?raw=true" />
</p>

This secret is built from a 48byte premaster secret generated and encrypted by the client with the public key of the server. It is then sent in a Client Key Exchange message to the server during the third step of the TLS handshake. The master secret is derived from this premaster secret and random values sent in clear-text with Client Hello and Server Hello messages.

This scheme is secure as long as only the server is able to decrypt the premaster secret (with its private key) sent by the client. *Let’s suppose that an attacker records all exchanges between the server and clients during a year. Two years later, the server is decommissioned and sent for recycling. The attacker is able to recover the hard drive with the private key. They can now decrypt any session they recorded: the encrypted premaster secret sent by a client is decrypted with the private key and the master secret is derived from it. The attacker can now recover passwords and other sensitive information that can still be valuable today.*

**The main problem lies in the fact that the private key is used for two purposes**: ***authentication*** of the server and ***encryption*** of a shared secret. Authentication only matters while the communication is established, but encryption is expected to last for years.

2. **Diffie-Hellman with discrete logarithm**

One way to solve the problem is to keep using the private key for authentication but uses an independent mechanism to agree on a shared secret. Hopefully, there exists a well-known protocol for this: the Diffie-Hellman key exchange. It is a method of exchanging keys without any prior knowledge. Here is how it works in ```TLS```: ***(```DHE-RSA-AES128-SHA```)***

```
1. The server needs to generate once (for example, with openssl dhparam command):
      p, a large prime number,
      g, a primitive root modulo p—for every integer a coprime to p, 
        there exists an integer k such that g^k\equiv a\pmod{p}.
2. The server picks a random integer a and compute g^a \bmod p. After sending its regular Certificate message, 
   it will also send a Server Key Exchange message (not included in the handshake depicted above) containing,
   unencrypted but signed with its private key for authentication purpose:
      random value from the Client Hello message,
      random value from the Server Hello message,
      p, g,
      g^a\bmod p=A.
3. The client checks that the signature is correct. It also picks a random integer b and sends g^b \bmod p=B
   in a Client Key Exchange message. It will also compute A^b\bmod p=g^{ab}\bmod p which is the premaster secret
   from which the master secret is derived.
4. The server will receive B and compute B^a\bmod p=g^{ab}\bmod p which is the same premaster secret known by the client.
```

Again, ***the private key is only used for authentication purpose***. An eavesdropper will only know p, g, g^a\bmod p and g^b\bmod p. Computing g^{ab}\bmod p from these values is the discrete logarithm problem for which there is no known efficient solution. 

So ```RSA``` in this case **points to the key pair of the server, the public key of which is in the server certificate.** This certificate is used to establish a chain to a trusted (root) certificate in the certificate store, e.g. the one in your browser or system store. This chain is verified and validated so that the public key of the server can be trusted to a certain degree (the level of trust established by trusting all of the CA's in the certificate store is an ongoing debate).

Because the Diffie-Hellman exchange described above always uses new random values a and b, it is called Ephemeral Diffie-Hellman (EDH or DHE). Cipher suites like ```DHE-RSA-AES128-SHA``` use this protocol to achieve **perfect forward secrecy**.

> **Perfect forward secrecy** is an enhanced version of forward secrecy. It assumes each exchanged key are independent and therefore a compromised key cannot be used to compromise another one.

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/ssl_2.png?raw=true" />
</p>

### **Man-in-the-middle (MitM) attacks** 

```HTTP``` 协议被认为不安全是因为传输过程容易被监听者勾线监听、伪造服务器，而 ```HTTPS``` 协议主要解决的便是网络传输的安全性问题。

首先我们假设不存在认证机构，任何人都可以制作证书，这带来的安全风险便是经典的 **“中间人攻击”** 问题。

“中间人攻击”的具体过程如下：

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/ssl_3.webp?raw=true" />
</p>

过程原理：
```
  本地请求被劫持（如DNS劫持等），所有请求均发送到中间人的服务器
  中间人服务器返回中间人自己的证书
  客户端创建随机数，通过中间人证书的公钥对随机数加密后传送给中间人，然后凭随机数构造对称加密对传输内容进行加密传输
  中间人因为拥有客户端的随机数，可以通过对称加密算法进行内容解密
  中间人以客户端的请求内容再向正规网站发起请求
  因为中间人与服务器的通信过程是合法的，正规网站通过建立的安全通道返回加密后的数据
  中间人凭借与正规网站建立的对称加密算法对内容进行解密
  中间人通过与客户端建立的对称加密算法对正规内容返回的数据进行加密传输
  客户端通过与中间人建立的对称加密算法对返回结果数据进行解密
  由于缺少对证书的验证，所以客户端虽然发起的是 HTTPS 请求，但客户端完全不知道自己的网络已被拦截，传输内容被中间人全部窃取。
```

- 浏览器是如何确保 ```CA``` 证书的合法性？

*证书包含什么信息？*

```
  颁发机构信息
  公钥
  公司信息
  域名
  有效期
  指纹
  ……
```
*证书的合法性依据是什么？*

首先，权威机构是要有认证的，不是随便一个机构都有资格颁发证书，不然也不叫做权威机构。另外，证书的可信性基于信任制，权威机构需要对其颁发的证书进行信用背书，只要是权威机构生成的证书，我们就认为是合法的。所以权威机构会对申请者的信息进行审核，不同等级的权威机构对审核的要求也不一样，于是证书也分为免费的、便宜的和贵的。

*浏览器如何验证证书的合法性？*

浏览器发起 ```HTTPS``` 请求时，服务器会返回网站的 ```SSL``` 证书，浏览器需要对证书做以下验证：

```
验证域名、有效期等信息是否正确。证书上都有包含这些信息，比较容易完成验证；
判断证书来源是否合法。每份签发证书都可以根据验证链查找到对应的根证书，操作系统、浏览器会在本地存储权威机构的根证书利用本地根证书可以对对应机构签发证书完成来源验证；
判断证书是否被篡改。需要与 CA 服务器进行校验；
判断证书是否已吊销。通过CRL（Certificate Revocation List 证书注销列表）和 OCSP（Online Certificate Status Protocol 在线证书状态协议）实现，其中 OCSP 可用于第3步中以减少与 CA
服务器的交互，提高验证效率
```

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/ssl_4.webp?raw=true" />
</p>

以上任意一步都满足的情况下浏览器才认为证书是合法的。

- 这里插一个我想了很久的但其实答案很简单的问题：
> 既然证书是公开的，如果要发起中间人攻击，我在官网上下载一份证书作为我的服务器证书，那客户端肯定会认同这个证书是合法的，如何避免这种证书冒用的情况？

> 其实这就是非加密对称中公私钥的用处，虽然中间人可以得到证书，但私钥是无法获取的，一份公钥是不可能推算出其对应的私钥，中间人即使拿到证书也无法伪装成合法服务端，因为无法对客户端传入的加密数据进行解密。(DHE-RSA-AES128-SHA)

*只有认证机构可以生成证书吗？*

如果需要浏览器不提示安全风险，那只能使用认证机构签发的证书。但浏览器通常只是提示安全风险，并不限制网站不能访问，所以从技术上谁都可以生成证书，只要有证书就可以完成网站的
```HTTPS``` 传输。

From: https://vincent.bernat.ch/en/blog/2011-ssl-perfect-forward-secrecy <br>
From: https://robertheaton.com/2014/03/27/how-does-https-actually-work/ <br>
From: https://www.codenong.com/cs107123938/

## **Cookie**

> ***It remembers stateful information for the stateless ```HTTP``` protocol***

### **Cookie的出现**

浏览器和服务器之间的通信少不了```HTTP```协议，但是**因为```HTTP```协议是无状态**的，所以**服务器并不知道上一次浏览器做了什么样的操作**，这样严重阻碍了交互式Web应用程序的实现。

针对上述的问题，网景公司的程序员创造了```Cookie```。

### **Cookie的传输**

**服务器端**在实现```Cookie```标准的过程中，需要**对任意```HTTP```请求发送```Set-Cookie``` ```HTTP```头作为响应**的一部分：

```
Set-Cookie: name=value; expires=Tue, 03-Sep-2019 14:10:21 GMT; path=/; domain=.xxx.com;
```

**浏览器端**会**存储**这样的```Cookie```，并**且为之后的每个请求添加```Cookie``` ```HTTP```请求头发送回服务器**：

```
Cookie: name=value
```

**服务器**通过**验证```Cookie```值**，来**判断浏览器发送请求属于哪一个用户**。

An ```HTTP``` cookie (```web cookie, browser cookie```) is a small piece of data that **a server sends to a user's web browser**. The **browser may store the cookie and send it back to the same server with later requests**. Typically, an ```HTTP``` ```cookie``` is used to tell **if two requests come from the same browser** — ***keeping a user logged in***, for example. ***It remembers stateful information for the stateless ```HTTP``` protocol***.

```Cookies``` are mainly used for three purposes:

- **Session management**

Logins, shopping carts, game scores, or anything else the server should remember

- **Personalization**

User preferences, themes, and other settings

- **Tracking**

Recording and analyzing user behavior

```Cookies``` were once used for general client-side storage. While this made sense when they were the only way to store data on the client, modern storage APIs are now recommended. ***```Cookies``` are sent with every request***, so they can worsen performance (especially for mobile data connections). Modern APIs for client storage are the Web Storage API (localStorage and sessionStorage) and IndexedDB.

From: https://mp.weixin.qq.com/s/u9aU2s-m3iqkKrwLGp266Q <br>
From: https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies

## [**SSH**](https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/3.%20Network%20Programming/3.%20%E5%9B%BE%E8%A7%A3TCP%20IP/Note.md#ssh)

## **DNS**

### DNS Basic Terms

- DNS是什么？

> DNS就是将域名转换为IP的，因为我们人类的记忆力太差，根本记不住IP，而电脑通信又必须用IP，所以人类发明了域名，让我们可以记住baidu.com、taobao.com这种还算能记得住的域名。然后通过DNS，将这些域名转换为电脑需要的IP。

- DNS是怎么工作的？

> 每个电脑里面都设置了本地DNS服务器（简称LDNS），需要的时候，就向LDNS发出请求，LDNS在网上问权威域名服务器（简称权威DNS），有时候问一家是不够的，要问一大圈下来，最后才能得到答案。

- 权威DNS是干什么的？

> 问我一个域名，我告诉你IP，如果我不知道，我告诉你谁可能知道，你再去问它。

- 什么是根域名服务器（简称根DNS）？

> 当LDNS啥都不知道的时候（也即没有任何缓存），就去问根DNS，根能告诉LDNS下一步该问谁。

- 全世界有多少根DNS？

> 13个，其中10个在美国，英国和瑞典各1个，日本1个。

### Why 13 root DNS?

> DNS主要使用UDP数据报传送报文，不含前面的各种头部，DNS报文要求被控制在512字节之内（ RFC1035 ），主要考虑是这个大小几乎可以在互联网上畅通无阻，不会因为路径中某个MTU太小（ MTU 通常总会 >= 576，见 RFC791 ）而导致IP分片，从而预防了各种不可预期的后果. 而每一个根DNS在DNS报文中都要占用一定的字节数，比如根的名称、TTL、IP地址等。这样，13个根域名服务器基本上就把空间占差不多了，剩余的字节还要用于包装DNS报头以及其它协议参数，所以根域名服务器不易太多，13个算是比较合适的数目。

- **But**

> 这13个根域名服务器，并不是只有13台物理的服务器。这13个根，只是一个逻辑上的概念，每个根DNS，背后都有多台真正的物理服务器在工作！截至2020年8月12日，全球一共有1097个根服务器。每一个根都有若干个镜像，分布在全球不同的地方。

### How does DNS works?

- 先介绍一下域名的级别：

.代表根域名， .com这种是顶级域名，也叫一级域名，baidu.com这种叫二级域名， www.baidu.com这种叫三级域名，依次类推。

注：也有其他叫法的，反正你知道这个意思就可以了。

- 再介绍一下最常见的两种域名服务器：

> *权威DNS*：负责对请求作出权威的回答。权威DNS中存储着记录，最常见的3种：A记录（记录某域名和其IP的对应），NS记录（记录某域名和负责解析该域的权威DNS），CNAME记录（负责记录某域名及其别名）。权威能直接回答的，就回A记录；需要其他权威DNS回答的，就回NS记录，然后LDNS再去找其他权威DNS问；如果该记录是别名类型的，就回CNAME，LDNS就会再去解析别名。

> *递归DNS*：通常就是**LDNS**，它接受终端的域名查询请求，负责在网上问一圈后，将答案返回终端。

```

现在举一个具体的例子：比如终端请求www.baidu.com这个域名的IP。

在没有缓存时，LDNS会从根DNS问起：

1、LDNS问根DNS说：“www.baidu.com的IP是多少啊？”。

2、根DNS说：“我哪有时间管你这么细的问题，你去问com顶级域的DNS吧，我只管到顶级域，喏，这些是com顶级域DNS的名字和IP，你去问它们吧”。（以NS记录回应）

3、LDNS又忙问com的权威DNS，com权威DNS说：“你问的这是三级域名，我不管这么多，你去问baidu.com的权威DNS吧，它的名字是ns.baidu.com，他的IP是XXX（这里可能给出多个权威DNS）”。

4、LDNS继续问baidu.com的权威DNS，这次痛快，因为www.baidu.com正是它管的，它可能直接给出A记录，也可能给出CNAME记录，如果是前者，就直接得到IP，如果是后者，就需要对别名再做查询。

5、最终，LDNS得到www.baidu.com的IP，并将其返回给终端。

```

<p align="center">
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/dns_1.jpg?raw=true" />
</p>

细心的人会问，在第1步中，*LDNS问根DNS的时候，他是怎么知道根DNS的IP的？*

这13个IP通常是预先配置在LDNS里面的。在LDNS初始化DNS缓存或者缓存失效的时候，LDNS向自己被预先配置的这些IP中的一个，发起对根的查询（也即询问.的NS记录），获得最新的根DNS的信息。

对于DNS服务器软件而言，这13个IP，配置在根提示文件（root hints file）中，可能是named.cache或root.ca或root.hints等等之类的文件。

上面就是各种教科书中都会讲到的DNS查询过程，**但实际上，没有这么麻烦，因为各个层面都是有缓存的。**

```

实际DNS查询的过程，是这样的：

举个例子，比如用户在浏览器中输入这个域名：123.abc.qq.com.cn

1、浏览器会先看自身有没有对这个域名的缓存，如果有，就直接返回，如果没有，就去问操作系统，操作系统也会去看自己的缓存，如果有，就直接返回，如果没有，再去hosts文件看，也没有，才会去问LDNS。

2、LDNS会去先看看自己有没有123.abc.qq.com.cn的A记录，要有就直接返回，要没有，就去看有没有abc.qq.com.cn的NS记录，如果有，就去问它要答案，如果没有，就去看有无qq.com.cn的NS的记录，如果有，就去问它，没有就去看有无com.cn的DNS，还没有就去看有无cn的DNS，如果连cn的NS记录都没有，才去问根。

所以，有了缓存以后，教科书上那种从根问起的情况，实际上很少发生。

```

***只有在各处都没有缓存的时候，我们才会问根。***

### How does Root DNS Mirror works？

根镜像承担起和根一样的功能。

根DNS中，最重要的文件就是根区文件（Root Zone file）。所有顶级域名记录都存在根区文件中。

辅根从主根同步数据，根镜像从根同步数据。最终，所有根和镜像都有着同样的根区文件。

***而且最有意思的是，根镜像和根有着同样的IP。***

我们知道，全球有一千多个根镜像，但是大多数人不知道，它们一起共享13个IP！  对的。因为只有13个根。

这是如何做到的？答案是 ***任播（Anycast，又译泛播）*** 技术。

任播最初由RFC1546提出，主要用在DNS根服务器上。

> 任播是指在IP网络上通过一个IP地址标识一组提供特定服务的主机，服务访问方并不关心提供服务具体是哪一台主机提供的，访问该地址的报文可以被IP网络路由到“最近”的一个（最好也只是一个，别送到多个）服务器上。这里“最近”可以是指路由器跳数、服务器负载、服务器吞吐量、客户和服务器之间的往返时间（ RTT，round trip time ）、链路的可用带宽等特征值。

这样，一方面，用户可以就近访问；另一方面，即便部分根出现故障也没事。

有些同学可能联想到**负载均衡**，没错，大致上就是这个意思。

*对于中国用户来说，对根的请求，一般不会跑到美国去，而是通过任播技术路由到中国境内的根镜像上。*

> DNS has always been designed to use both UDP and TCP port 53 from the start1 , with UDP being the default, and fall back to using TCP when it is unable to communicate on UDP, typically when the packet size is too large to push through in a single UDP packet.

From: https://mp.weixin.qq.com/s/JQE4iIFy5I4bDtAegZULWg

## **Message Digest Algorithm**

在处理密码加密时，不可以使用加密算法，因为所有的加密算法都是可以逆向运算的，也就是说，只要能够获取加密算法的类型、加密过程中使用的参数，就可以逆向运算，根据密文得到原文，所以，加密算法主要用于保证传输过程的数据安全，并不用能于长期存储的密码！

一般，***会使用消息摘要算法来实现密码加密***！

> **这种算法是根据“消息”计算得到“摘要”的算法，通常用于数据验证，即发送方和接收方的数据是否完全一致，例如下载文件、发送消息等。**

- 消息摘要算法具备几个特点：

```
  1. 消息相同，则摘要必然相同；
  2. 在算法不变的情况下，摘要的长度是固定的；
  3. 消息不同，则摘要几乎不会相同。
```
> **由于一般的消息摘要算法都是128位或以上位数的算法，发生碰撞（不同的消息却对应相同的摘要）的概念非常低，并且，在应用于密码加密时，由于密码的原文的长限是非常有限的，更加降低了发生碰撞的概率，所以，使用消息摘要算法对密码作加密处理是完全没有问题的！**

假设用户注册的原始密码是```1234```，通过消息摘要算法得到的是```81dc9bdb52d04dc20036dbd8313ed055```，就应该把这个摘要结果存储到数据库中，下次，用户尝试登录，如果输入的仍是```1234```，基于“消息相同，摘要一定相同”，使用同样的算法，得到的一定是```81dc9bdb52d04dc20036dbd8313ed055```，与数据库中存储的进行对比，是一致的，就允许登录，当然，用户登录时，如果输入的不是```1234```，则几乎不可能得到以上的摘要数据，与数据库中存储的摘要进行对比结果就不一致，则不允许登录！

> ***常见的消息摘要算法有```SHA```系列的和```MD```系列的，在这2个系列中，常用的有```SHA-256```、```SHA-384```、```SHA-512```、```MD5```。***

- **消息摘要算法也是存在“破解”的**

以```MD5```算法为例，它是128位的算法，理论上来说，发生碰撞的概念就是2的128次方分之一，如果实际发生碰撞的概率比这大得多，甚至找到了相关的算法支撑，则这种消息摘要算法就被理解为“破解”了！

> ***消息摘要算法是无法通过摘要进行逆向运算得到消息原文的！***

### **Salt value** (盐值)

Here is an *incomplete example* of a salt value for storing passwords. This first table has two username and password combinations. The password is not stored.

| Username  | Password  |
|---|---|
|  user1 |  password123 |
|  user2 |  password123 |

***The salt value is generated at random*** and can be any length; in this case the salt value is 8 bytes long. The salt value is appended to the plaintext password and then the result is hashed, which is referred to as the hashed value. Both the salt value and hashed value are stored.

|  Username | Salt value  |  String to be hashed | Hashed value = ```SHA256``` (Password + Salt value)  |
|---|---|---|---|
| user1  | E1F53135E559C253  |  password123E1F53135E559C253 | 72AE25495A7981C40622D49F9A52E4F1565C90F048F59027BD9C8C8900D5C3D8  |
|  user2 | 84B03D034B409D4E  |  password12384B03D034B409D4E | B4B6603ABC670967E99C7E7F1389E40CD16E78AD38EB1468EC2AA1E62B8BED3A  |

As the table above illustrates, **different salt values will create completely different hashed values**, even when the plaintext passwords are exactly the same. Additionally, dictionary attacks are mitigated to a degree as an attacker cannot practically precompute the hashes. However, a salt cannot protect common or easily guessed passwords.

***Without a salt, the hashed value is the same for all users that have a given password, making it easier for hackers to guess the password from the hashed value:***

| Username  | String to be hashed  | Hashed value = ```SHA256```  |
|---|---|---|
|  user1 |  password123 | 57DB1253B68B6802B59A969F750FA32B60CB5CC8A3CB19B87DAC28F541DC4E2A  |
|  user2 | password123  | 57DB1253B68B6802B59A969F750FA32B60CB5CC8A3CB19B87DAC28F541DC4E2A  |

- ***If a salt is too short, an attacker may precompute a table of every possible salt appended to every likely password. Using a long salt ensures such a table would be prohibitively large.***

From: https://blog.csdn.net/zhangxuelong461/article/details/104450284

## **IO 多路复用** && **同步阻塞网络 IO**

From: https://mp.weixin.qq.com/s/3gC-nUnFGv-eoSBsEdSZuA <br/>
From: https://mp.weixin.qq.com/s/OmRdUgO1guMX76EdZn11UQ <br/>
From: https://mp.weixin.qq.com/s/cIcw0S-Q8pBl1-WYN0UwnA

## **中断**

From：https://mp.weixin.qq.com/s/bTfeI5p4eO5j6I9edeV73g

## **编码、Unicode，Emoji**

From: https://mp.weixin.qq.com/s/gP8QPzTROGHpKreWf7lUMg

## **计算机网络文章话题**

From: https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzI0ODk2NDIyMQ==&action=getalbum&album_id=1629017939758596097&subscene=159&subscene=189&scenenote=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI0ODk2NDIyMQ%3D%3D%26mid%3D2247487683%26idx%3D1%26sn%3De0949e72e039759545450852d8bc0ada%26chksm%3De999e5d1deee6cc7ab9e42b50329924fee39c45955516b406046605d27928825a0f628d13e7c%26cur_album_id%3D1629017939758596097%26scene%3D189%23wechat_redirect&nolastread=1#wechat_redirect <br/>

From: https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MjM5Njg5NDgwNA==&action=getalbum&album_id=1532487451997454337&scene=173&from_msgid=2247484905&from_itemidx=1&count=3&nolastread=1#wechat_redirect
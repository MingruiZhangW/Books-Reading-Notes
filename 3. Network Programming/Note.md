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
  <img src="https://github.com/MingruiZhangW/Books-Reading-Notes/blob/main/resources/img/network_programming_note/tcp_24.jpeg?raw=true" />
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

## **HTTP && HTTPS && HTTP/2 && HTTP/3**

From: https://mp.weixin.qq.com/s/n8HBG9LuzQjOT__M4pxKwA <br/>
From: https://stackoverflow.com/questions/53488601/what-is-difference-between-https-and-http-2 <br/>
From: https://mp.weixin.qq.com/s/TU36OLc5pE-vbsEo0aHZGA <br/>
From: https://mp.weixin.qq.com/s/zNC6qnW3DXD6B8eHlL1tjw <br/>
From: https://www.codenong.com/cs107123938/

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

From: https://mp.weixin.qq.com/s/JQE4iIFy5I4bDtAegZULWg

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
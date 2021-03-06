###2.1应用层协议原理
    研发网络英语程序的核心是写出能够运行在不同的端系统和通过网络彼此通讯的程序

####2.1.1网络应用程序体系结构

    1. 主流的两种体系结构
        1. 客户-服务器体系结构 C/S
        2. 对等体系结构 P2P
    1.1 客户-服务器体系结构
        1. C/S中有一个总是打开的追击成为服务器，服务来自许多其他成为客户的主机的请求
        2. 客户相互之间不直接通信，客户通过服务器公开的、固定的IP地址，向服务器发送分组来与其他客户联系
        3. 例如Web、FTP、Telnet、Email
        4. C/S中会出现单独一台服务器跟不上它所有客户的请求的情况，
            因此配备大量主机的数据中心常被用于创建强大的虚拟服务器
    1.2 对等体系结构
        1. 对位于数据中心的专用服务器有最小的或没有依赖
        2. 应用程序在间断链接的主机对之间使用直接通信，这些主机对被称为对等方
        3. 例如BitTorrent，迅雷，Skype
        4. 最重要的特性之一：自扩展性
            4.1 在一个P2P文件共享中，每个对等方都由于请求文件产生负载，
                但每个对等方通过向其他对等方分发文件为系统增开服务能力
            4.2 P2P不需要庞大的服务器基础设施和服务器带宽
            4.3 由于高度非集中式结构，面临安全性、性能和可靠性挑战

####2.1.2进程通信
    运行在多个端系统的程序是由进程来进行通信。
    一个进程可以被认为是运行在端系统中的一个程序。
    当多个进程运行在相同的端系统时，他们使用进程间通信机制相互通信。
    在两个不同端系统上的进程，通过跨越计算机网络交换报文而相互进行通信。

    1. 客户和服务器进程
        1.1 网络应用程序由成对的进程组成，这些进程通过相互发送报文
        1.2 每对通信进程，发起通信的进程标识为客户，等待联系的标识为服务器
        1.3 P2P中，一个进程能够既是客户有又是服务器，它能够上载文件，也能下载文件

    2. 进程与计算机网络之间的接口
        2.1 进程通过套接字软件接口向网络发送报文和从网络接收报文
        2.2 套接字是建立网络应用程序的可编程接口，因此套接字也可称为应用程序和网络之间的API
        2.3 套接字是应用程序进程和运输层协议之间的接口
        
    3. 进程寻址
        3.1 进程向另一台主机的进程发送分组，接收进程需要一个地址。
            为了表示接收进程，需要定义两种信息： 1.主机的地址 2.目的主机中指定接收进程的标识符   
        3.2 因特网中，主机地址由IP地址标识。
        3.3 目的主机中的指定接收进程(接收套接字)，一般用目的地端口号标识。Web:80端口

####2.1.3可供应用程序使用的运输服务
    运输层协议提供的服务：可靠数据传输，吞吐量，定时，安全性

    1.可靠数据传输
        1.1 如果一个协议提供了确保数据正确、完全地交付给应用程序的另一端，则为可靠数据传输

    2. 吞吐量
        2.1 可用吞吐量就是发送进程能够想接收进程交付比特的速率
        2.2 具有吞吐量要求的应用，被称为带宽敏感应用
        2.3 弹性应用可以根据可用吞吐量或多或少利用可使用的吞吐量
    
    3. 定时
        3.1 保证发送方注入进套接字的每个比特到达对方套接字不迟于某个指定的时间如100ms
    
    4. 安全性
        4.1 为应用程序提供一种或多种安全服务
        4.2 在数据交付给接收进程之前，运输层协议会将数据解密

####2.1.4因特网提供的运输服务
    因特网提供两个运输层协议，UDP和TCP
    1. TCP服务
       1. TCP包括面向连接服务和可靠数据传输服务
       2. 面向连接服务：经历握手阶段后，在两个进程之间建立TCP连接，此链接为全双工的，结束时必须拆除该链接
       3. 可靠的数据传送服务：通信进程能够依靠TCP无差错，按顺序的交付所有发送数据
       4. 具有拥塞控制
    2. UDP服务
       1. 不提供不必要服务的轻量级运输协议，仅提供最小服务
       2. 无连接的，两个进程通信之前没有握手过程
       3. 不可靠数据传送服务，不保证报文的到达和到达顺序
       4. 没有拥塞控制
    3. 因特网运输协议所不提供的服务
       1. 不提供对吞吐量或定时的保证

####2.1.5应用层协议
    应用层协议定义了：
        1. 交换报文的类型，如请求报文和响应报文
        2. 各种报文类型的语法
        3. 字段的语义
        4. 确定一个进程何时以及如何发送报文，对报文进行响应的规则




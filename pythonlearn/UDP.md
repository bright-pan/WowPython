## 1.TCP/IP 参考模型
层与层之间相互协作的时候,即数据在经历不同网络层级的时候,会有数据的打包与解包工作。

- 第四层 应用层 (Application)
- 第三层 传输层 (Transport)
- 第二层 网络层 (Network)
- 第一层 链路层 (Link)



## 2.协议
让网络通讯的每一层在工作时，都能按照其相应的某种具体的工作流程来工作，比如具体的规章制度、规则、工作的标准，我们就需要制定出这些规则标准，这就是我们所说的不同网络层中的协议。

2.1 ip地址：用来在网络中标记一台电脑的一串数字，比如192.168.1.1；在本地局域网上是唯一的。
每个ip地址包括两部分：网络地址和主机地址；

2.2 子网掩码：子网掩码不能单独存在，它必须结合IP地址一起使用。子网掩码只有一个作用，就是将某个IP地址划分成网络地址和主机地址两部分。子网掩码的设定必须遵循一定规则。



## 3.端口
如果一个进程需要收发网络数据，那么它需要端口。操作系统为了统一管理，用端口号对端口进行标记。

- 知名端口
范围从0到1023

> 80端口分配给HTTP服务

> 21端口分配给FTP服务

- 动态端口

动态端口的范围是从1024到65535,动态分配是指当一个系统进程或应用程序进程需要网络通信时,它向主机申请一个端口,主机从可用的端口号中分配一个供他使用。当进程关闭时,同时也释放了所占用的端口号。



## 4.Packet Tracer
用户可以在软件的图形界面上直接使用拖拽方法建立网络拓扑，并可提供数据包在网络中行进的详细处理过程，观察网络实时运行情况。


### 4.1 通过集线器hub组网

> hub能够完成多个电脑链接，每个数据包的发送都是以广播的形式进行的，容易堵塞网络。

### 4.2 通过交换机组网

##### 交换机的作用：
- 转发过滤：当一个数据帧的目的地址在MAC地址表中有映射时，它被转发到连接目的节点的端口而不是所有端口（如该数据帧为广播帧则转发至所有端口）；
- 学习功能：以太网交换机了解每一端口相连设备的MAC地址，并将地址同相应的端口映射起来存放在交换机缓存中的MAC地址表中；

##### 通信过程 pc+switch
arp -a : arp缓存表记录IP对应的MAC

- 每个数据包的发送都是以广播的形式进行的，容易堵塞网络；
- 如果PC不知目标IP所对应的MAC，那么PC先发送arp,得到对方的MAC后，再进行数据传送；
- 当switch 第一次收到arp广播数据，会把arp广播数据包转发给所有端口（除来源端口）；如果以后还有pc询问此IP的MAC，那么只是向目标的端口进行转发数据；

### 4.3 路由器（Router） 网关设备（Gateway）

设置路由传输示意图

## 5.用户数据报协议 UDP
### 5.1 UDP特点：
UDP是面向无连接的通讯协议，UDP数据包括目的端口号和源端口号信息，由于通讯不需要连接，所以可以实现广播发送。UDP传输数据时有大小限制，每个被传输的数据报必须限定在64KB之内。UDP是一个不可靠的协议，发送方所发送的数据报并不一定以相同的次序到达接收方。

### 5.2 socket 简介
socket是封装的传输层和网络层的工具，也可称作套接字。

- 创建 socket
在python中使用 socket 中的 socket 的函数：

```
socket.socket(AddressFamily, Type)
```

AddressFamily:
1. AF_INET (用于internet进程间通信)
2. AF_UNIX (用于同一台机器进程间的通信)

Type:
1. SOCK_STREAM 流式套接字，用于TCP协议
2. SOCK_DGRAM 数据报套接字，用于UDP协议

```
# 创建 UDP 套接字
import socket
s = socket.socket(socket.AF_INET, socket.DGRAM)

```

```
# 创建 TCP 套接字
import socket
s = socket.socket(socket.AF_INET, socket.STREAM)
```


### 5.3 UDP 服务端

```
import socket
# 创建套接字
server_socket = socket.socket(socket.AF.INET, socket.DGRAM)

# 绑定ip地址和端口
address =("", 8080)
server_socket.bind(address)

# recv接收数据
recieve_data, client_addr = server_socket.recvfrom(1024)

# 将bytes转化成字符串
msg = recieve_data.decode("utf-8")
print(client_addr, ":", msg)

# 关闭服务器套接字
if msg = "quit":
    server_socket.close()
    break


# 测试
# -u 表示使用udp协议
nc -u 127.0.0.1 8080

```

### 5.4 UDP 客户端
```
import socket

# 创建套接字
client_socket = socket.socket(socket.AF_INET, socket.DGRAM)

# 服务器地址
address = ("127.0.0.1", 8080)

# 输入发送内容
data = input("Enter Words: ")

while date:
    client_socket.sendto(data.endecode("utf-8"), address)
    data = input("Enter Words: ")

# 关闭客户端套接字
client_socket.close()

# 测试
# -l 表示服务端端口开启，进行监听
nc -lu 127.0.0.1 8080

```

### 5.5 实现一个简易的DNF服务器模型
```
import socket

server_socket = socket.socket(socket.AF_INET, socket.DGRAM)
server_addr = ("", 8080)
server_socket.bind(server_addr)

# 用来存放域名和ip对应关系
domain_ip = {
  "baidu": "192.168.4.23",
  "sina": "192.168.233.23"
}

while True:
    recieve_data, client_addr = server_socket.recvfrom(1024)
    domain = recieve_data.decode("utf-8")
    print(domain, ": ", client_addr)

    ip = domain_ip.get(domain, "I don\'t know.")
    server_socket.sendto(recieve_data.endecode("utf-8"),client_addr)

server_socket.close()

# 客户端

client_socket = socket.socket(socket.AF_INET, socket.DGRAM)
server_addr = ("127.0.0.1", 8053)
demain = input("Enter Words: ")

while demain:
    client_socket.sendto(domain.endecode("utf-8"), server_addr)
    ip = client_socket.recv(1024)
    print(ip.decode("utf-8"))
    demain = input("Enter Words: ")

client_socket.close()

```

### 5.6 网络编程中的广播
```
import socket
server_socket = socket.socket(socket.AF_INET, socket.DGRAM)
server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_BROADCAST, 1)

data = input("WORDS:")
while data:
    server_socket.sendto(data.decode("utf-8"), ("<broadcast>", 8080))
    data = input("Words: ")

server_socket.close()

```
### 5.7 UDP 总结

1. UDP是传输层的一种协议，不需要进行连接就可以用来发送和接收数据，但不保证数据的可靠传输。
2. 绑定：一般情况下，服务器端，需要绑定端口，目的为了让其他的客户端能够正确发送到此进程。
客户端一般不需要绑定，而是让操作系统随机分配，这样就不会因为需要绑定的端口被占用而导致程序无法运行的情况。

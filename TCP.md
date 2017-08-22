## TCP 介绍
TCP是一种面向的、可靠的、基于字节流的传输层通信协议。
1. 面向连接
2. 基于数据流（字节流）
3. 可靠的传输

## 三次握手，数据传输，四次挥手
- establish connection
- date transfer
- close connection

## TCP服务器
```
import socket

server_sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# 绑定IP地址和端口
address = （"127.0.0.1", 8080）
server_sock.bind(address)

# 开启监听
server_sock.listen()

# 使用accept方法接收客户端数据
# client_socket 用来接收客户端服务，与客户端建立一对一的数据
client_socket, cliect_add = server_sock.accept()
print(cliect_add, "已经连接")

# recv 接收客户端数据
client_date = client_socket.recv(1024)
print("接收数据："， client_date.decode())

# 向客户端发送数据send()
client_socket.send("tankes.".encode())

# 关闭服务端
client_socket.close()

# 关闭监听端
server_sock.close()


# 测试
nc 127.0.0.1 8080

```
## TCP 客户端

```
import socket
client_sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# 用connect()建立连接
address = ("127.0.0.1", 8080)
clinet_sock.connect(address)

# 提示用户发送数据  
# 转化成二进制encode()
msg = input("Words: ")
clinet_sock.send(msg.encode())

# 接收服务端的数据recv()
recv_data = client_sock.recv()
print("收到：", recv_data.decode())

# 关闭客户端套接字
client_sock.close()


# 测试
nc -l 127.0.0.1 8080

```

- closed  表示关闭状态（初始状态）。
- listen 该状态表示服务器端的某个SOCKET处于监听状态，可以接受连接。
- SYN_SENT 这个状态与SYN_RCVD遥相呼应，当客户端SOCKET执行CONNECT连接时，它首先发送SYN报文，随即进入到了SYN_SENT状态，并等待服务端的发送三次握手中的第2个报文。SYN_SENT状态表示客户端已发送SYN报文。
- SYN_RCVD 该状态表示接收到SYN报文，在正常情况下，这个状态是服务器端的SOCKET在建立TCP连接时的三次握手会话过程中的中间状态，很短暂。此种状态时，当收到客户端的ACK报文后，会进入到ESABLISHED状态。
- ESTABLISHED 表示连接已经建立。
- FIN_WAIT_1 FIN_WAIT_1和 FIN_WAIT_2状态的真正含义都是表示等待对方的FIN报文。区别是：FIN_WAIT_1状态时当socket在ESTABLISHED状态时，想主动关闭连接，向对方发送了FIN报文，此时该socket进入到FIN_WAIT_1状态。
FIN_WAIT_2 状态是当对方回应ACK后，该socket进入到FIN_WAIT_2状态，正常情况下，对方应马上回应ACK报文，所以FIN_WAIT_1状态一般较难见到，而FIN_WAIT_2状态可用netstat看到。
- FIN_WAIT_2 主动关闭链接的一方，发出FIN收到ACK以后进入该状态。称为半连接或半关闭状态。该状态下的socket只能接收数据，不能发。
- TIME_WAIT 表示收到了对方的FIN报文，并发送出了ACK报文，等2MSL后即可回到CLOSED可用状态。如果FIN_WAIT_1状态下，收到对方同时带FIN标志和ACK标志的报文时，可以直接进入到TIME_WAIT状态，而无须经过FIN_WAIT_2状态。
- CLOSE_WAIT 此种状态表示在等待关闭，当对方关闭一个SOCKET后发送FIN报文给自己，系统会回应一个ACK报文给对方，此时则进入到CLOSE_WAIT状态。接下来查看是否还有数据发送给对方，如果没有可以close这个SOCKET，发送FIN报文给对方，即关闭连接。所以在CLOSE_WAIT状态下，需要关闭连接。

## 解决2MSL延时问题
为了解决服务器socket可能的2MSL延迟问题，我们可以为服务器socket设置SO_REUSEADDR选项。
```
import socket
# 创建socket
# 注意TCP协议对应的为SOCK_STREAM
server_sock = socket.socket(socket.AF_INET, sock.SOCK_STREAM)

# 使用setsockopt()方法设置socket的选项参数
# SOL_SOCKET = Set option level _ SOCKET 设置选项级别为socket级
# SO_REUSEADDR = socket option _ REUSEADDR 设置socket的选项参数为重用地址功能
# 1 表示开启此选项功能，即开启重用地址功能
server_sock.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)

# 绑定IP地址和端口
address = ("", 8080)
server_sock.bind(address)

# 让服务器端的socket开启监听，等待客户端的连接请求
server_sock.listen(128)

# 使用accept方法接收客户端的连接请求
client_sock, client_addr = server_sock.accept()
print("客户端%s:%s 进行连接！" % client_addr)

# recv()方法可以接收客户端发送过来的数据，指明最大收取1024个字节的数据
recv_data = client_sock.recv(1024)
print("接收到的数据为： "，recv_data.decode())

# send()方法向客户端发送数据，要求发送bytes类型的数据
client_sock.send("thank you!\n".encode())

# 关闭与客户端连接的socket
client_sock.close()

# 关闭服务器的监听socket
server_sock.close()


```

## 模拟QQ聊天
```

# 服务器端
import socket

# 创建socket
server_sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# 设置socket可以重用地址
server_sock.setsockopt(socket.SOL_SOCKET,socket.SO_REUSEADDR)

# 绑定本地信息
address = ("", 8080)
server_sock.bind(address)

# 开启监听
server_sock.listen(128)

while True:
    # 接收客户端的连接请求
    client_sock, client_addr = server_sock.accept()
    print("与客户端%s:%s建立了连接" % client_addr)

    while True:
        # 接收对方发过来的数据，最大接收字节为1024
        recv_data = client_sock.recv(1024)

        # 如果接收数据的长度为0，则意味着客户端关闭了链接
        if len(recv_data) > 0:
            print("客户端说：%s" % recv_data.decode())

            #发送一些数据到客户端
            msg = input("请输入回复内容： ")
            client_sock.send(msg.encode)
        else:
            break

        print("客户端%s:%s已下线" % client_addr)

        # 关闭客户端socket
        client_sock.close()

# 关闭服务器socket
server_sock.close()


```

```
# 客户端
import socket

# 创建socket
client_sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# 链接服务器
server_addr = ("127.0.0.1", 8080)
client_sock.connect(server_addr)

while True:

    # 提示用户输入数据
    msg = input("请输入要发送的消息：")

    # 若用户输入了内容，则发送，否则退出
    if len(msg) > 0:
        client_sock.send(msg.encode())

        # 接收对方发送过来的数据，最大接收1024个字节
        recv_date = client_sock.recv(1024)
        print("收到的消息：%s" % recv_data.decode())
    else:
        break

# 关闭套接字
client_sock.close()

```

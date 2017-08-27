##

```
import socket
listen_sock = socket.socket(socket.AF_INET, sock.SOCK_STREAM)
listen_sock.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
```
address = ("", port)
listen_sock.bind(address)
listen_sock.setblocking(False)
listen_sock.listen(128)

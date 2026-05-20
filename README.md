# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM

```
import socket

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)

host = '127.0.0.1'
port = 6000

server_socket.bind((host, port))
server_socket.listen(1)

print("Server is waiting for connection...")

conn, addr = server_socket.accept()
print("Connected with:", addr)

while True:
    data = conn.recv(1024).decode()

    if not data:
        break

    print("Client:", data)

    reply = input("Server: ")
    conn.send(reply.encode())
```
```
import socket

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = '127.0.0.1'
port = 6000

try:
    client_socket.connect((host, port))

    while True:
        msg = input("Client: ")
        client_socket.send(msg.encode())

        data = client_socket.recv(1024).decode()

        if not data:
            break

        print("Server:", data)

except ConnectionRefusedError:
    print("Server is not running!")

client_socket.close()

conn.close()
server_socket.close()
```

## OUPUT
<img width="1918" height="1102" alt="Screenshot 2026-05-20 102004" src="https://github.com/user-attachments/assets/05e7d683-6bfa-47c3-b9a8-84566f107437" />

<img width="1918" height="1107" alt="Screenshot 2026-05-20 102018" src="https://github.com/user-attachments/assets/a127aba9-53fd-4b9f-9ad6-f58a0a43afaf" />


## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.

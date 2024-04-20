# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
#### CLIENT:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```

#### SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip = input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address", s.recv(1024).decode())
```
## OUPUT - ARP
#### CLIENT:

![Screenshot 2024-04-20 175650](https://github.com/KrishnaPrasad148/2c.ARP_RARP_PROTOCOLS/assets/147332763/6753f0b8-c542-4316-a0a6-be664dba4625)

#### SERVER:

![Screenshot 2024-04-20 175646](https://github.com/KrishnaPrasad148/2c.ARP_RARP_PROTOCOLS/assets/147332763/f5ac56d5-c487-4e35-9c73-f1536e2ad1cf)

## PROGRAM - RARP
#### CLIENT:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```

#### SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```

## OUPUT -RARP
#### CLIENT:

![Screenshot 2024-04-20 180225](https://github.com/KrishnaPrasad148/2c.ARP_RARP_PROTOCOLS/assets/147332763/3624d173-bb97-47b3-b7a6-15057e11498b)

#### SERVER:

![Screenshot 2024-04-20 180220](https://github.com/KrishnaPrasad148/2c.ARP_RARP_PROTOCOLS/assets/147332763/99848ede-387b-41ca-903f-d1207331e591)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.

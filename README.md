## 2c.SIMULATING ARP /RARP PROTOCOLS

## NAME:T MOUNISH

## REGISTER NUMBER: 212223240098

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
## PROGRAM-ARP
## Client:
```py
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
## Server:
```py
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```

## OUPUT:
## Client:
![image](https://github.com/user-attachments/assets/cc372e1f-a22a-452a-9d5f-3a893f6a672f)

## Server:
![image](https://github.com/user-attachments/assets/c181aea4-1fcd-4227-bdf1-db9abd252c9a)

## PROGRAM-RARP
## Client:
```PY
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
## server:
```py
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```
## OUTPUT:
## client:
![image](https://github.com/user-attachments/assets/3ec03b4e-a7b5-4581-b67c-ec6b56f20561)

## server:
![image](https://github.com/user-attachments/assets/055b2336-4f83-434e-8d93-e79633c72c1d)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.

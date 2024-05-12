# 2c.SIMULATING ARP /RARP PROTOCOLS:
## NAME:N.KANNAN
## REG NO:212223230097
## AIM:
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
## PROGRAM - ARP:
## Client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,address=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
## Server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip = input("Enter logical address: ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP:
## CLIENT:
![Screenshot 2024-05-12 200800](https://github.com/kannan-nagaraju/2c.ARP_RARP_PROTOCOLS/assets/145742755/9ca6235b-b081-412d-a0bc-34c6d72fb802)

## SERVER:
![Screenshot 2024-05-12 200840](https://github.com/kannan-nagaraju/2c.ARP_RARP_PROTOCOLS/assets/145742755/2269aa41-6e9d-4a80-81e7-aed7207b2f79)

## PROGRAM - RARP:
```
import socket
s = socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr = s.accept()
address = {"6A:08:AA:C2":"165.165.80.1","8A:BC:E3:FA":"165.165.79.1"}
while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
## Server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip = input("Enter MAC Address: ")
    s.send(ip.encode())
    print("Logical Address:",s.recv(1024).decode())
```

## OUPUT -RARP:
## CLIENT:
![Screenshot 2024-05-12 200933](https://github.com/kannan-nagaraju/2c.ARP_RARP_PROTOCOLS/assets/145742755/fbde118e-7a59-41e4-987d-e4bff3f8128a)

## SERVER:
![Screenshot 2024-05-12 201014](https://github.com/kannan-nagaraju/2c.ARP_RARP_PROTOCOLS/assets/145742755/8fdac021-5db1-4cf2-a3d0-f649c0ac410d)

## RESULT:
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.

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
#### Server side 
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","192.168.43.143":"74:D4:DD:CF:7E:8F"};
while True:
    ip=c.recv(1024).decode()
    try:
       c.send(address[ip].encode())
    except KeyError:
       c.send("Not Found".encode())
```
#### Client Side
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address:",s.recv(1024).decode())
```
## OUPUT - ARP

#### Sever side
<img width="676" height="538" alt="image" src="https://github.com/user-attachments/assets/3d0a8e13-458d-4dab-8668-e6d6d8bc427e" />

#### Client side
<img width="615" height="631" alt="image" src="https://github.com/user-attachments/assets/9005c51d-973a-4b4b-8aa3-d8b35be97d3e" />


## PROGRAM - RARP

#### Server side
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"165.165.80.80","74:D4:DD:CF:7E:8F":"192.168.43.143"};
while True:
    mac=c.recv(1024).decode()
    try:
       c.send(address[mac].encode())
    except KeyError:
       c.send("Not Found".encode())
```
### Client side
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    mac=input("Enter MAC Address : ")
    s.send(mac.encode())
    print("IP Address:",s.recv(1024).decode())
```

## OUPUT -RARP
#### Server side
<img width="685" height="541" alt="image" src="https://github.com/user-attachments/assets/46fe73c5-11bd-4ca1-8641-9747a269e091" />


#### Client side
<img width="642" height="588" alt="image" src="https://github.com/user-attachments/assets/6599cdbe-0c1b-417b-b825-e13985757920" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.

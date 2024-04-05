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

## Program - ARP :
  ## Client :
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
  ## Server :
   ```
   import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip = input("Enter Logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
   ```
## Output - ARP :
  ## Client :
  ![Screenshot 2024-04-05 111202](https://github.com/Vinishofficial/2c.ARP_RARP_PROTOCOLS/assets/146931793/43f47be9-f027-4517-bb82-946ffc5eb104)

  ## Server :
  ![Screenshot 2024-04-05 111142](https://github.com/Vinishofficial/2c.ARP_RARP_PROTOCOLS/assets/146931793/f732aef6-0b98-48e8-b8dc-94898fc98ddb)

  
## Program - RARP :
  ## Client :
  ```
  import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"165.165.79.1"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
        
  ```
  ## Server :
   ```
   import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip = input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
   ```
## Output - RARP :
  ## Client :
 ![Screenshot 2024-04-05 111238](https://github.com/Vinishofficial/2c.ARP_RARP_PROTOCOLS/assets/146931793/51d94345-4aaf-4737-86d7-065869ae99dd)

  ## Server :
 ![Screenshot 2024-04-05 111226](https://github.com/Vinishofficial/2c.ARP_RARP_PROTOCOLS/assets/146931793/67b74a9c-89b5-4b0a-910e-f0d321fff829)

  
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.

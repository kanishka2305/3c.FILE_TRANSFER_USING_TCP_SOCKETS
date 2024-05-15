# EXP :3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM:
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM:
### Client:
```py
import socket
s = socket.socket()
host = socket.gethostname()
port = 6000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file','wb') as f:
    while True:
        print("Receiving data...")
        data = s.recv(1024)
        print("Data = %s", (data))
        if not data:
            break
    f.write(data)
f.close()
print("Successfully got the file")
s.close()
print("Connection closed")
```
### Server:
```py
import socket 
port = 60000 
s = socket.socket() 
host = socket.gethostname() 
s.bind((host, port))
s.listen(5) 
while True:
    conn, addr = s.accept()
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename='mytext.txt'
    f = open(filename,'rb')
    l = f.read(1024)
    while (l):
         conn.send(l)
         print('Sent ',repr(l))
         l = f.read(1024)
     f.close()
     print('Done sending')
     conn.send('Thank you for connecting'.encode())
     conn.close()
```
## OUPUT:
### Client:
![329767479-51e7c825-9a43-4728-9187-faa506550afb](https://github.com/kanishka2305/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/113497357/dc2a90e2-a7c8-472a-90e5-4df9185f15f7)

### Server:
![329767494-49dfbdc0-f6f4-4f8d-a80c-723ffe169eec](https://github.com/kanishka2305/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/113497357/3d164dc3-37b7-49a8-8bf9-f11ca5a04216)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.

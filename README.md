# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
client:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
  while(i<len(l)):
      st+=s
      c.send(str(l[i:st]).encode())
      ack=c.recv(1024).decode()
      if ack:
        print(ack)
        i+=s
```
server:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True: 
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())
```
## OUPUT
![Screenshot 2024-05-10 133122](https://github.com/Ettasupraja/2b_SLIDING_WINDOW_PROTOCOL/assets/151641352/88e5be73-cde1-4ab6-b922-bf525cdfaf6f)
![Screenshot 2024-05-10 133143](https://github.com/Ettasupraja/2b_SLIDING_WINDOW_PROTOCOL/assets/151641352/44e3735c-1db7-49e5-9f3f-9d385de7920f)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed

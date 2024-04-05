# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM:
 To write a python program for implementation of sliding window protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM:
## client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames:"))
l=list(range(size))
s=int(input("Enter window size:"))
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
## server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknoledgement recieved from the server".encode())
```
## OUTPUT:
## client:
![image](https://github.com/Rajaraman77/2b_SLIDING_WINDOW_PROTOCOL/assets/150319383/b026f94e-a07c-45b4-8756-ee277d344329)
## server:
![image](https://github.com/Rajaraman77/2b_SLIDING_WINDOW_PROTOCOL/assets/150319383/b994176e-3dea-4f5d-ad14-bcb5584963cf)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed

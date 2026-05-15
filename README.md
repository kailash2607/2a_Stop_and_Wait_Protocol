# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
### Server
~~~
import socket

# Create socket
s = socket.socket()

# Bind IP and port
s.bind(('localhost', 8000))

# Listen for client connections
s.listen(5)

print("Server waiting for connection...")

# Accept client connection
c, addr = s.accept()

print("Connected to:", addr)

while True:
    # Take input from server user
    data = input("Enter a data: ")

    # Send data to client
    c.send(data.encode())

    # Receive acknowledgement
    ack = c.recv(1024).decode()

    if ack:
        print(ack)
    else:
        c.close()
        break

~~~
### Client
~~~
import socket

# Create socket
c = socket.socket()

# Connect to server
c.connect(('localhost', 8000))

while True:
    # Receive message from server
    msg = c.recv(1024).decode()

    print("Server:", msg)

    # Send acknowledgement
    ack = input("Enter acknowledgement: ")

    c.send(ack.encode())
~~~
## OUTPUT
<img width="922" height="181" alt="image" src="https://github.com/user-attachments/assets/a2420dbc-ec89-4411-bc65-a8083a9a3c23" />

<img width="342" height="83" alt="image" src="https://github.com/user-attachments/assets/6ae698c6-8393-44d7-b63c-447c12bcbd92" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.

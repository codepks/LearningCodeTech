# Inter Process Communication

1.  Pipes : 
		a. Pipes are ligher than sockets and shared memories
		b. One can use pipes when you need light weight method of communcation
		c. Generally used when you need to send data from parent process to child process and when it is unidirectional

2. Shared Memory: A segment of memory that is shared between processes. This allows for fast communication since processes can read and write to the shared memory directly.

3. Semaphores: Used to control access to shared resources by multiple processes. They help in synchronizing processes to avoid race conditions.

4. Sockets: Allow communication between processes over a network. They can be used for communication between processes on the same machine or on different machines.

5. Signals: A limited form of communication used to notify a process that a specific event has occurred. Signals can be sent to processes to interrupt them or to notify them of events.

6.  Remote Procedure Calls (RPC): A protocol that allows a program to execute a procedure in another address space (commonly on another computer in a shared network).

7.  Memory-Mapped Files: A method that maps a file or a portion of a file into the memory space of a process, allowing multiple processes to access the same file concurrently. 
		a. Used in case of Databases





## Socket Connection vs TCP

TCP / IP vs Socket Connection
	1. TCP/IP is a protocol to communicate over different networks which makes sure that the reliable data is transmitted.
	2. Socket connection is an endpoint of TCP/IP communication 
	3. Types of socket connection : TCP IP and UDP. E.g. the Winsock API provides an API for connections over the TCP/IP stack on Windows.
 
```
import socket  

def udp_client():  
    # Create a UDP socket  
    client_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)  
    
    # Define the server address and port  
    server_address = ('localhost', 12345)  
    
    try:  
        # Send a message to the server  
        message = "Hello, UDP Server!"  
        print("Sending message: '{}'".format(message))  
        client_socket.sendto(message.encode(), server_address)  
        
        # Wait for a response from the server  
        data, server = client_socket.recvfrom(4096)  
        print("Received response: '{}'".format(data.decode()))  
        
    finally:  
        client_socket.close()  

if __name__ == "__main__":  
    udp_client()
```

### UDP Server:

1. Creates a UDP socket and binds it to localhost on port 12345.
2. Listens for incoming messages in an infinite loop.
3. When a message is received, it prints the message and the client's address.
4. Optionally sends a response back to the client.

### UDP Client:

1. Creates a UDP socket and defines the server's address.
2. Sends a message to the server.
3. Waits for a response and prints it.

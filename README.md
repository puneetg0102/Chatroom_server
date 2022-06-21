
# Chatroom_server

This application is implemented using CPP language and concepts related to 
sockets and multi-threading, which works on Linux based OS.



## Deployment

Since the chatroom_server is written in cpp; therefore installation of
g++ is a prerequisite. 

To deploy the application, first open the WSL terminal and compile the server.cpp and 
client.cpp files by commands:

```bash
  g++ -pthread -o server server.cpp
  g++ -pthread -o client client.cpp
```
After compiling the files, run the server by the command:
```bash
./server
```

After that, clients can join the server with the help of following command:
```bash
./client
```


## Internal Working

Our Application Chatroom_server conists of the server side and the client side which are connected to each other
through sockets. The port to which both the server and client sockets are connected has been set to 8000.  


### Client

The client side  controls the sending and recieving of the messages. 
It consists of two functions send_message and recv_message. 

When the server is running, on running the client with the given commands on terminal and entering a valid name, 
the socket is created. After connecting to the socket, the name is sent to the
server and the client is ready to interact with all other clients those who joins the server.
the server recieve a message that the client has joined the chat room as soon as the client enters a valid name. Whenever a message 
is sent by any other client, the name of the sending client along with the message
is diplayed on the client's terminal. If the client writes a message and unless
the message is not "exit" the message is broadcasted to all the users. On writing
exit, the client is removed from the server and all the other clients and the server
recieve a message forthe same.


### Server

The server side is designed to control how a client interacts 
with the other clients. For that, we have created functions
to add as well as remove clients from the queue. Since multi-threading is
used in the server, hence it is essential to use mutex locks while adding
and removing clients from the list. A broadcast_message function has been used, which sends the message of a 
client to all other clients and the server. 

On runnning the server, A socket is created and after 
the bind socket and listen functions are executed the server is opened for client
processes to join. When any client attempts to join the server a new thread is
created.After the creation of thread the client is added to the queue of active users.
Further, when a valid name is entered, the client becomes eligible to interact in the 
chat room. Then, all the messages of the client are sent with the broadcast_message
function to other clients and the server until the client sends the message exit.
On doing so, the client is removed from the server.


## Video Demo

https://user-images.githubusercontent.com/98050969/174826909-ce090684-f7d1-47b6-91b6-0c994555a5e5.mp4

## Learnings

In the course of this project, I have learned the working of sockets
and  the way in which multiple clients can interact with each other with the help of a server.
I have also understood how threads work as well as the concept of
multi-threading and mutex locks which have been implemented
through POSIX threads in the chat server. 
## Additional Tasks

- I have learned the implementation of real time chatroom application by using the concepts of socket programming and multi-threading.
 
- For sending and recieving messages I have used threads.

- A keyword ("exit") is used to remove a client from the server.

- The joining and leaving of clients is color coded.

- Mutex/locks have been used while adding and removing any client from the
  list of active users.

## References

- https://www.geeksforgeeks.org/socket-programming-cc/
- https://www.geeksforgeeks.org/multithreading-c-2/



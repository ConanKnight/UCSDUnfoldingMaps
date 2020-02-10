# Project README file

## Echo
### Client Side[1]
- In the Echo, we are asked to implement a simple echo function beweeen the `server` and the `client`. 
The server needs to receive the message from the client and then echo back to client.
- For the `echoclient`, a client-side `socket` needs to be created and then binds the socket with the server's address by `connect` method.
In this way, the client can talk to server by the client-side socket. After sending the message to the server, the `socket` will read the message echo back from the server.
The message will be put into a buffer. After the client side buffer get the message, the mission of client-side socket is done.
- The last step is to close the socket.
### Server Side
- The server also need to create a socket to process the requests from the clients. the socket should accept the requests from any 
ip address with the specific port. 
- After creating the socket and start to listen the socket, the server should always keep running and
processing requests from the clients. If there is a request from client, a new file descriptor will be created call `client_fd`, the message from client
side can be read to the buffer and rewrite back to the client. 
- After each round, the `client_fd` will be closed and a new one will be created once there is a new request from client.
### Test Echo
- open the `echoserver` file first in one terminal and then open the `echoclient` file in another terminal. Give an specific port # if neccessary. If not, the client will use the defaut port and message "Hello World!!".
- The server will print the message from client to indicate it successfully receive the message.
- The client will print the message from the server to indicate it also get the message echo back from the server.



## File Transfer[2]
### Transferclient
- The socket creatation process is similar to the echo, the only difference is that the client socket `socket_fd` will continue to 
receive the data from the server until the `received_bytes` is less or equal to 0.
- When the received data is all completed, close the client socket.

### Transferserver
- the creation socket process is also similar to the echo, the only difference is that the server needs to send all data in the 
txt file. when the `read_bytes` is smaller than the `BUFSIZE`, it means all data has been transferred.
- After the filetransfer request fromt the client, the server needs to close the current socket and wait for a new request from client.

### Test File Transfer
- open the `transferserver` first in one terminal and then open the `transferclient` in another terminal. Write some text in the defaut `6200.txt` file.
You can specify the port #. 
- When the tranfer starts, the client will create a defaut `cs6200.txt` file and then read the data from `6200.txt`. The same text data from `6200.txt` would be shown 
in `cs6200.txt`. 
- Further more, if the text changes in `6200.txt`, the same changes would happen in `cs6200.txt`, which proves the correctness of the codes.

## Part 1

- I have written the codes for gfserver.c but failed to pass the Bonnie Test. I have also sumitted some codes to from the github[3][4] and other open resources in my early submissions. 
- I have little knowledge about c and spend a lot of time setting up the envrioment, understanding the C, pointer, as
well as socket programming. This project is too hard for me and I will start early in future projets.
- I hope in the future there will be more tutorials/detailed written guides about this project. If this huge project can be divided into several miniprojects, that would be helpful.

### Test
I use the `make gfserver_main` to test the `gfserver.c` and the compile pass. Then I test the `gfclient_download_bad_method`,`gfclient_download_bad_path`, and
`gfclient_download_bad_scheme`, the client shown `INVALID` correctly, but the Bonnie test failed.


## Reference
- [1] https://github.com/zx1986/xSinppet/tree/master/unix-socket-practice
- [2] https://github.com/pumaatlarge/OMSCS
- [3] https://github.com/amilkov3/foo
- [4] https://github.com/pumaatlarge/OMSCS



# CN-assignment

Video File Transmission Over TCP Sockets

Demo Video link online 

https://github.com/user-attachments/assets/14bcb70c-29af-480f-ba6b-e88e5d2792a8


Overview
This task demonstrates a simple implementation of a sender/receiver program using TCP sockets to transmit video file content over a network. The task is to send the contents of a video file from the sender to the receiver using GNU C(gcc) in a Linux environment. The transmission occurs over a TCP connection, with the file data being sent in segments and reconstructed at the receiving end.
TASK Components
       It consists of two main programs:
1.	Sender (client): Responsible for reading a video file, segmenting its contents, and sending these segments over a TCP connection to a receiver.
2.	Receiver (server): Listens for incoming connections, accepts video file data from the sender, and writes the received segments to a new file.
Features
Sender Program
•	Video File Reading: Opens a specified video file, reads it in chunks, and sends the data over a TCP connection.
•	Segmented Transmission: Video content is sent in segments of 1024 bytes (or smaller for the last segment).
•	End-of-File (EOF) Detection: Sends an EOF signal ("EOF") to notify the receiver that the file transfer is complete.
•	Socket Closure: Closes the socket connection after the file is completely sent.
Receiver Program
•	Listening for Connections: Sets up a TCP socket and listens for incoming client connections.
•	File Writing: Receives the video data segments from the sender and writes them into a new video file.
•	Socket Closure: Closes both the file and socket after the transmission is complete.
How to Run
Compile the Programs
You need to compile both the sender and receiver programs using the GNU C compiler (gcc):
gcc sender.c -o sender
gcc receiver.c -o receiver
Step 2: Start the Receiver (Server)
Run the receiver program on the machine that will receive the video file. This machine listens for incoming connections and writes the received data into a new file:
./receiver
Make sure the receiver is running before starting the sender program.
Start the Sender (Client)
Run the sender program on the machine that will send the video file. This machine connects to the receiver and transmits the video in segments.
./sender
File Transfer
The video file will be transmitted from the sender to the receiver. The receiver will save the video as received_video.mp4. The connection will close automatically after the EOF signal is received.
Code Overview
Receiver Code (receiver.c)
•	Socket Setup: The receiver creates a TCP socket, binds it to a port (8877), and listens for incoming connections.
•	File Handling: Opens a file (received_video.mp4) to write the incoming video data.
•	EOF Detection: Looks for the "EOF" string to know when to stop receiving data.
Sender Code (sender.c)
•	Socket Setup: The sender creates a TCP socket and connects to the receiver.
•	File Handling: Opens a video file (video.mp4) and reads it in chunks of 1024 bytes.
•	EOF Notification: Sends the "EOF" string after all video data has been transmitted.


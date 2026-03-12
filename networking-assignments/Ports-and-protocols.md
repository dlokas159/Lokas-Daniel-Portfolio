# 1. Design and Planning
## Transport Layer Reliability
### Part 1 — Build the Network

#### Investigation 1 — Connection Establishment (Three-Step Setup)
##### Step A — Reset and Prepare & Step B — Generate TCP Traffic
<img width="699" height="177" alt="Screenshot 2026-03-04 at 2 45 02 PM" src="https://github.com/user-attachments/assets/e926bc1d-c40a-44fe-bf2e-b560a1f2d48a" />

##### Step C — Step Through the First Three Packets Only

[video](https://github.com/user-attachments/assets/e7390416-2681-4d37-af14-bb8b02abea90)

A TCP connection is created through a process called the three-way handshake. First, the client sends a packet with the SYN flag to request a connection. Second, the server responds with a packet containing SYN and ACK, which acknowledges the request and signals readiness to connect. Third, the client sends an ACK packet back to the server confirming the connection. After these three packets are exchanged, the TCP connection is established and data transmission can begin.

#### Investigation 2 — Acknowledgment and Ordering
<img width="463" height="558" alt="Screenshot 2026-03-04 at 2 47 28 PM" src="https://github.com/user-attachments/assets/44414379-519a-40e5-ae2e-9c04ec4d98ea" />
<img width="464" height="527" alt="Screenshot 2026-03-04 at 2 47 58 PM" src="https://github.com/user-attachments/assets/0c385b3e-86b1-4482-9ee8-987ccb71ea5f" />

TCP uses sequence numbers and acknowledgment numbers to keep data in the correct order and confirm successful delivery. Sequence numbers increase as more data is sent so the receiver knows the order of the packets. Acknowledgment numbers confirm which data has been received successfully. Sometimes a sender may transmit additional data before receiving acknowledgment depending on the window size. If the connection were interrupted, the sender would notice missing acknowledgments and retransmit the missing packets.

#### Investigation 3 — Header Fields and Error Detection
<img width="461" height="407" alt="Screenshot 2026-03-04 at 2 48 17 PM" src="https://github.com/user-attachments/assets/ab765c26-954d-446f-bd37-a91ea4234b17" />

The checksum field in the TCP header is used to detect errors in transmitted data. It verifies that the packet contents have not been corrupted while traveling across the network. If the receiving computer calculates a different checksum than the one in the packet, the segment is considered invalid and is discarded. Because the receiver does not acknowledge the corrupted packet, the sender eventually retransmits the data.

### Part 2 — Observing TCP Behavior
#### Step 1: Switch to Simulation Mode & Step 2: Generate TCP Traffic & Step 3: Filter for TCP
<img width="342" height="297" alt="Screenshot 2026-03-03 at 1 32 51 PM" src="https://github.com/user-attachments/assets/4ffc418a-4688-4aff-bc95-95cf096c4210" />

#### Step 4: Run the Simulation Slowly

[video](https://github.com/user-attachments/assets/af97f347-9ba6-44fd-9785-c447196ac180)

### Part 3 — Observe UDP Behavior
#### Step 1: Clear Simulation Step 2: Generate UDP Traffic
<img width="301" height="195" alt="Screenshot 2026-03-03 at 1 38 08 PM" src="https://github.com/user-attachments/assets/2a35be62-94f4-4fa1-bacd-47de3784ffd5" />

| Feature          | TCP                                                | UDP                                  |
| ---------------- | -------------------------------------------------- | ------------------------------------ |
| Connection setup | Requires a three-way handshake before data is sent | No connection setup is required      |
| Acknowledgment   | Uses acknowledgments to confirm delivery           | Does not use acknowledgments         |
| Ordering         | Delivers data in order using sequence numbers      | Does not guarantee order             |
| Retransmission   | Retransmits lost packets                           | Does not retransmit lost packets     |
| Overhead         | Higher overhead because of reliability features    | Lower overhead because it is simpler |


### Part 4
Step 1 — Start TCP Traffic
Step 2 — Interrupt the Link
Step 3 — Step Forward
Step 4 — Restore Connectivity
<img width="343" height="335" alt="Screenshot 2026-03-04 at 2 53 04 PM" src="https://github.com/user-attachments/assets/2b4257a9-711a-45ef-8b77-c342730c8747" />

TCP detects packet loss when acknowledgments stop arriving or when duplicate acknowledgments appear. This indicates that a packet may have been lost in transmission. The sender then retransmits the missing segment using the same sequence number. Because TCP can detect and resend lost packets, the communication usually continues successfully even if some packets are dropped.

### Part 5 — Port Number Rigor
Port numbers help identify which application on a device should receive the data. While an IP address identifies the computer itself, the port number identifies the specific program or service. For example, web servers commonly use port 80 for HTTP and port 443 for HTTPS. Ports allow multiple applications to use the network at the same time on the same device. Both TCP and UDP use port numbers for this purpose.

# 2. Technical Development
## Investigation 1 — Connection Establishment
Before any data is transmitted in TCP, a three-step handshake occurs between the client and server. The client sends a SYN packet requesting a connection. The server replies with a SYN-ACK packet to acknowledge the request and indicate it is ready. The client then sends a final ACK packet confirming the connection. Once this process is complete, both systems can begin exchanging data reliably.

## Investigation 2 — Acknowledgment and Ordering
If a TCP segment is sent but never acknowledged, the sender assumes that the packet was lost during transmission. The sender may detect this through a timeout or through repeated duplicate acknowledgments. When this happens, the sender retransmits the segment with the same sequence number. This process ensures reliable delivery of data across the network.

## Investigation 3 — TCP Header Fields
The checksum protects the integrity of the data being transmitted. If a packet becomes corrupted due to network interference or transmission errors, the checksum calculation will not match. The receiving computer will discard the corrupted packet instead of processing it. Because the packet is not acknowledged, the sender will eventually retransmit it.

## Part 1 — Full Stack Analysis: HTTP vs HTTPS
### Step 1 
curl -I http://example.com
ss -tn
<img width="1348" height="242" alt="unnamed (18)" src="https://github.com/user-attachments/assets/229d395f-3f88-4520-8d4a-0c6e7da9671e" />

### Step 2
curl -I https://example.com
ss -tn
<img width="1328" height="256" alt="unnamed (19)" src="https://github.com/user-attachments/assets/6d42fc47-982b-4523-8aaa-dfb6b25248b3" />

HTTP and HTTPS both operate at the application layer, but HTTPS includes encryption through TLS (Transport Layer Security). HTTP typically uses port 80, while HTTPS uses port 443. Both protocols still rely on TCP for reliable data delivery. The main difference is that HTTPS encrypts the data between the client and server, making communication more secure.

## Part 2 — DNS as a Supporting Application Protocol
nslookup example.com
<img width="380" height="252" alt="Screenshot 2026-03-11 at 12 48 30 PM" src="https://github.com/user-attachments/assets/0f1cc5c6-dcc9-4254-8ce1-0d26b67c233d" />

DNS normally uses port 53 and operates over UDP. UDP is preferred because DNS requests are small and need fast responses without the overhead of establishing a full connection. If a DNS response is too large for UDP, it may switch to TCP. DNS plays an important role in networking because it converts domain names into IP addresses.

## Part 3 — Remote Access Using SSH
### Step 1 — Identify Your Local IP
ip addr
<img width="581" height="306" alt="Screenshot 2026-03-11 at 12 49 52 PM" src="https://github.com/user-attachments/assets/4dab008b-e1b4-4e76-8e81-fbae7ed0695e" />

### Step 2 — Connect to Yourself via SSH
ssh your_username@localhost
<img width="713" height="500" alt="Screenshot 2026-03-11 at 12 50 41 PM" src="https://github.com/user-attachments/assets/13bdcc87-8ae1-4b88-95a1-aa379193167f" />

### Step 3 — Inspect the Connection
ss -tn
<img width="1414" height="252" alt="unnamed (20)" src="https://github.com/user-attachments/assets/b4b397c4-e9fb-43a4-8b78-0713dd25f8cc" />

SSH allows users to securely access a remote computer over a network. It normally uses port 22 and runs on top of TCP. TCP ensures that commands and responses are delivered reliably and in the correct order. SSH encrypts all communication so that sensitive data such as login credentials cannot be intercepted.

## Part 4 — Secure File Transfer
echo "Layered Networking Test" > stacktest.txt
scp stacktest.txt your_username@localhost:/home/your_username/
<img width="709" height="241" alt="Screenshot 2026-03-11 at 12 54 31 PM" src="https://github.com/user-attachments/assets/64c58ff9-82cd-40a5-af01-eec7087ef029" />

SCP is a protocol used to transfer files securely between computers. It works by using the encrypted connection provided by SSH. Because SSH uses TCP, SCP also relies on TCP for reliable transmission. Encryption ensures that the file contents cannot be read or modified while being transferred.

## Part 5 — Stack Mapping Requirement
Choose ONE of the following:
• HTTPS request
• SSH session
• SCP transfer

Construct a layered analysis:

| Layer        | Protocol                    | Purpose                                    |
| ------------ | --------------------------- | ------------------------------------------ |
| Application  | HTTP                        | Requests and receives web content          |
| Presentation | TLS                         | Encrypts data and protects privacy         |
| Session      | TLS Session / HTTPS session | Maintains the secure communication session |
| Transport    | TCP                         | Provides reliable, ordered delivery        |
| Network      | IP                          | Routes packets between devices             |


When a user visits a secure website, several networking layers work together. At the application layer, HTTP handles the request for the webpage. TLS at the presentation layer encrypts the data. TCP at the transport layer ensures reliable delivery of packets. Finally, IP at the network layer routes the packets across the internet to their destination.


## HTTP Response Status Codes Investigation

**Source Used:**  
MDN Web Docs — HTTP Response Status Codes  
https://developer.mozilla.org/en-US/docs/Web/HTTP/Status

---

### Task 1 — Understanding Status Code Categories

| Status Code Range | Meaning | Example Code | Explanation |
|---|---|---|---|
| **1xx** | Informational responses | **100 Continue** | This means the server has received the beginning of the request and the client should continue sending the rest of the request. |
| **2xx** | Successful responses | **200 OK** | This means the request was successful and the server returned the requested resource, such as a webpage. |
| **3xx** | Redirection messages | **301 Moved Permanently** | This means the requested resource has been permanently moved to a new URL and the client should use the new address in the future. |
| **4xx** | Client error responses | **404 Not Found** | This means the server could not find the requested page or resource. The request was valid, but the content does not exist at that location. |
| **5xx** | Server error responses | **500 Internal Server Error** | This means the server encountered a problem while trying to process the request and could not complete it. |

---

### Task 2 — Investigating Real Codes

| Status Code | Name | What It Means | When It Happens |
|---|---|---|---|
| **200** | OK | The request was successful and the server sent back the requested data. | Happens when a webpage loads normally without any issues. |
| **301** | Moved Permanently | The requested resource has been permanently moved to a new URL. | Happens when a website permanently changes the address of a page and wants browsers to update their bookmarks. |
| **302** | Found (Temporary Redirect) | The requested resource is temporarily located at a different URL. | Happens when a website temporarily redirects users to another page, such as during maintenance. |
| **404** | Not Found | The server cannot find the requested page or resource. | Happens when a user enters the wrong URL or the page has been deleted. |
| **500** | Internal Server Error | The server encountered an unexpected problem while processing the request. | Happens when there is a bug, misconfiguration, or crash on the web server. |

---

### Task 3 — Connecting Status Codes to Networking Concepts

HTTP status codes are handled at theApplication Layer because they describe the meaning of a web request and response. The Transport Layer, which uses TCP, is responsible for reliably delivering data between computers. TCP ensures that packets arrive correctly and in order, but it does not understand the meaning of the data being sent. HTTP, which operates at the Application Layer, defines how web browsers and servers communicate about web resources. Because status codes describe the outcome of an HTTP request, they must be handled at the Application Layer where the web communication rules are defined.

---

### Task 4 — Reasoning About Web Behavior

A server might return 301 Moved Permanently instead of just sending the new page so that browsers and search engines know the page has a new permanent address. This allows them to update bookmarks and indexes to the correct location. 404 errors are common on the internet because pages are often deleted, moved, or linked incorrectly, which causes the server to be unable to find the requested resource. A 500 Internal Server Error suggests that something went wrong on the server itself, such as a coding error, misconfiguration, or software failure that prevented the server from completing the request.


# 3. Testing & Evaluation
## Part 1 — Predict Before Testing
TCP is considered connection-oriented because it establishes a connection before sending data. UDP is connectionless, meaning it sends data without creating a session first. If UDP packets are lost, they are not automatically retransmitted. TCP uses more overhead because it tracks sequence numbers, acknowledgments, and connection states.

## Part 2 — Observing Listening Sockets (System Readiness)
### Step 1 — View Listening TCP Ports
ss -tln
<img width="1420" height="296" alt="unnamed (7)" src="https://github.com/user-attachments/assets/6bd34858-d210-4c72-9315-cff7addb3349" />

### Step 2 — Identify the Process Using a Port
sudo ss -tlpn
<img width="716" height="258" alt="Screenshot 2026-03-06 at 8 19 54 AM" src="https://github.com/user-attachments/assets/1c078f1e-36d5-4195-b304-404f62796cd8" />

If port 22 appears in a listening state, it means that an SSH server is running and waiting for incoming connections. If the port does not appear, the SSH service is likely not running. A port exists as a number in the networking system, but it is only considered listening when an application actively uses it.

### Step 3 — View Listening UDP Ports
ss -uln
<img width="1434" height="294" alt="unnamed (8)" src="https://github.com/user-attachments/assets/54bb27b6-2df7-4838-8d57-9c1b4305fe83" />

## Part 3 — Live TCP vs UDP Experiment
### Step 1 — Start TCP Listener (Terminal A)
nc -l 5000
<img width="586" height="86" alt="unnamed (9)" src="https://github.com/user-attachments/assets/c8927de2-c61c-4179-b232-2d70c547ccb6" />

### Step 2 — Confirm LISTEN State (Terminal C)
ss -tln
<img width="698" height="199" alt="Screenshot 2026-03-06 at 8 31 15 AM" src="https://github.com/user-attachments/assets/835a2021-1cb7-432f-b309-0ffc9d92823f" />

### Step 3 — Establish TCP Connection (Terminal B)
nc 127.0.0.1 5000
<img width="642" height="122" alt="unnamed (10)" src="https://github.com/user-attachments/assets/1e61bd53-c5f9-4eb1-8fb5-a37d74a4f63b" />

### Step 4 — Observe ESTAB State (Terminal C)
ss -tn
<img width="1414" height="246" alt="unnamed (11)" src="https://github.com/user-attachments/assets/2bdb92fd-00fd-4d25-bd07-d41fcd571672" />

A LISTEN state means that a program is waiting for incoming TCP connections. An ESTAB (established) state means that a connection between two systems has already been successfully created. The command ss -tln shows listening TCP sockets, while ss -tn shows active TCP connections. This demonstrates how TCP manages connection states during communication.

## UDP Experiment
### Step 1 — Start UDP Listener (Terminal A)
nc -u -l 6000
<img width="574" height="98" alt="unnamed (13)" src="https://github.com/user-attachments/assets/ee983831-af30-46c5-a669-6cbebf5fce35" />

### Step 2 — Send UDP Traffic (Terminal B)
nc -u 127.0.0.1 6000
<img width="780" height="126" alt="unnamed (12)" src="https://github.com/user-attachments/assets/c879cfff-b100-4932-9a6b-73b92d84d472" />

### Step 3 — Inspect UDP State (Terminal C)
ss -uln
<img width="691" height="418" alt="Screenshot 2026-03-06 at 8 36 22 AM" src="https://github.com/user-attachments/assets/d2719459-f8b6-4517-a813-2db4972d89e1" />

### UDP Analysis (Digital Portfolio with evidence in paragraph form)
UDP sockets typically appear with the state UNCONN, meaning they are not connected to a specific peer. This occurs because UDP does not create persistent connections like TCP. If a terminal closes suddenly, UDP communication simply stops without a formal closing process.

## Part 4 — Port and Ephemeral Port Analysis
Terminal A:
nc -l 5000
<img width="580" height="94" alt="unnamed (14)" src="https://github.com/user-attachments/assets/6847a8eb-ced8-492c-a0bd-d6bdcfae782f" />

Terminal B:
nc 127.0.0.1 5000
<img width="674" height="102" alt="unnamed (15)" src="https://github.com/user-attachments/assets/d42669a6-2e81-4120-93fa-454d8657ac24" />

Then immediately in Terminal C:
ss -tn
<img width="1414" height="274" alt="unnamed (16)" src="https://github.com/user-attachments/assets/177d495e-f6c3-45fc-b8d5-d6ca37f5e27a" />

A listening port is used by a server application waiting for incoming requests. An ephemeral port is a temporary port assigned by the operating system to a client during a connection. This allows many connections to occur at the same time without conflicts. UDP also uses ports to identify services, even though it does not create connections.

| Application       | Protocol     | Why?                                                                 |
| ----------------- | ------------ | -------------------------------------------------------------------- |
| Online Banking    | HTTPS        | It protects sensitive financial information through encryption       |
| Zoom Call         | UDP          | It reduces delay, which is important for live audio and video        |
| Netflix Streaming | HTTP/HTTPS   | It reliably delivers streaming content in chunks over the web        |
| File Download     | HTTPS        | It provides reliable transfer and can also encrypt the file transfer |
| DNS Query         | DNS over UDP | It is fast and efficient for small requests                          |


## Part 1 — Application Layer Investigation
### Step 1 — Inspect an HTTP Transaction
curl -I http://example.com
<img width="421" height="261" alt="Screenshot 2026-03-09 at 9 19 25 AM" src="https://github.com/user-attachments/assets/21593c7d-6ebf-4505-a253-ede0650e2ef6" />

The protocol being used is HTTP, which operates at the Application Layer. It runs on top of TCP, the transport protocol that provides reliable data delivery. We know this because HTTP normally uses TCP on port 80 for web communication. The Application Layer is responsible for interpreting the “200 OK” response because it is part of the HTTP protocol.

### Step 2 — Inspect an HTTPS Transaction
curl -I https://example.com
<img width="440" height="215" alt="Screenshot 2026-03-09 at 9 20 56 AM" src="https://github.com/user-attachments/assets/ef747178-7953-4a3e-86f1-da7d0ec0d524" />

When the request changed from http://example.com to https://example.com, the connection became secure instead of plain text. The additional protocol involved is TLS, which is used to encrypt the communication before the webpage data is exchanged. HTTP by itself does not provide encryption. The encryption logically occurs above TCP and below the application data, which is why HTTPS uses HTTP together with TLS rather than replacing HTTP itself.

## Part 2 — Presentation Layer Investigation
openssl s_client -connect example.com:443
<img width="968" height="694" alt="Screenshot 2026-03-09 at 9 22 30 AM" src="https://github.com/user-attachments/assets/c5a8a005-0ed4-4dd8-9b4c-366159fe76b7" />

Before application data is transferred in a secure HTTPS connection, the client and server exchange information during the TLS handshake. This includes security settings, certificate information, and the process for agreeing on encryption keys. This is not Layer 4 behavior, because TCP’s job is to move data reliably, not to negotiate encryption. The handshake solves the problem of how two systems can communicate securely and trust the connection before sending private data. It must happen first so that all later application data is protected.

## Conceptual Distinction
If TLS encrypts data, it is not replacing TCP. Instead, TLS operates above TCP. TCP is responsible for reliable transport, meaning it makes sure data arrives in order and is retransmitted if needed. TLS is responsible for formatting and encryption, meaning it protects the contents of the communication from being read or changed by others. These are different responsibilities, so TLS builds on top of TCP rather than replacing it.

## Part 3 — Session Layer Investigation
curl https://example.com & ss -tn
<img width="1916" height="398" alt="unnamed (17)" src="https://github.com/user-attachments/assets/1d12c4be-f866-4ea2-b676-d11382822ff6" />

When running curl https://example.com & ss -tn, the connection may still appear briefly as active depending on timing. In many cases it will move through an ESTAB state while data is being exchanged and then close when the transaction is finished. The session ends when the client and server are done communicating and close the connection. That decision is made by the systems and the application behavior, not just by TCP alone. If you log into a website with a username and password, TCP is not managing your login. That is handled at a higher layer by the web application and related session mechanisms.

| Protocol | Layer        | Purpose                                                      |
| -------- | ------------ | ------------------------------------------------------------ |
| HTTP     | Application  | Defines how web browsers and servers exchange web content    |
| HTTPS    | Application  | Provides secure web communication using HTTP with encryption |
| TLS      | Presentation | Encrypts and protects data in transit                        |
| DNS      | Application  | Translates domain names into IP addresses                    |
| TCP      | Transport    | Provides reliable, ordered delivery of data                  |


# 4. Reflection and Analysis
## Assignment 1 Reflection: 
TCP detects loss by using sequence numbers and acknowledgment numbers found in the TCP header. If a segment is sent and the acknowledgment does not arrive, TCP assumes the data was lost and retransmits it. This means deleting one TCP segment does not permanently break communication because TCP is designed to recover by sending the missing data again. In contrast, ICMP behaves differently because it does not provide the same reliable delivery features, so a lost ICMP packet is usually just lost. Reliability increases overhead because TCP must keep track of headers, acknowledgments, retransmissions, and connection state. This also shows the difference between layers: Layer 3 handles addressing and routing with IP, while Layer 4 handles reliability and ports with TCP.

## Assignment 2 Reflection:
TCP and UDP are structurally different because TCP is connection-oriented while UDP is connectionless. TCP reliability comes from the three-way handshake, sequence numbers, acknowledgments, and retransmissions. UDP avoids those features so it can send data with less delay and less overhead. Ports enable multiplexing by allowing many applications and sessions to share the same device and network connection at once. This was visible in the ss outputs, where TCP showed states like LISTEN and ESTAB, while the netcat UDP experiment showed UNCONN behavior instead of a true connection state. Protocol overhead matters because stronger reliability requires more tracking, more control information, and more processing.

## Assignment 3 Reflections: 
A. Encryption does not occur at Layer 3 because Layer 3 is responsible for routing packets across networks, not for protecting the contents of the data. TCP does not handle user authentication because authentication belongs to the application layer, where services decide who is allowed to log in. These responsibilities are separated so networks remain organized and efficient: transport reliability belongs to TCP, encryption belongs to TLS, and application logic belongs to protocols and services such as HTTP and web applications. If all of these tasks were collapsed into one layer, networks would become harder to design, less flexible, and much more difficult to troubleshoot because every protocol would need to handle too many responsibilities at once.

Your answers must show architectural reasoning.
B. Layer 5 helps manage communication state by maintaining the session between two systems during an exchange. Layer 6 handles formatting and encryption, which was visible in the TLS handshake when using openssl s_client -connect example.com:443. Layer 7 controls application behavior, such as when curl http://example.com and curl https://example.com request web resources using HTTP or HTTPS. Layer 4 alone is insufficient because reliable delivery does not provide encryption, session handling, or application meaning. TCP makes sure the data arrives correctly, but TLS protects it, and the application layer gives the data purpose and structure.


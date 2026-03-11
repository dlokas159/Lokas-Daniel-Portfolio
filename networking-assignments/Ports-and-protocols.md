# 1. Design and Planning
## Transport Layer Reliability
### Part 1 — Build the Network

#### Investigation 1 — Connection Establishment (Three-Step Setup)
##### Step A — Reset and Prepare & Step B — Generate TCP Traffic
<img width="699" height="177" alt="Screenshot 2026-03-04 at 2 45 02 PM" src="https://github.com/user-attachments/assets/e926bc1d-c40a-44fe-bf2e-b560a1f2d48a" />

##### Step C — Step Through the First Three Packets Only

[video](https://github.com/user-attachments/assets/e7390416-2681-4d37-af14-bb8b02abea90)

Record in your digital portfolio:
1. What flag appears in the first packet?
2. What flag(s) appear in the second?
3. What flag appears in the third?
4. After which packet does data begin?

#### Investigation 2 — Acknowledgment and Ordering
<img width="463" height="558" alt="Screenshot 2026-03-04 at 2 47 28 PM" src="https://github.com/user-attachments/assets/44414379-519a-40e5-ae2e-9c04ec4d98ea" />
<img width="464" height="527" alt="Screenshot 2026-03-04 at 2 47 58 PM" src="https://github.com/user-attachments/assets/0c385b3e-86b1-4482-9ee8-987ccb71ea5f" />

1. Do sequence numbers increase?
2. Do acknowledgment numbers increase?
3. Does the sender transmit additional data before receiving acknowledgment?
4. What does this imply about how TCP ensures delivery?
If the link were interrupted, what would the sender expect?

#### Investigation 3 — Header Fields and Error Detection
<img width="461" height="407" alt="Screenshot 2026-03-04 at 2 48 17 PM" src="https://github.com/user-attachments/assets/ab765c26-954d-446f-bd37-a91ea4234b17" />
Answer:
1. What is the purpose of the checksum?
2. If the checksum failed, would the receiver accept the data?
3. If data were rejected, what would logically happen next?**


### Part 2 — Observing TCP Behavior
#### Step 1: Switch to Simulation Mode & Step 2: Generate TCP Traffic & Step 3: Filter for TCP
<img width="342" height="297" alt="Screenshot 2026-03-03 at 1 32 51 PM" src="https://github.com/user-attachments/assets/4ffc418a-4688-4aff-bc95-95cf096c4210" />

#### Step 4: Run the Simulation Slowly

[video](https://github.com/user-attachments/assets/af97f347-9ba6-44fd-9785-c447196ac180)

### Part 3 — Observe UDP Behavior
#### Step 1: Clear Simulation Step 2: Generate UDP Traffic
<img width="301" height="195" alt="Screenshot 2026-03-03 at 1 38 08 PM" src="https://github.com/user-attachments/assets/2a35be62-94f4-4fa1-bacd-47de3784ffd5" />

| Feature           | TCP                              | UDP                           |
|------------------|----------------------------------|--------------------------------|
| Connection setup |        |                   |
| Acknowledgment   |                              |                            |
| Ordering         |                       |                 |
| Retransmission   |  |                            |
| Overhead         |                            |                         |

### Part 4
Step 1 — Start TCP Traffic
Switch to Simulation Mode.
Generate HTTP request again.
Step 2 — Interrupt the Link
Click the Switch → Config tab.
Select active FastEthernet interface.
Set Port Status = Off
This simulates a link failure.
Step 3 — Step Forward
Click Capture/Forward repeatedly.
Observe:
• Do packets stop arriving?
• Does the sender attempt retransmission?
• Do sequence numbers repeat?

Step 4 — Restore Connectivity
Set Port Status back to On.
Continue stepping.

<img width="343" height="335" alt="Screenshot 2026-03-04 at 2 53 04 PM" src="https://github.com/user-attachments/assets/2b4257a9-711a-45ef-8b77-c342730c8747" />

In paragraph form on your digital portfolio, answer
• What evidence shows TCP detected loss?
• What evidence shows retransmission?
• Why does communication not permanently break?

### Part 5 — Port Number Rigor
In paragraph form on your digital portfolio answer:
• Why does Layer 4 use port numbers?
• What problem do ports solve that IP cannot?
• How does the system distinguish multiple browser tabs?
• Does UDP also use ports?

# 2. Technical Development
## Investigation 1 — Connection Establishment
Before data is sent:
1. How many steps occur?
2. What flags appear in the first packet?
3. What flags appear in the second?
4. What confirms the connection is established?
Document the order exactly as observed. Do not define “three-way handshake.”
Describe what you see first.

## Investigation 2 — Acknowledgment and Ordering
Continue stepping through the simulation.
Observe:
• Do acknowledgment numbers increase?
• Do sequence numbers increase?
• Is data sent before confirmation?
Answer:
1. What happens if one segment is not acknowledged?
2. How would the sender detect that?
3. What evidence suggests retransmission would occur?
Support answers using packet details.

## Investigation 3 — TCP Header Fields
Open any TCP segment.
Locate:
• Sequence Number
• Acknowledgment Number
• Header Length
• Checksum
Answer:
1. What might the checksum protect against?
2. If checksum verification failed, would the receiver accept the data?
3. What would logically happen next?

## Part 1 — Full Stack Analysis: HTTP vs HTTPS
### Step 1 
curl -I http://example.com
ss -tn
<img width="1348" height="242" alt="unnamed (18)" src="https://github.com/user-attachments/assets/229d395f-3f88-4520-8d4a-0c6e7da9671e" />

### Step 2
curl -I https://example.com
ss -tn
<img width="1328" height="256" alt="unnamed (19)" src="https://github.com/user-attachments/assets/6d42fc47-982b-4523-8aaa-dfb6b25248b3" />

Now answer in paragraph form (with evidence) on your digital portfolio:
1. What changed at the application layer?
2. What changed at the transport layer?
3. What port numbers are involved?
4. What additional protocol appears between HTTP and TCP?
5. Is TLS replacing TCP — or operating above it?
Your explanation must trace:
Application → Encryption → Transport → IP

## Part 2 — DNS as a Supporting Application Protocol
nslookup example.com
<img width="380" height="252" alt="Screenshot 2026-03-11 at 12 48 30 PM" src="https://github.com/user-attachments/assets/0f1cc5c6-dcc9-4254-8ce1-0d26b67c233d" />

In paragraph form, and with evidence, on your digital portfolio, answer:
1. What port does DNS typically use?
2. Does it usually use TCP or UDP?
3. Why does DNS not require guaranteed delivery in most cases?
4. When might DNS switch to TCP?
Support reasoning with protocol design principles from the second lesson in this unit, called
“2TCP_UDP_ComparingTransmissionTypes”.

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

On your digital portfolio and in paragraph form, clearly answer (with evidence):
1. What port is SSH using?
2. What transport protocol is underneath it?
3. Is this connection encrypted?
4. What evidence supports your answer?
5. Which OSI layers are involved in this remote session?

## Part 4 — Secure File Transfer
echo "Layered Networking Test" > stacktest.txt
scp stacktest.txt your_username@localhost:/home/your_username/
<img width="709" height="241" alt="Screenshot 2026-03-11 at 12 54 31 PM" src="https://github.com/user-attachments/assets/64c58ff9-82cd-40a5-af01-eec7087ef029" />

Fully answer (in paragraph form, with evidence, on your digital portfolio):
1. What protocol does SCP rely on?
2. Does SCP require TCP?
3. Is the file encrypted?
4. What would happen if TCP reliability were removed?
5. Which layers are involved in this transfer?
Map the stack explicitly.

## Part 5 — Stack Mapping Requirement
Choose ONE of the following:
• HTTPS request
• SSH session
• SCP transfer

Construct a layered analysis:

| Layer        | Protocol | Purpose |
|--------------|----------|---------|
| Application  |          |         |
| Presentation |          |         |
| Session      |          |         |
| Transport    |          |         |
| Network      |          |         |

You must:
• Fill every layer.
• Justify each placement.
• Reference command output as evidence.
On your digital portfolio and in paragraph form, answer clearly and provide evidence:
1. Why does SSH require TCP?
2. Why is encryption not handled at Layer 3?
3. Why does HTTP not provide its own reliability?
4. What would break if port numbers did not exist?
5. Why separate remote access from file transfer protocols?
Write a structured paragraph on your digital portfolio explaining:
• How routing (Layer 3)
• Reliability (Layer 4)
• Encryption (Layer 6)
• Application logic (Layer 7)
work together in a single transaction.
Your explanation must:
• Reference curl
• Reference ssh
• Reference port numbers
• Distinguish between TCP reliability and TLS encryption
Avoid phrases like:
“Everything just works together.”

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

HTTP status codes are handled at theApplication Layer because they describe the meaning of a web request and response. The Transport Layer, which uses TCP, is responsible for reliably delivering data between computers. TCP ensures that packets arrive correctly and in order, but it does not understand the meaning of the data being sent. HTTP, which operates at the Application Layer, defines how web browsers and servers communicate about web resources. Because status codes describe the outcome of an HTTP request (such as success, redirect, or error), they must be handled at the Application Layer where the web communication rules are defined.

---

### Task 4 — Reasoning About Web Behavior

A server might return 301 Moved Permanently instead of just sending the new page so that browsers and search engines know the page has a new permanent address. This allows them to update bookmarks and indexes to the correct location. 404 errors are common on the internet because pages are often deleted, moved, or linked incorrectly, which causes the server to be unable to find the requested resource. A *500 Internal Server Error suggests that something went wrong on the server itself, such as a coding error, misconfiguration, or software failure that prevented the server from completing the request.


# 3. Testing & Evaluation
## Part 1 — Predict Before Testing
Before running any commands, answer in paragraph form in your digital portfolio:
1. What makes TCP “connection-oriented”?
2. What makes UDP “connectionless”?
3. If you send data using UDP and it never arrives, what happens?
4. Which protocol do you believe consumes more overhead? Why?

## Part 2 — Observing Listening Sockets (System Readiness)
### Step 1 — View Listening TCP Ports
ss -tln
<img width="1420" height="296" alt="unnamed (7)" src="https://github.com/user-attachments/assets/6bd34858-d210-4c72-9315-cff7addb3349" />

### Step 2 — Identify the Process Using a Port
sudo ss -tlpn
<img width="716" height="258" alt="Screenshot 2026-03-06 at 8 19 54 AM" src="https://github.com/user-attachments/assets/1c078f1e-36d5-4195-b304-404f62796cd8" />

Now answer in your digital portfolio:
• Which process is using port 22 (if visible)?
• If port 22 does not appear, what does that suggest?
• What is the difference between:
o A port existing
o A port listening

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

Digital Portfolio — Explain (with any evidence):
• What evidence shows LISTEN?
• What evidence shows ESTAB?
• What changed between ss -tln and ss -tn?
• Why does this prove TCP is connection-oriented?

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
Using system evidence, answer:
• Does UDP ever show ESTAB?
• What does UNCONN imply?
• Does UDP create persistent connection state?
• What happens if one terminal closes abruptly?
• Is there a handshake?
• Is there a formal teardown?

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

Digital Portfolio — Explain:
• Why does the operating system automatically assign an ephemeral port to the
client side of a TCP connection?
• Difference between:
o Listening port
o Ephemeral port
• Does UDP use ports?
• Why do ports exist if we already have IP addresses?
You must distinguish clearly between:
IP address → device
Port number → application

| Application        | Protocol | Why? |
|--------------------|----------|------|
| Online Banking     |          |      |
| Zoom Call          |          |      |
| Netflix Streaming  |          |      |
| File Download      |          |      |
| DNS Query          |          |      |

## Part 1 — Application Layer Investigation
### Step 1 — Inspect an HTTP Transaction
curl -I http://example.com
<img width="421" height="261" alt="Screenshot 2026-03-09 at 9 19 25 AM" src="https://github.com/user-attachments/assets/21593c7d-6ebf-4505-a253-ede0650e2ef6" />

Answer in paragraph form in your digital portfolio (and provide evidence):
1. What protocol is being used?
2. What transport protocol is underneath it?
3. How do you know?
4. Which layer is responsible for interpreting “200 OK”?

### Step 2 — Inspect an HTTPS Transaction
curl -I https://example.com
<img width="440" height="215" alt="Screenshot 2026-03-09 at 9 20 56 AM" src="https://github.com/user-attachments/assets/ef747178-7953-4a3e-86f1-da7d0ec0d524" />

Answer in paragraph form and provide evidence on your digital portfolio:
1. What changed?
2. What additional protocol must now be involved?
3. Does HTTP itself provide encryption?
4. Where does encryption logically occur?

## Part 2 — Presentation Layer Investigation
openssl s_client -connect example.com:443
<img width="968" height="694" alt="Screenshot 2026-03-09 at 9 22 30 AM" src="https://github.com/user-attachments/assets/c5a8a005-0ed4-4dd8-9b4c-366159fe76b7" />

Answer:
1. What is being exchanged before data transfer?
2. Is this Layer 4 behavior?
3. What problem is this solving?
4. Why must this occur before application data is sent?

## Conceptual Distinction
Without looking anything up, answer in paragraph form on your digital portfolio:
• If TLS encrypts data, is it replacing TCP?
• Or is it operating above it?
Your answer must distinguish between:
• Reliable transport
• Data formatting and encryption

## Part 3 — Session Layer Investigation
curl https://example.com & ss -tn
<img width="1916" height="398" alt="unnamed (17)" src="https://github.com/user-attachments/assets/1d12c4be-f866-4ea2-b676-d11382822ff6" />

Answer in paragraph form and reference evidence on your digital portfolio:
1. Is the connection still active?
2. What state is it in?
3. When does the session end?
4. Who decides that?
5. If you log into a website with a username and password:
• Is that TCP managing your login?
• Or is that handled at a higher layer?

| Protocol | Layer | Purpose |
|----------|-------|---------|
| HTTP     |       |         |
| HTTPS    |       |         |
| TLS      |       |         |
| DNS      |       |         |
| TCP      |       |         |

# 4. Reflection and Analysis
## Assignment 1 Reflection: 
Explain clearly in well-written paragraphs on your digital portfolio:
• How TCP detects loss
• How TCP confirms delivery
• Why deleting a TCP segment does not permanently break communication
• Why ICMP behaves differently
• Why reliability increases overhead
Your answer must reference:
• At least one packet header
• At least one observed retransmission
• Clear separation of Layer 3 vs Layer 4

2. Why does deleting a TCP segment not permanently break communication?
3. Why does deleting an ICMP packet behave differently?
4. What role do port numbers play in reliable communication?

## Assignment 2 Reflection:
Final Reflection
Return to your initial predictions.
Now write a structured paragraph explaining:
• Structural difference between TCP and UDP
• What makes TCP reliable (handshake, sequence numbers, acknowledgments)
• Why UDP avoids reliability
• How ports enable multiplexing
• Why protocol overhead matters

You must reference:
• At least one ss output
• At least one netcat experiment
Be architectural. Avoid vague phrasing.

## Assignment 3 Reflections: 
A. On your digital portfolio, in paragraph form, answer the following, making sure to
provide evidence:

1. Why does encryption not occur at Layer 3?
2. Why does TCP not handle user authentication?
3. Why separate:
• Transport reliability
• Encryption
• Application logic
4. What would break if all of this were collapsed into one layer?

Your answers must show architectural reasoning.
B. Write a structured paragraph explaining:
• What role Layer 5 plays in managing communication state
• What role Layer 6 plays in formatting and encryption
• What role Layer 7 plays in application behavior
• Why Layer 4 alone is insufficient
Your explanation must:
• Reference at least one curl command
• Reference the TLS handshake observation
• Distinguish between TCP reliability and TLS encryption

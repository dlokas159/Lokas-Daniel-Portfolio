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

5. ## Assignment 2 Reflection:
6. Final Reflection
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

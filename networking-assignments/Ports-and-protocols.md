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


# 4. Reflection and Analysis
## Assignment Reflection: 
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

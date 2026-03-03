# 1. Design and Planning
## Transport Layer Reliability
### Part 1 — Build the Network

#### Step 1: Create the Topology & Step 2: Connect Devices
<img width="406" height="297" alt="Screenshot 2026-03-03 at 1 27 04 PM" src="https://github.com/user-attachments/assets/cefb850f-a288-4f8d-a47f-c374ed1a004c" />z

#### Step 3: Assign IP Addresses
<img width="652" height="202" alt="Screenshot 2026-03-03 at 1 29 16 PM" src="https://github.com/user-attachments/assets/19902542-b4b8-4653-bb5b-3078b676740b" />
<img width="641" height="135" alt="Screenshot 2026-03-03 at 1 29 31 PM" src="https://github.com/user-attachments/assets/67520ddc-3165-4a67-8360-6cacd1348e7c" />

#### Step 4: Verify Connectivity
<img width="298" height="183" alt="Screenshot 2026-03-03 at 1 29 55 PM" src="https://github.com/user-attachments/assets/473243ed-e7e4-4025-818f-cc86dcbb1048" />
1. What layer is responsible for this ping?
2. Is ping using TCP or UDP?
3. Does successful ping prove TCP reliability?

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

## Part 2 — The Conceptual Trap

## Part 3 — Port Number Rigor


# 4. Reflection and Analysis
## Activity 1 Reflection: 
Now that you have completed all of the activities, write about these in a clear summary
paragraph:
1. Why would live video prefer UDP?
2. Why would financial transactions require TCP?
3. Which protocol introduces more overhead?
4. Which protocol reduces latency?
5. Why is reliability not always desirable?
Also include a structured paragraph explaining:
• Why Layer 3 cannot guarantee successful communication
• What mechanisms Layer 4 introduces
• What problem TCP solves
• Why UDP intentionally does not solve that problem
Your explanations must:
• Use correct terminology
• Reference Packet Tracer evidence
• Avoid vague phrasing

## Assignment 1 Final Reflection
On your digital portfolio, write a short, structured response answering:
1. What mechanism allows TCP to recover from packet loss?
2. Why does deleting a TCP segment not permanently break communication?
3. Why does deleting an ICMP packet behave differently?
4. What role do port numbers play in reliable communication?

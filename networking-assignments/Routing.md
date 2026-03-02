# 1. Design & Planning
## Investigation 1 — Your Machine’s Layer 3 Identity
### VM #1
<img width="718" height="437" alt="Screenshot 2026-02-23 at 8 43 24 AM" src="https://github.com/user-attachments/assets/c1327fc8-33cf-4f8f-9b83-96611858fe00" />

### VM #2
<img width="646" height="392" alt="Screenshot 2026-02-23 at 8 43 38 AM" src="https://github.com/user-attachments/assets/39e1ba2a-c3d0-4528-8731-8df386a738ba" />

### Questions: 
1. What is your IPv4 address?
2. What network are you on?
3. Is a default route present?
4. What device is listed as your gateway?

### Answer these questions:
1. Where is that information stored?
2. What would happen if the default gateway entry disappeared?

# 2. Technical Development
## Part 1 – Your Inside Identity
<img width="717" height="331" alt="Screenshot 2026-02-25 at 10 34 09 AM" src="https://github.com/user-attachments/assets/85f8dea2-4d4f-4971-8049-4952d238590b" />

### As a description to your screenshot, answer the following on your digital portfolio.
1. What is your IPv4 address?
2. Is this address globally unique?
3. Could another network somewhere else in the world use the same address?
4. What clues help you determine this?

### Now verify your thinking. Search online for:
“RFC1918 address ranges”
Identify the three private IPv4 ranges. Determine whether your IP falls within one of
those ranges. Write about this on your digital portfolio.

## Part 2 – Your Outside Identity
<img width="642" height="64" alt="unnamed (1)" src="https://github.com/user-attachments/assets/0810e73b-9154-4c5c-a325-31bcfb7f0b55" />

| Questionj | Private Address | Public Address |
|--------|--------------------|------------|
| Are they the same? |  |  |
| Why or why not? |  |  |

### Document all evidence on your digital portfolio and answer in paragraph form:
• Why does your machine appear to have two different IP addresses?
• What device or system is responsible for this translation?
• Where is that device located in the network?

## Part 3 – The “Can I Reach You?” Investigation (with a partner)
### Step 1 – Private Address Test
<img width="1382" height="350" alt="unnamed (2)" src="https://github.com/user-attachments/assets/ddd6eba8-260a-4c65-96c0-7c49f2aff570" />

### Step 2 – Public Address Test
<img width="1180" height="218" alt="unnamed (3)" src="https://github.com/user-attachments/assets/ac745249-8963-4bd7-97fb-112b397d7d2c" />

### Write about this on your digital portfolio, but be sure your response answers the following:
1. Do you and your partner share the same public IP?
2. Why might multiple devices appear to share one public IP?
3. If pinging a partner’s public IP fails, what might be blocking it?
4. Does the failure mean the address does not exist? Or does it suggest filtering?

## Part 1 - Build the network 
### Steps 1 & 2
#### Topology Layout
<img width="652" height="122" alt="Screenshot 2026-02-26 at 12 37 53 PM" src="https://github.com/user-attachments/assets/452926a6-f06e-4411-80df-bfe15eca2608" />

### Step 3
### IP Addresses Configured
<img width="645" height="184" alt="Screenshot 2026-02-26 at 12 38 42 PM" src="https://github.com/user-attachments/assets/9cbfbf87-79b5-47fc-be6c-afc92ccbaeda" />
<img width="638" height="175" alt="Screenshot 2026-02-26 at 12 38 55 PM" src="https://github.com/user-attachments/assets/355693be-52a0-4f04-a454-596e8f96bcf7" />

### Step 4
### Router Interface Configured
<img width="474" height="242" alt="Screenshot 2026-02-26 at 12 39 22 PM" src="https://github.com/user-attachments/assets/0b11c61e-3f5d-4659-b0c9-f5a3a685dbbe" />

## Part 2 - Observe Same-Network Communication
### Simulated PDU Movement
[video](https://github.com/user-attachments/assets/7a385781-aae0-4ea9-8b56-4df769731442)

Observe carefully:
• Does the packet go through the router or stay on the left side? no, stays on left
• What happens before the first ICMP packet is sent?
• Do you see ARP appear?

## Part 3 - Observe Inter-Network Communication
### Simulated Packet from PC0 --> PC1
[video](https://github.com/user-attachments/assets/e1c22b33-c935-4ae4-b691-29fd740d44cb)

When the packet leaves PC0:
• Destination IP?
• Destination MAC?
When it reaches the router:
• What happens to the Ethernet frame?
• Does the router keep the same MAC?
• Does the router keep the same IP?
When it leaves the router:
• What has changed?

• What has stayed constant?
You must identify:
• What is rebuilt at each hop
• What is preserved from start to finish

## Part 5 – Failure Thought Experiment
### Failed Attempt After Deleting the Router
<img width="637" height="128" alt="Screenshot 2026-02-26 at 12 56 38 PM" src="https://github.com/user-attachments/assets/135b8482-93c5-4509-86cf-9d2cda17b182" />
Answer on your digital portfolio:
• At what precise moment does communication break?
• Why can switches not solve this problem?
• What is the router doing that no other device can do?



# 3. Testing & Evaluation
## Investigation 2 — Three Destinations
### Case 1 — Send Traffic to Itself (Loopback)
<img width="579" height="174" alt="Screenshot 2026-02-23 at 8 55 03 AM" src="https://github.com/user-attachments/assets/bb683294-9804-432e-86f4-81e33300ffb8" />

#### Questions:
• Did this traffic leave your machine?
• Does the routing table need a gateway entry for this to work?

### Case 2 — Send Traffic to the Other VM (Same Network)
<img width="567" height="176" alt="Screenshot 2026-02-24 at 9 10 54 AM" src="https://github.com/user-attachments/assets/740e5882-0afc-4f3a-9317-4867c54375a2" />

#### Questions:
• Did Ubuntu send this to the default gateway?
• Which routing table entry allowed direct delivery?
• How can you prove it?

### Case 3 — Send Traffic Off the Network
<img width="574" height="188" alt="Screenshot 2026-02-24 at 9 14 21 AM" src="https://github.com/user-attachments/assets/dbac1052-d37e-43f7-b493-8ab42a1b4d23" />

#### Questions:
• What routing table entry made this possible?
• Why can Ubuntu not deliver this directly?
• What device handled the first step?

## Investigation 3 — How the Decision Is Made
Will the next hop be:
• Direct?
• **Gateway**
<img width="1386" height="266" alt="unnamed" src="https://github.com/user-attachments/assets/c23a6ec5-a2bd-4397-a0bd-7a2f47049cfe" />

##  Part 1 - Predict Before Testing 
<img width="692" height="146" alt="Screenshot 2026-03-02 at 9 48 18 AM" src="https://github.com/user-attachments/assets/00740512-0a8c-453a-8f2d-0d99adf47265" />

Identify:
• Your directly connected network
• Your default route
• Your gateway IP

If you send traffic to:
1. The other VM
2. 8.8.8.8
3. google.com
For each, predict:
• Will it go directly or through the gateway?
• What will the first hop be?
• How many hops do you expect?
• Why?

## Part 2 – Run Traceroute
<img width="725" height="397" alt="Screenshot 2026-03-02 at 9 54 47 AM" src="https://github.com/user-attachments/assets/0b387bfd-b43e-4270-b79e-c949858611dd" />

Step 1: Identify the first hop.
Step 2: Identify where private addresses stop appearing.
Step 3: Count total hops.

<img width="721" height="684" alt="Screenshot 2026-03-02 at 9 58 08 AM" src="https://github.com/user-attachments/assets/95c3516b-68da-4dd8-91a1-deaf68287231" />

On your digital portfolio, compare:
• Is the first hop the same?
• Is the total hop count the same?
• Where do the paths diverge?

## Part 3 – Interpret What You Are Seeing
For at least one traceroute output, create a structured analysis:
Complete the following on your digital portfolio. For each of the first 5 hops:
• Is the IP private or public?
• What device is this likely?
• Why?
• Is this inside your LAN, your ISP, or backbone infrastructure?
Use reasoning, not guesses.

## Part 4 – Validate with Routing Table
ip route get 8.8.8.8
<img width="1086" height="120" alt="unnamed (5)" src="https://github.com/user-attachments/assets/bced2aee-24de-42bb-adaa-2c81e7880137" />

On your digital portfolio, answer:
• What is the next hop?
• What interface is used?
• Does this match the first hop of traceroute?

ip route get <other VM IP>
<img width="890" height="120" alt="unnamed (4)" src="https://github.com/user-attachments/assets/51602d97-efd2-45e5-95ac-989d438a2f71" />

Critical Thinking (again, on your digital portfolio)
Why does ip route get only show one hop, but traceroute shows many?
What layer is each tool exposing?

## Part 5 – TTL Experiment
<img width="1116" height="212" alt="unnamed (6)" src="https://github.com/user-attachments/assets/5b67b10c-78d1-4aa4-bb2a-44f510365463" />
ONLY STARS POP UP

Observe:
• Where does it stop?
• Why?
Now, and your digital portfolio, answer:
• What is TTL?
• Why must routers decrement it?
• How does this allow traceroute to work?


# 4. Reflection & Analysis

## Explain, in your own words in a well-written paragraph:
1. What is the role of the routing table?
2. What is the role of the default gateway?
3. What condition must be true for direct delivery?
4. What condition requires router involvement?

## Part 4 – NAT Reasoning
Without searching for a formal definition, explain the following:
1. Why are private IPv4 addresses reused in millions of different networks?
2. Why are private addresses not routed on the public internet?
3. What would happen if every internal device required its own public IP?
4. Why does a business typically have one public IP but many internal devices?

## Part 4 - Analytical Pause
Without looking anything up, answer on your digital portfolio:
1. Why does the switch never modify the IP address?
2. Why must the router modify the MAC address?
3. Why does the source IP remain the same from PC0 to PC1?
4. What exactly does “next hop” mean in this simulation?
5. Why is the default gateway necessary?
6. How does this affect WAN design?

## Final Synthesis
Without looking anything up (and on your digital portfolio), explain clearly:
1. How can you determine the path of data from your device?
2. What does the first hop represent?
3. Why do private IPs appear early in the path?
4. Why can two different destinations share the same first several hops?
5. What is the difference between:
• A routing-table decision
• A traceroute path
Your explanation must reference:
• At least one routing-table output
• At least one traceroute observation

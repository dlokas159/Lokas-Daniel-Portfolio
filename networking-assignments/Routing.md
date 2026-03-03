# 1. Design & Planning
## Investigation 1 — Your Machine’s Layer 3 Identity
### VM #1
<img width="718" height="437" alt="Screenshot 2026-02-23 at 8 43 24 AM" src="https://github.com/user-attachments/assets/c1327fc8-33cf-4f8f-9b83-96611858fe00" />

### VM #2
<img width="646" height="392" alt="Screenshot 2026-02-23 at 8 43 38 AM" src="https://github.com/user-attachments/assets/39e1ba2a-c3d0-4528-8731-8df386a738ba" />

### Reflection
The information is stored in the computer’s operating system networking configuration and routing table, which keeps track of IP settings and network paths. The computer could still communicate with devices on the same network, but it would not be able to reach the internet or other networks.

# 2. Technical Development
## Part 1 – Your Inside Identity
<img width="717" height="331" alt="Screenshot 2026-02-25 at 10 34 09 AM" src="https://github.com/user-attachments/assets/85f8dea2-4d4f-4971-8049-4952d238590b" />

### Reflction
My device uses a private IP address, which is not globally unique. Other networks can reuse the same private address ranges because they are reserved for internal use (10.0.0.0/8, 172.16.0.0–172.31.255.255, and 192.168.0.0/16). Since my address falls within one of these ranges, it is meant only for local communication inside the network.

## Part 2 – Your Outside Identity
<img width="642" height="64" alt="unnamed (1)" src="https://github.com/user-attachments/assets/0810e73b-9154-4c5c-a325-31bcfb7f0b55" />

| Question            | Private Address | Public Address |
|---------------------|----------------|----------------|
| Are they the same?  | No             | No             |
| Why or why not?     | A private IP address is used within a local network and is not accessible from the internet. | A public IP address is assigned by an ISP and is visible on the internet. It allows communication outside the local network. |

### Reflection
My machine appears to have two IP addresses because one is private (used inside my local network) and the other is public (used on the internet). The router performs Network Address Translation (NAT), which translates private addresses into a public one. This device is located at the edge of the network, typically the home or school router.

## Part 3 – The “Can I Reach You?” Investigation (with a partner)
### Step 1 – Private Address Test
<img width="1382" height="350" alt="unnamed (2)" src="https://github.com/user-attachments/assets/ddd6eba8-260a-4c65-96c0-7c49f2aff570" />

### Step 2 – Public Address Test
<img width="1180" height="218" alt="unnamed (3)" src="https://github.com/user-attachments/assets/ac745249-8963-4bd7-97fb-112b397d7d2c" />

### Reflection
Devices on the same network often share one public IP address because NAT allows multiple internal devices to access the internet using a single external address. If pinging a public IP fails, it is usually because a firewall or router is blocking ICMP traffic, not because the address does not exist. Network security settings commonly prevent direct responses.

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

### Reflection 
Devices on the same network often share one public IP address because NAT allows multiple internal devices to access the internet using a single external address. If pinging a public IP fails, it is usually because a firewall or router is blocking ICMP traffic, not because the address does not exist. Network security settings commonly prevent direct responses.

## Part 3 - Observe Inter-Network Communication
### Simulated Packet from PC0 --> PC1
[video](https://github.com/user-attachments/assets/e1c22b33-c935-4ae4-b691-29fd740d44cb)

### Reflection
When traffic moves between networks, the router removes the old Ethernet frame and creates a new one for the next network segment. The MAC address changes at each hop because MAC addresses only work locally, but the source and destination IP addresses remain constant from start to finish.

## Part 5 – Failure Thought Experiment
### Failed Attempt After Deleting the Router
<img width="637" height="128" alt="Screenshot 2026-02-26 at 12 56 38 PM" src="https://github.com/user-attachments/assets/135b8482-93c5-4509-86cf-9d2cda17b182" />

### Reflection
Communication breaks when traffic needs to leave the local network but there is no router to forward it. Switches cannot solve this problem because they only operate within a single network. A router is required to connect different networks and determine the next hop for packets.

# 3. Testing & Evaluation
## Investigation 2 — Three Destinations
### Case 1 — Send Traffic to Itself (Loopback)
<img width="579" height="174" alt="Screenshot 2026-02-23 at 8 55 03 AM" src="https://github.com/user-attachments/assets/bb683294-9804-432e-86f4-81e33300ffb8" />

#### Reflection
When testing loopback, traffic never leaves the device and no gateway is needed. For same-network communication, packets are delivered directly using a connected route, so the default gateway is not used. For off-network communication, the default route sends traffic to the router, which handles forwarding. The ip route get command shows the local routing decision, while traceroute reveals every hop along the entire path.

### Case 2 — Send Traffic to the Other VM (Same Network)
<img width="567" height="176" alt="Screenshot 2026-02-24 at 9 10 54 AM" src="https://github.com/user-attachments/assets/740e5882-0afc-4f3a-9317-4867c54375a2" />

#### Reflection
TTL (Time To Live) limits how long a packet can travel across routers. Each router decreases the TTL by one to prevent packets from looping forever. Traceroute works by sending packets with small TTL values, causing each router along the path to respond when the TTL expires.

### Case 3 — Send Traffic Off the Network
<img width="574" height="188" alt="Screenshot 2026-02-24 at 9 14 21 AM" src="https://github.com/user-attachments/assets/dbac1052-d37e-43f7-b493-8ab42a1b4d23" />

#### Reflection
The routing table entry that made this possible was the default route (0.0.0.0/0) pointing to the gateway. Ubuntu cannot deliver this traffic directly because the destination is outside the local subnet, meaning it does not share the same network address. Since it is off-network, the system must forward the packet to the router. The router (default gateway) handled the first step by receiving the packet and forwarding it toward the destination network.

## Investigation 3 — How the Decision Is Made
Will the next hop be:
• Direct?
• **Gateway**
<img width="1386" height="266" alt="unnamed" src="https://github.com/user-attachments/assets/c23a6ec5-a2bd-4397-a0bd-7a2f47049cfe" />

##  Part 1 - Predict Before Testing 
<img width="692" height="146" alt="Screenshot 2026-03-02 at 9 48 18 AM" src="https://github.com/user-attachments/assets/00740512-0a8c-453a-8f2d-0d99adf47265" />

### Reflection
The directly connected network is the subnet assigned to the active interface. The default route is 10.12.16.1, and the gateway IP is the internal address of the router. Traffic sent to another VM on the same subnet will go directly, with the first hop being the destination itself and typically requiring only one hop. Traffic sent to 8.8.8.8 or google.com will go through the gateway because those destinations are outside the local subnet. The first hop will be the router, and multiple hops are expected because the packet must traverse ISP and backbone routers to reach the destination.

## Part 2 – Run Traceroute
<img width="725" height="397" alt="Screenshot 2026-03-02 at 9 54 47 AM" src="https://github.com/user-attachments/assets/0b387bfd-b43e-4270-b79e-c949858611dd" />

<img width="721" height="684" alt="Screenshot 2026-03-02 at 9 58 08 AM" src="https://github.com/user-attachments/assets/95c3516b-68da-4dd8-91a1-deaf68287231" />

### Reflection
The first hop in traceroute should be the default gateway. Private IP addresses typically appear at the beginning of the path because those routers are within the LAN or the ISP’s internal infrastructure. Private addresses stop appearing once traffic enters publicly routed internet infrastructure. The total hop count represents the number of routers traversed. When comparing traceroutes to different destinations, the first hop is usually identical because traffic exits through the same gateway. Paths diverge further along once packets reach different backbone routing paths.

## Part 3 – Interpret What You Are Seeing
In the first five hops of traceroute output, the first IP address is usually private and represents the local router inside the LAN. The next one or two hops may also belong to private or ISP-managed infrastructure. After this point, public IP addresses appear, representing regional ISP routers or backbone infrastructure. Private IP addresses indicate internal routing within the LAN or ISP, while public IP addresses indicate broader internet routing beyond the provider’s internal network.

## Part 4 – Validate with Routing Table
ip route get 8.8.8.8
<img width="1086" height="120" alt="unnamed (5)" src="https://github.com/user-attachments/assets/bced2aee-24de-42bb-adaa-2c81e7880137" />

### Reflection
The next hop shown is the gateway IP address. The interface listed is the active network interface. This matches the first hop seen in traceroute, confirming that traffic is initially forwarded to the router before continuing across external networks.

ip route get <other VM IP>
<img width="890" height="120" alt="unnamed (4)" src="https://github.com/user-attachments/assets/51602d97-efd2-45e5-95ac-989d438a2f71" />

### Critical Thinking 
The ip route get command shows only one hop because it reveals the local routing decision made by the operating system. Traceroute shows multiple hops because it displays every router along the entire path to the destination. The routing table exposes the system’s Layer 3 forwarding decision, while traceroute exposes the full Layer 3 path across interconnected networks.

## Part 5 – TTL Experiment
<img width="1116" height="212" alt="unnamed (6)" src="https://github.com/user-attachments/assets/5b67b10c-78d1-4aa4-bb2a-44f510365463" />

### Reflection
When only stars appear in traceroute, it indicates that routers are not returning responses when the TTL expires, often due to filtering or firewall rules. TTL (Time To Live) is a value in the IP header that limits how many routers a packet may traverse. Routers decrement TTL to prevent packets from looping indefinitely. Traceroute works by sending packets with progressively increasing TTL values; when TTL reaches zero at a router, that router responds, revealing its position in the path.


# 4. Reflection & Analysis

## Reflection
The routing table determines how packets are forwarded based on destination networks. The default gateway is used when traffic must leave the local subnet. Direct delivery requires that both devices share the same subnet. Router involvement is required when the destination resides on a different network, since only routers can forward traffic between separate networks.

## Part 4 – NAT Reasoning
Private IPv4 addresses are reused because they are valid only within local networks and are not globally routed. They are not routed on the public internet to prevent address conflicts and conserve limited IPv4 space. If every internal device required a unique public IP, the available address space would quickly be exhausted. Businesses typically have one public IP and many internal devices because Network Address Translation (NAT) allows multiple internal systems to share a single external address efficiently.

## Part 4 - Analytical Pause
A switch does not modify the IP address because it operates at Layer 2 and forwards frames based on MAC addresses. A router modifies the MAC address at each hop because each network segment has different Layer 2 addressing. The source IP remains the same from origin to destination to preserve end-to-end identity. The “next hop” refers to the next router or device that a packet is forwarded to. The default gateway is necessary to enable communication beyond the local subnet. This hierarchical routing structure allows WANs to scale by interconnecting multiple networks through routers.

## Final Synthesis
The path of data from a device can be determined by examining the routing table and running traceroute. The first hop represents the default gateway, which connects the local network to external networks. Private IP addresses appear early in the path because traffic begins inside the LAN or ISP’s internal infrastructure. Different destinations may share the same first several hops because they exit through the same gateway and ISP routing path. A routing-table decision shows how the local system selects the next hop, while a traceroute path reveals the complete sequence of routers across the full network journey.




Your explanation must reference:
• At least one routing-table output
• At least one traceroute observation

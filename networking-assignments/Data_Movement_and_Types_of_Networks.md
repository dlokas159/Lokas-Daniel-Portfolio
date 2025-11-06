# Networking & Data Movement Digital Portfolio

## 1. Planning & Design

Prior to completing the networking labs, foundational concepts of LAN communication and data movement through layered network models were reviewed. Notes and diagrams were used to understand how addressing, routing, and protocol operations occur in a local network environment.

### Key Concepts Prepared:
- Local Area Networks (LANs) allow devices in the same environment to communicate directly.
- IP addresses identify devices for routing and communication.
- MAC addresses identify physical network interfaces.
- ICMP-based tools, such as `ping`, verify connectivity and measure delay.

### Simple LAN Diagram
This preparation established a clear understanding of how virtual machines emulate real-world device communication.

### Classwork Evidence
The following images document class activities related to network planning, OSI model understanding, and data movement demonstrations:

#### OSI Layer Matching Activity
##### First Attempt 
![IMG_2356](https://github.com/user-attachments/assets/10c10749-0090-4f75-996b-a31a693eec4e)


##### Correct organization
<img width="710" height="858" alt="IMG_2357" src="https://github.com/user-attachments/assets/9d2cf691-fddb-44a5-8471-417b56b1d00c" />



#### Base-10 and Base-25 Block Modeling Activities
These images show the use of visual and physical representations to understand how data units and addressing scale in network systems.
![IMG_2335](https://github.com/user-attachments/assets/7da27a73-2cfb-4a5d-9b7c-9cafb3533575)
![IMG_2343](https://github.com/user-attachments/assets/a9741950-eb41-4e4f-8afc-790ed2048b92)
![IMG_2339](https://github.com/user-attachments/assets/c3b7a8ed-807b-4f9d-82f4-8f148e8964f3)
![IMG_2337](https://github.com/user-attachments/assets/9c2d7634-1871-4767-81e7-8bc2b8bb23c0)
![IMG_2341](https://github.com/user-attachments/assets/5bbd9e76-57e0-49ea-b94e-e0e5c26d078e)
![IMG_2333](https://github.com/user-attachments/assets/d59dc53a-0d70-479c-95d0-8f86e1db43a4)


---

## 2. Technical Development

Ubuntu Virtual Machines were used to perform network analysis, connection testing, and data format conversions. Several networking tools and commands were executed to observe how devices identify each other and exchange data.

### Networking Tools and Their Functions
| Command/Tool | Purpose | OSI Layer |
|---|---|---|
| `ifconfig` / `ip a` | Displays IP address, network interface details, and broadcast address | Layer 3 |
| `ping` | Tests network reachability and measures latency | Layer 3 (ICMP) |
| `netstat -a` | Displays active connections and listening ports | Layer 4 |
| `nc` (Netcat) | Sends text data over TCP for reliable communication | Layer 4 |
| `ipcalc` | Converts IP addresses into binary and displays subnet mask structure | Layer 3 |
| `printf` | Converts decimal IP octets into hexadecimal format | Data Representation Layer |

### Completed Lab Activities
- IP address and subnet mask were identified on each VM using `ip a`
- Network reachability was verified using `ping`
- Active ports and sessions were observed using `netstat`
- A direct TCP communication session was established using `nc`
- Binary and hexadecimal representations of IP addresses were generated using `ipcalc` and `printf`

These steps demonstrated how network communication occurs, how addressing is structured, and how data can be examined in multiple numeric formats.

---

## 3. Testing & Evaluation

### Connectivity Testing
`ping` confirmed successful communication between networked virtual machines. The results displayed packet transmission counts, round-trip timing values, and demonstrated effective LAN connectivity without packet loss.

### Connection Monitoring
`netstat -a` provided insight into open ports and active TCP/UDP connections, showing which network services were currently operating.

### Data Representation Analysis
Binary and hexadecimal conversions revealed how:
- Binary is used internally by computers for addressing and data interpretation.
- Hexadecimal provides a compact and readable shorthand representation (commonly used for MAC addresses).
- Decimal notation is used for human readability in standard IP addressing.

This evaluation confirmed how the same address can be represented differently depending on use context and hardware/software interpretation.

---

## 4. Reflection & Professionalism

This set of labs demonstrated how devices communicate within a local network and how different addressing systems interact during that process. The exercises showed the functional roles of IP addresses, MAC addresses, and transport protocols in maintaining reliable data exchange. Additionally, examining binary and hexadecimal forms of network data provided a deeper understanding of how network information is processed at the machine level. The portfolio is formatted clearly and presented in a professional and technical structure.

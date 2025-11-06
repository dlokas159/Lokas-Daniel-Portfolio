## 1. Planning & Design

Before beginning the labs, I reviewed how LANs operate, how devices communicate across networks, and how data moves through the OSI and TCP/IP models. I used class notes and diagrams to understand how information is addressed, transmitted, and verified between two computers.

### Key Concepts I Prepared For:
- LANs allow devices in the same local network to communicate directly.
- IP addresses identify each device on a network.
- MAC addresses identify network hardware at the data-link layer.
- Ping and traceroute use ICMP to test network reachability and path traversal.

### Simple LAN Diagram
This planning helped me understand how communication happens between two virtual machines just like real computers on a network.

---

## 2. Technical Development

I used Ubuntu Virtual Machines to test and analyze network communication.

### Commands and Networking Tools Used
| Command/Tool | Purpose | OSI Layer |
|---|---|---|
| `ifconfig` / `ip a` | Display IP address, network interface, and broadcast info | Layer 3 |
| `ping` | Tests reachability and measures network latency | Layer 3 (ICMP) |
| `netstat -a` | Shows active connections and listening ports | Layer 4 |
| `nc` (Netcat) | Sends text messages between VMs reliably using TCP | Layer 4 |
| `ipcalc` | Converts and displays network addresses in binary | Layer 3 |
| `printf` | Converts IP segments from decimal to hexadecimal | Data Representation |

### What I Completed
- Identified my VM’s IP address and network mask using `ip a`
- Used `ping` to confirm communication with another device on the LAN
- Examined active network ports and listening services with `netstat`
- Sent and received text messages between VMs using `nc`
- Converted IP address values into binary and hexadecimal to understand how computers store them

These activities allowed me to see how network data is structured, transmitted, and tested in real time.

---

## 3. Testing & Evaluation

### Ping Results Interpretation
`ping` confirmed that the two virtual machines could communicate. The results displayed:
- Packets sent and received
- Round-trip time (latency)
- Network stability (no packet loss)

This demonstrated reliable LAN communication.

### Netstat & Netcat Interpretation
`netstat -a` revealed active TCP and UDP sessions, showing what ports were open.  
`nc` proved how TCP ensures data is delivered reliably from one system to another.

### Binary & Hex Conversion Results
- Binary revealed how IP addresses are represented internally by machines.
- Hexadecimal showed the compressed form used in device identification (such as MAC addresses).
- Decimal is primarily for human readability.

This confirmed how the same address can appear differently depending on the representation required.

---

## 4. Reflection & Professionalism

These labs helped me understand how network data travels between devices at both a hardware and software level. I learned how IP addresses allow devices to identify each other and how binary and hexadecimal systems play a role in how computers store and process that addressing information. Tools such as `ping`, `netstat`, and `nc` gave me hands-on experience with real network connections and communication. Understanding how these commands operate strengthened my knowledge of the OSI layers and how communication is organized and verified in real networks. Overall, this lab improved my confidence in working with network systems and analyzing how devices interact within a LAN.

---

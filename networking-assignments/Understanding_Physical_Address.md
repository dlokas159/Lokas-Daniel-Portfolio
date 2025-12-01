# Part A — Exploring a Network Interface Card (NIC)

Every MAC address belongs to a piece of physical hardware called a **Network Interface Card (NIC)**. Even virtual machines use *virtual NICs* that operate the same way.  
In this activity, you will examine a NIC, label its features, and identify where the MAC address is located.

---

## 1. Observing the NIC Images

Study **Image A** and **Image B** and note the following:

- Ethernet port on a metal bracket  
- Green circuit board  
- Several chips and components  
- Gold connector edge (PCIe connector)  

Your goal is to understand the major physical features of a NIC.

---

## 2. Labeling the NIC 

Label these components:

### **1. Ethernet Port (RJ-45 Port)**
Where the network cable plugs in.

### **2. PCIe Connector (Gold Edge)**
Fits into the motherboard; provides power and data transfer.

### **3. Main Controller Chip**
The “brain” of the NIC that sends and receives frames.

### **4. MAC Address Sticker**
Usually located on the metal bracket or near the port.

#### Tasks for Image A
- Draw an arrow to the Ethernet port and label it.  
- Draw an arrow to the PCIe connector and label it.  
- Draw an arrow to the main controller chip and label it.
![IMG_2413](https://github.com/user-attachments/assets/c910c166-67e9-455a-80b7-5a2a3b6b7284)


#### Task for Image B
- Draw an arrow to the MAC address label and label it.  
- Record the MAC address exactly as printed:  
  `04:92:22:64:IA:80:4C`  
- Write one sentence explaining what a MAC address does on a local network.
![IMG_2414](https://github.com/user-attachments/assets/97755f43-13d7-40ad-999d-3764e9b88d25)


---

## 3. Add to Your Digital Portfolio

Write **one sentence each** explaining:

- What the Ethernet port is used for  
- What the PCIe connector is used for  
- Why the NIC needs a main chip  
- Why the MAC address belongs to the NIC  

### Reflection Prompt
**“Why is a MAC address considered a physical address, and how does seeing a real NIC help you understand this?”**  
Write 2–3 sentences.

---

# Part B — Interpreting Your MAC Address

Now you will retrieve your MAC address from your Ubuntu VM and interpret it using the OUI (Organizationally Unique Identifier).

---

## 1. Retrieve Your MAC Address

Use the same command from the earlier lesson to find your MAC address.  
Example:


Record your own MAC address.
92:e1:0d:6f:d4:91 
---

## 2. Identify the OUI

The first **three pairs** of the MAC address are the **OUI**.

Example:  
- Full MAC: `52:54:00:ab:cd:ef`  
- OUI: `52:54:00`

Write down:

- Your full MAC address: 92:e1:0d:6f:d4:91 
- Your OUI: 92:e1:0d

---

## 3. Look Up Your OUI

Use:

https://maclookup.app/

Record:

- Vendor/manufacturer  
- Whether it appears physical or virtual  
- Any notes provided

### Notes About Virtual OUIs
- Virtualization vendors (QEMU, VMware, VirtualBox, Hyper-V, etc.) use reserved MAC ranges.  
- Some lookup tools may show:
  - “No results found”  
  - “IEEE Registration Authority”  
  - Only the OUI block, not the company  

This is normal.

---

## 4. Compare Physical vs Virtual MAC Addresses

Write **4–5 sentences** explaining:

1. Where the MAC address appears on a physical NIC  
2. Where your VM’s MAC address came from  
3. What physical and virtual MACs have in common  
4. What is different  
5. Why a virtual NIC still requires a MAC address  

---

# MAC Address OUI Lookup Activity

Look up the OUIs of seven real-world MAC addresses using:

- https://maclookup.app  
- https://macvendors.com  
- https://standards-oui.ieee.org/oui/oui.txt  

For each MAC address, record:

- Full MAC address  
- OUI  
- Vendor/company  
- Vendor type (physical, virtual, both)  
- Notes

---

## Digital Portfolio Table

| Full MAC Address        | OUI (first 3 pairs) | Vendor / Company Name | Vendor Type (physical, virtual, both) | Notes |
|-------------------------|----------------------|------------------------|----------------------------------------|-------|
| F0:18:98:AA:BB:CC       |                      |                        |                                        |       |
| 3C:5A:B4:11:22:33       |                      |                        |                                        |       |
| 60:45:BD:12:34:56       |                      |                        |                                        |       |
| A4:BA:DB:22:33:44       |                      |                        |                                        |       |
| 04:1A:04:55:66:77       |                      |                        |                                        |       |
| 00:50:56:AA:BB:CC       |                      |                        |                                        |       |
| 52:54:00:12:34:56       |                      |                        |                                        |       |

---

## Reflection (3–4 Sentences)

Address:

- Patterns noticed in vendors  
- Why virtualization vendors need registered OUIs  
- How this activity improved your understanding of Layer 2 addressing  

---

## Upload Evidence to Your Portfolio

Include:

- Screenshot of Terminal showing your MAC address  
- Screenshot of your OUI lookup results  
- Your 4–5 sentence comparison from Part B  
- A 2-sentence summary answering:  
  **“What does my MAC address reveal about the hardware my VM is using?”**

---

# Part C — Understanding MAC Address Structure

Analyze your MAC address in terms of its meaning and its role in the OSI model.

---

## 1. Break Down Your MAC Address

Format:


- **OUI:** `aa:bb:cc`  
- **Device Identifier:** `dd:ee:ff`

---

## 2. Explain the OUI

Write 2–3 sentences explaining:

- What the OUI represents  
- How it connects the NIC to a manufacturer  
- Why OUIs must be globally unique  
- If yours is virtual, why a VM still needs a vendor prefix  

---

## 3. Explain the Device Identifier

Write 2–3 sentences explaining:

- Why each NIC needs a unique device identifier  
- Why no two devices on a LAN can share a MAC address  
- How uniqueness ensures correct frame delivery  

---

## 4. Compare Virtual vs Physical MAC Addresses

Write **4–6 sentences** explaining:

- Where physical NICs store MAC addresses  
- How virtual machines generate or assign MAC addresses  
- Similarities and differences  
- Why Layer 2 functions identically for physical and virtual hardware  

---

## 5. MAC Addresses in the OSI Model

Write 2–3 sentences explaining:

- Which OSI layer uses MAC addresses  
- Why MAC addresses never leave the local network  
- How routers replace MAC addresses when forwarding frames  

---

## Final Upload

Include:

- Explanations from Steps 2–5  
- Screenshot of your MAC address (optional if already uploaded)  
- One-sentence summary:  
  **“Why must every NIC — physical or virtual — have a globally unique MAC address?”**


# Understanding Logical Addressing (IPv4 and IPv6)

## Addressing: Physical and Logical

Yesterday you learned that every device has a physical address (MAC address) that identifies its Network Interface Card (NIC) inside a Local Area Network (LAN). MAC addresses work extremely well for communication within a single network, but they have one major limitation:

**A MAC address cannot help you reach a device outside your local network.**

This brings us to the idea of **logical addressing**, which allows networks across the entire world to communicate.

---

## Why Logical Addressing Exists

Imagine trying to send a letter to someone who lives in another state. A name alone isn't enough — you need a complete mailing address. Networking works the same way.

- **A MAC address** is like someone’s name. It uniquely identifies them inside a local space but is meaningless across long distances.
- **An IP address** is like a full mailing address. It identifies where a device is located in the global network so data can reach it from anywhere.

A MAC address allows communication only within a local network—for example, with a printer, a switch, or your home router.

To communicate across the world, the internet needs a consistent, structured, global addressing system.  
This global system is called **logical addressing**, implemented through **IP (Internet Protocol) addresses**.

Logical addresses allow devices to:

- Be located anywhere on Earth  
- Change networks and still remain reachable  
- Send and receive data across interconnected networks  

This is what enables the internet to function.

---

# IPv4 — The OG Internet Addressing System

IPv4 (Internet Protocol version 4) is the first widely deployed system for global addressing.

## Key Characteristics of IPv4

- **32-bit address**  
  IPv4 uses 32 bits, supporting about 4.3 billion unique addresses.

- **Written in dotted-decimal format**  
  Example:  
  `192.168.1.10`

- **Network portion + Host portion**  
  Some bits identify the network; the rest identify the device on that network.

- **Still widely used**  
  Even though it’s old, IPv4 remains everywhere.

---

## Why IPv4 Has Problems

By the early 2000s, it became clear that **4.3 billion addresses were not enough** for a world full of laptops, smartphones, servers, and IoT devices.

This led to the adoption of IPv6.

---

# IPv6 — The Next Generation of Internet Addressing

IPv6 was created to solve the limitations of IPv4 and support long-term global growth.

## Key Characteristics of IPv6

- **128-bit address**  
  Allows for **3.4 × 10³⁸** addresses — practically unlimited.

- **Written in hexadecimal with colons**  
  Example:  
  `2001:0db8:85a3::8a2e:0370:7334`

- **Designed for future growth**

- **Includes major improvements**
  - Built-in security features  
  - More efficient routing  
  - Better support for mobility  
  - No need for NAT in many cases  

Even though IPv6 is the future, most networks today use both IPv4 and IPv6.

---

# IPv4 vs IPv6 Comparison Table

| Category | IPv4 | IPv6 |
|----------|------|------|
| Bits | 32 | 128 |
| Capacity | ~4.3 billion | Virtually unlimited |
| Notation | Dotted decimal | Hexadecimal with colons |
| Example | 10.0.0.25 | fe80::1f4a:e3ff:fe21:bd10 |
| Reason for IPv6 | Address exhaustion | Long-term global growth |

IPv6 is not a replacement because IPv4 failed — the world simply outgrew IPv4.

---

## Physical Address (MAC Address)

- Built into hardware  
- Never changes (unless spoofed)  
- Used within the local network  
- Operates at **OSI Layer 2 (Data Link Layer)**  
- Identifies the **NIC**  

## Logical Address (IP Address – IPv4 or IPv6)

- Assigned manually or by DHCP  
- Can change depending on the network  
- Used to communicate **across networks**  
- Operates at **OSI Layer 3 (Network Layer)**  
- Identifies the device’s **network location**  

## Why We Need Both

A computer needs:

- A **MAC address** for local communication  
- An **IP address** for global communication  

Together, they form the foundation of modern networking.

---

# Logical Addressing Lab

You already know how to use the Terminal to locate your IPv4 and IPv6 addresses. Today you will analyze what those addresses mean and how they support global communication.

This activity focuses on:

- The role of logical addressing (IPv4 & IPv6)  
- Interpreting your addresses  
- Understanding IPv6 link-local addresses  
- Connecting addressing to global communication  

---

# Part A – Document Your IP Addresses

## Step 1 – Retrieve your IP information

<img width="649" height="326" alt="Screenshot 2025-12-01 at 1 42 00 PM" src="https://github.com/user-attachments/assets/fd154652-959b-4975-81fb-05ac8bb50248" />


## Step 2 – Record your addresses

Find and highlight:

- Your **IPv4 address**  
- Your **IPv6 link-local address** (`fe80::…`)

## Step 3 – Take a clear screenshot

Your screenshot must show:

- The `ip addr show` command  
- Your IPv4 and IPv6 lines  
<img width="646" height="328" alt="Screenshot 2025-12-01 at 1 48 56 PM" src="https://github.com/user-attachments/assets/66056a0b-d5b1-4199-af04-0c68a571d39d" />

---

# Part B – Research: IPv6 Link-Local and the Future of IPv6

## Research Question 1  
### Why does every interface automatically have an IPv6 link-local address?

Write a 4–6 sentence paragraph explaining:

- What an IPv6 link-local address is  
- Why it begins with `fe80::`  
- What types of communication it supports  
- Why it doesn’t need DHCP or external configuration  
- Why every IPv6-enabled device generates one automatically  

An IPv6 link-local address is a special type of address that allows devices to communicate with other devices on the same local network segment. It always begins with fe80:: because that prefix is reserved specifically for link-local communication in the IPv6 standard. These addresses support essential local functions like neighbor discovery, automatic configuration, and communication with routers. They do not need DHCP or external setup because the device can generate the address entirely on its own using built-in rules and part of its interface identifier. Every IPv6-enabled device automatically creates a link-local address so it can immediately communicate on the local network, even if no router or DHCP server is available.

---

## Research Question 2  
### Why is IPv6 important for the future of networking?

Write a 4–6 sentence paragraph explaining:

- Why IPv4 is no longer sufficient  
- How IPv6 solves address exhaustion  
- What new capabilities IPv6 introduces  
- Why networks must support both IPv4 and IPv6 during the transition  

IPv4 is no longer sufficient because the world has far more devices than the ~4.3 billion addresses that IPv4 can provide. IPv6 solves this problem by using 128-bit addresses, giving the internet an almost unlimited supply of unique addresses. Beyond increasing capacity, IPv6 introduces improvements like more efficient routing, built-in security features, and better support for mobile devices. Modern networks must support both IPv4 and IPv6 during the long transition because the global internet still relies heavily on IPv4, and switching everything at once is not realistic. Using both protocols at the same time ensures compatibility while the world gradually moves toward full IPv6 adoption.

---

## IPv4 vs IPv6 Comparison Table 

| **Feature** | **IPv4** | **IPv6** |
|-------------|-----------------------------|------------------------------|
| **Address length** | Uses a 32-bit address, so space is limited. | Uses a 128-bit address, giving it a massively larger range. |
| **Notation** | Written as four decimal numbers separated by dots (example: 192.168.1.10). | Written in hexadecimal and separated by colons (example: 2001:db8::1). |
| **Approximate capacity** | Supports about 4.3 billion unique addresses. | Supports an almost unlimited number of unique addresses. |
| **Example** | 10.0.0.25 | fe80::1f4a:e3ff:fe21:bd10 |
| **Where I see it used** | Common on home networks and older systems. | Found in newer networks and modern devices that support both IPv4 and IPv6. |


---

## Why Logical Addressing Exists

Write a 5–7 sentence paragraph explaining:

- Why we need IP addresses in addition to MAC addresses  
- How IP addresses enable communication beyond the local network  
- How routers use IP addresses  
- An example from your own experience (web browsing, gaming, email, etc.)  

---




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
https://mail.google.com/mail/u/0?ui=2&ik=5f8a137b04&attid=0.1&permmsgid=msg-a:r5267786008811769903&th=19a9d4184703f848&view=att&disp=safe&realattid=19a9d417d9c5b7c0e72&zw

#### Task for Image B
- Draw an arrow to the MAC address label and label it.  
- Record the MAC address exactly as printed:  
  `04:92:22:64:IA:80:4C`  
- Write one sentence explaining what a MAC address does on a local network.

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

---

## 2. Identify the OUI

The first **three pairs** of the MAC address are the **OUI**.

Example:  
- Full MAC: `52:54:00:ab:cd:ef`  
- OUI: `52:54:00`

Write down:

- Your full MAC address  
- Your OUI  

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


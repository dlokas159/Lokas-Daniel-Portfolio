## Initial Reflection Questions (Digital Portfolio)

Write a paragraph responding to:

1. **Which device inside a LAN would be the easiest for an attacker to compromise, and why?**
2. **Does proximity equal safety? How much can a device ‘see’ inside a LAN?**

The easiest device for an attacker to compromise inside a LAN is usually a regular user computer or any device that is not well secured. These devices often trust the network they are connected to and automatically accept information like IP addresses and gateways. If an attacker connects to the same network, they can take advantage of this trust to interfere with traffic or pretend to be a network device. Being physically close to the network does not mean it is safe. Once a device is connected, it can see broadcast traffic and interact with other devices on the LAN. Without protections like VLANs or access controls, devices can see more of the network than they should.

---

#### **Step 3 — Digital Portfolio Entry**

Create a section titled **“LAN Threat Scenario Rotation.”**

Add a table with these columns:

| Scenario Letter | Symptoms (Summary) | Your Hypothesis | Your Justification |
|----------------|--------------------|-----------------|--------------------|
| A | Default gateway does not match the actual router | DHCP misconfiguration | connectivity issues and network behavior changes |
| B | Switch CPU spikes, thousands of MACs appear on one port | MAC flooding attack | multiple MACs show up on one port even though there should be one |
| C | Clients recieve network settings from an unknown DHCP source | Misconfigured Router | unknown DHCP sources and connectivity issues |
| D | New device appears inside the broadcast domain and communicates broadly | Admin Issue | communicates broadly |
| E | A host reaches internal systems it should not access | Security Policy Bypass | Firewalls and other encryptions are not working |


# Digital Portfolio Requirement — Group Activity

After the “Group of Four” discussion, update **“LAN Threat Scenario Rotation”** with a reflection (5–7 sentences) addressing:

1. Which original hypotheses you feel confident about  
2. Which scenario was hardest to interpret  
3. How another pair influenced your thinking  
4. Patterns you noticed across scenarios

The strongest conclusions apply to Scenarios B and C because their symptoms clearly match how switches and DHCP normally function. Scenario D is the most difficult to interpret because the behavior could be caused by either weak network policies or intentional misuse. Group discussion highlights how many LAN threats rely on trust built into local networks. A clear pattern across all scenarios is that most problems originate inside the network rather than from external attackers. Many threats appear similar to normal network activity, making them difficult to detect. This demonstrates the importance of internal security controls on local area networks.

---


## Step 3 — Portfolio Entry

Add a section: **“Task A — LAN Observation”**, including:

1. **Screenshot** showing other hosts (ARP/neighbor/routing).  
2. **Reflection (2–3 sentences):**  
   How could an attacker misuse this information?

![unnamed](https://github.com/user-attachments/assets/e472e628-d58c-4aa4-be4a-91b23b6fe4d3)


This information could help an attacker identify important devices like the default gateway and active hosts on the network. ARP and neighbor tables reveal which IP addresses belong to which MAC addresses, which could be used to impersonate a trusted device or redirect traffic. Routing information also shows where to target if the goal is to intercept or block network access.

---

## Step 3 — Portfolio Entry

Create **“Task B — Evidence-to-Threat Analysis.”**

Add this table:

| Evidence from Your VM                                                   | Possible Threat Enabled | Why? (Your Explanation)                                                                                                                |
| ----------------------------------------------------------------------- | ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Default gateway shown in `ip route show`: [gateway IP]                  | ARP Spoofing            | Knowing the gateway lets an attacker pretend to be the gateway by sending fake ARP replies so traffic gets redirected.                 |
| ARP/neighbor entry: [gateway IP → gateway MAC]                          | ARP Spoofing            | ARP trust can be abused if an attacker changes the IP-to-MAC mapping so devices send traffic to the attacker’s MAC address.            |
| Visible hosts from `arp -a` / `ip neigh`: [list 2–4 IPs]                | Lateral Movement        | Seeing other internal hosts helps an attacker choose targets and attempt access to nearby systems once one device is compromised.      |
| Multiple MACs learned on one port (if observed in scenario/lab context) | MAC Flooding            | Flooding a switch with fake MAC addresses can overload its table and cause it to broadcast traffic, increasing sniffing opportunities. |



## Step 2 — Partner Discussion Questions

1. What does the attacker need to know first?
The attacker needs to know the default gateway IP address and the victim device’s IP address. 
2. Which device(s) would be targeted?
The target is typically a victim workstation and the default gateway/router, since spoofing often places the attacker between them.
3. What would a victim notice (if anything)?
The victim might notice slower internet, random disconnects, security warnings, or no obvious symptoms at all if the attacker forwards traffic normally.
4. Which VM resembles the impersonated device, and why?
The Linux Server VM (VM #2) resembles an infrastructure device perspective because it represents a server/network-side role, while the gateway is also an infrastructure role. The Ubuntu Desktop VM (VM #1) resembles the victim workstation perspective.

## Step 3 — Portfolio Entry

Create: **“Task C — Threat Mini-Simulation.”**

Include:

- Chosen threat  
- Answers to all four questions  
- A 3–4 sentence summary explaining how the threat abuses normal LAN behavior

ARP spoofing works because devices on a LAN trust ARP messages without strong verification. An attacker can send fake ARP replies so the victim thinks the attacker’s MAC address belongs to the gateway’s IP address. Once the ARP table is poisoned, traffic meant for the gateway can be redirected to the attacker. This abuses normal LAN behavior because ARP is designed for fast local communication, not strict identity checking.

---


## Part 1 — Screenshots From Both VMs

Add:

- **One screenshot from VM #1**

It shows active hosts, the default gateway, and IP-to-MAC mappings. This helps an attacker choose targets and potentially impersonate trusted devices using spoofing techniques.
![0](https://github.com/user-attachments/assets/6992e1eb-ccab-4c60-9cf0-8f29d2b72437)


- **One screenshot from VM #2**

It provides network layout details and trusted communication relationships. This can help identify which devices are infrastructure-related and how traffic flows through the LAN.
![0](https://github.com/user-attachments/assets/dac280f8-71cf-426a-bcf5-65b78391b660)


---

## Part 2 — Five Common Internal LAN Threats

Create a section: **“Five Common Internal LAN Threats.”**

For each threat, include:

- **Plain-language explanation**  
- **One sentence describing how it abuses LAN trust**

Threats:

- ARP Spoofing  
- MAC Flooding  
- Rogue DHCP Server  
- Unauthorized Plug-In Device  
- Lateral Movement  

## Five Common Internal LAN Threats

### ARP Spoofing
- **Explanation:** A device pretends to be another by sending false ARP replies.  
- **LAN Trust Abuse:** ARP messages are accepted without identity verification.

### MAC Flooding
- **Explanation:** Fake MAC addresses overload a switch’s table.  
- **LAN Trust Abuse:** Switches trust MAC learning on each port.

### Rogue DHCP Server
- **Explanation:** An unauthorized device hands out IP addresses.  
- **LAN Trust Abuse:** Clients accept DHCP offers automatically.

### Unauthorized Plug-In Device
- **Explanation:** An unknown device connects to the network.  
- **LAN Trust Abuse:** Open ports allow devices to join without authentication.

### Lateral Movement
- **Explanation:** An attacker moves from one internal system to another.  
- **LAN Trust Abuse:** Internal devices often trust each other by default.

---

## Part 3 — Final Reflection

Write 3–4 sentences responding to:

**“Which internal LAN threat do you believe is the most difficult for a network administrator to detect, and why?”**

Reference:

- Your VM evidence  
- Scenario patterns  
- How normal LAN behavior can hide malicious activity

ARP spoofing is one of the hardest internal LAN threats to detect because it looks like normal network traffic. ARP tables change during regular operation, which can hide malicious behavior. Evidence from ARP and neighbor outputs shows how easily mappings can be changed. This demonstrates how normal LAN behavior can mask attacks.


## STEP 1 — Identify Network Information on VM #2 (Linux Server)

You must first determine the target information from VM #2.

On VM #2, open a terminal and run:
bash
ip addr
ip route

![0](https://github.com/user-attachments/assets/cededb04-c6e0-459e-b308-ff6746f802f6)


## STEP 2 — Start ARP Packet Capture on VM #2

On VM #2, start listening for ARP traffic

sudo tcpdump -i <interface> arp

![unnamed](https://github.com/user-attachments/assets/417c5ce9-2aaf-43e4-b71f-34acef37683e)


### Written Analysis (Required)

Write a well-developed paragraph answering the following:

What information does ARP reveal about devices on a LAN?

Why does ARP assume devices are trustworthy?

How does this make ARP vulnerable to spoofing?

Why was Bridged mode required for this lab to work?

Your response should clearly reference evidence from the commands you ran.

ARP reveals IP-to-MAC relationships for devices on a LAN. It assumes devices are trustworthy and does not verify replies. This allows attackers to send fake ARP responses and redirect traffic. Bridged mode was required so both VMs could share the same broadcast domain and exchange ARP packets.


## LAN Attack Path Diagram (Homework)

### Diagram Upload
<img width="1785" height="981" alt="Screenshot 2026-01-15 201024" src="https://github.com/user-attachments/assets/e847ce2c-b478-491a-addc-d9f33f6e2d1a" />



### Explanation

This attack succeeds because devices on a LAN trust ARP messages without verification. The attacker sends a fake ARP reply claiming to be the default gateway, causing the victim to send traffic to the attacker instead of the router. This works because ARP updates are accepted as normal network behavior.

Dynamic ARP Inspection (DAI) would stop this attack by blocking invalid ARP messages that do not match trusted IP-to-MAC bindings. DHCP Snooping helps by identifying legitimate devices, and VLAN segmentation limits how much of the network an attacker can access.


## Enterprise Physical Security Threat Analysis

The following physical vulnerabilities represent serious risks in a pharmaceutical research environment. Each vulnerability is written as a weakness and explains why it is dangerous in this industry.

### 1. Unauthorized Access to Research Laboratories
- **What:** Individuals without proper authorization can enter laboratory spaces.
- **Where:** Research labs and clean rooms.
- **Why Risky:** These areas contain sensitive drug research, biological samples, and proprietary data that must be protected from theft or tampering.

### 2. Inadequate Separation Between Public and Restricted Areas
- **What:** Public office areas are not clearly separated from restricted zones.
- **Where:** Corporate headquarters and research facilities.
- **Why Risky:** Visitors or non-cleared staff could accidentally or intentionally enter secure areas.

### 3. Poor Environmental Controls for Network Equipment
- **What:** Network closets and server rooms lack proper temperature and humidity control.
- **Where:** On-site data center and wiring closets.
- **Why Risky:** Overheating or moisture can cause hardware failures, outages, and data loss.

### 4. Insufficient Surveillance of Critical Spaces
- **What:** Limited camera coverage and monitoring of sensitive areas.
- **Where:** Server rooms, labs, and network closets.
- **Why Risky:** Unauthorized access or sabotage may go undetected.

### 5. Exposed Network Hardware
- **What:** Server racks, switches, and network ports are not fully secured.
- **Where:** Data center and network closets.
- **Why Risky:** Rogue devices could be connected, or critical cables could be unplugged.

### 6. Weak Visitor and Personnel Procedures
- **What:** Visitors are not always escorted and access reviews are inconsistent.
- **Where:** Entire facility.
- **Why Risky:** Human error can bypass both physical and technical security controls.

---

## Physical Security Plan — Pharmaceutical Research Facility

This physical security plan uses a layered defense approach to protect people, data, and infrastructure.

### 1. Environmental Controls
- Climate-controlled data center with temperature and humidity monitoring
- Fire suppression systems designed for IT and laboratory environments
- Air filtration to reduce dust and contaminants

**Protection Provided:**  
These controls prevent equipment damage, system outages, and data loss.

---

### 2. Access Control
- Badge-based access for employees
- Biometric authentication for labs, data centers, and clean rooms
- Mantraps at highly restricted entry points
- Clearly defined security zones (public, restricted, highly restricted)

**Protection Provided:**  
Access controls ensure that only authorized individuals can enter sensitive areas.

---

### 3. Surveillance and Detection
- Security cameras covering entrances, corridors, labs, and server rooms
- Central monitoring and logging systems
- Motion sensors and alarms for after-hours access

**Protection Provided:**  
Monitoring deters unauthorized behavior and allows incidents to be detected and investigated.

---

### 4. Hardware Security
- Locked server racks and cabinets
- Secured network closets
- Disabled or covered unused switch ports
- Properly labeled and managed cabling

**Protection Provided:**  
These controls prevent physical tampering, rogue device connections, and accidental disruptions.

---

### 5. Personnel and Procedures
- Visitor escort requirements
- Regular access reviews and badge audits
- Security awareness training for staff
- Formal procedures for installing or removing equipment

**Protection Provided:**  
Clear procedures reduce human error and ensure consistent enforcement of security controls.

---

## Digital Physical Security Diagram



**Diagram Includes:**
- Facility perimeter
- Entry point
- Public, restricted, and highly restricted zones
- Data center and network closets
- Research labs and clean rooms
- Monitoring and security control room
- Cameras, access control points, locked areas, and environmental protections
- Boundaries showing restricted movement between zones

---

## Risk Justification and Priority Controls

The highest priority physical controls are access control, surveillance, and hardware security. These controls directly reduce the risk of theft, sabotage, data compromise, and regulatory violations by limiting who can physically access critical systems and ensuring that all activity is monitored. In a pharmaceutical research environment, even brief unauthorized access can result in stolen intellectual property, damaged research, or compliance failures.

Physical security also supports technical controls such as network segmentation, access control lists, and monitoring systems. When devices and infrastructure are physically protected, attackers cannot easily bypass logical defenses by plugging in rogue hardware or accessing network ports. Strong physical security ensures that technical controls remain effective and trustworthy across the enterprise.

---

## Conclusion

Physical security is a foundational requirement for network and cybersecurity. Without strong physical controls, technical protections can be bypassed or rendered ineffective. A layered physical security strategy protects people, data, and infrastructure while supporting reliable and secure network operations.


# Physical Security Controls for Network Devices and Physical Spaces

---

## Enterprise Physical Security Threat Analysis

The following physical vulnerabilities represent serious risks in a pharmaceutical research environment. Each vulnerability is written as a weakness and explains why it is dangerous in this industry.

### 1. Unauthorized Access to Research Laboratories
- **What:** Individuals without proper authorization can enter laboratory spaces.
- **Where:** Research labs and clean rooms.
- **Why Risky:** These areas contain sensitive drug research, biological samples, and proprietary data that must be protected from theft or tampering.

### 2. Inadequate Separation Between Public and Restricted Areas
- **What:** Public office areas are not clearly separated from restricted zones.
- **Where:** Corporate headquarters and research facilities.
- **Why Risky:** Visitors or non-cleared staff could accidentally or intentionally enter secure areas.

### 3. Poor Environmental Controls for Network Equipment
- **What:** Network closets and server rooms lack proper temperature and humidity control.
- **Where:** On-site data center and wiring closets.
- **Why Risky:** Overheating or moisture can cause hardware failures, outages, and data loss.

### 4. Insufficient Surveillance of Critical Spaces
- **What:** Limited camera coverage and monitoring of sensitive areas.
- **Where:** Server rooms, labs, and network closets.
- **Why Risky:** Unauthorized access or sabotage may go undetected.

### 5. Exposed Network Hardware
- **What:** Server racks, switches, and network ports are not fully secured.
- **Where:** Data center and network closets.
- **Why Risky:** Rogue devices could be connected, or critical cables could be unplugged.

### 6. Weak Visitor and Personnel Procedures
- **What:** Visitors are not always escorted and access reviews are inconsistent.
- **Where:** Entire facility.
- **Why Risky:** Human error can bypass both physical and technical security controls.

---

## Physical Security Plan — Pharmaceutical Research Facility

This physical security plan uses a layered defense approach to protect people, data, and infrastructure.

### 1. Environmental Controls
- Climate-controlled data center with temperature and humidity monitoring
- Fire suppression systems designed for IT and laboratory environments
- Air filtration to reduce dust and contaminants

**Protection Provided:**  
These controls prevent equipment damage, system outages, and data loss.

---

### 2. Access Control
- Badge-based access for employees
- Biometric authentication for labs, data centers, and clean rooms
- Mantraps at highly restricted entry points
- Clearly defined security zones (public, restricted, highly restricted)

**Protection Provided:**  
Access controls ensure that only authorized individuals can enter sensitive areas.

---

### 3. Surveillance and Detection
- Security cameras covering entrances, corridors, labs, and server rooms
- Central monitoring and logging systems
- Motion sensors and alarms for after-hours access

**Protection Provided:**  
Monitoring deters unauthorized behavior and allows incidents to be detected and investigated.

---

### 4. Hardware Security
- Locked server racks and cabinets
- Secured network closets
- Disabled or covered unused switch ports
- Properly labeled and managed cabling

**Protection Provided:**  
These controls prevent physical tampering, rogue device connections, and accidental disruptions.

---

### 5. Personnel and Procedures
- Visitor escort requirements
- Regular access reviews and badge audits
- Security awareness training for staff
- Formal procedures for installing or removing equipment

**Protection Provided:**  
Clear procedures reduce human error and ensure consistent enforcement of security controls.

---

## Digital Physical Security Diagram

<img width="964" height="582" alt="Screenshot 2026-01-16 at 10 40 33 AM" src="https://github.com/user-attachments/assets/29b6fe72-a841-4416-b9c9-6b371dbce043" />

This diagram demonstrates how physical security supports network and cybersecurity by controlling access, monitoring activity, and protecting critical infrastructure. Strong physical controls ensure that technical security measures remain effective and trustworthy in a pharmaceutical research environment.

---

## Risk Justification and Priority Controls

The highest priority physical controls are access control, surveillance, and hardware security. These controls directly reduce the risk of theft, sabotage, data compromise, and regulatory violations by limiting who can physically access critical systems and ensuring that all activity is monitored. In a pharmaceutical research environment, even brief unauthorized access can result in stolen intellectual property, damaged research, or compliance failures.

Physical security also supports technical controls such as network segmentation, access control lists, and monitoring systems. When devices and infrastructure are physically protected, attackers cannot easily bypass logical defenses by plugging in rogue hardware or accessing network ports. Strong physical security ensures that technical controls remain effective and trustworthy across the enterprise.

---

## Conclusion

Physical security is a foundational requirement for network and cybersecurity. Without strong physical controls, technical protections can be bypassed or rendered ineffective. A layered physical security strategy protects people, data, and infrastructure while supporting reliable and secure network operations.

## Security Controls to Mitigate Vulnerabilities in a Switched LAN Report

[Report](https://docs.google.com/document/d/1M4oCt8gIXYMBSntO-kc73rdrwpg44H4et1QLc6AoTFk/edit?usp=sharing)


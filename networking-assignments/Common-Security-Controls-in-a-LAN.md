# 1. Planning & Conceptual Understanding  

### Initial Reflection — LAN Trust and Exposure

The easiest device for an attacker to compromise inside a LAN is typically a standard user workstation or other lightly secured endpoint. These devices inherently trust the local network and automatically accept information such as IP addresses, default gateways, and ARP responses. If an attacker connects to the same LAN, they can exploit this trust to impersonate network infrastructure or intercept traffic. Physical proximity alone does not imply safety; once connected, a device can observe broadcast traffic and interact with other hosts. Without segmentation mechanisms such as VLANs or access controls, devices can see far more of the network than intended.

This reflects a core weakness of flat LANs: internal trust is assumed by default. Technical security controls protect traffic logically, while physical security controls prevent unauthorized devices from ever joining the network. Both are required to reduce internal risk.

---

### LAN Threat Scenario Rotation — Hypothesis Development

| Scenario | Symptoms (Summary) | Hypothesis | Justification |
|--------|------------------|-----------|---------------|
| A | Default gateway mismatch | DHCP misconfiguration | Incorrect gateway settings cause routing and connectivity issues |
| B | Switch CPU spike; many MACs on one port | MAC flooding attack | MAC table overflow forces broadcast behavior |
| C | Clients receive IPs from unknown source | Rogue or misconfigured DHCP | DHCP clients trust the first offer received |
| D | New device communicates broadly | Unauthorized device or admin error | Excessive broadcast visibility indicates weak access control |
| E | Host accesses restricted systems | Security policy bypass | Internal trust and lack of segmentation enable access |

---

### Group Reflection 

The strongest conclusions apply to Scenarios B and C because their symptoms closely match known switch and DHCP behaviors. Scenario D was the most difficult to interpret because similar behavior could result from misconfiguration or malicious intent. Input from another group emphasized how LAN threats often exploit trust rather than technical flaws. A clear pattern across scenarios is that most attacks originate internally. Many threats resemble normal traffic, making detection difficult. This reinforces the need for internal security controls and monitoring.

---

# 2. Technical & Security Development  

### Task A — LAN Observation

**Evidence:**  
Screenshot showing ARP/neighbor and routing information  
![LAN Observation](https://github.com/user-attachments/assets/e472e628-d58c-4aa4-be4a-91b23b6fe4d3)

**Reflection:**  
ARP and routing data reveal active hosts, IP-to-MAC mappings, and the default gateway. This information could be misused by an attacker to impersonate trusted devices or redirect traffic. Identifying infrastructure devices makes interception and disruption easier.

---

### Task B — Evidence-to-Threat Mapping

| Evidence from VM | Possible Threat | Explanation |
|-----------------|----------------|-------------|
| Default gateway from `ip route show` | ARP spoofing | Enables impersonation of the gateway |
| ARP entry (IP → MAC) | ARP spoofing | Trust in ARP allows poisoning |
| Visible hosts from `arp -a` | Lateral movement | Reveals internal targets |
| Multiple MACs on one port | MAC flooding | Forces switch to broadcast traffic |

---

### Task C — Threat Mini-Simulation (ARP Spoofing)

**Attacker Needs to Know:**  
- Default gateway IP  
- Victim IP address  

**Targets:**  
- Victim workstation  
- Default gateway/router  

**Victim Symptoms:**  
- Slower connectivity  
- Possible warnings  
- Often no visible signs  

**Impersonated Device Perspective:**  
- Linux Server VM represents infrastructure  
- Ubuntu Desktop VM represents victim endpoint  

**Summary:**  
ARP spoofing exploits the lack of authentication in ARP. An attacker sends forged replies mapping the gateway IP to their own MAC address. Once ARP tables are poisoned, traffic is redirected through the attacker. This attack abuses normal LAN behavior and blends into legitimate traffic.

---

# 3. Testing, Observation & Risk Evaluation  

### VM Evidence

**VM #1 — Workstation View**  
![VM1](https://github.com/user-attachments/assets/6992e1eb-ccab-4c60-9cf0-8f29d2b72437)

**VM #2 — Infrastructure View**  
![VM2](https://github.com/user-attachments/assets/dac280f8-71cf-426a-bcf5-65b78391b660)

---

### ARP Testing and Packet Observation

**Commands Used:**  
'''bash
ip addr
ip route
sudo tcpdump -i <interface> arp

**Evidence:**

![0](https://github.com/user-attachments/assets/cededb04-c6e0-459e-b308-ff6746f802f6)

![unnamed](https://github.com/user-attachments/assets/417c5ce9-2aaf-43e4-b71f-34acef37683e)

**Analysis:**
ARP reveals IP-to-MAC relationships for devices on a LAN and assumes all responses are trustworthy. Because ARP does not verify identity, attackers can send forged replies to poison ARP tables. Bridged mode was required so both VMs shared the same broadcast domain, allowing ARP traffic to be observed and manipulated.

**Risk Evaluation Reflection**
ARP spoofing is one of the most difficult internal LAN threats to detect because it closely resembles normal traffic. ARP tables change frequently during standard operation, masking malicious behavior. Evidence from ARP and neighbor outputs shows how easily mappings can be altered. Normal LAN behavior can therefore hide active attacks.

# 4. Professional Integration & Portfolio Quality

### Internal LAN Threat Catalog
ARP Spoofing: Impersonates devices using fake ARP replies; abuses unauthenticated ARP trust.
MAC Flooding: Overloads switch MAC tables; exploits automatic MAC learning.
Rogue DHCP: Issues unauthorized IP leases; clients trust DHCP offers.
Unauthorized Plug-In Device: Unknown device joins network; open ports allow access.
Lateral Movement: Attacker spreads internally; internal trust enables access.

---

### LAN Attack Path Diagram
<img width="1785" height="981" alt="Screenshot 2026-01-15 201024" src="https://github.com/user-attachments/assets/e847ce2c-b478-491a-addc-d9f33f6e2d1a" />

**Explanation:**
The attacker impersonates the gateway using ARP spoofing, redirecting traffic. Controls such as Dynamic ARP Inspection, DHCP Snooping, and VLAN segmentation would prevent this attack.

---

### Physical Security Integration — Pharmaceutical Research Facility
Key risks include unauthorized lab access, weak zone separation, poor environmental controls, limited surveillance, exposed hardware, and inconsistent visitor procedures. These vulnerabilities allow attackers to bypass technical defenses by gaining physical access.

### Physical Security Plan:

Environmental controls (climate, fire suppression)

Access control (badges, biometrics, mantraps)

Surveillance (cameras, monitoring)

Hardware security (locked racks, disabled ports)

Personnel procedures (escorts, audits, training)

<img width="964" height="582" alt="Screenshot 2026-01-16 at 10 40 33 AM" src="https://github.com/user-attachments/assets/29b6fe72-a841-4416-b9c9-6b371dbce043" />

Strong physical security ensures technical controls remain effective and trustworthy.

---

### Embedded Professional Artifact
Switched LAN Security Assessment Report:
[Report](https://docs.google.com/document/d/1M4oCt8gIXYMBSntO-kc73rdrwpg44H4et1QLc6AoTFk/edit?usp=sharing)

### Conclusion
This portfolio demonstrates a complete understanding of internal LAN risk, supported by VM evidence, threat analysis, and physical security integration. By connecting observation, testing, and control selection, this assessment shows how layered defenses reduce both technical and physical attack paths.









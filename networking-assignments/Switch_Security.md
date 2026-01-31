
# Switch Security Portfolio

---

## 1. Planning & Conceptual Understanding  
(Evidence of reasoning about LAN security before formal controls are applied)

### Initial Security Thinking

Within a Local Area Network, the device most susceptible to compromise is a typical end-user workstation, such as a student or employee laptop. These devices frequently connect and disconnect, execute diverse software, and are implicitly trusted once attached to a switch port. Being inside the network increases risk rather than reducing it, because internal traffic is commonly assumed to be legitimate and is less strictly monitored than external traffic. A normal device inside a switched LAN can still observe meaningful information by default, including the default gateway, neighboring devices, and IP-to-MAC relationships. This visibility creates attacker opportunity by enabling internal reconnaissance and positioning without requiring authentication or elevated privileges, demonstrating why switched LANs are vulnerable even before formal security controls are applied.

---

## 2. Threat Scenario Analysis & Reasoning  

![IMG_2048 (1)](https://github.com/user-attachments/assets/2c07f089-247f-4a3d-a851-57a44fc36c20)
![IMG_2049 (1)](https://github.com/user-attachments/assets/f5c40ada-64e5-4e74-913b-39f82863afba)

| Scenario | Symptoms (Summary) | Hypothesis | Justification |
|--------|--------------------|------------|---------------|
| **Scenario A** | Multiple devices lose internet access while remaining connected; default gateway differs from expected | Incorrect gateway information is being distributed internally | Many devices are affected simultaneously, IP addresses remain valid, and no official network changes occurred, indicating internal misdirection rather than external outage |
| **Scenario B** | Switch CPU usage spikes; hundreds of MAC addresses learned on one port | One device is overwhelming the switch with multiple identities | A single port learning many MAC addresses rapidly stresses switch resources, and disconnecting that port stabilizes performance |
| **Scenario C** | Devices receive IP addresses quickly but are placed on incorrect subnets or DNS servers | Conflicting IP configuration information exists inside the LAN | Fast assignment, inconsistent DNS and gateway values, and a functioning official DHCP server suggest multiple configuration sources |
| **Scenario D** | Unknown device appears and communicates with multiple hosts from a public wall jack | An unauthorized device has gained internal LAN access | The device is undocumented, appears suddenly during normal hours, and originates from loosely controlled physical access |
| **Scenario E** | A student workstation communicates with restricted internal systems without alerts | Excessive internal trust due to lack of segmentation | Communication remains internal, devices share the same switch, and the network is not segmented into VLANs |

---

## 3. VM Evidence Collection & Interpretation  

### VM Evidence

Ubuntu virtual machine output demonstrates that a standard device can observe the default gateway’s IP and MAC address using `arp -a`, as well as neighboring devices and router presence using `ip neigh`. This information is visible without authentication or administrative privileges.

<img width="1227" height="162" alt="Screenshot 2026-01-30 202744" src="https://github.com/user-attachments/assets/c096c656-152d-44c7-ae31-1be7817628bd" />

### Interpretation

This information is valuable to an attacker because it enables internal network mapping and identification of infrastructure devices. Knowledge of gateway addresses and neighbor relationships can be leveraged to influence trusted internal communication. The evidence demonstrates that meaningful reconnaissance is possible inside a switched LAN without triggering alerts.

### Evidence → Vulnerability → Control Mapping

| VM Evidence | Vulnerability | Control | Why This Control Mitigates Risk |
|-----------|---------------|---------|--------------------------------|
| Gateway MAC visible in ARP table | Gateway impersonation | DHCP Snooping | DHCP Snooping mitigates risk by restricting which devices can provide network configuration |
| Neighbor discovery reveals router presence | Internal reconnaissance | VLAN Segmentation | VLANs mitigate risk by limiting broadcast visibility between device groups |
| Large number of MACs learned on one port | Switch resource exhaustion | Port Security | Port security mitigates risk by limiting MAC addresses per physical port |

---

## 4. Reflection, Synthesis & Professional Quality  

### Switch Security Controls — Visual Observations

#### Flat Network (No Controls)

<img width="535" height="393" alt="Screenshot 2026-01-16 at 9 58 54 AM" src="https://github.com/user-attachments/assets/2c0c4c96-209b-4467-a5c3-462a7b8ec3ef" />

A flat switched network allows unrestricted communication between all connected devices and assumes universal trust. This design increases internal risk by allowing any compromised device to interact with other hosts.

#### VLAN Segmentation

<img width="727" height="513" alt="Screenshot 2026-01-16 at 10 03 30 AM" src="https://github.com/user-attachments/assets/f33865cc-0aa6-40d1-9240-c8c4c6d48ffa" />

VLAN segmentation reduces broadcast visibility and limits unnecessary communication. However, VLANs alone do not fully mitigate internal risk because routing or misconfiguration can still allow unwanted access.

#### Port Security

<img width="317" height="759" alt="Screenshot 2026-01-16 at 10 20 18 AM" src="https://github.com/user-attachments/assets/d77d5f50-775f-4b4a-b3d4-a5df3b23e48b" />

Port security mitigates unauthorized physical access by controlling what devices can connect to switch ports, but it does not address threats originating from already authorized devices.

#### DHCP Snooping, DAI, and ACLs (Conceptual)

These controls enforce trust boundaries by validating network configuration and limiting internal communication paths.

---

### Secure VLAN-Based LAN Design

<img width="1767" height="995" alt="Screenshot 2026-01-30 203209" src="https://github.com/user-attachments/assets/7b0e67cc-34d2-4342-9016-4b9ac3f0f2c6" />


**VLAN Structure**
- VLAN 10 — Students  
- VLAN 20 — Teachers  
- VLAN 30 — Administration  
- VLAN 40 — Servers  

**Communication Rules**
- Students → Servers: Restricted  
- Students → Teachers: Restricted  
- Students → Administration: Denied  
- Teachers → Servers: Allowed  
- Administration → Servers: Allowed  

Students represent the least trusted VLAN, while Servers and Administration require the most protection. The switch should enforce the strictest controls at access ports and inter-VLAN boundaries.

### Control Layering Justification

VLANs alone do not fully secure the network because they provide logical separation without validating traffic sources. DHCP Snooping is necessary to mitigate unauthorized devices distributing network configuration. Dynamic ARP Inspection depends on DHCP Snooping to validate IP-MAC bindings. Access Control Lists remain necessary to mitigate unauthorized communication even after segmentation.

### Final Reflection

Scenario C is the most realistic because devices continue to function at a basic level while receiving incorrect configuration, making the issue difficult to diagnose. The analysis demonstrates that a normal device can observe substantial internal network information by default, reinforcing that switched LANs rely heavily on implicit trust. The hardest internal threat to detect is a trusted device quietly observing or influencing traffic, as switches inherently treat internal communication as legitimate unless explicitly restricted.

# Common Security Controls in a LAN

In the previous lesson, you explored how Ubuntu configures its network interfaces behind the scenes and practiced assigning and verifying a static IP address using Netplan. That work gave you a foundation in how devices identify themselves on a network and how addressing affects communication. In this new lesson series, we are shifting from how devices are assigned addresses to how those devices—and the network they operate on—are protected from threats inside a LAN.

Just like the last assignment, you will learn through hands-on investigation, guided discovery, and independent practice using your Ubuntu and Linux VMs. There will be no traditional lectures—instead, you will uncover how LAN attacks work by examining your own system outputs, analyzing real network behaviors, and collaboratively determining how different security controls prevent misuse.

Across the next several class periods, you will:

- Identify common internal LAN threats such as ARP spoofing, MAC flooding, rogue DHCP servers, unauthorized plug-in devices, and lateral movement.
- Analyze technical, administrative, and physical security controls used in modern networks.
- Practice a structured **“Threat → Control”** analysis to justify security decisions.
- Use command-line tools in your VMs to observe reconnaissance behavior and determine how VLAN segmentation, port security, DHCP snooping, and 802.1X limit attackers.
- Consider how physical access influences the security of network devices, wiring closets, and switches.

---

## Initial Reflection Questions (Digital Portfolio)

Write a paragraph responding to:

1. **Which device inside a LAN would be the easiest for an attacker to compromise, and why?**
2. **Does proximity equal safety? How much can a device ‘see’ inside a LAN?**

---

# Threat Discovery Rotation Using Cards or Digital Tiles

Today you will work with a partner to investigate how internal LAN threats reveal themselves through symptoms observed on a network. Each scenario describes a real issue a network administrator might notice, but none of them give you the threat name.

Your job: analyze clues, draw conclusions, and support your reasoning with evidence.

> **Read this entire document before starting.**

---

## Rotation Overview

You and your partner will rotate through **five scenarios**, each with:

- Observed symptoms
- Guiding questions
- Space for notes and reasoning

### Steps for Each Scenario

#### **Step 1 — Read**
Read the symptoms carefully. Identify patterns.

#### **Step 2 — Discuss (with your partner)**

- What do you think is happening?
- Why? Which symptoms support your idea?

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


Fill in all columns for each scenario.

### Important Notes

- Correct threat names will be revealed later.
- Focus on reasoning, not accuracy.
- Use your knowledge of ARP tables, DHCP, MAC learning, routing, etc.

---

## Group Comparison Discussion

After completing all scenarios, meet with another pair.

Discuss the following scenarios:

- **Scenario A:** A device suddenly receives the wrong gateway.  
- **Scenario B:** Switch CPU spikes; many MAC addresses appear on one port.  
- **Scenario C:** Clients receive IPs from an unexpected source.  
- **Scenario D:** An unknown device appears inside the broadcast domain.  
- **Scenario E:** A host reaches internal hosts it should never reach.

### Compare:

- What threat each scenario might represent  
- Which symptoms led you to your conclusion  
- Differences in reasoning  

### Guiding Questions

- What patterns did I notice?
- Misconfiguration or attack?
- What trust assumptions are being exploited?

---

# Digital Portfolio Requirement — Group Activity

After the “Group of Four” discussion, update **“LAN Threat Scenario Rotation”** with a reflection (5–7 sentences) addressing:

1. Which original hypotheses you feel confident about  
2. Which scenario was hardest to interpret  
3. How another pair influenced your thinking  
4. Patterns you noticed across scenarios  

---

# VM-Based Threat Evidence Hunt

You will now gather **real LAN evidence** using both VMs.

## VMs Used

- **VM #1 — Ubuntu Desktop:** typical workstation perspective  
- **VM #2 — Linux Server VM:** infrastructure/server perspective  

---

# Task A — Observe How Devices Learn About the LAN

## Step 1 — Commands to Run (Ubuntu VM)

Run and screenshot:
ip addr show
arp -a
ip neigh
ip route show


## Step 2 — Identify

- Your subnet  
- Your default gateway  
- Visible hosts  
- ARP / neighbor table entries  
- Patterns about how devices learn about other hosts  

## Step 3 — Portfolio Entry

Add a section: **“Task A — LAN Observation”**, including:

1. **Screenshot** showing other hosts (ARP/neighbor/routing).  
2. **Reflection (2–3 sentences):**  
   How could an attacker misuse this information?

---

# Task B — Evidence-to-Threat Analysis

Threat list:

- ARP Spoofing  
- MAC Flooding  
- Rogue DHCP Server  
- Unauthorized Plug-In Device  
- Lateral Movement  

## Step 2 — Choose Two Pieces of Evidence

Examples:

- ARP entries  
- Gateway identity  
- Neighbor table info  
- Visible hosts  
- Routing info  

## Step 3 — Portfolio Entry

Create **“Task B — Evidence-to-Threat Analysis.”**

Add this table:

| Evidence from Your VM | Possible Threat Enabled | Why? (Your Explanation) |
|------------------------|-------------------------|--------------------------|

Guiding questions:

- What could an attacker change here?  
- What trust does the LAN rely on?  

---

# Task C — Mini-Simulation Without Tools

Choose one threat:

- ARP Spoofing  
- MAC Flooding  
- Rogue DHCP Server  
- Unauthorized Plug-In Device  
- Lateral Movement  

## Step 2 — Partner Discussion Questions

1. What does the attacker need to know first?  
2. Which device(s) would be targeted?  
3. What would a victim notice (if anything)?  
4. Which VM resembles the impersonated device, and why?

## Step 3 — Portfolio Entry

Create: **“Task C — Threat Mini-Simulation.”**

Include:

- Chosen threat  
- Answers to all four questions  
- A 3–4 sentence summary explaining how the threat abuses normal LAN behavior  

## Step 4 — Pair Discussion

Share key reasoning and compare similarities/differences.

---

# Portfolio Wrap-Up — Homework

To conclude, add the following to your portfolio.

---

## Part 1 — Screenshots From Both VMs

Add:

- **One screenshot from VM #1**
- **One screenshot from VM #2**

Each screenshot must show information an attacker could exploit (ARP, routing, MAC/IP mappings, visible hosts, etc.).

Under each screenshot, write:

**Why would this information be valuable to an attacker?**

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

---

## Part 3 — Final Reflection

Write 3–4 sentences responding to:

**“Which internal LAN threat do you believe is the most difficult for a network administrator to detect, and why?”**

Reference:

- Your VM evidence  
- Scenario patterns  
- How normal LAN behavior can hide malicious activity  

# Hands-On Lab — Observing ARP Requests and Replies (Bridged Mode)

## Required Network Configuration (DO NOT SKIP)

- **VM #1 (Ubuntu Desktop):** Bridged  
- **VM #2 (Linux Server):** Bridged  

Both VMs must be bridged to the **same physical network adapter**.  
If the VMs are not bridged, ARP replies may not occur.

---

## STEP 1 — Identify Network Information on VM #2 (Linux Server)

You must first determine the target information from VM #2.

On VM #2, open a terminal and run:
bash
ip addr
ip route
Record the following from VM #2:

The interface name that has an IPv4 address

Examples: enp0s1, ens33, eth0

The IPv4 address of VM #2

The default gateway

You will use VM #2’s IP address as the ARP target.

## STEP 2 — Start ARP Packet Capture on VM #2

On VM #2, start listening for ARP traffic

sudo tcpdump -i <interface> arp

sudo tcpdump -i enp0s1 arp
Important Rules (READ CAREFULLY)

Replace <interface> with your actual interface name

Do NOT include IP addresses in this command

arp is the only filter you should use

If the command is correct, you will see:
listening on enp0s1, link-type EN10MB (Ethernet)

## STEP 3 — Generate ARP Requests from VM #1 (Ubuntu Desktop)

Switch to VM #1.

Run the following command, targeting the IP address of VM #2:
sudo arping -c 5 -I <interface> <VM2-IP-address>
Example: 
sudo arping -c 5 -I ens33 172.16.110.132

What This Does

VM #1 broadcasts ARP requests asking:
“Who has <VM #2 IP>?”

VM #2 responds with its MAC address

What You SHOULD See
On VM #1 (arping)

ARP request messages

ARP reply messages

MAC address of VM #2

Final statistics showing packets transmitted and received

On VM #2 (tcpdump)

ARP requests arriving from VM #1

ARP replies sent back to VM #1

IP-to-MAC associations displayed

Typical output may look like:

ARP, Request who-has 172.16.110.132 tell 172.16.110.101
ARP, Reply 172.16.110.132 is-at aa:bb:cc:dd:ee:ff

If You See an Error Message

Error:

tcpdump: can't parse filter expression: syntax error


Cause:

You included an IP address in the tcpdump command

You typed placeholder brackets < >

Fix:

Use only:

sudo tcpdump -i <interface> arp

What You Must DOCUMENT (Digital Portfolio)

Include screenshots showing:

ip addr and ip route on VM #2

arping output on VM #1

tcpdump output on VM #2

Written Analysis (Required)

Write a well-developed paragraph answering the following:

What information does ARP reveal about devices on a LAN?

Why does ARP assume devices are trustworthy?

How does this make ARP vulnerable to spoofing?

Why was Bridged mode required for this lab to work?

Your response should clearly reference evidence from the commands you ran.

In-Class “Mini-Project” — Visualizing an Internal LAN Attack

You will create a clean, neatly constructed diagram illustrating how an internal LAN attack can occur when no security controls are in place. This assignment helps visualize the flow of information during an attack and demonstrates your understanding of how LAN vulnerabilities are exploited.

You may complete your diagram digitally (using a diagram-making site) or by hand (uploading a clear photo or screenshot). If drawn by hand, it must be neat, labeled, and easy to read.

Approved Diagram Tools (Choose One)

Google Drawings

Lucidchart

Canva

Figma

Diagrams.net (formerly draw.io)

Microsoft PowerPoint or Google Slides

Your final diagram must be exported as a screenshot and uploaded to your digital portfolio.

What Your Diagram Must Include
1. Devices Involved

VM #1 (Workstation)

VM #2 (Server-like device)

Switch

Default gateway or router

2. One Internal LAN Threat (Choose One)

ARP Spoofing

MAC Flooding

Rogue DHCP Server

Unauthorized Plug-In Device

Lateral Movement

3. Sequence of Events

Use arrows or numbered steps (3–5 steps minimum) to show:

What the attacker sends

How the switch responds

How victim devices are affected

Where the LAN’s trust assumptions fail

4. Annotations

Label each major component

Add brief, clear explanations

The diagram should make sense to someone who did not complete the lab

Digital Portfolio Requirements

Create a section titled “LAN Attack Path Diagram (Homework)” and include:

Your completed diagram
Upload the image, PDF, or photo.

A thorough explanation addressing:

Why this attack succeeds when no internal security controls are present

Which security control introduced in today’s reading would stop this attack

How that control prevents the attack from progressing

Your explanation should connect directly to concepts from today’s reading:

Port Security

VLAN Segmentation

DHCP Snooping

Dynamic ARP Inspection (DAI)

Access Control Lists (ACLs)

Expectations

The diagram must be:

Neatly organized

Clearly labeled

Visually understandable

Fully uploaded to your digital portfolio


If you want, I can also:
- Strip the horizontal rules (`---`) entirely
- Reformat headings to match a specific LMS (Canvas / GitHub / Obsidian)
- Add a **title block** with course name, lab number, and student info placeholders

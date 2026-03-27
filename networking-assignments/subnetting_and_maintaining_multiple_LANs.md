# Design and Planning
## Subnet and IP Challenges
<img width="749" height="196" alt="Screenshot 2026-03-24 at 2 35 30 PM" src="https://github.com/user-attachments/assets/709da92d-fbf7-4be4-adab-0411279501bd" />

The first number should be the same. For example 192.50.40.111 and 192.35.36.120 

<img width="751" height="212" alt="Screenshot 2026-03-24 at 2 35 39 PM" src="https://github.com/user-attachments/assets/a56e9bbf-e6f7-4c89-8538-1e2656b55bce" />

The first two set of numbers must be the same. For example 192.50.40.111 and 192.50.36.120

<img width="757" height="182" alt="Screenshot 2026-03-24 at 2 35 51 PM" src="https://github.com/user-attachments/assets/e60adae8-8e80-4525-a055-e0a82c3d5f56" />

The first three set of numbers must be the same. Also last number must be 0-255. For example 192.50.40.111 and 192.50.40.120

<img width="714" height="102" alt="Screenshot 2026-03-24 at 2 41 06 PM" src="https://github.com/user-attachments/assets/6e0ac902-dd98-44a4-b8a5-f52a09797b50" />

They all start with strings of 1s in binary. 

<img width="703" height="131" alt="Screenshot 2026-03-24 at 2 41 36 PM" src="https://github.com/user-attachments/assets/9250f48d-b969-4f69-95eb-eeb5fa2b6d1a" />

Their binary form is such that there is an uninterrupted string of 1s only at the beginning of the string. Ex. 255.255.192.0



# Technical Development
## Assignment 1: 
### Part 1: Build the Network
<img width="572" height="304" alt="Screenshot 2026-03-26 at 8 25 23 AM" src="https://github.com/user-attachments/assets/24c96d31-e5cb-47ed-8c75-c37b9e440be2" />

### Part 2: Investigate Communication
ping 192.168.1.25 (succeeded)
<img width="291" height="178" alt="Screenshot 2026-03-26 at 8 26 01 AM" src="https://github.com/user-attachments/assets/9d5b2561-0482-40c5-90af-49a3b4903dd2" />

ping 192.168.2.10 (failed)
<img width="245" height="62" alt="Screenshot 2026-03-26 at 8 26 48 AM" src="https://github.com/user-attachments/assets/698fb7ae-a898-4108-8a04-d0108965e409" />

Record Observations
• Which pings succeed?
• Which fail?
Key Question
What determines whether the ping works?

### Part 3: Modify and Test Again
ping 192.168.2.10 (failed)
<img width="293" height="143" alt="Screenshot 2026-03-26 at 8 28 52 AM" src="https://github.com/user-attachments/assets/bff3b764-064b-4835-9716-04fb36363519" />

Analyze
• Did anything change?
• Why or why not?

### Scenario A
Change all subnet masks to:
255.0.0.0
Test communication again.

ping 192.168.2.10 (succeeded)
<img width="282" height="154" alt="Screenshot 2026-03-26 at 8 30 41 AM" src="https://github.com/user-attachments/assets/50f65fc5-61ec-47b4-ae40-f5d0ff175871" />

### Scenario B
Set:
• PC0 → 172.16.1.10 /
255.255.0.0
• PC1 → 172.16.2.20 /
255.255.0.0

ping 192.168.2.10 (failed)
<img width="299" height="136" alt="Screenshot 2026-03-26 at 8 33 03 AM" src="https://github.com/user-attachments/assets/5589c920-5d54-4f67-8555-d24fcb70310b" />
Are they on the same
network?

### Scenario C
Create:
• Two PCs that look
“similar” but are NOT
on the same network
<img width="347" height="285" alt="Screenshot 2026-03-26 at 8 35 05 AM" src="https://github.com/user-attachments/assets/12f98653-8369-4778-8a6e-f3e7fcc4095e" />

• Two PCs that look
“different” but ARE
on the same network
<img width="351" height="294" alt="Screenshot 2026-03-26 at 8 36 46 AM" src="https://github.com/user-attachments/assets/5ad3944f-7c72-4234-b9be-2a8a418f8fd8" />

## Assignment 2: 
### Scenario C: Small Business Workspace
### Part 1: Device Exploration
<img width="725" height="401" alt="Screenshot 2026-03-27 at 9 14 59 AM" src="https://github.com/user-attachments/assets/f6dfabb9-9df6-4098-9077-c12bd7ac0bd5" />

Take a screenshot (and explain it) showing:
• All devices placed
• All devices labeled
• Clean, organized layout

### Part 2: Design Decisions & Part 3: Final Network Layout
<img width="680" height="372" alt="Screenshot 2026-03-27 at 9 24 25 AM" src="https://github.com/user-attachments/assets/c8821202-0ec3-4c2f-a3bf-13d247a912ce" />

explain the final layout in a paragraph



# Testing and Evaluation


# Reflection and Analysis
## Assignment 1 Reflection
2. Written Explanation Write your response in one paragraph that answers all of the
following. Provide screenshots if they can help support your response.
A: Explain how a device determines whether another device is on the same network.
B: Describe a situation where two IP addresses look similar but are NOT on the same network.
C: Describe a situation where two IP addresses look different but ARE on the same network.
D Why is a router required when devices are on different networks?

## Assignment 2 Reflection: 
Write at least one well-developed paragraph that explains your design decisions based on
your assigned scenario.
Your paragraph must include:
• Why you selected the specific devices in your network
• Why certain parts of your network are wired and others are wireless
• Whether you chose a peer-to-peer or client-server model, and why


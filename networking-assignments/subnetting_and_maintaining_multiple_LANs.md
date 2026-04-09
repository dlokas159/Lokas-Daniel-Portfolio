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

A ping works if both devices are on the same network. If they are on different networks and there is no router, the ping will fail.

### Part 3: Modify and Test Again
ping 192.168.2.10 (failed)
<img width="293" height="143" alt="Screenshot 2026-03-26 at 8 28 52 AM" src="https://github.com/user-attachments/assets/bff3b764-064b-4835-9716-04fb36363519" />

Nothing changed at first because the devices were still on different networks. Without changing the subnet mask or adding a router, they still could not communicate.

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

No, they are not on the same network.

### Scenario C
Two PCs that look “similar” but are NOT on the same network
<img width="347" height="285" alt="Screenshot 2026-03-26 at 8 35 05 AM" src="https://github.com/user-attachments/assets/12f98653-8369-4778-8a6e-f3e7fcc4095e" />

Two PCs that look “different” but ARE on the same network
<img width="351" height="294" alt="Screenshot 2026-03-26 at 8 36 46 AM" src="https://github.com/user-attachments/assets/5ad3944f-7c72-4234-b9be-2a8a418f8fd8" />

## Assignment 2: 
### Scenario C: Small Business Workspace
### Part 1: Device Exploration

<img width="725" height="401" alt="Screenshot 2026-03-27 at 9 14 59 AM" src="https://github.com/user-attachments/assets/f6dfabb9-9df6-4098-9077-c12bd7ac0bd5" />

The network layout includes multiple PCs, a switche, and a wireless device. All devices are clearly labeled and organized neatly. The layout shows how each device is connected, making it easy to understand the structure of the network.

### Part 2: Design Decisions & Part 3: Final Network Layout

<img width="680" height="372" alt="Screenshot 2026-03-27 at 9 24 25 AM" src="https://github.com/user-attachments/assets/c8821202-0ec3-4c2f-a3bf-13d247a912ce" />

The final network layout was designed to be clean and efficient, with all devices clearly labeled and connected through switches to keep communication organized. Wired connections were used for devices that require stable and fast connections, such as desktop computers, while wireless connections could be used for flexibility and mobility.

# Testing and Evaluation
## Assignment 3:
### Part 1: Add the Router & Part 2: Configure Router Interfaces

Fully configured setup with router working
<img width="831" height="400" alt="Screenshot 2026-03-30 at 10 17 38 AM" src="https://github.com/user-attachments/assets/c5a49bdf-c288-4d1f-bb2f-756861b6aed6" />
<img width="510" height="496" alt="Screenshot 2026-03-30 at 10 18 13 AM" src="https://github.com/user-attachments/assets/5fc4e7b8-2909-4b03-9c56-8eeee46632d0" />

### Part 3: Configure Default Gateway on PCs
Default gateways and ip addresses set on a pc in each LAN
<img width="638" height="156" alt="Screenshot 2026-03-30 at 10 21 00 AM" src="https://github.com/user-attachments/assets/1b2b2393-e2ca-46b7-ae3b-9248edaaea25" />
<img width="644" height="145" alt="Screenshot 2026-03-30 at 10 21 30 AM" src="https://github.com/user-attachments/assets/a5a17735-a3b6-4acf-8080-b683d0773bd9" />

### Part 4: Test Communication
Communication from LAN 1 to LAN 2
<img width="298" height="172" alt="Screenshot 2026-03-30 at 10 22 39 AM" src="https://github.com/user-attachments/assets/ff0e4b0f-73f5-4bf7-99c6-f1f91fa80621" />

The router connects different networks (LANs) together and allows devices on separate networks to communicate with each other.

## Assignment 4:
### Part 1: Troubleshooting Investigation
#### 1. Ping (Command Prompt)
ping 192.168.2.10 (failed)
<img width="311" height="167" alt="Screenshot 2026-03-31 at 12 38 19 PM" src="https://github.com/user-attachments/assets/3dc37ad0-9aef-4787-926e-490b51b1291f" />

#### 2. IP Configuration
PC2 IP Configuration
<img width="640" height="140" alt="Screenshot 2026-03-31 at 12 40 36 PM" src="https://github.com/user-attachments/assets/3b4ad1fc-bebe-43d5-8a0b-61e4e5055e52" />

#### 3. Visual Inspection
Physical Layout
<img width="791" height="425" alt="Screenshot 2026-03-31 at 12 42 01 PM" src="https://github.com/user-attachments/assets/0ba92f9c-e0ca-4422-9c16-13312f2d1cdb" />

#### 4. Router CLI
Router IOS Command Line Interface
<img width="614" height="466" alt="Screenshot 2026-03-31 at 12 42 27 PM" src="https://github.com/user-attachments/assets/055e59a6-b5f6-4cc8-aaf1-6dee16bdaa09" />

### Step 2: Identify the Problem
The second terminal had not yet been configured
<img width="450" height="110" alt="Screenshot 2026-03-31 at 12 44 59 PM" src="https://github.com/user-attachments/assets/e86ee8c9-6641-4443-9208-bacd49a1567d" />

### Step 3: Apply a Fix
Working Layout
<img width="796" height="410" alt="Screenshot 2026-03-31 at 12 46 25 PM" src="https://github.com/user-attachments/assets/bafcc5f3-a4fe-4d6f-a1ff-5e0579d95906" />

### Step 4: Test Again
ping 192.168.2.10 (working)
<img width="350" height="175" alt="Screenshot 2026-03-31 at 12 47 36 PM" src="https://github.com/user-attachments/assets/2869ab87-457a-4b11-96e4-1cd43f5154c0" />

# Reflection and Analysis
## Assignment 1 Reflection
A device determines whether another device is on the same network by comparing its IP address and subnet mask. The subnet mask tells the device which part of the IP address represents the network. If those parts match, the devices are on the same network. For example, two IP addresses like 192.168.1.10 and 192.168.2.10 may look similar but are not on the same network if the subnet mask is 255.255.255.0. On the other hand, addresses like 172.16.1.10 and 172.16.2.20 may look different but are on the same network if the subnet mask is 255.255.0.0.

## Assignment 2 Reflection: 
In my network design, I selected devices including a router, switch, server, multiple PCs, and a laptop to create a structured and functional small business network. The router was used to connect the network and allow communication outside of the local network, while the switch was used to connect all internal devices efficiently. I included a server to represent centralized storage or services, which supports a client-server model instead of peer-to-peer because it is more organized and scalable for a business environment. Most devices were connected using wired connections to ensure stable and fast communication, especially for the PCs and server, while the laptop represents a device that could be used more flexibly. The layout is clean and organized with all devices connected through the switch, which helps reduce network issues and makes the system easier to manage and expand in the future.

## Assignment 3 Reflection: 
The router allowed devices on different LANs to communicate by acting as a bridge between networks. Each router interface connects to a different network and has its own IP address, which helps direct traffic correctly. The default gateway is the router’s IP address that devices use when sending data to another network. When I tested communication using ping, it initially failed between networks, but after configuring the router and setting the default gateways correctly, the ping succeeded. This showed that the router was correctly forwarding data between the LAN

## Assignment 4 Reflection: 
One issue I encountered was that a device could not communicate with another network because it was not configured properly. I discovered this problem by using the ping command, which failed, and then checking the IP configuration settings. I also looked at the router command line interface to identify the issue. The problem was fixed by correctly configuring the device with the proper IP address and settings. After applying the fix, I tested the network again using ping, and it worked successfully. This confirmed that the network was functioning properly.

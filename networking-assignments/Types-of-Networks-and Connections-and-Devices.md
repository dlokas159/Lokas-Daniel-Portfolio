# Types of Networks & Connections & Devices

Answer the following in complete sentences in a well-written paragraph on your digital porfolio:
1. Are your internal and external IP addresses the same or different?
2. Which IP belongs to your local network?
3. Which IP belongs to the internet?
4. Why might a virtual machine use Network Address Translation (NAT) when
connecting to the internet?
5. How does Shared mode make it easier to connect multiple virtual machines on one
computer?

## The output of ip a in Shared (NAT) mode
![shared](files/shared.png)

## The output of ip a in Bridged mode
![bridged](files/bridged.png)

## The WhatIsMyIPAddress.com page results for both modes
### whatismyipdress.com IPv4 Shared Mode
![ipv4](files/IPv4.png)


### whatismyipdress.com IPv4 Bridged Mode
![ipv4](files/IPv4(2).png)

Answer the following in complete sentences in a well-written paragraph on your digital
portfolio:
1. How did your internal IP address change when you switched to Bridged mode?
2. Did your external IP address change or remain the same?
3. In Bridged mode, does your virtual machine act more like a separate computer or a
computer behind another device?
4. Why might an organization choose Bridged mode instead of Shared (NAT) mode?
5. What security or management challenges could come with using Bridged mode?


| Mode | Internal (Private) IP | External (Public) IP | Notes |
| :------ | :------- | :------- | :------- |
| **Shared(NAT)** | 192.168.64.2/24 | 173.95.44.210 | The Internal and Extrenal are different but the external for bridged and shared are the same |
| **Bridged** | 10.32.1.32/23 | 173.95.44.210 | internal and external are very different |


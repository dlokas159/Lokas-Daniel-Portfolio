# Types of Networks & Connections & Devices

Answer the following in complete sentences in a well-written paragraph on your digital porfolio:
1. Are your internal and external IP addresses the same or different?
2. Which IP belongs to your local network?
3. Which IP belongs to the internet?
4. Why might a virtual machine use Network Address Translation (NAT) when
connecting to the internet?
5. How does Shared mode make it easier to connect multiple virtual machines on one
computer?

The internal and external IP addresses are different. The internal IP belongs to the local network and identifies the virtual machine inside a home or school network. The external IP belongs to the internet and is assigned by the internet provider. A virtual machine uses Network Address Translation (NAT) to share the host computer’s internet connection, which helps it go online without needing its own public IP. Shared mode makes it easier to connect multiple virtual machines on one computer because they can all use the same internet connection safely and easily.

## The output of ip a in Shared (NAT) mode
<img width="719" height="356" alt="Image 11-5-25 at 10 25 AM" src="https://github.com/user-attachments/assets/e95ba587-029b-4fc6-b118-14ffdb21f01d" />



## The output of ip a in Bridged mode
<img width="725" height="293" alt="Screenshot 2025-11-05 at 10 31 28 AM" src="https://github.com/user-attachments/assets/05a75fb6-809d-4b1b-a3e5-92daf460d37e" />


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

When it was switched to Bridged mode, the internal IP address changed from 192.168.64.2 to 10.32.1.32, showing that the VM joined a new part of the local network. The external IP stayed the same because both modes used the same internet provider. In Bridged mode, the VM acts more like a separate computer on the network instead of being hidden behind the host. An organization might use Bridged mode to let virtual machines communicate directly with other devices. However, it can be less secure because each VM is fully visible on the network.


| Mode | Internal (Private) IP | External (Public) IP | Notes |
| :------ | :------- | :------- | :------- |
| **Shared(NAT)** | 192.168.64.2/24 | 173.95.44.210 | The Internal and Extrenal are different but the external for bridged and shared are the same |
| **Bridged** | 10.32.1.32/23 | 173.95.44.210 | internal and external are very different |

Write a short paragraph (5–7 sentences) beneath your table addressing the following:
• Which mode made your VM appear as its own device on the local network?
• Which mode provided a safer, more controlled environment?
• How does NAT help manage limited IPv4 addresses and improve security?
• What did you learn about how data travels from a device to the internet?

Bridged mode made the VM appear as its own device on the network. Shared (NAT) mode provided a safer, more controlled setup because it hides the VM behind the host computer. NAT helps save IPv4 addresses by letting many devices share one public IP while keeping their private addresses separate. It also adds security by blocking outside access. Data travels from a local device through the router (and sometimes NAT) before reaching the internet and coming back to the right device.

Write a short reflection (1 paragraph, 5–8 sentences) below your screenshots that answers these:
• How did your IP addresses change between Shared and Bridged mode?
• What did this experiment teach you about how local and public networks communicate?
• Why might IT professionals use different network configurations for home, business, or
lab environments?
• Which mode do you think is best for classroom use, and why?

When switching between Shared and Bridged mode, the internal IP changed, but the external IP stayed the same. This showed how local and public networks work together through routers and IP translation. IT professionals use different network setups for safety, testing, or direct access. For classroom use, Shared (NAT) mode is better because it’s safer and easier to manage. This activity taught how devices connect to each other and the internet.

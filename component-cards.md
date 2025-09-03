## 1. Project Overview

**Problem Statement:** 
This project helped us learn all of the different parts of a computer and their functions.

**Objectives:**  
- Identify main hardware components (CPU, RAM, GPU, Storage, Motherboard, PSU, NIC, Cooling System, I/O Devices).  
- Describe the function of each component.  
- Trace the path of data through hardware during typing and saving a file.  
- Understand software layers (Firmware/UEFI, Drivers, OS, Libraries/Runtimes, Applications).  

**Success Criteria:**  
- Complete hardware card arrangement correctly for the typing/saving exercise.  
- Correctly map software layers and interactions.  
- Document choices, reflections, and explanations.  

---

## 2. Design & Planning

**Hardware Process:**  
First diagram (Image 1):
Layout is more vertical and linear.
Information flows mostly top-to-bottom, with the motherboard in the center and arrows pointing outward to GPU, CPU, RAM, and storage.
![screenshot](IMG_2202.jpg)
It’s simpler, easier to follow, but less detailed about the back-and-forth relationships between parts.
Second diagram (Image 2):
Layout is more spread out and complex, showing multiple directions of data and power flow.
Uses more arrows, including loops, to show two-way connections (e.g., between CPU, RAM, NIC, GPU, and I/O devices).
It gives a clearer sense of interaction between components, but looks more cluttered compared to the first.
![screenshot](IMG_2202.jpg)

**Software Process:**  
This diagram shows the layers of computer software, from bottom to top. At the base is Firmware/UEFI, which starts the machine. Above that are Device Drivers, which let the operating system talk to hardware. The Operating System manages programs and hardware, while the Networking Stack handles internet connections. Libraries and Runtimes give apps extra code they need, and Applications are the programs people use. On the side, extra layers like Virtual Machines, Security/Encryption, and the File System add protection, file organization, and support for different programming environments.
![screenshot](IMG_2205.JPG)


---

## 3. Reflection & Analysis

This project taught me how both hardware and software components work together to make a computer work. I learned the roles of CPU, RAM, GPU, storage devices, and I/O devices. Mapping the data flow when typing and saving a document helped me understand the how components worked with each other and communicate. Working with software strips also helped me understand how applications, libraries, OS, drivers, and firmware interact. During the Build-A-PC challenge, I had to make upgrade decisions, which taught me about performance real-world planning. I now better understand why drivers are essential. Next steps include practicing more networking configuration and maybe buildinhg another pc in the future. 

---

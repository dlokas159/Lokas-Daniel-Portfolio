## **Assignment 1: Cybersecurity Basics for Devices**

### **Planning & Design**
The goal of this assignment was to identify vulnerabilities on an **Ubuntu VM**, secure it using a **firewall**, and evaluate **encryption**. The objectives included:

- Scanning for open ports
- Enabling and configuring **UFW**
- Blocking insecure services (e.g., **Telnet**)
- Checking disk encryption status

This aligns with the **CIA triad** by improving:
- **Confidentiality** (through encryption)
- **Integrity** (by disabling unnecessary services)
- **Availability** (by ensuring required services remain online)

---

### **Technical Development**
1. I used the command:
    ```bash
    netstat -tuln
    ```
    This identified open ports.

**Necessary Ports Identified:** SSH (22), DNS (53), DHCP (68)

**Unnecessary Ports Identified:** CUPS (631), discovery services (5353), high ports (9843, 53443, 59686)

2. Installed and enabled **UFW firewall**:

    ```bash
    sudo apt update && sudo apt upgrade
    sudo apt install ufw -y
    sudo ufw enable
    ```

3. Blocked insecure **Telnet**:

    ```bash
    sudo ufw deny 23/tcp
    ```

4. Checked disk encryption:

    ```bash
    lsblk -f
    ```
    Output showed only ext4 and vfat, meaning **no LUKS encryption**.

#### **Outputs**
[Netstat -tuln Output](files/unnamed(3).png)
[ufw enable](files/unnamed.png)
[ufw deny](files/unnamed(1).png)
[lsblk -f](files/unnamed(2).png)

---

### **Testing & Evaluation**
**UFW** was enabled and firewall rules applied successfully.

Ports were analyzed for risk; **SSH (22)** was the most likely attack target due to brute-force attempts.

**Telnet** was blocked to prevent plaintext credential attacks.

Disk encryption was not enabled, which is acceptable for a classroom VM but **unsafe** for real-world laptops.

---

### **Reflection & Professionalism**
This assignment demonstrated how security controls directly protect devices:

- Every open port represents a **potential risk**.
- Firewalls act as a security guard for network traffic.
- **Encryption** ensures confidentiality, keeping data safe even if stolen.

I gained professional experience in configuring Linux firewalls with **UFW** and learned why insecure protocols like **Telnet** must be disabled. This directly connects to enterprise cybersecurity practices, where system administrators **harden endpoints** before deployment.

***
***

## **Assignment 2: Outdated Software Log**

### **Planning & Design**
The purpose of this assignment was to analyze installed software for outdated versions, evaluate the risks, and update them.

**Planned steps:**

1. Run version-check commands:

    ```bash
    openssl version
    firefox --version
    libreoffice --version
    python3 --version
    apache2 -v
    gimp --version
    java -version
    ssh -V
    ```

2. Compare installed versions with the latest releases.
3. Mark results as up-to-date or outdated.
4. Use `sudo apt update && sudo apt upgrade -y` before testing.

---

### **Technical Development**
1. Checked and recorded software versions in the log.
2. **OpenSSL** was identified as the most dangerous if outdated, since it could allow attackers to break encryption.
3. Updated **Java** and confirmed installation with `java -version`.

#### **Outputs**
[install apache2](files/screenshot.jpg)
[apache2](files/screenshot(1).jpg)

---

### **Testing & Evaluation**
Outdated applications were detected and upgraded.

**Risks identified:**

- **OpenSSL**: could expose encrypted communications.
- **Apache/Java**: could allow remote code execution or malware injection.
- **GIMP/LibreOffice**: potential for malicious file exploits.

Updates were applied to eliminate vulnerabilities.

---

### **Reflection & Professionalism**
This assignment reinforced the importance of **patch management** in cybersecurity.

- **Outdated software** is a common attack vector.
- Schools, hospitals, and businesses must update regularly to protect sensitive data and ensure compliance.
- On a real laptop, outdated programs could lead to **malware, identity theft, or full system compromise**.

I concluded that **OpenSSL** was the most critical to update, since weak encryption undermines the security of all communications. This connects directly to real-world cybersecurity work, where keeping systems **patched** is the first line of defense.

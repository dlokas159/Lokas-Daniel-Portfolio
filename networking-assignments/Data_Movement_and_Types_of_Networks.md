
## **1. Planning & Design**

### Objectives
- Design a **strong password algorithm** focusing on length, entropy, and unpredictability.
- Apply the algorithm to **change the default Ubuntu password**.
- Install and verify **Multi-Factor Authentication (MFA) using `pam_google_authenticator`**.
- Perform **system updates and patches**, examining logs.
- Align password rules with **NIST SP 800-63B** and concepts from **OWASP Authentication Guidelines**.

### Planning Artifacts
- Drafted password algorithm using user-based prompts to generate complex outputs :contentReference[oaicite:0]{index=0}.
- Reflected on password strength and entropy (long + randomized + personal but non-public info).
- Identified commands needed for:
  - `passwd`, `sudo`, `apt update`, `apt upgrade`
  - `google-authenticator`, `SSH` config changes
- Noted importance of removing default credentials and implementing layered security.
- Took screenshots during each key step (password change, MFA, patch logs, etc.).

---

## **2. Technical Development**

### 
- Created an algorithm combining personal facts, numbers, symbols, and a reversed word.
- Tested the algorithm-generated password for usability and complexity.

### Change Default Ubuntu Password
- Logged in with default `ubuntu:ubuntu`.

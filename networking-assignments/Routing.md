# 1. Design & Planning
## Investigation 1 — Your Machine’s Layer 3 Identity
### VM #1
<img width="718" height="437" alt="Screenshot 2026-02-23 at 8 43 24 AM" src="https://github.com/user-attachments/assets/c1327fc8-33cf-4f8f-9b83-96611858fe00" />

### VM #2
<img width="646" height="392" alt="Screenshot 2026-02-23 at 8 43 38 AM" src="https://github.com/user-attachments/assets/39e1ba2a-c3d0-4528-8731-8df386a738ba" />

### Questions: 
1. What is your IPv4 address?
2. What network are you on?
3. Is a default route present?
4. What device is listed as your gateway?

### Answer these questions:
1. Where is that information stored?
2. What would happen if the default gateway entry disappeared?

# 2. Technical Development
## Part 1 – Your Inside Identity
<img width="717" height="331" alt="Screenshot 2026-02-25 at 10 34 09 AM" src="https://github.com/user-attachments/assets/85f8dea2-4d4f-4971-8049-4952d238590b" />

### As a description to your screenshot, answer the following on your digital portfolio.
1. What is your IPv4 address?
2. Is this address globally unique?
3. Could another network somewhere else in the world use the same address?
4. What clues help you determine this?

### Now verify your thinking. Search online for:
“RFC1918 address ranges”
Identify the three private IPv4 ranges. Determine whether your IP falls within one of
those ranges. Write about this on your digital portfolio.

## Part 2 – Your Outside Identity



# 3. Testing & Evaluation
## Investigation 2 — Three Destinations
### Case 1 — Send Traffic to Itself (Loopback)
<img width="579" height="174" alt="Screenshot 2026-02-23 at 8 55 03 AM" src="https://github.com/user-attachments/assets/bb683294-9804-432e-86f4-81e33300ffb8" />

#### Questions:
• Did this traffic leave your machine?
• Does the routing table need a gateway entry for this to work?

### Case 2 — Send Traffic to the Other VM (Same Network)
<img width="567" height="176" alt="Screenshot 2026-02-24 at 9 10 54 AM" src="https://github.com/user-attachments/assets/740e5882-0afc-4f3a-9317-4867c54375a2" />

#### Questions:
• Did Ubuntu send this to the default gateway?
• Which routing table entry allowed direct delivery?
• How can you prove it?

### Case 3 — Send Traffic Off the Network
<img width="574" height="188" alt="Screenshot 2026-02-24 at 9 14 21 AM" src="https://github.com/user-attachments/assets/dbac1052-d37e-43f7-b493-8ab42a1b4d23" />

#### Questions:
• What routing table entry made this possible?
• Why can Ubuntu not deliver this directly?
• What device handled the first step?

## Investigation 3 — How the Decision Is Made
Will the next hop be:
• Direct?
• **Gateway**
<img width="1386" height="266" alt="unnamed" src="https://github.com/user-attachments/assets/c23a6ec5-a2bd-4397-a0bd-7a2f47049cfe" />


# 4. Reflection & Analysis

## Explain, in your own words in a well-written paragraph:
1. What is the role of the routing table?
2. What is the role of the default gateway?
3. What condition must be true for direct delivery?
4. What condition requires router involvement?




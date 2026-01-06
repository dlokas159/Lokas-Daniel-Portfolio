# Adaptive Arm-Based Beverage Delivery System  
**Capstone Project — Pearl Rehab Center**

---

## Project Status
**In Progress**  
This project is currently under active development. Design, prototyping, and testing are ongoing, and no final hardware or software implementation has been completed yet.

---

## Project Overview

The **Adaptive Arm-Based Beverage Delivery System** is a mechanical assistive device being developed in collaboration with **Pearl Rehab Center**. The goal of this project is to design a **robotic arm with a self-balancing cup holder** that helps individuals with limited mobility independently access beverages.

The system is intended to:
- Hold a standard drinking cup
- Stabilize the cup during movement
- Move the cup toward the user in a controlled and safe manner

The device will be **3D printed** and controlled using an **Arduino-based system**, with servo motors enabling smooth, precise motion.

---

## Why This Project Was Chosen

This project was selected because it:
- Addresses a **real-world accessibility challenge**
- Serves a **specific rehabilitation center and user group**
- Combines **mechanical design, electronics, and programming**
- Aligns with assistive-technology principles of independence and dignity

A successful version of this project would allow users with limited upper-body mobility to drink without requiring constant assistance from caregivers.

---

## Inspiration & Prior Art 

This project draws inspiration from existing assistive and robotic arm projects, including:
- **past robotic arm project** — Original author/maker: **Aaron Dunnigan**


### How This Project Will Differ
- Designed specifically for **rehabilitation center use**
- Focused on **cup stabilization and user safety**
- Modular design for future customization
- Emphasis on affordability and 3D-printable components

---

## Design Specifications (In Progress)

Key design considerations include:
- Range of motion appropriate for seated users
- Self-balancing cup holder mechanism
- Motor torque vs. speed tradeoffs
- Mounting method (table, wheelchair, or bed-side)
- User safety and spill prevention

**Design Specification Considerations Document:**  
[Link](https://docs.google.com/document/d/1RlveuHIZWM5QWMhkt3ebb2Dl6V2vLC_BaKYv-PvAG7E/edit?usp=sharing)

---

## Planned System Components

### Mechanical
- 3D-printed robotic arm segments
- Self-balancing cup holder mechanism
- Mounting bracket system

### Electronics
- Arduino microcontroller
- Servo motors (model TBD)
- Power supply (TBD)
- Wiring and connectors

### Software
- Arduino control code
- Servo motion control logic
- Safety limits and motion constraints

---

## Bill of Materials 

![Screenshot](Screenshot.png)

---

## Tools & Equipment (Planned)

### Digital Tools
- Arduino IDE
- Fusion 360 (CAD)

### Fabrication Tools
- 3D Printer
- Hand tools (screwdrivers, hex keys)
- Fab Lab equipment (as needed)

---

## Files to Be Included (As Project Progresses)

- Arduino source code: [code](https://docs.google.com/document/d/1JzSWEezLwWs6ETRjX4n0eiQ5AaLUB9aJAykjetHIvts/edit?usp=sharing)
- STL files for 3D printing: [print](https://drive.google.com/file/d/18iG6IoLDqeNWONsQEqfif6LjOAfSxby3/view?usp=sharing)
**First 3D printed gyro cup model**
  <img width="792" height="652" alt="Screenshot 2025-12-19 at 3 43 05 PM" src="https://github.com/user-attachments/assets/6c588462-365a-4e63-a908-00b46d773c70" />

**Failed Model**
<img width="933" height="705" alt="Screenshot 2025-12-19 at 3 41 50 PM" src="https://github.com/user-attachments/assets/886b3453-45d4-4e01-8b4c-47af7907c736" />

**3D print file photo**
<img width="666" height="571" alt="Screenshot 2026-01-05 at 6 22 50 PM" src="https://github.com/user-attachments/assets/334d9de8-774f-4d5e-abd9-c8d3ce7c96db" />


---

## Project Timeline

- **Upcoming Milestones**
  - CAD modeling of arm components
  - First 3D-printed prototype
  - Arduino motion testing
  - Cup stabilization testing
  - Iterative refinement based on feedback

---

## Documentation of Learning 

This section will include:
- Journal entries
- Key design decisions and reasoning
- Challenges encountered during prototyping

## Journal Entries for Final Project:
- **9-18-2025**  
  Committed to working with Pearl Rehab Center and began research into existing assistive technologies.

- **10-1-2025**  
  Researched cup holder mechanisms and mounting systems.  
  Evaluated servo motor options for the robotic arm.  
  Collaborated with Aaron to define design requirements and produced an initial system sketch.

- **10-8-2025**  
  Refined overall project concept and clarified system goals.  
  Began planning the mechanical arm structure and self-balancing cup holder approach.

- **10-15-2025**  
  Began preliminary CAD planning for robotic arm components.  
  Considered joint layout, range of motion, and modular design for 3D printing.

- **10-22-2025**  
  Planned Arduino control approach and basic servo wiring layout.  
  Researched motion control strategies and safety considerations.

- **10-29-2025**  
  Prepared for initial prototyping and identified required materials and print settings.  
  Reviewed design assumptions and noted areas for iteration.

- **11-6-2025**  
  Reviewed project requirements and accessibility goals for users with limited mobility.  
  Refined ideas for how the robotic arm would approach and deliver a cup safely.

- **11-7-2025**  
  Continued research on self-balancing cup holder mechanisms.  
  Looked into passive vs. active stabilization approaches.

- **11-8-2025**  
  Sketched alternative cup holder and arm joint concepts.  
  Considered how center of gravity affects spill prevention.

- **11-13-2025**  
  Began outlining the mechanical structure of the robotic arm.  
  Considered joint count, arm reach, and mounting options.

- **11-14-2025**  
  Researched Arduino-compatible servo control methods.  
  Reviewed example Arduino servo projects for reference.

- **11-18-2025**  
  Aaron and I researched different servo motors to see which ones would work best for the robotic arm. We looked at torque ratings, sizes, and cost, and compared small micro servos to larger metal-gear servos. The smaller servos were too weak to safely hold a cup, especially when the arm is extended. The larger, very high-torque servos seemed unnecessary and could move too aggressively near a user.

From this research, we decided that a medium-torque servo would be the best option for prototyping because it provides enough strength while still allowing smoother, safer movement. This helped guide the direction of the arm design moving forward.

- **12-8-2025**  
  Reviewed overall system design and identified components needing further refinement.  
  Updated project documentation to reflect current progress.

- **12-10-2025**  
  Planned next steps for CAD modeling and prototyping.  
  Organized research notes and reference materials.

- **12-11-2025**  
  I tried printing the self-balancing cup holder multiple times. Two of the prints failed completely, and one only printed about halfway before stopping. These failures showed that the design had weak areas, thin walls, and was difficult to print in its current orientation.

Based on this, I realized the design needs to be simplified and reinforced. I plan to redesign the cup holder with thicker walls and better support so it can print more reliably and be strong enough for real use.

- **12-14-2025**  
  I spent time thinking about safety since the arm will be operating close to a person’s face and upper body. Fast or unpredictable movement could cause spills or discomfort. Because of this, I decided that smooth and slow motion is more important than speed or reach.

This will affect how the arm is programmed and how far it is allowed to move.


---

## Current Challenges 
1. Strength vs. Smooth Motion

The robotic arm must be strong enough to hold a filled cup while moving smoothly and safely. Higher-torque servos improve strength but can cause quick movement if not controlled. 

2. Self-Balancing Cup Holder Fabrication

The self-balancing cup holder has been hard to manufacture. It was printed two times: one prints failed completely, and one print completed only partially. These failures revealed issues with print orientation and thin structural sections. We fixed the model by changing the thickness of the rim. 

3. User Safety and Stability

Because the system operates near the user, safety is critical. Mechanical motion limits and software constraints will be used to control speed and range of motion. We are going to make a stable mounting system to prevent tipping or unintended movement.


---

## Next Steps

- Finalize mechanical design concepts
- Test servo control logic
- Build and evaluate early prototypes

---

## Summary

This capstone project is a process for designing an assistive device that helps a mobility-impaired person maintain his/her autonomy. Through a partnership with Pearl Rehab Center, this project is focused on ensuring that a practical, well-designed, and meaningful solution is achieved that can be used in a real-life situation.

---

**Name:** [Daniel Lokas]  
**Course:** [Senior Engineering]  
**Instructor:** Mr. Dubick]  
**School:** [Charlotte Latin School]

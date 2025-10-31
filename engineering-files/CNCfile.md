# CNC PCB Milling Log

This repository documents my progress learning CNC PCB design and milling — from creating the design file to producing a final physical board.

---

## 2025-10-27
**Activity:**  
Created the CNC file in MakerCAD following the provided tutorial.

**Details:**  
Learned how to use MakerCAD to generate the toolpaths and export the file format required for PCB milling. Followed the step-by-step process to understand how traces and cutouts are defined.

**Reflection:**  
This was a solid introduction to the workflow. The tutorial helped clarify the coordinate setup and how to properly define the tool diameter for accurate milling. There was some initial confusion about exporting the correct file type, but rechecking the tutorial solved it.

---

## 2025-10-28
**Activity:**  
Created the CNC file independently for practice.

**Details:**  
Repeated the process without the tutorial to reinforce understanding. Focused on creating clean trace paths and ensuring all connections were correctly aligned before exporting the file.

**Reflection:**  
Working independently helped build confidence with the CNC design process. Some alignment issues occurred initially, requiring rework of the trace layout. After adjustments, the final file matched the expected output. This was valuable practice for the actual board.

---

## 2025-10-30
**Activity:**  
Printed the CNC file and learned how to use the milling machine.

**Details:**  
Used the prepared CNC file to mill the PCB. Learned how to set up the machine, position the material, and monitor the milling process to ensure the traces were cut accurately.

**Reflection:**  
It was exciting to see the digital design turn into a physical board. The biggest challenge was understanding how to correctly zero the machine to avoid cutting too deep or too shallow. After a few adjustments, the milling ran smoothly.

---

## 2025-10-31
**Activity:**  
Received the final PCB and inspected the board.

**Details:**  
Checked the milled board for any broken traces, shorts, or rough edges. Verified that all connections matched the design and that the board was ready for component soldering.

**Reflection:**  
The final board turned out well. The traces looked clean, and everything matched the original design. It was rewarding to see the full process—from CAD design to final physical PCB—come together successfully.

---

## Project Files

- **CNC Design File (.mkc):** [Add your file here](path/to/your_file.mkc)  
- **CNC Toolpath File (.nc):** [Add your file here](path/to/your_file.nc)

---

## Workflows & Documentation

- **Google Doc Workflow #1:** [Add link here](https://docs.google.com/)  
- **Google Doc Workflow #2:** [Add link here](https://docs.google.com/)

---

## Final PCB

![CNC PCB](CNC.jpg)  
*Final CNC PCB after milling.*

---

## Final Reflection

Throughout this project, one of the main challenges was ensuring that the **digital measurements in MakerCAD matched the physical dimensions** of the board material used for milling. The first few attempts revealed slight mismatches in trace spacing and board size, which required recalibrating the CNC machine and double-checking the scaling within the software. This experience emphasized the importance of verifying units, toolpath precision, and material thickness before printing.  

Another learning point was understanding how **tool zeroing and cutting depth** directly affect the trace quality. Initially, the cuts were too shallow, leaving excess copper, but careful re-zeroing and testing resolved the issue.  

In the end, successfully producing a clean and accurate PCB was a rewarding milestone. This project helped strengthen my understanding of the **entire CNC workflow**—from CAD design to fabrication—and built confidence in troubleshooting, precision measurement, and digital manufacturing techniques.

---

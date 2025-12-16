# TOPO MOUNTAIN — CNC Topography of Beirut, Lebanon

## Project Overview

This project is a **wooden CNC-milled topographic map of Beirut, Lebanon**, created as part of my TOPO MOUNTAIN series. The goal was to transform geographic elevation data into a physical relief map using CNC machining, emphasizing both accuracy and craftsmanship.

The final piece was machined from wood and highlights the elevation contours and terrain variation of the Beirut region.

---

## Photos / Videos

![IMG_2418](https://github.com/user-attachments/assets/f5b2d8ac-e80f-4a74-b74d-01ab7ef54dc2)

https://github.com/user-attachments/assets/053faa4e-982c-4b83-8be0-fb1a95b9b857


---

## Workflow

### 1. Data Acquisition
- Source topographic elevation data for Beirut, Lebanon  
- Convert elevation data into a usable heightmap  
- Normalize elevation ranges for CNC machining depth  

<!-- TODO: Add data source links (e.g., USGS, OpenTopoMap, etc.) -->

---

### 2. Design & Toolpath Setup (Vectric Aspire)

- Imported the heightmap into **Vectric Aspire**
- Scaled the model to fit stock dimensions
- Defined material thickness and zero position
- Generated:
  - Roughing toolpath
  - Finishing toolpath

<!-- TODO: Insert screenshots of Aspire setup -->
![Aspire Setup Screenshot](./images/aspire_setup.jpg)

---


## Issue Encountered: Incorrect Anchor Point

### The Problem

During initial machining attempts, the project **printed in the wrong physical location on the stock**. After troubleshooting, I discovered that:

- The Aspire setup was referencing **Anchor 2**
- The CNC machine was zeroed expecting **Anchor 1**
- This mismatch caused the toolpaths to shift unexpectedly when running the job

As a result, the carving would start offset from the intended position, risking material waste and potential tool crashes.

---

### The Solution

To resolve the issue:

1. Returned to **Vectric Aspire**
2. Verified the **Job Setup → Origin / Anchor settings**
3. Reset the anchor to **Anchor 1**
4. Re-exported all CNC toolpaths
5. Re-zeroed the CNC machine to match Anchor 1 exactly

Once both the software and machine referenced the **same anchor point**, the toolpaths aligned perfectly, and the job ran as expected.

---

## Files Included

### Design Files
- `Beirut_Topography.asp`
<!-- TODO: Confirm final Aspire file name -->

### CNC Toolpaths
- `beirut_roughing.nc`
- `beirut_finishing.nc`
<!-- TODO: Confirm toolpath filenames and formats -->

### Additional Assets
- Heightmap source file: **[FILE NAME]**
- Reference images: **[OPTIONAL]**

---

## Lessons Learned

- **Anchor consistency is critical**: The software origin and machine zero must always match
- Always double-check:
  - Job Setup
  - Anchor point
  - Material orientation
- A single incorrect reference point can invalidate an otherwise correct workflow

---

## What I Would Do Differently

- Add a **new and modified checklist** before machining:
  - Verify anchor
  - Run toolpaths above material
- Label anchor points physically on the spoilboard
- Save multiple Aspire job versions with explicit anchor naming

---

## Future Plans

- Expand the TOPO MOUNTAIN series to other cities
- Experiment with:
  - Layered contour maps
  - Resin infill for elevation contrast
  - Larger stock sizes for higher resolution
- Explore automated scripts for heightmap preprocessing

---

## Summary

This project reinforced the importance of precision not just in machining, but in **setup discipline**. Creating a CNC topographic map of Beirut was both technically challenging and personally meaningful. Resolving the anchor point issue improved my understanding of CNC coordinate systems and will directly inform all future CNC projects.

---

*Project by: [Daniel Lokas]*  
*Date: [12/16/2007]*  
*Course / Context: [Senior Engineering]*


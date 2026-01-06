# TOPO MOUNTAIN — CNC Topography of Beirut, Lebanon

## Project Overview

This project is a **wooden CNC-milled topographic map of Beirut, Lebanon**, created as part of my TOPO MOUNTAIN series. The goal was to transform geographic elevation data into a physical relief map using CNC machining, emphasizing both accuracy and craftsmanship.

The final piece was machined from wood and highlights the elevation contours and terrain variation of the Beirut region.

---

## Photos / Videos

### 3D Printed Topo File Image
<img width="1118" height="725" alt="Screenshot 2026-01-06 092051" src="https://github.com/user-attachments/assets/786e32f1-0f3d-4d00-8758-e2109714cbde" />

### Topo Being Milled
![IMG_2418](https://github.com/user-attachments/assets/f5b2d8ac-e80f-4a74-b74d-01ab7ef54dc2)

https://github.com/user-attachments/assets/053faa4e-982c-4b83-8be0-fb1a95b9b857

### Final Topo
![IMG](https://github.com/user-attachments/assets/6a92ae92-8934-4922-94c0-568fd5e8f679)


---
## Workflows (from Mr. Dubick)

---

## CNC Topography Workflow

### 1. Terrain Generation (Terrain2STL)

- Navigate to https://jthatch.com/Terrain2STL/
- Pan and center the map on the target location (Beirut, Lebanon)
-<img width="428" height="305" alt="Screenshot 2026-01-05 192423" src="https://github.com/user-attachments/assets/d98de3ce-7ede-4a2c-93fd-1bc719811ebf" />
 
- Define the model area using the red selection box:
  - Move, resize, and rotate the box as needed
- Adjust terrain settings: <img width="222" height="192" alt="Screenshot 2026-01-05 192510" src="https://github.com/user-attachments/assets/1a2fb40a-af27-40ef-a810-4882fd8edc5f" />

  - **Vertical Scale (Z-scale):** Controls elevation exaggeration
  - **Water Drop:** Lowers water bodies to emphasize coastlines
  - **Base Height:** Adds a solid base beneath the terrain
- Generate and download the terrain model as an **STL (.zip)** file

---

### 2. Job Setup & STL Import (Aspire – CAD)

- Create a new Aspire file
- Set job type to **Single-Sided**
- Define stock dimensions (X, Y, Z) to match the material
- Set zero positions:
  - **Z-zero:** Material surface (top)
  - **XY datum:** Bottom-left
- Import the STL file and orient it:
  - Orientation: **Top**
  - Scale the model to fit the stock (Z height ≤ material thickness)
  - Center the model in the workspace
- Position the model relative to the cutting plane to preserve relief and base thickness

---

### 3. Component Scaling & Positioning

- Adjust **Shape Height** to enhance vertical relief
- Set **Base Height** to raise the model closer to the top of the stock
- Center the component within the material
- Draw a rectangular boundary matching the final stock size  
  *(Used for machining limits and profiling)*
<img width="776" height="267" alt="Screenshot 2026-01-05 192702" src="https://github.com/user-attachments/assets/7137f66b-1a74-493e-b0db-462d9394efa5" />

---

### 4. 3D Toolpath Creation (CAM)

#### Roughing Pass
- Tool: **⅛" flat end mill** (ATC Tool #1)
- Strategy: **Z-Level** or **Raster**
- Boundary: **Model boundary**
- Leave a small machining allowance for finishing

#### Finishing Pass
- Tool: **⅛" ball nose** (ATC Tool #6)
- Strategy: **Raster** or **Offset**
- Boundary: **Model boundary**
- Used to generate final surface detail
<img width="227" height="327" alt="Screenshot 2026-01-05 192737" src="https://github.com/user-attachments/assets/af159167-8718-40d8-9da0-289b07485fb5" />

---

### 5. 2D Profile Toolpath

- Select the rectangular boundary
- Tool: **⅛" flat end mill**
- Set cut depth to release the part from the stock
- Use **climb cutting**
- Tabs not required

---

### 6. Simulation & Export

- Preview all toolpaths together to verify accuracy and detail
- Check for missed areas or collisions
- Review machining time via **Toolpath Summary**
- Save the Aspire project file (**.crv3d**)
- Export combined toolpaths using the **Carvera ATC post-processor**
- Output a single CNC file that runs roughing, finishing, and profiling sequentially

---

## PCB Toolpath & Milling Workflow

### Key Notes

- **0.8 mm corn flat-end bit:** Used to remove bulk material
- **0.2 mm × 30° engraving bit:** Used to cut copper traces
- The Makera milling machine uses **clamps** (not adhesive), so **tabs are required**
- Toolpath usage:
  - **2D Pocket:** Copper traces
  - **2D Contour:** Board edge cuts
  - **2D Drilling:** Drill holes

---

### PCB Toolpath Workflow (MakeraCAM)

1. Open **MakeraCAM**
2. Select **3-AXIS**
3. Edit stock settings:
   - Material: **PCB**
   - Length (X): **127 mm**
   - Width (Y): **101 mm**
   - Height (Z): **1.7 mm** (FR4 thickness)
<img width="226" height="522" alt="Screenshot 2026-01-05 192645" src="https://github.com/user-attachments/assets/9b296281-9f3d-4cf3-930f-577e4f7dc15b" />

4. Import all Gerber files using **Import PCB**
5. Reposition Gerbers:
   - Select all 2D layers
   - Use **Adjust Object → Transform → Move**
   - Set anchor point to **Bottom Left**
   - Set X and Y to **6 mm**
6. Toggle visibility:
   - Enable only **F_Cu** and **Edge_cuts**
7. Create copper trace toolpath:
   - Select **2D Path → 2D Pocket**
   - End depth: **0.05 mm**
   - Tools:
     - 0.8 mm corn tool
     - 0.2 mm × 30° engraving tool
   - Material: **PCB**
   - Click **Calculate**
8. Drill holes (if applicable):
   - Toggle visibility for drill files
   - Select **2D Drilling**
   - Drill tip end depth: **1.7 mm**
   - Tool: **0.8 mm corn tool**
   - Click **Calculate**
9. Edge cuts:
   - Toggle visibility to show only **Edge_cuts**
   - Select inner outline
   - Choose **2D Contour**
   - End depth: **1.7 mm**
   - Tool: **0.8 mm corn tool**
   - Strategy: **Outside**
   - Tabs: **Custom**, add ~3 staggered tabs
   - Click **Calculate**
10. Preview all toolpaths
11. Export toolpaths:
    - Select all toolpaths
    - Rename file using: `LastName_FirstInitial_ProjectName_gcode.nc`
<img width="245" height="507" alt="Screenshot 2026-01-05 192810" src="https://github.com/user-attachments/assets/ee7e8127-c549-450d-830d-fdf55a8fc6b7" />

---

### PCB Milling on Carvera Controller

1. Open **Carvera Controller**
2. Connect to the correct **COM port**
3. Switch to manual control interface and press **Home**
4. Verify probe voltage is **≥ 3.6V**
5. Load the G-code file
6. Preview toolpaths in file preview mode
7. Select **Config and Run**
   - Enable **Auto Vacuum**
   - Enable **Auto Leveling**
8. Click **Run** to begin milling



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

### 3D Print File (stl)
- [.stl](https://drive.google.com/file/d/17b8iErIgdTPC2QINoPxt5SSZ8n9nIliX/view?usp=sharing)

### Design File (ASPIRE)
- [.crv3d](DanielLTopo.crv3d)


### CNC Toolpath
- [.cnc](DanielLTopo.cnc)



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


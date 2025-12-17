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

#### 1. Terrain Generation (Terrain2STL)

Navigate to https://jthatch.com/Terrain2STL/

Pan and center the map on the target location (Beirut, Lebanon)

Define the model area using the red selection box:

Move, resize, and rotate as needed

Adjust terrain settings:

Vertical Scale (Z-scale): Controls elevation exaggeration

Water Drop: Lowers water bodies to emphasize coastlines

Base Height: Adds a solid base under the terrain

Generate and download the terrain model as an STL (.zip) file

#### 2. Job Setup & STL Import (Aspire – CAD)

Create a new Aspire file

Set job type to Single-Sided

Define stock dimensions (X, Y, Z) to match material

Set zero:

Z-zero: Material surface (top)

XY datum: Bottom-left

Import the STL and orient it:

Orientation: Top

Scale model to fit stock (Z height ≤ material thickness)

Center the model in the workspace

Position the model relative to the cutting plane to preserve relief and base thickness

#### 3. Component Scaling & Positioning

Adjust Shape Height to enhance vertical relief

Set Base Height to raise the model closer to the top of stock

Center the component in the material

Draw a rectangular boundary matching final stock size (used for machining limits and profiling)

#### 4. 3D Toolpath Creation (CAM)

Roughing Pass

Tool: ⅛" flat end mill (ATC Tool #1)

Strategy: Z-Level or Raster

Boundary: Model boundary

Leave a small machining allowance for finishing

Finishing Pass

Tool: ⅛" ball nose (ATC Tool #6)

Strategy: Raster or Offset

Boundary: Model boundary

Generates final surface detail

#### 5. 2D Profile Toolpath

Select the rectangular boundary

Tool: ⅛" flat end mill

Cut depth set to release the part from stock

Climb cutting, no tabs required

#### 6. Simulation & Export

Preview all toolpaths together to verify accuracy and detail

Check for missed areas or collisions

Review machining time via Toolpath Summary

Save the Aspire project file (.crv3d)

Export combined toolpaths using the Carvera ATC post-processor

Output a single CNC file that runs roughing, finishing, and profiling sequentially

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

### Design File (ASPIRE)
- 


### CNC Toolpath
- 



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


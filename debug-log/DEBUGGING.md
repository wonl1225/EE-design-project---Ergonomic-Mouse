# Debugging Process (Ongoing)

## Problem Overview

When motion input is applied, the cursor slowly shifts toward the lower-left corner of the screen with occasional glitch-like jumps being observed. 

## Initial Hypotheses
  
- Possible degradation or defect of the ADNS-3080 sensor

- Software collision between the sensor code and other subsystems
  
- Incorrect motion accumulation 

- Hardware issues (incorrect circuits, SI) 

- logic errors within the sensor motion accumlation code

## Debug Strategy and Results

### Sensor Replacement

The initial ADNS-3080 sensor was replaced with a new unit due to possible defects in the original sensor itself. 

**Results:** The same kind of cursor drifting occured, implying that the issue was not caused by a sensor degradation. 

### Code Isolation

Every non-essential subsystems (rotary encoder and button input code) were removed from firmware for testing. 

**Results:** No change in behavior was observed, indicating subsystem interference is unlikely to be an issue. 

### Stationary Surface Test

The sensor was placed on a flat, stationary surface without any motion input

**Results:** The cursor remained at the center with minor movements. This suggests that the main issue is mainly related to motion handling rather than noise or circuit instability. 

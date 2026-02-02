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

### LED Pin Configuration Investigation
The ADNS-3080 sensor's LED pin was intentionally left floating, assuming the internal LED would be sufficient. When power issues were suspected, the LED pin was connected to the Arduino VCC pin to force LED activation.

**Results:** Connecting the LED pin directly to VCC did not resolve the issue. There was no change in behaviour no matter the LED pin. The sensor's internal LED operates correctly when adequate power is supplied.

### Hardware Power Issue Investigation

The PCB was tested for proper power delivery to the ADNS-3080 sensor.

**Results:** The sensor LED did not illuminate when connected via PCB, indicating a VCC trace issue. When tested on breadboard with direct 5V/GND connections with jumper wires, the sensor powered on successfully indicated by the LED and Product ID (0x17) was verified. This confirms a hardware power delivery fault in the PCB design.

### Motion Tracking Behavior (Breadboard)
When power issue was resolved via breadboard:
- SQUAL values were 0, indicating poor surface detection
- Cursor drift persisted with random directional movement

**Results:** Motion tracking remained unstable regardless of configuration, suggesting either focus/height calibration issues or motion accumulation code errors.

### Current Status
Possible causes identified so far:
1. PCB VCC trace prevents sensor power delivery (hardware issue)
2. Software issues with motion tracking
3. Possible optical focus problems

PINOUT:

VCC → 5V (try jumper wires)

GND → GND (try jumper wires)

NCS → D10

MOSI → D16

MISO → D14

SCLK → D15

RST → 3.3V (10k resistor)

NPO → left floating

LED → left floating

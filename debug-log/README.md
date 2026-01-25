# Debugging Process (Ongoing)

## Problem Overview

The cursor shifts itself into a left-bottom corner with occasional glitches when movement is entered.
  
## Hypotheses
  
- Degradation of ADNS-3080 sensor itself

- Error of sub-system code colliding with the sensor code
  
- Motion behavior

- Circuits 

- logic errors within the sensor motion accumlation code

## Debug Strategy

- The initial ADNS-3080 sensor was replaced with a new product due to possible defects in the original sensor itself. This strategy did not work as the same kind of cursor drifting occured. 

- Isolating the sensor code from all other subsystems(rotary encoder and click button code) did not work, indicating that collision with systems was not the issue.

- Motion behavior when the device is stationary was verified by placing the sensor on a flat surface. At a flat surface, the cursor stayed stationary at the center with occasional minor movements. This is a huge indication that the main issue lies with motion behavior rather than signal-processing within the circuit.  

- 

- 

# 8/1 Macropad PCB
Repo for my (mis)adventures in creating a custom PCB for a macropad. I have always been a fan of custom keyboards. My daily driver is a stripped-down DROP ALT keyboard. I replaced the switches with ones that I hand-lubed, swapped the stabilizers with higher quality ones, and fitted custom keycaps to complete the build. After falling even further down the rabbit hole, the only natural progression of this hobby was clearly to create a custom PCB. This PCB has 8 slots for MX-hybrid switches (no LED pins) and 1 rotary encoder (hence, 8/1). The design of this build was inspired by ai03's <a href="https://wiki.ai03.com/books/pcb-design/chapter/pcb-designer-guide">PCB Designer Guide</a>.

## Software
KiCad 7.0 was used to create the schematics and design for the PCB. A custom footprint library, MX_ALPS_HYBRID, was used for the switch slot footprints, but everything else is available on vanilla KiCad.

## Schematics
The following are images of the schematics that were created in KiCad. This schematics file was then used to generate the PCB template.
### Microcontroller Unit

<p align="center">
 <img width="50%" alt="image" src="https://github.com/Lyam-Milbury/custom-keeb-pcb/assets/71610885/4d9e4aec-b5a9-4d14-b685-b89465e45fe4">
</p>

The Microcontroller unit (MCU) used for this project was the ATMega32U4-A. This microcontroller is perfect for this application, as this project did not require a large amount of processing power. It boasts a humble 44 pins, 24 of which can be used as bi-directional I/O ports for the signals sent by our key presses. This design could easily be scaled up to a fully sized keyboard matrix and this MCU would still have pins to spare. It also has 32 KBs of flash memory with is more than enough for the firmware that will be flashed onto it.

### Auxillary Units 

The rest of the schematics include the following:
* 3x4 keyboard matrix created using diodes as switches
* Decoupling capacitors to filter out electrical noise
* A crystal which controls the speed of the MCU
* A reset button for testing purposes
* The USB 2.0 circutry
  
|Keyboard Matrix|Decoupling Capacitor, Crystal, Reset Button, USB connection|
-----------------------|-------------------------------------------------------------
<img width="100%" alt="image" src="https://github.com/Lyam-Milbury/custom-keeb-pcb/assets/71610885/e8ed98e2-0e7c-4e45-927e-37bb78382463"> | <img width="100%" alt="image" src="https://github.com/Lyam-Milbury/custom-keeb-pcb/assets/71610885/a48ad6ef-51ce-4e9c-b2bf-ddbfd2240428">

## PCB Designs

### Version 1 
<p align="center">
 <img width="529" alt="MacropadV1" src="https://github.com/Lyam-Milbury/custom-keeb-pcb/assets/71610885/7fe2130b-4112-43df-bbb9-b840eb43114f">
</p>
This was the first design I came up with. As soon as I finished it, I already knew I wasn't too proud of it. The traces were messy and the placement of some of the components wasn't optimal.

### Version 2
<p align="center">
 <img width="513" alt="MacropadV2" src="https://github.com/Lyam-Milbury/custom-keeb-pcb/assets/71610885/cf8f9bfc-c3f3-49e2-adeb-f1813f5d90f7">
</p>
Version two is the latest design. I moved the MCU and the reset switch to allow connections to be traced with more ease. IMore care in laying out the traces, opting for bus-style traces wherever I could. while keeping in mind that some traces needed to be intentionally isolated to prevent crosstalk. I knew this design would be good enough for production, so I also added final touches, such as the drill holes in the bottom corners, the ground fill in the top third to protect sensitive components from electrical noise, and a print of a little dude pressing the reset button.


## TODOs & Note
The design has already been sent to a manufacturer and is in production as I'm typing this. Once I receive the boards, if everything works as expected, here are the next steps I'll be taking to complete this project:
1. Solder components to the PCB
2. Use QMK to write custom macros
3. Design & 3d print enclosure

Designing this PCB has been a blast. I'm a computer engineer by education but I took more of a software-oriented route for my trade. This has reminded me of how much fun hardware design can be and will not be the last one design.

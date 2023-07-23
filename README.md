# XY_Pen_Plotter
<p align="center">
  <img src="https://github.com/Ruthvik-1411/XY_Pen_Plotter/blob/main/assets/v3.01.jpg" height=350 width=450>
</p>
<p>The pen plotter is a drawing machine capable of creating complex designs, patterns, and artworks on paper or flat surfaces. It a type of CNC (Computer Numerical Control) machine designed to draw or sketch images using a pen or similar writing instrument. It operates on two or more axes, allowing precise control over the movement of the pen across the drawing surface. The pen plotter can execute complex patterns and designs with exceptional accuracy, making it an excellent tool for both artistic and technical applications.This repository contains all the information and resources you need to build your very own pen plotter.</p>

### Key Features
* <b>Low cost:</b> The structure of the pen plotter is made mostly out of wooden blocks and connected using available screws. The base for linear movement is achieved using linear rods that are extracted from a mini drafter. The electronic part of the plotter also uses 28byj-48 steppers which are the cheapest steppers. Most of the components of the plotter are just things lying around in the house.
* <b>Single Stepper Motor for X-Axis Movement:</b> The X-axis movement is managed by a 28byj-48 unipolar stepper motor, providing precise control over the horizontal positioning of the pen.
* <b>Two Stepper Motors for Y-Axis Movement:</b> The pen plotter features two stepper motors that work in parallel to control the movement of the pen along the Y-axis. This enables smooth and synchronized motion for creating detailed drawings.
* <b>GT2 Timing Belts for Enhanced Performance:</b> The plotter uses GT2 timing belts, known for their reliability and reduced backlash, ensuring consistent and accurate drawings.
* <b>Customizable Software Control:</b> The pen plotter is compatible with popular CNC software like GRBL (G-code sender) and can be easily controlled through a computer interface.

## Tools and Materials
* Wooden blocks (54x7 - 2, 40x7 - 2) any size to make a |=| structure.
* Smooth linear rods (from mini drafter) - 6 (2 along x, 4 along y in parallel)
* Rollers or linear bearings that allow for linear motion on rods.
* screws and other misc components for mechanical support
* 28byj-48 uniploar steppers - 3
* ULN2003 stepper motor driver - 3
* GT2 timing belt 1 mtr - 3
* 16 teeth 5mm bore timing pulley - 6(3 at motor shaft, 3 at other end)
* SG90 servo motor
* Limit switches - 3
* Arduino Uno R3 and jumper wires
* Capacitor 100nF (104) - 2
* Resistor 4.7K&#8486; (4k7) - 2
* USB cable and adapter (5V, ~1A) 

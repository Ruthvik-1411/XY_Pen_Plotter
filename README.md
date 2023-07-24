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
* Prototype board or breadboard
* USB cable and adapter (5V, ~1A) 
* Drilling tool would be handy
* Marker or pen and paper

## Hardware specifications and assembly
<p align="center"> <img src="https://github.com/Ruthvik-1411/XY_Pen_Plotter/blob/main/assets/v2.01.jpg" height=300 width=350><img src="https://github.com/Ruthvik-1411/XY_Pen_Plotter/blob/main/assets/bot.jpg" height=300 width=350></p>

* The wooden blocks can be made into any dimension but it should have 4 units. Two units between which the vertical rods are fixed at each end. To maintain the structure and a constant distance between the units, two smaller blocks are attached. If not they become a parallelogram shape. By adding intermediate blocks it gives a rectangular shape with fixed shape. It is a shown in the figure above.
* To move on the linear rods along x,y direction three blocks are placed. Two pairs of linear rods run on each side parallely (y-axis) as seen in the figures above. Two wooden blocks are placed on each side(on the rods) and between these two parallel blocks runs the third pair of linear rods responsible for x motion. On these rods for x axis lies the third block which has the pen lifting mechanism.
* The linear motion can be achieved by using linear bearings or similar kind of structure. Initially I tried using wheels similar to the way train runs on tracks. One challenge of this is the wheels have a small point of contact and they tend to bend toward the motion. The situtation can be better understood by considering a cycle is moving on a linear rod, when u apply incredible force on one end say back tire, the front tire will rise up. Since the blocks sit on top of these small wheels when they are pulled to one side, the other edge rises up. When the wooden block on the y-axis bend towards one side the entire x-axis blocks which are on this also bend in that direction. This bends the pen lifter and produces bad results. So I used bearings which are around the linear rod rather that wheels that only stay on top of the rods. When they are around the rod the blocks are bound to the rod. Unlike before there will be no motion upwards or downwards.
* Since there are two motors for y axis movement, they are fixed on one end. The third motor responsible for x motion stays on one of the moving blocks placed on y axis rods. The 5mm pulley is tightened to the shaft of each motor and a pulley is kept on the other end around a linear rod. The GT2 timing belt runs between the shaft of motor and freely moving pulley on the other end. The two ends of the timing belt is fixed around two screws on the moving blocks as shown in the below images.
<p align="center"> <img src="https://github.com/Ruthvik-1411/XY_Pen_Plotter/blob/main/assets/v2.1.jpg" height=300 width=350><img src="https://github.com/Ruthvik-1411/XY_Pen_Plotter/blob/main/assets/v2.03.jpg" height=300 width=350></p>

* A simple handmade pen lifter is made using some mechanix I had with me. When servo moves a certain angle i.e. when the shaft of the servo rises it lifts the pen holder and keeps it there. When returned to zero the spring pushes the pen holder downwards. The pen holder and <b>pen lifting mechanism was one of the most complex part of the plotter</b>. Many pen holders and pen lifting mechanisms are available online, but they are quite expensive, so a simple mechanism was developed. I could not add a detailed picture of this mechanism as all the parts are fixed and removing them will make it difficult to mount again. But by watching the demo video and images you can get an idea of how it works and the mechanism.
* Now the motion is made possible along x,y directions and even the pen lifting mechanism is established and the plotter can move around in any direction it wants and actuate the pen accordingly. But one important aspect of the plotter is that it has a restricted space for movement. It should move only between the motor and its opposite. The software can give instructions to the motors to move around, but it is not aware of the <b>limits</b> of motion. For the system to understand the physical limits of the world limit switches are added at the physical ends of the plotter. 
  * There are two approaches to add the limit switch, one is the home position approach where limit switches are placed at the starting position of the block. The user can then give soft limits i.e the maximum distance the plotter can travel in a given direction. If the other end is 300mm far away then 300 will be the soft limit in that direction. The software stops the motor after it moves that distance away from the start.
  * The other is end of travel approach, where limit switches are placed on the other end of the motor and when the block hits the switch, the software understands that it has hit the physical end on the other side and stop. Without the limit switch the blocks will either ram straight into the motor or worse, damage the belt after getting stuck on other end.
* The plotter can now truly travel in the xy space <b>safely</b>. The wiring of the switches and motors can be done by connecting the motor to the driver and powering the pins. In this setup the block's home position is the far end, opposite of the motor and the motor rotates in the direction such that the blocks move towards the motor. This makes the wiring easy as limit switches are placed near motor. The control pins are connected according to the direction of motion that is required, by reversing the control pins the direction can be reversed. In this setup, the y axis steppers should move in opposite directions for the plotter to move in one direction i.e. the belt is fixed in such a way. Both the y axis steppers should actuate same time, so the control pins are combined and a single set of pins is powered.
## Software specifications and setup
* Now the hardware part is all done. All that is left for the system to do is to control the motors(their direction, speed), monitor the limit switches and actuate the servo that handle the pen lifting. The obvious approach is to use a microncontroller to take care of these things. Arduino is the first thing that comes to mind. Code can be made to monitor the limit switched and by following some examples you can run the steppers as well. The code to do the action as simple as drawing a rectangle become quite large. This is because the stepper is controlled by moving a certain number of steps. This rotates the shaft by certain angle and thus the gt2 belt traverse some distance. A correlation between number of steps and distance (in real world) should be calibrated and added into the code. The code should run the motors for some duration, make changes and so on. This makes the code complex as hell. That's where something called gcode comes in.
* G-code (Geometric code) is a programming language for cnc machines. It is used to tell the machine what to do and how to do by using certain commands and dividing complex shapes and works into smaller tasks. Gcode commands looks like this G## X## Y## F##.
    * G## - for specific action, move in straight line(linear interpolation), circular interpolation clockwise etc
    * X##,Y## - set the end position
    * F## - feed rate(speed)
* The machine performs these actions based on a G code. Where do we get the Gcode from? Well, first let's say you want to draw something, say your name or an image. There is something called <a href="https://inkscape.org/">inkscape</a>. It is like MS paint but better suited for cnc purposes. An image or text can be drawn in the inkscape. Now for a cnc machine or an xy plotter everything you draw or write is finally a path that the actuator has to move along. Inkscape can convert the drawing into a path as a combination of linear,clock, anti clock wise and other movements. You can select the drawing and convert into path by choosing path->object to path option. This path that the inkscape generated should be converted to g code. It should also add in the factor of the pen lifting.
* <a href="https://github.com/arpruss/gcodeplot/releases">G code plot</a> is an inkscape extension which can do this for us. Dowload the zip file from here and extract it. To add this extension you should copy the contents of the gcodeplot folder and paste it at "C:\Program Files\Inkspace\share\inkscape\extensions". The location can vary but this should be in the main Inkscape folder. Now open the inkscape, create the drawing, convert the object to path and choose save as ".gcode". The gcode plot now asks for some options which can be configured accordningly, but best left the same. The importance of gcodeplot doesn't lie on converting into gcode but allowing the user to add a servo lift action. When you click save as .gcode, a gcodeplot window pops up. In the cutting setting you can add the pwm signal that the servo requires for lifting. Lift up and Lift down commands can be given. M05 means "zero deg" and M03 xxx(0-255) corresponding to 0-180 deg rev. Since the gcode should also include the lift commands these commands are placed wherever required.
  * One thing that should change is that the drawing that was first made should be made upside down. This is because the inkscape origin is at top left. But gcodeplot's origin is at bottom left. By converting the drawing upside down, the machine can draw it exactly else the result will be an upside down copy. The process is same for other steps.
*  We can now convert our drawings into gcode. How can we tell the motors or our controller to perform actions based on this? That's where <a href="https://github.com/grbl/grbl">GRBL</a> comes in. GRBL is an open source software or firmware which enables motion control for CNC machines. We can easily install the GRBL firmware to an Arduino and so we instantly get a low cost, high performance CNC controller. The GRBL uses G-code as input, and outputs motion control via the Arduino. GRBL is the interpretor that converts the gcode into the motor control and monitoring limit switches. GRBL is designed for arduino boards. There are specific pins that the motors, switches should be connected to. But the official GRBL is designed for bipolar stepper motors with cnc controllers and driver boards. The setup that is made uses unipolar 28byj-48 stepper motors and also has servo motor. Official <a href="https://github.com/grbl/grbl">GRBL</a> isn't developed for this setup. We have to improvise and look for a firmware that suits our setup.
*  Thankfully someone has painfully gone through all the code in the official grbl and made changes that fit our setup. This repository made by ruizivo <a href="https://github.com/ruizivo/GRBL-28byj-48-Servo">https://github.com/ruizivo/GRBL-28byj-48-Servo</a> can be used for this setup. This is like a library that can be added to arduino and upload as a sketch into arduino uno. The zip file can be downloaded and the grbl folder can be copied into the the libraries of arduino software. The grbl folder has some c and header files. Some files need to be changed for the software to work. The <a href="https://github.com/Ruthvik-1411/XY_Pen_Plotter/tree/main/grbl"> grbl</a> folder that is available in this repo has all the changes that are needed for the setup to work. It can be pasted into the library folder of arduino software and it's done.
*  The GRBL firware that is suited for this setup can be uploaded into the arduino by going to examples, scrolling down and choosing grblUpload file. The file is also available in this repo. Now the arduino can interpret the gcode that it receives. Now we have the gcode and an arduino microcontroller that can understand the gcode and actuate the stepper motors,servo motor and monitor the limit switches. But how can we send the gcode to arduino? We have <a href="https://winder.github.io/ugs_website/download/">UGS</a> (Universal Gcode Sender), an open source and widely used software compatible with many cnc machines that are available. UGS takes gcode as an input and sends tha gcode to arduino controller at specific baud rate. GRBL uses a standard 115200 buad rate to communicate with arduino. But UGS has to be configured for each machine. Once configured it can work with any drawing and task at hand.
*  UGS requires the grbl to be installed on the controller beforehand. Now you can connect the arduino and connect to the arduino from ugs. You can follow the setup wizard that's built-in ugs or manually change the settings. Some major configuration that are required are :
    *  Setup Wizard:
        * After connecting the controller and making the connections with motors and switches accordingly, you can proceed with the wizard. You can check the direction of rotation of motor and change the software postive direction or physically reverse the control pins.
        * Now the software should be calibrated according to the movement made in physical world. Stepper motors move in steps and software has control over number of steps to rotate, but it should be related to the distance to be moved. So steps/mm should be calibrated. Initially 250 steps is considered as 1mm in software. Grbl moves 250 steps and respective distance travelled by the blocks should be taken to calibrate the software. The estimate is given so that 1mm in software will equal 1mm in physical world.
        * Limit switches should be checked by manually triggering them and buttons change in colour or create an alarm. The switches action can also be inverted depending on the circuit.
        * Homing option can be enabled to let the system check its working. It can be skipped if there is any error in software.
   * Manual Commands:
        *  When arduino is connected there are a set of commands displayed with $ sign infront of them. Each command has their own significance. For more information you can check this <a href="https://honingmill.fandom.com/wiki/Configuring_Grbl_v0.9">wiki</a>. Some commands that should be changed are $5,20,21,24,25,100,101,110,111,130,131.
        *  $5 - to invert limit switch(1),$20 - to activate soft limits(max travel)(1),$21 - to activate hard limit(1),$24 - to set homing speed(speed,if homing is active),$25 - to set homing seek speed,$100,101 - the steps/mm calibrated previously for x,y,$110,111 - the maximum speed of x,y steppers,$130,131 - max travel from end to end of x,y axis in mm. The changes can be made by entering $x=value and hitting enter. These change happen when setup wizard is used as well.
     *  After configuring the GRBL paramaters for the setup, all you have to do is send the gcode to arduino and the software takes care of the rest.
* Now that arduino can understand what to do and how to do it all it needs is the gcode from ugs. The gcode that is complied from gcode plotter can be loaded into the ugs and the drawing can be seen in the visualizer. The setup looks like below.
<p align="center"> <img src="https://github.com/Ruthvik-1411/XY_Pen_Plotter/blob/main/assets/actual_temp1.png" height=353 width=350><img src="https://github.com/Ruthvik-1411/XY_Pen_Plotter/blob/main/assets/snip1.jpg" height=370 width=580></p>

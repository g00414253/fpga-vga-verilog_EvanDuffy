---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: demo
---
System on Chip Design & Verification FPGA VGA Driver Project to display graphics on a 640x480 display,Using Vivado and Verilog.

## **Template VGA Design**
### **Project Set-Up**
The project set-up involes developing a FPGA VGA driver by using Vivado. Within the project the target is an Artix-7 FPGA (part xc7a35tcpg236-1) by using Verilog as the design language.The synthesis and implementations have been run successfully with some warnings, and the design has been verified with no fails in the endpoints in the timing analysis. This project set up can be used to create custom VGA imaging.


<img src="https://raw.githubusercontent.com/g00414253/fpga-vga-verilog_EvanDuffy/main/docs/assets/images/ProjectSummary.png">
<!--### **Template Code**
Outline the structure and design of the Verilog code templates you were given. What do they do? Include reference to how a VGA interface works. Guideline: 2/3 short paragraphs, consider including screenshot(s).
### **Simulation**
Explain the simulation process. Reference any important details, include a well-selected screenshot of the simulation. Guideline: 1/2 short paragraphs.
### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.
### **Demonstration**
Perhaps add a picture of your demo. Guideline: 1/2 sentences. --!>

The Verilog code templates in the project form the basics for generating and displaying a 640x480 VGA Output. The templates include modules for VGA synchronization signals,RGB signal generation, and memory initialization for image data.The design maintains to VGA timing standards, ensure compatiability with VGA displays.
### Simulation
The simulation process within Vivado is used to validate the functionaility of the desing before implementing the hardware.By running the Verilog testbench in Vivado, the timing of synchronization signals and the correct rendering of pixel data can be observed.*The image below is of the waveform output which can be used to verifiy the designs behavior.* 

<img src="https://raw.githubusercontent.com/g00414253/fpga-vga-verilog_EvanDuffy/main/docs/assets/images/Simulation.png">

The image shows the Vivado simulation, validating the design's functionality by displaying signal waveforms like `clk`, `red`, `green`, and `blue`. This ensures correct timing and behavior before hardware implementation.

### Synthesis
The synthesis process translates the Verilog HDL into a hardware netlist, ready for implementation on the FPGA. Post-synthesis, the design undergoes implementation to map the logic onto the FPGA's fabric, and a successful timing report confirms its readiness for deployment.

### Demostration
<a href="https://raw.githubusercontent.com/g00414253/fpga-vga-verilog_EvanDuffy/main/docs/assets/images/Demo_Vid.webm" target="_blank">Video Demonstration</a>

## **My VGA Design Edit**
For my own VGA Design i will be improving on the basic flashing colours test bench. My plan is to change the colours that are flashing while also improving the transitons by fading into the next colour instead of an instant swap. I will also add three buttons to interact with the display. One to increase the transtion speed, one to decrease the transiton speed and one to reset the speed by to its default pace.
### **Code Adaptation**
To implement buttons that would change the display i had to make edits to mulitple files.

#### *-Master.Xdc File Changes*
<img src="https://raw.githubusercontent.com/g00414253/fpga-vga-verilog_EvanDuffy/main/docs/assets/images/Basys3_Master.xdc.png">
The above snippet of code from the projects constraint file which in Vivado is a ".xdc file", which is used to map the physical pins of the FPGA to the logical signals in the design.This setup will provide proper communication between design and components by defining pin numbers and the volatge standards.

The Code above Configures a Clock Signal,a switch (rst) ,two push buttons (btn_up, btn_down) and three LEDS (led[0], led[1], and led[2]).



#### *-Input/Output and Registers declerations*
<img src="https://raw.githubusercontent.com/g00414253/fpga-vga-verilog_EvanDuffy/main/docs/assets/images/ColourCycleDeclerations.png">
The code above has been taken from the ColourCycle Module, in this section the Inputs/Outputs and Registers have been declared.

#### 1. Inputs:

clk: Clock signal.
rst: Reset signal.
btn_up: Button to increase speed.
btn_down: Button to decrease speed.
Outputs:

#### 2. Outputs:

red, green, blue: Outputs for controlling the RGB color channels (each 4 bits wide).
led: Debugging LEDs (3 bits wide).
Internal Registers:

#### 3. Internal Registers:

colour: A 12-bit register representing the current RGB color.
fade_counter: A 32-bit counter for managing the color fading speed.
speed: A 32-bit register to control the speed of color changes.
direction: A 1-bit register indicating fading direction (0 = down, 1 = up).



#### *-Colour Fading Logic*
<img src="https://raw.githubusercontent.com/g00414253/fpga-vga-verilog_EvanDuffy/main/docs/assets/images/ColourFadingLogic.png">
This block controls the fading colour logic,enabling smooth transitions between the colour changes by incrementing or decrementing the colour value over time.

#### Reset Logic:
On a reset (rst):
The fade_counter is set to 0.
direction is set to 1 (indicating the initial fading direction is upward).

The colour starts at 12'b1111_0000_0000 (a full red value in 12-bit RGB).
Fade Counter:

The fade_counter is incremented at each clock cycle.
When it reaches the speed threshold, it resets to 0 and triggers a color update.

#### Fading Up: 
When direction is 1:
The color value (colour) is incremented.
If the color reaches the maximum value (12'hFFF), the direction switches to fading down (direction = 0).

#### Fading Down:

When direction is 0:
The color value is decremented.
If the color reaches 0, the direction switches to fading up (direction = 1).

#### Speed Control:

The fading speed is controlled by comparing fade_counter to the speed register. A higher speed value results in slower color changes, while a lower value makes them faster.


#### *-Speed Control Logic*
<img src="https://raw.githubusercontent.com/g00414253/fpga-vga-verilog_EvanDuffy/main/docs/assets/images/SpeedControlLogic.png">
This code snippet implements speed control logic for adjusting the fading speed of an RGB color controller based on button inputs. 
Pressing btn_up speeds up the fading.
Pressing btn_down slows down the fading.
The default speed provides a balanced starting point, and the step sizes for adjustment (250000 and 500000) ensure noticeable changes without abrupt jumps.

#### Reset Logic:

On reset (rst):
The speed register is set to a default value of 32'd5000000, which corresponds to a medium fading speed.
Button Logic for Speed Adjustment:

#### Increase Speed (btn_up):

If the btn_up button is pressed and the speed value is greater than 32'd50000:
The speed value is decremented by 32'd250000, resulting in faster color fading.
#### Decrease Speed (btn_down):

If the btn_down button is pressed and the speed value is less than 32'd30000000:
The speed value is incremented by 32'd500000, resulting in slower color fading.

#### Conditions:

The speed value is clamped within a range:
A minimum limit of 32'd50000 prevents the fading from becoming too fast.
A maximum limit of 32'd30000000 prevents it from becoming excessively slow.
Summary:
This logic dynamically adjusts the fading speed based on user input:


### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.
### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.
### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.

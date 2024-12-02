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
#### *-Input/Output and Registers declerations*
#### *-Colour Fading Logic*
#### *-Speed Control Logic*


### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.
### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.
### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.

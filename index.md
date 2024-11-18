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
### **Template Code**
<!-- Outline the structure and design of the Verilog code templates you were given. What do they do? Include reference to how a VGA interface works. Guideline: 2/3 short paragraphs, consider including screenshot(s).
### **Simulation**
Explain the simulation process. Reference any important details, include a well-selected screenshot of the simulation. Guideline: 1/2 short paragraphs.
### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.
### **Demonstration**
Perhaps add a picture of your demo. Guideline: 1/2 sentences. --!>

The Verilog code templates in the project form the basics for generating and displaying a 640x480 VGA Output. The templates include modules for VGA synchronization signals,RGB signal generation, and memory initialization for image data.The design maintains to VGA timing standards, ensure compatiability with VGA displays.
#Simulation


## **My VGA Design Edit**
Introduce your own design idea. Consider how complex/achievabble this might be or otherwise. Reference any research you do online (use hyperlinks).
### **Code Adaptation**
Briefly show how you changed the template code to display a different image. Demonstrate your understanding. Guideline: 1-2 short paragraphs.
### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.
### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.
### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.

## **More Markdown Basics**
This is a paragraph. Add an empty line to start a new paragraph.

Font can be emphasised as *Italic* or **Bold**.

Code can be highlighted by using `backticks`.

Hyperlinks look like this: [GitHub Help](https://help.github.com/).

A bullet list can be rendered as follows:
- vectors
- algorithms
- iterators

Images can be added by uploading them to the repository in a /docs/assets/images folder, and then rendering using HTML via githubusercontent.com as shown in the example below.

<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/VGAPrjSrcs.png">

# 3T1D [3 Transistor 1 Diode] Capacitorless DRAM

This repository presents the design of Differential End CSVCO implemented using Synopsis Custom Compiler on 28nm CMOS Technology.

# Table of Contents
 * [Introduction](#Introduction)
 * [Literature Survey on Memories](#Literature-Survey-on-Memories)
 * [3T1D DRAM Design](#3T1D-DRAM-Design)
 * [Reference Circuit](#Reference-Circuit)
 * [Reference Waveform](#Reference-Waveform)
 * [Tools Used](#Tools-Used)
 * [Netlist of the Circuit](#Netlist-of-the-Circuit)
 * [Observations](#Observations)
 * [Author](#Author)
 * [Acknowledgements](#Acknowledgements)
 * [References](#References)


# Introduction:

Memories play an essential role in design of any electronics design where storage of data is required. Memories are used to store data and retrieve data when required. Read Only Memory (ROM) and Random Access Memory (RAM) are two types of memories used in modern day architectures. Random Access Memory is of two types Dynamic Random Access Memory
(DRAM) and Static Random Access Memory (SRAM). SRAM is static in nature and faster as compared to DRAM. SRAM is expensive and consume less power. SRAM have more transistors
per bit of memory. They are mostly used as cache memories. DRAMS on the other hand are dynamic in nature and slower as compared to SRAM. DRAM are expensive and consume more
power, they require less transistor per bit of memory. They are mostly used as main memories. DRAM is widely used for main memories in personal and mainframe computers and engineering workstation. DRAM memory cell is used for read and write operation for single bit storage for circuits. A single DRAM cell is capable of storing 1 bit data in the capacitor in the form of charge. Charge of the capacitor decreases with time .Hence refresh signals are used to refresh the data in the capacitor. When a read signal reads the data it refreshes it as well. Many different cell designs exist for modern day DRAM cell. These designs are differentiated by the no. of transistors used in their designing. As the no. of transistors increase, power dissipation also increases. DRAM is one of the most common and cost efficient random access memory used as main memory for workstations. The charge stored in memory cell is time dependent. For high density memories DRAM cell with low power consumption and less area are preferred.

# Literature Survey on Memories:

Volatile memories enclose mainly two different types, static memories known as SRAM (Static RAM) and dynamic memories, DRAM (Dynamic RAM). The main difference between them is the time while they can store the information without any loss. SRAM on one hand, keep the information as long as they are powered. Only if the power is unplugged their content is lost. On the other hand, DRAM cells store the data for a short period of time, around milliseconds. To avoid losing data with time, DRAM takes advantage of block known as DRAM controller, which permits the memory to be refreshed before the data is corrupted and therefore irrecoverable. So, there exists a way to keep the data safe on a DRAM.
The advantage of DRAM compared to SRAM is that they consume less area. This reduced surface leads to memory chips with larger storage capacity and lower cost.

# 3T1D DRAM Design

Many different cell designs exist for modern day DRAM cell. These designs are differentiated by the no. of transistors used in their designing. As the no. of transistors increase, power dissipation also increases. In this paper, 3T1D DRAM cell is designed and analyzed. These DRAMs have an advantage over SRAM, that is, their resistance to process variation. This feature helps it to be used at low feature sizes. Another advantage of 3T1D DRAM is that it does not slow down as its size is scaled down. 3T1D DRAM uses the gated diode instead of capacitor to store the data value. The absence of a capacitor in it provides a significant reduction in power consumption as compared to several DRAM cell designs.


<p align="center">
<img src="Project Images/3T1D Cell.jpg"></br>
  Fig 1: 3T1D DRAM Cell
</p>
Figure above represents a 3T-1D DRAM cell used for reference for designing the circuit at a transistor level.
The basis of the storage system is the charge placed in node S, written from BL write line when T1 is activated. Consequently, it has a DRAM cell nature, but it allows a non-destructive read process (a clear advantage over 1T1C memories) and high performance read and writes operation, comparable to 6T.With T1 and T3 transistors as accessing devices, the whole cell is composed by four transistors of similar size to the corresponding of 6T. This implies a more compact cell structure. In order to write the cell at the BL write line level it is only required to activate T1 through the WL write line. Hence, the S node stores either a 0 or a VDD-Vth voltage depending on the logic value. This voltage results in the accumulation of charge at the gate of devices D1 and T2.A key aspect of the 3T1D memory cell is that the capacitance of the gated diode (D1) when Vgs is above Vth is significantly higher with respect to lower voltages, because there is a substantial amount of charge stored in the inversion layer. In order to read the cell, the read bit line BL read has to be previously pre-charged at VDD level. Then T3 is activated from WL read line. If a high (1) level is stored in S, transistor T2 turns on and discharges the bit line. If a low (0) level is stored in S, transistor T2 does not reach enough conduction level. The objective of the gated diode D1 is to improve Read Access Time. When a high (1) level is stored in S, D1 connected to WL read line causes a boosting effect of the voltage level in node S. The voltage level reached at node S is close to Vdd voltage causing a fast discharge of the parasitic capacitance in BL read. If allow (0) level is stored, transistor T2 keeps turned off.

# Pre-Layout Schematic and Simulation Waveform:

## Reference Circuit:

Fig 2 shows the transistor-level reference schematic of the DRAM cell.
<p align="center">
  <img src="Project Images/Reference Circuit.jpg"></br>
  Fig 2: Reference Circuit Diagram
</p>
<p>
This 3T-1D DRAM cell is very different from all others DRAM cell. Its key feature is that it provides non-destructive read operation and also its speed of operation is high, it gives less leakage power and is more stable than the SRAM and other capacitor-based DRAMs. Variation only affects the operating frequency of the cell,making it much more robust to process variations than the 6T design. The figure above shows us the transistor- level reference schematic of the cell. 

To write to the cell, the write bitline is charged to the value we wish to store in the cell, and the write wordline is strobe. To read from the cell, the read bitline is precharged high and the read wordline is strobe. If a 1 is stored in the cell, transistor T2 turns on and the bitline discharges. The key to fast access times is the gated diode, which is tied to the read wordline. When a 1 is stored in the cell, the diode provides a ‘boosting’ effect to the value at the storage temporarily giving it a value close to (and sometimes greater than) Vdd, allowing T2 to turn on quickly and discharge the bitline. When a 0 is stored in the cell, the capacitance of D1 is smaller and little to no voltage boosting occurs, keeping T2 turned off. Because the 3T-1D is a dynamic memory, the value at the storage node[s] leaks away with time.

## Reference Waveform:
A reference waveform expected at the end of the simulation and analysis of the above schematic is shown in the figure below. 
The waveform includes 5 plots [in the order of appearance] on the X Axis - 
1) Bitline
2) WRCLK [Write Signal]
3) Vc [Storage Node]
4) RCLK [Read Signal]
5) DRAMOP [Read Signal Output]
<p align="center">
  <img src="Project Images/Reference Waveform.jpg"></br>
  Fig 3: Pre-Simulation Waveform
</p>
<p>
	
# Tools Used:

<b>• Synopsys Custom Compiler:</b></br>
&emsp;The Synopsys Custom Compiler™ design environment is a modern solution for full-custom analog, custom digital, and mixed-signal IC design. As the heart of the Synopsys Custom Design Platform, Custom Compiler provides design entry, simulation management and analysis, and custom layout editing features. This tool was used to design the circuit on a transistor level.

<b>• Synopsys Primewave:</b></br>
&emsp;PrimeWave™ Design Environment is a comprehensive and flexible environment for simulation setup and analysis of analog, RF, mixed-signal design, custom-digital and memory designs within the Synopsys Custom Design Platform. This tool helped in various types of simulations of the above designed circuit.

<b>• Synopsys 28nm PDK:</b></br>
&emsp;The Synopsys 28nm Process Design Kit(PDK) was used in creation and simulation of the above designed circuit.

# Post-Layout Schematic and Simulation:

## Schematic:

### Transistor-level Schematic:
Keeping in mind the Reference circuit diagram above, the schematic of the DRAM was designed at a transistor-level using the 28nm PDK library on the Custom Compiler Schematic Editor.
<p align="center">
  <img src="Project Images/3T1D DRAM Schematic.jpg"></br>
  Fig. 4: 3T1D DRAM Schematic
</p>

### Symbol:
Initially, after designing the schematic, it was then converted to a symbol so as to be used for further reference while designing the testbench for the same.
<p align="center">
  <img src="Project Images/symbol.jpg"></br>
  Fig. 5: Symbol Design
</p>

### Testbench:
The Testbench has been created using the Symbol designed previously and the Vpulse and Vsupply values have been set.
<p align="center">
  <img src="Project Images/Testbench Schematic.jpg"></br>
  Fig. 6: Testbench Design


## Simulation:

### Transient Analysis:
After creating and saving the schematic go to 'Tools' and open 'Primewave' to start the simulation. In the Primewave select the 'model file' i.e the '28nm PDK's .lib file presentin the HSPICE folder. After this select the 'tran' analysis in the analysis window and give the 'Start', 'Stop', and 'Step Size' parameters and save it. Then add the outputs which needs to be plotted by selecting the nets on the schematic.</br> 
Then go to 'Simulations -> Netlist and Run' to generate a netlist and run the simulation to get the below output.
<p align="center">
  <img src="Project Images/Trans Output.jpg"></br>
  Fig. 7: Transient Analysis of the Testbench
</p>
The above graph has a Vsupply value of 1.2V and a total time period of 50ns.

## SPICE Netlist:

Refer to the netlist of the 3-Stage Differential End CSVCO here: <a href='differential_CSVCO.cir.out'>Netlist</a>
Refer to the netlist of the 5-Stage Differential End CSVCO here: <a href='Differential_csvco_5stage.cir.out'>Netlist</a>

# Observations:
• Maximum frequency obtained for Supply voltage of 1.2V in 3-Stage Differential End CSVCO is around 22 GHz</br>
• As expected the bias current flowing into the delay stages is increasing as the the control voltage is increasing.</br>
• Also as expected the VCO's output frequency is increasing as the control voltage is increasing.</br>
• It can also be observed as the number of delay cells increase the frequency of oscillation decreases.</br>
• One other thing to be noted is that in the parametric sweep we can see that the 5 stage VCO's graph is more linear as compared to the 3 stage VCO's graph which means that the 5 stage VCO is more stable and has better phase SNR.</br>

# Author:
• Trinath Harikrishna, B.Tech(ECE), SRM Institute of Science and Technology, Kattankulattur, Chennai-603203.

# Acknowledgements:
• <a href='https://www.iith.ac.in/events/2022/02/15/Cloud-Based-Analog-IC-Design-Hackathon/'>Cloud Based Analog IC Design Hackathon</a></br>
• <a href='https://www.synopsys.com/'>Synopsys India</a></br>
• <a href='https://www.vlsisystemdesign.com/'>VLSI System Design (VSD) Corp. Pvt. Ltd India</a></br>

# References:
[1] B. Razavi. A 2-GHz 1.6-mW phase-locked loop. IEEE Journal of Solid-State Circuits 1997; 32 (5): 730-735.</br>
[2] R.Rahul and R.Thilagavathy, "A low phase noise CMOS voltage-controlled differential ring oscillator,"ICCICCT,2014

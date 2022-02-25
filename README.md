# 3T1D Capacitorless DRAM using 28nm CMOS Technology

Featured in this repository is the Design and Analysis of a 3T1D Capacitorless DRAM using the 28nm Process Design Kit implemented on the Synopsys Custom Design Platform.

# Table of Contents
 * [Introduction](#Introduction)
 * [Literature Survey on Dynamic Memory](#Literature-Survey-on-Dynamic-Memory)
 * [3T1D DRAM Design](#3T1D-DRAM-Design)
 * [Reference Schematic and Simulation](#Reference-Schematic-and-Simulation)
 * [Tools Used](#Tools-Used)
 * [Schematic Design and Simulation](#Schematic-Design-and-Simulation)
 * [SPICE Netlist](#SPICE-Netlist)
 * [Observations & Conclusion](#Observations-&-Conclusion)
 * [Author](#Author)
 * [Acknowledgements](#Acknowledgements)
 * [References](#References)


# Introduction:

Memories play an essential role in design of any electronics design where storage of data is required. Memories are used to store data and retrieve data when required. Read Only Memory (ROM) and Random Access Memory (RAM) are two types of memories used in modern day architectures. Random Access Memory is of two types Dynamic Random Access Memory
(DRAM) and Static Random Access Memory (SRAM). SRAM is static in nature and faster as compared to DRAM. SRAM is expensive and consume less power. SRAM have more transistors
per bit of memory. They are mostly used as cache memories. DRAMS on the other hand are dynamic in nature and slower as compared to SRAM. DRAM are expensive and consume more
power, they require less transistor per bit of memory. DRAM is widely used for main memories in personal and mainframe computers and engineering workstation. DRAM memory cell is used for read and write operation for single bit storage for circuits. For high density memories DRAM cell with low power consumption and less area are preferred. The advantage of DRAM compared to SRAM is that they consume less area. This reduced surface leads to memory chips with larger storage capacity and lower cost.

# Literature Survey on Dynamic Memory:

The two types of volatile memories, that is, SRAM (Static RAM) and DRAM (Dynamic RAM) have one major difference between them which being the time they can store the information without any loss. SRAM on one hand, keep the information as long as they are powered. Only if the power is unplugged their content is lost. On the other hand, DRAM cells store the data for a short period of time, around milliseconds. To avoid losing data with time, DRAM takes advantage of block known as DRAM controller, which permits the memory to be refreshed before the data is corrupted and therefore irrecoverable. So, there exists a way to keep the data safe on a DRAM.

Dynamic random access memory (DRAM) is a type of memory that stores each bit of data in a separate capacitor within an integrated circuit. The basic DRAM cell consists of one transistor and one capacitor. Due to the leakage of the capacitors, the information eventually fades unless the capacitor charge is refreshed periodically. This refresh requirement makes DRAM a dynamic memory as opposed to SRAM (Static random access memory). Recently the capacitorless DRAMs have attracted attention, due to the lack of the capacitor and the problems associated with the scaling of the capacitor, and due to its ability to achieve higher device density.

Moreover, the scaling of the conventional 1Transistor/1Capacitor (1T/1C) DRAM is becoming increasingly difficult, in particular due to the capacitor which has become harder to scale, as device geometries shrink. Apart from the problems associated with the scaling of the capacitor, scaling introduces yet another major problem for the DRAM manufacturers which is the leakage current. In both the memory cell as well as the supporting circuitry, leakage becomes more significant as complementary metal-oxide-semiconductor (CMOS) processing nodes progress from different nanotechnology. 

This problem has a resolution, that is, the help of 3T-1D structure. In this 3T-1D DRAM structure by simply joining source and drain of N-mos transistor we can produce voltage controlled capacitor diode hence the name 3T-1D cell.

# 3T1D DRAM Design

A single DRAM cell is capable of storing 1 bit data in the capacitor in the form of charge. Charge of the capacitor decreases with time. Hence refresh signals are used to refresh the data in the capacitor. When a read signal reads the data it refreshes it as well. Many different cell designs exist for modern day DRAM cell. These designs are differentiated by the no. of transistors used in their designing. As the no. of transistors increase, power dissipation also increases. 

<p align="center">
<img src="Project Images/3T1D Cell.jpg"></br>
  Fig 1: 3T1D DRAM Cell
</p>
Figure above represents a 3T-1D DRAM cell used for reference for designing the circuit at a transistor level.
The basis of the storage system is the charge placed in node S, written from BL write line when T1 is activated. Consequently, it has a DRAM cell nature, but it allows a non-destructive read process (a clear advantage over 1T1C memories) and high performance read and writes operation, comparable to 6T. With T1 and T3 transistors as accessing devices, the whole cell is composed by four transistors of similar size to the corresponding of 6T. This implies a more compact cell structure. In order to write the cell at the BL write line level it is only required to activate T1 through the WL write line. Hence, the S node stores either a 0 or a VDD-Vth voltage depending on the logic value. This voltage results in the accumulation of charge at the gate of devices D and T2. A key aspect of the 3T1D memory cell is that the capacitance of the gated diode (D) when Vgs is above Vth is significantly higher with respect to lower voltages, because there is a substantial amount of charge stored in the inversion layer. In order to read the cell, the read bit line BL read has to be previously pre-charged at VDD level. Then T3 is activated from WL read line. If a high (1) level is stored in S, transistor T2 turns on and discharges the bit line. If a low (0) level is stored in S, transistor T2 does not reach enough conduction level. The objective of the gated diode D is to improve Read Access Time. When a high (1) level is stored in S, D connected to WL read line causes a boosting effect of the voltage level in node S. The voltage level reached at node S is close to Vdd voltage causing a fast discharge of the parasitic capacitance in BL read. If allow (0) level is stored, transistor T2 keeps turned off.

# Reference Schematic and Simulation:

## Reference Circuit:

Fig 2 shows the transistor-level schematic used as reference for DRAM design.
<p align="center">
  <img src="Project Images/Reference Circuit.jpg"></br>
  Fig 2: Reference Circuit Diagram
</p>
<p>
This 3T-1D DRAM cell is very different from all others DRAM cell. Its key feature is that it provides non-destructive read operation and also its speed of operation is high, it gives less leakage power and is more stable than the SRAM and other capacitor-based DRAMs. Variation only affects the operating frequency of the cell,making it much more robust to process variations than the 6T design. The figure above shows us the transistor-level reference schematic of the cell. 

From the Fig 1, we can say that the Memory architecture is designed in a way in which the capacitor gets re-placed by diode D which acts as voltage controlled capacitor. Hence, it relies on a “gated diode” (D) to improve array access speed. This diode can be thought of having larger capacitance when storing a “1” and a smaller capacitance when storing a “0”. Each time the cell is read, the bottom side of this capacitor is also raised to VDD. If the cell stores a “1” and it is read, the charge stored on the big capacitor of D1.

The Read and write operations take place as follows-
To write to the cell, the write bitline is charged to the value we wish to store in the cell, and the write wordline is strobe. To read from the cell, the read bitline is precharged high and the read wordline is strobe. If a 1 is stored in the cell, transistor T2 turns on and the bitline discharges. The key to fast access times is the gated diode, which is tied to the read wordline. When a 1 is stored in the cell, the diode provides a ‘boosting’ effect to the value at the storage temporarily giving it a value close to (and sometimes greater than) Vdd, allowing T2 to turn on quickly and discharge the bitline. When a 0 is stored in the cell, the capacitance of D is smaller and little to no voltage boosting occurs, keeping T2 turned off. Because the 3T-1D is a dynamic memory, the value at the storage node[s] leaks away with time.

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
The Synopsys Custom Compiler™ design environment is a modern solution for full-custom analog, custom digital, and mixed-signal IC design. As the heart of the Synopsys Custom Design Platform, Custom Compiler provides design entry, simulation management and analysis, and custom layout editing features. 
To know more, kindly refer to: <a href='https://www.synopsys.com/implementation-and-signoff/custom-design-platform/custom-compiler.html'>Synopsys Custom Compiler</a></br>

<p align="center">
  <img src="Project Images/custom_compiler_img.jpg"></br>
</p>
<p>

<b>• Synopsys Primewave:</b></br>
PrimeWave™ Design Environment is a comprehensive and flexible environment for simulation setup and analysis of analog, RF, mixed-signal design, custom-digital and memory designs within the Synopsys Custom Design Platform. The transient analysis of the above schematic was made possible because of this very tool. 
To know more, kindly refer to: <a href='https://www.synopsys.com/implementation-and-signoff/ams-simulation/primewave.html'>Synopsys PrimeWave Design Environment</a></br>

<b>• Synopsys 28nm PDK:</b></br>
The 28 nanometer Process design kit by Synopsys was the focal point behind the Design and Analysis of this project.

# Schematic Design and Simulation:

## Schematic:

### Transistor-level Schematic:
Keeping in mind the Reference circuit diagram above, the schematic of the DRAM was designed at a transistor-level using the 28nm PDK library on the Custom Compiler Schematic Editor.
<p align="center">
  <img src="Project Images/3T1D DRAM Schematic.jpeg"></br>
  Fig. 4: 3T1D DRAM Schematic
</p>

### Symbol:
Initially, after designing the schematic, it was then converted to a symbol so as to be used for further reference while designing the testbench for the same.
<p align="center">
  <img src="Project Images/symbol.jpeg"></br>
  Fig. 5: Symbol Design
</p>

### Testbench:
The Testbench has been created using the Symbol designed previously and the Vpulse and Vsupply values have been set.

<p align="center">
  <img src="Project Images/Testbench Schematic.jpeg"></br>
  Fig. 6: Testbench Design


## Simulation:

### Transient Analysis:
in order to perform a successfull Transient Analysis simulation of the above Testbench Design, following steps were followed:
1) After completion of Testbench design, click 'Save'
2) Then, navigate to 'Tools' and in the drop-down menu of Tools, select 'Primewave'. 
3) The Testsuite Simulation window appears, here double-click on the 'model file' and then in the include path option paste '/PDK/SAED_PDK32nm/hspice'.
4) Then click to add Model File and select from that folder the 'saed32nm.lib', that is, the 28nm PDK's .lib file presentin the HSPICE folder and set section as 'TT'. Click Ok.
5) Now double click on Analyses and you should see the Analysis window appear. Select from here '.tran' analysis and give the 'Start', 'Stop', and 'Step Size' parameters and save it by clicking Ok. 
6) Then add the outputs which need to be plotted by selecting the nets from the 'Pick from design' option.</br> 
7) Then navigate to 'Simulations' and click 'Netlist and Run' to generate the SPICE netlist and get the Output waveform on the Waveview Simulation window.

<p align="center">
  <img src="Project Images/Trans_output.jpg"></br>
  Fig. 7: Transient Analysis of the Testbench
</p>
Due to the threshold voltage of T1 in the Fig 1, there is a degraded level on the storage node [Vc] when storing a “1”, hence the Dynamic nature of DRAM.
The above graph has a Vsupply value of 1.2V and a total time period of 50ns.

# SPICE Netlist:

Herewith is the Netlist generated for the above design:

	*  Generated for: PrimeSim
	*  Design library name: lib1
	*  Design cell name: 3T1D_DRAM_tb
	*  Design view name: schematic
	.lib 'saed32nm.lib' TT

	*Custom Compiler Version S-2021.09
	*Tue Feb 22 20:44:28 2022

	.global gnd!
	********************************************************************************
	* Library          : lib1
	* Cell             : 3T1D_DRAM
	* View             : schematic
	* View Search List : hspice hspiceD schematic spice veriloga
	* View Stop List   : hspice hspiceD
	********************************************************************************
	.subckt _3t1d_dram dramop rclk vc wrclk bit_line
	xm4 dramop net32 gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
	xm3 gnd! vc gnd! gnd! n105 w=3.5u l=0.03u nf=1 m=1
	xm5 net32 rclk gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
	xm12 bit_line wrclk vc vc n105 w=3.5u l=30n nf=1 m=1
	xm0 gnd! vc gnd! gnd! n105 w=0.6u l=0.5u nf=1 m=1
	xm7 dramop net32 net47 net47 p105 w=0.1u l=0.03u nf=1 m=1
	xm6 net32 gnd! net47 net47 p105 w=0.1u l=0.03u nf=1 m=1
	vs1 net47 gnd! dc=1.2
	.ends _3t1d_dram

	********************************************************************************
	* Library          : lib1
	* Cell             : 3T1D_DRAM_tb
	* View             : schematic
	* View Search List : hspice hspiceD schematic spice veriloga
	* View Stop List   : hspice hspiceD
	********************************************************************************
	xi1 op rclk vc wrclk bit_line _3t1d_dram
	vdatain bit_line gnd! dc=0 pulse ( 0 1.2 0 100p 100p 10n 20n )
	vr_clk rclk gnd! dc=0 pulse ( 0 1.2 6n 100p 100p 2n 10n )
	vwr_clk wrclk gnd! dc=0 pulse ( 0 1.2 0.2n 100p 100p 2n 10n )

	.tran '1n' '50n' name=tran

	.option primesim_remove_probe_prefix = 0
	.probe v(*) i(*) level=1
	.probe tran v(op) v(rclk) v(vc) v(wrclk) v(bit_line)

	.temp 25

	.option primesim_output=wdf

	.option parhier = LOCAL

	.end

# Observations & Conclusion:
Thus, the design and analysis of the 3T1D Capacitorless DRAM using 28nm CMOS has been successfully carried out on the Synopsys Custom Compiler with the following observations:</br>

• The storage of data in this type of DRAM design is made possible via the use of a gated diode as an alternative to capacitor based DRAM cells.</br>
• Because the 3T-1D DRAM is a dynamic memory, the value at the storage node[Vc] leaks away with time but because of its resistance to process variation, this 3T1D DRAM does not slow down as its size is scaled down helping it to be used at low feature sizes.</br>
• The 3T1D design eliminates existing memory drawabacks associated with the 4T and 3T1C based DRAM Designs.</br>

# Author:
• Ayush Gupta, B.Tech(ECE), SRM Institute of Science and Technology, Kattankulattur, Chennai-603203.

# Acknowledgements:
• <a href='https://in.linkedin.com/in/kunal-ghosh-vlsisystemdesign-com-28084836/'>Kunal Ghosh</a>, Founder, VSD Corporation Pvt. Ltd</br>
• <a href='https://iith.ac.in/'>IIT Hyderabad</a></br>
• <a href='https://www.synopsys.com/'>Synopsys India</a></br>

# References:
[1] Prateek Asthana, Sangeeta Mahesh, “Performance Comparison of 4T, 3T and 3T1D DRAM cell design on 32 nm Technology”, 4th International Conference on Computer Science, Engineering and Applications, July 2014.</br>
[2] rof Y.N Thakare, Dr. S.N. Kale, “Comparative Analysis of 4T and 3T-1D DRAM to minimize Power Consumption”, Journal of Applied Science and Computations, ISSN NO: 1076-5131

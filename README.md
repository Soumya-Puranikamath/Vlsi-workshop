Hello everyone.Here I will be posting what I learnt during 2 weeks workshop under VSD.
* Learning the importance of VLSI in today's world.
* Aurdino as example,learnt what is pakaging actually and this package contain small chip.
* Different types of packaging such as QFN(quad flat no-leads), DIP(dual-in line pacakging), TO packaging and other different types

  
 chip as following parameter:
 
 *PADs are the one's through which signal flows inside and outside of the chip.
 
 *Core is one where the digital logic gates are connected.
 
 *Die is one which determines the size of chip.
 
  ![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/862c8752-34a2-451e-bb41-6cf7751b1d70)

**Introduction to RISC-V architecture:**
The instructions are the only way through  which  machine can understand  what operations it has to perform. ISA which mean" Instruction Set Architecture" is communicating with machine. Here we write code in c,c++ or java language then through assembler this code will be converted into assembly level language and then to the machine level language as 1or 0. 
RTL  of the design is expressed through hardware description language which will be applied to the layout. 

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/25690e6d-550b-4de7-a0eb-664b3692db0b)

**From software application to hardware:**
Application software or apps enter into system software and get converted to hardware language.The major components of system software are os,compiler,assembler.

1.OS:It converts application software to c,c++ or java language.

2.Compiler:The compiler takes output of O.S as input and converts the codes in C,C++,Java etc.. into Instruction set(.exe files). These instructions will be dependent on type of hardware used.

3.Assembler:Assembler converts the .exe files into binary language and provides it to the hardware, and hardware performs the respective operations.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/2d9593a4-09d9-457f-86cf-5aa9f246bd5c)

SOC Design and Openlane:

 To design any ASIC digital circuit we need three things.
 1.EDA tools

 2.PDKS

 3.RTL designs


![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/7870e2e2-9ae4-4195-aa81-7f39fa96b60b) ![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/4ebf2497-4804-4292-a4cd-21647a1138f7)


RTL Design:
RTL stands for REgister Transfer level.It is very crucial in  VLSI.
Exactly, RTL design is pivotal in VLSI (Very Large Scale Integration) because it bridges the gap between high-level behavioral descriptions of a digital system and the low-level implementation using hardware components. At the RTL level, designers specify the functionality of the digital circuit in terms of data transfers between registers and the logical operations that manipulate these data. This abstraction allows for efficient synthesis into actual hardware components while maintaining a high level of flexibility and scalability in the design process.

EDA Tools:
EDA (Electronic Design Automation) tools play a crucial role in the design and verification of Integrated Circuits (ICs). These tools help engineers to create, simulate, and test the design of ICs to ensure they meet the desired performance specifications and density requirements. 

PDK:
A Process Design Kit (PDK) is indeed an essential collection of files and data used to model and facilitate the design of integrated circuits (ICs) within specific semiconductor fabrication processes. PDKs provide the necessary information and models that allow EDA tools to accurately simulate, design, and verify ICs. In 2020 Google collabarated with SkyWater Technology and made FOSS 130nm Production PDK OpenSource which is called as skywater pdk.It contains  process design rules like DRC,LVS,device models and digital standard cell libraries.PDK i interconnection between FAB and designers.

*Process Design Rules : DRC , LVS , PEX

*Device Models

*Digital Standard Cell Libraries

*I/O Libraries 

Simplified RTL to GDS Flow:

The RTL to GDS (RTL2GDS) flow involves several key stages that transform a high-level RTL description of a digital circuit into a GDSII file, which can be used for manufacturing the integrated circuit (IC). 
![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/4612cf58-cff3-4218-84b0-6ba32f84ed75)


ASIC Design Flow:

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/23437728-8900-470a-a89b-6578b358bcf6)

1.Synthesis:This is first main steps in ASIC design flow.During the synthesis stage, the RTL file is converted into a gate-level netlist using components from the Standard Cell Library. Standard cells are pre-designed and pre-verified blocks that represent basic logic functions like AND, OR, NOT, flip-flops, and more. 

These cells are designed to have a regular layout with uniform height but varying widths, facilitating a more efficient and structured placement and routing process.
These standard cell have different models based on electrical,HDL,spice,layout(Abstact detail).

2.Floor and Power planning:This plays crucial in not only the ASIC design but any chip design.Floor depends on how much silicon area is utilizing for chip design.It depends on wheather you are designing single component or whole chip.We should design in such way that there should be robust power supply and power utilisation minimum.However this floor and power plannning will affect the cost of the chip.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/193c0d31-8971-4e97-b7ed-c68f250c89fe)

From above figure we can say that floor planning is nothing but dividing chip die area into different system building blocks and places for I/O pads.

In 











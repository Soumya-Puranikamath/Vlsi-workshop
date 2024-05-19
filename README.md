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

In micro floor planning dimensions,pin location and rows definitions are present.


Multiple Vdd and ground connnections are given through rings and straps.

3.Placement:Placement is done in two steps.One is global followed by detailed.During the Placement stage, components are positioned within the areas planned during the FloorPlanning stage. This includes placing the standard cells required in the design within the predefined cell boundaries. Placement is performed in two main stages:

Global Placement:

Standard cells are initially placed roughly in their target locations.
Overlaps are allowed, and precise placement rules may not be followed.
The focus is on an approximate distribution of cells to optimize overall design metrics like timing and wire length.

Detailed Placement:

Standard cells are adjusted to their final, exact positions.
Placement rules are strictly enforced to avoid overlaps and ensure manufacturability.
The objective is to place each cell optimally to meet timing, power, and area constraints.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/86cbd35c-0a9e-4d55-a7b3-379632111041)

4.CTS:CTS which means Clock Tree Synthesis.Before performing the routing of signals, clock routing must be completed. The primary challenge in clock routing is clock skew, which is the difference in arrival times of the clock signal at different points in the design. To minimize clock skew, symmetric tree structures are used. These structures ensure that the clock signal reaches all parts of the design simultaneously by maintaining balanced path lengths.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/4d459760-576d-4d39-8e97-1cf8f664d64e)

5.Routing:After clock routing is completed, signal routing begins, utilizing the remaining metal layers to make necessary connections within the design. This process occurs in two stages: Global Routing and Detailed Routing. In the Global Routing stage, the tool generates a high-level Routing Guide, which outlines the general paths for the connections and follows the instructions given in the Process Design Kit (PDK). In the Detailed Routing stage, the actual routing is performed according to the guide generated in the Global Routing stage.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/51fc4714-73e5-4707-b362-112644837399)

6.Sign-off:After routing is completed, the chip moves to the Sign-off stage, where various checks ensure its integrity and readiness for fabrication. Physical verification checks include Design Rule Check (DRC) and Layout Versus Schematic (LVS). During DRC, the design is verified for any violations of the design rules provided by the Process Design Kit (PDK), ensuring manufacturability and reliability. LVS checks confirm that the layout matches the gate-level netlist functionality, ensuring the physical layout performs as intended. Additionally, timing checks such as Static Timing Analysis (STA) are performed to identify any timing violations, ensuring that all timing constraints are met and the chip will operate correctly at the desired clock speed. 

Introduction to OPENLANE:

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/d7786e14-8d96-4e21-9e58-2ad280848d50)

OpenLane is an open-source flow initiated by e-fabless for a true open-source tape-out experiment. It is a platform that supports various tools such as Yosys, OpenRoad, Magic, KLayout, and other open-source tools. OpenLane integrates the various steps of silicon implementation and abstracts them, making the process more accessible and streamlined. At e-fabless, they have developed an SoC family called Strive. Strive is a family of open-everything SoCs, featuring open PDK (Process Design Kit), open RTL (Register Transfer Level), and open EDA (Electronic Design Automation) tools. This open-source approach aims to democratize chip design and fabrication, allowing wider access and collaboration within the semiconductor industry.

Strive SOC family is as follows:
![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/c9d4bd98-c4c2-490e-a448-ed8a3e8af4f6)

The main goal of OpenLane is to produce a clean GDS file without any human intervention, ensuring there are no LVS, DRC, or timing violations. It is primarily optimized for the Skywater 130nm OpenPDK but also supports XFab180 and GF130G processes. OpenLane works out of the box and is capable of hardening both macros and chips. It offers two modes of operation: autonomous and interactive. One of its features, Design Space Exploration, helps find the best set of flow configurations. Currently, OpenLane includes nearly 43 design examples, with more to be added soon.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/96cc2fff-e149-4d2c-9e98-339c69551f6c)

 Each step in RTL to GDS2 uses different open source tools.
 DFT uses fault which performs following functions.
1.Scan Insertion
2.Automatic Test Pattern Generation(ATPG)
3.Test Pattern Compaction
4.Fault coverage
5.Fault Simulation

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/842f5e54-45dd-473d-b76d-071cae9440a1)

 For physical implementation we use OpenROAD.
 It performs functions as mentioned in figure.
 ![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/43f19621-b3d8-4745-836c-d46d6548556a)

When routing is not done properly metal wire fabricated acts as antenna which damage the mosfet during fabrication.
![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/dbbbd95b-afa1-4227-b502-686534bbf08b)



To avoid this two solutions we opted.
1.Bridging attaches a higher layer intermediary. It requires Router awareness.

2.Add antenna diode cell to leak away the charges. Antenna diodes are provided by the SCL. 


For this we took a preventive approach.
Add a Fake antenna didoe next to every cell input after placement.
Run the Antenna Checker(Magic) on the routed layout.
If the checker reports violation on the cell input pin, replace the fake diode cell by a real one.

For physical verification DRC,LVS are done.
magic tool is used for DRC and spice simulation and magic and netgen are used for LVS.


Invoking OPENLANE in Ubantu:

![Screenshot from 2024-05-13 15-23-30 - 1 (1)](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/10194b81-ac6c-4e6f-84cb-ef97ecbe368d)

In desktop,work folder is present.It consists of Openlane working directory which leads to Openlane.To enter the bash file type docker after enterning Openlane environment.To invoke the software type ./flow.tcl -interactive
Now we need to select the design on which we are going to perform RTL to GDS flow, we will be having 30 to 40 designs that are pre-built in the design folder in openlane and we will be selecting "picorv32a.v" design for this project.Now in order to perform synthesis(first stage of the project) on this design, first we need to setup the design and for that the command will be  **prep -design picorv32a**

![Screenshot from 2024-05-15 15-22-45](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/2780bbfb-a119-41b1-b9db-7d7b882c145c)

To check the files after design is prepared.

![Screenshot from 2024-05-15 15-33-05](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/fc169058-d8ac-4f6c-9020-465828c9c208)


Initially every directory will be empty because we haven't performed any operations on the design.But we will have a direcrory named tmp and it contains different types of files.One of the files will be "merged.lef" file, it contains metal layer level and cell level information.merged.lef was created by merglef.py

![Screenshot from 2024-05-15 15-58-15](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/f3bcaf8f-2bcd-4f96-9139-e8343cbb2181)

tmp file contains empty files.It contains empty files.merged.lef file is also in tmp file,when it is opened its content will be as follows.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/22484b50-0a82-40ee-b0a4-8a3dcc457180)

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/e9ed4d50-ec53-430e-bc02-520589c61755)

All layer and via level information will be present.

After opening config.tcl using less config.tcl command.

![Screenshot from 2024-05-15 15-58-05](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/05a0d25d-5c48-4fed-9107-2e8a8ced2608)

After the design is downloded,this step is followed.**run_synthesis** is used to run design.It takes few minutes to run design.When the process is completed it shows synthesis was succesfull.
After compliting run synthesis,no of flip flops,and,or,nor etc will be given.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/7106e15a-d1ce-4d0d-8392-d2fd73a01e7a)

There will be total 1613 flip flops.
**flip flop ratio**=((no of flip flops)/(total no of cells))*100=(1613/14876)*100=10.84%

Before Performing Synthesis the reports directory was null. After Synthesis completed  the reports that are generated during synthesis will be  in the reports directory.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/26a8e433-ce3c-4f44-a707-03ea5977cbe3)

when we open the 2-opensta.rpt file ,it showed delay and cap,fanout etc.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/0e5f8e17-e4ea-4259-a200-424d8dd7413b)

How to define width, height of core and die?

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/2c73e2bb-09cd-46f8-a15b-b0b327931ba7)

Let us consider the basic netlest.Netlist is nothing but which defines all the connectivity between different components.When we are defining about the dimensions of chip,its nostly dependent on dimensions of gates present in the chip.
![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/179560ea-65bf-4a38-893e-be455adab596)
![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/3b0c26d8-2dcf-4b3d-b110-9d7c11a48dc3)
![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/8fa17ac2-24d7-4825-bb12-0ad604c0e3b1)

Utilisation factor=area of netlist/total area of core.
It helps to determine how much area is utilised in chip die.If its 1 then chip die is completely utilised and no space left for extra cells.
Aspect ratio=height/width.If aspect ratio is 1 then it is square otherwise it will be rectangle.

Concept of pre placement cells:

The concept of pre-placing cells involves reusing already designed blocks to avoid redesigning them repeatedly. Common pre-placed blocks, known as macros or IPs, include memory, comparators, and multiplexers. These blocks should be placed strategically, especially near input pins if they have numerous connections to them, to minimize wiring length. The term "pre-placed" refers to positioning these blocks during the floorplan stage, before the general placement stage. During the floorplan stage, these blocks are placed, and placement blockages are defined to prevent the tool from placing other standard cells too close to them during the placement stage. Utilizing pre-placed cells can significantly reduce the time-to-market by streamlining the design process and ensuring efficient layout.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/cc6e9feb-97ca-4a30-8f22-977447e757fd)

Decoupling capacitor:
Generally, pre-placed blocks, or macros, are high-power draining components. In some cases, the power they receive from the power source may be insufficient for proper switching due to voltage drops in the interconnecting wires, causing the signal to fall outside the noise margin. To address this issue, decoupling capacitors (decaps) are used. Decoupling capacitors store charge and provide a local reservoir of power to the high-power blocks, helping to stabilize the voltage and ensure that the signals remain within the acceptable noise margin. This helps maintain reliable performance of the pre-placed blocks by mitigating the effects of voltage drops.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/e86c960b-1cfd-4db6-baf5-af519da67f71)


Noise margin:

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/cca94902-6e25-4f0c-8a25-004585abdbdd)

Power planning:

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/0a17b13c-01ac-4bd8-9c1a-0726de738a3a)
In the previous section, we discussed using decoupling capacitors (decap cells) to manage power for different blocks. However, decap cells have limitations such as increased leakage power and chip area. To address these issues, we use a technique called power planning. Power planning involves designing an efficient power distribution network to ensure reliable power delivery throughout the chip.There will be two switching phenomenon.

1.Voltage drop : When a group of cells are simultaneously switching from 0 to 1, then every cell needs the power and In case the power is supplying from one source, there may occur the shotage of power and drop in the input voltage happens at that place. This is called as "Voltage Drop". The problem occurs only when the voltage level goes below the noise margin.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/fada13b0-f4ad-4953-917a-c359a0d29ddc)

2.Ground bounce:When most capacitors requires current to discharge from 1 to 0,every cell dumps power to the ground simultaneously through the same ground pin. This can cause the ground voltage, instead of staying at 0V, to experience a temporary rise, known as "ground bounce." Ground bounce becomes problematic when the voltage level exceeds the noise margin, potentially leading to signal integrity issues and circuit malfunction. Ensuring the ground voltage remains within acceptable limits is crucial for maintaining reliable chip performance.

To prevent these abnormalities, a technique known as power planning is employed. This method involves creating separate power meshes: one for Vdd and another for ground. These meshes are constructed using the top two metal layers, chosen for their lower voltage drop characteristics. The meshes are distributed throughout the design and connected to multiple Vdd and ground sources, ensuring stable and reliable power delivery across the chip.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/3d9f5c37-f586-478d-8266-49b610cae735)

Using this technique, whenever a cell needs power to switch from 0 to 1, it draws power from the nearest Vdd layer. Conversely, if a cell needs to discharge power, it will do so to the nearest ground layer.
Here blue line indicates vddand grey line indicates ground and x marks indicates connection.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/ff0fe5ed-94ec-40ad-9396-f620cf11bc26)

Pin placement and Routing:

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/449b4b1a-3cd7-485c-b0c9-fabda290e057)

To ensure the floorplan runs smoothly, designers must carefully manage certain parameters, known as switches, that influence the floorplan. For instance, the utilization factor and aspect ratio are crucial switches. Designers should verify these switches before initializing the floorplan to ensure they align with the project requirements. The image below illustrates the various types of switches used during the floorplan stage.
![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/63d04501-b16e-45af-9386-f44c5201f47c)

In the OpenLane least priority  is for default(Floorplanning.tcl) and the second highest priority  is for config.tcl and the highest priority is for PDK_varient.tcl for considering the values for switches.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/9531c85b-8d5a-4551-81f5-ea6c5afceabe)

When we open config.tcl file in picorv32a,it open ups like the below figure.
![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/3bc178db-6e55-4224-9043-05c3b7175e55)
vertical metal willbe one more thaan horizontal metal.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/e3fdabdb-5f27-4384-bcef-bf0137bb017f)

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/f2815625-cb94-4c89-8a1d-babd726ff741)

In order to enter into the MAGIC tool ,command we use:

**magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &**

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/6fe9aa4d-0fc8-4a96-abb5-d75e54afc964)

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/5c70e385-478d-4546-aecf-5f9b0af2b2a6)

To center the design on the screen, start by selecting the entire design by pressing 'S' on the keyboard followed by 'V'. 

To zoom into a specific area, left-click and drag to select the area, then right-click and press 'Z' to zoom in on the selected region.

To view the details of a particular cell in the design, move the cursor to the cell and press 'S' to select it. Then, in the tkcon window, type the command "what" to display the details of the selected item.

Netlist binding and initial place design:

In the netlist, each element is represented by a unique shape, such as an AND gate having one shape and an OR gate having another. However, in a library, every element is depicted with only a square or rectangular shape. The library contains all the elements ready for use, each accompanied by its properties like area, delay, etc. Additionally, there are multiple versions of the same element, each with different properties.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/f634a02b-486b-479e-bd11-dd7e13db3e93)

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/af7daf04-f93b-45e6-822b-f8737cc26f4e)


In the image above, there are three different sets of identical elements. The larger elements are faster but take up more area, while the smaller elements occupy less area but operate more slowly compared to the larger ones.

Optimize placement using estimated wire-length and capacitance:

During placement, it's crucial to consider the estimated wire length and position the cells accordingly. This estimation is done by calculating the distance from the input sources of the cells to the output sinks they drive.In the example above, the tool places the blocks based on the estimated wire length, as illustrated in the figure below.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/56847923-ab77-47e0-8ab5-6268f93546c5)


After run_placement:

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/0fb3cb2c-200f-49fd-8f94-0b9384f1a991)

After the placement is done,to check the cells are correctly placed or not we go for GUI.The command will be
**magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &**

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/fa41bd99-1b12-4a7b-8228-816edf66f9f7)

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/0f6149d0-b74a-4e12-a188-8c5b56cf335e)


**Design library cell using Magic Layout and ngspice characterization**:

Inception of Layout and CMOS fabrication process:
Lab steps to create std cell layout and extract spice netlist:

To extract the SPICE netlist for an inverter from the MAGIC tool for simulation in ngspice, follow these steps:

First, you need to create an extraction file for the inverter. This can be done by using the `extract all` command in the tkcon window within MAGIC. Running this command will generate an extracted file in the `vsdstdcelldesign` directory.

When the distance between i/o pins is changed  the floorplan will be changed.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/c5965fa9-01f1-465c-8128-ba43c2af298a)

Git glone vsdcelldesign and list files present in it.vsdcell design already containsthe inverter standard cell.In vsdcelldesign directory when magic -T sky130A.tech sky130_inv.mag & comand is given inverter layout will be opened.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/39d42802-47f5-49ed-896c-5e12d229143c)

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/8399ee03-6140-4acf-a57e-f55aaf3eb880)

Next we need to create a spice file using this extracted file to use within the ngspice tool.For this the command will be ext2spice cthresh 0 rthresh 0, this will not create any new file.After that use command ext2spice , this will create a spice file in the vsdstdcelldesign directory.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/423e2d8a-328c-4f1d-bf06-f79cf75829e9)

Spice file will be present in vsdcelldesign directory with name sky130_inv.spice.When the spice file is opened it has to be modified accordindly as mentioned below.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/3d98b30f-d9c3-498c-b45e-bbc6acf9068a)

To run the spice file,we have to install the ngspice is vsdcelldesign directory.Command will be **sudo apt install ngspice**.When it is installed Completely open the spice file with command **ngspice sky130_inv.spice**.To plot the tansiant response curve give the command **plot y vs time a**.The transiant waveform will be obtained.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/8ac02bc6-5d0f-4857-925a-aa554f3c4873)

From the plot that we got from ngspice, we need to characterize four parameters of the Inverter.

Rise time : It is the time taken for the output waveform to go to 80% of its max value from 20% of its max value.

x0 = 6.16138e-09, y0 = 0.660007

x0 = 6.20366e-09, y0 = 2.64009

From the above values, Rise time = 0.0422 ns

Fall time : It is the time taken for the output to fall from 80% of its max value to 20% of its max value.

x0 = 8.04034e-09, y0 = 2.64003

x0 = 8.06818e-09, y0 = 0.659993

From the above values , Fall Time = 0.0278 ns

Propogation Delay : It is the time taken for the 50% of transition from 0 to 1 at the output for the 50% transistion from 1 to 0 at the input side.

x0 = 2.18449e-09, y0 = 1.64994

x0 = 2.15e-09, y0 = 1.65011 From the above values , Prop Delay = 0.034 ns

Cell Fall Delay : It is the time taken for the 50% of transition from 1 to 0 at the output for the 50% transistion from 0 to 1 at the input side.

x0 = 4.05432e-09, y0 = 1.65

x0 = 4.05001e-09, y0 = 1.65

From the above values , cell fall delay = 0.0043 ns

We have succesfully characterized the Inverter, now we should create a LEF file.

Lab Introduction to Sky130 pdk's and steps to download labs: To download the lab files in the home directory use the command- **wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz**. To extract the labs from the zip file use the commandtar** xfz drc_tests.tgz**In the downloaded files .In lab files , .magicrc file act as the start-up script for MAGIC.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/e97947c7-9e4d-4f99-ba89-255b2db1b76e)

Lab Introduction to Magic and steps to load sky130 tech-rule:
Use the command magic -d XR to open the Magic tool.

![image](https://github.com/Soumya-Puranikamath/Vlsi-workshop/assets/169351521/14a26089-8434-4891-8a92-4cd4f0904713)

select the area in GUI and click on m3layer in layer box and press P.The selcted area will be filled with metal3 layer.To create via,type **cif see VIA2** in tkcon2.3 terminal.The selectedd metal will be filled with via.We can also determine the distance between each via by selecting the box between two vias and pressing the box in tkcon terminal.


Lab exercise to fix Poly-9 error in Sky130 tech file:To load poly9 file,type **load poly** in tkcon terminal.





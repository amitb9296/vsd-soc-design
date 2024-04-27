<h1 align="center">VSD-SoC-Design</h1>

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li>
      <a href="#rtl-to-gdsii-flow">RTL to GDSII flow</a>
    </li>
    <li>
      <a href="#day-1-inception-of-open-source-eda-openlane-and-sky130-pdk">Day 1: Inception of Open Source EDA, OpenLANE and Sky130 PDK</a>
      <ul>
          <li><a href="#understanding-from-software-application-to-hardware">Understanding from Software Application to Hardware</a></li>
          <li><a href="#introduction-to-risc-v">Introduction to RISC-V</a></li>
          <li><a href="#introduction-to-qfn-48-package-chip-pad-core-die-ips">Introduction to QFN-48 package, Chip, Pad, Core, Die, IPs</a></li>
	  <li><a href="#openlane-asic-flow">OpenLANE ASIC Flow</a></li>
	  <li><a href="#openlane-directory-structure">OpenLANE Directory Structure</a></li>
	  <li><a href="#design-preparation-step">Design Preparation Step</a></li>
	  <li><a href="#run-synthesis">Run Synthesis</a></li>
      </ul>
    </li>
  </ol>
</details>


<!-- ABOUT THE PROJECT -->
## About The Project

The aim of project is interactive tutorial experienced during the VSD Advanced Physical Design workshop using OpenLANE.

OpenLANE is an open-source automated RTL to GDSII flow, which includes other open-source tools like OpenROAD, Yosys, Magic, Netgen, Fault, OpenPhySyn, SPEF-Extractor and also uses custom methodology scripts for design optimization.


## RTL to GDSII flow
![rtl2gdsii](https://github.com/amitb9296/vsd-soc-design/assets/53483701/be57231c-6bb4-40a2-bd23-dfb3fe2d99b3)

* **Design Specification**

  The initial stage in the chip design process involves defining the requirements and specifications of the chip. This encompasses outlining the functionality of your product, its intended usage, and the performance metrics it needs to achieve.
  Once these requirements are established, they serve as the foundation for designing the architecture and layout of the chip. Following the architectural design phase, designers proceed to create a Micro-Architectural Specification (MAS).
  This document serves as a detailed description of the chip's architecture, enabling designers to make precise predictions regarding the design's performance, power consumption, and die size.
  
* **RTL Coding**

  This step involves the creation of the digital logic circuits required to implement the functionality defined in the functional design stage. This stage includes creating a logical design using a hardware description language (HDL) and verifying the design’s correctness using simulations.

  Based on the architectural document, RTL designers starts to integrate differrent IPs required as per architecure. This process is iterative as there could be incremental changes through out the design phase depending upon requirement.
  IPs used could be differrent types of memories, interface protocols like (USB, PCIEx) other high speed interfaces, Display, modem, sensors etc. 
  
* **Functional Verification**

  Functional verification, an essential stage, ensures that your logic conforms to the specified requirements, confirming whether the design operates as intended. Companies allocate significant resources to this phase due to its potential to become a critical bottleneck.
  Despite this investment, companies still face significant hardware bugs that can disrupt a platform. The challenge lies in testing every possible outcome, which can result in trillions of test cases for large designs. Developing tools to efficiently and comprehensively test designs without
  overlooking any aspect remains a significant challenge. Substantial subfields within functional verification focus on addressing various aspects involved in verifying a circuit.
   
* **Logic Synthesis**

  Logic synthesis is the process of converting a high-level description of a digital circuit into a detailed representation that can be implemented using logic gates and other components. It involves translating a design specified in a hardware description language (HDL) such as Verilog or VHDL into a netlist of logic gates, flip-flops, and 
  interconnections. The goal of logic synthesis is to optimize the design for factors such as performance, area, and power consumption while meeting the specified timing constraints. This process enables efficient implementation of complex digital designs in hardware.

  As shown in figure below. It uses Standard Cell Libraries(SCL) provided by foundary. These area of standard cells are varies as technology node varies. These SCL jhave differrent views/models shown following figure. which are again used for differrent types of simulations.
  
  | ![image](https://github.com/amitb9296/vsd-soc-design/assets/53483701/595fd351-feb1-45a4-9314-2931614eaea6) | ![image](https://github.com/amitb9296/vsd-soc-design/assets/53483701/a125594a-b3f1-44ba-a227-2dcf7d4cb061) |
  |------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|

  
* **DFT synthesis**

  Internal Scan involves connecting internal flip-flops and latches to enable observation during test mode. Scan chain insertion is a widely used structured technique for digital circuits. In the VLSI industry, this process is also referred to as DFT (Design for Testability) insertion or DFT synthesis.
  
* **Floor Planning**

  The aim is to strategically allocate silicon area and design a dependable power distribution network (PDN) to supply power to each component of the synthesized netlist. Prior to placement, macro placement and blockages must be defined to ensure compliance with the GDS file.
  During power planning, a ring is established, connected to the pads to distribute power along the chip's edges. Additionally, power straps are incorporated to deliver power to the chip's center using higher metal layers, addressing concerns such as IR drop and electro-migration.

  | ![image](https://github.com/amitb9296/vsd-soc-design/assets/53483701/7602d7a7-a0ab-4ab7-a274-5314be704226) | ![image](https://github.com/amitb9296/vsd-soc-design/assets/53483701/589cda04-c28a-4294-85dc-415409d9d0d8) | ![image](https://github.com/amitb9296/vsd-soc-design/assets/53483701/69fbad54-16ef-47c6-a0d1-6754530355f9) |
  |------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
  

* **Placement**

  Standard cells are positioned on the floorplan rows, aligned with sites specified in the technology LEF file. The placement process occurs in two stages: Global and Detailed. During Global placement, an attempt is made to find the optimal position for all cells, although they may initially overlap and not align with rows.
  Detailed placement refines the global placement by legalizing all placements while endeavoring to adhere to the preferences established during global placement.

  | ![image](https://github.com/amitb9296/vsd-soc-design/assets/53483701/1527a7d2-bf30-4ddd-926d-916b6d506fbc) | ![image](https://github.com/amitb9296/vsd-soc-design/assets/53483701/3612a0b9-b565-42ca-864b-b2eac6a18d6e) |
  |------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|


* **Clock Tree Synthesis**

  Clock tree synthesis involves creating the clock distribution network, which serves to deliver the clock signal to all sequential elements. The key aim is to establish a network with minimal skew across the chip, often achieved using common network topologies like H-trees.
  
  ![image](https://github.com/amitb9296/vsd-soc-design/assets/53483701/ec4f00d6-4cb3-46cb-8705-66ca47eb40c7)


* **Routing**

  The interconnect system between standard cells is implemented using the remaining available metal layers following Clock Tree Synthesis (CTS) and Power Distribution Network (PDN) generation. Routing is conducted on routing grids to minimize Design Rule Checking (DRC) errors.
  Router uses metal layers as defined by PDK. For each metal layer PDK defines thickness, pitch that defines tracks and the minimum width. Also defines VS that can be sued to connect wire segments of differrent metal layers together.

  | ![image](https://github.com/amitb9296/vsd-soc-design/assets/53483701/ef0d950f-ea0f-4666-b835-afe1d9540025) | ![image](https://github.com/amitb9296/vsd-soc-design/assets/53483701/f0c0cf3e-9814-4a96-93d2-4323699a6742) |
  |--------------------------|-------------------|
  
* **Static Timing Analysis**

  Static Timing Analysis (STA) stands as a pivotal stage within the realm of Very Large Scale Integration (VLSI) circuit design and validation. Here’s a deeper exploration:

  What is STA?
  Static Timing Analysis (STA) serves as a methodology employed to assess the timing efficacy of a digital design, meticulously scrutinizing every conceivable pathway for potential timing discrepancies. Its aim is to guarantee adherence to predetermined timing constraints, encompassing factors like setup time, hold time, and clock skew.
  The significance of STA lies in its role in assuring the dependable functionality of VLSI chips at designated operational frequencies.

  **Key Concepts in STA:**

  * Timing Paths: These denote the logical routes within the design that contribute to the propagation delay of signals.

  * Time Borrowing: In certain cases, paths can "borrow" time from other paths to satisfy timing requirements.

  * Setup and Hold Time: These represent crucial timing parameters ensuring proper data capture at flip-flops.

  * Interconnect Delay Models: These models factor in delays stemming from wire resistance and capacitance.

  * Maximum Clock Frequency: The utmost clock frequency at which the design operates while adhering to timing constraints.


  **STA Process:**

  * STA scrutinizes the design without applying specific input vectors.
  * Input to an STA tool comprises the routed netlist, clock definitions, and external environment specifications.
  * The tool computes signal propagation delays along each path and identifies timing violations.


  **Common STA Violations:**

  * Setup Violation: Arises when data arrives too tardily at a flip-flop before the clock edge.
  * Hold Violation: Occurs when data changes too swiftly after the clock edge.
  * Clock Skew: Pertains to discrepancies in arrival times of the clock signal at different chip locations.
  
    <img width="518" alt="image" src="https://github.com/amitb9296/vsd-soc-design/assets/53483701/723125b7-150d-427b-983d-8a89a750bc39">


* **Gate Level Simulation**

  Gate level simulation is performed on 

  [Gate-Level Simulation (GLS)](https://www.edn.com/gate-level-simulations-verification-flow-and-challenges/) serves several crucial purposes in the verification and validation process of a digital design:

  * Ensuring correct power-up and reset behavior, verifying absence of unintentional dependencies on initial conditions.
  * Validating low-power structures added during synthesis, offering confidence in their functionality.
  * Identifying multicycle paths and validating their functionality with appropriate tests.
  * Estimating power consumption accurately based on the netlist.
  * Verifying Design-for-Testability (DFT) structures like scan chains and ATPG patterns.
  * Screening for defects using tester patterns on gate-level netlists.
  * Detecting glitches on edge-sensitive signals due to combinational logic, considering worst and best-case scenarios.
  * Evaluating critical timing paths in asynchronous designs that may be missed by Static Timing Analysis (STA).
  * Identifying and addressing simulation artifacts that could mask RTL-level bugs.
  * Highlighting potential simulation-synthesis mismatches and netlist-level issues.
  * Ensuring correct functionality of special logic circuits, including reset circuits and uninitialized logic.
  * Validating design performance at target frequencies with actual delays.
  * Identifying the need for synchronizers and potential timing violations in flip-flops.
 
Once GLS is clean 

<!-- Day 1 Inception of Open Source EDA -->
## Day 1: Inception of Open Source EDA, OpenLANE and Sky130 PDK

### Understanding from Software Application to Hardware 

Software application is a computer program written in higher language like C, Java etc., to carry out a specific task other than one relating to the operation of the computer itself, typically to be used by end-user. Example Paint, Word, media player etc.

Now these software applications could consist of millions of line of code and could rely on sophisticated software libraries that implements complex functions in support of the application. The hardware in a computer can only execute extremely simple low-level instructions. To go from a complex application to the simple instructions involves several layers of software that interpret or translate high-level operations into simple computer instructions.

System Software: Software that provides services that are commonly useful including operating systems, compiler, loaders, and assemblers.

Operating System: Supervising program that manages the resources of a computer for the benefit of the program that run on that computer.  

Following figure shows that many layers of software are organized primarily in a hierarchical fashion, with applications being the outermost ring and a variety of systems software sitting between the hardware and applications software. There are many types of systems software, but two types of systems software are central to every computer system today: an operating system and a compiler. An operating system interfaces between a user’s program and the hardware and provides a variety of services and supervisory functions. 

![Screenshot 2024-04-26 230121](https://github.com/amitb9296/vsd-soc-design/assets/53483701/543daade-bbfa-4456-af6c-cdb5f8e6bd08)


**Compiler**:  It's a program that translates high-level language statements into assembly language statements i.e., translation of a program written in a high-level language, such as C, C++, Java, or Visual Basic into instructions that the hardware can execute. 

The easiest signals for computers to understand are on and off, and so the computer alphabet is just two letters. The two symbols for these two letters are the numbers 0 and 1, and we commonly think of the computer language as numbers in base 2, or binary numbers. We refer to each “letter” as a binary digit or bit. Computers operates on commands, which are called instructions. Instructions, which are just collections of bits that the computer understands and obeys, can be thought of as numbers. 

For example, the bits 1000110010100000


Let's say a software is written in C language. Compiler translates this program into assembly language program. Assembly language is a symbolic representation of machine instructions, which basically tells what operation to perform on operands. 

Assembly languages are an abstracted set of ISA opcodes, logic, and instructions that allow for variables/macros/functions/methods/etc. They can be very basic (meaning almost 1-1 mapping) or they can support more complex operations like structural programming blocks.

There are various types of Instruction Set Architectures example given below.
	
 1) Complex Instruction Set Computer (CISC)
 
 2) [Reduced Instruction Set Computer (RISC)](https://en.wikipedia.org/wiki/Reduced_instruction_set_computer)
 
 3) Very Long Instruction Word (VLIW)

Now this assembly language program is again translated into binary machine language program by assembler. As shown in following figures.

| ![image](https://github.com/amitb9296/vsd-soc-design/assets/53483701/842e35c6-a3a9-47dd-a025-2394e6282b56)        |	![Screenshot 2024-04-27 003442](https://github.com/amitb9296/vsd-soc-design/assets/53483701/fbc6b088-13b0-4976-97d7-644a5274feb3)   |
|-------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|


### Introduction to RISC-V
[RISC-V](https://en.wikipedia.org/wiki/RISC-V) is an open architecture that is controlled by RISC-V International, not a proprietary architecture that is owned by a company like ARM, MIPS, or x86.
Refer to following images. Few instructions are given below, observe instruction are 32-bit wide. This simplifies hardware i.e., hardware logic required to implement risc-v instruction is less.

| ![image](https://github.com/amitb9296/vsd-soc-design/assets/53483701/9c45ddd7-d703-4da9-a22d-3f150f77b18a)  | ![image](https://github.com/amitb9296/vsd-soc-design/assets/53483701/8fba7143-b9bf-45a9-8b8d-7ccfb37f7810) |
|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|


### Introduction to QFN-48 package, Chip, Pad, Core, Die, IPs

**Chip** : The intact and stable die with ample capacity is extracted and packaged to create a chip. The primary function of a chip typically serves as a carrier, while an integrated circuit is the outcome of numerous intricate design procedures.
In common language the “brains” inside many of today’s digital devices like smartphones, tablets, VR headsets, laptops, etc. Sometimes people call chips “semiconductors” or “integrated circuits”.

figure on left shows, the Arduino Leonardo is a microcontroller board based on the ATmega32u4. It has 20 digital input/output pins (of which 7 can be used as PWM outputs and 12 as analog inputs), a 16 MHz crystal oscillator, a micro USB connection, a power jack, an ICSP header, and a reset button.
Figure on right shows, different peripheral placed around the microcontroller depending upon it's application needs.

| ![Screenshot 2024-04-26 153909](https://github.com/amitb9296/vsd-soc-design/assets/53483701/a2636e5e-ee7d-486f-be0b-3d679937da91) | ![Screenshot 2024-04-26 155527](https://github.com/amitb9296/vsd-soc-design/assets/53483701/1d632029-165c-467f-b499-7e0fdde8d43a) |
|-----------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
|                                                 Arduino board                                                                     |                                           Processor/SoC                                                                           | 

**Die**: A die is a small unit in a silicon chip, including a fully designed single chip and a part of the dicing groove area adjacent to the chip in the horizontal and vertical directions.

| ![image](https://github.com/amitb9296/vsd-soc-design/assets/53483701/287185e8-3711-4d2f-ae81-a066c089ff20) | ![image](https://github.com/amitb9296/vsd-soc-design/assets/53483701/f3bbb90a-d875-4fda-862e-049e504baf7c) |
|------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|



**Package**: A semiconductor package is a metal, plastic, glass, or ceramic casing containing one or more discrete semiconductor devices or integrated circuits. Package offers a method for linking it to the surrounding environment, like a printed circuit board, using connectors such as lands, balls, or pins.

There are different type of packages as shown in left fig. Refer to [IC package type](https://www.electronicsforu.com/resources/dip-smd-qfp-bga-ic-packages)

Figure on right shows one of type of package i.e., Quad Flat No-leads (QFN-48)

| ![image](https://github.com/amitb9296/vsd-soc-design/assets/53483701/8241140f-b1c7-4990-9cb6-7fd29bf5e653) | ![Screenshot 2024-04-26 181449](https://github.com/amitb9296/vsd-soc-design/assets/53483701/1b5ae52a-c924-494e-b2fb-986416444cb3) |
|------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|


**Pad**: A chip needs to engage with its external surroundings, involving communication with other microprocessors using protocols such as I2C, SPI, and SCI. Furthermore, it must interface with diverse sensors, employing devices like Analog to Digital Converters (ADCs). Accessing external memory components might also be essential. 
Additionally, the microprocessor may need to operate visual protocol-based devices such as LCDs. These interactions are made feasible by the inclusion of I/O pads, which form the periphery of any chip.
For more information please refer to [EDN](https://www.edn.com/general-purpose-input-output-pad-cases-of-drive-contention/).

| ![Screenshot 2024-04-26 181618](https://github.com/amitb9296/vsd-soc-design/assets/53483701/f04acd51-4cfc-4711-a6fc-bd6a5dda79b9) | ![Screenshot 2024-04-26 181325](https://github.com/amitb9296/vsd-soc-design/assets/53483701/de530046-7854-4ecc-95b4-9d8ad9e1f3e4) |
|-----------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|

**Core/IPs**: An Intellectual Property (IP) core in the semiconductor industry refers to a reusable unit of logic, functionality, cell, or layout design. Typically, it is developed with the intention of licensing to multiple vendors for incorporation as building blocks in various chip designs.

In modern System-on-Chip (SoC) designs, pre-designed IP cores or blocks are increasingly crucial. This is due to the prevalence of standard microprocessors and a multitude of system functionalities that are standardized. 
Once designed, these components can be reused across numerous designs, streamlining development processes and enhancing efficiency.
![Screenshot 2024-04-26 181855](https://github.com/amitb9296/vsd-soc-design/assets/53483701/89dfce9f-1213-4d0f-ba84-c56089ef5278)


## **OpenLANE ASIC Flow**

To function OpenLANE ASIC flow it needs Process Design Kit (PDK) which is the interface between designers and the foundary. This workshop uses the open-source RTL2GDSII EDA tools and Skywater 130nm PDK is required to implement the full RTL2GDSII flow as shown following figures.

| <img width="940" alt="image" src="https://github.com/amitb9296/vsd-soc-design/assets/53483701/3b73db61-3075-4846-83e3-e0dc051f672e"> | <img width="782" alt="image" src="https://github.com/amitb9296/vsd-soc-design/assets/53483701/31fcbbdd-113f-40c2-83b7-c3e710f8a71e"> |
|-----------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|

## **OpenLANE Directory Structure**

* **pdks** 

     |-> open_pdks
  
     |-> **sky130A** => files present in this directory are made compatible to work with Open-source EDA tools used in our OpenLANE ASIC flow. SKY130A is variant of SKY130 PDK.
  
   	|-> .config/

    	|-> nodeinfo.json => It contains foundary information, technology node, feature size,
                             information about standard cells and IO cells to be used.
  
	|- libs.ref/ => Contains all the process specific file like timing, LEF, cell LEF

		|-> sky130_fd_sc_hd => we are using skywater foundary 130A standard cell with high density variant.
                 	|-> techlef => contains layer information
  				|-> lib     => contains differrent lib files for differrent PVT corners
  
 	|- libs.tech/ => Contains all the files specific to tools used in OpenLANE ASIC flow. 

   |- skywater-pdk


* **openlane** => Working directory.
  
	* **How to invoke OpenLANE tool**
 
 			|-> docker
   
   	above commamd is aliased to following command

  		|-> docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=PDK_ROOT -u $(id -u $USER):$(id -g $USER) openlane:rc2
       
	* Run flow using following command.

   			|-> ./flow.tcl -interactive	

	**NOTE**: OpenLANE flow is automated so do use -interactive argument


  	![image](https://github.com/amitb9296/vsd-soc-design/assets/53483701/adc75473-67ed-40d6-bf17-bae645473fc9)


   	Once you see % prompt use following command

  		|-> package require openlane 0.9

  ## **Design Preparation Step**
  	
   	* How to prepare design

       		|-> prep -design picorv32a
   	  
  	![image](https://github.com/amitb9296/vsd-soc-design/assets/53483701/d343be97-4114-4c05-adb4-532173ebaa58)

  	the command used to prepare design merges standard cell LEFs with the tool related LEF files. Stors all the required config files into config.tcl


  ## **Run Synthesis**

		|-> run_synthesis
	
  

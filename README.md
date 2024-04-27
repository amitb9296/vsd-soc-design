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
      <a href="#day-1-inception-of-open-source-eda-openlane-and-sky130-pdk">Day 1 Inception of Open Source EDA, OpenLANE and Sky130 PDK </a>
      *
      <ul>
          <li><a href="#understanding-from-software-application-to-hardware">Understanding from Software Application to Hardware</a></li>
          <li><a href="#introduction-to-risc-v">Introduction to RISC-V</a></li>
          <li><a href="#introduction-to-qfn-48-package-chip-pad-core-die-ips">Introduction to QFN-48 package, Chip, Pad, Core, Die, IPs</a></li>
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


<!-- Day 1 Inception of Open Source EDA -->
## Day 1 Inception of Open Source EDA, OpenLANE and Sky130 PDK

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



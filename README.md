# Phase Locked Loop (PLL) for Clock Generation in SerDes

## Overview
This project involves designing a high-performance Phase Locked Loop (PLL) for Serializer/Deserializer (SerDes) systems using 180nm CMOS technology. Developed as a capstone project, this PLL system is aimed at providing stable and low-jitter clock generation for data serialization, essential for high-speed data transmission in communication systems.

## Table of Contents
- [Introduction](#introduction)
- [Motivation](#motivation)
- [Objectives](#objectives)
- [Specifications](#specifications)
- [Tools and Technology](#tools-and-technology)
- [Theory and Background](#theory-and-background)
  - [Overview of PLL](#overview-of-pll)
  - [Applications in SerDes](#applications-in-serdes)
  - [System Flow](#system-flow)
- [Methodology](#methodology)
- [Building Blocks](#building-blocks)
  - [Phase Frequency Detector (PFD)](#phase-frequency-detector-pfd)
  - [Charge Pump](#charge-pump)
  - [Voltage Controlled Oscillator (VCO)](#voltage-controlled-oscillator-vco)
  - [Frequency Divider](#frequency-divider)
- [Circuit Schematics](#circuit-schematics)
  - [Phase Frequency Detector Schematic](#phase-frequency-detector-schematic)
  - [Charge Pump Schematic](#charge-pump-schematic)
  - [VCO Schematic](#vco-schematic)
  - [Complete PLL Schematic](#complete-pll-schematic)
- [Simulation Results](#simulation-results)
  - [Transient Response](#transient-response)
- [Conclusion](#conclusion)
- [Future Work](#future-work)
- [References](#references)
- [Team Members and Mentors](#team-members-and-mentors)

## Introduction
This section provides an overview of the PLL design project, its objectives, and its application in SerDes systems.

## Motivation
A sudden advancement in the semiconductor industry has resulted in technology scaling, which requires faster data rates and necessitates high-speed clocks in the multi-GHz range. With ever-increasing data rates, the I/O links need to scale appropriately to keep up with performance demands. Parallel links have not been able to match up with system performance. Thus, there is a need for Serializer/Deserializer (SerDes) circuits, which further require PLLs for efficient data transmission. PLLs play a pivotal role in ensuring the accurate transmission of data across various interfaces by generating synchronized clock signals that minimize errors and maintain stability.
Therefore, the main motivation of this project is to overcome the barriers of complexity and provide an improved solution to the existing challenges in clock speed and stability within PLL systems, addressing the growing demands of high-performance technology.

## Objectives
1. Design a PLL capable of generating a stable and low-jitter clock signal to ensure reliable data transmission over high-speed serial links.
2. To achieve an output frequency more than 3 Ghz.
3. To implement and simulate each PLL component in Cadence Virtuoso  for functionality and parameter optimization.

## Specifications

| Parameter             | Value                    |
|-----------------------|--------------------------|
| Supply Voltage (VDD)  | 1.8 V                    |
| Output Frequency      | 4.44 GHz                 |
| Duty Cycle            | 50%                      |
| Process Corner        | Typical                  |
| Operating Temperature | 25°C (Room Temperature)  |

## Tools and Technology
- **Cadence Virtuoso**
- **Spectre**
- **180nm CMOS Technology**

## Theory and Background

### Overview of PLL
A Phase Locked Loop (PLL) is a negative feedback control system that generates a high- frequency output clock whose phase is related to the low-frequency input clock. The low- frequency clock can be generated using a crystal.
![Screenshot 2024-11-12 174241](https://github.com/user-attachments/assets/8a62fb1b-baa9-4b90-b5be-903585fc9a98)

### Applications in SerDes
PLLs are critical in Serializer/Deserializer systems for generating stable clock signals, ensuring data integrity over high-speed communication channels. With skyrocketing data-rate interfaces, the need for clock frequencies in the multi-GHz range is paramount and requires the use of Phase-Locked Loops (PLLs). They are capable of generating high-frequency.

### System Flow
![SystemFlow](https://github.com/user-attachments/assets/0da5c7eb-6f18-4a00-b251-571cb6eb7a70)

## Methodology 

The methodology section outlines the step-by-step approach taken to design and implement the PLL for clock generation in SerDes applications. The project follows a structured process to ensure accurate design and simulation of each component.

1. **Component Analysis**: Each core component of the PLL (Phase Frequency Detector, Charge Pump, Voltage Controlled Oscillator, and Frequency Divider) was studied individually to understand its functionality and requirements.
2. **Design Specification**: Specifications, such as the desired output frequency, supply voltage, and process technology, were defined based on the project objectives.
3. **Schematic Design**: Each component was designed in Cadence Virtuoso, following industry best practices for CMOS-based circuit design.
4. **Simulation and Optimization**: Each component underwent simulations to verify its performance. Parameters were adjusted as needed to optimize for stability, low jitter, and high-frequency operation.
5. **Integration and System Simulation**: After verifying each component, they were integrated into a complete PLL system. The entire system was then simulated to ensure correct phase and frequency alignment.
6. **Result Analysis**: Transient responses were analyzed to validate that the PLL meets the desired specifications.

This methodology ensured a systematic and thorough design process, resulting in a reliable and high-performance PLL suitable for high-speed SerDes applications.

## Building Blocks 

### Phase Frequency Detector (PFD)
One of main blocks of PLL circuit is “Phase Frequency Detector ( P F D )”, which is the initial block of PLL circuit. It has two input ports one having input or reference signal whose phase and frequency to be locked is fed to PFD.

<div align="center">
    <img src="https://github.com/user-attachments/assets/a53fa9f8-44c7-4e34-94c6-ffdafec2db89" alt="Phase Frequency Detector Schematic">
</div>

### Charge Pump
Charge pump converts the UP and DOWN signals generated by PFD into corresponding current values. Charge pump is followed by the loop filter. Charge pump either pumps current into loop filter or pump out the current from loop filter.
The main function of loop filter is to convert signal from PFD to a ripple free DC control voltage.We need to calculate the values of the capacitors and resistor in the loop filter, the zeros and the poles in the system as well as the charge pump current before implementing our design. This is done by first choosing the unity-gain bandwidth, phase margin and resistor.

<div align="center">
    <img src="https://github.com/user-attachments/assets/f3547b80-d962-4dd1-baff-6f1328facb7d" alt="Charge Pump Schematic">
</div>

### Voltage Controlled Oscillator (VCO)
A Voltage-Controlled Oscillator (VCO) is an electronic oscillator whose oscillation frequency is controlled by an input voltage. VCOs are used in PLLs to generate precise and adjustable frequencies based on stable single frequency clock. It is implemented on the basis of barkhausen criteria.

<div align="center">
    <img src="https://github.com/user-attachments/assets/1c16e9cc-33de-4d75-8aa8-b435e139abb6" alt="Voltage Controlled Oscillator Schematic">
</div>

### Frequency Divider
The frequency divider reduces the output frequency to maintain synchronization with the reference clock.

<div align="center">
    <img src="https://github.com/user-attachments/assets/8f31a4f8-b524-40dd-ba12-1e5c1bdc3db9" alt="Frequency Divider Schematic">
</div>

## Circuit Schematics

### Phase Frequency Detector Schematic

<div align="center">
    <img src="https://github.com/user-attachments/assets/22b3a6a0-3621-41f6-a365-7781c5c452bc" alt="Phase Frequency Detector Schematic">
</div>

### Charge Pump Schematic

<div align="center">
    <img src="https://github.com/user-attachments/assets/44f32c7d-c166-4544-a7e3-af84f857dcee" alt="Charge Pump Schematic">
</div>

### VCO Schematic

<div align="center">
    <img src="https://github.com/user-attachments/assets/9531007a-a4e5-4ca2-b164-65e4596979cc" alt="VCO Schematic">
</div>

### Complete PLL Schematic

<div align="center">
    <img src="https://github.com/user-attachments/assets/ae68de16-2d67-46e3-a6fa-6018936d545a" alt="Complete PLL Schematic">
</div>

## Simulation Results

### Transient Response

<div align="center">
    <img src="https://github.com/user-attachments/assets/495f7462-5668-48bd-86a0-f0521a68f5b8" alt="Transient Response Schematic">
</div>

- The VCO consists of 4 NOT gates in which 3 are inside a loop making it a 3-stage VCO.<br>
- Time of one cycle= 71.195328ns-71.419819ns = 0.224491ns. Giving a frequency of 1/t= 4.4545GHz.

## Conclusion
Summarizes the performance and success of the PLL design, noting key achievements in frequency stability, low jitter, and fast locking time.

## Future Work
- **Prototyping and Testing**: Extend the design for physical prototyping and testing in real-world SerDes systems.
- **Optimization**: Further tuning for different process technologies and broader frequency ranges.

## References
List of references and academic papers cited in the project:

1. P. D. D. K. O. A. a. K. S. R. K. P. P. Sreehari, "Power optimized PLL implementation in 180nm CMOS technology," 18th International Symposium on VLSI Design and Test, pp. 1-2, 2014.
2. A. L. S. Loke, "A Versatile 90-nm CMOS Charge-Pump PLL for SerDes Transmitter Clocking," IEEE Journal of Solid-State Circuits, vol. 41, no. 8, pp. 1894-1907, August 2006.
3. H. K. S. G. K. M. P. a. P. S. R. Ahiwar, "Design High Frequency Phase Locked Loop Using Single Ended VCO for High Speed Applications," 2022 IEEE Conference on Interdisciplinary Approaches in Technology and Management for Social Innovation (IATMSI), pp. 1-6, 2022.
4. R. E. Best, *Phase-Locked Loops: Design, Simulation, and Applications*, 6th ed., New York, 2007.
5. R. J. Baker, *CMOS Circuit Design, Layout, and Simulation*, 3rd ed., Wiley-IEEE Press, 2010, p. 1208.
6. J. M. Rabaey, *Digital Integrated Circuits: A Design Perspective*, Prentice-Hall, Inc., 1996, p. 702.
7. Razavi, B. (1996), "Design of High-Speed, Low-Jitter Phase-Locked Loops for High-Frequency Applications."
8. Dongil Lee, Taeho Lee, Young-Ju Kim, and Lee-Sup Kim, "A 21%-Jitter-Improved Self-Aligned Dividerless Injection-Locked PLL With a VCO Control Voltage Ripple-Compensated Phase Detector," *IEEE Transactions on Circuits and Systems II: Express Briefs*, Vol. 63, No. 8, August 2016.
9. IEEE Standard for a Precision Clock Synchronization Protocol for Networked Measurement and Control Systems, IEEE Standard 802.3, 1983.
10. IEEE Standard for Verilog Hardware Description Language, IEEE Standard 1364, 1995.
11. IEEE Standards for Device Modeling, IEEE Standard 2700 Series, 2017.
12. IEEE Standard for Standard Delay Format (SDF) Language Reference Manual, IEEE Standard 1497.
13. IEEE Standard 1588, IEEE Standard for a Precision Clock Synchronization Protocol for Networked Measurement and Control Systems, 2019.

## Team Members and Mentors

- **Team Members**: Girish Arora, Madhav Anand, Aayush Raj, Niyati Bhateja
- **Mentors**: Dr. Anil Singh, Dr. Alpana Agarwal


# Low Dropout Voltage Regulator (LDO) Design

This repository contains the design and simulation of a **Low Dropout Voltage Regulator (LDO)** circuit, developed using Cadence Virtuoso. The project focuses on achieving high performance and stability for the given specifications, making it a valuable reference for CMOS LDO design.

## Table of Contents
- [Introduction](#introduction)
- [What is a Voltage Regulator?](#what-is-a-voltage-regulator)
  - [Applications and Use Cases](#applications-and-use-cases)
- [PMOS LDO vs. NMOS LDO](#pmos-ldo-vs-nmos-ldo)
  - [PMOS LDO](#pmos-ldo)
  - [NMOS LDO](#nmos-ldo)
  - [Main Issue with NMOS LDO](#main-issue-with-nmos-ldo)
- [Amplifier in LDO Circuit](#amplifier-in-ldo-circuit)
  - [Specifications](#specifications)
  - [Designed Specifications of the Balanced Amplifier](#Designed-Specifications-of-the-Balanced-Amplifier)
  - [Advantages of Balanced Amplifier](#advantages-of-balanced-amplifier)
- [Design Specifications (LDO Regulator)](#design-specifications-(LDO-Regulator))
- [Acknowledgements](#acknowledgements)

## Introduction
Voltage regulators are fundamental components in modern electronics, ensuring a stable and reliable power supply to circuits and devices. This project focuses on the design of a Low Dropout Voltage Regulator (LDO), which is a type of linear regulator designed to operate efficiently with minimal voltage differences between the input (Vdd) and output (Vout). By providing consistent voltage output under varying conditions, LDOs play a critical role in power management systems.

## What is a Voltage Regulator?
A voltage regulator is an electronic circuit that maintains a constant output voltage irrespective of variations in the input voltage or load conditions. It acts as a safeguard for sensitive components by preventing voltage fluctuations that can cause malfunctions or damage.

### Applications and Use Cases
Voltage regulators are widely used in:
- **Consumer Electronics**: Smartphones, laptops, and wearable devices.
- **Automotive Systems**: Power management in electric vehicles and infotainment systems.
- **Industrial Equipment**: Stable power supply for sensors and control systems.
- **Medical Devices**: Ensuring consistent operation of life-critical systems.
- **Telecommunication**: Powering networking equipment like routers and base stations.

***Need of an LDO Regulator**: Lets understand this with an example, For suppose you have a Mobile Phone whose battery is fully charged i.e. 100% (say, 5V). Now at the end of the day us being us, we have our mobile phones at 5% (say, 2.3V), but but but... in our devices we have hundreds of different components and each one needs a specific constant voltage (For eg: processor needs 0.5V, display needs 1.2V etc.). Thus for a varying battery input of 5V to 2.3V our components have a demand of a constant/fixed voltage and this demand is fulfulled by our LDO regulators or some other circuits working on the concept of LDO regulator.*

LDOs are particularly advantageous in low-noise, compact, and energy-sensitive applications due to their simplicity and high-performance characteristics.

## PMOS LDO v/s NMOS LDO

### PMOS LDO
In a PMOS-based LDO regulator, a PMOS transistor serves as the pass element. The gate of the PMOS transistor is controlled by a feedback loop to regulate the output voltage. PMOS LDOs are known for their low dropout voltage since the PMOS transistor does not require a significant additional voltage beyond the input to operate.

#### Advantages of PMOS LDO
- **Low Dropout Voltage**: Operates efficiently with minimal input-output voltage difference.
- **Simpler Control Circuitry**: Easier to design compared to NMOS-based counterparts.
- **Power Efficiency**: Ideal for low-power applications.

| ![PMOS LDO](https://github.com/HarshitSri-Analog/Low-Drop-Out-Voltage-Regulator/blob/main/Schematics%20%26%20Simulation/PMOS%20LDO%20ckt.png) | 
| :---: | 
| Fig 1: PMOS-LDO Regulator |

### NMOS LDO
An NMOS-based LDO regulator uses an NMOS transistor as the pass element. However, unlike the PMOS design, NMOS transistors require a higher gate drive voltage to maintain conduction. This often necessitates the use of a charge pump or an additional circuit to boost the gate voltage, increasing complexity and power consumption.

| ![NMOS LDO](https://github.com/HarshitSri-Analog/Low-Drop-Out-Voltage-Regulator/blob/main/Schematics%20%26%20Simulation/images.jpeg) | 
| :---: | 
| Fig 2: NMOS-LDO Regulator |

#### Main Issue with NMOS LDO
The primary drawback of NMOS LDOs is the need for a higher gate drive voltage, which can result in:
- **Increased Dropout Voltage**: The NMOS pass element requires a larger voltage overhead, making it less efficient in low-dropout scenarios.
- **Complex Gate Drive Circuitry**: Requires additional components like charge pumps, leading to higher design complexity and power consumption.

## Amplifier in LDO Circuit
The amplifier used in this LDO design is not a conventional operational amplifier but a **balanced amplifier**, which provides superior performance for this application.

### Specifications
- **High Gain**: Ensures accurate regulation of the output voltage.
- **Wide Unity Gain Bandwidth (UGB)**: Facilitates faster response to load and line variations.
- **Phase Margin**: Designed to ensure stability under all operating conditions.

The detailed design and analysis of the balanced amplifier are provided in the repository under the documentation section [here](https://github.com/HarshitSri-Analog/Low-Drop-Out-Voltage-Regulator/blob/main/Balanced%20Amplifier.pdf). 

### Designed Specifications of the Balanced Amplifier
| **Parameter**       | **Value**       |
|---------------------|-----------------|
| Voltage Gain        | 55 dB          |
| Unity Gain Bandwidth (UGB) | 13.42 MHz    |
| Phase Margin        | 69.42 degrees  |
| Power Consumption   | 0.28 mW        |

This amplifier's performance significantly contributes to the accuracy and stability of the LDO Regulator circuit.

### Advantages of Balanced Amplifier
- **Enhanced Stability**: Achieves a better phase margin, minimizing the risk of oscillations.
- **High Precision**: Maintains tight control over the output voltage despite variations in input voltage or load.
- **Reduced Noise**: Balanced design helps in achieving low output voltage ripple, suitable for sensitive applications.

## Design Specifications (LDO Regulator)

| **Specification**              | **Given**            | **Achieved**         |
|---------------------------------|----------------------|----------------------|
| Output Voltage (Vout)          | 1.8V                | 1.807V              |
| Input Voltage (Vdd)            | 3.3V to 2V          | -                   |
| Load Current (Iload)           | 0.5mA to 10mA       | -                   |
| Reference Voltage (Vref)       | 1.2V                | 1.2V                |
| Feedback Current (Ifb)         | 20µA                | 20.11uA             |
| Unity Gain Bandwidth (UGB)     | ≥ 5MHz              | 5.735MHz            |
| Phase Margin                   | > 60°               | 63.85°              |
| Output Voltage Range (Vdd Var) | -                   | 8.55mV              |
| Output Voltage Range (Iload Var)| -                   | 2.17mV             |

## Acknowledgements
Special thanks to [Cadence Virtuoso](https://www.cadence.com/en_US/home/tools/custom-ic-analog-rf-design/virtuoso-studio.html) team for providing an advanced platform for analog design & simulation. Additionally, gratitude is extended to [Analog Layout & Design](https://youtube.com/@analoglayoutdesign2342?si=MGVNuvAb5QREWzpp) channel for providing such an informative lecture on [Designing LDO Regulator Circuit](https://youtu.be/kuY9KpJeZW0?si=XeTRorBCeDtmaaFk). 

Feel free to explore the repository for insights into the design and implementation of LDO Volateg Regulator. Contributions and feedback are welcome!

***If you find this repository helpful, please consider giving it a ⭐!***

# OpenFASOC

Fully Open-Source Autonomous SoC Synthesis using Customizable Cell-Based Synthesizable Analog Circuits The FASoC Program is focused on developing a complete system-on-chip (SoC) synthesis tool from user specification to GDSII with fully open-sourced tools.

## Prerequisites

Please build the following tools:

Magic https://github.com/RTimothyEdwards/magic

Netgen https://github.com/RTimothyEdwards/netgen

Klayout https://github.com/KLayout/klayout Please use this command to build preferably: ./build.sh -option '-j8' -noruby -without-qt-multimedia -without-qt-xml -without-qt-svg

Yosys https://github.com/The-OpenROAD-Project/yosys

OpenROAD https://github.com/The-OpenROAD-Project/OpenROAD (commid id: 7ff7171)

open_pdks https://github.com/RTimothyEdwards/open_pdks

open_pdks is required to run drc/lvs check and the simulations
After open_pdks is installed, please update the open_pdks key in common/platform_config.json with the installed path, down to the sky130A folder
Other notice:

Python 3.7 is used in this generator.
All the required tools need to be loaded into the environment before running this generator.

## Design Generation

### Temperature Sensor generator

This page gives an overview of how the Temperature Sensor Generator (temp-sense-gen) works internally in OpenFASoC.

#### Circuits

This generator creates a compact mixed-signal temperature sensor based on the topology from this paper <https://ieeexplore.ieee.org/document/9816083>.

It consists of a ring oscillator whose frequency is controlled by the voltage drop over a MOSFET operating in subthreshold regime, where its dependency on temperature is exponential.
Block diagram of the temperature sensor’s circuit

The physical implementation of the analog blocks in the circuit is done using two manually designed standard cells:
![tempsense_ckt](https://user-images.githubusercontent.com/110079631/199317479-67f157c5-6934-470b-8552-5451b1361b9c.png)


#### Block Diagram
![photo_2022-11-02 10 43 24](https://user-images.githubusercontent.com/110079631/199403863-d02e56c8-40ad-417f-9002-d7130cf23770.jpeg)

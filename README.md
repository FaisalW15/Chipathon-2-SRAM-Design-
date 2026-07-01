# Chipathon 2 SRAM Design
This is a schematic design of a 32x4 SRAM for AI Accelorators as part of the Chipathon 2 competition 2026 by KACST. 
The team consisted of four members and the SRAM was designed using SiemensEDA. I served as the head Digital Engineer and Architect,
with my main contributions being the design of the Row Decoder, Selection Multiplexers, and overall optimization of the system.


# Introduction 
As we step further into the fourth industrial revolution, AI continues to play a greater role
shaping the future and enabling organizations. Due to the massive amounts of data being
shifted around in AI applications such as Large Language Models, the need for a memory with
lower access-time increases.
Our aim is to design a functional SRAM that reduces the access-time and propagation-delay as
much as possible, and this will be done by creating multiple potential designs for each
functional block and comparing their propagation-delay and selecting the design with the least
propagation-delay.

# Overview
The internal SRAM architecture is comprised of 4 major blocks: The Row Decoder, an
array of 6T SRAM cells, Selection Multiplexers and Sense Amplifiers.

The row decoder receives an address and selects one wordline, the mutiplexer selects
which bitline to read or write, and the Sense Amplifier compares the voltage of the bitline
with it's negative counterpart to select the highest and amplify the signal.
The 6-Transistor SRAM bit cell has the capacity to store 1 bit, and is connected to
bitlines on either side that are precharged when reading or are driven by write drivers
when writing.

Key transistor-level decisions include splitting the transistor gates to two fingers within
multiple blocks, and sizing the PMOS transistors to be twice the size of the NMOS
tranistors to pass a stronger HIGH signal.

To achieve a high access-time and lower propagation-delay, the main trade-off was with
area due to increased amount of gates and a slight increase in power consumption.

# Methodology
The design flow started with constructing potential schematics with
different design decisions, verifying functionality and propagation delay
and power consumption through the simulation to select the best design.

Each team member was responsible for the design and testing of one
functional block, with the system integration being a team effort.

# Decoder Design
The decoder was designed to achieve as low propagation delay as possible, and was selected based on what design would give the lowest amount of stages
and lowest logical effort in order to increase the access time.

![image alt](https://github.com/FaisalW15/Chipathon-2-SRAM-Design-/blob/main/3to8_decoder.png?raw=true)

# Multiplexer Design
The multiplexer was designed using transmission gates in order to maintain signal integrity for both 1's and 0's.

![image alt](https://github.com/FaisalW15/Chipathon-2-SRAM-Design-/blob/main/multiplexer.png?raw=true)

# Sense Amplifier
The sense amplifer detects the small voltage swings on the bitlines coming from the multiplexer during a read operation to either set it to VDD or GND.

![image alt](https://github.com/FaisalW15/Chipathon-2-SRAM-Design-/blob/main/senseAmplifier.png?raw=true)

# SRAM Top View
This is the overall top view schematic of the entire circuit upon system integration.

![image alt](https://github.com/FaisalW15/Chipathon-2-SRAM-Design-/blob/main/SRAM_Top_View.png?raw=true)

# SRAM Results Waveform
This is the final waveform of the SRAM showcasing the fully functional system.

![image alt](https://github.com/FaisalW15/Chipathon-2-SRAM-Design-/blob/main/SRAM_Results_Waveform.png?raw=true)

# Results 
This is a brief of the improvement the team was able to achieve by the end of the competition.

![image alt](https://github.com/FaisalW15/Chipathon-2-SRAM-Design-/blob/main/SRAM_Overall_Stats.png?raw=true)

# Future Improvements
- Increasing sense amplifer sensitivity
- Using pass transistors instead of transmission gates where applicable to decrease access time
- Using cascaded buffers to decrease capacitance on the Word Lines
- High-skew inverters to decrease transistor size
- Decreasing power-consumption

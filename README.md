# Chipathon-2-SRAM-Design-
This is a design of an SRAM for AI Accelorators as part of the Chipathon 2 competition 2026 by KACST.

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

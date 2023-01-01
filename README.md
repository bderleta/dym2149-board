# dym2149-board
Dual YM2149 synth board design

An application of ATMega32 in PDIP package capable of driving two of YM2149 PSG chips. Reference firmware is just passing packets to selected PSG, but possibilities are very wide.

# Features

- ATMega32 PDIP, clocked with 16MHz XTAL
- 10 pin ISP (KANDA) and JTAG ports 
- Two sockets for YM2149 PSG chips, independent control lines, shared data/address line
- DIP8 socket for SPI flash/RAM
- 595 shift register with 8 pin output header, controlled via SPI, for debugging/driving peripherals
- Headers for both I/O ports of each PSG
- 32768 Hz secondary oscillator for CPU Timer2
- Requires DIP8/DIP14 CXO for clocking YM chips
- Revision 1a design features separate mixer board to enable developing various output stages (different chip/channel assignments, active opamp stage, etc)

![Rev 1a board render](/ym2149.png)

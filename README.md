# dym2149-board
Dual YM2149 synth board design using retro technology (THT elements, DIP packages)

![Rev 2 board render](/assets/ym2149-front.png)

An application of ATMega32 8-bit MCU in PDIP package capable of driving two of YM2149 PSG chips. [Reference firmware](https://github.com/bderleta/dym2149-firmware-ph) is just passing packets to selected PSG, but possibilities are very wide.

# Revision 2 changes

-  `U595_SRCLR` and `U595_RCLK` are swapped, to put `RCLK` to pin `OC0`, allowing to strobe `RCLK` pin from Timer0 compare output. This way the onboard shift register can be driven fully asynchronously, as `SRCLK` and `SER` are driven by SPI peripheral. Attention must be paid when SRAM/flash is used in the application.
- `YM1_BC1` and `YM1_SEL` are swapped, to put `YM1_SEL` to pin `OC1B`, allowing to switch `YM1_SEL` pin from Timer1 compare output. `YM2_SEL` is already on `OC1A` in all revisions. As `SEL` pin divides internal PSG clock by 2, in theory it should also divide an output frequency by 2, leading to sound an octave lower than before, although it has to be tested if any interesting effects can be obtained this way.
- Placement of I2C and UART ports has been slightly changed.

# Features

- ATMega32 MCU in PDIP package, clocked with external 16MHz crystal oscillator
- 10 pin ISP (KANDA) and JTAG ports 
- Two sockets for YM2149 PSG chips, independent control lines, shared data/address line
- DIP8 socket for SPI flash/RAM
- 595 shift register with 8 pin output header, controlled via SPI, for debugging/driving peripherals
- Headers for both I/O ports of each PSG
- 32768 Hz secondary oscillator for CPU Timer2
- Requires DIP8/DIP14 CXO for clocking YM chips
- Revision 1a/2 design features separate [mixer board](https://github.com/bderleta/dym2149-oric-mixer) to enable developing various output stages (different chip/channel assignments, active opamp stage, etc)

![Rev 2 board render](/assets/ym2149-top.png)

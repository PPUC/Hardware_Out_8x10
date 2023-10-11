# Lamp Matrix PCB for PPUC Project
This is the hardware for a LED lamp matrix card which was designed for the PPUC pinball project, but can be useful in other applications as well. The intentionally usecase is to connect a original equipped pinball playfield (including cable harness). Normally I'd prefer a serial WS2812 LED strip to do a DIY pinball but if all the LEDs and cables are in place already, it is useful to connect the lamp matrix directly (for LED use only, not for incandescent bulbs as power of the outputs is limited).
It is designed for being low cost and functional for experimental use.  
Not everything is tested nor does it fulfill EMC or any other specifications.  
Use at your own risk!
To make use of anything of this project a basic understanding of electronics and programming is necessary. Nothing of it is "plug and play". I'm surely not liable for any damage to assemblies, pinball machines or even persons.

## Name
Out_8x10 as it has 18 outputs. 8 high side switches and 10 low side switches which can form a 8x10 matrix but could also be used as simple high side and low side outputs.  

## Power Supply
The IO card must be supplied by 5 V (+-0.5 V) for logic and nominal 20 V for outputs. As these outputs are open source and open drain, the 20 V supply can actually be up to 26 V. In the circuit diagram the voltage is called 20 V.

## Controller
A RP2040 is used for it's cost/performance ratio. It is the same controller that is used in the Raspberry Pi Pico.

## Communication Interfaces
* RS_485: main communication interface for controlling outputs and scan inputs. Usually connected to a host interface like a PC or Raspberry Pi or similar.
* USB C: for programming, debug and flashing
* Serial Wire: alternative for programming, debug and flashing

## Switches (on board)
* Reset: hardware reset for controller (RP2040)
* Boot: if active, the board connects to a PC like an USB stick. Usually used for programming the code into the flash memory on the board.
* DIP-switches: usually used to select an address for RS485 (16 combinations)

## High Side Switch Outputs
There are 8 outputs featuring a high side switch, usually used for lamp coloums. The voltage is derived form 20 V power connection. Current and power is limited by a linear regulator (78L24) wich is actually not used for regulating the voltage but to protect the switch form overload in case of a short circuit. Each output can drive a constant current of 100 mA witch is normaly sufficiant for 10 LED lamps (e.g. 10 rows of LEDs). Short term peak current is about 300 mA. The 20 V supply can actually range from 7 V to 26 V.

## Low Side Switch Outputs
There are 10 outputs featuring a low side switch, usually used für lamp rows. The outputs are open drain and drive currents up to 3 A with a load connected to a voltage of up to 30 V.

## Special Output
One special output is available for high speed signals. The voltage is 5 V, it is a push pull output that can drive a current up to 8 mA. It can be used to e.g. control a WS2812 LED strip.





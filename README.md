# ZX-Interface-1-Replacement-ROM-Programming-Adapter
Programming adapter for the ZX Interface 1 Replacement ROM.

This is the programming adapter that is required to allow reprogramming of the ZX Interface 1 Replacement ROM.

You need to link J1 Pins 1-8 on the adapter PCB to J1 Pins 1-8 on the ROM PCB and select the correct SST39SF device on the programmer. See the ROM folder for more information on layout of the ROM and where to place the ROM images.


It can also be used to reprogram the Retroleum 24-pin switchable ROM replacement module with a bit of faffing about. See the relevant picture in the pictures folder for connection details.


The Retroeleum ROM unused connector is wired as follows starting from the left pin.

A12, ~WE, A14, A13, ~CE

and is configured in the following manner,

A12 - connected to 24 Pin Socket Pin 21 and is left unconnected.

~WE pulled Hi by 10K resistor in normal operation. Can be overidden by programmer. Connect to J1 pin 1 to program.

A14 pulled Lo by 10K resistor in normal operation. Can be overidden by programmer. Connect to J1 Pin 6 to program.

A13 pulled Lo by 10K resistor in normal operation. Can be overidden by programmer. Connect to J1 Pin 7 to program. This can be used in the Interface 1 to allow the use of 16K ROM images. 

~CE pulled Lo by 10K resistor in normal operation. Can be overidden by programmer. Connect to J1 Pin 8 to program.


A15 selects ROM to use by the switch, pulls line Hi via 10K to 5V or Lo via short to Gnd. Manually switched when programming.

A16 permanently connected to Ground. Cannot be overridden by programmer.


To program,

1 - Select the correct device SST39SF010 DIP32.

2 - Add wires for ~WE, A14, A13 and ~CE. See picture for details.

3 - Device ID 'should' work but programmer should complain with a Pin 2 connection error. Turn OFF Pin Detect.

4 - Erase EEPROM.

5 - Set Switch to A.

6 - Load ROM A at offset 0x00000

7 - Program

8 - Set Switch to B.

9 - Load ROM B at offset 0x00000

10 - Program - Ensure that Erase before Programming is NOT selected.

You should now have two ROMs programmed and can be selected by the switch. 


If using 16K ROM images, connect A13 on the unused connector to address A13 on the Interface 1. This can be found on the Spectrum Edge Connector. See picture for details. 

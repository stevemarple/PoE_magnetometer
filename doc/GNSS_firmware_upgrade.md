# GNSS firmware upgrade instructions

## Introduction

The firmware on the GNSS module should only be updated if required.  The microcontroller does not have the means to update the firmware so the GNSS serial data lines must be accessed directly. In normal use the microcontroller is driving the GNSS module serial RX input. One method to disconnect the microcontroller is to remove it from its IC socket (after having removed the Ethernet shield). A less invasive method is to keep the microcontroller in its reset state so that its GPIO connections are placed into a high-impedance state and are effectively disconnected. The second method is preferred. IT is not necessary for the GNSS antenna to be connected during this process.

## Requirements

* A Windows 10 PC.
    * A serial program such as with Teraterm or putty should be installed.
    * The NVS firmware updater program `PatchWriter` should be installed.
* Three jumper wires, each approximately 100 mm long. Wires terminated with male 0.1" header pins are ideal but AWG 24 solid code wire with 6 mm of insulation removed from each end could also be used.
* The latest firmware for the GNSS module. Ensure you use the firmware for the exact hardware version present as programming the firmware intended for a different hardware version can render the module inoperable.

## Force microcontroller into reset state

Connect the microcontroller's USB interface to a Windows 10 PC. Use a serial terminal program such as Teraterm or putty to read the serial data from the MCP2200 USB serial port emulator. Ensure local echo is on, hardware and software flow control are both off, and that lines are terminated with `CR` and `LF`.
The default connection serial details used are 115200 baud, 8 bits, no parity, and one stop bit (often referred to as `115200 8N1`). Verify that the serial log output can be read. Insert a jumper wire from the `RESET` pin on the Ethernet shield to `GND`. The serial output should stop. If the wire is temporarily removed for a few seconds the initial boot messages from the microcontroller should be sent over the serial connection, and should include information about the MCU model and firmware version. 

Ensure the wire is connected and that the flow of serial data has stopped. 

## Connect the external USB interface to the GNSS module

With the microcontroller still held in reset connect one jumper wire from Arduino pin number `1` to Arduino pin number `2`. Connect a second wire from Arduino pin number `0` to Arduino pin number `3`. Ignore any break messages on from the serial terminal, they are due to the wrong baud rate.

Select the correct baud rate for the GNSS module, the default connection details are 9600 baud, 8 bits, no parity, and one stop bit (`9600 8N1`). The serial program should show messages from the GNSS module (probably `$GNGGA` and `$GNRMC` although variations on `$GxGGA` and `$GxRMC` are possible depending on the satellite constellation(s) used in the position calculation).

The current firmware can be identified by sending the command
```
$POVER*5E
```
The module should respond with an NMEA sentence of the form
```
$ALVER,NVS,CSM54,0504*76
```
This shows that the module is manufactured by NVS Technologies (`NVS`), it is a CSM module version 5.4 (`CSM54`) and that the current firmware version is 5.4 (`0504`). 

## Use PatchWriter to update the firmware

Run the PatchWriter software. It should identify the hardware version and existing firmware version. Follow the PatchWriter instructions to upgrade the firmware. Do not remove the power or serial connection whilst it is upgrading, and ensure the firmware upgraded has suceeded.

## Remove jumper wires

Remove the two jumper wires which redirect the serial port connection **before** the wire which holds the microcontroller in its reset state.

## Confirm riometer operation

Use the `screen` command to observer correct operation of the data logging process.

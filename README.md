# RB-PRO4: Pan-Tilt System
A construction comprised of two joints with two degrees of rotational freedom, pan and tilt. Each joint is equipped with a DC motor and encoder, which are sensed using an FPGA and then regulated using a PID controller implemented via a MCU; the system is interfaced using a Joystick for movement control and CLI for command control.

![Cad Model][cad-model-gif]

The main objective of the project is to develop a stable and responsive system controller in accordance with specified [system requirements](#system-requirements). The robot must respond appropriately when interfaced with a joystick, even in the presence of potential disturbances.

[cad-model-gif]: https://raw.githubusercontent.com/rb-pro4-f19/Overleaf/master/assets/img/cad_model.gif

---

##### Table of Contents

* [System Architecture](#system-architecture)
* [System Requirements](#system-requirements)
* [Interfacing](#interfacing)
	+ [Console Interface (UART)](#console-interface--uart-)
	+ [Intersystem Communication (SPI)](#intersystem-communication--spi-)
	+ [FPGA Debugging (UART)](#fpga-debugging--uart-)
* [Controller](#controller)

---

## System Architecture
The system is comrpised of three main components, which together control the Pan-Tilt robot:

- Command Line Interface ([CLI][cli])
- TM4C Microcontroller ([MCU][mcu])
- Field Programmable Gate Array ([FPGA][fpga])

The MCU is interfaced via a console over a UART serial connection, enabling users to enter system commands. Movement control of the robot is achieved using a joystick connected to the MCU, which acts as the system controller. Intersystem communication between the FPGA and MCU is facilitated using SPI, with the MCU as master. The FPGA allows for direct data collection using a UART output for debugging, enabled via the MCU console.

![system_architecture]

Information regarding the system components can be found in their respective read-me files of their repositories. ~~A table of system commands can be found [here][table_cli].~~

[system_architecture]: https://raw.githubusercontent.com/rb-pro4-f19/Overleaf/master/assets/img/system_architecture.jpg
[table_cli]: #system-architecture
[cli]: https://github.com/rb-pro4-f19/CLI
[mcu]: https://github.com/rb-pro4-f19/MCU
[fpga]: https://github.com/rb-pro4-f19/FPGA

## System Requirements
Text.

## Interfacing


### Console Interface (UART)
Text.

### Intersystem Communication (SPI)
Data between the MCU (master) and FPGA (slave) is transmitted using SPI and a custom 16-bit frame format and communication protocol. ~~The command table can be found [here][table_spi]~~.

##### Configuration
The standard Freescale protocol is configured to `16-bit` frames with a transmission rate of `8 Mb/s` in `Mode 0`.

##### Frame Format
The `16-bit` frame are comprised of an address, data and checksum field, with varying sizes: respectively `ADDR:4`, `DATA:8` and `CHKSUM:4`. Response frames from FPGA to MCU omits the address fields and consists instead of respectively `DATA:12` and `CHKSUM:4`.

![frm_format]

##### Protocol
Frames transmitted to the FPGA must be acknowledged with a frame of valid checksum, although the content of the frame may be disregarded. Checksum is calculated using the [BSD algorithm][bsd_wiki] on the 12 most-significant bits of a frame.

[table_spi]: #intersystem-communication--spi-
[bsd_wiki]: https://en.wikipedia.org/wiki/BSD_checksum
[frm_format]: https://raw.githubusercontent.com/rb-pro4-f19/Overleaf/master/assets/img/spi_frames.jpg

### FPGA Debugging (UART)
Text.

## Controller
Text.

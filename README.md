# RB-PRO4: Pan-Tilt System
A construction comprised of two joints with two degrees of rotational freedom, pan and tilt. Each joint is equipped with a DC motor and encoder, which are sensed using an FPGA and then regulated using a PID controller implemented via a MCU; the system is interfaced using a Joystick for movement control and CLI for command control.

![Cad Model][cad-model-gif]

The main objective of the project is to develop a stable and responsive system controller in accordance with specified [system requirements](#system-requirments). The robot must respond appropriately when interfaced with a joystick, even in the presence of potential disturbances.

[cad-model-gif]: https://github.com/rb-pro4-f19/Overleaf/blob/master/assets/img/cad_model.gif

---

##### Table of Contents

* [System Architecture](#system-architecture)
* [System Requirements](#system-requirments)
* [Interfacing](#interfacing)
	+ [Console Interface (UART)](#console-interface--uart-)
	+ [Intersystem Communication (SPI)](#intersystem-communication--spi-)
	+ [FPGA Debugging (UART)](#fpga-debugging--uart-)
* [Controller](#controller)

---

## System Architecture
The MCU is interfaced via a CLI using UART enabling users to interact with the system, whereas movement control of the robot is achieved using a joystick connected to the MCU. Intersystem communication between the FPGA and MCU is facilitated using SPI, with the MCU as master.

![System Arhictecture](https://github.com/rb-pro4-f19/Overleaf/blob/master/assets/img/system_architecture.jpg)

Links to the components of system.

## System Requirements
Text.

## Interfacing
Text.

### Console Interface (UART)
Text.

### Intersystem Communication (SPI)
Data between the MCU (master) and FPGA (slave) is transmitted using SPI and a custom 16-bit frame format and communication protocol.

##### Configuration
The standard Freescale protocol is configured to `16-bit` frames with a transmission rate of `8 Mb/s` in `Mode 0` `(SPO: 0 SPH: 0)`.

##### Frame Format
The `16-bit` frame are comprised of an address, data and checksum field, with varying sizes: respectively `ADDR:4`, `DATA:8` and `CHKSUM:4`. Response frames from FPGA to MCU omits the address fields and consists instead of respectively `DATA:12` and `CHKSUM:4`.

<div class="tg-wrap"><table>
  <tr>
    <th colspan="3">Test</th>
  </tr>
  <tr>
    <td>Address</td>
    <td>Data</td>
    <td>Checksum</td>
  </tr>
</table></div>

#### Protocol
Frames transmitted to the FPGA must be acknowledged with a frame of valid checksum, although the content of the frame may be disregarded. Checksum is calculated using the BSD algorithm on the 12 most-significant bits of a frame.

### FPGA Debugging (UART)
Text.

## Controller
Text.

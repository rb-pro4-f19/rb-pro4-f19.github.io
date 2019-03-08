# RB-PRO4: Pan-Tilt System
A construction comprised of two joints with two degrees of rotational freedom, pan and tilt. Each joint is equipped with a DC motor and encoder, which are sensed using an FPGA and then regulated using a PID controller implemented via a MCU; the system is interfaced using a Joystick for movement control and CLI for command control.

![Cad Model][cad-model-gif]

The main objective of the project is to develop a stable and responsive system controller in accordance with specified [system requirements](#system-requirments). The robot must respond appropriately when interfaced with a joystick, even in the presence of potential disturbances.

[cad-model-gif]: https://github.com/rb-pro4-f19/Overleaf/blob/master/assets/img/cad_model.gif

---

##### Table of Contents

* [System Architecture](#system-architecture)
* [System Requirments](#system-requirments)
* [Interfacing](#interfacing)
	+ [Console Interface (UART)](#console-interface--uart-)
	+ [Intersystem Communication (SPI)](#intersystem-communication--spi-)
	+ [FPGA Debugging (UART)](#fpga-debugging--uart-)
* [Controller](#controller)

---

## System Architecture
The MCU connects to a CLI using serial connection, enabling users to interact with the system. Control of the Pan-Tilt system is achieved using a joystick connected to the MCU, where communication (motor PWM and encoder data) is facilitated by parallel connections to an FPGA with multiple SPI modules.

![System Arhictecture](https://github.com/rb-pro4-f19/Overleaf/blob/master/assets/img/system_architecture.jpg)

Links to the components of system.

## System Requirments
Text.

## Interfacing
Text.

### Console Interface (UART)
Text.

### Intersystem Communication (SPI)
Text.

### FPGA Debugging (UART)
Text.

## Controller
Text.

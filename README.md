# emeir-pulse
Monitor the counter of an electricity meter with Arduino and light sensor.

This repository is a fork of the [emeir](https://github.com/skaringa/emeir) project by Martin Kompf. This fork is alternative firmware, which runs on the same hardware but with a "simplified" sensor, to use the "emeir" hardware on modern digital electricity meters which send light pulses with an (infrared) LED.

![Electricity meter with light sensor](https://raw.githubusercontent.com/wiki/M-Reimer/emeir-pulse/images/digital_meter_sensor.jpg)


The software consists of two parts:

* Data acquisition part running on an Arduino Nano. It controls a light sensor, detects trigger levels, skips pulses if so desired and communicates with a master computer over USB serial.
* Data recording part running on a the master computer (Raspberry Pi). It retrieves the data from the Arduino over USB serial and stores counter and consumption values into a round robin database.

More information about circuit, setup and calibration can be found in the project [Wiki](https://github.com/M-Reimer/emeir-pulse/wiki).

## Commands from host (RasPi) to Arduino

* __D__ - retrieve and print raw data
* __T__ - enter trigger mode and print trigger data (0/1)
* __S__ _low_ _high_ - Set trigger levels (e.g. 85 90)
* __C__ - Cancel data acquisition and enter command mode

Arduino is in trigger mode upon start - Send __C__ to enter command mode

## Schematics

![Schematics](https://raw.githubusercontent.com/wiki/M-Reimer/emeir-pulse/images/pulsesensor.png)

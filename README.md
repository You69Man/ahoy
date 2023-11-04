[![CC BY-NC-SA 4.0][cc-by-nc-sa-shield]][cc-by-nc-sa]
[![Ahoy Build][release-action-badge]][release-action-link] [![Ahoy Dev Build][dev-action-badge]][dev-action-link]

This work is licensed under a
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa].

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

[cc-by-nc-sa]: https://creativecommons.org/licenses/by-nc-sa/4.0/deed.de
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png
[cc-by-nc-sa-shield]: https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg

[release-action-badge]: https://github.com/lumapu/ahoy/actions/workflows/compile_release.yml/badge.svg
[release-action-link]: https://github.com/lumapu/ahoy/actions/workflows/compile_release.yml

[dev-action-badge]: https://github.com/lumapu/ahoy/actions/workflows/compile_development.yml/badge.svg
[dev-action-link]: https://github.com/lumapu/ahoy/actions/workflows/compile_development.yml


# 🖐 Ahoy!
![Logo](https://github.com/lumapu/ahoy/blob/main/doc/logo1_small.png?raw=true)

This repository provides hardware and software solutions for communicating with Hoymiles inverters via radio. Our system allows you to easily obtain real-time values, such as power, current, and daily energy, as well as set parameters like the power limit of your inverter to achieve zero export. You can access these functionalities through our user-friendly web interface, MQTT, or JSON. Our solutions simplify the process of monitoring and fine-tuning your solar panel system to help you achieve your goals.

## Changelog
[latest Release](https://github.com/lumapu/ahoy/blob/main/src/CHANGES.md)
[Development Version](https://github.com/lumapu/ahoy/blob/development03/src/CHANGES.md)


--- Fork information ---

This fork aims to improve the display layouts of several low-res displays

Current status of progress Nokia5110:
- Nokia5110: improved layout with additional fixed headline for day of week, date and time, and centered text (already merged in lumapu >=0.7.34)
- improved 5x8 pixel font (some glyphes like dot and zero were deformed) and enhanced by ahoy specific symbols (already merged in lumapu >=0.7.50)
- added sun and moon symbols with values that show number of producing and sleeping inverters (already merged in lumapu >=0.7.50)
- added calender and sigma symbols for YieldDay and YieldTotal (already merged in lumapu >=0.7.50)
- added symbol for WiFi and MQTT that indicates WiFi and MQTT connection status (already merged in lumapu >=0.7.50)
- added RSSI bar for WiFi (already merged in lumapu >=0.7.50)
- added symbol für NRF24 that indicates if radio board is connected (already merged in lumapu >=0.7.50)
- added RSSI bar for NRF24 (currently fed by quality information from the transition package heuristics to 'fake' radio RSSI)

![alt text](https://github.com/You69Man/ahoy/blob/feature/display_84x48_symbolic_PR/pics/PXL_20230824_204200660.jpg?raw=true)


Current status of progress OLEDs 128x64:
There is also already a working implementation for OLED 128x64, with a bit of a higher font and symbol resolution.
OLEDs however tend to quickly burn-in for which reason a screensaver is a must.

The currently implemented screensaver vor OLEDs is based on shifting pixels. The drawback of this kind of screensaver is, that not the whole screen can be used for the layout (or some of the pixels would "fall off" the screen).
So, moving the whole screen content is no good option for a layout that is very well optimized. 

Using the pixel shift screensaver reduced the new layout to following new features:
- layout with additional fixed headline for day of week, date and time, and centered text
- sun and moon symbols with values that show number of producing and sleeping inverters
- calender and sigma symbols for YieldDay and YieldTotal


--- New Motion Screensaver ---

There is a new option for new screensaver based on a motion detection sensor (PIR sensor). 
This requires a free GPIO pin and a PIR sensor.
When moving in front of the Ahoy, the display goes on automatically. After one minute without movement the display goes off again, to protect it against burn in.

Activating this option also adds the following features for the 128x64 pixel OLEDs:
- symbol for WiFi and MQTT that indicates WiFi and MQTT connection status
- RSSI bar for WiFi
- symbol für NRF24 that indicates if radio board is connected
- RSSI bar for NRF24 (currently fed by quality information from the transition package heuristics to 'fake' radio RSSI))

![alt text](https://github.com/You69Man/ahoy/blob/feature/display_84x48_symbolic_PR/pics/PXL_20230901_061927908.jpg?raw=true)


Table of approaches:

| Board  | MI | HM | HMS/HMT | comment | HowTo start |
| ------ | -- | -- | ------- | ------- | ---------- |
| [ESP8266/ESP32, C++](Getting_Started.md) | ✔️ | ✔️ | ✔️ |  👈 the most effort is spent here | [create your own DTU](https://ahoydtu.de/getting_started/) |
| [Arduino Nano, C++](tools/nano/NRF24_SendRcv/) | ❌ | ✔️ | ❌ | |
| [Raspberry Pi, Python](tools/rpi/) | ❌ | ✔️ | ❌ | |
| [Others, C/C++](tools/nano/NRF24_SendRcv/) | ❌ | ✔️ | ❌ |  |

⚠️ **Warning: HMS-XXXXW-2T WiFi inverters are not supported. They have a 'W' in their name and a DTU serial number on its sticker**

## Getting Started
1. [Guide how to start with a ESP module](Getting_Started.md)

2. [ESP Webinstaller (Edge / Chrome Browser only)](https://ahoydtu.de/web_install)

3. [Ahoy Configuration ](ahoy_config.md)

## Our Website
[https://ahoydtu.de](https://ahoydtu.de)

## Success Stories
- [Getting the data into influxDB and visualize them in a Grafana Dashboard](https://grafana.com/grafana/dashboards/16850-pv-power-ahoy/) (thx @Carl)

## Support, Feedback, Information and Discussion
- [Discord Server (~ 7.300 Users)](https://discord.gg/WzhxEY62mB)
- [The root of development](https://www.mikrocontroller.net/topic/525778)

### Development
If you encounter any problems, use the issue tracker on Github. Provide a detailed description of the issue and consider if it is related to our software. This will help us provide effective solutions.

**Contributors are always welcome!**

### Related Projects
- [OpenDTU](https://github.com/tbnobody/OpenDTU)
  <- Our sister project ✨ for Hoymiles HM- and HMS-/HMT-series (for ESP32 only!)
- [hms-mqtt-publisher](https://github.com/DennisOSRM/hms-mqtt-publisher)
  <- a project which can handle WiFi inverters like HMS-XXXXW-2T
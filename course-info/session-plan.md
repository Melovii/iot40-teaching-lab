# Session plan

Four sessions of 60 minutes each. Every session starts with a one-minute recap so it can be attended on its own.

| Session | Title | Course weeks | Learning outcomes |
| ------- | ----- | ------------ | ----------------- |
| 1 | The whole system | 1, 5, 6 | 1, 5 |
| 2 | Circuit and firmware | 1, 4, 7 | 2, 3 |
| 3 | The board in KiCad | 4, 7 | 2, 3 |
| 4 | End to end | 7, 9, 10, 11, 12 | 3, 4, 5, 6 |

Dates and room: TODO, to be confirmed with the instructor.

## Session 1 - The whole system

| Time | Block | Content |
| ---- | ----- | ------- |
| 0:00 - 0:15 | The loop and Industry 4.0 | Measure, decide, act. Where IoT already lives. Industry 1.0 to 5.0, digital twins, predictive maintenance |
| 0:15 - 0:35 | The IoT and AI stack | Five layers, radios and protocols, what AI does in IoT, from a fixed rule to a neural network |
| 0:35 - 1:00 | The circuit, built live | Voltage divider, shunt and op-amp, MOSFET switch, whole system running. Built in Tinkercad, shown on real hardware |

Ends with how the same skeleton fits other projects (smart home energy, health monitor, machine health, connected node).

## Session 2 - Circuit and firmware

Question: how do you trust a number from a circuit?

- Embedded constraints: memory, power, bandwidth, security
- ADC: resolution against accuracy, noise
- Filtering: RC low-pass, moving average, the noise and delay trade
- Calibration: offset, gain, two-point fit, checking against a multimeter
- Current sensing: shunt value as a compromise between signal and loss
- Switching: logic-level MOSFET, gate resistor, pull-down, flyback diode
- Power: LDO against buck, decoupling
- Firmware: sample, filter, decide, publish, obey commands, with safe defaults
- From signal to model: windows and features, labelled data, train/test split, where the model runs

## Session 3 - The board in KiCad

Question: how does a breadboard become a board?

- Schematic: symbols, nets, ERC
- Connecting the ESP32-S3 on headers
- Footprints and placement
- Kelvin sensing at the shunt
- Layout rules: trace width, decoupling, return path
- Grounding
- Power rails, protection, connectors, test points
- DRC and the 3D view
- Wireless on a board, power budget for battery devices, hardware that runs models

## Session 4 - End to end

Question: how do you get from a current to a decision?

- The physical build running
- MQTT: topics, broker, QoS, retained messages, last will
- Protocol map: MQTT, CoAP, Profinet, WirelessHART, M2M and M2C
- Dashboard and alert rules
- Machine learning workflow
- Detector 1: rolling z-score on the board
- Detector 2: isolation forest on the laptop
- Fault injection and results
- Closing the loop: alert, command, MOSFET off
- Reliability, edge or cloud, operations, cybersecurity
- Industry 5.0, cobots, V2V and AIoT; scaling to many nodes
- What the project does not prove

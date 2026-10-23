# IoT 4.0 course

Teaching materials for four one-hour sessions given alongside COM473, Internet of Things & Industry 4.0 (Electrical and Electronics Engineering, Faculty of Engineering). The sessions follow one small working project from the circuit up to the dashboard and the anomaly detector.

## Overview

The running example is an ESP32-S3 energy monitor for a low-voltage DC load (12 V or less, no mains). It measures voltage and current, filters the readings, publishes them over MQTT, shows them on a dashboard and flags abnormal consumption. When a power limit is exceeded, a MOSFET switches the load off.

```
sensors (V, I) -> ESP32-S3 (filter, decide) -> MQTT broker -> dashboard + model
        ^                                                          |
        +------------- MOSFET switches the load <------------------+
```

The project is deliberately small. It is the shortest complete path from a circuit to an AI layer, so every block of an IoT system can be shown working on one bench. The same sense, connect, decide, act structure applies to other projects, and students can pick their own for the Week 13-14 presentations.

Split of work:

- Besir Munajed: sensing and switching circuit, Tinkercad build, KiCad board.
- Zaid Safadi: ESP32-S3 firmware, MQTT broker, dashboard, anomaly detection.

Scope and limits:

- Low-voltage DC only.
- Faults are injected on the bench, not collected from real equipment.
- The KiCad board is designed and checked but not fabricated. The bench uses a breadboard equivalent.

## Sessions

| Session | Topic | Slides |
| ------- | ----- | ------ |
| 1 | The whole system: measure, decide, act. IoT and AI stack, Industry 4.0, circuit in Tinkercad | [slides](slides/session-1/) |
| 2 | Circuit and firmware: ADC, filtering, calibration, current sensing, MOSFET switching, power, firmware structure | [slides](slides/session-2/) |
| 3 | The board in KiCad: schematic, placement, routing, grounding, checks | [slides](slides/session-3/) |
| 4 | End to end: MQTT, dashboard, anomaly detection, reliability, security | [slides](slides/session-4/) |

Each session is 60 minutes and stands alone, with a one-minute recap of the system at the start. Agendas, course-week mapping and demos are in [course-info/session-plan.md](course-info/session-plan.md).

## Repository layout

- [course-info/](course-info/) - course description, weekly plan, learning outcomes, session plan
- [slides/](slides/) - slides for the four sessions
- [kicad/](kicad/) - schematic and board design, exported outputs
- [tinkercad/](tinkercad/) - simulated circuit and demo clips
- [firmware/](firmware/) - ESP32-S3 code
- [dashboard/](dashboard/) - MQTT dashboard (Node-RED)
- [models/](models/) - anomaly detection: z-score rule and isolation forest
- [docs/](docs/) - architecture, MQTT topics, safety notes, known limitations

## Requirements

Hardware:

- ESP32-S3 development board
- Current and voltage sensor with an I2C interface, and a shunt resistor
- Logic-level N-channel MOSFET, flyback diode, gate resistor and pull-down
- Low-voltage DC supply (12 V or less) and a resistive or small motor load
- Multimeter for calibration checks

Software:

- KiCad (version TODO)
- Tinkercad Circuits (browser)
- PlatformIO or Arduino IDE (TODO which one)
- MQTT broker (TODO which one)
- Node-RED
- Python 3 for the models (TODO packages and versions)

## Usage

1. Open the slides for the session in [slides/](slides/).
2. Circuit demos: open the Tinkercad link in [tinkercad/](tinkercad/README.md).
3. Board: open the project in [kicad/](kicad/README.md).
4. Firmware: copy the example config to a local config file, fill in Wi-Fi and broker details, then build and flash. See [firmware/](firmware/README.md).
5. Dashboard: import the flow into Node-RED. See [dashboard/](dashboard/README.md).
6. Models: see [models/](models/README.md) for training and evaluation.

Wi-Fi names, passwords, broker addresses and IP addresses stay out of the repository. They go in local files that are listed in .gitignore.

## Authors

- Besir Munajed
- Zaid Safadi

## License

TODO decide before sharing the repository

# Architecture

## Blocks

| Block | Role | Built by |
| ----- | ---- | -------- |
| Sense circuit | Divider for voltage, shunt for current, I2C sensor chip | Besir |
| Load switch | Logic-level MOSFET with gate resistor, pull-down and flyback diode | Besir |
| Power | 12 V input, protection, regulator to 5 V and 3.3 V | Besir |
| Board | KiCad schematic and layout | Besir |
| Firmware | Sample, filter, decide, publish, obey commands | Zaid |
| Broker | MQTT message routing | Zaid |
| Dashboard | Node-RED charts, gauge, alerts | Zaid |
| Model | Rolling z-score and isolation forest | Zaid |

## Layers

| Layer | In this project |
| ----- | --------------- |
| Sense | Voltage and current of a DC load |
| Connect | Wi-Fi and MQTT |
| Store | TODO where readings are logged |
| Analyse | z-score on the board, isolation forest on the laptop |
| Act | Alert on the dashboard, MOSFET switches the load |

## Data flow

1. The sensor measures voltage and current of the load.
2. The ESP32-S3 filters the readings and computes power.
3. The board publishes a measurement message to the broker.
4. The dashboard and the model subscribe to it.
5. A rule or the model raises an alert. A command goes back on a command topic.
6. The board switches the MOSFET.

## Where decisions run

The protective cut runs on the board. It works with the network down. The model adds alerts and can move the limit, but it does not act alone.

## Design choices

- The built-in ADC of the ESP32-S3 is 12-bit but noisy and not linear, so a dedicated sensor chip is used.
- MQTT suits constrained devices: small messages, one sender and many listeners, and a broker so the parts stay decoupled.
- A dev board on sockets keeps the PCB simple. A bare module would need its own reset and boot circuit, USB, decoupling and antenna keep-out.

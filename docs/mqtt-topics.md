# MQTT topics

Topic names are our own naming for this project, not a standard.

| Topic | Direction | Content |
| ----- | --------- | ------- |
| energy/node1/power | board -> broker | Measurement message (JSON) |
| TODO | board -> broker | Node status, retained, with last will "offline" |
| TODO | dashboard -> board | Command: load on or off |
| TODO | board -> broker | Alert |

## Measurement message

JSON, one message per sample or window.

| Field | Unit | Meaning |
| ----- | ---- | ------- |
| TODO | V | Voltage |
| TODO | A | Current |
| TODO | W | Power |
| TODO | - | Timestamp or sequence number |

## Settings

- QoS: TODO
- Retained: status topic only (TODO confirm)
- Last will: set on connect, published by the broker if the board vanishes
- Authentication and TLS: TODO

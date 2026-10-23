# kicad

KiCad project for the energy monitor board. The board holds the sense circuit, the load switch, the power rails and the ESP32-S3 development board on headers.

Status: designed and checked with ERC and DRC. Not fabricated.

## Sections of the schematic

| Section | Contents |
| ------- | -------- |
| Power input | 12 V input, reverse-polarity protection, fuse sized above normal load current |
| Regulation | Regulator to 5 V and 3.3 V rails, decoupling |
| Sensing | Shunt in the load path, I2C sensor chip, I2C pull-ups |
| Switch | Logic-level N-channel MOSFET, gate resistor, pull-down, flyback diode |
| MCU | ESP32-S3 dev board on sockets, only the pins in use are connected |
| Connectors | Screw terminals for supply and load, test points for 3.3 V, ground, gate and shunt sense |

## Layout notes

- Parts grouped by function: power, sense, switch, ESP32 headers.
- Decoupling capacitors beside the supply pins they serve.
- Shunt close to the load connector. Two thin sense traces run from the shunt's own pads to the sensor (Kelvin connection).
- Load return current is kept out of the sense path. Grounds join at one point on a ground fill.
- Load trace width taken from KiCad's PCB Calculator (IPC-2221 method) for the actual current, copper weight and temperature rise.
- MOSFET and regulator get copper area and sit away from the sensor.
- Connectors on the board edge. The dev board's antenna keep-out is respected.

## Checks

- ERC on the schematic: TODO result
- DRC on the board: TODO result
- 3D viewer used to check connector and header positions

Clean checks show the board matches the rules set. They do not show that it works.

## Files

- exports/ - schematic PDF, board PDF, Gerbers if produced
- TODO project files (.kicad_pro, .kicad_sch, .kicad_pcb) and KiCad version

## Design values

TODO fill from the actual design: shunt value, MOSFET part, regulator part, sensor part, board size, layer count.

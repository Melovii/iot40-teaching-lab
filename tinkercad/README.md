# tinkercad

The sensing and control circuit as built in Tinkercad Circuits before the real hardware.

Circuit link: TODO

## What it covers

| Block | Description |
| ----- | ----------- |
| Voltage measurement | Resistor divider scales the load voltage into the ADC range |
| Current measurement | Shunt resistor in the load path, op-amp amplifies the small drop |
| Power | Computed in code as P = V x I |
| Switching | MOSFET switches a DC motor, with a flyback diode across it |
| Decision | Upper power limit turns the load off, a lower limit turns it back on |

## Example values

Example values used on the slides. The real circuit uses the parts we own and the values we measured.

- Divider: Vout = Vin x R2 / (R1 + R2). 27 kohm over 10 kohm turns 12 V into about 3.24 V.
- Shunt: V = I x R. 0.1 ohm at 1 A drops 100 mV and dissipates 100 mW. An op-amp with gain 11 gives 1.1 V.
- Low-pass filter: fc = 1 / (2 x pi x R x C). 10 kohm and 100 nF give about 159 Hz.

## Differences from the real build

- An Arduino stands in for the ESP32-S3: 5 V logic and a 10-bit ADC, against 3.3 V and a 12-bit ADC.
- The real build uses a dedicated I2C sensor chip because the ESP32-S3's built-in ADC is noisy and not linear.
- A real ESP32 pin is 3.3 V, so the real MOSFET must switch fully at a 3.3 V gate. Check the part in the Tinkercad library and say so if it is a generic one.
- Tinkercad cannot do Wi-Fi, MQTT or the model.

## Clips

| Session | Clip | Length |
| ------- | ---- | ------ |
| 1 | Measure voltage and current | about 90 s |
| 1 | Switch the load with two limits | about 90 s |
| 2 | Noise and a moving average | about 75 s |
| 2 | Flyback diode and the voltage spike | about 75 s |

TODO store clips and screenshots here

# firmware

ESP32-S3 firmware for the energy monitor. It reads voltage and current from the sensor over I2C, filters the readings, decides whether the load is within its limits, publishes measurements over MQTT and obeys commands to switch the MOSFET.

Build system: TODO PlatformIO or Arduino IDE
Framework and version: TODO

## Loop

```
sample -> filter -> decide -> publish -> obey commands
```

The loop is TODO timed loop or FreeRTOS tasks (state which one is used).

## Safe defaults

- Load is off at boot.
- Load goes off if the sensor stops answering.
- Load goes off if no command or heartbeat arrives within a timeout (TODO value).
- The protective cut runs on the board. It does not depend on Wi-Fi or the broker.

## Decision logic

- Power is computed as P = V x I from the filtered readings.
- Two limits (hysteresis): cut at the upper limit, restore at a lower one, so the load does not chatter around a single threshold.
- Rolling z-score detector on the last N readings, see [../models/](../models/README.md).

## Configuration

Copy [secrets.example.h](secrets.example.h) to secrets.h and fill it in. secrets.h is listed in .gitignore and must not be committed.

## Pins

| Function | Pin |
| -------- | --- |
| I2C data | TODO |
| I2C clock | TODO |
| MOSFET gate | TODO |

Check the board's pin table for strapping pins before choosing a GPIO.

## MQTT

Topic names and message format are in [../docs/mqtt-topics.md](../docs/mqtt-topics.md).

## Build and flash

TODO commands

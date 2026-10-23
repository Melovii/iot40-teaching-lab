# dashboard

Node-RED dashboard that subscribes to the MQTT topics from the board. A dashboard is just another subscriber: the device, the dashboard and the model never talk to each other directly, only through the broker.

## What it shows

- Chart of voltage, current and power over time
- Gauge for present power
- Alert when the detector fires or the power limit is exceeded
- Node status (online or offline, from the retained status and last-will messages)

## Flow

```
mqtt in -> json -> chart / gauge
                -> rule (limit or detector flag) -> alert
                -> command (publish) -> board
```

## Setup

1. Install Node-RED and the dashboard nodes (TODO version).
2. Start the MQTT broker (TODO which one, how).
3. Import [flow.json](flow.json) (TODO export the flow).
4. Set the broker address in the broker config node. Do not commit real addresses or credentials.

## Topics

See [../docs/mqtt-topics.md](../docs/mqtt-topics.md).

## Notes

- Retained messages let a newly opened dashboard see the last value at once.
- Redact Wi-Fi names, passwords and IP addresses before taking screenshots.

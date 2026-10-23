# Safety and limits

## Bench safety

- Low-voltage DC only, 12 V or less. No mains anywhere on the bench.
- Nothing exposed above 12 V.
- Faults are caused by adding a resistor load in parallel, loading a small fan lightly or unplugging the load. No shorts.
- The load is off at boot and off again if the sensor or the network goes silent.
- Hard limits live in hardware or firmware, not only in the cloud. A cyber attack or a network failure must not be able to switch a load into danger.

## Security habits

- Unique credential per device, no default passwords.
- Encrypted links (TLS) and signed updates where the platform allows.
- Wi-Fi names, passwords and IP addresses stay out of the repository, screenshots and clips.

## What the project does not prove

- Faults were injected by us on a bench, not collected from real equipment.
- Low-voltage DC readings say little about mains behaviour.
- Small data: results may not carry over to other loads.
- The board is designed and checked, not fabricated.
- Clean ERC and DRC runs show the board matches the rules set, not that it works.

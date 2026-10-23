# models

Anomaly detection on the load's voltage, current and power. Two detectors are compared on the same recorded runs.

## Workflow

collect -> label -> train -> validate -> deploy -> monitor

1. Collect: recorded runs of the load under normal operation, and runs with injected faults.
2. Label: write down which stretches were normal and which had a fault, and when. Labels come from the run notes, not from the model.
3. Train: fit on normal data only.
4. Validate: test on held-out runs. Never test on the data used to fit.
5. Deploy: rule on the board, model on the laptop.
6. Monitor: normal drifts with temperature, ageing and supply, so check over time.

## Windows and features

Readings are grouped into windows. Each window is summarised as mean, peak, spread and change of voltage, current and power. Window length is the same trade as the filter: short reacts fast but is jumpy, long is stable but slow.

## Detector 1: rolling z-score

Keep the last N readings, compute mean and spread, score the new reading as z = (x - mean) / spread, and raise an alert when |z| exceeds a limit. Hysteresis clears the alert. Light enough to run on the ESP32-S3. The limit trades missed faults against false alarms and is tuned from the recorded data.

## Detector 2: isolation forest

Learns what normal looks like from window features. Odd points are separated from the rest with few random cuts. It learns only from normal data and cannot say why something is abnormal. Runs on the laptop on the same recorded data as detector 1.

## Evaluation

- Same recorded runs and same fault list for both detectors.
- Fault types: TODO (for example resistor added in parallel, load removed).
- Split between fitting and testing: TODO describe.
- Metrics: TODO (missed faults, false alarms, delay from cause to alert).
- Results table: TODO, only from measured runs.

If the learned model is not better than the z-score rule, that is reported as it is.

## Files

- data/ - TODO recorded runs
- notebooks or scripts - TODO

## Limits

- Faults are injected on a bench, not collected from real equipment.
- Low-voltage DC readings say little about mains behaviour.
- Small data: results may not carry over to other loads.

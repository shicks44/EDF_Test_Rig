# Electric Ducted Fan Test Rig & Fault Detection

An independent engineering project combining mechanical design, Arduino instrumentation, MATLAB data analysis, and machine learning to study electric ducted fan (EDF) performance and detect abnormal sensor behavior.

**Status:** In development. Hardware integration, data processing, and synthetic fault generation are ongoing. Machine learning training and validation are planned.

## Overview

This project develops an instrumented EDF test rig to investigate relationships between thrust, rotational speed, and electrical power consumption.

The intended workflow connects experimental measurements with MATLAB analysis and a labeled dataset for machine learning. Synthetic faults are introduced into copies of recorded measurements to explore how abnormal sensor behavior can be detected.

## Objectives

- Measure thrust, RPM, voltage, and current.
- Analyze EDF performance across operating conditions.
- Visualize experimental data using MATLAB.
- Generate reproducible, labeled synthetic sensor faults.
- Develop and evaluate machine learning models for anomaly detection.
- Document the mechanical, electrical, and software development process.

## System Components

| Component | Purpose |
|---|---|
| EDF and mechanical test stand | Test platform and thrust measurement arrangement |
| Arduino | Sensor acquisition and control logic |
| Load cell and HX711 amplifier | Thrust measurement |
| RPM sensor | Rotational speed measurement |
| Voltage and current sensors | Electrical input measurements |
| LCD | Local measurement display |
| MATLAB | Data processing, visualization, and fault generation |
| Machine learning pipeline | Planned anomaly detection and fault classification |

Final component selection and sensor configuration will be documented as the design progresses.

## Arduino Firmware

The firmware development focuses on integrating the measurement channels and producing consistent data for analysis.

Its scope includes:

- Sensor acquisition.
- Calibration factors and unit conversion.
- Measurement timing.
- Local LCD output.
- Structured serial data output.
- Throttle control and ramping logic.

## MATLAB Analysis

The MATLAB workflow separates data analysis from synthetic fault generation.

### Main Analysis Script

The main script is intended to:

- Import recorded sensor data.
- Check missing values and measurement consistency.
- Plot thrust, RPM, voltage, and current over time.
- Calculate electrical input power.
- Compare thrust against RPM and power consumption.
- Call the fault generation function.
- Export labeled datasets for machine learning.

### Fault Generation Function

A separate function introduces controlled errors into copies of the original measurements.

Proposed fault types include:

| Fault | Description |
|---|---|
| Bias | Constant offset applied to a measurement |
| Drift | Gradually changing measurement offset |
| Spikes | Brief, isolated disturbances |
| Increased noise | Additional random signal variation |
| Dropout | Missing measurements over an interval |
| Stuck sensor | Measurement remains fixed |
| Scaling error | Incorrect multiplicative calibration factor |

The original data is preserved, and modified samples are labeled for traceability. These simulated errors represent measurement anomalies; they do not establish the behavior of real equipment failures.

## Performance Analysis

Planned plots and comparisons include:

- Thrust versus time.
- RPM versus time.
- Voltage and current versus time.
- Thrust versus RPM.
- Thrust versus electrical input power.
- Original versus fault-injected signals.

Electrical input power is calculated using:

**P = V × I**

where:

- **P** is electrical power in watts.
- **V** is voltage in volts.
- **I** is current in amperes.

Thrust per electrical watt can also be used to compare operating points. This ratio is expressed in N/W and is not a dimensionless propulsive efficiency.

## Machine Learning

The planned first stage is binary classification of normal and anomalous measurements. Further development may include classification of individual sensor fault types.

### Dataset Preparation

The dataset design will retain:

- Measurement timestamps and units.
- Source recording identifiers.
- Original and modified data provenance.
- Fault labels and affected sensor channels.
- Fault generation parameters.

Labels and fault generation metadata will be excluded from model input features.

### Evaluation Approach

- Split data by source recording before generating synthetic variants or analysis windows.
- Keep each recording and its derived samples in the same partition.
- Fit normalization and preprocessing using training data only.
- Evaluate precision, recall, F1 score, and confusion matrices.
- Measure false alarms on held-out normal recordings.

Results from synthetic faults will be distinguished from any future evaluation on real anomalies.

## Engineering Skills

This project brings together:

- Mechanical design and instrumentation.
- Embedded programming in Arduino C++.
- Sensor integration and calibration.
- Electrical measurement.
- MATLAB scripting and function development.
- Data visualization and signal analysis.
- Synthetic dataset generation.
- Machine learning workflow design.
- Technical documentation.

## Roadmap

- [ ] Finalize hardware integration and documentation.
- [ ] Complete sensor calibration and repeatability checks.
- [ ] Collect baseline measurements.
- [ ] Complete the MATLAB analysis workflow.
- [ ] Implement and verify synthetic fault generation.
- [ ] Prepare training, validation, and test datasets.
- [ ] Train and compare baseline machine learning models.
- [ ] Publish experimental plots and evaluation results.

## Author

**Shawn Hicks**  
Mechanical Engineering and Artificial Intelligence  
Western University

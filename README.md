# Two-Stage OTA Design in TSMC 180nm Technology

A complete design and analysis of a two-stage CMOS Operational Transconductance Amplifier (OTA) implemented in **TSMC 180nm technology** using **LTspice**.  
This project was developed as part of the course assignment for **EE206 – Analog Circuits** 

---

## Overview

This repository contains the design, simulation, and analysis of two different two-stage OTA architectures:

- **Design 1 — Power Optimized Architecture**
- **Design 2 — High-Speed Architecture**

Both designs satisfy the assignment specifications while exploring the trade-offs between:

- Power consumption
- Gain bandwidth product (GBW)
- Stability
- Phase margin
- Closed-loop accuracy
- Slew capability

---

## Design Specifications

| Parameter | Specification |
|---|---|
| Technology | TSMC 180nm CMOS |
| Supply Voltage | 1.8 V |
| Minimum DC Gain | ≥ 40 dB |
| Closed Loop Configuration | Non-Inverting Amplifier |
| Closed Loop Gain | 2 |
| Capacitive Load | 10 pF |
| Tail Current | 100 µA |
| Reference Current | 10 µA |
| Input Step | 0.2 V |

---

# Design 1 — Power Optimized OTA

## Key Features

- Low-power architecture
- Second-stage current matched to first-stage tail current
- Miller compensation with nulling resistor
- Stable closed-loop response

## Compensation Network

| Component | Value |
|---|---|
| Miller Capacitor | 5 pF |
| Nulling Resistor | 2.5 kΩ |
| Load Capacitor | 10 pF |

---

## Performance Summary

| Parameter | Value |
|---|---|
| DC Gain | 68.28 dB |
| GBW | 12.803 MHz |
| Phase Margin | 67.5° |
| Output Step | 0.3990 V |
| Gain Error | 0.251% |
| Power Dissipation | 289.09 µW |

---

## Observations

- Excellent stability
- Minimal ringing
- Highly power efficient
- Requires compensation resistor for stability due to RHP zero

---

# Design 2 — High-Speed OTA

## Key Features

- High-drive second stage
- 5× larger second-stage current
- Improved bandwidth and transient response
- No nulling resistor required

## Compensation Network

| Component | Value |
|---|---|
| Miller Capacitor | 5 pF |
| Nulling Resistor | Removed |
| Load Capacitor | 10 pF |

---

## Performance Summary

| Parameter | Value |
|---|---|
| DC Gain | 68.37 dB |
| GBW | 15.447 MHz |
| Phase Margin | 63.81° |
| Output Step | 0.3997 V |
| Gain Error | 0.083% |
| Power Dissipation | 1.018 mW |

---

## Observations

- Higher bandwidth
- Faster transient response
- Better tracking accuracy
- Significantly higher power consumption

---

# Design Trade-Offs

| Feature | Design 1 | Design 2 |
|---|---|---|
| Power Consumption | Low | High |
| Bandwidth | Moderate | Higher |
| Stability | Requires nulling resistor | Naturally stable |
| Accuracy | Good | Excellent |
| Thermal Efficiency | Better | Poorer |
| Load Driving Capability | Moderate | Strong |

---

# Theoretical Design Approach

The OTA was designed using long-channel MOS devices to reduce channel-length modulation effects and improve output resistance.

A channel length of:

```text
L = 0.5 µm
```

was selected for all transistors.

The transistor sizing was derived using the square-law saturation equation:

```math
W = L \cdot \frac{2I_D}{\mu C_{ox} V_{OV}^2}
```

Initial overdrive voltage assumption:

```text
VOV = 200 mV
```

---

# Simulation Results

The project includes:

- DC Operating Point Analysis
- AC Analysis
- Bode Plots
- Gain Bandwidth Analysis
- Phase Margin Analysis
- Closed-loop Transient Simulations
- Power Dissipation Calculations

All simulations were performed using:

- LTspice
- TSMC 180nm BSIM models

---

# Tools Used

- LTspice
- TSMC 180nm CMOS Models


---

# Conclusion

Both OTA implementations successfully satisfy the required specifications while demonstrating practical analog design trade-offs.

- **Design 1** prioritizes power efficiency and thermal performance.
- **Design 2** prioritizes bandwidth, slew capability, and precision.



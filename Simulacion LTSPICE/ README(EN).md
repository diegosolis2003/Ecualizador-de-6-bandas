# LTspice Simulation - 6-Band Analog Equalizer

This directory contains the SPICE validation environment for the analog equalizer. The main file is `Ecualizador.asc`, which integrates all the filtering and summing stages of the audio system.

## 🔬 Schematic Structure

The simulation file is designed to perform an end-to-end frequency response analysis, evaluating both the individual bands and the behavior of the active summer.

* **Active Models:** `ADTL084` operational amplifier models powered by ±12 V symmetrical supplies are used to replicate the behavior of the Sallen-Key stages and the summer.
* **Sallen-Key Filters (4th Order):** Implementation of the six parallel branches (cascaded HP2 and LP2) tuned to the calculated center frequencies (57 Hz to 4.9 kHz) with two-octave bandwidths.
* **Active Summer:** Configurable input resistor network to simulate potentiometers in different positions, testing the gain limits.

## ⚙️ Execution Instructions

To view the frequency response curves (Bode Plots):

1. Open the `Ecualizador.asc` file in LTspice.
2. Click on **Run** (the running person icon on the top toolbar).
3. The simulator will automatically execute the pre-configured logarithmic sweep AC analysis directive: `.ac dec 1000 20 20k` (1000 points per decade, from 20 Hz to 20 kHz).

## 📈 Key Measurement Nodes (Probes)

You can click on the following schematic labels to observe the signals of interest in the LTspice waveform viewer:

* `VoutB1` to `VoutB6`: Individual response of the corresponding band-pass filter (before the summer).
* `VoutSum-12dB`: Total system output with maximum attenuation (Rp = 50 kΩ).
* `VoutSum0dB`: Total system output with unity gain (Rp = 10 kΩ).
* `VoutSum+12dB`: Total system output with maximum amplification (Rp = 0 Ω).

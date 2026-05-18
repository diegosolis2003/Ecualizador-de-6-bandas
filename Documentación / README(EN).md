# Technical Documentation - 6-Band Analog Equalizer

This directory contains the calculation reports and theoretical justification for the design of a six-band analog equalizer, optimized for the frequency spectrum of an electric piano.

## 📄 Report Contents

The main file in this folder is `Ecualizador .pdf`, which details step-by-step the engineering behind the hardware:

* **System Architecture:** Breakdown of the circuit's four stages (Input buffer, Sallen-Key filtering stage, Gain control, and Power stage).
* **Frequency Definition:** Acoustic justification and mathematical calculation of the center frequencies using the geometric mean.
* **Bandwidth Optimization:** Comparative analysis demonstrating why the bandwidth was expanded to two octaves to avoid severe gain drops at the center frequencies (reducing attenuation to -0.45 dB).
* **Active Filter Calculation:** Detailed tables with the exact resistor and capacitor values for the second-order high-pass and low-pass filters (Butterworth response, Q ≈ 0.707).
* **Inverting Summer Design:** Equations and selection of commercial components to ensure a safe and symmetrical adjustment of ±12 dB, avoiding operational amplifier saturation.

## 📊 Key Calculated Parameters

* **Center Frequencies (f0):** 57 Hz, 127 Hz, 316 Hz, 886 Hz, 2121 Hz, 4900 Hz.
* **Summer - Feedback Resistor (Rf):** 13.3 kΩ.
* **Summer - Minimum Series Resistor (Rs):** 3.3 kΩ.
* **Summer - Band Potentiometer (Rp):** 50 kΩ linear.
* **Maximum Speaker Margin (8 Ω, 35W):** 16.7 VRMS / 24.4 dB maximum gain.
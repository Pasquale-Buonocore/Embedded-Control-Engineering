# Lesson M05 — Tuning the Current Loops

## Goal

Choose and tune the d- and q-axis PI controllers for a target bandwidth, then verify current tracking and stability across operating points. Explain when the simple RL tuning fails and adjust the design for coupling, delay, and voltage limits.

## Topics

The approximate plant `1 / (L s + Rs)`. Under ideal decoupling and negligible delay, derive the PI starting point `Kp = L wc` and `Ki = Rs wc` for chosen bandwidth `wc`. Add d-q cross-coupling, back-EMF feedforward, sampling and PWM delay, voltage-vector saturation, and anti-windup.

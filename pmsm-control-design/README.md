# PMSM Control Design

A control-focused specialization for designing and tuning current, speed, and position loops around an existing PMSM FOC implementation. Prerequisites: [Automatic Control 01–08](../automatic-control/README.md). Embedded drivers, Clarke/Park implementation, and PWM generation are outside this track; their timing and voltage limits remain part of the control model.

## Learning sequence

| Lesson | Question to answer | Core work |
|---|---|---|
| M01 — What should feedback achieve? | Why add P, I, or D action? | Define tracking, disturbance rejection, steady-state error, rise/settling time, overshoot, robustness, noise sensitivity, and control effort. Compare the closed-loop response with and without each term. |
| M02 — Poles, zeros, and controller design | What does it mean to place a zero near a plant pole, and why would we do it? | Derive closed-loop poles from the characteristic equation; use root locus and Bode plots to see how gain and controller zeros change the response. Work through an RL plant with PI control. Distinguish nominal pole-zero cancellation from robust design; include parameter error and delay. |
| M03 — Tuning a PI/PID in general | How do we choose gains from requirements and measurements? | Compare model-based pole placement, frequency-domain loop shaping (crossover and phase margin), and practical step-response tuning. Include derivative filtering, setpoint weighting, anti-windup, and a repeatable measurement/tuning checklist. |
| M04 — PMSM plant for control | Which dynamics does each loop actually control? | Derive the d-q voltage equations, torque equation, and mechanical dynamics. Identify Rs, Ld, Lq, flux linkage, inertia J, friction B, and load torque; distinguish SPMSM and IPMSM where it affects control. |
| M05 — Tune the d- and q-axis current loops | How do we turn current requests into controlled torque? | Start with the decoupled RL approximation and derive PI gains from a target bandwidth. Add d-q cross-coupling and back-EMF feedforward, current sampling and PWM delay, voltage-vector saturation, anti-windup, and checks at different speeds and currents. |
| M06 — Tune the speed loop | How do we reject load torque and track speed? | Treat the closed current loop as the inner plant; derive the mechanical plant and tune the speed PI for bandwidth and damping. Include current/torque limits, load disturbances, friction, inertia uncertainty, and speed-estimate filtering. |
| M07 — Tune the position loop | How do we follow a motion command without excessive overshoot? | Cascade position over speed and current; choose bandwidth separation, position P/PD or 2-DOF structures, trajectory generation, velocity/acceleration feedforward, following error, and mechanical resonances or backlash. |
| M08 — Validate the complete drive | How do we know the tuning works beyond one operating point? | Simulate and measure reference steps, load steps, frequency response, saturation recovery, parameter changes, low/high-speed operation, and quantization/noise. Record acceptance criteria and iterate from the innermost loop outward. |

## Running exercise

Use one PMSM and load model throughout the track. First design a PI for the approximate current plant `1 / (L s + Rs)`; under ideal decoupling and negligible delay, a chosen current bandwidth `wc` gives the starting point `Kp = L wc`, `Ki = Rs wc`. Then add the actual d-q coupling, back-EMF, discrete timing, and voltage limits to see where the simple design stops predicting behavior. Reuse the verified current loop as the plant for speed design, then close the position loop around both. Every lesson should state the model assumptions, units, performance target, and measured evidence.

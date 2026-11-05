# Automatic Control

Foundations of classical control, from transfer functions to discrete controllers.

Future examples in this area will use generic first- and second-order systems. The lessons should answer what a controller is meant to achieve before introducing tuning formulas: steady-state accuracy, transient response, disturbance rejection, stability margins, and sensitivity to noise and model error.

In particular, lessons 04–06 should develop the meaning of poles, zeros, root locus, and loop shaping. A controller zero may approximately cancel a known plant pole in a nominal model, but exact cancellation is fragile when parameters vary or delays are present. PI/PID tuning should be compared through pole placement, frequency-domain design, and measured step-response methods, with explicit units and performance targets. Lessons 07–08 then add saturation, anti-windup, sampling, and computational/PWM delay. The [PMSM Control Design](../pmsm-control-design/README.md) track applies these ideas to motor loops.

## Lessons

- [Lesson 01 — Laplace Transform and Transfer Functions](01-laplace-transform-and-transfer-functions.md)
- [Lesson 02 — Time-Domain Analysis](02-time-domain-analysis.md)
- [Lesson 03 — Stability](03-stability.md)
- [Lesson 04 — Frequency-Domain Analysis](04-frequency-domain-analysis.md)
- [Lesson 05 — Feedback Control](05-feedback-control.md)
- [Lesson 06 — P, PI and PID Controllers](06-p-pi-and-pid-controllers.md)
- [Lesson 07 — Saturation and Anti-Windup](07-saturation-and-anti-windup.md)
- [Lesson 08 — Continuous-to-Discrete Control](08-continuous-to-discrete-control.md)

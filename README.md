# Embedded Control Engineering Learning Roadmap

## 🎯 Repository Objective

This repository documents a structured learning path to rebuild and extend practical **Control Engineering** skills through four progressive projects:

1. **DC Motor Control**
2. **Sensor & State Estimation Lab**
3. **Inverted Pendulum**
4. **Self-Balancing Robot**

The goal is not only to review classical automatic control theory, but to connect it with real embedded implementation topics such as:

- dynamic system modelling;
- transfer functions;
- state-space representation;
- stability analysis;
- frequency-domain analysis;
- PID control;
- digital control;
- sampling and aliasing;
- digital filtering;
- state estimation;
- Kalman filtering;
- sensor fusion;
- controllability and observability;
- pole placement;
- LQR;
- real-time implementation;
- embedded software constraints;
- MIL / SIL / PIL / HIL validation;
- fault injection and robustness analysis.

The final objective is to develop a complete **Embedded Control Engineer** workflow:

```text
Physical System
      ↓
Mathematical Model
      ↓
System Analysis
      ↓
Sensor Acquisition
      ↓
Signal Processing
      ↓
State Estimation
      ↓
Control Design
      ↓
Simulation
      ↓
Embedded Implementation
      ↓
MIL / SIL / PIL / HIL
      ↓
Validation
```

---

# 🗺️ Learning Path Overview

The roadmap is divided into four main projects.

Each project introduces new concepts while reusing the knowledge developed in the previous ones.

| Project | Main Focus |
|---|---|
| Project 1 — DC Motor Control | Classical control and embedded implementation |
| Project 2 — Sensor & State Estimation Lab | Signal processing, filtering and sensor fusion |
| Project 3 — Inverted Pendulum | State-space and modern control |
| Project 4 — Self-Balancing Robot | Complete embedded control architecture |

---

# Project 1 — DC Motor Control

## Objective

Develop a complete speed and/or position control system for a DC motor, starting from the physical equations and ending with a digital controller running on embedded hardware.

The project will be used to rebuild the foundations of classical control theory.

---

## Lesson 1 — Dynamic System Modelling

### Topics

- physical modelling;
- input, output and state variables;
- first-order and second-order differential equations;
- mechanical systems;
- electrical systems;
- coupled electromechanical systems.

### DC motor equations

Electrical model:

```math
V = Ri + L\frac{di}{dt} + K_e\omega
```

Mechanical model:

```math
J\frac{d\omega}{dt} = K_t i - b\omega - \tau_L
```

### Deliverable

Derive the complete mathematical model of the DC motor.

---

## Lesson 2 — Laplace Transform and Transfer Functions

### Topics

- Laplace transform review;
- transfer function definition;
- poles;
- zeros;
- system order;
- characteristic equation;
- static gain.

### Deliverable

Derive:

```math
G(s)=\frac{\Omega(s)}{V(s)}
```

for the DC motor.

---

## Lesson 3 — Time-Domain Analysis

### Topics

- impulse response;
- step response;
- rise time;
- settling time;
- overshoot;
- steady-state error;
- dominant poles.

### Deliverable

Analyse the open-loop motor response in MATLAB / Simulink.

---

## Lesson 4 — Stability

### Topics

- concept of stability;
- asymptotic stability;
- pole location;
- Routh-Hurwitz criterion;
- relationship between poles and transient response.

### Deliverable

Determine the stability of the motor model and study how physical parameters modify the poles.

---

## Lesson 5 — Frequency-Domain Analysis

### Topics

- sinusoidal response;
- frequency response;
- Bode plots;
- magnitude;
- phase;
- bandwidth;
- gain margin;
- phase margin.

### Deliverable

Generate and interpret the Bode diagram of the motor.

---

## Lesson 6 — Feedback Control

### Topics

- open-loop vs closed-loop systems;
- negative feedback;
- reference tracking;
- disturbance rejection;
- sensitivity;
- feedback trade-offs.

### Deliverable

Create the first closed-loop motor control architecture.

---

## Lesson 7 — P, PI and PID Controllers

### Topics

- proportional control;
- integral control;
- derivative control;
- PID architecture;
- tuning;
- effect of each term;
- derivative filtering.

### Experiments

Evaluate how changing:

```text
Kp
Ki
Kd
```

affects:

- rise time;
- overshoot;
- settling time;
- steady-state error.

### Deliverable

Design a speed controller for the DC motor.

---

## Lesson 8 — Saturation and Anti-Windup

### Topics

- actuator limits;
- PWM saturation;
- integrator windup;
- anti-windup techniques;
- clamping;
- back-calculation.

### Deliverable

Extend the controller with actuator saturation and anti-windup logic.

---

## Lesson 9 — Continuous-to-Discrete Control

### Topics

- continuous control;
- discrete control;
- sampling;
- zero-order hold;
- Z-transform introduction;
- Euler discretization;
- Tustin transform;
- discrete PID.

### Deliverable

Convert the continuous controller into a discrete implementation.

---

## Lesson 10 — Embedded Control Loop

### Topics

- control-loop frequency;
- timer interrupt;
- deterministic execution;
- jitter;
- latency;
- WCET;
- floating point vs fixed point.

### Architecture

```text
Timer ISR
   ↓
Read Encoder
   ↓
Estimate Speed
   ↓
Controller
   ↓
PWM Update
```

### Deliverable

Define the embedded software architecture for the motor controller.

---

## Lesson 11 — Motor Hardware Interface

### Topics

- PWM;
- H-bridge;
- quadrature encoder;
- timer peripherals;
- current sensing;
- ADC;
- motor driver basics.

### Deliverable

Interface the controller with a real DC motor.

---

## Lesson 12 — Project 1 Validation

### Tests

- step reference;
- load disturbance;
- actuator saturation;
- sensor noise;
- different sample times;
- controller parameter variations.

### Final Deliverable

A working embedded DC motor speed controller.

---

# Project 2 — Sensor & State Estimation Lab

## Objective

Learn how real sensor data must be acquired, analysed, filtered and fused before being used by a control algorithm.

Typical hardware:

- accelerometer;
- gyroscope;
- magnetometer;
- encoder;
- optional GPS.

---

## Lesson 13 — Sensor Measurement Fundamentals

### Topics

- measurement noise;
- accuracy;
- precision;
- resolution;
- bias;
- offset;
- scale factor;
- drift;
- calibration.

### Deliverable

Acquire and inspect raw IMU data.

---

## Lesson 14 — Sampling Theory

### Topics

- sampling frequency;
- Nyquist-Shannon theorem;
- aliasing;
- oversampling;
- anti-alias filtering;
- sample-time selection.

### Experiment

Generate deliberate aliasing and analyse its effect.

### Deliverable

Define the acquisition frequency for the IMU.

---

## Lesson 15 — Frequency Analysis of Sensor Data

### Topics

- time-domain analysis;
- FFT;
- frequency spectrum;
- noise frequency content;
- spectral peaks;
- vibration identification.

### Deliverable

Analyse real sensor data in MATLAB or Python.

---

## Lesson 16 — Digital Filters

### Topics

- moving average;
- low-pass filter;
- high-pass filter;
- band-pass filter;
- notch filter;
- FIR;
- IIR;
- filter order;
- phase delay.

### Deliverable

Implement and compare different filters on IMU data.

---

## Lesson 17 — Filtering Inside a Control Loop

### Topics

- filter delay;
- phase loss;
- noise rejection;
- relationship between controller bandwidth and sensor filtering.

### Deliverable

Study the effect of excessive filtering on closed-loop performance.

---

## Lesson 18 — Sensor Calibration

### Topics

- accelerometer offset;
- gyroscope bias;
- scale factor;
- axis misalignment;
- temperature effects;
- calibration procedures.

### Deliverable

Implement an IMU calibration procedure.

---

## Lesson 19 — Orientation Estimation

### Topics

- roll;
- pitch;
- yaw;
- Euler angles;
- gyroscope integration;
- accelerometer-based inclination;
- drift.

### Deliverable

Estimate orientation independently from accelerometer and gyroscope.

---

## Lesson 20 — Complementary Filter

### Topics

- low-frequency information;
- high-frequency information;
- complementary filtering;
- gyro drift compensation.

### Architecture

```text
Gyroscope ──► High-frequency information ──┐
                                           ├──► Angle Estimate
Accelerometer ► Low-frequency information ─┘
```

### Deliverable

Implement a complementary filter for attitude estimation.

---

## Lesson 21 — State-Space Stochastic Models

### Topics

- process model;
- measurement model;
- process noise;
- measurement noise;
- covariance;
- Gaussian noise.

Model:

```math
x_{k+1}=Ax_k+Bu_k+w_k
```

```math
z_k=Hx_k+v_k
```

### Deliverable

Build a stochastic model of a simple dynamic system.

---

## Lesson 22 — Kalman Filter

### Topics

- prediction;
- covariance prediction;
- innovation;
- Kalman gain;
- correction;
- Q matrix;
- R matrix.

### Deliverable

Implement a linear Kalman Filter.

---

## Lesson 23 — Kalman Filter Tuning

### Topics

- effect of Q;
- effect of R;
- model confidence;
- sensor confidence;
- convergence;
- noisy measurements.

### Deliverable

Perform experiments with different Q and R matrices.

---

## Lesson 24 — Extended Kalman Filter

### Topics

- nonlinear systems;
- nonlinear measurement models;
- Jacobian;
- EKF prediction;
- EKF correction.

### Deliverable

Use an EKF for IMU-based attitude estimation.

---

## Lesson 25 — Sensor Fusion

### Topics

- combining multiple sensors;
- redundant measurements;
- complementary sensors;
- IMU + encoder;
- IMU + magnetometer;
- optional GPS + IMU.

### Deliverable

Create a multi-sensor state estimator.

---

## Lesson 26 — Project 2 Validation

### Tests

- sensor noise;
- artificial bias;
- sensor dropout;
- incorrect calibration;
- delayed measurements;
- different sampling rates.

### Final Deliverable

A complete embedded sensor acquisition, filtering and state-estimation pipeline.

---

# Project 3 — Inverted Pendulum

## Objective

Move from classical control to state-space and modern control techniques.

The inverted pendulum will be used to study:

- linearization;
- controllability;
- observability;
- state feedback;
- pole placement;
- LQR;
- observers;
- Kalman estimation.

---

## Lesson 27 — Nonlinear System Modelling

### Topics

- nonlinear differential equations;
- coupled mechanical systems;
- pendulum dynamics;
- equilibrium points.

### Deliverable

Derive the nonlinear equations of the inverted pendulum.

---

## Lesson 28 — Linearization

### Topics

- equilibrium point;
- Taylor expansion;
- small-angle approximation;
- Jacobian;
- local linear model.

### Deliverable

Linearize the pendulum around the upright equilibrium.

---

## Lesson 29 — State-Space Representation

### Topics

State vector:

```math
x =
\begin{bmatrix}
position \\
velocity \\
angle \\
angular\ velocity
\end{bmatrix}
```

System:

```math
\dot{x}=Ax+Bu
```

```math
y=Cx+Du
```

### Deliverable

Build the state-space model in MATLAB / Simulink.

---

## Lesson 30 — Eigenvalues and State-Space Stability

### Topics

- eigenvalues;
- eigenvectors;
- modes;
- unstable modes;
- continuous-time stability;
- discrete-time stability.

### Deliverable

Analyse the unstable dynamics of the pendulum.

---

## Lesson 31 — Controllability

### Topics

Controllability matrix:

```math
\mathcal{C}=
[B\ AB\ A^2B\ ...]
```

- rank;
- controllable modes;
- physical meaning.

### Deliverable

Verify that the pendulum is controllable.

---

## Lesson 32 — Observability

### Topics

Observability matrix:

```math
\mathcal{O}=
\begin{bmatrix}
C \\
CA \\
CA^2 \\
...
\end{bmatrix}
```

- measurable states;
- estimated states;
- sensor placement.

### Deliverable

Analyse observability with different sensor configurations.

---

## Lesson 33 — State Feedback

### Topics

```math
u=-Kx
```

- state feedback;
- closed-loop poles;
- eigenvalue placement.

### Deliverable

Stabilize the pendulum using full-state feedback.

---

## Lesson 34 — Pole Placement

### Topics

- desired poles;
- damping;
- settling time;
- control effort;
- closed-loop dynamics.

### Deliverable

Design a pole-placement controller.

---

## Lesson 35 — Linear Quadratic Regulator

### Topics

Cost function:

```math
J=
\int_0^\infty
(x^TQx+u^TRu)\,dt
```

- Q matrix;
- R matrix;
- control effort;
- state penalties;
- optimal feedback.

### Deliverable

Design and tune an LQR controller.

---

## Lesson 36 — Luenberger Observer

### Topics

- state observer;
- observer dynamics;
- estimation error;
- observer poles.

### Architecture

```text
Plant
  │
  ├──► Measurements
  │
  ▼
Observer
  │
  ▼
Estimated State
  │
  ▼
Controller
```

### Deliverable

Implement a state observer.

---

## Lesson 37 — Kalman State Estimator

### Topics

- observer vs Kalman filter;
- deterministic vs stochastic estimation;
- noisy state measurements.

### Deliverable

Replace the ideal observer with a Kalman-based estimator.

---

## Lesson 38 — Discrete State-Space Control

### Topics

- discrete state equations;
- discrete eigenvalues;
- discrete LQR;
- discrete observer;
- sample-time effects.

### Deliverable

Prepare the controller for embedded execution.

---

## Lesson 39 — Project 3 Validation

### Tests

- initial-angle variations;
- sensor noise;
- actuator saturation;
- parameter uncertainty;
- external disturbances;
- delayed measurements.

### Final Deliverable

A complete simulated state-space controller for an inverted pendulum.

---

# Project 4 — Self-Balancing Robot

## Objective

Integrate all previous topics into a complete embedded mechatronic control system.

The robot will combine:

- DC motors;
- encoders;
- IMU;
- filtering;
- sensor fusion;
- state estimation;
- state-space control;
- real-time embedded software.

---

## Lesson 40 — System Architecture

### Architecture

```text
             IMU
              │
              ▼
           Filter
              │
Encoder ──────┤
              ▼
        Sensor Fusion
              │
              ▼
        State Estimator
              │
              ▼
       LQR Controller
              │
              ▼
          PWM Output
          /       \
       Motor     Motor
```

### Deliverable

Define hardware and software architecture.

---

## Lesson 41 — Robot Dynamic Model

### Topics

- wheel dynamics;
- motor dynamics;
- body dynamics;
- inverted pendulum approximation;
- state definition.

### Deliverable

Create the robot mathematical model.

---

## Lesson 42 — Sensor Acquisition Architecture

### Topics

- IMU communication;
- encoder acquisition;
- timer synchronization;
- timestamping;
- deterministic sampling.

### Deliverable

Implement synchronized sensor acquisition.

---

## Lesson 43 — Real-Time State Estimation

### Topics

- embedded filtering;
- sensor fusion execution rate;
- estimator timing;
- latency;
- numerical stability.

### Deliverable

Run the estimator on the MCU.

---

## Lesson 44 — Real-Time Controller

### Topics

- control task;
- ISR vs task execution;
- scheduler interaction;
- sample-time guarantee;
- execution-time measurement.

### Deliverable

Execute the LQR controller in real time.

---

## Lesson 45 — Actuator Control

### Topics

- PWM;
- motor driver;
- dead zone;
- saturation;
- nonlinear friction;
- current limits.

### Deliverable

Drive both motors from the control algorithm.

---

## Lesson 46 — Cascade Control

Possible architecture:

```text
Position Controller
        ↓
Velocity Reference
        ↓
Balance Controller
        ↓
Motor Command
```

### Topics

- inner loop;
- outer loop;
- bandwidth separation;
- cascade control.

### Deliverable

Add position or velocity regulation while maintaining balance.

---

## Lesson 47 — Embedded Robustness

### Topics

- watchdog;
- sensor plausibility;
- missing samples;
- deadline monitoring;
- invalid sensor data;
- safe-state strategy.

### Deliverable

Add diagnostic and protection mechanisms.

---

## Lesson 48 — Fault Injection

Inject faults such as:

```text
IMU bias
Encoder spike
Encoder freeze
Sensor dropout
Sample delay
CPU overload
Actuator saturation
Wrong calibration
```

### Deliverable

Analyse controller behaviour under faults.

---

# Verification and Validation Track

The four projects should progressively introduce a Model-Based Design verification workflow.

---

## Lesson 49 — MIL

### Model-in-the-Loop

```text
Plant Model
     ↕
Controller Model
```

### Goals

- validate control logic;
- verify nominal behaviour;
- run parameter sweeps;
- run automated simulations.

---

## Lesson 50 — SIL

### Software-in-the-Loop

```text
Plant Model
     ↕
Generated / Production C Code
```

### Goals

Compare:

```math
Output_{MIL} \approx Output_{SIL}
```

---

## Lesson 51 — PIL

### Processor-in-the-Loop

```text
Simulation Environment
        ↕
Target MCU
```

### Goals

- execute controller on real processor;
- measure execution time;
- evaluate numerical differences;
- verify target-specific behaviour.

---

## Lesson 52 — HIL

### Hardware-in-the-Loop

Example architecture:

```text
Embedded Controller
        │
        ▼
   Physical I/O
        │
        ▼
   Real-Time Plant
      Speedgoat
```

### Goals

- real-time validation;
- closed-loop testing;
- fault injection;
- sensor emulation;
- actuator emulation;
- latency analysis.

---

# Final Capstone Validation

The final Self-Balancing Robot should be validated through:

```text
MIL
 ↓
SIL
 ↓
PIL
 ↓
HIL
 ↓
Real Hardware
```

---

# 📚 Final Competency Map

At the end of this roadmap the following competencies should have been exercised.

## System Modelling

- [ ] Differential equations
- [ ] Transfer functions
- [ ] State-space models
- [ ] Linearization
- [ ] Parameter identification

## Classical Control

- [ ] Stability
- [ ] Step response
- [ ] Bode plots
- [ ] Gain margin
- [ ] Phase margin
- [ ] PID control
- [ ] Anti-windup

## Digital Control

- [ ] Sampling
- [ ] Z-domain concepts
- [ ] Controller discretization
- [ ] Sample-time selection
- [ ] Latency and jitter analysis

## Signal Processing

- [ ] FFT
- [ ] Aliasing
- [ ] FIR filters
- [ ] IIR filters
- [ ] Low-pass filters
- [ ] Notch filters

## State Estimation

- [ ] Luenberger observer
- [ ] Kalman Filter
- [ ] Extended Kalman Filter
- [ ] Sensor fusion

## Modern Control

- [ ] Controllability
- [ ] Observability
- [ ] State feedback
- [ ] Pole placement
- [ ] LQR

## Embedded Implementation

- [ ] Timer-driven control loop
- [ ] PWM
- [ ] ADC
- [ ] Encoder
- [ ] IMU
- [ ] Execution-time analysis
- [ ] WCET awareness
- [ ] Fault handling

## Verification

- [ ] MIL
- [ ] SIL
- [ ] PIL
- [ ] HIL
- [ ] Fault injection

---

# 🏁 Final Goal

At the end of the repository, the objective is to be able to approach a new control problem and systematically answer:

1. What is the physical plant?
2. What are the inputs, outputs and states?
3. How can the system be modelled?
4. Is the system stable?
5. Is it controllable?
6. Is it observable?
7. Which sensors are required?
8. What noise and bandwidth limitations do the sensors have?
9. Which signals need filtering?
10. Which states must be estimated?
11. Which control architecture is appropriate?
12. What sample time is required?
13. How should the controller be discretized?
14. How do latency and jitter affect stability?
15. Can the algorithm run within the real-time deadline?
16. How does the system behave under saturation and disturbances?
17. How can the design be verified through MIL, SIL, PIL and HIL?
18. How does the controller behave when sensors or actuators fail?

The repository is therefore intended to become both a **Control Engineering learning laboratory** and a practical portfolio of **Embedded Control Systems** development.

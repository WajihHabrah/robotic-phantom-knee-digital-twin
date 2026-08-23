# System Architecture

The Robotic Phantom Knee uses a distributed architecture combining robotic actuation, variable-stiffness mechanics, pneumatic soft-tissue simulation, embedded sensing, ROS 2 communication, and a Unity-based digital twin.

The system is organized into two main layers:

* **Digital and control layer** — Raspberry Pi, ROS 2, and Unity
* **Physical phantom-knee platform** — robotic actuation, variable-stiffness mechanism, pneumatic soft-tissue system, and embedded sensing

---

## High-Level Architecture

```text
                    ┌─────────────────────────────┐
                    │      Unity Digital Twin     │
                    │ Visualization · GUI · UX    │
                    └──────────────┬──────────────┘
                                   │
                            ROS Communication
                                   │
                    ┌──────────────▼──────────────┐
                    │       Raspberry Pi 5        │
                    │ Ubuntu 24.04 · ROS 2 Jazzy  │
                    └──────────┬─────────┬────────┘
                               │         │
                        Control│         │Sensor Data
                               │         ▲
                               │   ┌─────┴──────────────┐
                               │   │  Embedded Sensors  │
                               │   │ IMU · Mag · Temp   │
                               │   └─────┬──────────────┘
                               │         │
                               ▼         │
                    ┌─────────────────────────────┐
                    │    Robotic Phantom Knee     │
                    │      Physical Platform      │
                    └────────┬───────────┬────────┘
                             │           │
              ┌──────────────┘           └──────────────┐
              ▼                                         ▼
┌─────────────────────────────┐          ┌─────────────────────────────┐
│ Antagonistic Robotic        │          │ Pneumatic Soft-Tissue      │
│ Actuation                   │          │ System                     │
│                             │          │                             │
│ BEAR Motor 1                │          │ Inflation                  │
│ BEAR Motor 2                │          │ Pressure Release           │
│ Tracking · Clamping         │          │ Variable Compliance        │
│ Backdrivability             │          │ Soft-Tissue Deformation    │
└──────────────┬──────────────┘          └─────────────────────────────┘
               │
               ▼
┌─────────────────────────────┐
│ Variable-Stiffness          │
│ Mechanism (VSA)             │
│                             │
│ Elastic Mechanical          │
│ Compliance                  │
└─────────────────────────────┘
```

The pneumatic subsystem is shown separately from the robotic actuation and variable-stiffness mechanism because it represents a distinct physical function of the phantom knee rather than a downstream stage of the actuation chain.

---

## System Organization

### Digital and Control Layer

The digital and control layer coordinates communication, control, visualization, and system monitoring.

It consists of:

* Raspberry Pi 5
* Ubuntu 24.04 LTS
* ROS 2 Jazzy
* Unity-based digital twin

The Raspberry Pi operates as the central communication and control platform.

---

### Physical Phantom-Knee Platform

The physical platform integrates four main engineering subsystems:

1. Antagonistic robotic actuation
2. Variable-stiffness mechanism
3. Pneumatic soft-tissue simulation
4. Embedded sensing

These subsystems work together to reproduce selected mechanical and soft-tissue behaviours of the knee in a controlled bench-top environment.

---

## Antagonistic Robotic Actuation

Two backdrivable BEAR actuators are arranged antagonistically around the knee mechanism.

The actuator subsystem supports:

* Position control
* Velocity feedback
* Current-related feedback
* Antagonistic tracking
* Adjustable clamping behaviour
* External-load-driven backdrivability

The antagonistic arrangement enables controlled interaction between the two actuators around the knee joint.

---

## Variable-Stiffness Mechanism

The robotic actuation subsystem interacts with an elastic variable-stiffness mechanism.

The mechanism introduces mechanical compliance into the knee platform and provides a physical basis for investigating variable joint stiffness.

Its functions include:

* Elastic resistance
* Mechanical compliance
* Variable-stiffness behaviour
* Interaction with antagonistic actuation

The VSA mechanism is therefore associated directly with the robotic actuation subsystem rather than with the pneumatic subsystem.

---

## Pneumatic Soft-Tissue System

The pneumatic subsystem represents selected soft-tissue behaviour around the phantom knee.

It operates as a separate physical subsystem integrated into the knee platform.

The pneumatic system provides:

* Controlled inflation
* Controlled pressure release
* Variable surface compliance
* Physical deformation around the knee
* Simplified soft-tissue simulation

This subsystem supports investigation of the physical interface between the phantom knee and external devices such as early-stage exoskeleton concepts.

---

## Embedded Sensing

Distributed embedded sensor nodes monitor motion and local system conditions.

The sensing hardware includes:

* ISM330DHCX inertial measurement unit
* MMC5983MA magnetometer
* TMP117 temperature sensor
* FeatherS3 microcontroller platforms

Sensor data is transmitted to the Raspberry Pi and integrated into the ROS 2 communication architecture.

---

## ROS 2 Layer

ROS 2 Jazzy provides the middleware connecting the physical system, embedded sensors, robotic actuators, and Unity digital twin.

The ROS 2 layer supports:

* Actuator commands
* Actuator feedback
* Sensor acquisition
* Position and velocity communication
* Data routing
* Unity communication
* System monitoring

---

## Unity Digital Twin

The Unity-based digital twin represents the physical robotic knee in real time.

The digital environment supports:

* Real-time joint visualization
* Physical-to-digital synchronization
* Interactive control
* Sensor-data visualization
* System monitoring
* GUI interaction
* Interactive component exploration

Unity communicates with the physical system through the ROS 2 communication layer.

---

## Information and Control Flow

The system uses bidirectional communication between the physical platform and the digital twin.

```text
Embedded Sensors
       │
       ▼
     ROS 2
       │
       ▼
Unity Digital Twin


Unity / Control Commands
       │
       ▼
     ROS 2
       │
       ▼
Robotic Actuators
       │
       ▼
Variable-Stiffness Mechanism
       │
       ▼
Robotic Phantom Knee
```

The pneumatic soft-tissue subsystem is integrated physically into the phantom knee and provides compliance independently of the main robotic actuation chain.

---

## Functional View

A simplified functional interpretation of the platform is:

```text
Digital Twin
     ↕
ROS 2 / Raspberry Pi
     ↕
Robotic Phantom Knee
     │
     ├── Antagonistic Actuation
     │        └── Variable-Stiffness Mechanism
     │
     ├── Pneumatic Soft-Tissue Simulation
     │
     └── Embedded Sensing
```

This representation emphasizes that the actuation, VSA, pneumatics, and sensing systems are integrated subsystems of the same physical robotic phantom knee.

---

## Summary

The architecture combines:

* Robotic antagonistic actuation for controlled knee motion
* An elastic variable-stiffness mechanism for mechanical compliance
* A pneumatic subsystem for soft-tissue simulation
* Embedded sensors for physical-state monitoring
* ROS 2 for communication and control
* Unity for digital-twin visualization and interaction

Together, these components form an integrated physical and digital test platform for controlled evaluation of early-stage exoskeleton and rehabilitation-robotics concepts.

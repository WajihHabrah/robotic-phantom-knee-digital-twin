# Robotic Phantom Knee Digital Twin

A robotic phantom knee developed as a physical and digital test platform for evaluating early-stage exoskeleton concepts.

The system combines antagonistic robotic actuation, embedded sensing, pneumatic soft-tissue simulation, ROS 2 communication, and a Unity-based digital twin.

This project was developed as part of my Master's thesis in Biomedical Engineering at Chalmers University of Technology.

---

## Project Overview

The Robotic Phantom Knee is a one-degree-of-freedom experimental platform designed to reproduce selected mechanical and soft-tissue behaviours of the human knee in a controlled bench-top environment.

The platform integrates:

* Two antagonistically arranged robotic actuators
* Variable-stiffness mechanical behaviour
* Pneumatic soft-tissue simulation
* Embedded inertial and temperature sensing
* Raspberry Pi-based control
* ROS 2 communication
* Unity-based real-time digital twin
* Interactive control and visualization

The platform was developed to support controlled testing and early-stage evaluation of robotic and exoskeleton concepts before human testing.

---

## Demonstration

### Project Video

[Watch the full project demonstration on YouTube](https://www.youtube.com/watch?v=lWRFAtuQzvM)

The demonstration covers:

* Operating principle
* 3D modelling and printing
* Mechanical assembly
* Hardware subsystems and integration
* GUI and user interaction
* Antagonistic tracking and clamping
* Partial-system testing

### Portfolio Page

[View the project in my engineering portfolio](https://wajihhabrah.github.io/projects/robotic-phantom-knee-digital-twin.html)

---

## System Architecture

A simplified representation of the system is:

```text
Embedded Sensors
      │
      ▼
Raspberry Pi 5
Ubuntu 24.04 LTS
ROS 2 Jazzy
      │
      ├──────────────► Robotic Actuators
      │
      │
      └──────────────► Unity Digital Twin
                         │
                         ▼
                  Visualization
                  Control / GUI
```

The Raspberry Pi operates as the central communication and control platform, coordinating actuator commands, sensor acquisition, ROS 2 communication, and data exchange with the Unity digital twin.

---

## Robotic Actuation

The mechanical platform uses two backdrivable robotic actuators arranged antagonistically around the knee mechanism.

The actuators support:

* Position control
* Velocity feedback
* Torque/current-related feedback
* Antagonistic tracking
* Adjustable clamping behaviour
* External-load-driven backdrivability

The antagonistic configuration enables the platform to investigate controlled resistance, joint behaviour, and variable-stiffness concepts.

---

## Variable-Stiffness Actuation

An elastic variable-stiffness mechanism is incorporated into the robotic knee system.

The concept allows mechanical resistance around the knee joint to be influenced through the interaction between the antagonistic actuators and the elastic mechanism.

This provides a physical basis for investigating variable joint stiffness and compliant robotic behaviour.

---

## Pneumatic Soft-Tissue Simulation

Pneumatic chambers are used to reproduce selected soft-tissue compliance around the knee structure.

The pneumatic subsystem provides:

* Controlled inflation
* Controlled pressure release
* Variable surface compliance
* Physical deformation around the phantom knee

This subsystem was developed to provide a simplified physical representation of soft-tissue behaviour for exoskeleton-interface testing.

---

## Embedded Sensing

The system includes distributed embedded sensors for monitoring motion and local system conditions.

Sensor hardware includes:

* ISM330DHCX inertial measurement unit
* MMC5983MA magnetometer
* TMP117 temperature sensor
* FeatherS3 microcontroller platforms

Sensor data is transmitted to the Raspberry Pi and integrated into the ROS 2 communication architecture.

---

## Control Platform

### Raspberry Pi

The central computing platform is:

* Raspberry Pi 5
* Ubuntu 24.04 LTS
* ROS 2 Jazzy

The Raspberry Pi manages:

* Actuator communication
* Sensor acquisition
* ROS 2 nodes
* Data routing
* Communication with the Unity digital twin

---

## ROS 2

ROS 2 is used as the main middleware for communication between the physical hardware and digital components.

The ROS 2 system includes functionality for:

* Actuator control
* Actuator feedback
* Embedded sensor acquisition
* Position and velocity communication
* Unity connectivity
* Real-time system visualization

Selected ROS 2 components may be added to the `ros2/` directory as the repository is prepared for public release.

---

## Unity Digital Twin

A Unity-based digital twin represents the physical robotic knee in real time.

The digital environment supports:

* Real-time joint visualization
* Physical-to-digital synchronization
* Control interaction
* Sensor-data visualization
* System monitoring
* Interactive component exploration

The Unity model communicates with ROS 2 through the ROS–Unity communication interface.

---

## 3D Modelling and Fabrication

Custom structural and mechanical components were designed and fabricated specifically for the robotic phantom knee.

The development workflow included:

* 3D modelling
* Mechanical design
* Iterative prototyping
* 3D printing
* Mechanical assembly
* Integration with actuators, sensors, and pneumatic components

Blender was used for several modelling and visualization tasks during development.

---

## Repository Structure

```text
robotic-phantom-knee-digital-twin/
│
├── docs/
│   └── images/
│
├── embedded/
│
├── hardware/
│
├── ros2/
│
├── unity/
│
└── README.md
```

### `docs/`

Technical documentation, architecture diagrams, figures, and supporting material.

### `embedded/`

Selected embedded-system documentation and firmware related to the distributed sensors.

### `hardware/`

Hardware architecture, subsystem descriptions, mechanical integration information, and selected design documentation.

### `ros2/`

Selected ROS 2 packages, nodes, configuration files, and communication documentation.

### `unity/`

Documentation and selected material related to the Unity digital twin.

---

## Technologies

### Robotics and Control

* ROS 2 Jazzy
* Robotic actuation
* Antagonistic control
* Variable-stiffness concepts
* Real-time feedback

### Embedded Systems

* Raspberry Pi 5
* FeatherS3
* IMU sensing
* Magnetometer sensing
* Temperature sensing
* Serial communication

### Simulation and Digital Twin

* Unity
* ROS–Unity communication
* Real-time visualization
* Digital-twin synchronization

### Mechanical Development

* 3D modelling
* 3D printing
* Mechanical prototyping
* Pneumatic systems
* Variable-stiffness mechanisms

---

## Project Status

The thesis project has been completed and experimentally demonstrated.

This repository is being prepared as a curated public technical representation of the project.

Not all development files are included. Large build files, temporary files, complete Unity project data, generated ROS 2 build directories, and institution-related or unnecessary internal material are intentionally excluded.

---

## Master's Thesis

This project formed the practical and research basis of my Master's thesis in Biomedical Engineering at Chalmers University of Technology.

**Official publication:**

[Chalmers Open Digital Repository](https://hdl.handle.net/20.500.12380/311285)

---

## Author

**Wajih Habrah**
Biomedical Engineer

* [Portfolio](https://wajihhabrah.github.io/)
* [LinkedIn](https://www.linkedin.com/in/wajih-habrah-38103367/)
* [GitHub](https://github.com/WajihHabrah)
* [YouTube Demonstration](https://www.youtube.com/watch?v=lWRFAtuQzvM)

---

## Notice

This repository is intended for portfolio, educational, and technical documentation purposes.

Only material suitable for public release is included. Confidential, institution-restricted, third-party proprietary, or unnecessary internal development material is excluded.

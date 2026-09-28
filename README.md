# Smart-Industrial-Valve-Actuator
ESP32-S3-based smart valve actuator with stepper motor control, 24V hardware architecture, and FSM-based control for precise industrial automation.
An ESP32-S3-based embedded industrial automation system designed to control a valve actuator using a stepper motor, 24 V power architecture, and finite-state-machine (FSM) control logic for reliable and repeatable valve positioning.

The project focuses on applying embedded control principles to an industrial actuation problem, combining microcontroller programming, motor control, power interfacing, control logic and hardware validation.

1. Project Overview

Industrial valves are commonly used to regulate or control the flow of fluids and gases in automated systems. Reliable positioning of the valve actuator is important because incorrect positioning can affect the operation of the overall process.

This project develops a microcontroller-based actuator system capable of controlling valve movement through a stepper motor.

The system uses an ESP32-S3 as the main controller and implements state-based control logic to manage actuator operation.

2. Objectives

The primary objectives of the project are:

Develop an embedded valve-actuation system using ESP32-S3.
Control a stepper motor for valve positioning.
Implement reliable state-based actuator control.
Integrate the 24 V power architecture with the embedded control system.
Develop repeatable actuator movement.
Validate the actuator over repeated operating cycles.
Evaluate positional repeatability and system reliability.
3. System Architecture

The overall system can be represented as:

             ┌─────────────────────┐
             │     Control Input   │
             └──────────┬──────────┘
                        │
                        ▼
             ┌─────────────────────┐
             │      ESP32-S3       │
             │   Control Logic     │
             └──────────┬──────────┘
                        │
                        ▼
             ┌─────────────────────┐
             │    FSM Controller   │
             └──────────┬──────────┘
                        │
                        ▼
             ┌─────────────────────┐
             │ Stepper Motor Drive │
             └──────────┬──────────┘
                        │
                        ▼
             ┌─────────────────────┐
             │   Valve Actuator    │
             └─────────────────────┘

The ESP32-S3 executes the control logic and generates the required actuator commands.

4. Hardware Architecture
ESP32-S3

The ESP32-S3 acts as the primary embedded controller.

Its responsibilities include:

Executing actuator-control firmware.
Managing the actuator state machine.
Generating motor-control commands.
Coordinating the operating sequence.
Handling control inputs and system states.
24 V Power Architecture

The actuator system uses a 24 V power architecture, appropriate for the industrial-control context of the project.

The power architecture separates the actuator-side power requirements from the low-voltage embedded controller.

Conceptually:

             24 V Supply
                  │
        ┌─────────┴─────────┐
        │                   │
        ▼                   ▼
 Actuator / Motor       Embedded Power
        │                   │
        ▼                   ▼
 Stepper Motor           ESP32-S3

The exact power-conversion and protection implementation should be documented in the hardware schematic accompanying this repository.

5. Stepper Motor Control

A stepper motor is used as the actuator for valve movement.

The controller translates the desired valve operation into motor-control commands.

The basic control sequence is:

Desired Valve Position
          ↓
    Control Decision
          ↓
   Motor Direction
          ↓
      Step Pulses
          ↓
   Stepper Movement
          ↓
     Valve Position

The use of a stepper motor allows controlled incremental movement of the actuator.

6. Finite-State Machine Control

The actuator operation is organized using a Finite State Machine (FSM).

Instead of treating the actuator as a single continuous operation, the controller manages distinct operating states.

A conceptual representation is:

             ┌───────────────┐
             │     IDLE      │
             └───────┬───────┘
                     │
                     ▼
             ┌───────────────┐
             │    OPENING    │
             └───────┬───────┘
                     │
                     ▼
             ┌───────────────┐
             │     OPEN      │
             └───────────────┘

             ┌───────────────┐
             │   CLOSING     │
             └───────┬───────┘
                     │
                     ▼
             ┌───────────────┐
             │    CLOSED     │
             └───────────────┘

The actual implementation should follow the states and transitions implemented in the firmware.

FSM-based control provides a structured way of handling:

Start/stop conditions
Actuator movement
Target states
State transitions
Completion conditions
Abnormal operating conditions where implemented
7. Control Sequence

A typical actuator operation follows this sequence:

1. Receive actuator command
        ↓
2. Determine required valve state
        ↓
3. Enter appropriate FSM state
        ↓
4. Generate stepper-motor control
        ↓
5. Move actuator
        ↓
6. Reach target position/state
        ↓
7. Stop motor
        ↓
8. Maintain final state

This approach keeps the actuator operation deterministic and easier to debug.

8. Embedded Control

The project combines several embedded-system concepts:

Microcontroller programming
Digital control logic
State machines
Motor control
Hardware interfacing
Real-time operation
Power-system integration
Actuator control

The ESP32-S3 provides the computational and control layer while the motor/actuator forms the physical output layer.

9. Hardware-Software Integration

The project demonstrates the interaction between embedded firmware and physical hardware.

       SOFTWARE
           │
           ▼
     ESP32-S3 Firmware
           │
           ▼
      Control Logic
           │
           ▼
       Motor Drive
           │
           ▼
       HARDWARE
           │
           ▼
    Stepper Actuator
           │
           ▼
       Valve Motion

This hardware-software interaction is central to the project.

10. Validation

The actuator was subjected to 300+ operating cycles to evaluate repeatability and reliable operation. The documented testing achieved approximately ±0.9° positional repeatability.

The validation process demonstrates that the project was tested beyond a single successful demonstration.

Validation Focus
Repeated actuator operation
Position consistency
Control-state reliability
Motor actuation
System response
Long-cycle repeatability
11. Key Result
Positional Repeatability

±0.9°

Validation Cycles

300+ operating cycles

These results provide a measurable indication of the actuator's repeatability during testing.

12. Engineering Challenges
Reliable Actuation

The controller must consistently translate control commands into physical actuator movement.

Approach: Use structured FSM-based control and controlled stepper-motor operation.

Repeatability

Repeated operation can reveal positioning inconsistencies that may not be visible during a single test.

Approach: Validate the actuator over multiple operating cycles and measure positional repeatability.

Power Integration

The system combines a 24 V industrial-side architecture with a low-voltage microcontroller.

Approach: Separate the actuator power architecture from the embedded controller requirements.

Control-State Management

Industrial actuators can have multiple operating conditions that need to be handled predictably.

Approach: Implement FSM-based control rather than relying on unstructured sequential logic.

13. Software / Development
Controller
ESP32-S3
Embedded Development
Embedded C/C++
Microcontroller programming
FSM-based control
Stepper-motor control
Engineering Areas
Industrial Automation
Embedded Systems
Control Systems
Motor Control
Actuator Systems
Hardware-Software Integration
14. Project Workflow

The development process can be summarized as:

Requirement
    ↓
Actuator Architecture
    ↓
24 V Power Architecture
    ↓
ESP32-S3 Integration
    ↓
Stepper Motor Control
    ↓
FSM Implementation
    ↓
Hardware Integration
    ↓
Functional Testing
    ↓
Repeated-Cycle Validation
    ↓
Performance Evaluation
15. Why This Project Matters

This project demonstrates the practical integration of:

Microcontroller + Control Logic + Motor + Actuator + Power Architecture + Testing

rather than focusing only on firmware development.

The project provides hands-on exposure to the type of engineering workflow involved in embedded control and industrial automation systems.

16. Key Technologies

Controller

ESP32-S3

Actuation

Stepper Motor
Valve Actuator

Control

Finite State Machine
Embedded Control
Motor Control

Hardware

24 V Power Architecture
Embedded Hardware
Actuator Interface

Engineering

Industrial Automation
Embedded Systems
Control Systems
Hardware-Software Integration
Functional Testing
Performance Validation
17. Project Status

Status: Completed Prototype / Validated System

The system has been validated through 300+ operating cycles, achieving approximately ±0.9° positional repeatability during testing.

18. Repository Structure

A suitable repository structure can be:

Smart-Industrial-Valve-Actuator/
│
├── README.md
│
├── firmware/
│   ├── main/
│   └── control/
│
├── hardware/
│   ├── schematic/
│   ├── pcb/
│   └── wiring/
│
├── simulation/
│
├── testing/
│   ├── test-results/
│   └── validation-data/
│
├── documentation/
│
└── images/

Only include folders/files that actually exist in the repository.

19. Skills Demonstrated
Embedded C/C++
ESP32-S3
Microcontroller Programming
Stepper Motor Control
FSM-Based Control
Industrial Automation
Actuator Control
Hardware-Software Integration
24 V System Architecture
Hardware Testing
Performance Validation
Troubleshooting
Control Systems

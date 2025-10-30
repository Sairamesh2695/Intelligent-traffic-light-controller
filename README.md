#🟢 Intelligent Traffic Light Controller (I-TLC)
🧠 Project Overview

I-TLC is a Verilog-based design for an Intelligent Traffic Light Controller that operates using a finite state machine (FSM). The system is developed to efficiently manage traffic flow at a four-way intersection without the need for a human traffic officer.

The design prioritizes the main road traffic—assumed to have a higher density—while ensuring safety and fairness for side-road vehicles and pedestrians through sensor-based detection and timed signal transitions.

🚦 Features

Automated traffic control using FSM logic

Sensor-based detection for vehicles/pedestrians on the side road

Priority handling for main road congestion

Clearly defined state transitions using traffic rules

Configurable timing for each light phase (TL = 10s, TS = 6s)

Red, Yellow, and Green light behavior based on standard traffic norms

🧩 System Description

The system consists of:

Main Road Light (priority traffic)

Side Road Light (controlled via sensor)

Clock input for timing

Reset for initialization

Sensor input indicating side-road presence

Traffic Rules Followed:
Light	Description
🔴 Red	Stop the vehicle completely
🟡 Yellow	Slow down and prepare to stop before zebra line
🟢 Green	Vehicle can proceed normally
🔁 FSM Design
State Assignment
Bit	Representation
MSB	Red light
LSB	Green light
Timer Parameters

TL (Timer Large) – 10 seconds

TS (Timer Small) – 6 seconds

State Table
State	Side Road Output	Main Road Output
S0	100001	
S1	100010	
S2	001100	
S3	010100	
Transition Logic
From	Condition	To
S0	TL = 1, C = 0	S1
S1	TL = 0, C = 1	S2
S2	TS expires	S3
S3	TL expires & C = 0	S0
🧮 Functional Flow

Initialization: System resets to default state (main road green).

Sensor Detection: Side road sensor activates when vehicles/pedestrians are present.

FSM Transition: Controller cycles through states based on timers and sensor signals.

Signal Update: LEDs/light signals update accordingly for main and side roads.

🧰 Tools & Technologies

Language: Verilog HDL

Simulation: ModelSim / Vivado

Design Methodology: Finite State Machine (FSM)

Hardware Target: FPGA implementation (optional)

📊 Simulation Result

The simulation verifies correct state transitions and timing behavior, ensuring:

Main road flow is prioritized under normal conditions.

Side road traffic is allowed safely when detected.

All traffic rules are adhered to dynamically via FSM logic.

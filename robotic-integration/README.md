# Virtual Commissioning for Robotic Integration

Digital twin for robot-conveyor integration with PLC synchronization and virtual testing.

---

## Project Overview

This project demonstrates the implementation of a **digital twin for robotic systems** to enable virtual commissioning before physical deployment. By integrating simulation software, PLC simulators, and robot controller software, the entire system can be tested and validated without requiring physical hardware.

**Key Innovation:** Test robot programs, PLC logic, and conveyor interactions in a virtual environment, eliminating the need to purchase and install physical robots during the development phase.

**Status:** Proof of concept completed successfully  
**Domain:** Robotic integration, virtual commissioning, digital twin

---

## Key Results

### Proof of Concept Success
- ✅ **Successfully integrated** Simulation Software + PLC + Robot Controller
- ✅ **Demonstrated** bidirectional communication between all three systems
- ✅ **Validated** robot-conveyor synchronization in virtual environment
- ✅ **Proved feasibility** of testing control logic without physical hardware

### Expected Benefits (Based on PoC)
- **Cost savings:** Eliminate need to purchase robots during development phase
- **Faster iterations:** Test and refine robot programs without waiting for hardware delivery
- **Reduced commissioning time:** Validate control logic before on-site deployment
- **Risk mitigation:** Identify integration issues early in virtual environment

---

## Problem Statement

Traditional robotic system commissioning relies heavily on physical testing, which presents significant challenges:

### Time-Consuming
- Ordering robots and preparing test environments takes **several weeks**
- Testing control logic on real systems involves long setup times and iterative adjustments
- Project delays accumulate during FAT (Factory Acceptance Test) and SAT (Site Acceptance Test)

### High Costs
- Purchasing physical robots for testing requires significant upfront capital investment
- Setting up physical test environments is expensive and resource-intensive
- Changes after installation are costly and time-consuming

### Limited Flexibility
- Modifying physical systems after installation is labor-intensive
- Testing "what-if" scenarios requires additional hardware or significant reconfiguration
- Errors discovered during commissioning cause expensive delays

**These challenges are amplified** as automation systems become more complex, requiring tighter coordination between robots, PLCs, conveyors, and other equipment.

---

## Proposed Solution: Digital Twin Approach

### Core Concept

Create a **virtual replica** of the robotic system that integrates:
- **3D simulation software:** Plant layout and robot visualization
- **PLC Simulator:** Virtual PLC running real control logic (TIA Portal + PLCSim Advanced)
- **Robot Controller:** Virtual robot controller running actual robot programs

**Key Advantage:** This approach simulates **the entire plant ecosystem**, not just robot-PLC communication. It includes conveyors, sensors, and other equipment, ensuring comprehensive testing.

### Why This Approach?

We chose integration through simulation software over direct PLC-to-robot connection because:
1. ✅ Simulates the complete system (conveyors, sensors, other equipment)
2. ✅ Provides flexibility to integrate third-party automation solutions
3. ✅ Enables testing of complex interactions between multiple systems
4. ✅ Offers visual validation of robot movements and system behavior
5. ✅ Supports future expansion and customization

---

## Implementation Process

The digital twin implementation follows three key phases:

### Phase 1: Simulation Software Setup and Preparation

**Objective:** Configure the simulation environment with all necessary components.

**Activities:**
1. **Robot Configuration**
   - Added robot model with predefined joint definitions
   - Configured gripper for box handling
   - Integrated robot controller interface

2. **Conveyor System Setup**
   - Created pick-up and drop-off conveyors
   - Configured workflow for box movement
   - Defined sensors and triggers

**Outcome:** Complete simulation environment ready for integration.

---

### Phase 2: Simulation Software-PLC Connection and Tags Mapping

**Objective:** Establish bidirectional communication between simulation and PLC.

**Technology Stack:**
- **PLC:** Siemens TIA Portal
- **PLC Simulator:** PLCSim Advanced
- **Communication:** Real-time bidirectional data exchange

**Implementation:**

1. **Connection Establishment**
   - Configured network connection between simulation software and PLCSim Advanced
   - Enabled automatic tag synchronization
   - Verified bidirectional data flow

2. **IO Tag Mapping**

   **System IOs:** Physical elements in simulation
   - Conveyor sensors → PLC input tags
   - Conveyor motors → PLC output tags
   - Robot request signals → PLC inputs
   - Example mapping:
```
     PLC Tag: SR4.PE1 → Simulation Sensor: "isBlocked"
```

   **Robot IOs:** Custom robot control tags
   - Robot enable signals
   - Pick/place request triggers
   - Position feedback tags
   - Status indicators

**Outcome:** Seamless real-time communication between PLC and simulation environment.

---

### Phase 3: Simulation Software-Robot Controller Connection

**Objective:** Integrate robot controller software with digital twin.

**Technology Stack:**
- **Robot Controller:** Fanuc Roboguide
- **Integration:** Simulation software plugin for Roboguide
- **Communication:** Direct IO mapping

**Implementation:**

1. **Connection Setup**
   - Installed simulation software plugin in Roboguide
   - Established connection between systems
   - Synchronized robot IOs

2. **IO Tag Assignment**
   - All Roboguide IOs automatically appear in simulation software
   - Mapped robot outputs to simulation robot properties
   - Connected robot inputs to PLC and conveyor signals

3. **Gripper Logic Implementation**
   - Developed custom gripper control logic
   - Connected gripper to designated robot outputs
   - Tested pick-and-place operations

**Outcome:** Fully functional virtual robot controlled by real robot programs.

---

## Test Results

### Proof of Concept Validation

The test case demonstrated a complete pick-and-place cycle:

**Scenario:**
1. Box arrives on input conveyor
2. Sensor detects box → PLC signals robot
3. Robot picks box from input conveyor
4. Robot places box on output conveyor
5. Box exits on output conveyor

**Results:**
- ✅ **PLC logic executed correctly** in virtual environment
- ✅ **Robot program ran successfully** without physical hardware
- ✅ **Conveyor synchronization worked as expected**
- ✅ **Gripper operations functioned properly**
- ✅ **System timing and coordination validated**

![Robot-Conveyor Setup](./media/videos/POC.gif)

This video shows the real testing workflow, including:
- Running the simulation with PLC and robot controller
- Identifying synchronization issues
- Debugging communication problems
- Iterative testing approach

### Technical Achievements

| Component | Achievement |
|-----------|-------------|
| **Simulation Setup** | Configured in 1 day |
| **PLC Integration** | Bidirectional communication established |
| **Robot Integration** | Virtual robot controlled by real programs |
| **System Validation** | Complete pick-and-place cycle tested successfully |



#### Testing and Debugging

![Testing and Debugging Process](./media/videos/Robot1.gif)

![Problem-Solving Demo](./media/videos/Robot1.gif)

This video shows the real testing workflow, including:
- Discovering integration issues during testing
- Analyzing root causes
- Implementing fixes in real-time
- Validating solutions

**These videos showcase the actual development process**, highlighting the iterative nature of virtual commissioning and the ability to rapidly identify and resolve issues without physical hardware.

---

## Benefits Demonstrated

### 1. Cost Savings

**Traditional Approach:**
- Purchase robot: €30,000-€80,000
- Setup test environment: €10,000-€20,000
- **Total initial investment:** €40,000-€100,000

**Digital Twin Approach:**
- Software licenses: €4,000-€5,000 (one-time)
- **Savings:** €35,000-€95,000 per project

### 2. Time Savings

**Traditional Approach:**
- Robot ordering and delivery: 4-8 weeks
- Physical setup and testing: 2-4 weeks
- Iterative adjustments: 1-3 weeks
- **Total:** 7-15 weeks before commissioning

**Digital Twin Approach:**
- Virtual environment setup: 1 week
- Testing and validation: 1-2 weeks
- **Total:** 2-3 weeks before commissioning
- **Time saved:** 5-12 weeks

### 3. Increased Flexibility

**Traditional Limitations:**
- Physical changes require hardware modifications
- Testing alternatives requires additional equipment
- Errors discovered late in commissioning

**Digital Twin Advantages:**
- ✅ Test unlimited scenarios virtually
- ✅ Rapid iteration on control logic
- ✅ Early error detection
- ✅ Risk-free experimentation

---

## Technical Architecture

### System Integration Diagram
```
┌──────────────────────────────────────────────────┐
│            Simulation (Core Platform)            │
│                                                  │
│  ┌──────────────┐          ┌──────────────────┐  │
│  │   Robot      │          │    Conveyors     │  │
│  │ Visualization│◄────────►│    & Sensors     │  │
│  └───────┬──────┘          └────────┬─────────┘  │
│          │                          │            │
│          │    Bidirectional IO      │            │
│          │                          │            │
└──────────┼──────────────────────────┼────────────┘
           │                          │
           ▼                          ▼
 ┌─────────────────┐        ┌──────────────────┐
 │   Roboguide     │        │   PLCSim Advanced│
 │ (Robot Programs)│        │   (PLC Logic)    │
 └─────────────────┘        └──────────────────┘
```

### Component Responsibilities

**Simulation Software:**
- 3D visualization of robot and plant
- Physics simulation
- Workflow management
- IO tag synchronization hub

**PLC Simulator (PLCSim Advanced):**
- Runs actual PLC control logic
- Manages system sequencing
- Coordinates robot-conveyor timing
- Provides real-time feedback

**Robot Controller (Roboguide):**
- Executes actual robot programs
- Simulates robot kinematics
- Validates trajectory planning
- Tests safety logic

---

## Lessons Learned

### What Worked Well

**1. Seamless Integration**
- Simulation software plugins for both PLC and robot controller worked reliably
- Bidirectional communication was stable and real-time
- IO mapping process was straightforward

**2. Reusable Components**
- Robot models can be reused across projects
- Gripper logic is easily adaptable
- Conveyor configurations are transferable

**3. Early Validation**
- Identified potential timing issues before physical deployment
- Tested multiple pick-and-place strategies virtually
- Validated PLC logic without site access

### Challenges Encountered

**1. Gripper Configuration**
- Custom gripper logic required for each gripper type
- Not automatically inherited from Roboguide
- **Solution:** Created library of common gripper configurations

**2. Timing Synchronization**
- Ensuring simulation runs at real-time speed
- Matching PLC scan cycle with simulation tick rate
- **Solution:** Configured synchronization parameters carefully

**3. Learning Curve**
- Understanding IO mapping conventions
- **Solution:** Developed documentation and templates

---

## Project Status and Future Work

### Current Status: Proof of Concept Completed ✅

The proof of concept successfully demonstrated:
- ✅ Technical feasibility of digital twin approach
- ✅ Integration of all three core systems
- ✅ Virtual commissioning of robot-conveyor workflow
- ✅ Validation of control logic without physical hardware

### Project Discontinued

**Reason:** Project was halted after one month due to:
- Reassignment to other priorities
- Disrupted collaboration with Belgium branch
- Resource reallocation

**Despite discontinuation**, the proof of concept proved the viability of the approach for future projects.

### Future Potential

If resumed, the project could deliver:

**Phase 1: Framework Completion (8-12 weeks)**
- Develop reusable digital twin templates
- Create library of robot and gripper configurations
- Establish standardized integration process

**Phase 2: Live Project Deployment (12-16 weeks)**
- Deploy digital twin alongside actual project
- Validate approach in real commissioning scenario
- Measure actual time and cost savings

**Phase 3: Scaling (Ongoing)**
- Roll out to multiple robot integration projects
- Expand to support additional robot brands
- Integrate with other automation systems

---

## Technologies Used

- **Simulation Platform:** Simulation software (3D discrete event simulation)
- **PLC:** Siemens TIA Portal + PLCSim Advanced
- **Robot Controller:** Fanuc Roboguide
- **Programming:** C# for custom logic and gripper control

---

## Note on Proprietary Work

This project was completed during professional work at Dymation (2024). The proof of concept was successfully delivered before project discontinuation. All proprietary code and client-specific details have been removed. Documentation focuses on methodology, architecture, and technical approach.

*Return to [main portfolio](../README.md) | View [other projects](../README.md#featured-projects)*

---

© 2022-2025 Mohammad Bahrami. All Rights Reserved.
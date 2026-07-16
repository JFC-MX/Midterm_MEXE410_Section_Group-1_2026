## CAPA (Corrective and Preventive Action)

This report addresses the critical non-conformances identified during the system audit of the SAFR-2000 Smart Autonomous Forklift Robot. The engineering team has reviewed the identified flaws regarding system autonomy, sensor integrity, computational architecture, physical stability, and braking dynamics. The following sections detail the re-engineering strategies required to bring the system into full compliance with industrial safety standards.

---

## NCR Question-1:
NCR-Q-1) "If the robot is autonomous, why does losing communication immediately make it unsafe? Doesn't that suggest your autonomy depends on continuous external supervision rather than onboard intelligence?"

<ins>Identified Non-Conformance:</ins>
The system immediately enters an unsafe/protective stop state upon losing external communication, indicating a reliance on external supervision rather than true onboard autonomy.

<ins>Root Cause:</ins>
The control logic erroneously equated a loss of fleet-management communication with a loss of local environmental awareness.

* <ins>**Corrective & Preventive Action:**</ins>
    * The control architecture will be re-engineered to feature a "Local Autonomous State."
    * Upon communication loss, the vehicle will no longer execute an immediate hard stop in active traffic lanes.
    * Onboard intelligence will utilize its local map to gracefully decelerate and route the forklift to a pre-designated safe shoulder or designated drop zone.
    * A Category 2 stop will only be initiated if the onboard sensors detect an immediate, unavoidable physical obstruction during this localized navigation.
 
---

## NCR-02: Sensor Data Corruption and Validation

* **Identified Non-Conformance:** The safety architecture lacks a mechanism to detect incorrect or corrupted data from a LiDAR or depth camera, relying solely on detecting total sensor failure.
* **Root Cause:** The perception module accepted sensor inputs as absolute truth without dynamic cross-validation against expected physical behaviors.
* **Corrective & Preventive Action:**
    * We will implement a closed-loop observer model utilizing state-space representations of the forklift's mechanical system.
    * By continuously calculating the expected kinematics using system $A, B, C, D$ matrices, the controller will predict the robot's spatial state in real-time.
    * If a sensor reports environmental or positional data that violently deviates from the predicted physical state, the system will flag the input as invalid.
    * The architecture will fallback to a sensor-voting protocol utilizing the remaining redundant LiDARs to safely maneuver or halt the vehicle.
 
---

## NCR-03: Sensor Architecture and Computational Overhead

* **Identified Non-Conformance:** The use of multiple LiDAR sensors lacks engineering justification regarding computational workload, latency, and synchronization compared to a single 360° unit.
* **Root Cause:** The initial design prioritized field-of-view redundancy without optimizing the data pipeline, leading to potential real-time processing bottlenecks.
* **Corrective & Preventive Action:**
    * A single 360° LiDAR is unviable because the forklift mast and a 2,000 kg payload physically occlude the sensor, creating massive frontal blind spots.
    * To resolve the synchronization and latency issues of multiple units, the perception hardware will be re-engineered.
    * Point-cloud filtering and sensor fusion will be offloaded to a dedicated, hardware-accelerated FPGA at the edge.
    * This removes the computational burden from the main CPU, ensuring that real-time safety performance and obstacle detection occurs in microseconds without impacting battery endurance.

---

## NCR-04: Physical Stability vs. Software Limits

* **Identified Non-Conformance:** The system relies on software commands to maintain stability, lacking physical safeguards to prevent a 2,000 kg tip-over in the event of software latency or failure.
* **Root Cause:** The mechanical chassis design leaned heavily on software-defined deceleration profiles to prevent inertial tipping, violating fail-safe mechanical principles.
* **Corrective & Preventive Action:**
    * The mechanical system model of the forklift chassis will be physically altered to drastically lower the center of gravity.
    * Physical hard-stops and limit switches will be integrated into the mast and tilt assemblies to physically restrict the load from reaching an unstable moment arm.
    * The suspension will incorporate heavy-duty mechanical dampers to remove lateral allowance and ensure rigidity during high-speed turns.
    * These physical constraints guarantee that even if the software freezes while commanding maximum speed, the vehicle's geometry physically cannot exceed the tipping threshold.

---

## NCR-05: Braking Dynamics and Payload Validation

* **Identified Non-Conformance:** There is a lack of engineering calculation demonstrating that the braking system can safely halt a maximum payload (2,000 kg) at maximum speed (1.5 m/s) in a shared human workspace.
* **Root Cause:** Braking specifications were estimated based on unladen chassis weights rather than rigorous electromechanical modeling of the fully loaded system.
* **Corrective & Preventive Action:**
    * The drive and braking system will undergo a full redesign utilizing high-fidelity mathematical modeling of the electromechanical systems.
    * Calculations will strictly define the equivalent inertia and damping of the transmission under a full 2,000 kg load.
    * Fail-safe, normally engaged spring brakes will be upgraded to match the required stopping torque derived from the torque-speed characteristics of the DC drive motors.
    * Stopping distances will be hardware-validated to guarantee they fall within the protective field limits defined by ISO 3691-4, ensuring the robot will always halt before contacting a detected pedestrian.

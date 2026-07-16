## 📝 CAPA (Corrective and Preventive Action) 📝

   This report addresses the critical non-conformances identified during the system audit of the SAFR-2000 Smart Autonomous Forklift Robot. The engineering team has reviewed the identified flaws regarding system autonomy, sensor integrity, computational architecture, physical stability, and braking dynamics. The following sections detail the re-engineering strategies required to bring the system into full compliance with industrial safety standards. </br>

---

## NCR Question-1:
### "If the robot is autonomous, why does losing communication immediately make it unsafe? Doesn't that suggest your autonomy depends on continuous external supervision rather than onboard intelligence?"

### CAPA-1:
* <ins>Identified Non-Conformance:</ins>
The system immediately enters an unsafe/protective stop state upon losing external communication, indicating a reliance on external supervision rather than true onboard autonomy.

* <ins>Root Cause:</ins>
The control logic erroneously equated a loss of fleet-management communication with a loss of local environmental awareness.

* <ins>**Corrective & Preventive Action:**</ins>
    * Upon communication loss, programs will be updated so the vehicle will no longer execute an immediate hard stop in active traffic lanes.
    * Onboard intelligence will utilize its local map to gracefully decelerate and route the forklift to a pre-designated safe shoulder or designated drop zone.
    * A Category 2 stop will only be initiated if the onboard sensors detect an immediate, unavoidable physical obstruction during this localized navigation.
 
---

## NCR Question-2:
### "Your safety architecture depends heavily on LiDARs and depth cameras. If one of these sensors provides incorrect data rather than failing completely, how does the system detect that it is receiving invalid information instead of making an unsafe decision based on incorrect inputs?"

### CAPA-2:
* <ins>Identified Non-Conformance:</ins>
The safety architecture lacks a mechanism to detect incorrect or corrupted data from a LiDAR or depth camera, relying solely on detecting total sensor failure.

* <ins>Root Cause:</ins>
The perception module accepted sensor inputs as absolute truth without dynamic cross-validation against expected physical behaviors.

* <ins>**Corrective & Preventive Action:**</ins>
    * Implement a closed-loop observer model utilizing state-space representations of the forklift's mechanical system.
    * Flag sensor input as invalid if the reported environmental or positional data violently deviates from the predicted physical state.
    * Fall back to a sensor-voting protocol utilizing the remaining redundant LiDARs to safely maneuver or halt the vehicle if invalid data is detected.
 
---

## NCR Question-3:
### "Why did you select multiple LiDAR sensors instead of a single 360° LiDAR? Considering the increased computational workload, synchronization, calibration complexity, and battery consumption, what engineering analysis demonstrates that this architecture is necessary and does not compromise real-time safety performance?"

### CAPA-3:
* <ins>Identified Non-Conformance:</ins>
The use of multiple LiDAR sensors lacks engineering justification regarding computational workload, latency, and synchronization compared to a single 360° unit.

* <ins>Root Cause:</ins>
The initial design prioritized field-of-view redundancy without optimizing the data pipeline, leading to potential real-time processing bottlenecks.

* <ins>**Corrective & Preventive Action:**</ins>
    * Re-engineer and calibrate the perception hardware to resolve synchronization and latency issues.
    * Offload point-cloud filtering and sensor fusion to a dedicated, controller (FPGA or PLC) at the edge.
    * Remove the computational burden from the main CPU to ensure real-time safety performance and obstacle detection occurs in microseconds without impacting battery endurance.
 
---

## NCR Question-4:
### "You claim that software-defined operational limits prevent tip-over and maintain stability. Software cannot generate stability, it only sends commands. If the software miscalculates, freezes, or experiences excessive latency, what physically prevents a 2,000 kg forklift from tipping over?"

### CAPA-4:
* <ins>Identified Non-Conformance:</ins>
The system relies on software commands to maintain stability, lacking physical safeguards to prevent a 2,000 kg tip-over in the event of software latency or failure.

* <ins>Root Cause:</ins>
The mechanical chassis design leaned heavily on software-defined deceleration profiles to prevent inertial tipping, violating fail-safe mechanical principles.

* <ins>**Corrective & Preventive Action:**</ins>
    * Physically alter the mechanical system model of the forklift chassis to drastically lower the center of gravity.
    * Integrate physical hard-stops and limit switches into the mast and tilt assemblies to physically restrict the load from reaching an unstable moment arm.
    * Guarantee through these mechanical constraints that the vehicle physically cannot exceed the tipping threshold, even if the software freezes while commanding maximum speed.
 
 ---

 ## NCR Question-5:
### "You claim a payload capacity of 2,000 kg while stating that the vehicle operates safely alongside human workers. What engineering calculations or validation demonstrate that the braking system, stopping distance, and stability remain within safe limits under maximum payload and maximum speed?"

### CAPA-5:
* <ins>Identified Non-Conformance:</ins>
There is a lack of engineering calculation demonstrating that the braking system can safely halt a maximum payload (2,000 kg) at maximum speed (1.5 m/s) in a shared human workspace.

* <ins>Root Cause:</ins>
Braking specifications were estimated based on unladen chassis weights rather than rigorous electromechanical modeling of the fully loaded system.

* <ins>**Corrective & Preventive Action:**</ins>
    * Execute a full redesign of the drive and braking system utilizing high-fidelity mathematical modeling of the electromechanical systems.
    * Strictly define the equivalent inertia and damping of the transmission under a full 2,000 kg load.
    * Upgrade the fail-safe, normally engaged spring brakes to match the required stopping torque derived from the torque-speed characteristics of the DC drive motors.
 ---

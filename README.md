<h1 align="center">MEXE 410 Midterm Project: Mechatronics Innovation & ISO/IEC Accreditation Simulation (ISO/IEC)</h1>
<h2 align="center">MEXE 3301 Group #1: SAFR-2000: Smart Autonomous Forklift Robot </h2>

---

# 🔍 Product Description 🔎

## What it does:
  The SAFR-series 2000 is an unmanned, autonomous driving forklift robot that utilizes the fusion for multi-sensor capabilities for intelligent navigation and precise material handling. It is designed to completely automate the transportation of palletized payloads (for up to 2000 Kg). This robot has a sub-centimeter positioning accuracy of ±5mm and a maximum adjustable speed of 1.5m/s. It also has access to features beyond just simple transport, such as dynamic real-time mapping, flexible obstacle avoidance, to precisely recognize the pallet area and how to carry it efficiently.

## Who uses it:
  The primary users are operations and facility managers across the Logistics, Automation, Manufacturing, and Retail industries. It is specifically deployed to facilities that require highly adaptable, constant ease of transportation of payloads within the facility and work safely alongside human workers without the need for isolated automated zones.

## Main Parts:
  To achieve the multi-level intelligent navigation and handling, the SAFR-series relies on a heavy integration of hardware and software architecture:

* <ins> Sensors For Perception:</ins> It contains a multitude of LiDAR (Light Detection and Ranging) sensors, as well as depth cameras positioned in various parts for different purposes. These are positioned at the top of the robot to map the environment. Additionally, these are also positioned at the front and back to detect obstacles. Similarly, they are also situated at the rear fork-tip to ensure the load is carried stably. 

* <ins>Drive and Actuation System:</ins> The main chassis houses the inner components with the forks positioned at the front. These forks are capable of lifting heights up to 210mm with the ability to counter tilt and adjust for inclines. 

* <ins>Power Systems:</ins> It is configured with a rechargeable battery with operation times of about 5 hours with charging times no longer than 2 hours. 

* <ins>Control and Monitoring Infrastructure:</ins> It contains 4G and Wi-Fi modules with support to be controlled remotely and to customize the scheduling of operation time and sends data to be monitored. 

---

# 🦺 Safety Architecture 🦺

* In accordance with ISO 13850, the autonomous forklift possesses multiple seriesed emergency stops that is easily identifiable and actuated through the use of a red mushroom style button that is mechanically latched and twist released around the chassis of the vehicle which ensures both redundancy, ease of access and operation. Apart from this, the machine will follow a category 1 stop in order for a safe shutdown procedure to occur such as a graceful speed braking for the machine as well as engaging mechanical stops that will be discussed later which thereafter follows the de-energizing of the machine as a whole.

* In accordance with ISO 3691-4:2023, the autonomous forklift will enter a protective stop, a state in which is similar to a category 2 stop whereas the vehicle can is stopped  if:
    * <ins>Loss of Power:</ins> A protective stop will occur once power is lost through the use of normally engaged mechanical brakes on springs that are disengaged through the use of electromagnetic actuators and are placed along the vehicle’s wheels and lift.
    * <ins>Loss of Communication:</ins> If communication is lost from the control and monitoring center for a set duration, the vehicle will enter a protective stop until a connection is reestablished.
    * <ins>Sensor Obstruction:</ins> If any of the sensors are obstructed at any point of the vehicle’s operation, the machine will enter a protective stop until the obstruction is cleared.

* In accordance with ISO 10218-1, ISO 10218-2, and ISO 3691-4, SAFR-2000 incorporates multiple physical safeguards and operational limits to prevent hazardous motion and ensure safe interaction with personnel and warehouse infrastructure. The vehicle operates only within predefined virtual operating zones through mapped navigation, intelligent fleet management, and virtual geofencing which prevents unauthorized entry in restricted or personnel-exclusive areas. To maintain vehicle stability and prevent mechanical failure or tip-over incidents, the smart forklift executes software-defined operational limits. Furthermore, all moving mechanical assemblies like the lifting mechanism, transmission components, as well as electrical compartments are enclosed or shielded with appropriate protective guarding to minimize accidental contact during operation and maintenance while maintaining adequate clearance around pinch points and crush zones. In addition, safety-rated LiDAR sensors continuously monitor designated protective fields surrounding the vehicle, automatically reducing travel speed or preventing motion whenever personnel or obstacles enter predefined warning or safety zones to also complement such measures. These physical constraints and safeguarding mechanisms complement the emergency stop and protective stop architectures by preventing unsafe operating conditions before they develop into hazardous events.


---

# 🗺 Standards Mapping 🗺

## Mapped Standard 1: ISO 10218-1 and ISO 10218-1: Industrial Robot Safety Requirements and Robot Systems and Integration
  **How we comply:** The Smart Forklift complies with the said standards by incorporating LiDAR sensors and obstacle detection systems to continuously detect people, objects, and other potential hazards within its operating environment like its line-of-path, making collision risks during autonomous operation decreased. Furthermore, it is equipped with emergency stop and protective stop functions are installed which automatically halts the forklift whenever unsafe operating conditions or unexpected obstacles are detected, which ensures the safety of nearby personnel and equipment. The forklift is also integrated properly into warehouse operations through predefined navigation maps, intelligent fleet management, and designated travel routes allowing coordinated, reliable, and safe interaction with other autonomous robots, warehouse equipment, and human workers. 



## Mapped Standard 2: ISO 45000 Family: Occupational Health and Safety
  **How we comply:** SAFR-2000 complies with ISO 45000 family by minimizing the need for manual material handling as well as conventional forklift operation which reduces workers’ exposure to relative injuries, repetitive tasks, and vehicle-related accidents. With its collision avoidance, pedestrian or personnel detection, automatic speed control, and safe stopping (with fault notification), accidents are prevented in shared warehouse environments which protects both operators and nearby personnel. Additionally, a Human-Machine Interface enables authorized personnel to safely monitor the forklift’s operating status, perform diagnostics, modify operational parameters, and configure system settings, improving maintenance efficiency while supporting safe and reliable operation.  


## Mapped Standard 3: ISO 31000: Risk Management
  **How we comply:** During the design, deployment, and operation of the system, potential operational risks like collisions, navigation errors, dropped loads, and battery-related failures are identified and assessed. To minimize such risks, the forklift has obstacle avoidance, load stability monitoring, intelligent route replanning, and emergency stopping to reduce the probability and severity of operational hazards. In addition, its IoT connectivity and intelligent fleet management system allows real-time monitoring, remote diagnostics, predictive maintenance, and performance analysis, allowing risks to be continuously evaluated, managed, and mitigated throughout the forklift's operational life while supporting continuous system improvement. 



## Mapped Standard 4: ISO/IEC 27001: Information Security Management
  **How we comply:** The Smart Autonomous Forklift utilizes IoT connectivity and fleet management software to communicate operational data and coordinate warehouse activities. To protect these systems, secure communication protocols, authenticated user access, and controlled data management are implemented to help maintain the confidentiality, integrity, and availability of operational information while reducing the risk of unauthorized access or cyber threats.

---











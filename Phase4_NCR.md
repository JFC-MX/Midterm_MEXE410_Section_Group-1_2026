# **📄 NON-CONFORMANCE REPORT 📄**

This report presents the non-conformances identified by the auditors during the live assessment of the **SAFR-2000 Smart Autonomous Forklift Robot**. The findings were based on the innovators' responses during their project defense and the technical justifications they provided for their design decisions.

---

# **🚩 Standards Non-Conformances**

---

## **Non-Conformance #1**

### **Dependence on External Communication for Safe Autonomous Operation**

**Applicable Standard:**

**ISO 3691-4: Driverless Industrial Trucks and Their Systems**

**Evidence from the Defense**

During the defense, the innovators explained that whenever communication with the monitoring station is lost, the autonomous forklift immediately performs a protective stop because monitoring personnel can no longer receive telemetry or monitor the vehicle's status. While this approach prioritizes safety, it also suggests that continuous communication is treated as a requirement for safe operation rather than relying primarily on onboard autonomous sensing and decision-making. The documentation did not clearly explain how the vehicle could safely continue or transition to a safe state using only its onboard perception and control systems during temporary communication loss.

---

## **Non-Conformance #2**

### **Insufficient Validation of Sensor Data Integrity**

**Applicable Standard:**

**ISO 13849-1: Safety-Related Parts of Control Systems**

**Evidence from the Defense**

During the defense, the innovators explained that multiple LiDAR sensors and depth cameras provide redundancy and continuously receive real-time information. However, they did not explain how the system determines whether a sensor is providing incorrect or corrupted data instead of simply failing completely. No detailed discussion was provided regarding sensor validation, cross-checking, sensor fusion fault detection, or decision-making when conflicting sensor information is received. As a result, the robustness of the perception system under abnormal sensor conditions was not sufficiently demonstrated.

---

## **Non-Conformance #3**

### **Limited Engineering Justification for Multiple LiDAR Architecture**

**Applicable Standard:**

**ISO 12100: Safety of Machinery – Risk Assessment and Risk Reduction**

**Evidence from the Defense**

The innovators justified the use of multiple LiDAR sensors primarily through redundancy and protective stopping capability. However, they did not provide engineering analysis comparing this configuration with the use of a single 360-degree LiDAR sensor. Factors such as computational workload, synchronization, calibration complexity, battery consumption, and real-time processing performance were not discussed. Consequently, the necessity of the selected sensor architecture was not fully supported by engineering analysis.

---

## **Non-Conformance #4**

### **Mechanical Stability Not Fully Justified During Control System Failure**

**Applicable Standard:**

**ISO 3691-4: Driverless Industrial Trucks and Their Systems**

**Evidence from the Defense**

During questioning, the innovators stated that software-defined operational limits and protective stopping prevent vehicle tip-over during abnormal conditions. They also mentioned the presence of a spring-loaded braking system. However, the explanation focused primarily on software intervention rather than the mechanical features that physically maintain vehicle stability. The relationship between the vehicle's center of gravity, chassis design, load distribution, and braking system was not clearly explained, making the mechanical justification for stability during controller failure incomplete.

---

## **Non-Conformance #5**

### **Incomplete Validation of Braking Performance Under Maximum Payload**

**Applicable Standard:**

**ISO 3691-4: Driverless Industrial Trucks and Their Systems**

**Evidence from the Defense**

The innovators stated that the forklift's safe stopping distance was determined to be approximately two meters using the maximum operating speed of 1.5 m/s and a typical coefficient of friction. However, no supporting engineering calculations, braking force analysis, deceleration calculations, safety factors, simulations, or experimental validation were presented to demonstrate that the braking system can consistently maintain safe stopping performance while carrying the maximum rated payload of 2,000 kg.

---

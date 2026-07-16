# Phase2_Audit_Checklist

## MEXE410 – Conformity Assessment and International Compliance Standards

**Phase:** 2 – Audit Documentation

**Auditing Group:** *Group 9*

**Audited Group:** *Group 1*

**Audited Project:** **SAFR-2000 – Smart Autonomous Forklift Robot**

**Audit Date:** *July 16, 2026*

---

# Audit Objective

The objective of this audit was to evaluate the technical design, engineering justifications, safety architecture, and compliance considerations of the SAFR-2000 Smart Autonomous Forklift Robot. The audit focused on determining whether the design decisions were technically justified, adequately documented, and consistent with accepted engineering practices and international standards.

---

# Audit Findings

---

## Finding 1 – Software-Based Stability

### Audit Question

> **You claim that software-defined operational limits prevent tip-over and maintain stability. Software cannot generate stability; it only sends commands. If the software miscalculates, freezes, or experiences excessive latency, what physically prevents a 2,000 kg forklift from tipping over?**

### Auditee's Response (Summary)

The group explained that high latency or communication loss activates a protective stop. The forklift is equipped with a mechanical spring-loaded braking system that physically stops the vehicle during abnormal conditions.

### Auditor's Assessment

The response correctly identified the protective stop mechanism and the fail-safe braking system. However, it did not clearly explain that vehicle stability is fundamentally determined by mechanical design rather than software.

Software can only enforce operational limits by preventing unsafe commands. The physical stability of the forklift depends on factors such as its center of gravity, chassis geometry, wheelbase, load distribution, and braking system.

### Recommendation

Future documentation should clearly distinguish between:

- Mechanical stability
- Software control
- Functional safety

The report should emphasize that software supports safe operation, while mechanical design provides the actual physical stability.

---

## Finding 2 – Multiple LiDAR Architecture

### Audit Question

> **Why did you select multiple LiDAR sensors instead of a single 360° LiDAR? Considering the increased computational workload, synchronization, calibration complexity, and battery consumption, what engineering analysis demonstrates that this architecture is necessary and does not compromise real-time safety performance?**

### Auditee's Response (Summary)

The group explained that multiple LiDAR sensors provide redundancy. If one sensor fails, the remaining sensors continue monitoring the environment, and the controller initiates a protective stop whenever a critical sensor fault is detected.

### Auditor's Assessment

The redundancy explanation is technically valid. However, the response did not explain why multiple sensors were selected over a single 360° LiDAR, nor did it discuss the engineering trade-offs associated with increased computational requirements.

### Recommendation

The report should include engineering justification regarding:

- Sensor redundancy
- Blind spot reduction
- Obstruction caused by the mast or carried load
- Sensor fusion
- Computational load
- Processing latency
- Battery consumption

---

## Finding 3 – Sensor Data Validation

### Audit Question

> **Your safety architecture depends heavily on LiDARs and depth cameras. If one of these sensors provides incorrect data rather than failing completely, how does the system detect that it is receiving invalid information instead of making an unsafe decision based on incorrect inputs?**

### Auditee's Response (Summary)

The group stated that multiple sensors continuously provide real-time data. If incorrect information is detected, the system activates its safety mechanisms to prevent unsafe operation.

### Auditor's Assessment

Although the response recognizes the importance of redundancy, it does not adequately explain how incorrect sensor information is identified. Having multiple sensors does not automatically validate sensor accuracy.

### Recommendation

The documentation should explain:

- Sensor fusion methodology
- Cross-validation between LiDAR and depth cameras
- Detection of conflicting sensor readings
- Decision-making process during sensor disagreement
- Conditions that trigger a protective stop

---

## Finding 4 – Communication Loss

### Audit Question

> **If the robot is autonomous, why does losing communication immediately make it unsafe? Doesn't that suggest your autonomy depends on continuous external supervision rather than onboard intelligence?**

### Auditee's Response (Summary)

The group explained that although the forklift performs its tasks autonomously, monitoring personnel continuously receive telemetry. When communication is interrupted, supervisors can no longer monitor the system, so the forklift enters a protective stop.

### Auditor's Assessment

The response correctly explains the role of supervision. However, it may unintentionally imply that autonomous operation depends on continuous communication.

### Recommendation

The documentation should clarify that:

- Navigation and obstacle avoidance are performed onboard.
- Communication supports fleet management, monitoring, and diagnostics.
- The protective stop following communication loss is a conservative safety policy rather than a navigation requirement.

---

## Finding 5 – Braking Performance Validation

### Audit Question

> **You claim a payload capacity of 2,000 kg while stating that the vehicle operates safely alongside human workers. What engineering calculations or validation demonstrate that the braking system, stopping distance, and stability remain within safe limits under maximum payload and maximum speed?**

### Auditee's Response (Summary)

The group explained that using the maximum operating speed of **1.5 m/s** and a typical tire-to-floor coefficient of friction, the safe stopping distance was calculated to be approximately **2 meters**.

### Auditor's Assessment

The response demonstrates that engineering calculations were considered. However, the assumptions and methodology were not sufficiently explained to fully validate the claimed stopping performance.

### Recommendation

The report should include:

- Braking equations
- Assumed coefficient of friction
- Deceleration calculations
- Safety factor
- Simulation or experimental validation
- References to applicable engineering standards

---

# General Observations

## Strengths

- Well-organized project documentation.
- Good selection of safety-related technologies.
- Appropriate use of LiDAR-based obstacle detection.
- Inclusion of fail-safe braking and protective stopping.
- Consideration of international safety standards.
- Good understanding of autonomous warehouse operation.

## Opportunities for Improvement

The audit identified opportunities to strengthen the technical documentation by providing:

- More detailed engineering justifications.
- Design trade-off analysis.
- Supporting calculations.
- Validation methods.
- Risk analysis for sensor faults.
- Additional references to engineering standards.

Providing stronger technical evidence would improve the overall credibility of the project during future engineering reviews.

---

# Overall Assessment

The SAFR-2000 Smart Autonomous Forklift Robot demonstrates a technically sound conceptual design with strong consideration for automation and safety. The project reflects a good understanding of autonomous material handling systems and incorporates several important functional safety features.

While the overall concept is well developed, several engineering decisions require deeper technical justification and supporting calculations. Expanding these areas would strengthen both the project's conformity assessment and its technical defensibility.

# Root Cause Analysis

## Project

Arduino-Based Heart Sound Acquisition System

## Selected QA Problem

### Sampling Configuration Requires Verification

The heart sound acquisition system uses Timer1-based interrupt sampling to control the timing of analog signal acquisition. The sampling configuration is therefore an important parameter that requires systematic verification and documentation.

---

## 5-Why Analysis

### Why 1 - Why does the sampling configuration require verification?

Because the system depends on Timer1 for periodic acquisition of the analog heart sound signal.

### Why 2 - Why is Timer1 important?

The analog signal acquisition is performed inside the Timer1 compare interrupt, which determines when the ADC sampling operation takes place.

### Why 3 - Why can an incorrect Timer1 configuration be a problem?

An incorrect timer configuration can result in an unintended sampling interval and therefore affect the timing of acquired samples.

### Why 4 - Why is the sampling interval important?

The acquired heart sound signal depends on appropriate sampling of the analog input. An unsuitable sampling configuration can affect the representation of the acquired signal.

### Why 5 - Why should the sampling configuration be documented and verified?

Documented verification provides traceability between the intended acquisition configuration and the implementation in the Arduino source code.

---

## Root Cause

The sampling configuration did not previously have a dedicated documented QA verification procedure.

---

## Corrective Action

A dedicated sampling-configuration test case was added to the QA test plan.

The relevant Timer1 configuration and acquisition logic were reviewed in the source code.

Physical measurement of the actual sampling rate remains pending because the physical heart sound acquisition hardware is currently unavailable.

---

## Verification Status

### Software Verification

The Timer1 configuration and acquisition logic were reviewed through source-code analysis.

### Hardware Verification

Physical verification using the actual Arduino and heart sound sensor is pending until the hardware setup becomes available.

---

## Evidence

The analysis is supported by:

- Arduino source code
- Timer1 configuration in the source code
- Existing heart sound acquisition project documentation
- QA test plan
- QA test results

---

## QA Lesson

The analysis demonstrates the importance of documenting critical timing parameters and maintaining traceability between software implementation, expected behavior and physical validation.

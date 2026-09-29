# QA Test Results

## Project

Arduino-Based Heart Sound Acquisition System

## Test Results

| Test ID | Test | Expected Result | Evidence | Status |
|---|---|---|---|---|
| T01 | Analog signal acquisition | Samples are acquired from analog input A0 | Source code and existing project readings | Observed |
| T02 | Sampling configuration | Timer1 configuration supports the intended acquisition process | Source-code analysis | Verified by Code Analysis |
| T03 | Serial communication | Acquired data is transmitted through USB serial communication | Existing Spike Recorder evidence | Observed |
| T04 | Signal quality | Heart sound waveform is observable and suitable for analysis | Existing waveform/readings | Observed |
| T05 | Circular buffer | Head and tail mechanism manages the sampling buffer | Source-code analysis | Verified by Code Analysis |
| T06 | Channel configuration | Channel configuration produces the intended acquisition behavior | Source-code analysis | Pending Hardware Verification |
| T07 | Command processing | Serial commands are interpreted according to the implemented logic | Source-code analysis | Pending Hardware Verification |

## Evidence Classification

### Observed

These results are supported by previously available experimental data, readings, waveforms or screenshots from the heart sound acquisition project.

### Verified by Code Analysis

These results are based on inspection of the Arduino source code and its implementation.

### Pending Hardware Verification

These tests require the physical heart sound sensor and Arduino acquisition setup. They are not represented as newly performed tests because the physical hardware is currently unavailable.

## QA Observation

The existing source code provides the main acquisition functions including analog sampling, Timer1-based timing, circular buffering and serial transmission. The QA process identifies these functions as important verification points for reliable heart sound signal acquisition.

## Validation Limitation

Physical re-testing of the complete acquisition chain is pending until the original hardware setup becomes available.

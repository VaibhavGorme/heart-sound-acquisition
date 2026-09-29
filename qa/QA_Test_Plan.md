# QA Test Plan

## Project

Arduino-Based Heart Sound Acquisition System

## Purpose

The purpose of this QA test plan is to verify the important functional and software aspects of the Arduino-based heart sound acquisition system.

## Test Areas

### T01 - Analog Signal Acquisition

Verify that the system acquires the analog heart sound signal through analog input A0.

### T02 - Sampling Configuration

Verify the Timer1 configuration used for periodic signal acquisition.

### T03 - Serial Communication

Verify the transmission of sampled data through USB serial communication to the receiving software.

### T04 - Signal Quality

Review the acquired heart sound waveform and previously recorded readings to evaluate signal quality.

### T05 - Circular Buffer

Review the head and tail mechanism used for continuous sample buffering.

### T06 - Channel Configuration

Review the behavior associated with the number of configured analog channels.

### T07 - Command Processing

Review the serial command-processing mechanism used by the acquisition software.

## Evidence Classification

### Observed

Results supported by existing experimental data, readings or screenshots.

### Verified by Code Analysis

Results supported by inspection of the source code.

### Pending Hardware Verification

Tests that require access to the physical heart sound acquisition setup and cannot be newly performed while the hardware is unavailable.

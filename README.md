# Arduino-Based Heart Sound Acquisition System

## Project Overview

This project focuses on the acquisition of heart sound signals using an Arduino-based data acquisition system. The analog signal from the heart sound sensor is acquired through an analog input and processed using timer-controlled sampling.

The acquired samples are stored in a circular buffer and transmitted through USB serial communication to Spike Recorder for visualization and recording.

## Objectives

- Acquire analog heart sound signals.
- Perform timer-based signal sampling.
- Store sampled data using a circular buffer.
- Transmit acquired data through USB serial communication.
- Visualize the acquired signal using Spike Recorder.
- Apply GitHub-based QA documentation and problem-solving practices.

## Hardware

- Arduino-based acquisition board
- Heart sound sensor
- Stethoscope/sensor interface
- USB connection
- Computer

## Software

- Arduino IDE
- Arduino C/C++
- Spike Recorder
- GitHub

## Signal Acquisition

The heart sound sensor produces an analog signal that is connected to the analog input A0 of the Arduino.

The Arduino samples the signal using a Timer1-based interrupt mechanism. The acquired samples are placed into a circular buffer and transmitted through the serial interface.

## Communication

The system uses USB serial communication between the Arduino and the computer.

The current source code configures the serial communication at 230400 baud.

## QA Approach

The project uses GitHub Issues, commits, branches and documentation to track QA observations, analyze potential problems and document corrective actions.

## Project Status

Baseline source code uploaded.

QA analysis and documentation are in progress.

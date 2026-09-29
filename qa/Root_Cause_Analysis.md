# Root Cause Analysis

## Project

Arduino-Based Heart Sound Acquisition System

## Physical Measurement Evidence

Previously recorded heart-sound WAV files from the acquisition system were analyzed as experimental evidence.

The recordings were found to have a sampling rate of 10,000 Hz and a single audio channel.

| Recording | Sampling Rate | Channels | Duration (s) | Samples | RMS | Peak | Peak-to-Peak |
|---|---:|---:|---:|---:|---:|---:|---:|
| BYB_Recording_2026-04-10_14.27.08.wav | 10000 Hz | 1 | 61.6592 | 616592 | 0.01657 | 0.21402 | 0.29166 |
| BYB_Recording_2026-04-10_14.26.17.wav | 10000 Hz | 1 | 48.9392 | 489392 | 0.01983 | 0.25992 | 0.35449 |
| BYB_Recording_2026-04-10_14.26.09.wav | 10000 Hz | 1 | 3.3696 | 33696 | 0.01828 | 0.15582 | 0.21259 |
| BYB_Recording_2026-04-10_11.19.10.wav | 10000 Hz | 1 | 22.4048 | 224048 | 0.00958 | 0.15671 | 0.20093 |
| Additional WAV recording | 10000 Hz | 1 | 26.8288 | 268288 | 0.01679 | 0.21500 | 0.27060 |

The amplitude values represent normalized digital sample amplitudes from the WAV recordings. They are not directly interpreted as volts or dB SPL because no voltage or acoustic calibration reference was available.

## Selected QA Problem

### Sampling Configuration Verification

The heart sound acquisition system uses Timer1-based interrupt sampling to control the timing of analog signal acquisition.

The Arduino source code specifies a configuration intended for 10 kHz single-channel sampling.

## Measurement-Based Verification

The previously recorded WAV files were inspected using their actual audio metadata.

All five recordings have a sampling frequency of:

**10,000 Hz**

The recordings are also single-channel recordings.

This provides experimental evidence that the recorded data was acquired/stored at a 10 kHz sampling rate.

For example:

- 61.6592 seconds × 10,000 samples/second = 616,592 samples
- 48.9392 seconds × 10,000 samples/second = 489,392 samples
- 3.3696 seconds × 10,000 samples/second = 33,696 samples

The calculated sample counts exactly correspond to the recorded WAV files.

## 5-Why Analysis

### Why 1 - Why does the sampling configuration require verification?

Because the system depends on Timer1 for periodic acquisition of the analog heart sound signal.

### Why 2 - Why is Timer1 important?

The analog signal acquisition is performed inside the Timer1 compare interrupt, which determines when the ADC sampling operation takes place.

### Why 3 - Why can an incorrect Timer1 configuration be a problem?

An incorrect timer configuration can result in an unintended sampling interval and therefore affect the timing of acquired samples.

### Why 4 - Why is the sampling interval important?

The recorded heart sound signal depends on regular sampling of the analog input. The sampling frequency determines the time interval between consecutive samples.

### Why 5 - Why should the sampling configuration be documented and verified?

Documented verification provides traceability between the intended acquisition configuration and the recorded experimental data.

## Root Cause

The sampling configuration required explicit verification against the recorded experimental data.

## Corrective Action

The sampling configuration was added as a dedicated QA test case.

The Arduino source code was reviewed and the previously recorded WAV files were analyzed.

The WAV recordings consistently show a 10 kHz sampling rate, providing experimental evidence consistent with the intended single-channel acquisition configuration.

## Verification Status

### Software Verification

The Timer1 configuration and ADC acquisition logic were reviewed through source-code analysis.

### Experimental Verification

Previously recorded physical measurements were analyzed from the WAV files.

All analyzed recordings have:

- 10 kHz sampling frequency
- One channel
- Recorded sample counts consistent with their durations

Therefore, the sampling-rate configuration is supported by both source-code analysis and recorded experimental data.

## Evidence

The analysis is supported by:

- Arduino source code
- Previously recorded heart-sound WAV files
- Existing Spike Recorder acquisition workflow
- QA test plan
- QA test results

## Limitation

The WAV amplitude values are digital sample amplitudes. No calibration reference was available to convert these values into absolute voltage or sound-pressure level (dB SPL).

## QA Lesson

The analysis demonstrates the importance of correlating software configuration with actual experimental data. Reviewing both the source code and recorded WAV metadata provides stronger traceability than relying only on code inspection.

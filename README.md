# Heartbeat and Breath Sound Separation Using DSP

## Project Overview

This project demonstrates real-time Digital Signal Processing (DSP) to distinguish and analyze heartbeat and breath sounds from a physiological signal. Developed using Texas Instruments' Code Composer Studio (CCS) and TI-RTOS, this project leverages efficient DSP algorithms running on a TI C674x DSP processor.

## Objectives

- Separate and analyze heartbeat and breath sounds from a combined physiological signal.
- Implement real-time signal sampling and processing.
- Visualize the processed signals, FFT magnitude, and energy envelopes.
- Count heartbeats and breaths accurately within given sample buffers.

## Project Specifications

- **Sampling Frequency:** 2000 Hz
- **Buffer Size:** 4405 samples
- **Filters:**
  - **Notch Filter (IIR):** Removes noise at 250 Hz.
  - **Heartbeat Detection:** IIR Elliptic Lowpass Filter (below 135 Hz).
  - **Breath Sound Detection:** IIR Elliptic Highpass Filter (>135 Hz).

### Tools & Technologies Used

- **Development Environment:** Code Composer Studio (CCSv11)
- **DSP Hardware:** Texas Instruments C674x DSP on OMAP-L138
- **RTOS:** TI-RTOS (SYS/BIOS)
- **Filter Design Software:** MATLAB (Filter Designer)

## Implementation Details

The program is structured to leverage real-time multitasking capabilities of TI-RTOS, utilizing:

- **Timer ISR (HWI):** Periodically samples the physiological input signal.
- **Software Interrupt (SWI):** Handles real-time sample fetching and synchronization.
- **Semaphore:** Manages synchronization between interrupt service routines and processing tasks.
- **Tasks:** Core DSP operations executed to separate and analyze signals.

## Flow of Operations

1. **Sampling:** Timer ISR initiates periodic sampling at 2000 Hz.
2. **Filtering:**
   - Notch filter removes unwanted frequency noise.
   - Low-pass filter isolates heartbeat signals.
   - Highpass filter isolates breath sounds.
3. **Envelope & Energy Calculation:** Calculates energy and smoothed envelopes for both signals.
4. **Signal Counting:** Uses sliding-window analysis to count heartbeats and breaths within each buffer.
5. **Visualization:** Displays FFT magnitude, signal envelopes, energy graphs, and real-time processing load.

## Results & Visualizations

- **Signal Separation:** Clear separation and identification of heartbeat and breath signals.
- **FFT Analysis:** Graphical representation before and after filtering.

### Screenshots
- **Notch Filtering:** ![image](https://github.com/user-attachments/assets/c1b69c1c-8e82-48a7-bd94-33c08ca01a80)
- **Breath sound Filtering:** ![image](https://github.com/user-attachments/assets/b6c01d14-d124-45b7-b660-797c2067a513)
- **Heartbeat Filtering:** ![image](https://github.com/user-attachments/assets/4c21ae65-7356-4dad-81bb-46e6e5a9ea77)

- **Envelope Analysis:** Accurate detection of signal peaks using envelope smoothing techniques.
- **Performance Metrics:** Execution graph, task load, and CPU utilization clearly indicating real-time performance.
  
## Comprehensive Documentation
For detailed insights, theoretical background, design considerations, complete methodology, results, and graphs, refer to the comprehensive project documentation:
[Comprehensive Documentation](docs/DSP-Heartbeat-VS-Breath-Sound-Analysis.pdf)

## Repository Structure

```
DSP-Heartbeat-Breath
├── docs/
│   └── DSP-Heartbeat-VS-Breath-Sound-Analysis.pdf
├── src/
│   ├── Heartbeat_VS_BreathSound_FinalProject.zip
└── README.md
```

## Authors
- **Francis Aboud**
- **Bshara Habib**

## Supervisor
- **Itzhak Kroin**

## Course
Programming DSP Processors, Department of Electrical and Electronic Engineering, Braude College of Engineering

## Future Enhancements
- Optimize processing speed through code refactoring.
- Implement adaptive filtering for dynamic real-world data.
- Integration of machine learning algorithms for improved signal classification.

## Setup Instructions
- Clone or download this repository.
- Open **Code Composer Studio**.
- Select ```File -> Import... -> CCS``` Projects, then click **Next**.
- Choose **Select archive file** and import:
- ```DSP-Heartbeat-Breath/src/Heartbeat_VS_BreathSound_FinalProject.ZIP```
- Click **Finish** to import.
- Build the project via ```Project -> Build Project```.
- Debug and run on the connected DSP hardware.
  

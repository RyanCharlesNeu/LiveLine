## LiveLine 
**Real-Time Power-Line Fault Monitoring System**
<br>
**INNOVATE: L3Harris Endowed Summer Program**
<br>
**Role: Systems Engineering Lead & Team Lead**

<!-- HERO IMAGE: full device/enclosure photo -->
<img src="assets/IMG_1242.jpg" width="40%" />

## Overview

Power line failures leaves roughly 34 million households without power and costs the U.S. economy an estimated $150 billion every year, and outages are getting more frequent and lasting longer as the grid ages. While many outages are sudden, such as lightning strikes or large trees falling on a line, many failure modes could be prevented if utility companies had access to live data on the line. When a line does fail, it can cut power to homes and hospitals, disable traffic systems, and in dry conditions, spark a wildfire. Despite this, most power lines still aren't monitored in real time, so developing faults are usually caught only after they've already caused damage. LiveLine is a clamp-mounted sensor system that attaches directly to a power line and tracks it continuously, catching the early mechanical and thermal warning signs of a developing equipment fault before it turns into an outage or a fire.


The sections below distinguish between the **full product vision** and **what has been validated in the current prototype**, since the two are at different stages of maturity.

## System Architecture
LiveLine is designed to fuse five independent sensing modalities into a single clamp-mounted enclosure, each targeting a different fault precursor:

| Sensor | Target Signal | Component | Photo |
|---|---|---|---|
| Strain Gauge | Tension, force, sag, stress, strain | CEA-13-250UWA-350 | <img src="assets/LIVELINE2.png" width="80" /> |
| IMU | Vibration, tilt, mechanical fatigue (via Miner's Rule) | QCIOT-ICM42688P | <img src="assets/LIVELINE2 (1).png" width="80" /> |
| Temperature Sensor | Line temperature, ambient temperature | DS18B20 | <img src="assets/LIVELINE2 (2).png" width="80" /> |
| Acoustic Sensor | Acoustic fault detection | Nano 30 | <img src="assets/LIVELINE2 (3).png" width="80" /> |
| Current Sensor | Current detection | SCT-013 | <img src="assets/LIVELINE2 (4).png" width="80" /> |

## CAD & Enclosure

The clamp and enclosure were designed in SolidWorks and 3D printed in PLA for prototyping. The clamp uses a half-shell hinge design for ease of installation on live lines. The IMU, strain gauge, and acoustic sensor are mounted directly on the clamp body, while the current and temperature sensors are housed within the PLA enclosure.


<img src="assets/LIVELINE2 (6).png" width="55%" /> <img src="assets/LIVELINE2 (7).png" width="39%" />

*CAD design (left) and the printed PLA enclosure (right).*

<img src="assets/IMG_1275.jpeg" width="50%" />

*Multiple printed prototypes, show casing rapid prototyping and design iteration process.*

## Circuit Diagram


<img src="assets/Screenshot 2026-08-06 204953.png" width="80%" />

*Circuit diagram of the sensor electronics. This diagram covers the core sensor wiring; the  strain gauge (mounted on the clamp body) are not pictured.*


## Live Data Dashboard

The target product includes a live dashboard showing real-time sensor data, current line status, and a predicted failure mode based on sensor readings. The mockup below is running on simulated data to demonstrate the intended interface; it is not yet connected to live sensor output.

<img src="assets/LIVELINE2 (8).png" width="80%" />

*Dashboard mockup showing live data view, line status, and failure mode prediction, running on simulated data.*


## Prototype Validation

### Vibration (IMU)

Verified functional.

**Vibration / IMU demo:**


https://github.com/user-attachments/assets/1eeec7b4-399e-44b4-9e49-9601d9c09212



<br>

### Current & Temperature

The current sensor was verified functional, confirmed accurate within a 10% margin in testing against a hot pot load monitored on a watt meter. The temperature sensor was validated in the same test, showing a measurable rise in line temperature that tracked with the increase in current draw.

<img src="assets/Screenshot 2026-08-06 231237.png" width="100%" />

*Current sensor test setup: hot pot plugged into a watt meter for a known reference reading, compared against the sensor's live output. Line temperature rose in step with current draw, validating the temperature sensor alongside it.*

<br>

### Acoustics (Nano 30)

Verified functional. Validated using a Hsu-Nielsen pencil break test (a standard method for generating a controlled acoustic emission event), which produced a clear, detectable signal on the oscilloscope. Further characterization of real fault signatures is limited by the sensor's high sensitivity, which is being addressed in the next testing round.

<img src="assets/IMG_1261.jpg" width="55%" />

*Oscilloscope output from a Hsu-Nielsen pencil break test, showing a clear signal spike captured by the acoustic sensor.*

<br>

### Tension

The prototype demonstrated the ability to detect large tension events using a fixed-clamp test setup. This validated the sensing concept but not the final mechanical design, addressed in the next section.

**Tension sensor demo:**

https://github.com/user-attachments/assets/c27b1532-991c-4ed6-aec1-5699cf689674

## Design Iteration: Tension Sensor

The initial prototype validated tension detection using a fixed test clamp, which is not representative of how the sensor will operate in the field. The next design iteration replaces this with a **sliding-clamp mechanism**: one clamp remains fixed while the second slides freely, with a linear potentiometer mounted between the two to directly measure strain along the line as it develops. This removes the fixed-point limitation of the current prototype and is designed to reflect real in-field conditions.

<img src="assets/LIVELINE2 (5).png" width="60%" />

## Status

LiveLine is an ongoing project. The prototype phase, completed as part of the L3Harris INNOVATE Program, validated core sensing concepts across four of five planned sensor modalities. The current enclosure and clamp are a functional prototype, not a field-ready design, the aluminum clamp is electrically conductive, and the enclosure has no shielding or weatherproofing yet. The design changes needed to close that gap are detailed below.

## Future Work

- **High-quality plastic clamp** — replace the current aluminum clamp with a non-conductive plastic that still transmits vibration accurately to the IMU and acoustic sensor
- **EMF shielding** — protect sensor electronics from electromagnetic interference near energized lines
- **IP68 weatherproofing** — move from PLA prototype to a fully sealed, weather-rated polycarbonate enclosure for extended outdoor deployment
- **Sliding-clamp tension sensor** — build and validate the potentiometer-based design described above
- **Solar power** — enable long-duration, unattended field deployment without battery replacement
- **Satellite communication** — support remote data transmission from field sites without relying on local network infrastructure
- **AI alert prediction** — move from raw sensor logging toward a model that predicts failure mode and timing from live sensor data
- **Acoustic sensor characterization** — resolve signal-handling limitations to fully validate acoustic fault detection
- **Field validation** of the complete sensor suite against real fault conditions



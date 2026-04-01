# Sensor Fusion - Self Study (Udacity Curriculum)

## About Me

**ADAS Software Integration & Validation Engineer | 8 Years | BMW ADAS Supply Chain**

I spent 8 years at KPIT Technologies GmbH as an ECU Software Integration and Validation Engineer, working directly in the BMW ADAS supply chain between BMW and Tier 1 suppliers to integrate, build, and validate ADAS ECU software.

### What I did at KPIT

- Integrated software components from Tier 1 suppliers and BMW into flashable ECU binaries
- Owned CI/CD pipelines for **6 BMW ADAS ECUs** across 12 vehicle models and 8 software releases
- Validated integrated ECU software on **dSPACE HIL**: flashing, calibration, diagnostics, feature testing, error injection
- Improved build success rate from **73% to 94%** with zero field deployment errors
- Automated requirements traceability for **Audi/Mobileye** project: 2,500+ requirements at 99.8% traceability

### Tools I used professionally

|Area |Tools |
|-------------------|-----------------------|
|HIL Simulation |dSPACE ControlDesk |
|Calibration |CANape (XCP) |
|Test Execution |ECU-TEST |
|Runtime Measurement|Gliwa T1 |
|CI/CD |Jenkins, GitHub Actions|
|Artefact Management|JFrog Artifactory |
|Build Compilers |Tasking, Green Hills |
|Scripting |Python, Bash |
|Requirements |Codebeamer, ReqIF |

## Why I Am Learning Sensor Fusion

For 8 years I validated **outputs** of the ADAS perception stack, did AEB trigger correctly, did ACC maintain the right distance, did the feature behave as expected after integration.

The sensor fusion stack was always inside the ECU producing those outputs. I validated what came out. I never looked inside.

I am now learning the internals, how LiDAR point clouds are processed, how RADAR Doppler measurements work, how camera detections are fused, how Kalman Filters track objects across sensor inputs.

The goal is not to become a perception developer. The goal is to become a validation engineer who understands the full stack from raw sensor input to ECU output and can design better tests, identify root causes faster, and speak credibly across the perception and integration boundary. I tested the results of fusion for 8 years. I am now learning how fusion works.

## Course Progress

|Module |Status |Project |
|-----------------|-------------|----------------------------------------------------------|
|**LiDAR** |🔄 In Progress|Obstacle Detection — 3D bounding boxes from point cloud |
|**RADAR** |⬜ Upcoming |Object Detection — Doppler, FFT, clustering |
|**Camera** |⬜ Upcoming |Feature Tracking — keypoint detection, descriptor matching|
|**Kalman Filter**|⬜ Upcoming |Sensor Fusion — EKF/UKF combining RADAR and Camera |

## Module 1 — LiDAR

**Concepts covered:**
- Point cloud structure - X, Y, Z, Intensity
- PCL (Point Cloud Library) for processing
- Voxel Grid filtering - downsampling raw point cloud
- RANSAC — ground plane segmentation
- Euclidean Clustering - grouping points into objects
- 3D Bounding Box generation

**Why this matters for validation:**
In HIL testing, LiDAR sensor models feed simulated point clouds into the ADAS ECU. Understanding point cloud processing helps design smarter test scenarios - sparse point clouds, ground plane ambiguity, object occlusion — edge cases that black box testing misses.

**Tools:** C++, PCL Library, CMake, Ubuntu

## Certification
ISTQB Certified Tester — Foundation Level (CTFL)

## Connect
[LinkedIn](https://www.linkedin.com/in/lavanya-penumaka/)

Image Asset Mapping & Placement Guide
Label
Source File
Figure Title
Target Section in README
1<img width="690" height="416" alt="image" src="https://github.com/user-attachments/assets/396aa8d7-985f-4d31-be64-d79f8ed4eca9" />
Raw Aerial Harbour Baseline
Introduction / Header
2<img width="1024" height="362" alt="image" src="https://github.com/user-attachments/assets/75d832f2-974d-4d6d-9ce0-10ee2973da68" />
Original vs. OBB Detections (229)
Analytics  Aerial Detection Performance
3<img width="1990" height="985" alt="image" src="https://github.com/user-attachments/assets/5bf3b197-0738-479b-ae7e-6fc3fa51b820" />
High-Density OBB Annotations (238)
Analytics  High-Density OBB Annotations
4<img width="1590" height="495" alt="image" src="https://github.com/user-attachments/assets/5bff145f-56ee-4171-ad56-615379398cde" />
OBB Detection Statistics Dashboard
Analytics  Spatial Area Savings Dashboard
5<img width="1282" height="495" alt="image" src="https://github.com/user-attachments/assets/1a6c6d42-9111-4b71-b18c-5a8ab3b87be4" />
OBB Savings — Diagonal Ship Clusters
Analytics  Rotation Angle Optimization
6<img width="1589" height="495" alt="image" src="https://github.com/user-attachments/assets/4f30abb1-cc97-4599-905b-e98002c33079" />
OBB Saving vs Rotation Angle
Analytics  Rotation Angle Optimization
7<img width="989" height="587" alt="image" src="https://github.com/user-attachments/assets/abe67478-bcfd-4eae-93ee-5844abc0632f" />





Rotation Angle Analysis (Polar)
Analytics  Rotation Angle Optimization


Technical Projects

An advanced computer vision repository focused on aerospace defense and tactical situational awareness. This project implements core capabilities designed for edge deployment in high-stakes environments: a robust aerial Deep Learning architecture for object detection/classification, a neuromorphic event-based pipeline for high-speed counter-Unmanned Aerial Systems (c-UAS), and a comprehensive simulation framework for UAV-assisted wireless communication systems.

🛠️ Project Frameworks & Core Capabilities
1. High-Resolution Aerial OBB Perception Pipeline (YOLOv8-OBB)
A mission-critical framework engineered to identify, isolate, and classify tactical assets and potential threats in real time from dynamic, top-down UAV perspectives.

Tiled Inference Engine: Implements a custom sliding-window mechanism (640px tiles, 320px stride) combined with geometric Non-Maximum Suppression (NMS) deduplication to process massive multi-megapixel aerial maps without losing small-target resolution.
Spatial Profiling & Optimization: Calculates Oriented Bounding Box (OBB) area against standard Axis-Aligned Bounding Box (AABB) area, significantly reducing wasted processing space. This delivers a 48.9% overall area saving, peaking at 54.3% for specific high-rotation targets.
Edge-Ready Export: Automatically exports PyTorch architectures to ONNX (opset=17) for TensorRT FP16 compilation, targeting a 5-10x inference speedup on edge hardware.
Tech Stack: Python, PyTorch, Ultralytics (YOLOv8-OBB), OpenCV, NumPy, Matplotlib.

2. Event-Based Vision Pipeline for High-Speed Counter-UAS
Standard frame-based cameras suffer from motion blur and latency when tracking high-velocity targets like micro-drones or low-altitude UAS. This pipeline processes asynchronous temporal event streams (neuromorphic data) to achieve microsecond-level latency and high dynamic range tracking.

Core Focus: Asynchronous pixel-level illumination change processing, ultra-low latency target tracking, and high-speed motion deblurring.
Neuromorphic Data Ingestion: Utilizes tonic.datasets to ingest DAVIS 6-DoF event data. The ArrayEventStream module dynamically chunks raw asynchronous events (X, Y, Timestamp, Polarity) into user-defined microsecond time windows (e.g., 10,000 µs) for edge-efficient batch processing.
Dynamic Time Surface (TS) Formulation: Converts sparse, asynchronous event streams into dense 2D spatial maps. It applies microsecond-level exponential decay to raw events, highlighting the leading edge of moving objects while gracefully fading older pixel activations.
Spatiotemporal Clustering & Tracking: Implements deterministic clustering utilizing scipy.ndimage. It applies dynamic thresholding to the Time Surface and uses connected-component labeling to isolate moving targets, outputting stable bounding-box regression data for object tracking.
Tech Stack: Python, OpenCV, custom spatiotemporal filtering, and specialized event-data manipulation libraries.

3. UAV-Assisted Wireless Communication Systems & Dynamic Trajectory Planning
A comprehensive Python-based simulation framework designed to model Air-to-Ground (A2G) wireless communication channels using ITU-R recommendations. This project evaluates signal propagation, optimal altitude placement, and dynamic 3D flight trajectories to maximize coverage and data throughput for multi-user ground networks in urban environments.

Line-of-Sight (LOS) Probability: Calculates deterministic and stochastic LOS/NLOS conditions based on elevation angles and environmental parameters (μa=9.61, μb=0.16).
Path Loss & Shadowing: Computes Free Space Path Loss (FSPL) alongside excessive NLOS attenuation and log-normal shadowing, dynamically reacting to the 3D spatial distance between the drone and ground users.
Signal Metrics: Accurately models Received Signal Strength (RSS) in dBm, Signal-to-Interference-plus-Noise Ratio (SINR) in dB, and utilizes the Shannon capacity formula to determine theoretical data rates.
Flight Patterns: Supports mathematically generated circular, lawnmower, spiral, straight, and stationary hover trajectories.
Time-Series Tracking: Samples the drone's position at discrete time intervals, mapping continuous RSS, SINR, and throughput metrics as the drone interacts with static or clustered ground user distributions.
Coverage Heatmapping: Generates high-resolution 2D spatial heatmaps to visually diagnose RSS drop-offs, SINR dead zones, and LOS probability across the simulated grid.
📊 Analytics & Visual Results
Aerial OBB Perception Pipeline
The aerial OBB perception pipeline includes a comprehensive analytics suite to validate spatial optimization, rotation tracking, and detection confidence.

Aerial Detection Performance:
The model successfully identifies tightly packed naval assets in complex harbor environments, detecting 238 distinct oriented objects with a mean confidence of 0.750.




High-Density OBB Annotations:


Spatial Area Savings Dashboard:
By utilizing Oriented Bounding Boxes (OBB), the pipeline reduces wasted background area by an average of 48.9% compared to traditional AABB methods.


Rotation Angle Optimization:
Deep dive analysis into specific angular clusters (e.g., ships docked diagonally at 10-30 degrees) yields an area saving of up to 54.3%, heavily optimizing downstream processing payloads by discarding irrelevant pixel data.




UAV Wireless Communication Systems
The simulator includes a robust evaluation suite that identifies critical trade-offs between UAV altitude, physical distance, and network reliability.

Static Altitude Optimization:

Optimal Placement: Analysis across an altitude range of 50m to 500m identified 250m as the optimal hovering altitude for the simulated urban environment.


Peak Performance: At 250m, the system achieved a 100% coverage probability (all users > -90 dBm) and a peak average data rate of 242.24 Mbps.


Dynamic Flight Performance (Circular Trajectory):

Network Reliability: While navigating the coverage zone at 15 m/s, the drone maintained exceptional network stability with a 99.72% connectivity uptime (only 0.28% outage time).


Throughput Delivery: The moving UAV sustained an average data rate of 176.14 Mbps per user across the network.


Signal Integrity: Maintained an average Received Signal Strength of -67.60 dBm and a strong average SINR of 26.39 dB throughout the 120-second flight duration.


Event-Based Vision Pipeline
The system includes a built-in telemetry and visualization suite to monitor event density, time-surface rendering, and clustering accuracy over time.

Live Pipeline Summary: The pipeline successfully resolves high-speed motion, transitioning from raw ON/OFF polarity events to continuous, exponentially decayed Time Surfaces. By t=500.0 ms, the clustering algorithm successfully isolates dynamic shapes, applying tight spatial bounding boxes around individual geometries despite asynchronous data.

Performance Metrics:

Temporal Resolution: 10 ms (10,000 µs) sliding windows.


Decay Tuning: 30,000 µs exponential decay profile for optimal motion-trail length.


Noise Filtering: Hardware-level refractory period simulation (500 µs) combined with spatial minimum-pixel thresholds (20px) to reject background noise.

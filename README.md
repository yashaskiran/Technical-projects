# Technical projects
Advanced computer vision systems for defense operations, featuring a neuromorphic event-based pipeline for high-speed counter-UAS tracking and a deep learning framework for robust object detection and classification.

# Computer Vision Pipelines

An advanced computer vision repository focused on aerospace defense and tactical situational awareness. This project implements two core capabilities designed for edge deployment in high-stakes environments: a neuromorphic event-based pipeline for high-speed counter-Unmanned Aerial Systems (c-UAS) and a robust deep learning architecture for object detection and classification.

---

## 🛠️ Project Frameworks

### 1. Event-Based Vision Pipeline for High-Speed Counter-UAS
Standard frame-based cameras suffer from motion blur and latency when tracking high-velocity targets like micro-drones or low-altitude UAS. This pipeline processes asynchronous temporal event streams (neuromorphic data) to achieve microsecond-level latency and high dynamic range tracking.

*   **Core Focus:** Asynchronous pixel-level illumination change processing, ultra-low latency target tracking, and high-speed motion deblurring.
*   **Key Capabilities:** Efficiently extracts spatiotemporal features of fast-moving aerial objects against complex, dynamic backgrounds (e.g., cloudy skies, clutter).
*   **Tech Stack:** Python, OpenCV, custom spatiotemporal filtering, and specialized event-data manipulation libraries.

### 2. Deep Learning Object Detection & Classification
A mission-critical framework engineered to identify, isolate, and classify tactical assets and potential threats in real time. 

*   **Core Focus:** High-precision multi-class classification utilizing deep convolutional architectures.
*   **Key Capabilities:** Optimized to balance inference speed and precision-recall metrics, minimizing false-negative rates in target identification under varied environmental conditions (lighting, occlusion, scale).
*   **Tech Stack:** Python, TensorFlow / Keras, OpenCV, scikit-image.
  <img width="1489" height="798" alt="image" src="https://github.com/user-attachments/assets/291f5c0f-45c1-4a64-ad21-10819888b8bf" />


---

## 🚀 Getting Started (Google Colab Deployment)

Both systems are optimized to run directly via Google Colaboratory leveraging hosted GPU acceleration. 

### Prerequisites
Ensure your runtime environment includes the necessary hardware accelerators:
*   **Runtime Type:** Python 3.x with GPU enabled (T4 or higher recommended).

### Running the Notebooks
1. Clone this repository directly into your Colab environment or open the notebooks via the GitHub integration.
2. Install the necessary baseline dependencies:
```bash
pip install opencv-python tensorflow keras scikit-image NumPy

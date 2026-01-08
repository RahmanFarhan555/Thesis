# Thesis
# Association of Multimodal Detections for Contour Estimation and Machine Learning Network Training

## Overview

This project focuses on estimating **3D object depth estimation using camera sensor** by leveraging **multimodal sensor fusion and cross-modal learning**. The system associates detections from **Camera, LiDAR, and RADAR** to build reliable object representations and uses **close-range 3D supervision** to enable **long-range depth estimation using only 2D bounding boxes**.

The work is motivated by challenges in autonomous driving perception, where accurate depth estimation for distant objects is critical but LiDAR data becomes sparse or unavailable.

---

## Key Contributions
- Implemented a **multimodal association framework** to match Camera, LiDAR, and RADAR detections using spatial, temporal, and azimuth-based constraints.
- Developed **monocular depth estimation** using classical **triangle similarity** as a geometric baseline.
- Designed a **cross-modal learning pipeline** that uses agreement between Camera and LiDAR at close range to supervise depth learning.
- Implemented an **Machine Learning based depth estimation model** that predicts 3D object depth for distant objects using **only 2D bounding box supervision**.
- Introduced **projection-based augmentation** to improve robustness of depth prediction across long ranges.
- Evaluated sensor reliability and effective range under **daylight, night, and adverse weather scenarios**.

---

## Methodology
1. **2D Object Detection**
   - Objects are detected from monocular images using a YOLO-based detector.
   - Outputs include bounding boxes, class labels, and confidence scores.

2. **Multimodal Association**
   - Camera detections are associated with LiDAR and RADAR tracks using:
     - Temporal alignment
     - Spatial proximity
     - Projection consistency
     - Azimuth similarity
   - Supports many-to-many associations and verification steps.

3. **Depth Estimation**
   - **Geometric approach**: Triangle similarity using camera intrinsics.
   - **Learning-based approach**: A neural network learns to map 2D box features to depth using close-range LiDAR supervision.
   - The trained Machine Learning model generalizes to **long-range objects with only 2D input**.

4. **Object Representation**
   - Fused detections are visualized using complementary color coding to indicate multi-sensor agreement.
   - Unified object contours and depth estimates are produced for downstream analysis.

---

## Model Architecture
- Backbone: CNN-based image feature extractor
- Head: MLP-based depth regression network
- Input: 2D bounding box geometry and visual features
- Output: Estimated object depth in metric space
- Training: Supervised using close-range LiDAR ground truth
- Inference: Camera-only for distant objects

---

## Dataset
- Real-world autonomous driving data
- Includes synchronized Camera images, LiDAR point clouds, and RADAR tracks
- Dataset split into training and evaluation sets
- KITTI-style annotation format used for compatibility

---

## Results
- Demonstrates improved depth estimation compared to camera-only baselines
- Shows effective generalization to distances beyond LiDAR’s reliable range
- Highlights strengths and limitations of geometric vs learning-based methods
- Validated across multiple environments:
  - Rural daylight
  - Urban snowy conditions
  - Suburban night scenes


---

## Future Work
- Extend to end-to-end multi-view training
- Incorporate uncertainty-aware depth prediction
- Improve robustness under extreme weather conditions
- Integrate temporal modeling for depth stability

---

<img width="279" height="243" alt="image" src="https://github.com/user-attachments/assets/5553744e-7f1d-4f25-a360-acafdb2363c4" />


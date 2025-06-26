# 🏃‍♂️ Multi-View Football Player Tracking – Assignment Submission

## 🎯 Objective

To identify and track football players consistently across two video streams captured from different camera angles (`broadcast.mp4` and `tacticam.mp4`). The goal is to assign **global player IDs** such that each player is consistently identified across both views, despite challenges like differing viewpoints, lack of facial or jersey features, and player movement.

---

## 📁 Files Included

| File | Description |
|------|-------------|
| `Soccer_Player_Detector.ipynb` | Full Colab notebook with step-by-step implementation |

---

## 🧠 Approach Overview

### 1. **Player Detection**
- Used the provided `best.pt` YOLOv11 model via the Ultralytics API.
- Detected players frame-by-frame in both videos.

### 2. **Tracking**
- Implemented a lightweight `CentroidTracker` to assign local `track_id`s to players in each view.
- Maintains identities across frames within each video.

### 3. **Motion Feature Extraction**
- Extracted motion trajectories (Δx, Δy) per `track_id`.
- Created fixed-length feature vectors representing each player's movement pattern.

### 4. **Cross-View Matching**
- Compared motion signatures between the two views using **cosine similarity**.
- Used the **Hungarian algorithm** to assign one-to-one global player IDs.

### 5. **Visualization**
- Annotated both videos with consistent `global_player_id`s.
- Exported final annotated videos for evaluation.

---

## 🛠️ Tools & Libraries

- `Python`, `OpenCV`, `Ultralytics YOLOv11`
- `SciPy`, `Scikit-learn`, `gdown`, `MoviePy`
- Google Colab environment for development and testing

---

## 📌 Key Results

- Players are consistently tracked and matched across different camera angles.
- Videos clearly demonstrate the system's ability to identify players by motion without relying on jersey numbers or face recognition.

---

## 👤 Author

**Kirtiraj Tilakdhari Jamnotiya**  
B.Tech Mechatronics Engineering, IIT Bhilai  
📧 kjamnotiya@gmail.com  
📱 +91 9270865999

---

## 📎 Notes

- Due to lack of jersey/face visibility, the system relies purely on **motion cues** and **tracking consistency**.
- Future improvements can integrate pose estimation (MediaPipe, OpenPose) or ball-player interaction for action-level identification.

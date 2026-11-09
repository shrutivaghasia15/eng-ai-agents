# Assignment 3 – Drone Detection and Kalman Tracking

This assignment uses a YOLO detector with a Kalman filter to track a drone across video sequences.

## Approach

- Fine-tuned the YOLO detector for 30 epochs.
- Used a Kalman filter with state `[cx, cy, vx, vy, w, h]`.
- Used Mahalanobis gating to select detections.
- Added coasting for missed detections.
- Added a reacquisition rule using a lower confidence threshold and wider gate when the track is lost.
- Tested different process and measurement noise settings.

## Final Tracking Results

- video13 detector AUC: **0.066**
- video13 Kalman tracker AUC: **0.165**
- Detector absent-box rate (all 20 sequences): **0.99**
- Kalman tracker absent-box rate (all 20 sequences): **0.31**

Both required tracking conditions were met.

## Noise Sensitivity

The best setting in my final 3 × 3 sweep was:

- `accel_std = 2.0`
- `meas_std = 2.0`
- AUC = **0.408**
- P@20 = **0.565**

## Output Video

The repository includes the rendered Kalman tracking output video:

`video12_kalman.mp4`

The green box shows the ground truth and the red box shows the Kalman tracker prediction.

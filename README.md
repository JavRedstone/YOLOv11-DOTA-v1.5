# DOTA Aerial Object Detection - YOLOv11 Demo Project
By: Javier H.

Colab link: https://colab.research.google.com/drive/1mb9WWhO9-k271FvuFEUB8LfRGbXbcCN-?usp=sharing

---

This project demonstrates how to preprocess and train the [YOLOv11](https://docs.ultralytics.com/models/yolo11/) model on aerial imagery using sample data from the **DOTA v1.5** dataset.

## Dataset

- **DOTA** (Dataset for Object deTection in Aerial images): A large-scale benchmark for detecting oriented objects in aerial images.
- **Version**: v1.5 (used for demonstration; v2.0 is not in Google Drive); [Official site](https://captain-whu.github.io/DOTA/dataset.html)
- **Note**: YOLOv11 is typically trained on DOTA v1.0, but this project focuses more on **data transformation and preprocessing**, not benchmarking accuracy.

## Model

- **Model**: YOLOv11 Nano variant
- **Input Size**: 640×640 (default)

## Preprocessing & Data Transformation (Main Focus)

This project shows one of the processes I take to convert datasets into YOLO-compatible format, especially for datasets similar DOTA with oriented bounding boxes (OBB) or varying image resolution and sizes.

- **Tiling**: Images are split into overlapping tiles of 640×640 pixels (with black padding as needed)
- **Label Adjustment**:
  - Translates OBB annotations to fit each tile
  - Clamps bounding boxes to tile edges
  - Converts polygon OBBs to YOLO-oriented format (normalized coordinates)
  - Converts class names to integer indices
- **Why Tiling?**:
  - Prevents distortion from resizing non-square images
  - Preserves detail in high-resolution images
  - Improves detection of small, dense aerial objects

## Training

- Training is done using the transformed dataset
- Evaluation metrics, training logs, and visual results (e.g., predictions, confusion matrix, loss curves) are produced to monitor performance

This project focuses on **the process and pipeline** in training the YOLOv11 model.

## Experimentation

Experimentation is crucial in machine learning, so it is natural that there is trial and error present in the code. This is a Jupyter notebook after all. As a result, some cells have duplicate import statements due to running them individually for debugging purposes.

## Files

- The `model_training_[date].txt` with the latest date has the latest model training runs on a T4 GPU (with a short accompanying video during training).
- The `JavierH_YOLOv11_DOTA_v1_5.ipynb` has the Jupyter Notebook with the shared Google Colab link attached.
- The `yolo_runs/obb_exp/` folder contains the data generated during the latest run of YOLOv11.
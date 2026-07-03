# YOLOv8 Training and Inference Workflow

## Install Dependencies

Install Ultralytics YOLOv8:

```bash
pip install ultralytics
```

Verify installation:

```bash
yolo
```

---

## Dataset Preparation

The dataset was collected and annotated using Roboflow.

Dataset Structure:

```text
pipe_clamp_detection/
│
├── train/
│   ├── images/
│   └── labels/
│
├── valid/
│   ├── images/
│   └── labels/
│
├── test/
│   ├── images/
│   └── labels/
│
└── data.yaml
```

---

## Model Training

Train YOLOv8s on the custom clamp dataset:

```bash
yolo task=detect mode=train model=yolov8s.pt data=data.yaml epochs=50 imgsz=640
```

### Parameters

| Parameter | Description |
|------------|-------------|
| task=detect | Object detection task |
| mode=train | Training mode |
| model=yolov8s.pt | YOLOv8 Small model |
| data=data.yaml | Dataset configuration |
| epochs=50 | Number of training epochs |
| imgsz=640 | Input image resolution |

---

## Resume Training

If training is interrupted:

```bash
yolo task=detect mode=train model=runs\detect\train\weights\last.pt data=data.yaml epochs=50 resume=True
```

---

## Validation and Evaluation

YOLO automatically evaluates:

- Precision
- Recall
- mAP@50
- mAP@50-95

Generated files:

```text
runs/detect/train/
│
├── results.png
├── confusion_matrix.png
├── weights/
│   ├── best.pt
│   └── last.pt
```

---

## Image Prediction

Run detection on a single image:

```bash
yolo task=detect mode=predict model=runs\detect\train\weights\best.pt source=image.jpg
```

Example:

```bash
yolo task=detect mode=predict model=runs\detect\train\weights\best.pt source=test.jpg
```

---

## Folder Prediction

Run detection on all validation images:

```bash
yolo task=detect mode=predict model=runs\detect\train\weights\best.pt source=valid\images
```

Results are saved automatically in:

```text
runs/detect/predict/
```

---

## Video Prediction

Run detection on a video:

```bash
yolo task=detect mode=predict model=runs\detect\train\weights\best.pt source=video.mp4
```

Example:

```bash
yolo task=detect mode=predict model=runs\detect\train\weights\best.pt source="clamp_test.mp4"
```

---

## Improved Video Detection

For small objects:

```bash
yolo task=detect mode=predict model=runs\detect\train\weights\best.pt source="clamp_test.mp4" conf=0.1 imgsz=960
```

### Parameters

| Parameter | Description |
|------------|-------------|
| conf=0.1 | Lower confidence threshold |
| imgsz=960 | Higher resolution for small object detection |

---

## Webcam Detection

Default webcam:

```bash
yolo task=detect mode=predict model=runs\detect\train\weights\best.pt source=0
```

External USB camera:

```bash
yolo task=detect mode=predict model=runs\detect\train\weights\best.pt source=1
```

---

## Output Files

### Best Model

```text
runs/detect/train/weights/best.pt
```

### Latest Checkpoint

```text
runs/detect/train/weights/last.pt
```

### Prediction Results

```text
runs/detect/predict/
runs/detect/predict2/
runs/detect/predict3/
...
```

---

## Training Results

| Metric | Score |
|----------|----------|
| Precision | 0.97 |
| Recall | 0.90 |
| mAP@50 | 0.94 |
| mAP@50-95 | 0.75 |

The trained YOLOv8 model achieved strong performance for pipe clamp detection on unseen validation images and videos.

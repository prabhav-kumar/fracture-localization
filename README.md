# Fracture Detection in X-ray Images using YOLOv8

This project uses the powerful YOLOv8 object detection model to automatically **detect and localize bone fractures** in X-ray images. It's trained on a custom annotated dataset and fine-tuned to recognize fracture regions with high precision.

---

## 📁 Dataset

We used the publicly available **FracAtlas dataset** from Kaggle:

🔗 [FracAtlas Dataset on Kaggle](https://www.kaggle.com/datasets/abdohamdg/fracatlas-dataset)

The dataset contains X-ray images of bone fractures with labeled bounding boxes for training an object detection model. It's organized in YOLO format with separate folders for training, validation, and testing.

**Structure:**

Fracatlas/
├── images/
│ ├── train/
│ ├── val/
│ └── test/
├── labels/
│ ├── train/
│ ├── val/
│ └── test/
└── fracatlas.yaml


**Class:**  
- `0` – Fracture

---

## 🚀 Model Details

- **Model Used:** YOLOv8m (from Ultralytics)
- **Pretrained:** Yes (on COCO)
- **Task:** Object Detection (Fracture Classification + Localization)
- **Framework:** Python + PyTorch (via Ultralytics)

We fine-tuned the pretrained YOLOv8m weights on our custom fracture dataset. The model is capable of both identifying whether a fracture is present and highlighting its location with bounding boxes.

---

## ⚙️ Training Configuration

- **Epochs:** 50  
- **Batch Size:** 16  
- **Image Size:** 640 × 640  
- **Optimizer:** SGD (default YOLOv8 optimizer)  
- **Augmentations:** Flip, scale, crop, HSV adjustments, etc. (default YOLOv8 settings)

---

## 📊 Model Performance

Here’s how the model performed during training, validation, and testing:

### Training Metrics
| Metric       | Value  |
|--------------|--------|
| Precision    | 0.743  |
| Recall       | 0.581  |
| mAP@0.5      | 0.638  |
| mAP@0.5:0.95 | 0.283  |

### Validation Metrics
| Metric       | Value  |
|--------------|--------|
| Precision    | 0.655  |
| Recall       | 0.538  |
| mAP@0.5      | 0.545  |
| mAP@0.5:0.95 | 0.247  |

### Test Metrics
| Metric       | Value  |
|--------------|--------|
| Precision    | 0.718  |
| Recall       | 0.484  |
| mAP@0.5      | 0.580  |
| mAP@0.5:0.95 | 0.254  |

---

## 📷 Sample Predictions

The trained model is able to accurately draw bounding boxes around fractures in new X-ray images. It works well even on previously unseen data.

---

## How to Run the Project

1. **Clone this repository:**
   ```bash
   git clone https://github.com/yourusername/fracatlas-yolov8.git
   cd fracatlas-yolov8
   ```
2. **Install dependencies:**
   ```bash
   pip install ultralytics
   ```
3. **Train (optional):**
   ```bash
   yolo task=detect mode=train model=yolov8m.pt data=fracatlas.yaml epochs=50 imgsz=640
   ```
4. **Run inference:**

   ```bash
   yolo task=detect mode=predict model=best.pt source=/path/to/image_or_folder
   ```
## Want the Trained Model?

To get the trained YOLOv8 fracture detection model (.pt file), feel free to email me at:
📧 k.prabhav2005@gmail.com
I’ll be happy to share it with you.

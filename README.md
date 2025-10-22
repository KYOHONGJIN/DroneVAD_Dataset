# DroneVAD Dataset (v1.0)

DroneVAD is a **UAV-based Video Anomaly Detection dataset** designed for moving-camera aerial surveillance scenarios.  
It provides video clips captured from a flying drone to study spatio-temporal anomalies such as vehicles on sidewalks or humans on rooftops.

👉 **[Download from Google Drive](https://drive.google.com/uc?id=YOUR_FILE_ID)**  
(Replace `YOUR_FILE_ID` with the actual Google Drive shared file ID.)

---

## 📁 Folder Structure
DroneVAD_Dataset/  
├── 00.vehicle_road/  
│ └── sequence1/  
│ ├── train/  
│ │ ├── 01/ # Cropped frame folder (640×640)    
│ │ ├── 02/    
│ │ └── ...  
│ ├── test/  
│ │ ├── 01/ # Cropped frame folder  
│ │ ├── 01.npy # Frame-level label for folder 01  
│ │ ├── 02/  
│ │ ├── 02.npy  
│ │ └── ...  
│ └── videos/ # Original MP4 clips  
├── 01.parking_lot/  
│ └── sequence1/  
│ ├── train/  
│ ├── test/  
│ └── videos/  
└── 02.rooftop_of_building/  
└── sequence1/  
├── train/  
├── test/  
└── videos/  


---

## 🧩 Directory Details

| Folder | Description |
|---------|--------------|
| **train/** | Contains only **normal** frame sequences used for model training. Each subfolder (e.g., `01/`, `02/`) includes 640×640 cropped frames extracted from 30 FPS videos. |
| **test/** | Contains **both normal and abnormal** frame sequences. Each frame folder (e.g., `01/`, `02/`) has a corresponding `.npy` label file with frame-wise anomaly labels. |
| **videos/** | Original MP4 clips before frame extraction. Used for reference or visualization. |

---

## 📄 Example of `.npy` Label File

Each `.npy` file (e.g., `01.npy`) corresponds to the frame folder with the same name (e.g., `test/01/`).

| Example | Description |
|----------|--------------|
| `test/01/` | Contains frames like `000001.jpg`, `000002.jpg`, … |
| `test/01.npy` | NumPy array of same length as number of frames |

**Example:**

```python
import numpy as np
labels = np.load("test/01.npy")
print(labels[:10])
# array([0, 0, 0, 0, 1, 1, 1, 0, 0, 0])
```
---
## How to Download
pip install gdown
gdown https://drive.google.com/uc?id=YOUR_FILE_ID -O DroneVAD_Dataset_v1.0.zip
unzip DroneVAD_Dataset_v1.0.zip

---
## Data Specification
| Item                  | Value                                     |
| --------------------- | ----------------------------------------- |
| Altitude              | 60, 80 meters                              |
| Frame rate            | 30 FPS                                    |
| Frame crop size       | 640×640 pixels                            |
| Resolution (original) | 1920×1080                                 |
| Format                | MP4 (videos), JPG (frames), NPY (labels)  |
| Drone                 | DJI Mavic 3                               |
| Environment           | Campus, parking lots, rooftops            |
| Label granularity     | Frame-level binary (0=normal, 1=abnormal) |

---
## Recommended Usage
DroneVAD can be used for:
- Unsupervised/Self-supervised video anomaly detection
- Future frame prediction or reconstruction-based learning
- Transformer or memory-augmented models (e.g., ANDT, MemAE, Drone-Guard)
Suggested Pipeline:
1) Train models using train/ frames (normal-only).
2) Evaluate models on test/ frames.
3) Compare predicted anomaly scores with .npy labels to compute AUC, EER, or F1.

---
## License
This dataset is released under the
Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0) license.
It may be used and modified for research and non-commercial purposes with proper citation.

---
## Citation 
If you use DroneVAD in your research, please cite:

@dataset{DroneVAD_2025,
  author  = {Kyo, Hong Jin},  
  title   = {DroneVAD: UAV Video Anomaly Detection Dataset},  
  year    = {2025},  
  url     = {https://github.com/KYOHONGJIN/DroneVAD_Dataset}  
}  

---
## Acknowledgement
This work was supported by the IITP (Institute of Information & Communications Technology Planning & Evaluation) –
ITRC (Information Technology Research Center) grant funded by the Korea government
(Ministry of Science and ICT) (IITP-2025-RS-2024-00438409).

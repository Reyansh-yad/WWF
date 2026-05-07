<div align="center">

<img src="https://img.shields.io/badge/eSewa_×_WWF-Hackathon_2026-2db36f?style=for-the-badge&logoColor=white" />
<img src="https://img.shields.io/badge/Challenge-1_Wildlife_AI-39e07a?style=for-the-badge" />
<img src="https://img.shields.io/badge/Status-In_Development-f5a623?style=for-the-badge" />

<br/><br/>

# 🐆 WildLens — Wildlife Species Detection AI

### *Automated camera trap image classification using computer vision*

**eSewa × WWF Hackathon 2026 · Challenge 1**

<br/>

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![YOLOv8](https://img.shields.io/badge/YOLOv8-Ultralytics-00BFFF?style=flat-square)](https://ultralytics.com)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-009688?style=flat-square&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![React](https://img.shields.io/badge/React-18+-61DAFB?style=flat-square&logo=react&logoColor=black)](https://react.dev)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

<br/>

</div>

---

## 📌 Table of Contents

- [Problem Statement](#-problem-statement)
- [Our Solution](#-our-solution)
- [Demo](#-demo)
- [Features](#-features)
- [Architecture](#-system-architecture)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Dataset](#-dataset)
- [Model Performance](#-model-performance)
- [API Reference](#-api-reference)
- [Team](#-team)

---

## 🎯 Problem Statement

WWF and wildlife conservation researchers deploy **camera traps** — motion-triggered cameras — across forests and wildlife corridors to monitor biodiversity. These cameras generate **thousands of images per day**.

> **The Problem:** Up to **80% of images are empty** — triggered by wind, shadows, or vegetation movement. Researchers spend countless hours manually sifting through these images to find ones that actually contain animals.

This is:
- ⏱️ **Extremely time-consuming** — weeks of manual review per dataset
- 💸 **Expensive** — researcher hours wasted on irrelevant frames
- 🐘 **Slows conservation decisions** — delayed species reports, missed sightings

---

## 💡 Our Solution

**WildLens** is an AI-powered web application that automatically analyzes camera trap images and:

1. **Detects** whether an image contains wildlife or not (binary classification)
2. **Identifies** the species present with confidence score (bonus feature)
3. **Filters** and organizes images into a clean dashboard for researchers

> ✅ What used to take **days of manual review** now takes **seconds**.

---

## 🎥 Demo

> 📺 **[Watch Demo Video →](YOUR_YOUTUBE_LINK_HERE)**

<!-- Replace with actual screenshot once available -->
```
Upload Image → AI Detects → Results Dashboard
     📷              🤖               📊
[camera_trap.jpg]  [YOLOv8]   [Snow Leopard: 92%]
```

---

## ✨ Features

| Feature | Status |
|---|---|
| 🔍 Wildlife vs. No-Wildlife classification | ✅ Core Feature |
| 🐾 Species identification (Snow Leopard, Deer, Tiger, etc.) | ✅ Core Feature |
| 📊 Confidence score per detection | ✅ Core Feature |
| 🖼️ Batch image upload (folder upload) | ✅ Core Feature |
| 📁 Filtered results dashboard (wildlife / empty) | ✅ Core Feature |
| 📥 Export results as CSV report | 🚧 In Progress |
| ☁️ Cloud deployment (AWS/GCP) | 🔜 Planned |
| 📱 Mobile-responsive UI | ✅ Core Feature |

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────┐
│                   USER (Researcher)                  │
└────────────────────────┬────────────────────────────┘
                         │ Uploads image(s)
                         ▼
┌─────────────────────────────────────────────────────┐
│              React.js Frontend (Port 3000)           │
│  ┌──────────────┐  ┌───────────────┐  ┌──────────┐  │
│  │ Upload Page  │  │ Processing UI │  │ Results  │  │
│  │ Drag & Drop  │  │ Loading State │  │Dashboard │  │
│  └──────────────┘  └───────────────┘  └──────────┘  │
└────────────────────────┬────────────────────────────┘
                         │ POST /predict (multipart/form-data)
                         ▼
┌─────────────────────────────────────────────────────┐
│             FastAPI Backend (Port 8000)              │
│  ┌────────────────────────────────────────────────┐  │
│  │  /predict endpoint                             │  │
│  │  → Preprocess image (OpenCV)                   │  │
│  │  → Run YOLOv8 inference                        │  │
│  │  → Return JSON: {has_wildlife, species, conf}  │  │
│  └────────────────────────────────────────────────┘  │
└────────────────────────┬────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────┐
│           YOLOv8 Model (best.pt)                     │
│  Fine-tuned on Wildlife Insights / iNaturalist       │
│  Output: Class Label + Bounding Box + Confidence     │
└─────────────────────────────────────────────────────┘
```

---

## 🛠️ Tech Stack

### AI / Machine Learning
| Tool | Purpose |
|---|---|
| ![Python](https://img.shields.io/badge/-Python_3.10-3776AB?logo=python&logoColor=white&style=flat-square) | Core AI/ML language |
| **YOLOv8 (Ultralytics)** | Object detection — wildlife classification |
| **PyTorch** | Model training framework |
| **OpenCV** | Image preprocessing & manipulation |
| **Jupyter Notebook** | Model experimentation |

### Backend
| Tool | Purpose |
|---|---|
| ![FastAPI](https://img.shields.io/badge/-FastAPI-009688?logo=fastapi&logoColor=white&style=flat-square) | REST API server |
| **Uvicorn** | ASGI server |
| **Pillow** | Image handling |

### Frontend
| Tool | Purpose |
|---|---|
| ![React](https://img.shields.io/badge/-React_18-61DAFB?logo=react&logoColor=black&style=flat-square) | UI framework |
| **TailwindCSS** | Styling |
| **Axios** | API requests |

### DevOps
| Tool | Purpose |
|---|---|
| ![GitHub](https://img.shields.io/badge/-GitHub-181717?logo=github&logoColor=white&style=flat-square) | Version control |
| **Docker** *(optional)* | Containerization |
| **Google Colab** | Model training (free GPU) |

---

## 📁 Project Structure

```
WildLens/
│
├── 📂 backend/
│   ├── main.py                  # FastAPI app entry point
│   ├── predict.py               # YOLOv8 inference logic
│   ├── preprocess.py            # Image preprocessing utils
│   ├── requirements.txt         # Python dependencies
│   └── models/
│       └── best.pt              # Trained YOLOv8 weights
│
├── 📂 frontend/
│   ├── public/
│   ├── src/
│   │   ├── App.jsx
│   │   ├── components/
│   │   │   ├── UploadZone.jsx   # Drag-and-drop image upload
│   │   │   ├── ResultCard.jsx   # Detection result card
│   │   │   └── Dashboard.jsx    # Results overview
│   │   └── api/
│   │       └── predict.js       # API calls to backend
│   ├── package.json
│   └── tailwind.config.js
│
├── 📂 model/
│   ├── train.py                 # Model training script
│   ├── evaluate.py              # Evaluation & metrics
│   ├── dataset.yaml             # YOLOv8 dataset config
│   └── notebooks/
│       └── wildlife_detection.ipynb  # Colab training notebook
│
├── 📂 docs/
│   ├── architecture.png         # System architecture diagram
│   ├── demo_screenshots/        # UI screenshots
│   └── TeamName_Challenge1_Submission.pdf  # Pitch deck
│
├── .gitignore
├── docker-compose.yml           # (optional)
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.10+
- Node.js 18+
- Git

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/TeamName_Challenge1.git
cd TeamName_Challenge1
```

### 2. Backend Setup

```bash
cd backend

# Create virtual environment
python -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Start the API server
uvicorn main:app --reload --port 8000
```

> ✅ API will be live at `http://localhost:8000`
> 📖 Auto-generated docs at `http://localhost:8000/docs`

### 3. Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Start development server
npm run dev
```

> ✅ App will be live at `http://localhost:3000`

### 4. Quick Model Test

```bash
# From project root
python -c "
from ultralytics import YOLO
model = YOLO('backend/models/best.pt')
results = model('path/to/your/test_image.jpg')
print(results[0].boxes)
"
```

### 5. requirements.txt

```
ultralytics>=8.0.0
torch>=2.0.0
torchvision>=0.15.0
opencv-python>=4.8.0
fastapi>=0.100.0
uvicorn>=0.23.0
pillow>=10.0.0
python-multipart>=0.0.6
numpy>=1.24.0
```

---

## 📦 Dataset

We use the following open-source datasets for training:

| Dataset | Source | Size | Use |
|---|---|---|---|
| **Wildlife Insights** | wildlife.ai | ~1M+ images | Primary training set |
| **iNaturalist** | inaturalist.org | Millions | Species diversity |
| **Snapshot Serengeti** | zooniverse.org | 3.2M images | African wildlife |
| **COCO Animals** | cocodataset.org | Subset | Augmentation |

### Dataset Split

```
Total Images: ~2,000 (hackathon prototype)
├── Train:      1,600 (80%)
├── Validation:   200 (10%)
└── Test:         200 (10%)

Classes:
├── wildlife_present   → 1,000 images
└── no_wildlife        → 1,000 images
```

---

## 📊 Model Performance

> *Results on held-out test set (updated as training progresses)*

| Metric | Score |
|---|---|
| **Accuracy** | TBD |
| **Precision** | TBD |
| **Recall** | TBD |
| **F1 Score** | TBD |
| **mAP@0.5** | TBD |
| **Inference Time** | ~50ms/image |

### Training Config

```yaml
model: yolov8n.pt          # YOLOv8 Nano (fastest)
epochs: 50
imgsz: 640
batch: 16
optimizer: Adam
lr0: 0.001
device: cuda / cpu
```

---

## 📡 API Reference

### `POST /predict`

Accepts an image and returns wildlife detection result.

**Request:**
```http
POST http://localhost:8000/predict
Content-Type: multipart/form-data

file: <image_file>
```

**Response:**
```json
{
  "has_wildlife": true,
  "species": "Snow Leopard",
  "confidence": 0.91,
  "bounding_box": [120, 80, 450, 380],
  "processing_time_ms": 48
}
```

**Response (no wildlife):**
```json
{
  "has_wildlife": false,
  "species": null,
  "confidence": 0.97,
  "bounding_box": null,
  "processing_time_ms": 31
}
```

**Error Response:**
```json
{
  "error": "Invalid image format",
  "status": 422
}
```

---

## 👥 Team

<table>
  <tr>
    <th>Name</th>
    <th>Role</th>
    <th>Responsibility</th>
  </tr>
  <tr>
    <td><strong>Reyansh [Last Name]</strong></td>
    <td>ML Engineer / Team Lead</td>
    <td>YOLOv8 model training, FastAPI backend</td>
  </tr>
  <tr>
    <td><strong>Member 2</strong></td>
    <td>Frontend Developer</td>
    <td>React UI, dashboard design</td>
  </tr>
  <tr>
    <td><strong>Member 3</strong></td>
    <td>Backend Developer</td>
    <td>API integration, data pipeline</td>
  </tr>
  <tr>
    <td><strong>Member 4</strong></td>
    <td>Designer / Presenter</td>
    <td>UI/UX design, pitch deck, demo</td>
  </tr>
</table>

**Institution:** Nepal Engineering College, Pokhara University
**Event:** eSewa × WWF Hackathon 2026 — Challenge 1

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- [Ultralytics YOLOv8](https://ultralytics.com) — object detection framework
- [Wildlife Insights](https://wildlife.ai) — dataset and inspiration
- [Microsoft MegaDetector](https://github.com/microsoft/CameraTraps) — reference implementation
- [eSewa & WWF Nepal](https://esewa.com.np) — for organizing this challenge

---

<div align="center">

**Built with ❤️ for Wildlife Conservation · eSewa × WWF Hackathon 2026**

*"Technology in service of nature"*

</div>

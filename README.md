# 🦺 PPE Kit Detection System

An AI-powered real-time Personal Protective Equipment (PPE) detection system using **YOLOv8**, **FastAPI**, and **React**.

The system detects safety compliance (helmet, jacket, gloves, boots, goggles) from **live video streams** and **uploaded images**, and highlights violations in real time.

---

## 🚀 Features

- 🔴 Real-time PPE detection via webcam
- 🟢 Image upload & detection
- ⚠️ Automatic violation detection (missing PPE)
- 🎯 Person-wise PPE analysis
- 🎥 Live video streaming using FastAPI
- 📊 Real-time alert system
- 🔄 Start/Stop camera control
- ⚡ Fast and lightweight backend

---

## 🧠 Tech Stack

### Backend
- Python
- FastAPI
- OpenCV
- Ultralytics YOLOv8
- PyTorch

### Frontend
- React (Vite)
- Tailwind CSS
- React Router

---

## 📂 Project Structure
```
PEE_kit_detection/
│
├── ml_service/
│ ├── app.py # FastAPI backend
│ ├── requirements.txt # Python dependencies
│ ├── utils/
│ │ └── logic.py # Violation detection logic
│ └── models/ # (Not included in repo)
│
├── frontend/
│ ├── src/
│ ├── package.json
│
└── README.md
```

---

## 🧪 API Endpoints

| Endpoint | Method | Description |
|--------|--------|------------|
| `/detect_image` | POST | Upload image & detect PPE |
| `/video_feed` | GET | Live video stream |
| `/latest_status` | GET | Get latest detection status |
| `/toggle_camera` | POST | Start/Stop webcam |

---

## 🧠 How It Works

1. Webcam captures frames  
2. Human detection model identifies persons  
3. Each person is cropped  
4. PPE model runs on each crop  
5. Missing PPE is detected  
6. Alerts are generated and streamed  

---

## 📸 Screenshots

> 📌 Add your screenshots here

### 🔹 Dashboard (Live Detection)
![Dashboard](./Frontend/src/assets/screenshots/dashboard.png)

### 🔹 Image Detection
![Image Detection](./Frontend/src/assets/screenshots/image_detection.jpeg)

### 🔹 Violation Alert
![Violation](./Frontend/src/assets/screenshots/violation.jpeg)

---

## 📦 Model Weights

⚠️ Model files are not included due to size.

👉 Download from:  
**https://drive.google.com/drive/folders/15PjZgrJML0rLKwg8MUtdO2RfZMYwkf1P?usp=drive_link**

After downloading, place inside: 
```
ml_service/models/

```
Example:

```
ml_service/models/best.pt

```

---

## ⚙️ Installation & Setup

### 🔹 1. Clone Repository
```
git clone https://github.com/arcane-2004/PEE_kit_detection.git

cd PEE_kit_detection
```

---

### 🔹 2. Backend Setup
```
cd ml_service
python -m venv venv
source venv/bin/activate # Mac/Linux
venv\Scripts\activate # Windows

pip install -r requirements.txt
```

---

### 🔹 3. Run Backend
```
uvicorn app:app --reload
```
Backend runs at:  
```
http://127.0.0.1:8000
```

---

### 🔹 4. Frontend Setup
```
cd frontend
npm install
npm run dev
```

Frontend runs at:  
```
http://localhost:5173
```
Create a `.env` file in the `client` directory:

```env
# Backend API URL
VITE_API_BASE_URL=http://localhost:8000
```

---

## 🎮 Usage

- Open frontend in browser  
- Start camera using UI  
- View live detection  
- Upload images for testing  
- Monitor alerts in real-time  

---

---

## 📌 Future Improvements

### 🔁 1. Person Tracking (DeepSORT / ByteTrack)
- Integrate **DeepSORT** or **ByteTrack** for persistent person tracking across frames
- Assign unique IDs to each detected person
- Track PPE compliance history per individual over time
- Useful in large industrial environments with multiple workers

### 🔊 2. Sound Alerts for Violations
- Trigger **real-time audio alerts** when PPE violations are detected
- Different alert tones for different missing items (e.g., no helmet vs no gloves)
- Browser-based implementation using the **Web Audio API**
- Configurable alert cooldown to prevent repeated noise

### ☁️ 3. Cloud Deployment
- Dockerize both **FastAPI backend** and **React frontend**
- Deploy backend on **AWS EC2 / GCP / Railway**
- Deploy frontend on **Vercel / Netlify**
- Use **NGINX** as a reverse proxy for production setup
- Add environment-based config (`.env.production`)

### 📊 4. Violation History Dashboard
- Log every detected violation with:
  - Timestamp
  - Person ID
  - Missing PPE items
  - Snapshot image of the violation
- Store logs in **SQLite / PostgreSQL**
- Display violation history in a dedicated React dashboard page
- Export logs as **CSV / PDF reports**

### 🧠 5. Model Optimization
- Convert YOLOv8 model to **ONNX / TensorRT** format for faster inference
- Implement **model quantization** for edge deployment (Raspberry Pi, Jetson Nano)
- Add support for multiple camera streams simultaneously
- Benchmark and compare inference speeds across formats

### 🔔 6. Email / SMS Notification System
- Send **email alerts** (via SMTP / SendGrid) when violations are detected
- Integrate **Twilio** for SMS alerts to supervisors
- Configurable thresholds (e.g., alert only after 3 consecutive violations)
- Daily/weekly **violation summary reports** via email

### 👤 7. Role-Based Access Control (RBAC)
- Add **user authentication** (JWT-based login)
- Define roles: Admin, Supervisor, Viewer
- Admins can configure detection settings
- Supervisors receive alerts and view dashboards
- Implement using **FastAPI OAuth2 + React Auth Context**

### 📱 8. Mobile App Support
- Build a **React Native** or **Flutter** mobile app
- View live detection feed on mobile
- Receive **push notifications** for violations
- Works over local network or cloud-deployed backend

### 🗂️ 9. Multi-Site / Multi-Camera Support
- Support multiple camera feeds from different locations
- Dashboard with a **grid view** of all camera streams
- Site-wise violation tracking and reporting
- Useful for large factories or construction sites

### 🧪 10. Unit & Integration Tests
- Add **pytest** test suite for backend logic (`utils/logic.py`)
- Add **React Testing Library** tests for frontend components
- Set up **GitHub Actions CI/CD** to auto-run tests on every push
- Achieve minimum **80% code coverage**

---

## 🤝 Contributing

Pull requests are welcome! Feel free to improve the system.

---

## 📜 License

This project is for educational purposes.

---

## 👨‍💻 Author

**Sumit Kumar**

---

## ⭐ If you like this project

Give it a ⭐ on GitHub!

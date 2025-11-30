# ASL Hand-Sign Recognition (Custom Dataset + Hold-to-Type System)

This project is an American Sign Language hand-sign recognition system built with MediaPipe, OpenCV, and a Random Forest classifier.

It includes:
- Dataset collector (captures images for A–Z)
- Feature extractor (MediaPipe hand landmarks → normalized data)
- Model trainer
- Real-time inference program with:
  - Letter detection
  - Hold-to-type system
  - On-screen sentence building

You must create your own dataset and your own model because mine contains my face and hands.

---

## 📸 Example ASL Image  
You can add your own example image here later:

![ASL Example](images/your_image_here.jpg)

---

## 📁 Project Structure
```
project/
│-- collect_imgs.py
│-- create_dataset.py
│-- train_classifier.py
│-- inference_classifier.py
│-- data/
│-- model.p
│-- data.pickle
│-- README.md
```

---

## 🔧 Requirements

Install dependencies:
```
pip install opencv-python mediapipe scikit-learn numpy matplotlib
```

---

## 🧪 Create Virtual Environment (recommended)

### Create venv
```
python -m venv venv
```

### Activate
Windows:
```
venv\Scripts\activate
```

macOS / Linux:
```
source venv/bin/activate
```

### Freeze for GitHub
```
pip freeze > requirements.txt
```

### .gitignore
```
venv/
```

---

## 📸 Step 1: Collect Your Dataset

Run:
```
python collect_imgs.py
```

For each class (0–25):
- Live preview appears
- Press Q to start capturing
- Script saves images into /data/<class_number>/

Class → Letter map:
0=A … 25=Z  
Optional: 26 = space

---

## ✍ Step 2: Create Dataset (Extract Landmarks)

Run:
```
python create_dataset.py
```

Produces:
- `data.pickle`

---

## 🤖 Step 3: Train the Model

Run:
```
python train_classifier.py
```

Outputs:
- `model.p`

---

## 🎥 Step 4: Real-Time Inference (Hold-to-Type)

Run:
```
python inference_classifier.py
```

Features:
- Detects ASL letters live  
- Draws landmarks + bounding box  
- Shows predicted letter  
- Hold a letter for 2 seconds to type it  
- “Typed sentence” shown at bottom  
- Press Q to quit  

Adjust hold time:
```
HOLD_TIME = 2.0
```

---

## 🖼 Add Your ASL Image to README

Create folder:
```
images/
```

Add file:
```
images/asl.jpg
```

Insert into README:
```
![ASL Example](images/asl.jpg)
```

---

## 🧭 How to Upload to GitHub Using VS Code

1. Open project folder in VS Code  
2. Click Source Control  
3. Click “Initialize Repository”  
4. Stage all files  
5. Write a commit message  
6. Click ✓ Commit  
7. Click “Publish Branch”  
8. Choose Public or Private  

---

## 🧼 Suggested .gitignore
```
venv/
__pycache__/
*.pickle
*.p
*.mp4
data/
model.p
```

---

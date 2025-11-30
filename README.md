# ASL Hand-Sign Recognition (Custom Dataset + Hold-To-Type Input)

This project is a real-time American Sign Language hand-sign recognition system.
It uses MediaPipe Hands, OpenCV, and a Random Forest classifier to detect hand landmarks and classify them into letters A–Z.
The system includes a hold-to-type feature that adds a letter to a sentence when held for a fixed duration.

---------------------------------------------------------------------

## ✨ Features

- Real-time ASL letter prediction
- MediaPipe hand landmark detection
- Normalized landmark feature extraction
- Trainable custom model
- Hold a hand sign for 2 seconds to type it
- On-screen sentence display
- Fully offline
![ASL](ASL_alphabet.png)


---------------------------------------------------------------------

## 📁 Project Structure

(project folder)
    collect_imgs.py
    create_dataset.py
    train_classifier.py
    inference_classifier.py
    data/
    model.p
    data.pickle
    README.md

---------------------------------------------------------------------

## ⚠️ Important

This repository does NOT include:
- a dataset  
- a trained model  

You must collect and train your own, for privacy reasons.

---------------------------------------------------------------------

## 🔧 Installation

Run inside your virtual environment:

    pip install opencv-python mediapipe scikit-learn numpy matplotlib

---------------------------------------------------------------------

## 🧪 Step 1: Collect Your Dataset

Start the collector:

    python collect_imgs.py

Instructions:
- A camera preview opens
- For each class (0–25), press Q to capture images
- Images save to: data/<class_number>/

Mapping:
0 = A  
1 = B  
...  
25 = Z  
optional 26 = space

---------------------------------------------------------------------

## ✍️ Step 2: Create Dataset (Landmark Extraction)

Run:

    python create_dataset.py

This script:
- Processes all images
- Extracts MediaPipe hand landmarks
- Normalizes landmarks
- Saves dataset to data.pickle

---------------------------------------------------------------------

## 🤖 Step 3: Train Your Model

Run:

    python train_classifier.py

This:
- Loads data.pickle
- Trains Random Forest classifier
- Exports model.p

---------------------------------------------------------------------

## 🎥 Step 4: Real-Time Inference (Hold-To-Type)

Run:

    python inference_classifier.py

Features:
- Displays predicted letter above bounding box
- Hold letter for 2 seconds → it gets added to a sentence
- Press Q to quit

Adjust hold time inside the script:

    HOLD_TIME = 2.0

---------------------------------------------------------------------

## 📚 How It Works (Technical Overview)

1. MediaPipe generates 21 hand landmarks.
2. For each landmark → extract x and y.
3. Normalize values relative to minimum x/y.
4. Create a 42-length feature vector.
5. Model predicts the corresponding letter.
6. In inference:
   - Track if prediction stays the same
   - If stable long enough → commit to sentence


---------------------------------------------------------------------

## 🤝 Contributions

Possible improvements:
- Add numbers 0–9
- Support for ASL words
- GUI interface
- Text-to-speech output
- Better ML model

---------------------------------------------------------------------

## 🙌 Notes

This project is for learning and experimentation.
It is NOT a certified ASL interpretation system.


# SCENE-DETECT — Human Scene Detection for Smart Homes

**SCENE-DETECT** is a smart, privacy-conscious scene understanding system designed to assist blind and visually impaired individuals. It automatically detects what is happening in a room — specifically:

- Person is **present and OK**
- Person is **present and NOT OK** (e.g., collapsed or lying)
- **No person** in the scene

The system uses pose detection and intelligent rules to classify each situation and optionally provides a voice alert when something is wrong.

---

## Project Highlights

- **Privacy first**: no original images are stored or shown
- **Real-time** and **image-based** variants
- Works with **single or multiple persons**
- Powered by **MediaPipe** and **YOLOv8-Pose**
- Audio alerts for critical events

---

## Project Files

### `detection_with_images.py`
**Single Image Scene Detection**  
This script processes individual images from three folders:
- `/Nobody/`
- `/Person OK/`
- `/Person NOT OK/`

For each image:
- Detects pose using MediaPipe
- Classifies the scene
- Draws a clean stick-figure skeleton on a 512×512 canvas
- Labels the result and saves it

📁 Useful for: testing, dataset analysis, offline evaluation

---

### `detection_with_live_mediapipe.py`
**Live Scene Detection (Single Person Only)**  
Uses a webcam or phone camera feed and processes each frame using MediaPipe Pose.

- Only detects **one person** at a time
- Very accurate pose quality (33 points, including z-depth)
- Draws stick-figure in real time on a clean canvas
- Announces via voice: **"Person not okay!"**
- Discards the original image after use (privacy maintained)

📁 Best for: simple demos, high-accuracy single-person use

---

### `detection_with_live_yolo.py`
**Live Scene Detection (Multi-Person)**  
Uses YOLOv8-Pose for real-time detection of **multiple people**.

- Draws each person as a stick figure in **true position**
- Classifies each person individually: **OK** / **NOT OK**
- Places labels near each person
- Voice alert if **anyone** is "NOT OK"
- All raw image data is deleted after use to preserve privacy

📁 Best for: advanced demos, multi-person environments, smart home simulation

---

### `Scene_Detect_CNN.ipynb`
**2D Image based Scene Detection**  
This script is built on the Google Colab. It takes the zip file from the Google drive. It processes individual images from three folders splitted into Train and Test directories:
- `/Nobody/`
- `/Person OK/`
- `/Person NOT OK/`

For each image:
- Assign images the class/label with the name of folder
- Perform Image Augmentation and Image processing using CNN model
- Trains the model
- Labels the result using OpenCV

---

## Voice Output
All live scripts support audio alerts via `pyttsx3`. The system says:  
**“Alert. Person not okay.”**  
...when a collapsed person is detected.

---

## Requirements

Install dependencies:

**For Linux**
```bash
pip install -r requirements_linux.txt
```

**For Windows**
```bash
pip install -r requirements_win.txt
```

Basic requirements:
- Python 3.8+
- OpenCV
- MediaPipe
- Ultralytics (for YOLOv8)
- pyttsx3

---

## How to Run

**Image detection:**
```bash
python detection_with_images.py
```

**Live detection (MediaPipe):**
```bash
python detection_with_live_mediapipe.py
```

**Live detection (YOLOv8 multi-person):**
```bash
python detection_with_live_yolo.py
```

---

## Privacy Compliance

SCENE-DETECT ensures:
- Original RGB frames are deleted immediately after pose extraction
- Output is shown as skeleton-only canvas
- Designed with assistive and ethical AI principles in mind

---

## Use Cases

- 🏠 Smart home monitoring for elderly or visually impaired
- 🧪 Human activity classification demos
- 👩‍🏫 Teaching pose estimation + privacy-centered design
- 📊 Dataset analysis and model evaluation

---

## Authors

- **Farrukh Rasool**
- Smart Scene Detect Project, OTH Amberg-Weiden
- Course: Industry 4.0 Project/ Artificial Intelligence for Industrial Applications


## License
This project is licensed under the terms of the GNU General Public License v3.0 (GPLv3).

You are free to:

Share — copy and redistribute the material in any medium or format

Adapt — remix, transform, and build upon the material for any purpose

Under the following terms:

Copyleft — If you modify and distribute the project, you must release it under the same GPLv3 license.

---

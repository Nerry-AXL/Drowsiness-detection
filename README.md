# Drowsiness Detection System

This repository contains a Drowsiness Detection System built using Python, OpenCV, and machine learning techniques. The system is designed to monitor a driver's eye movements and alert them if signs of drowsiness are detected, helping to prevent accidents caused by fatigue.

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [How It Works](#how-it-works)
- [Model Details](#model-details)
- [Results](#results)
- [Contributing](#contributing)

## Project Overview

Drowsiness while driving is a significant cause of road accidents. This project aims to create a system that detects driver drowsiness in real-time and issues a warning to help prevent accidents. The system uses computer vision to track the driver’s eyes and assess their level of alertness.

## Features

- Real-time eye detection using OpenCV.
- Calculation of Eye Aspect Ratio (EAR) to determine drowsiness.
- Alerts (audio/visual) when drowsiness is detected.
- Adjustable thresholds for customizing the sensitivity of drowsiness detection.

## Installation

To run this project, you need Python installed on your system along with the required libraries. Install the dependencies using the following command:

```bash
pip install -r requirements.txt
```

### Dependencies

- Python 3.x
- OpenCV
- dlib
- imutils
- NumPy

## Usage

1. **Clone the repository:**

    ```bash
    git clone https://github.com/Nerry-AXL/Drowsiness-detection.git
    ```

2. **Navigate to the project directory:**

    ```bash
    cd Drowsiness-detection
    ```

3. **Run the detection script:**

    ```bash
    python drowsiness_detection.py
    ```

4. **Adjust settings:**
   You can customize the sensitivity of the drowsiness detection by modifying the `EAR_THRESHOLD` and `EAR_CONSEC_FRAMES` values in the script.

## How It Works

### Eye Aspect Ratio (EAR)

The system relies on calculating the Eye Aspect Ratio (EAR), which is a measure of the eye's openness. It is computed using the distances between specific facial landmarks around the eyes:

- EAR = (||p2 - p6|| + ||p3 - p5||) / (2 * ||p1 - p4||)

Where p1 to p6 are the eye's landmark points. When the eyes close, the EAR value decreases significantly. By monitoring this value, the system can detect when the eyes remain closed for too long, indicating drowsiness.

### Dlib and OpenCV

- **Dlib** is used for face landmark detection, which helps in locating the eyes.
- **OpenCV** captures the video feed from the camera and processes the frames in real-time.

### Drowsiness Detection

The system continuously monitors the EAR value. If it falls below a certain threshold (`EAR_THRESHOLD`) for a consecutive number of frames (`EAR_CONSEC_FRAMES`), the system triggers an alert, indicating that the driver may be drowsy.

## Model Details

- **Face Landmark Detection Model:** Dlib’s pre-trained model is used to detect facial landmarks.
- **Eye Aspect Ratio (EAR) Calculation:** A simple yet effective method to assess whether the eyes are open or closed.

## Results

The system performs well in detecting drowsiness under controlled conditions. It can successfully alert the driver if their eyes remain closed for too long, which is a strong indicator of drowsiness.

## Contributing

Contributions are welcome! If you have ideas to improve the system, such as integrating additional sensors or improving detection accuracy, feel free to fork the repository, make your changes, and submit a pull request.

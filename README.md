# Hand Tracking Volume Control

This project enables you to control your system's volume using hand gestures, by leveraging computer vision and the MediaPipe library. It detects your hand and the distance between your thumb and index finger to intuitively adjust the volume level.

---

## Features

* **Real-time Hand Tracking**: Uses MediaPipe to accurately detect and track hand landmarks.
* **Gesture-based Volume Control**: Adjusts system volume based on the distance between your thumb and index finger.
* **Visual Feedback**: Displays the current volume bar and percentage directly on the screen.
* **FPS Counter**: Shows the frames per second for real-time performance monitoring.

---

## Prerequisites

Before you get started, make sure you have the following installed:

* **Python 3.x**
* **pip** (Python package installer)

---

## Installation

1.  **Download the `main.py` file** from this repository.

2.  **Open your terminal or command prompt** and navigate to the directory where you saved `main.py`.

3.  **Install the required Python packages** by running:

    ```bash
    pip install opencv-python mediapipe numpy comtypes pycaw
    ```

---

## How to Run

1.  **Execute the `main.py` script** from your terminal:

    ```bash
    python main.py
    ```

2.  If prompted, **allow camera access** for the application.

3.  **Position your hand** clearly in front of your webcam.

4.  **Control the volume** by changing the distance between your thumb and index finger:
    * **Bringing your fingers closer** will **decrease** the volume.
    * **Extending your fingers further apart** will **increase** the volume.

5.  **Press the 'Q' key** on your keyboard to quit the application.

---

## How It Works

The script operates using these core components:

* **`cv2` (OpenCV)**: Handles video capture from your webcam, processes individual frames, and displays the visual output.
* **`mediapipe`**: Specifically, `mp.solutions.hands` is used to detect and identify key landmarks on your hand within the video feed.
* **`numpy`**: Provides numerical operations, particularly `np.interp`, which is essential for mapping the calculated finger distance to your system's actual volume range.
* **`pycaw`**: This Python library interfaces with the Windows audio API, allowing the script to control your system's master volume.

The main process flow is as follows:

1.  The script initializes your webcam and sets up the MediaPipe hand tracking model.
2.  It continuously captures video frames from the webcam.
3.  Each captured frame is processed by MediaPipe to detect any hands and their landmarks.
4.  If a hand is detected, the distance between the tip of your thumb (landmark index 4) and the tip of your index finger (landmark index 8) is calculated.
5.  This distance is then mapped to the system's volume range (typically 0% to 100%).
6.  Finally, `pycaw` is used to update the system volume to the new calculated level.
7.  The video feed also displays real-time visual cues, including a volume bar, percentage, and the application's frames per second (FPS).

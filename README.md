# Multiple-Human-Activity-Recognition
This project implements a real-time Human Activity Recognition (HAR) system using video input (webcam). It uses:

YOLOv8 for multi-person detection,

ONNX Runtime with a pretrained ResNet-34 (Kinetics) model for action classification,

OpenCV for video capture and rendering.

🛠️ Features

Real-time webcam-based activity detection

Multi-person tracking with per-person action prediction

Action labels displayed above each detected person

Efficient frame sampling for temporal activity analysis
 Requirements

Install the following dependencies:

pip install -r requirements.txt

Where requirements.txt includes:

opencv-python numpy onnxruntime ultralytics

🖥️ How It Works

The webcam feed is captured using OpenCV.

YOLOv8 detects persons in each frame.

Each detected person is cropped, resized, and added to a buffer.

Once 16 frames (SAMPLE_DURATION) are collected for a person:

A blob is constructed (video clip).

The ONNX model predicts the activity from the video clip.

Predicted actions are displayed directly above each person's head in the video.

📸 Sample Output

Person 1 → "Jumping" Person 2 → "Clapping"

🧠 Model Details

Action recognition model: ResNet-34 trained on Kinetics dataset

Input size: 16 frames × 112 × 112 (RGB)

Output: 400 activity classes

Detection model: YOLOv8 (person class)

📈 Performance Tips

Use a GPU-compatible ONNX Runtime (e.g., CUDAExecutionProvider)

Replace yolov8l.pt with yolov8s.pt or yolov8m.pt for better FPS

Use tracking (DeepSORT, ByteTrack) to maintain consistent person IDs

🎯 Future Improvements

Add DeepSORT tracking for stable person ID assignment

Enable user-defined recording and activity logging

Web dashboard to monitor live activity feed

Replace ResNet with a lightweight transformer (e.g., TimeSformer)

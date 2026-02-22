<div align="center">
  <h1>High-Tech Face Scanner</h1>
  <p><em>Real-time face tracking with blink detection, mouth openness, and head roll visualization</em></p>
  
  <!-- Labels -->
  <p>
    <img src="https://img.shields.io/badge/Python-3.8.10-blue.svg" alt="Python Version">
    <img src="https://img.shields.io/badge/MediaPipe-0.10.11-green.svg" alt="MediaPipe Version">
    <img src="https://img.shields.io/badge/OpenCV-4.11.0.86-orange.svg" alt="OpenCV Version">
    <img src="https://img.shields.io/badge/NumPy-1.24.4-purple.svg" alt="NumPy Version">
  </p>
  
</div>

---

## Overview

A real-time face scanning application that tracks and visualizes facial features with a cyberpunk aesthetic. The system detects and displays:

- **Eye blinks** with counter
- **Mouth openness** percentage
- **Head roll** angle visualization
- **Iris tracking**
- **Face wireframe overlay**
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/946247c9-4070-49b4-883d-c1eeaf43d7dd" />

## Features

| Feature | Description |
|---------|-------------|
| **Real-time Face Mesh** | 468 facial landmarks with wireframe overlay |
| **Blink Detection** | Tracks both eyes independently with counter |
| **Mouth Openness** | Visual indicator with percentage and dynamic circle |
| **Head Roll** | Visual line showing head tilt |
| **Eye Crops** | Live thumbnails of both eyes |
| **Iris Tracking** | Pupil position detection |
| **Cyberpunk UI** | Neon blue and yellow color scheme |

## Requirements

### Tested Environment (Working Configuration)
```bash
Python: 3.8.10
MediaPipe: 0.10.11
OpenCV: 4.11.0.86
NumPy: 1.24.4
```

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/4kaneli/face-scan.git
   cd face-scan
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the application**
   ```bash
   python scan.py
   ```

## Project Structure

```
face-scan/
├── scan.py                 # Main application file
├── README.md               # Documentation
├── requirements.txt        # Dependencies with exact versions
└── assets/                 # Demo videos/images
    └── demo.mp4               # Sample video input
```

## Usage

### Basic Commands
- Press `q` or `ESC` to quit
- Uses webcam by default (index 0)
- Can process video files by changing `CAM_INDEX`

### Customization Parameters

The code includes adjustable parameters for UI positioning:

| Parameter | Description | Default |
|-----------|-------------|---------|
| `TRACK_COLOR` | Wireframe color | Blue (255,0,0) |
| `TEXT_COLOR` | Text color | Yellow (0,255,255) |
| `BLINK_OFFSET_X/Y` | Blink counter position | 180, -50 |
| `MOUTH_CIRCLE_MAX` | Max mouth circle size | 50 |
| `EYE_OPEN_THRESHOLD` | Blink sensitivity | 0.28 |

## How It Works

1. **Face Detection**: MediaPipe FaceMesh detects 468 facial landmarks
2. **Eye Analysis**: Calculates Eye Aspect Ratio (EAR) for blink detection
   - `EAR = (|p2-p3| + |p5-p6|) / (2 * |p1-p4|)`
3. **Mouth Tracking**: Measures distance between upper and lower lip
4. **Head Pose**: Uses eye positions to determine head roll angle
5. **Visualization**: Overlays all data with customizable UI elements

## Configuration

### Change Input Source
```python
# For webcam (default)
CAM_INDEX = 0

# For video file
CAM_INDEX = "path/to/video.mp4"
```

### Adjust UI Elements
Modify the offset parameters in `scan.py` to reposition UI elements based on your screen/facial structure:

```python
# Example: Move blink counter to bottom right
BLINK_OFFSET_X = 300
BLINK_OFFSET_Y = 500
```

## Notes

- **Tested with**: Python 3.8.10, MediaPipe 0.10.11, OpenCV 4.11.0.86, NumPy 1.24.4
- Best performance in good lighting conditions
- Tested on:
  - CPU: i7-4810MQ
  - RAM: 8GB
  - Camera: 720p
  - FPS: 28–32
- UI elements are fully customizable via offset parameters

## Known Issues & Solutions

| Issue | Solution |
|-------|----------|
| Camera not opening | Check CAM_INDEX value (0 for built-in, 1 for external) |
| Low FPS | Reduce FRAME_W/FRAME_H values |
| Inaccurate blink detection | Adjust EYE_OPEN_THRESHOLD (0.2-0.3 range) |

## Contributing
Contributions are welcome! Feel free to:
- **Report bugs**
- **Suggest features**
- **Submit pull requests**

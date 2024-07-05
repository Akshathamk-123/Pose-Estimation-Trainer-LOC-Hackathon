# Pose Estimation with MediaPipe and OpenCV

This is a project that was done as a part of a 24-hour hackathon called LOC-Samarpana

This project demonstrates the use of MediaPipe and OpenCV to perform pose estimation and calculate angles between key body points. The implementation includes functions to find and draw poses, identify key landmarks, and compute angles for fitness or motion analysis purposes.

## Requirements

- Python 3.x
- OpenCV
- MediaPipe
- NumPy

## Installation

1. Clone the repository or download the code files.
2. Install the required libraries using pip:

```bash
pip install opencv-python mediapipe numpy
```

## Usage

The script captures video input and processes it to detect poses and calculate angles between specified landmarks. Follow the steps below to run the script.

### Code Overview

The script consists of several functions:

1. **findPose**: Detects and draws the pose landmarks on the image.
2. **findPosition**: Finds and returns the positions of landmarks.
3. **findAngle**: Calculates the angle between three landmarks.

### Functions

#### `findPose(img, draw=True)`

This function takes an image as input, processes it to detect pose landmarks, and optionally draws the landmarks on the image.

- `img`: Input image.
- `draw`: Boolean flag to draw landmarks on the image.

Returns the processed image with landmarks drawn.

#### `findPosition(img, draw=True)`

This function finds and returns the positions of the detected landmarks.

- `img`: Input image.
- `draw`: Boolean flag to draw circles on the detected landmarks.

Returns a list of landmark positions.

#### `findAngle(img, p1, p2, p3, draw=True)`

This function calculates the angle between three specified landmarks.

- `img`: Input image.
- `p1`, `p2`, `p3`: Landmark indices.
- `draw`: Boolean flag to draw the angle and related lines/circles on the image.

Returns the calculated angle.

### Main Function

The `main` function captures video input, processes each frame to detect poses, calculates angles between landmarks, and displays the results. It also tracks and visualizes the count of repetitions for a specified motion (e.g., dumbbell curls).

#### Running the Script

To run the script, execute the following command:

```bash
python script_name.py
```

Replace `script_name.py` with the name of your script file.

### Example Output

The script displays the processed video frames with pose landmarks, angle calculations, and a repetition count visualized on the screen.

## Customization

You can customize the script for different use cases by modifying the landmarks used for angle calculation and adjusting the motion detection logic in the `main` function.

### Example Usage in `main`

The `main` function demonstrates how to use the provided functions to process a video file (`a_t.mp4`) and display the pose estimation and angle calculation results. Modify the video file path or capture device as needed.

## Acknowledgements

- [MediaPipe](https://mediapipe.dev)
- [OpenCV](https://opencv.org)

Feel free to contribute to this project by opening issues or submitting pull requests on the repository.

---

## Certificate of Participation
![LOC](https://github.com/Akshathamk-123/AI-Trainer-OpenCV/assets/92522733/becf9341-72e2-4fb2-b659-f9d3a3a94078)


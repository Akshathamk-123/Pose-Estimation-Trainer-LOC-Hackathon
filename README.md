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

```python
def main():
    cap = cv2.VideoCapture('a_t.mp4')  # Replace with your video file or capture device
    pTime = 0
    dir = 0
    count = 0

    while True:
        success, img = cap.read()
        if not success:
            break
        img = cv2.resize(img, (1280, 720))
        img = findPose(img, False)
        lmList = findPosition(img)
        if len(lmList) != 0:
            angle = findAngle(img, 12, 14, 16, False)
            per = np.interp(angle, (210, 310), (0, 100))
            bar = np.interp(angle, (220, 310), (650, 100))

            color = (255, 0, 255)
            if per == 100:
                color = (0, 255, 0)
                if dir == 0:
                    count += 0.5
                    dir = 1
            if per == 0:
                color = (0, 255, 0)
                if dir == 1:
                    count += 0.5
                    dir = 0

            cv2.rectangle(img, (1100, 100), (1175, 650), color, 3)
            cv2.rectangle(img, (1100, int(bar)), (1175, 650), color, cv2.FILLED)
            cv2.putText(img, f'{int(per)} %', (1100, 75), cv2.FONT_HERSHEY_PLAIN, 4, color, 4)
            cv2.rectangle(img, (0, 450), (250, 720), (0, 255, 0), cv2.FILLED)
            cv2.putText(img, str(int(count)), (45, 670), cv2.FONT_HERSHEY_PLAIN, 15, (255, 0, 0), 25)

        cTime = time.time()
        fps = 1 / (cTime - pTime)
        pTime = cTime
        cv2.putText(img, str(int(fps)), (50, 100), cv2.FONT_HERSHEY_PLAIN, 5, (255, 0, 0), 5)

        cv2.imshow("Image", img)
        cv2.waitKey(1)

main()
```

## License

This project is licensed under the MIT License.

## Acknowledgements

- [MediaPipe](https://mediapipe.dev)
- [OpenCV](https://opencv.org)

Feel free to contribute to this project by opening issues or submitting pull requests on the repository.

---

## Certificate of Participation
![LOC](https://github.com/Akshathamk-123/AI-Trainer-OpenCV/assets/92522733/becf9341-72e2-4fb2-b659-f9d3a3a94078)


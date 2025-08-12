# 📹 Object Detection and Tracking in Videos

This project demonstrates background subtraction-based object detection and tracking in videos using Python, OpenCV, and NumPy.

It processes a video file, identifies moving objects by calculating a static background and removing it, and then draws bounding boxes around these objects in each frame.

***

## ✨ Features

- **Dynamic Background Modeling**: Calculates a median frame from random samples to create a robust static background model.
- **Background Subtraction**: Uses absolute difference to isolate moving foreground objects from the static background.
- **Noise Reduction**: Applies a Gaussian Blur to smooth the difference image and reduce false positives.
- **Clear Segmentation**: Uses Otsu's Binarization to automatically find the optimal threshold value and create a clean black-and-white mask of the objects.
- **Contour Detection**: Identifies the outlines of all segmented objects.
- **Object Tracking**: Draws bounding boxes around detected contours on the original video frames.
- **Video Output**: Compiles the processed frames into a new video file.

***

## 🛠️ Technologies Used

-   Python 3.8+
-   OpenCV
-   NumPy
-   Matplotlib (for visualization within the notebook)

***

## ⚙️ Installation

1.  **Clone the repository:**
    ```bash
    
    cd object_tracking
    ```

2.  **Install the required libraries:**
    ```bash
    pip install opencv-python numpy matplotlib
    ```

***

## ▶️ Usage

1.  Place your input video file inside the `Media/` folder.
2.  Open the Jupyter Notebook and **update the video file path** in the cell where the video is loaded.
    ```python
    # Find this line and change 'your_video.mp4' to your file's name
    cap = cv2.VideoCapture('Media/your_video.mp4')
    ```
3.  Run all cells in the notebook in order.
4.  The output video will be generated in the root directory as **`Detect.avi`**.

***

## 📊 How It Works

1.  **Frame Sampling**: The script first captures 30 random frames from the input video.
2.  **Median Frame Calculation**: It computes the median of these frames to generate a single, static background image.
3.  **Processing Loop**: The script then iterates through every frame of the video from the beginning.
4.  **Difference & Thresholding**: For each frame, it calculates the absolute difference between the frame and the median background, blurs the result, and applies Otsu's threshold to create a binary mask.
5.  **Contour & Bounding Box**: It finds the contours in the binary mask and draws a purple bounding box around each detected contour.
6.  **Video Compilation**: Each processed frame is written to the `Detect.avi` output file.

# 📹 Object Detection and Tracking in Videos

This project demonstrates background subtraction-based object detection and tracking in videos using Python, OpenCV, and NumPy.

It processes a video file (`vtest.avi`), identifies moving objects by calculating a static background and removing it, and then draws bounding boxes around these objects in each frame. The final processed video is saved as `Detect.avi`.

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
    git clone <your-repo-url>
    cd object_tracking
    ```

2.  **Install the required libraries:**
    ```bash
    pip install opencv-python numpy matplotlib
    ```

***

## ▶️ Usage

1.  Make sure the sample video `vtest.avi` is placed inside the `Media/` folder.
2.  Open and run the Jupyter Notebook:
    ```bash
    jupyter notebook "Object detection and tracking in videos.ipynb"
    ```
3.  Execute all the cells in order. The script will process the input video and save the result.
4.  The output video will be generated in the root directory as **`Detect.avi`**.

***

## 📊 How It Works

1.  **Frame Sampling**: The script first captures 30 random frames from `vtest.avi`.
2.  **Median Frame Calculation**: It computes the median of these frames to generate a single, static background image. This method is effective at removing objects that may have been present in some of the sampled frames.
3.  **Processing Loop**: The script then iterates through every frame of the video from the beginning.
4.  **Difference & Thresholding**: For each frame, it calculates the absolute difference between the frame and the median background, blurs the result to reduce noise, and applies Otsu's threshold to create a binary mask.
5.  **Contour & Bounding Box**: It finds the contours in the binary mask and draws a purple bounding box around each detected contour on the original color frame.
6.  **Video Compilation**: Each processed frame with bounding boxes is written to the `Detect.avi` output file.

# Image Segmentation Using Thresholding Techniques in OpenCV

## Aim

To segment an image using Global Thresholding, Adaptive Thresholding, and Otsu's Thresholding techniques using Python and OpenCV.

The program performs the following operations:

- Global Thresholding
- Adaptive Thresholding
- Otsu's Thresholding

## Software Used

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (cv2)
- NumPy
- Matplotlib

## Algorithm

### Step 1:

Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:

Load the input image using OpenCV.

### Step 3:

Convert the input image into grayscale format.

### Step 4: Global Thresholding

- Select a fixed threshold value.
- Apply thresholding to separate foreground and background pixels.
- Display the thresholded image.

### Step 5: Adaptive Thresholding

- Compute threshold values for small regions of the image.
- Apply Adaptive Mean Thresholding.
- Apply Adaptive Gaussian Thresholding.
- Display the segmented images.

### Step 6: Otsu's Thresholding

- Automatically determine the optimal threshold value.
- Apply Otsu's thresholding technique.
- Display the segmented image.

### Step 7:

Compare the results obtained from Global, Adaptive, and Otsu's thresholding methods.

## Program

```

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Load the input image
img = cv2.imread('rabbit.jpg')

if img is None:
    print("Error: Image not found")
else:
    # Step 2: Convert image to grayscale
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

    # Step 3: Global Thresholding
    ret, global_thresh = cv2.threshold(
        gray, 127, 255, cv2.THRESH_BINARY
    )

    # Step 4: Adaptive Mean Thresholding
    adaptive_mean = cv2.adaptiveThreshold(
        gray, 255,
        cv2.ADAPTIVE_THRESH_MEAN_C,
        cv2.THRESH_BINARY,
        11, 2
    )

    # Step 5: Adaptive Gaussian Thresholding
    adaptive_gaussian = cv2.adaptiveThreshold(
        gray, 255,
        cv2.ADAPTIVE_THRESH_GAUSSIAN_C,
        cv2.THRESH_BINARY,
        11, 2
    )

    # Step 6: Otsu's Thresholding
    otsu_value, otsu_thresh = cv2.threshold(
        gray, 0, 255,
        cv2.THRESH_BINARY + cv2.THRESH_OTSU
    )

    # Step 7: Display all results
    titles = [
        'Original Image',
        'Grayscale Image',
        'Global Thresholding',
        'Adaptive Mean Thresholding',
        'Adaptive Gaussian Thresholding',
        "Otsu's Thresholding"
    ]

    images = [
        cv2.cvtColor(img, cv2.COLOR_BGR2RGB),
        gray,
        global_thresh,
        adaptive_mean,
        adaptive_gaussian,
        otsu_thresh
    ]

    plt.figure(figsize=(12, 8))

    for i in range(6):
        plt.subplot(2, 3, i + 1)
        plt.imshow(images[i], cmap='gray' if i != 0 else None)
        plt.title(titles[i])
        plt.axis('off')

    plt.tight_layout()
    plt.show()

    print("Global Threshold Value:", ret)
    print("Otsu Threshold Value:", otsu_value)

```
## Developed By
# Name: Vijiyalakshmi A
# Register No: 212225240185

## Output

### Original Grayscale Image

- The grayscale version of the input image is displayed.
- Serves as the input for thresholding operations.

<img width="312" height="420" alt="image" src="https://github.com/user-attachments/assets/35a9e1f5-81e2-406f-8be8-8efabcbbad91" /><img width="325" height="420" alt="image" src="https://github.com/user-attachments/assets/0c4e6ef6-eb95-4d6e-9453-92e728b814fc" />


### Global Thresholding

- Original image is displayed.
- Thresholded image is displayed.
- A fixed threshold value is used for segmentation.
- Pixels are classified as foreground or background.

<img width="312" height="420" alt="image" src="https://github.com/user-attachments/assets/35a9e1f5-81e2-406f-8be8-8efabcbbad91" /><img width="291" height="420" alt="image" src="https://github.com/user-attachments/assets/6f78cfe6-968f-4ae5-a327-29c19e5723b6" />


### Adaptive Thresholding

- Original image is displayed.
- Adaptive Mean Thresholded image is displayed.
- Adaptive Gaussian Thresholded image is displayed.
- Threshold values vary across different regions of the image.
- Suitable for images with uneven illumination.

<img width="312" height="420" alt="image" src="https://github.com/user-attachments/assets/35a9e1f5-81e2-406f-8be8-8efabcbbad91" /><img width="315" height="416" alt="image" src="https://github.com/user-attachments/assets/e23b39e0-efe0-4e5f-81b5-73781beb381a" /><img width="340" height="426" alt="image" src="https://github.com/user-attachments/assets/6227b377-0ed0-4bd2-a075-7fc303ecc790" />


### Otsu's Thresholding

- Original image is displayed.
- Otsu segmented image is displayed.
- Optimal threshold value is calculated automatically.
- Produces improved segmentation for bimodal histograms.

<img width="312" height="420" alt="image" src="https://github.com/user-attachments/assets/35a9e1f5-81e2-406f-8be8-8efabcbbad91" /><img width="301" height="417" alt="image" src="https://github.com/user-attachments/assets/dce5aa2a-d34e-4d5b-a154-265b5f4ea6aa" />


## Result
Thus, image segmentation is successfully performed using **Global Thresholding, Adaptive Thresholding, and Otsu's Thresholding** techniques in OpenCV. 

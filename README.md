# EXP 5 - IMAGE SMOOTHENING AND SHARPENING USING OPEN CV

## Aim:

To write a Python program using OpenCV to apply different smoothing filters (Averaging, Weighted Averaging, Gaussian, Median) and sharpening filters (Laplacian Kernel and Laplacian Operator) for image enhancement, and display each result separately along with the original image for comparison.

---

## The program performs the following operations:

- Read and display an input image  
- Apply Averaging filter  
- Apply Weighted Averaging filter  
- Apply Gaussian filter  
- Apply Median filter  
- Apply Laplacian sharpening using kernel  
- Apply Laplacian operator  
- Display all outputs for comparison  

---

##  Software Used:

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

##  Algorithm:

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image (e.g., `image.jpg`).

### Step 3:
Convert the image from BGR to RGB format for display.

### Step 4:
Apply Averaging Filter using `cv2.blur()`.

### Step 5:
Apply Weighted Averaging Filter using a custom kernel with `cv2.filter2D()`.

### Step 6:
Apply Gaussian Filter using `cv2.GaussianBlur()`.

### Step 7:
Apply Median Filter using `cv2.medianBlur()`.

### Step 8:
Apply Laplacian Sharpening using Kernel with `cv2.filter2D()`.

### Step 9:
Convert image to grayscale and apply Laplacian Operator using `cv2.Laplacian()`.

### Step 10:
Display all filtered images using a grid layout for comparison.

---

##  Developed By:

**Name:** R P Loshini<br>
**Register No:** 212225230155 

## Program:

```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 2: Read the input image
image_path = r"C:\Users\acer\DIPT\dog.jpg"
img_bgr = cv2.imread(image_path)

# Step 3: Convert the image from BGR to RGB format for display
img_rgb = cv2.cvtColor(img_bgr, cv2.COLOR_BGR2RGB)

# Step 4: Apply Averaging Filter using cv2.blur()
avg_blur = cv2.blur(img_rgb, (5, 5))

plt.figure(figsize=(10, 4))
plt.subplot(1, 2, 1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(avg_blur)
plt.title("Step 4: Averaging Filter")
plt.axis('off')
plt.show()

# Step 5: Apply Weighted Averaging Filter using a custom kernel with cv2.filter2D()
weighted_kernel = np.array([
    [1, 2, 1],
    [2, 4, 2],
    [1, 2, 1]
], dtype=np.float32) / 16.0

weighted_blur = cv2.filter2D(img_rgb, -1, weighted_kernel)

plt.figure(figsize=(10, 4))
plt.subplot(1, 2, 1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(weighted_blur)
plt.title("Step 5: Weighted Averaging Filter")
plt.axis('off')
plt.show()

# Step 6: Apply Gaussian Filter using cv2.GaussianBlur()
gaussian_blur = cv2.GaussianBlur(img_rgb, (5, 5), 0)

plt.figure(figsize=(10, 4))
plt.subplot(1, 2, 1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(gaussian_blur)
plt.title("Step 6: Gaussian Filter")
plt.axis('off')
plt.show()

# Step 7: Apply Median Filter using cv2.medianBlur()
median_blur = cv2.medianBlur(img_rgb, 5)

plt.figure(figsize=(10, 4))
plt.subplot(1, 2, 1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(median_blur)
plt.title("Step 7: Median Filter")
plt.axis('off')
plt.show()

# Step 8: Apply Laplacian Sharpening using Kernel with cv2.filter2D()
sharpen_kernel = np.array([
    [ 0, -1,  0],
    [-1,  5, -1],
    [ 0, -1,  0]
], dtype=np.float32)

sharpened_img = cv2.filter2D(img_rgb, -1, sharpen_kernel)

plt.figure(figsize=(10, 4))
plt.subplot(1, 2, 1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(sharpened_img)
plt.title("Step 8: Laplacian Sharpening (Kernel)")
plt.axis('off')
plt.show()

# Step 9: Convert image to grayscale and apply Laplacian Operator using cv2.Laplacian()
gray_img = cv2.cvtColor(img_bgr, cv2.COLOR_BGR2GRAY)
laplacian = cv2.Laplacian(gray_img, cv2.CV_64F)
laplacian_abs = cv2.convertScaleAbs(laplacian, alpha=3.0)  # Enhanced contrast for visible edges

plt.figure(figsize=(10, 4))
plt.subplot(1, 2, 1)
plt.imshow(gray_img, cmap='gray')
plt.title("Original Grayscale Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(laplacian_abs, cmap='gray')
plt.title("Step 9: Laplacian Operator (Grayscale Edges)")
plt.axis('off')
plt.show()

# Step 10: Display all filtered images using a grid layout for comparison
fig, axes = plt.subplots(2, 4, figsize=(16, 8))

# 1. Original Image
axes[0, 0].imshow(img_rgb)
axes[0, 0].set_title("1. Original Image")
axes[0, 0].axis('off')

# 2. Averaging Filter
axes[0, 1].imshow(avg_blur)
axes[0, 1].set_title("2. Averaging Filter")
axes[0, 1].axis('off')

# 3. Weighted Averaging Filter
axes[0, 2].imshow(weighted_blur)
axes[0, 2].set_title("3. Weighted Averaging")
axes[0, 2].axis('off')

# 4. Gaussian Filter
axes[0, 3].imshow(gaussian_blur)
axes[0, 3].set_title("4. Gaussian Filter")
axes[0, 3].axis('off')

# 5. Median Filter
axes[1, 0].imshow(median_blur)
axes[1, 0].set_title("5. Median Filter")
axes[1, 0].axis('off')

# 6. Laplacian Sharpening Kernel
axes[1, 1].imshow(sharpened_img)
axes[1, 1].set_title("6. Laplacian Sharpening")
axes[1, 1].axis('off')

# 7. Laplacian Operator
axes[1, 2].imshow(laplacian_abs, cmap='gray')
axes[1, 2].set_title("7. Laplacian Operator")
axes[1, 2].axis('off')

# Hide 8th subplot frame
axes[1, 3].axis('off')

plt.tight_layout()
plt.show()
```

---

##  Output:

### Smoothing Filters

- Averaging filter produces blurred image  
- Weighted averaging provides smoother result with less distortion  
- Gaussian filter preserves edges better while reducing noise  
- Median filter removes salt-and-pepper noise effectively  

###  Sharpening Filters

- Laplacian kernel enhances edges and fine details  
- Laplacian operator detects edges clearly in grayscale  

<img width="1058" height="563" alt="image" src="https://github.com/user-attachments/assets/5fc8daa3-d1be-4b05-b9ae-c2d79854c760" />


---

##  Result:

Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.

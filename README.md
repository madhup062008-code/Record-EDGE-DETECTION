# Record-EDGE-DETECTION-edge-detection-opencv-

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---

## Program
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read image
img = cv2.imread("image.jpg")

if img is None:
    print("Image not found!")
    exit()

# Convert to RGB and Grayscale
rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# Sobel
sobelx = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=3)
sobely = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=3)
sobel = cv2.magnitude(sobelx, sobely)
sobel = np.uint8(sobel)

# Prewitt
kernelx = np.array([[1,0,-1],
                    [1,0,-1],
                    [1,0,-1]])

kernely = np.array([[1,1,1],
                    [0,0,0],
                    [-1,-1,-1]])

prewittx = cv2.filter2D(gray, -1, kernelx)
prewitty = cv2.filter2D(gray, -1, kernely)
prewitt = cv2.addWeighted(prewittx, 0.5, prewitty, 0.5, 0)

# Roberts
kernelx = np.array([[1,0],
                    [0,-1]])

kernely = np.array([[0,1],
                    [-1,0]])

robertsx = cv2.filter2D(gray, -1, kernelx)
robertsy = cv2.filter2D(gray, -1, kernely)
roberts = cv2.addWeighted(robertsx, 0.5, robertsy, 0.5, 0)

# Laplacian
laplacian = cv2.Laplacian(gray, cv2.CV_64F)
laplacian = np.uint8(np.absolute(laplacian))

# Canny
canny = cv2.Canny(gray, 100, 200)

# Display Images
plt.figure(figsize=(15,10))

plt.subplot(2,3,1)
plt.imshow(rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(2,3,2)
plt.imshow(sobel, cmap="gray")
plt.title("Sobel")
plt.axis("off")

plt.subplot(2,3,3)
plt.imshow(prewitt, cmap="gray")
plt.title("Prewitt")
plt.axis("off")

plt.subplot(2,3,4)
plt.imshow(roberts, cmap="gray")
plt.title("Roberts")
plt.axis("off")

plt.subplot(2,3,5)
plt.imshow(laplacian, cmap="gray")
plt.title("Laplacian")
plt.axis("off")

plt.subplot(2,3,6)
plt.imshow(canny, cmap="gray")
plt.title("Canny")
plt.axis("off")

plt.tight_layout()
plt.show()
```

## Developed By

- **Name: MADHU .P**
- **Register No: 212225040215** 

---

## Output
<img width="346" height="516" alt="image" src="https://github.com/user-attachments/assets/5d4b82de-69fa-4b8a-9204-609604723513" />

###  Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map
<img width="361" height="513" alt="image" src="https://github.com/user-attachments/assets/ec922cec-99d0-4329-a748-e48deedab67f" />

###  Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges  
<img width="338" height="515" alt="image" src="https://github.com/user-attachments/assets/12855d8a-d0db-4e66-bde0-f8aecd1526d4" />

###  Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise  
<img width="348" height="520" alt="image" src="https://github.com/user-attachments/assets/ab54f33f-f17f-4aca-a07d-7ac3299645c1" />

###  Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes  
<img width="347" height="522" alt="image" src="https://github.com/user-attachments/assets/dc89b77a-b92a-4800-9762-2ed55f21697c" />

###  Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges  
<img width="341" height="512" alt="image" src="https://github.com/user-attachments/assets/c1b613b9-8ef0-4d1c-91c1-2948bcd0791a" />

---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.

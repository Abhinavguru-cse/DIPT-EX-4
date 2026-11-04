# DIPT-EX-4
# Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---

##  Program

### Developed By:
**Name:** T.Goshanrajan

### Register No:
212225040098

---
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the image
img = cv2.imread("car.jpg")

if img is None:
    print("Image not found!")
    exit()
# Convert BGR to RGB for Matplotlib
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

height, width = img.shape[:2]

# ----------------------------------------------------
# Image Translation
# ----------------------------------------------------
translation_matrix = np.float32([[1, 0, 50],
                                 [0, 1, 80]])

translated = cv2.warpAffine(img_rgb, translation_matrix, (width, height))

plt.figure(figsize=(10,5))

plt.subplot(1,2,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(translated)
plt.title("Translated Image")
plt.axis("off")

plt.show()

# ----------------------------------------------------
# Image Scaling
# ----------------------------------------------------
downscaled = cv2.resize(img_rgb, None, fx=0.5, fy=0.5)

upscaled = cv2.resize(img_rgb, None, fx=2, fy=2)

plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(img_rgb)
plt.title("Original")

plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(downscaled)
plt.title("Downscaled (0.5x)")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(upscaled)
plt.title("Upscaled (2x)")
plt.axis("off")

plt.show()

# ----------------------------------------------------
# Image Shearing
# ----------------------------------------------------
horizontal_matrix = np.float32([[1,0.5,0],
                                [0,1,0]])

vertical_matrix = np.float32([[1,0,0],
                              [0.5,1,0]])

horizontal = cv2.warpAffine(img_rgb, horizontal_matrix, (width+200,height))

vertical = cv2.warpAffine(img_rgb, vertical_matrix, (width,height+200))

plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(img_rgb)
plt.title("Original")

plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(horizontal)
plt.title("Horizontal Shearing")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(vertical)
plt.title("Vertical Shearing")
plt.axis("off")

plt.show()

# ----------------------------------------------------
# Image Reflection
# ----------------------------------------------------
horizontal_flip = cv2.flip(img_rgb,1)

vertical_flip = cv2.flip(img_rgb,0)

both_flip = cv2.flip(img_rgb,-1)

plt.figure(figsize=(10,10))

plt.subplot(2,2,1)
plt.imshow(img_rgb)
plt.title("Original")
plt.axis("off")

plt.subplot(2,2,2)
plt.imshow(horizontal_flip)
plt.title("Horizontal Reflection")
plt.axis("off")

plt.subplot(2,2,3)
plt.imshow(vertical_flip)
plt.title("Vertical Reflection")
plt.axis("off")

plt.subplot(2,2,4)
plt.imshow(both_flip)
plt.title("Both-axis Reflection")
plt.axis("off")

plt.show()

# ----------------------------------------------------
# Image Rotation
# ----------------------------------------------------
center = (width//2, height//2)

rotation45 = cv2.getRotationMatrix2D(center,45,1)

rotation90 = cv2.getRotationMatrix2D(center,90,1)

rotated45 = cv2.warpAffine(img_rgb,rotation45,(width,height))

rotated90 = cv2.warpAffine(img_rgb,rotation90,(width,height))

plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(img_rgb)
plt.title("Original")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(rotated45)
plt.title("45° Rotation")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(rotated90)
plt.title("90° Rotation")
plt.axis("off")

plt.show()
```


##  Output

### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed

<img width="795" height="239" alt="image" src="https://github.com/user-attachments/assets/0d2ca20c-39b0-41ba-ae4b-622cc5a6ed89" />


### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed  


<img width="1182" height="234" alt="image" src="https://github.com/user-attachments/assets/1ca0d6db-9dac-49bb-ab54-e8d8aa02f08d" />


### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed  


<img width="1182" height="348" alt="image" src="https://github.com/user-attachments/assets/fb164c74-c4aa-4c2a-927d-7229b58e294d" />


### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed  


<img width="795" height="659" alt="image" src="https://github.com/user-attachments/assets/8df581fd-21eb-474e-b93b-40433c445c33" />


### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed


<img width="1182" height="233" alt="image" src="https://github.com/user-attachments/assets/732788d4-e74d-473f-9e1c-8aed1b30134d" />


---



##  Result



Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.

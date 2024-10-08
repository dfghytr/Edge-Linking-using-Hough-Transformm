# Edge-Linking-using-Hough-Transformm
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:
Import all the necessary modules for the program.
### Step2:
Load a image using imread() from cv2 module.
### Step3:
Convert the image to grayscale.
### Step4:
Using Canny operator from cv2,detect the edges of the image.
### Step5:
Using the HoughLinesP(),detect line co-ordinates for every points in the images.Using For loop,draw the lines on the found co-ordinates.Display the image.

## PROGRAM:
### Input image and grayscale image
```
import numpy as np
import cv2
import matplotlib.pyplot as plt
gray_img = cv2.imread('IMAGE2.webp', cv2.IMREAD_GRAYSCALE)
img_c = cv2.imread('IMAGE2.webp', cv2.IMREAD_COLOR)
img_c = cv2.cvtColor(img_c, cv2.COLOR_BGR2RGB)
gray_rgb = cv2.cvtColor(gray_img, cv2.COLOR_GRAY2RGB)
gray = cv2.GaussianBlur(gray_img, (3, 3), 0)
plt.figure(figsize=(13, 13))
plt.subplot(1, 2, 1)
plt.imshow(img_c)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(gray, cmap='gray')
plt.title("Gray Image")
plt.axis("off")
plt.show()

```

### Canny Edge detector output
```
canny = cv2.Canny(gray, 120, 150)
plt.imshow(canny, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis("off")
plt.show()
```
### Hough Line Transform
```
lines = cv2.HoughLinesP(canny, 1, np.pi/180, threshold=80, minLineLength=50, maxLineGap=250)
for line in lines:
    x1, y1, x2, y2 = line[0]
    cv2.line(img_c, (x1, y1), (x2, y2), (255, 0, 0), 3)
plt.imshow(img_c)
plt.title("Result Image with Hough Transform")
plt.axis("off")
plt.show()
```
## Output
### Input image and grayscale image
![Screenshot 2024-10-03 153247](https://github.com/user-attachments/assets/78036150-365a-4d6a-b633-9371f8a609ad)


### Canny Edge detector output
![Screenshot 2024-10-03 153340](https://github.com/user-attachments/assets/9917c1ba-9497-4c50-b5a3-cf9d27e683e8)


### Display the result of Hough transform
![Screenshot 2024-10-03 153429](https://github.com/user-attachments/assets/5e269832-53d1-438b-9645-2b91528c8d1b)


## RESULT:
Thus, the program to detect the lines using Hough Transform implemented successfully.

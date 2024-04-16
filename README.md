# EX-7 Edge Linking using Hough Transform
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

### PROGRAM
```python
import numpy as np
import cv2
import matplotlib.pyplot as plt
img=cv2.imread("ex7.jpg",0)
img_c=cv2.imread("ex7.jpg",1)
img_c=cv2.cvtColor(img_c,cv2.COLOR_BGR2RGB)
gray=cv2.cvtColor(img,cv2.COLOR_GRAY2RGB)
gray = cv2.GaussianBlur(gray,(3,3),0)
plt.figure(figsize=(13,13))
plt.subplot(1,2,1)
plt.imshow(img_c)
plt.title("Original Image")
plt.axis("off")
plt.subplot(1,2,2)
plt.imshow(gray)
plt.title("Gray Image")
plt.axis("off")
plt.show()
# Find the edges in the image using canny detector and display
canny=cv2.Canny(gray,120,110)
plt.imshow(canny)
plt.title("Canny Edge Detector")
plt.axis("off")
plt.show()
# Detect points that form a line using HoughLinesP
lines=cv2.HoughLinesP(canny,1,np.pi/180,threshold=80,minLineLength=50,maxLineGap=250)
# Draw lines on the image
for line in lines:
    x1,y1,x2,y2=line[0]
    cv2.line(img_c,(x1,y1),(x2,y2),(255,0,0),3)
# Display the result
plt.imshow(img_c)
plt.title("Result Image")
plt.axis("off")
plt.show()
```
## Output

### Input image and grayscale image
![image](https://github.com/SandhiyaR1/Edge-Linking-using-Hough-Transformm/assets/113497571/d099cdf4-98cb-46bd-a4e4-29215d09b145)

### Canny Edge detector output
![image](https://github.com/SandhiyaR1/Edge-Linking-using-Hough-Transformm/assets/113497571/b623ae2f-b668-4720-a449-4dee1f297f75)

### Display the result of Hough transform
![image](https://github.com/SandhiyaR1/Edge-Linking-using-Hough-Transformm/assets/113497571/5ca5ca82-9a41-47e7-a2bb-63fcc63c659f)

## Result
Thus the program is written with Python and OpenCV to detect lines using Hough transform.

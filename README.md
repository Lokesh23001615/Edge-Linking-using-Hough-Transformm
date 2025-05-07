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
## Program 
```
Developed by : Lokesh M
Reister Number : 212223230114
```
### Loading the Image
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
image = cv2.imread('cow.jpg') 
plt.subplot(1,1 , 1)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Input Image')
plt.axis('on')
```
### Gray scale Image
```python
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
plt.subplot(1,1,1)
plt.imshow(gray_image, cmap='gray')
plt.title('Grayscale Image')
plt.axis('on')
```
### Canny Edge Detector
```python
edges = cv2.Canny(gray_image, 50, 150, apertureSize=3)
plt.subplot(1,1,1)
plt.imshow(edges, cmap='gray')
plt.title('Canny Edge Detector Output')
plt.axis('on')
```
### Hough Transform
```python
lines = cv2.HoughLinesP(edges, rho=1, theta=np.pi/180, threshold=100, minLineLength=50, maxLineGap=10)
output_image = image.copy()
if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(output_image, (x1, y1), (x2, y2), (0, 255, 0), 2)
plt.subplot(1,1,1)
plt.imshow(cv2.cvtColor(output_image, cv2.COLOR_BGR2RGB))
plt.title('Hough Transform - Line Detection')
plt.axis('on')
```
## Output

### Input image and grayscale image
![image](https://github.com/user-attachments/assets/fc7c6e33-f736-410b-85df-884a35ffe6c6)
![image](https://github.com/user-attachments/assets/f9f5feef-dfbf-4552-a996-c807fefb5ab2)


### Canny Edge detector output
![image](https://github.com/user-attachments/assets/199ffe2f-b88e-4aba-abd1-4c278dd150dc)



### Result of Hough transform
![image](https://github.com/user-attachments/assets/aa7617a6-59fe-485a-8745-c711fd6daea1)

## Result 
Hence lines are detected using canny edge detector and hough transform.

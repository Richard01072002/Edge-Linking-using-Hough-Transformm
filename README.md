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
## program: 
```
#name-RICHARDSON A
#RegNo. - 212222233005
import cv2
import numpy as np
import matplotlib.pyplot as plt
image = cv2.imread('HappyFish.jpg')  # Replace with your image path
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
edges = cv2.Canny(gray_image, 50, 150, apertureSize=3)

# Detect lines using the probabilistic Hough transform
lines = cv2.HoughLinesP(edges, rho=1, theta=np.pi/180, threshold=100, minLineLength=50, maxLineGap=10)
# Draw the lines on the original image
output_image = image.copy()
if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(output_image, (x1, y1), (x2, y2), (0, 255, 0), 2)

# Displaying results using Matplotlib
plt.figure(figsize=(12, 12))

# Input Image and Grayscale Image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Input Image')
plt.axis('off')

plt.imshow(gray_image, cmap='gray')
plt.title('Grayscale Image')
plt.axis('off')

# Canny Edge Detection Output
plt.imshow(edges, cmap='gray')
plt.title('Canny Edge Detector Output')
plt.axis('off')

# Hough Transform Result
plt.imshow(cv2.cvtColor(output_image, cv2.COLOR_BGR2RGB))
plt.title('Hough Transform - Line Detection')
plt.axis('off')

# Display all results
plt.show()
```

## Output

### orignal image:
<img width="944" alt="Screenshot 2024-10-16 at 5 02 59 PM" src="https://github.com/user-attachments/assets/0a588c2f-e2c3-4ba4-a6f7-86c2b4692b5b">

### Input image and grayscale image
<img width="512" alt="Screenshot 2024-10-16 at 5 03 23 PM" src="https://github.com/user-attachments/assets/c1e93c79-54e5-4991-9fed-2379a6a09110">

### Canny Edge detector output

<img width="517" alt="Screenshot 2024-10-16 at 5 05 21 PM" src="https://github.com/user-attachments/assets/87825b11-3c9e-442e-a9a9-a1d807f8ab97">


### Display the result of Hough transform

<img width="537" alt="Screenshot 2024-10-16 at 5 04 03 PM" src="https://github.com/user-attachments/assets/cfb9107b-a207-4007-92b7-396ba5802182">

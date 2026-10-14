# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** LOHINI S  
- **Register Number:** 212225240079

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
gray = cv2.imread("Eagle_in_Flight.jpg", 0)
plt.imshow(gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
plt.show()

```

#### 2. Print the image width, height & Channel.
```
img = cv2.imread("Eagle_in_Flight.jpg")
height, width, channels = img.shape
print("Width:", width)
print("Height:", height)
print("Channels:", channels)
```

#### 3. Display the image using matplotlib imshow().
```
import matplotlib.pyplot as plt
img = cv2.imread("Eagle_in_Flight.jpg")
plt.imshow(img)
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```
img = cv2.imread("Eagle_in_Flight.jpg")
cv2.imwrite("Eagle.png", img)
print("Image saved successfully")
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```
color = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```
img = cv2.imread("Eagle.png")
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
height, width, channel = img.shape
plt.imshow(img)
plt.show()
print("Width:", width)
print("Height:", height)
print("Channel:", channel)
```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```
img = cv2.imread("Eagle.png")
crop = img[50:430,200:550]
plt.imshow(crop[:, :, ::-1])
plt.axis('off')
plt.show()
```

#### 8. Resize the image up by a factor of 2x.
```
resize = cv2.resize(img, None, fx=2, fy=2)
plt.imshow(resize[:, :, ::-1])
plt.show()
```

#### 9. Flip the cropped/resized image horizontally.
```
flip = cv2.flip(resize, 1)
plt.imshow(flip[:, :, ::-1])
plt.show()

```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```
img = cv2.imread("Apollo-11-launch.jpg")
plt.imshow(img[:, :, ::-1])
plt.show()
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```
text = 'Apollo 11 Saturn V Launch, July 16, 1969'
font_face = cv2.FONT_HERSHEY_PLAIN
cv2.putText(img, text, (250, 700), font_face, 2, (255, 255, 255), 2)
plt.imshow(img, cmap='gray')
plt.show()
```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```
rect_color = (255, 0, 255)
cv2.rectangle(img, (480, 80), (700, 630), rect_color, 3)
```

#### 13. Display the final annotated image.
```
plt.imshow(img[:, :, ::-1])
plt.show()
```

#### 14. Read the image ('Boy.jpg').
```
img = cv2.imread('boy.jpg')
plt.imshow(img[:, :, ::-1])
plt.show()
```

#### 15. Adjust the brightness of the image.
```
matrix_ones = np.ones(img.shape, dtype=np.float64)
```

#### 16. Create brighter and darker images.
```
matrix = np.ones(img.shape, dtype=np.uint8) * 50
img_brighter = cv2.add(img, matrix)
img_darker = cv2.subtract(img, matrix)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```
plt.figure(figsize=(15, 5))
plt.subplot(1, 3, 1)
plt.imshow(img[:, :, ::-1])
plt.title("Original Image")
plt.subplot(1, 3, 2)
plt.imshow(img_darker[:, :, ::-1])
plt.title("Darker Image")
plt.subplot(1, 3, 3)
plt.imshow(img_brighter[:, :, ::-1])
plt.title("Brighter Image")
plt.show()
```

#### 18. Modify the image contrast.
```
matrix1 = np.ones(img.shape) * 1.1
matrix2 = np.ones(img.shape) * 1.2
img_higher1 = cv2.multiply(img, 1.1)
img_higher2 = cv2.multiply(img, 1.2)
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```
img_lower = cv2.multiply(img, 0.8)
plt.figure(figsize=(15, 5))
plt.subplot(1, 3, 1)
plt.imshow(img[:, :, ::-1])
plt.title("Original Image")
plt.subplot(1, 3, 2)
plt.imshow(img_lower[:, :, ::-1])
plt.title("Lower Contrast")
plt.subplot(1, 3, 3)
plt.imshow(img_higher2[:, :, ::-1])
plt.title("Higher Contrast")
plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```
img = cv2.imread('boy.jpg')
b, g, r = cv2.split(img)
plt.subplot(1, 3, 1)
plt.imshow(b, cmap='gray')
plt.title('Blue Channel')
plt.subplot(1, 3, 2)
plt.imshow(g, cmap='gray')
plt.title('Green Channel')
plt.subplot(1, 3, 3)
plt.imshow(r, cmap='gray')
plt.title('Red Channel')
plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```
b, g, r = cv2.split(img)
merged = cv2.merge([b, g, r])
plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.subplot(1, 2, 2)
plt.imshow(cv2.cvtColor(merged, cv2.COLOR_BGR2RGB))
plt.title("Merged Image")
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```
img = cv2.imread('boy.jpg')
hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
h, s, v = cv2.split(hsv)
plt.figure(figsize=(12, 4))
plt.subplot(1, 3, 1)
plt.imshow(h, cmap='gray')
plt.title("Hue")
plt.subplot(1, 3, 2)
plt.imshow(s, cmap='gray')
plt.title("Saturation")
plt.subplot(1, 3, 3)
plt.imshow(v, cmap='gray')
plt.title("Value")
plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```
hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
h, s, v = cv2.split(hsv)
merged = cv2.merge([h, s, v])
plt.figure(figsize=(10, 4))
plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.subplot(1, 2, 2)
plt.imshow(cv2.cvtColor(merged, cv2.COLOR_HSV2RGB))
plt.title("Merged Image")
plt.show()
```

## Output:
- **i)** Read and Display an Image.  
- **ii)** Adjust Image Brightness.  
- **iii)** Modify Image Contrast.  
- **iv)** Generate Third Image Using Bitwise Operations.

## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.


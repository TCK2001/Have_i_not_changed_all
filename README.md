# Have_i_not_changed_all

abstract :
The most challenging problem in the engineering field: The one phrase from your boyfriend/girlfriend: "Have I not changed at all?"
Now, you don't need to worry! Let's solve it with Python.

## Abstract:
The most challenging problem in the engineering field: The one phrase from your boyfriend/girlfriend: "Have I not changed at all?" Now, you don't need to worry! Let's solve it with Python.

## Libraries:
```python
import cv2
from PIL import Image, ImageChops
import matplotlib.pyplot as plt
import numpy as np
```
## pillow imageoperations
```python
diff = ImageChops.difference(img_L, img_R)
```
![image](https://github.com/TCK2001/Have_i_not_changed_all/assets/87925027/d0c1b049-f11b-42eb-b912-94a103743233)

## Structural Similarity
```python
score, diff = structural_similarity(img_L_gray, img_R_gray, full=True)
```
![image](https://github.com/TCK2001/Have_i_not_changed_all/assets/87925027/77cefaf6-c7b1-432d-a877-a8492297b283)

## OpenCV Absoulte Difference
```python
diff = 255 - cv2.absdiff(img_L_gray, img_R_gray)
```
![image](https://github.com/TCK2001/Have_i_not_changed_all/assets/87925027/165139a9-e747-45a9-9bfb-a7db5d4a6645)

## Otsu's Threshold
```python
_, thresh = cv2.threshold(diff, 0, 255, cv2.THRESH_BINARY_INV | cv2.THRESH_OTSU)
```
![image](https://github.com/TCK2001/Have_i_not_changed_all/assets/87925027/8c54dba8-0960-4f40-b5d7-747af17f217c)

## visualize
```python
import imutils

cnts = cv2.findContours(thresh.copy(), cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)
cnts = imutils.grab_contours(cnts)

img_L_result = img_L_np.copy()
img_R_result = img_R_np.copy()

for c in cnts:
    x, y, w, h = cv2.boundingRect(c)
```
![image](https://github.com/TCK2001/Have_i_not_changed_all/assets/87925027/20ba5732-ed07-45b2-9dbe-f7e26b11822c)

## GIF
```python
from IPython.display import Image as Img
from IPython.display import display

img_L.save('out.gif', save_all=True, append_images=[img_R], loop=0, duration=500)

display(Img(url='out.gif'))
```
![Image Alt Text](https://github.com/TCK2001/Have_i_not_changed_all/out.gif)

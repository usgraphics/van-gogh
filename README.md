# Van Gogh Portraits in Perceptually Linear Colormaps

![new_colormaps_all](https://github.com/user-attachments/assets/f9cb8cd9-07ca-4528-8140-9b7acb6ea4ec)

# Source code
If you need full size "raw" images, please clone the repo and help yourself with the jpegs organized by folder. If you'd like to generate them, the source code (not tested since 2017) is as follows:


This code was extracted from a jupyter notebook.

```python
from matplotlib import cm
from skimage.transform import (hough_line, hough_line_peaks,probabilistic_hough_line)
from skimage.feature import canny
from skimage import data
import numpy as np
import matplotlib.pyplot as plt
import colormaps as cmaps
%config InlineBackend.figure_format = 'retina'

plt.register_cmap(name='viridis', cmap=cmaps.viridis)
plt.set_cmap(cmaps.viridis)
%pylab inline
pylab.rcParams['figure.figsize'] = (24,24)
color_img = data.imread('van_gogh.jpg')
grey_img = data.imread('van_gogh.jpg', as_grey = True)

red_img = color_img.copy()
red_img[:,:,1] = 0
red_img[:,:,2] = 0

blue_img = color_img.copy()
blue_img[:,:,0] = 0
blue_img[:,:,1] = 0

green_img = color_img.copy()
green_img[:,:,0]=0
green_img[:,:,2]=0

plt.set_cmap(cmaps.inferno)
[fig, ax] = plt.subplots()
ax.axis('off')
plt.imsave('red_img_plasma.jpg', red_img)
[fig, ax] = plt.subplots()
ax.axis('off')
plt.imsave('green_img_plasma.jpg', green_img)
[fig, ax] = plt.subplots()
ax.axis('off')
plt.imsave('blue_img_plasma.jpg', blue_img)

[fig, ax] = plt.subplots()
ax.axis('off')
plt.imsave('red_channel_inferno.jpg',red_img[:,:,0],vmin=0, vmax=255)
[fig, ax] = plt.subplots()
ax.axis('off')
plt.imsave('green_channel_inferno.jpg',green_img[:,:,1],vmin=0, vmax=255)
[fig, ax] = plt.subplots()
ax.axis('off')
plt.imsave('blue_channel_inferno.jpg',blue_img[:,:,2],vmin=0, vmax=255)

plt.set_cmap(cmaps.viridis)
[fig, ax] = plt.subplots()
ax.axis('off')
plt.imsave('red_channel_viridis.jpg',red_img[:,:,0],vmin=0, vmax=255)
[fig, ax] = plt.subplots()
ax.axis('off')
plt.imsave('green_channel_viridis.jpg',green_img[:,:,1],vmin=0, vmax=255)
[fig, ax] = plt.subplots()
ax.axis('off')
plt.imsave('blue_channel_viridis.jpg',blue_img[:,:,2],vmin=0, vmax=255)

plt.set_cmap(cmaps.magma)
[fig, ax] = plt.subplots()
ax.axis('off')
plt.imsave('red_channel_magma.jpg',red_img[:,:,0],vmin=0, vmax=255)
[fig, ax] = plt.subplots()
ax.axis('off')
plt.imsave('green_channel_magma.jpg',green_img[:,:,1],vmin=0, vmax=255)
[fig, ax] = plt.subplots()
ax.axis('off')
plt.imsave('blue_channel_magma.jpg',blue_img[:,:,2],vmin=0, vmax=255)
```

## Project Description

Segmentation using SLIC to obtain super-pixels, VGG16-FCN to obtain a pixel-wise prediction and Loopy Belief Propagation to perform inference in a Conditional Random Field that encourages smoothness in labelling.

SLIC - *Simple Linear Iterative Clustering* python implementation to obtain **Super-Pixels**. 
Paper: http://www.kev-smith.com/papers/SLIC_Superpixels.pdf (A K-Means implementation is also available as SLIC class inherits from KMeans). 

Loopy Belief Propagation - Inference algorithm to find optimal labelling in a factor graph.


## Example output

**Parameters:** m = 20, K =100

<table style="width:70%">
  <tr>
  <img src="https://github.com/mgamal96/Segmenation/blob/master/imgs/bear_superpixels.png?raw=true" alt="Paris" class="center">
  </tr>
</table>

## Code Description
 
 * slic.py
    * Contains SLIC and K-Means algorithms
 * max_sum.py
    * Contains graph building routine and max-sum algorithm

## Usage

### SLIC

``` Python

from slic import *

# 1. Instatiate SLIC object 
sl = SLIC()

# 2. Obtain cluster centers and assignments as an integer mask
mus, sets, = sl.run(img_CIElab, k=100, iters=5)

# 3. Obtain a colour mask (i.e. each pixel is given the colour cluster center it's assigned to)
clr_mask = sl.get_color_mask(mus, sets) 

# 4. Plot
plt.imshow(clr_mask); plt.show()

```


### K-Means

``` Python

from slic import *


# SLIC EXAMPLE

# 1. Instatiate SLIC object 
 km = KMeans()

# 2. Obtain cluster centers and assignments as an integer mask
mus, sets = km.run(img, k=10)

# 3. Plot
plt.imshow(sets[:,:,0]); plt.show()

```



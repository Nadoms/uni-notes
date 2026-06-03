# W9 - Image Stitching

Even if images are perfectly aligned there can still be lighting issues showing discontinuity.
![e2f489099febdfd743cadbf483c6274e.png](./e2f489099febdfd743cadbf483c6274e.png)

One must fit a model which finds a transformation T between matches, minimising the residual error.
$\sum{\text{residual}(T(x_i), x_i')}$

## Transformations
**Filtering** - Changing pixel values.
**Warping** - Changing pixel locations.
- Euclidean - Translation + rotation
- Similarity - Translation + rotation + scaling
- Affine - Translation + rotation + scaling + shearing
![a688aa2deb73fa551bd4e9fed4490045.png](./a688aa2deb73fa551bd4e9fed4490045.png)
- Projective - Homography
![fb4ba16c212dc0106832f6565aee3bde.png](./fb4ba16c212dc0106832f6565aee3bde.png)

### Linear Transformations
A transformation is **global** if it performs the same action to every pixel.
A transformation is **linear** if it can be represented by a 2x2 transformation matrix, T.
Translation is not linear - everything else is. Their properties are:
- Origin maps to origin
- Lines map to lines
- Parallel lines remain parallel
- Ratios are preserved
- Closed under composition (means there always is a matrix which can compose of multiple transformations)

**Homogenous coordinates** - Add an extra dimension to allow for a linear transformation.
![af906585fded01395969fa746a2c8a9c.png](./af906585fded01395969fa746a2c8a9c.png)
Converting from homogenous coordinates to 2D coordinates:
$\left(
  \begin{array}{c}
    x \\
    y \\
    w
  \end{array}
\right) \mapsto (x/w, y/w)$
Now translation can be represented.
![89ef002dd1fb1498ec2e32778f943e75.png](./89ef002dd1fb1498ec2e32778f943e75.png)

Any transformation which has a "001" at the bottom is an **affine** transformation.
![25daf6dbdf62e26b4ea09e53cf0380a2.png](./25daf6dbdf62e26b4ea09e53cf0380a2.png)
These are basically like linear transformations but the origin no longer maps to the origin.

### Projective Transformations
This is the mapping of one plane to another via a single point.
![fc9305f7a24e0b32f6c5f1f6acb2468d.png](./fc9305f7a24e0b32f6c5f1f6acb2468d.png)
These come about from changing the "001" on the final row, e.g. out-of-plane rotation. Now there are 8 unknown values to find.
![ff50ce47ebf0ea9d9640e59c9a44d739.png](./ff50ce47ebf0ea9d9640e59c9a44d739.png)

Parallel lines may not be parallel anymore, and ratios may not be preserved.
4 pairs of matches are all that are needed to compute the 8 unknown translation matrix values.

### Robustness
Not all matches will be correct. Matches are either right, or very wrong, so using least squares will not cut it when fitting a transformation.
Objective: Maximise **inliers**.
![a4f4ce31c3e8b82246eb6a998b56607b.png](./a4f4ce31c3e8b82246eb6a998b56607b.png)
**Random sample consensus (RANSAC)** - Inliers will agree with each other, outliers will disagree with each other. Find the consensus; ignore the outliers.
- Randomly select $s$ sample matches.
- Compute transformation from sample group.
- Find the inliers to the transformation from the total match set.
- If number of inliers is sufficiently large, re-compute least-squares estimate of transformation on all of the inliers.
- Repeat $n$ times, and keep the transformation with the largest number of inliers.
$n$ is a result of the % of outliers and the % confidence we want to guarantee.

### Warping
**Forward warping** - Mapping an image to another by sending each pixel to its transformed location.
Issue: One may encounter holes in the image.
![9faad721e6f868107baaadf38c7e0bb6.png](./9faad721e6f868107baaadf38c7e0bb6.png)

**Inverse warping** - Start from the destination image, and sample the colour value from the interpolated source image.
![095e14ae614905f07418a5997180d81f.png](./095e14ae614905f07418a5997180d81f.png)

### Panorama Stitching
Now we can easily make panoramas:
- Detect features in all images
- Match features together
- Compute a homography (3x3 transformation matrix) using RANSAC
- Perform some image blending

### Image Blending
**Alpha blending** - Simply cross-dissolve between the two images.
![fd876b7a0d7997ceab813bcf461628f2.png](./fd876b7a0d7997ceab813bcf461628f2.png)
The window size is the area when the images are merged.
Larger than largest prominent feature = ghosting
Smaller than the size of smallest prominent feature * 2 = seams
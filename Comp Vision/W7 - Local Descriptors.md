# W7 - Local Descriptors and Stereo Basics
## Local Descriptors
The simplest feature descriptor is a list of intensities in a patch.
This is highly impacted by rotational and intensity changes.

### Rotation Invariance
Instead, we could list intensity gradient directions in a patch. Magnitude is less important.
![0a71cdf42f4012c7a638447d85126309.png](./0a71cdf42f4012c7a638447d85126309.png)
We can rotate each patch to have its dominant gradient direction point the same way.
![f0bde6becbf63f5a4456b9eefcd93c33.png](./f0bde6becbf63f5a4456b9eefcd93c33.png)

### SIFT
**Scale invariant feature transform (SIFT)** - Feature location and scale using DoG, then compute histogram of image gradient orientations of pixels in region.
It divides a patch into subpatches, for which it computes the histogram for each with the 8 reference angles.
![8c72f996794ef04c2a6c0fccd3ee2595.png](./8c72f996794ef04c2a6c0fccd3ee2595.png)
The resulting descriptor is 128D.
- Handles up to 60 degree 3D viewpoint changes
- Handles illumination changes
- Fast and efficient

### Comparing Descriptors
**Sum of square differences** - Compute SSD distance between descriptor entries. Can give good scores to ambiguous matches.
One can consider ambiguous matches by checking the distance ratio between two matches.
![d2c941dc74c92ed22cee7cc2a529ea32.png](./d2c941dc74c92ed22cee7cc2a529ea32.png)
Values close to 1 should be considered more carefully, or the features should be discarded as misleading.
Features too far away, further than some threshold, should be thrown out.

Evaluation can be done with ROC (TP / FP).

### Applications
- Image alignment
- Panorama stitching
- Object recognition
- Motion tracking
- Robot navigation

## Stereo Basics
How do we recover 3D information from an image? We can use:
- Shading
- Texture
- Focus
- Perspective
- Motion

**Stereo vision** - Given multiple images of an object, compute its 3D shape.
This can be narrowed down to a calibrated, binocular pair of image sources.
![f7292b2805664b77a29f5f363f193b00.png](./f7292b2805664b77a29f5f363f193b00.png)

Looking at one camera at a time:
![80cd98f8fcff40ad9f69187043b6d23b.png](./80cd98f8fcff40ad9f69187043b6d23b.png)
We can separate the vector to point P into two triangles in the X and Y axes.

With two cameras, we can triangulate like so:
![d525baf97f12f03fef237b4172e0268c.png](./d525baf97f12f03fef237b4172e0268c.png)
We end up with a depth formula:
$Z = \frac{bf}{x_l - x_r}$
Depth = baseline x focal length / disparity in image displacement
Images are projected into a new plane such that only depth in the x-axis matters. (?)

### Correspondences
To get point data in the first place, we need points from both images which match.
**Epipolar constraint** - Match for a given $x_l, y_l$ lies on the line $y_l = y_r$, if the camera is rectified to align with the baseline.

**Moravec operator** - An operator for corner detection. idk
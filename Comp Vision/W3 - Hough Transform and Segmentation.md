# W3 - Hough Transform and Segmentation
## Generalised Hough Transform
### Cartesian Hough Lines
These are used to find lines in an edge-detected image.
Parameter space linear equation: $c = -xm + y$, so $-x$ is the gradient, and $y$ is the intercept.
We can plot a line onto parameter space for every point in the image, and see where they cross.
![ef5d89b36e099e931d35d3dfe6701036.png](./ef5d89b36e099e931d35d3dfe6701036.png)
The graph above has $m$ on the horizontal axis and $c$ on the vertical axis.
Crossings of more than 2 lines are of interest, meaning more than 3 points fall in a line in $xy$ space.
We can create the parameter space discretely with a 2D accumulator array. This allows us to pick points which are "near enough".

### Polar Hough Lines
The problem with the Cartesian system is that a line can be vertical and its $m,c$ undefined. We can use polar coordinates instead.
$r = x\cos{\theta} + y\sin{\theta}$, and again we fit a curve in the $r, \theta$ parameter space.

### Hough Circles
We can use Hough circles to find the centre of points arranged in a circle.
Consider all circles which can go through a point.
$(x - a)^2 + (y - b)^2 = r^2$
becomes
$(a - x)^2 + (b - y)^2 = r^2$
such that the parameters are $x, y$.

In the parameter space / accumulator array, circles are drawn instead of lines / curves.
![a5628e4f79ad2a9ee3bbc0f824a01da1.png](./a5628e4f79ad2a9ee3bbc0f824a01da1.png)
Where there is a crossing in parameter space is where there is a circle in image space passing through many points.
![fa2ab5e96b4155026299997288fc4a34.png](./fa2ab5e96b4155026299997288fc4a34.png)
To find circles of any radius, as well as configuring $a,b$, we need a 3D accumulator array for $a,b,r$.

### Generalised Hough Transform
Instead of fitting for lines and circles, we can try to look for any arbitrary shape.
Pick a reference point within the shape, $x_c, y_c$.
Each $(r, \alpha)$ is the information needed to get from $x,y$ to the reference point.
![3b69805f17c1fc92e4600522dcde7dea.png](./3b69805f17c1fc92e4600522dcde7dea.png)
To model the template shape, we use the **R-table**:
- Consists of a range of edge angles, $\phi$
- For every contour pixel, the edge gradient $\phi$ and the $(r,\alpha)$ is appended to the R-table
- Using $(r, \alpha)$ pairs, a centre can be calculated
![44420b034b026f49e9a3ac165c916488.png](./44420b034b026f49e9a3ac165c916488.png)
Using this information, we can take every edge pixel in the image, its gradient direction, and again use an accumulator array to find points which are likely centres.
![b1905a12a523c87b38f2eb38eb402741.png](./b1905a12a523c87b38f2eb38eb402741.png)![6c911007bc5d57a6ac72a34d150e073a.png](./6c911007bc5d57a6ac72a34d150e073a.png)
This can then be thresholded to give a yes or no answer on a shape appearing.

## Segmentation
### Grouping
Goal: Group similar image features together.
![b3f5f318a014217b74158f7dd57a266c.png](./b3f5f318a014217b74158f7dd57a266c.png)
Used for auto-selection, background blur, social media stickers, etc.

Grouping is not always so easy. Elements in a collection can have properties arising from relationships.
![57527fbb27db7243eaa989b7038d6cc4.png](./57527fbb27db7243eaa989b7038d6cc4.png)
This leads to **Gestalt psychology**,  where "the whole is greater than the sum of its parts".
![d9b619b2bca7e9f4ec1f0c2ae75b1748.png](./d9b619b2bca7e9f4ec1f0c2ae75b1748.png)

**Top-down** - Pixels belong together because they are from the same object.
**Bottom-up** - Pixels belong together because they look similar.

We can obtain a ground truth through human segmentation, but this is not an objective process.
By repeating this multiple times and overlaying them, some edges will be stronger than others.

**Superpixels** - Oversegment an image and then draw your overlay onto it.
![42e63668526622087394b1e670afa035.png](./42e63668526622087394b1e670afa035.png)
This ensures that edges will not overlap.

### Clustering
Goal: Label pixels with what they belong to.
![9784242ce556b4271bba80fdd47edddc.png](./9784242ce556b4271bba80fdd47edddc.png)
Could choose 3 colours as representative intensities.
The best colours minimise sum of squares distance for points being assigned to their closest colour.
**K-means clustering** - Randomly initialise the cluster centre colours, compute the clusters, compute new centres, and repeat.
This will always quickly converge to a local minimum.

Disadvantages:
- Must specify K
- Sensitive to initial centres
- Sensitive to outliers
- Detects spherical clusters only

Our feature space doesn't have to be 1D (just intensity), it can be 3D (e.g. RGB).
![4555b38e17a719dc71ee96327fbd1aab.png](./4555b38e17a719dc71ee96327fbd1aab.png)
Even position (x, y) can be included in the feature space, to incorporate proximity into clustering.
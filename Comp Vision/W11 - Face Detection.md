# W11 - Face Detection

## Decision Trees
Decision trees can be made for simple classification problems with discrete variables.

Example: Which variable should be the root node? The one which best predicts the result alone.
![465653995771251573a450fdf9148d1a.png](./465653995771251573a450fdf9148d1a.png)

### Gini Impurity
**Gini impurity** - A measure to determine how well a variable determines a result by itself.
$\text{Gini} = 1-p_y^2-p_n^2$
Lower = Less impurity.
![deafdfea47dfe9ee9325cff51fdf5030.png](./deafdfea47dfe9ee9325cff51fdf5030.png)
Gini impurity needs to be recalculated for child nodes, once a root is picked.

To handle continuous values, one can fill in values between each sample and calculate the Gini impurity for each.
![b16a490e8e69657dce8a5b80568e517a.png](./b16a490e8e69657dce8a5b80568e517a.png)
We can then pick the lowest one - the one which divides the data the best.
![31d4cb16a81c1f9f3fd6209945ecee6d.png](./31d4cb16a81c1f9f3fd6209945ecee6d.png)

### Random Forests
Decision trees are not very accurate.
Solution: Make a **bootstrapped dataset** which copies samples from the original into a new dataset of the same size.
Once a root is chosen, a random set of the remaining variables are also chosen to fill out the rest of the tree.
Repeat this hundreds of times, now we have a random forest.
![c9c316874748ee2672efcb55af7d7902.png](./c9c316874748ee2672efcb55af7d7902.png)

This forest votes on each new data point, and the most likely category is chosen.

## AdaBoost
**Adaptive boosting** - ML technique combining simple decision trees into a single, more accurate model. Each portion targets the mistakes made by previous, combining with a weighted vote.

Instead of a forest of trees, AdaBoost uses a **forest of weighted stumps**.
Each sample is given a weight of importance to classify right - by default equal.
The algorithm iterates:
- Use Gini impurity again to select the first stump (instead of root of tree).
- Error of each stump is the sum of incorrect sample weights.
- Store the say for this stump, $\text{say} = 0.5 \times \ln(\frac{1-\text{Error}}{\text{Error}})$
- Update sample weights so that misclassified samples are higher priority.
- If incorrect, $w' = w \times \text{Error}^{\text{say}}$
- If correct, $w' = w \times \text{Error}^{-\text{say}}$
- A new stump is created by looking at Gini impurities again.

To classify using a forest of stumps, just sum their amount of say during voting.

## Face Detection

### Applications
- Face focus, exposure, red-eye removal
- Tracking
- Adult / child detection
- Face recognition
- Cat and dog face-on detection

### Viola Jones
By blurring a face, one can simplify the structure down into **rectangular features** containing shadows and highlights.
![4cf278bc78a66d132cf42e31a63c2595.png](./4cf278bc78a66d132cf42e31a63c2595.png)

**Integral image** - At a pixel $x, y$, its value is the sum of all pixels at positions $(<x, <y)$.
![2fa018d7ee2c0d6a6bd9bcb29e3bfa5f.png](./2fa018d7ee2c0d6a6bd9bcb29e3bfa5f.png)
A bigger data type is required to store such large values.
For more complicated integral calculations, multiple intensity reference are required. E.g. 4 here to find the green square.
![d7bbd42a37daea35ab9018a16b1d2e02.png](./d7bbd42a37daea35ab9018a16b1d2e02.png)

For Viola Jones algorithm:
- Faces must be 24x24, normalised intensities, straight-on
    - $x'=(x-\bar{x})/\sigma$, where $\bar{x}$ is mean, etc. This makes all images have the same avg intensity and contrast.
    - Within a window, the std can be calculated from the mean and integral image squared.
    - This normalisation gives dark pixels negative values and light pixels positive values.
- Uses rectangle features
- Uses AdaBoost to classify faces
- 200 rectangular features
- 95% detection rate
The two best features are below:
![58d550c82e5eb6921c76142c128f400e.png](./58d550c82e5eb6921c76142c128f400e.png)

Issue: Most patches are not faces. Slow processing.
Solution: **Cascade classifier** which quickly discards most non-faces (70%).
The 10-stage cascade had a much lower FP rate and slightly lower detection. Each stage has more features. Detection speed increase.
- Trained in a day
- Searches 384x288 images in 0.067s
- Applies features at multiple scales and locations
# W2 - Edges and Convolution
note: missed part 1 and 2
## Edge Detection
Edges are produced by:
- Depth discontinuity
- Surface colour discontinuity
- Illumination discontinuity

Edges correspond to the image intensity first derivative extrema, or second derivative zero-crossings.
![0ac4e6bbf0f323696ecb8f6cd8d1633e.png](./0ac4e6bbf0f323696ecb8f6cd8d1633e.png)

First derivative filter:
![d1e58b88291100c08e35e6484b1dc5cc.png](./d1e58b88291100c08e35e6484b1dc5cc.png)
Result of applying a filter to an edge:
![1d0d2462a335d0757321320e4d605bd0.png](./1d0d2462a335d0757321320e4d605bd0.png)

Second derivative filter:
![c2e21e1549a6552df234bd773c83a5c6.png](./c2e21e1549a6552df234bd773c83a5c6.png)
Result of applying the filter:
![6ee6406cd87eba283dc89cc842a00a3f.png](./6ee6406cd87eba283dc89cc842a00a3f.png)

This edge detection is extremely sensitive to noise. It can be mitigated by pre-smoothing.
![b2ea5874b2912254800bd2c1f259808e.png](./b2ea5874b2912254800bd2c1f259808e.png)

## Kernel Edge Detection
**Prewitt Kernel** - Kernel which detects edges along an axis and performs some smoothing.
![2397e2fec475011b5f1cd88ad8a7f95e.png](./2397e2fec475011b5f1cd88ad8a7f95e.png)
The Sobel Kernel performs weighted smoothing (1, 2, 1).
These produce derivative images for both axes, $I_x, I_y$.
**Edge Magnitude** - $\sqrt{{I_x}^2 + {I_y}^2}$
**Edge Direction** - $\tan^{-1}{\frac{{I_x}}{{I_y}}}$
These kernels are separable, in that they can be implemented as a cascade of 1D convolution.
For the Sobel Kernel:
![5128a37204cc8e95b8f7b40327a5db6b.png](./5128a37204cc8e95b8f7b40327a5db6b.png)
This means we go from $n \times n$ to $2 \times 1 \times n$ convolutions.

## Gaussian Edge Detection
### Canny Edge Detection
With a Gaussian mask, usually the insignificant edges of the distribution are cut off.
![a4e35a1a373a1db7e5a1b52c05d529c7.png](./a4e35a1a373a1db7e5a1b52c05d529c7.png)
- Good for anti-aliasing
- Kernel is separable by x and y
![bc7e5257118ae9bbf5d08c08a464c8bf.png](./bc7e5257118ae9bbf5d08c08a464c8bf.png)
This allows use to do a cascade of 1D convolutions instead.

**Canny Edge Detector** - Use Gaussian smoothing to select scale, then do edge detection.
Edge detection at larger scales is more reliable.
Differentiation is convolution, and convolution is associative:
![24e42cb0a0242308ef17a06689e0c011.png](./24e42cb0a0242308ef17a06689e0c011.png)
Meaning we can instead convolve with the derivative of the Gaussian, along the two axes.
![a57ab6e3dece676bad9f9dcd54e2dde4.png](./a57ab6e3dece676bad9f9dcd54e2dde4.png)

By itself, this produces thick edges. Finding the strongest edge pixel is a 2nd derivative problem.
**Thinning** - Non-maxima of an edge can be suppressed.
![ed550426b6cc4be45fac42d493822147.png](./ed550426b6cc4be45fac42d493822147.png)

### Laplacian Edge Detection
**Laplacian Kernel** - Second derivative kernel. It produces zero-crossings, without edge direction.

Laplacian of Gaussian:
![7203a6d24d34bd73533674d1c3e80c9a.png](./7203a6d24d34bd73533674d1c3e80c9a.png)

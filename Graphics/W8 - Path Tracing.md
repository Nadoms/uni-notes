# W8 - Path Tracing
Whitted-style ray-tracing produces crisp shadow edges due to using point light sources.
In reality, shadows have:
**Umbra** - Dark part of the shadow (point 1)
**Penumbra** - Edge of the shadow, lit by some light (point 2)
![5da65294c5d282e1cab7e3d10618bec9.png](./5da65294c5d282e1cab7e3d10618bec9.png)
The realism of the shadow scales with the number of shadow feelers sampling the area light source.

Instead of taking a Whitted-style hierarchical approach, we can trace paths of rays taking uniformly random directions.
![01b33235438ea89dcab418e53e2dedf6.png](./01b33235438ea89dcab418e53e2dedf6.png)
From this sampling, we can estimate how light would behave in real life. This allows simulation of diffuse surfaces by shooting many rays through each pixel.

**SPP** - Samples per pixel, usually in the 100s or 1000s to get a noise-free image.

**Texture Baking** - When lighting and objects in the scene are static, you can generate textures for the scene and bake them on, just like with radiosity.

**Ambient Occlusion** - Taking a point and shooting rays from that point, darkening it based on number of blocked rays.
![268476107c9050803a011d6c2b8192ea.png](./268476107c9050803a011d6c2b8192ea.png)

**Caustics** - Reflection of the surface of water or refraction through water, glass, etc.
![a7b580f85178c5fef0a807e5d050c391.png](./a7b580f85178c5fef0a807e5d050c391.png)
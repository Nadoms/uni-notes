# W7 - Raytracing and Radiosity

## Raytracing
**Ray** - A line with an origin point vector and a direction vector, usually normalised to 1.

**Raycasting** - Firing a single ray into the scene and simulating where it goes.

**Whitted Recursive Algorithm**
1. Cast a ray from the viewpoint through a pixel on the view plane.
2. At intersections, generate a shadow-feeler ray to every light source on the screen.
4. At non-opaque intersectations, apply refraction to bend the ray.
5. Continue until the ray runs out of energy or you're deep enough in the ray tree.
This makes everything hard and shiny, as it ignores the "explosive" diffuse reflection calculations.
![fd2ea0bfd3a226942e1a5da1424533a9.png](./fd2ea0bfd3a226942e1a5da1424533a9.png)

## Radiosity
- Better suited for diffuse reflection, over specular.
- Patches up a scene in quadrilaterals or triangles.
- Calculates how objects exchange light energy.
- Light sources are polygons emitting their own energy.
- Doesn't care about the viewpoint at all.
- love
With infinite areas:
![5bbede9913f9a0a3729b3242d8ae2e41.png](./5bbede9913f9a0a3729b3242d8ae2e41.png)
Simplified to discrete polygons:
![fabd5f590e3927e9db667730e30cfbc4.png](./fabd5f590e3927e9db667730e30cfbc4.png)

**Energy transmission (form) factors:**
- Patch size
- Patch distance
- Patch orientation
- Patch obstructions

**Progressive radiosity** - Iteratively transmitting energy to relevant patches.
![5f29bd834c2c96a4978b505b0919a88e.png](./5f29bd834c2c96a4978b505b0919a88e.png)
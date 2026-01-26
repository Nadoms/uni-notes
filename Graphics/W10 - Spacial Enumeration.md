# W10 - Spatial Enumeration
Spacial enumeration techniques are used to organise space so that high-level calculations on them can be done more quickly, such as:
- Whether a point is inside any objects or not
- Whether a ray collides with any objects or not

## Regular Spatial Enumeration
**Gridcell** - A 3D array of voxels, where each point maps to the object it contains.
- Finding what object is at a point is O(n).
- Space complexity is O(n^3).
- Empty space is wasted.
![0f09d99f5e0234d8d6262b4ab7097b6a.png](./0f09d99f5e0234d8d6262b4ab7097b6a.png)

**Octree** - Recursively split a big cube where it matters most.
- Have a threshold for the number of objects allowed in a section.
- Each section contains a list of objects within it.
- Adapts to the objects in space, with less waste on emptiness.
- Time complexity is O(log n)
- Space complexity is O(n)
![6c39c2f7a4e47fbe1377dd842fa57e7f.png](./6c39c2f7a4e47fbe1377dd842fa57e7f.png)

## Irregular Spatial Enumeration
**Spacial Cohesion** - How objects tend to cluster together in the real world.

**Hierarchical Bounding Volume** - Start with objects, and wrap them in bounding volumes.
- Opposite direction of an octree, going bottom-up.
- Surround clusters of volumes in a grouped volume.
![44e56d594333e2196396cb18598c075f.png](./44e56d594333e2196396cb18598c075f.png)

**Binary-Space Partitioning** - Halves the scene until each section is under the object limit.
- Similar to Octree, but more adaptive.
- Can be axis-aligned, like below.
![a5a14d860fbedc385e28ab0a0c691ba9.png](./a5a14d860fbedc385e28ab0a0c691ba9.png)

## Culling
There is frustum culling, which doesn't render objects outside our your FOV.
Then there is portal culling, which considers a section of the FOV through doors, windows, etc.
![2f519589a5c7194ec0132353108b709d.png](./2f519589a5c7194ec0132353108b709d.png)
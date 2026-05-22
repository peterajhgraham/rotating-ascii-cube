# Rotating ASCII Cube

A real-time 3D ASCII cube renderer in C++, in ~150 lines.

```
      +--------+
     /|       /|
    / |      / |
   +--------+  |
   |  +-----|--+
   | /      | /
   |/       |/
   +--------+
```

## The math

Each frame, every cube vertex is rotated by two angles `A` and `B` using the standard rotation matrices around the X and Y axes — `(y, z) → (y·cosA − z·sinA, y·sinA + z·cosA)` and the analogous form for Y. The rotated point is then projected to the screen with a perspective divide: `x' = K·x/(z + d)`, `y' = K·y/(z + d)`, where `d` pushes the cube away from the camera so `z + d > 0`. Edges are rasterized between projected vertices with Bresenham's line algorithm. A per-pixel z-buffer storing `1/(z + d)` keeps nearer points on top — larger reciprocal wins, so back edges get correctly occluded.

## Build & run

```
g++ -o rotating_cube rotating_cube.cpp -lm
./rotating_cube
```

Best viewed in a terminal at least 160×44 characters.

---

Written for fun. The math is real.

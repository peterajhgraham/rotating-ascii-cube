# Rotating ASCII Cube

Real-time 3D ASCII renderer in C++ with rotation matrix math, z-buffering, and projection in ~150 lines.

A terminal program that spins a cube by composing X and Y rotation matrices each frame - `(y, z) -> (y*cosA - z*sinA, y*sinA + z*cosA)` and the Y equivalent - then projects the rotated vertices onto the screen with a perspective divide: `x' = K*x/(z+d)`, `y' = K*y/(z+d)`. Edges are rasterized with Bresenham's line algorithm. A per-pixel z-buffer keyed on `1/(z+d)` ensures nearer edges overwrite farther ones, giving correct occlusion.

https://github.com/user-attachments/assets/06601427-6c2b-435b-ba5b-ded2195fc7b9

## Directory Structure

```
ASCII_Rotating_Cube/
├── rotating_cube.cpp
├── LICENSE
├── README.md
└── .gitignore
```

## Prerequisites

* **C++ Compiler**

* **Terminal** (Unix-like systems recommended)

## Usage

1. **Clone**:
   ```
   git clone https://github.com/peterajhgraham/Rotating_ASCII_Cube.git
   cd Rotating_ASCII_Cube
   ```

3. **Compile**:
   ```
   g++ -o rotating_cube rotating_cube.cpp -lm
   ```

4. **Run**:
   ```
   ./rotating_cube
   ```

## Customization

* **Rotation Speed:** You can modify the rotation speed by changing the values of `A += 0.02f;` and `B += 0.015f;` in the `rotating_cube.cpp` file
   * Increase/decrease the values of A & B proportionately to avoid an uneven and distorted cube

* **Cube Size:** Adjust the cube size by modifying the `cubeSize` variable

## Notes

* Best viewed in a terminal with at least 160x44 characters

* The code uses the Bresenham's line algorithm for drawing lines between the cube's vertices

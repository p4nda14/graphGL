# graphGL

A small OpenGL tool for visualizing mathematical functions as 3D meshes.

I was (and am still) teaching myself OpenGL and can only learn by doing, so I came up with this, and so far I'm pretty proud of it. As a reminder, this is my own little side project born from trying to learn OpenGL, so nothing is probably very well optimized. Anyway, thanks for trying it!

## Usage

graphGL currently supports 3 functions (don't worry, more to come).

### `visualize`

```cpp
void visualize(float (*zValues), float domain[2], float range[2], float zrange[2], float precision, bool anim);
```

| Parameter | Description |
|-----------|-------------|
| `float (*zValues)` | A function that returns the mathematical function's dependent variable. The program will try to pass a `std::array<float, 2>` to this function, corresponding to the x and y positions in the mesh. |
| `float domain[2]` | X values you want to show. Expects `{minXValue, maxXValue}`. |
| `float range[2]` | Y values you want to show. Expects `{minYValue, maxYValue}`. |
| `float zrange[2]` | Z values you want to show. Expects `{minZValue, maxZValue}`. |
| `float precision` | The number of individual points to calculate. Should be a value that can be turned into an `int`. |
| `bool anim` | Whether the function changes over time. *(Not implemented yet.)* |

### `setMeshColor`

```cpp
void setMeshColor(float color[4]);
```

| Parameter | Description |
|-----------|-------------|
| `float color[4]` | The RGBA values you want the mesh to be, scaled from 0 to 1. Expects `{r, g, b, a}`. |

### `setBgColor`

```cpp
void setBgColor(float color[4]);
```

| Parameter | Description |
|-----------|-------------|
| `float color[4]` | The RGBA values you want the background to be, scaled from 0 to 1. Expects `{r, g, b, a}`. |
  

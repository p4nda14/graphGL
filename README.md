# graphGL

A small OpenGL tool for visualizing mathematical functions as 3D meshes.

I was (and am still) teaching myself OpenGL and can only learn by doing, so I came up with this, and so far it's working pretty well. As a reminder, this is my own little side project born from trying to learn OpenGL, so nothing is probably very well optimized. Anyway, thanks for trying it!



## Usage

graphGL currently supports 3 functions (don't worry, more to come).

### `visualize`

```cpp
void visualize(float (*zValues) (std::array<float, 2>, float t), std::array<float, 2> domain, std::array<float, 2> range, float prec, bool meshType, bool anim);
```

| Parameter | Description |
|-----------|-------------|
| `float (*zValues) (std::array<float, 2>, float t)` | A function that returns the mathematical function's dependent variable. The program will try to pass a `std::array<float, 2>` to this function, corresponding to the x and y positions in the mesh, and a `float` corresponding to the time elapsed. |
| `std::array<float, 2> domain` | X values you want to show. Expects `{minXValue, maxXValue}`. |
| `std::array<float, 2> range` | Y values you want to show. Expects `{minYValue, maxYValue}`. |
| `float prec` | The number of individual points to calculate. Should be a value that can be turned into an `int`. |
| `bool meshType` | A selector for either a wire mesh or solid mesh, uses inbuilt definitions `GRAPHGL_MESHTYPE_SOLID` or `GRAPHGL_MESHTYPE_WIRE` |
| `bool anim` | Whether the function changes over time. |

### `setMeshColor`

```cpp
void setMeshColor(float color[4]);
```

| Parameter | Description |
|-----------|-------------|
| `float color[4]` | The RGBA values you want the mesh to be. Expects `{r, g, b, a}`. |

### `setBgColor`

```cpp
void setBgColor(float color[4]);
```

| Parameter | Description |
|-----------|-------------|
| `float color[4]` | The RGBA values you want the background to be. Expects `{r, g, b, a}`. |



## Installation

  

## Example

Create a function that returns a `float` in this example it will be called "wave"
```cpp
float wave(std::array<float,2> pos, float time){
}
```
Being sure to have two inputs to the function, both a 2d array of type `float` (this will be the position of the point the program is trying to calculate) and a float that corresponds to the elapsed time since the window was started.

Next Fill the function with whatever calculations the mathematical function will perform.
```cpp
return 3 * sin(0.25 * sqrt(pow(pos[0],2)+pow(pos[1],2)) - time);
```
In this case we are using a 3d wave propagation function, the mathematical function for which looks like this:
```math
z = \sin(A \sqrt{x^2 + y^2} - t)
```

Then call the visualize function and put the name of your function as the first input, then the domain and range of the function, and the mesh type and whether you want it to change over time.
```cpp
 visualize(wave, {-20,20}, {-20,20}, 150.0f, GRAPHGL_MESHTYPE_SOLID, true);
```

And there you have it, here's the full sample code
```cpp
#include <graphGL/graphGL.hpp>
#include <array>
#include <cmath>

double G = 6.6743*(pow(10,(-11)));
double mass = 1.988416*(pow (10,30));
double massPosition[] = {0 ,0};
const double AU = 1.496e11;

float wave(std::array<float,2> pos, float time){
    return 3 * sin(0.25 * sqrt(pow(pos[0],2)+pow(pos[1],2)) - time);
}

int main(){
    //setBgColor(258.0f, 0.0f, 0.0f, 100.0f);
    setMeshColor(0.0f, 256.0f, 0.0f, 100.0f);
    visualize(wave, {-20,20}, {-20,20}, 150.0f, GRAPHGL_MESHTYPE_SOLID, true);
    return 0;
}

```

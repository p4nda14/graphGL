# graphGL
I was (and am still) teaching myself OpenGL and can only learn by doing, so I came up with this and so far I'm pretty proud of it. As a reminder this is my own 
little side project birthed from my trying to learn openGL, so nothing is probably very well optimized. Anyway thanks for trying it.

# Usage
Currently supporting 3 functions (don't worry more to come);

void visualize(float (*zValues), float domain[2], float range[2], float zrange[2], float precision, bool anim);
  Where:
  -float (*zValues) : A function that returns the mathematical function's dependent variable.
          (The program will try to pass a std::array<float, 2> variable to this function corresponding to the x and y positions in the mesh.)
  -float domain[2]  : X values you want to show. expects: {minXValue, maxXValue}
  -float range[2]   : Y values you want to show. expects: {minYValue, maxYValue}
  -float zrange[2]  : Z values you want to show. expects: {minZValue, maxZValue}
  -float precision  : The number of individual points to calculate. Should be a value that can be turned into an int.
  -bool anim        : Whether the function changes over time. (not implemented yet)

void setMeshColor(float color[4]);
  where:
  -float color[4] : The RGBA values you want the mesh to be, scaled from 0 to 1. {r,g,b,a}

void setBgColor(float color[4]);
  Where:
  -float color[4] : The RGBA values you want the background to be, scaled from 0 to 1. {r,g,b,a}
  

# Custom-3D-engine

3D rendering engine from scratch written on JS. Obviously it can't compete with real advanced engines, but it was really interesting and informative to learn and understand all the mathematical formulas and principles behind it.

## Installation

To use the 3D rendering engine, simply clone the repository

```
git clone https://github.com/Levael/Custom-3D-engine.git
```

## Code Overview

### CONSTRUCTOR

The main component of the engine is a JavaScript class called `Engine`. Its `constructor` method initializes the engine by creating a canvas element and attaching a 2D context to it. It sets some initial properties such as background color, maximum view distance, and movement and view steps. It also defines some coordinate lines for X, Y, and Z axes.

The `CAMERA` object represents the virtual camera used for viewing the 3D scene. It contains the screen center coordinates and the camera direction, which is specified in terms of X and Y angles.

The `cubeInit` method initializes a simple cube that can be rendered in the 3D space.

The rest of the code defines event listeners for keyboard and pointer events, allowing the user to interact with the 3D scene.

Overall, the code provides a solid foundation for building a 3D rendering engine in JavaScript from scratch.

### ENVIROMENTAL FUNCTIONS

The updCanvasSize method updates the canvas size to match the window size and recalculates some properties related to the camera view.

The logInTo_3DMode method logs in to 3D mode by adding event listeners for mouse movement and pointer lock, displaying the canvas, and starting the animation loop.

The logOutFrom_3DMode method logs out from 3D mode by removing event listeners, stopping the animation loop, and hiding the canvas.

The keySwitch method handles keyboard input for movement, but only if the pointer lock element is the canvas.

The startAnimation method starts the animation loop.

The animationLoop method draws a new frame and calls itself recursively at 60fps by default until the animation is stopped.

### DRAWING FUNCTIONS

This code section defines a set of functions for drawing points and lines on a 2D canvas, as well as functions for manipulating a virtual camera in a 3D space.

The clearCanvas function fills the canvas with a background color to reset it for new drawings.

The drawPoint function takes in the x and y coordinates of a point and draws it on the canvas with a specified color.

The drawLine function takes in the starting and ending points of a line and draws it on the canvas with a specified color and line width.

### CAMERA FUNCTIONS

The setDirection_fromR function sets the direction of the virtual camera based on two input angles in radians.

The getDirection_inR function returns the direction of the virtual camera in radians.

The moveForward and moveBack functions move the virtual camera forward and backward respectively by adjusting its coordinates in the 3D space.

The rotateCamera function rotates the virtual camera's direction by specified angles around the X and Y axes.

### SCENE FUNCTIONS

This code defines several functions that are used to draw and manipulate objects in a 3D space.

The showPoint function takes a single point in 3D space and converts its coordinates to 2D screen coordinates. If the point is not visible on the screen, it is not drawn. Otherwise, the point is drawn using a given color.

The showPointsArray function takes an array of points and calls showPoint on each one, effectively drawing all of them on the screen.

The showLine function takes two points in 3D space and converts their coordinates to 2D screen coordinates. It then draws a line connecting the two points on the screen, using a given color and line width.

The showCubeBorder function takes an array of points that define the vertices of a cube and calls showLine to draw the edges of the cube. The cube can be rotated using the cubeRotate function before it is drawn. The color and line width of the cube can also be specified.

The showCoordinatLines function takes an object containing three lines that define the X, Y, and Z axes, and draws them on the screen using their specified colors and line widths.

The drawNewFrame function clears the canvas, draws the coordinate lines, rotates and draws the cube, and is intended to be called repeatedly to create the animation effect.

### CALCULATION FUNCTIONS

These are calculation functions used in a graphics rendering program.

The getFlattenedLine function takes a 3D line as input and returns a 2D line. If both the starting and ending points of the 3D line have a z-coordinate greater than 0, it calculates the 2D points of the flattened line using the getFlattenedPoint function. Otherwise, if both the starting and ending points of the 3D line have a z-coordinate less than 0, it returns the string 'not_seen'. If only one point has a z-coordinate greater than 0, it calculates the 2D point of the flattened line that intersects with the screen using the getScreenIntersectPoint function.

The getFlattenedPoint function takes a 3D point as input and returns a 2D point. It calculates the x and y coordinates of the flattened point based on the distance from the point to the viewer, the distance from the point to the screen, and the viewing angle.

The getScreenIntersectPoint function takes a 3D line as input and returns the point where the line intersects with the screen. It calculates the slope and y-intercept of two lines that are perpendicular to the 3D line and pass through the starting point of the 3D line. It then calculates the x and y coordinates of the intersection point of these two lines. If the 3D line is vertical or horizontal, it handles these cases separately to avoid dividing by zero. Finally, it calculates the x and y coordinates of the intersection point in 2D space based on the viewing angle and screen size.

### MATRIXES FUNCTIONS

These senctions are related to matrix transformations for 3D graphics.

The getRotationMatrixAround_Y, getRotationMatrixAround_X, and getRotationMatrixAround_Z functions return matrices that represent rotation around the Y, X, and Z axis respectively. These matrices are used in the getRotatedPointCoord function to apply rotation to a point's coordinates.

The getRotatedPointCoord function takes a point's coordinates and a rotation matrix as input, and returns the new coordinates of the rotated point. The function iterates over each coordinate of the point and multiplies it by the corresponding values in the rotation matrix to apply the rotation.

Finally, the getNew3D_PointCoods function applies the Y and X angle rotations to the point's coordinates, which are first converted to relative coordinates with respect to the camera position. The function calls getRotationMatrixAround_Y and getRotationMatrixAround_X to obtain the matrices used for the rotations.

### CUBE FUNCTIONS 

This is a JavaScript code for a Cube object, which has two methods: cubeInit() and cubeRotate().

The cubeInit() method initializes the properties of the Cube object, such as its position, size, color, and vertexes. It takes two arguments: center_point (an object with x, y, z properties representing the center point of the cube) and edge_size (a number representing the length of the cube's edges).

The cubeRotate() method takes three optional arguments: Y_angle, X_angle, and Z_angle (numbers representing the angles to rotate the cube around the Y, X, and Z axes, respectively). This method uses matrix multiplication to calculate the new coordinates of each vertex after the rotation, and updates the cube_vertexes property of the Cube object with the new coordinates.

Overall, this code defines a Cube object with methods to initialize and rotate it in 3D space.

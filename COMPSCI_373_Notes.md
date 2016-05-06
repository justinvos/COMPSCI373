# COMPSCI 373 Notes
Justin Vos
## Vectors
A **vector** in \(k\)-space is a \(k\)-tuple, with each term corresponding to the amount in each dimension.

A **dot product** of two vectors is the sum of each product of the corresponding terms.

The **magnitude** of a vector is the scalar length of the vector. Defined as \(|v|=\sqrt{(v\cdot v)}\).  
A vector \(v\) is **normalised** when \(|v|=1\). The normalised \(v\) is defined as \(\hat{v}=\frac{v}{|v|}\).

Vectors \(u\) and \(v\) are **orthogonal** \((90^\circ)\) iff \(u\cdot v=0\).  
Vectors \(u\) and \(v\) are less than \(90^\circ\) apart iff \(u\cdot v>0\).  
Vectors \(u\) and \(v\) are more than \(90^\circ\) apart iff \(u\cdot v<0\).

**Projecting** the vector \(b\) onto \(a\) is defined as \(proj_a(b)=b_a=\frac{b\cdot a}{a\cdot a}\cdot a\).

The **minimum distance from a line** \(L\) to a point \(B\) can be found from \(|c|=|b-b_a|\), where \(b\) is the position vector of B and \(a\) is the direction vector along the line \(L\).

The **area of a parallelogram** defined by the vectors \(a\) and \(b\) is \(|a\times b|\).  
The **volume of a parallelepiped** defined by the vectors \(a\), \(b\) and \(c\) is \((a\times b)\cdot c\).

## Matrices
A \(m\times n\) **matrix** has \(m\) rows and \(n\) columns.

In **matrix multiplication**, each term of the resulting matrix is the dot product of the corresponding row vector and column vector as defined \(A_{ij}=(B_{i1},\cdots ,B_{im})\cdot (C_{1j},\cdots ,C_{nj})^T\) where \(A=BC\).

The **determinant** of a \(2\times 2\) matrix \(M\) is defined as \(det(M)=det\left( \begin{bmatrix}a & b \\ c & d\end{bmatrix}\right)=ad-bc\).

The **inverse** of a \(2\times 2\) matrix \(M\) is \(M^{-1}=\begin{bmatrix}a & b \\ c & d\end{bmatrix}^{-1}=\frac{1}{det(M)}\begin{bmatrix}d & -b \\ -c & a \end{bmatrix}\)

## Planes

A **plane** can be represented in the equation form: \(ax+by+cz+d=0\) or in the vector normal form: \(\begin{pmatrix}a \\ b \\ c \end{pmatrix}\).

The **normal of a plane** is the normalised sum of all the cross products of the adjacent edge vectors in an anti-clockwise direction.

The **distance between a plane** \(P\) and a point \(Q\) can be found using \(\frac{Q\cdot P+d}{|P|}\).

## Matrix Transformations

**Translation**: \(M\times \begin{bmatrix}1 & 0 & t_x \\ 0 & 1 & t_y \\ 0 & 0 & 1\end{bmatrix}\).

**Scale**: \(M\times \begin{bmatrix}s_x & 0 \\ 0 & s_y\end{bmatrix}\).

**Shearing**: \(M\times \begin{bmatrix}1 & s_x\\ s_y & 1\end{bmatrix}\).

**\(90^\circ\) Rotation**: \(M\times \begin{bmatrix}0 & -1 \\ 1 & 0\end{bmatrix}\).

**\(180^\circ\) Rotation**: \(M\times \begin{bmatrix}-1 & 0 \\ 0 & -1\end{bmatrix}\).

**\(-90^\circ\) or \(270^\circ\) Rotation**: \(M\times \begin{bmatrix}0 & 1 \\ -1 & 0\end{bmatrix}\).

## Light
A **spectral density function** (SDF) is a function of energy at different wavelengths.

**Hue** is the dominant wavelength.  
**Luminance** or **brightness** is the total power, the integral of the SDF.  
**Saturation** or **purity** is the amount of luminance in the dominant component.

The **incident light** is the original light before it interacts with the object.  
**Absorbed light** is the light wavelengths that are retained in the object.  
**Transmitted light** is the light wavelengths that travel through and exit the object.  
**Reflected light** is the light wavelengths that bounce off the entry surface.

A **spectral response function** (SRF) is a function of the energy returned from an object at different wavelengths.

\(SDF_{Light\ source}\times SRF=SDF_{Result}\)

## Colour spaces
**CIE XYZ** is a clour space of all the visible colours.

**Additive colour spaces** are used for materials that produce light. They start at black and adding all of the primary colours results in white e.g. RGB.  
**Subtractive colour spaces** are used for materials that reflect light. They start at white and adding all of the primary colours results in black e.g CMYK.

HSL (Hue, Saturation, Lightness) is a colour model representing the RGB colour space as vertical bicone. With the vertical axis representing the lightness, the distance from center as the saturation and the direction from the center as the hue.

HSV (Hue, Saturation, Value) is a colour model representing the RGB colour space as a vertical cone pointing downwards. With the vertical axis representing the value, the distance from the center as the saturation and the direction from center as the hue.

## OpenGL
**OpenGL** (Open Graphics Library) is a cross-language, cross-platform application programming interface (API) for rendering.

**GL** (Graphics Library) is the main function library for polygon rendering.

**GLU** (Graphics Library Utility) contains extra functions such as tessellations of spheres, cones, curved surfaces, etc.

**GLUT** (Graphics Library Utility Toolkit) is not part of the OpenGL specification, provides support for a windowing environment in a window-system independent manner.

The **rendering process** involves:
1. Polygon definition
2. Model-view transformation
3. Illumination
4. Projection transformation
5. Clipping
6. Viewport transformation
7. Rasterisation
8. Display

An OpenGL program has 3 important parts:
* A ```main``` function which initialises the drawing window and sets up the scene and event handling.
* A ```init``` function which defines the scene and the view of the scene. This can be done inside the display function, but is more efficient in its own separate ```init``` method.
* A ```display``` function that draws the scene. Will be performed automatically by calling the ```glutDisplayFunc``` function.

## Creating a drawing window
The ```glutInit``` function initiates a window session with the underlying operating system.  
The ```glutInitDisplayMode``` function specifies the display mode for the window.  
The glutInitWindowSize function sets the width and height in pixels of the window.  
The ```glutInitWindowPosition``` function sets the screen location through x and y co-ordinates.  
The ```glutCreateWindow``` function creates a window with the given title. The size, location and display mode are determined by the most recent calls to their respective functions. This function returns a unique window identifier which can be used to select this particular window later.

## Interacting with a drawing window
The ```glClearColor``` function sets the colour used for clearing the drawing window.  
The ```glMatrixMode``` function specifies which matrix stack to use in subsequent matrix operations.  
The ```glLoadIdentity``` function initialises the matrix stack with an identity matrix.  
The ```gluOrtho2D``` function defines a 2D orthographic projection matrix, which maps a section of the 2D world onto the drawing window.  
The **world-window** is the section of the world displayed.  
The **viewport** is the drawing window on the screen.  
\(\begin{bmatrix} u \\ v \end{bmatrix}=\begin{bmatrix} Ax+C \\ By+D \end{bmatrix}\) where \(A=\frac{v_r-v_t}{w_r-w_l}\), \(B=\frac{v_t-v_b}{w_t-w_b}\), \(C=v_l-Aw_l\), \(D=v_b-Bw_b\).

The ```glClear``` function clears all pixels in the buffer specified by mask.  
The ```glColor3f```, ```glColor3b```, ```glColor3d``` and ```glColor4f``` functions set the colour for subsequent drawing commands.  
The ```glBegin``` and ```glEnd``` functions delimit the vertices that define a primitive or a group of primitives.  
The ```glVertex2fv``` specifies a pointer to an array of two float numbers representing a vertex.  
The ```glPointSize``` function sets the point size.  
The ```glLineWidth``` function sets the line width.  
The ```glFlush``` function empties all buffers, causing all issued commands to be executed as quickly as they are accepted by the actual rendering engine.

Primitive types:
* ```GL_POINTS``` treats each vertex as a single point.
* ```GL_LINES``` treats each pair of vertices as an independent line segment.
* ```GL_LINE_STRIPS``` draws a connected group of line segments from the first vertex to the last.
* ```GL_LINE_LOOP``` draws a connected group of line segments from the first vertex to the last and an extra from the last to the first, completing the loop.
* ```GL_TRIANGLES``` treats each triplet of vertices as one independent triangle.
* ```GL_TRIANGLE_STRIP``` draws a connected group of triangles with the first triangle using the first three vertices and each subsequent triangle using the last two vertices and a new third vertex.
* ```GL_TRIANGLE_FAN``` draws a connected group of triangles with each triangle using the first vertex.
* ```GL_QUADS``` treats each group of four vertices as an independent quadrilateral.
* ```GL_QUAD_STRIP``` draws a connected group of quadrilaterals with the first quadrilateral using the first four vertices and each subsequent quadrilateral using the last two vertices and two new vertices.
* ```GL_POLYGON``` draws a single convex polygon.


## Modelling and rendering
A **polygon mesh** is defined by a set of vertices and a set of faces to create the illusion of a solid 3D object.  
**Manually defined polygon meshes** are created through manually defining each vertex (in anti-clockwise order) to create faces, while this is straightforward, it is impractical for anything more than the most basic meshes.  
**Parametric surfaces** are defined by a function of spline surfaces e.g. Bezier surfaces, non-uniform rational B-spline surfaces, etc.  
**Subdivision surfaces** generate smooth surfaces from course meshes by iteratively subdividing them.  
**Implicit surfaces** are defined on all points by a function, which gives a very small selection of surface shapes.  
**Constructive solid geometry** (CSG) is the combination of simple objects to more complex objects by using set operations (union, intersection, etc.).  
**Point clouds** are the generation of the set of vertices for polygon meshes from laser sensors, however, this approach can take up a large amount of space and can be inaccurate.

An **object modelling environment** is where 3D models or meshes are created.  
An **animation environment** is where models are arranged and animated.  
**Rendering tools** can be used to create previews and photo-realistic images or movies of a scene.

**Backface culling** is the process of removing faces that are not being rendered, thereby increasing processing speed. This can be done in OpenGL using the following two lines of code:
```
glCullFace(GL_BACK);
glEnable(GL_CULL_FACE);
```

## Rendering polygon meshes
The ```glutSolidCube``` function renders a solid cube centered at the origin with the specified length \(size\).  
The ```glutSolidCone``` function renders a solid cone oriented along the z-axis with the base at \(z=0\) and the top at \(z=height\) and with a base radius of \(base\).  
The ```glutSolidSphere``` function renders a solid sphere centered at the origin with the radius \(radius\).  
The ```glutSolidTeapot``` function renders a solid teapot centered at the origin with a diameter of approximately \(2\times size\).  
The ```glutSolidTorus``` function renders a solid torus (doughnut) centered at the origin whose axis is aligned with the z-axis.  
There are also the ```glutSolidTetrahedron```, ```glutSolidOctahedron```, ```glutSolidDodecahedron``` and ```glutSolidIcosahedron``` functions which render their respective solid polygon meshes.

The ```glutWire...``` functions render all the shapes above as a wire frame rather than a solid object.

A **parametric curve** is a 2D curve defined by a set of points \(p(t)=(x(t),y(t))^t\) where \(x(t)\) and \(y(t)\) are functions of the parameter \(t\) over an interval \([t_{min},t_{max}]\).

**Drawing a parametric curve** involves drawing a discrete number of vertices using the parametric curve function and connecting them with line strips.

A **parametric surface** is defined as the set of points \(p(s,t)=\begin{cases}x(s,t)\\y(s,t)\\z(s,t)\end{cases}\).

**Drawing a parametric surface** involves drawing a discrete number of vertices using the parametric curve function and connecting them with quad strips.

A **surface of revolution** is a surface defined by a parametric curve rotating around an axis.


## Transformations in OpenGL
OpenGl has two \(4\times 4\) transformation matrices:
* The **Projection matrix**, defined \(P\), which handles perspective projections and scaling from world co-ordinates to screen co-ordinates.
* The **Model-View matrix**, defined \(M\), which handles both modelling operations and the viewing transformation.

All vertices are multiplied by \(M\) and then \(P\) before the 3D to 2D projection is done.

The ```glMatrixMode``` function selects the matrix to interact with.  
The ```glLoadIdentity``` function loads the identity matrix.  
The ```glLoadMatrixf``` function loads the specified matrix.

The current loaded matrix can be transformed with the following matrices:
* The ```glTranslatef``` function translates by the specified distance parameters.
* The ```glScalef``` function scales the by the specified parameters along each axis.
* The ```glRotatef``` function rotates anti-clockwise around the specified axioms by the specified angle.
* The ```glMultMatrixf``` function is a general purpose matrix.

All transformations are multiplied on the right of the current loaded matrix.

The ```glPushMatrix``` makes a copy of the current top transformation matrix and places the copy on top of the stack.  
The ```glPopMatrix``` removes the top transformation matrix.

Any vertices being drawn will only use the top transformation matrix.

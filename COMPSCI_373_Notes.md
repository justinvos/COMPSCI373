# COMPSCI 373 Notes
Justin Vos
## Geometry
### Vectors
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

## Modelling with Polygonal Meshes
### Rendering polygon meshes
The ```glutSolidCube``` function renders a solid cube centered at the origin with the specified length \(size\).  
The ```glutSolidCone``` function renders a solid cone oriented along the z-axis with the base at \(z=0\) and the top at \(z=height\) and with a base radius of \(base\).  
The ```glutSolidSphere``` function renders a solid sphere centered at the origin with the radius \(radius\).  
The ```glutSolidTeapot``` function renders a solid teapot centered at the origin with a diameter of approximately \(2\times size\).  
The ```glutSolidTorus``` function renders a solid torus (doughnut) centered at the origin whose axis is aligned with the z-axis.  
There are also the ```glutSolidTetrahedron```, ```glutSolidOctahedron```, ```glutSolidDodecahedron``` and ```glutSolidIcosahedron``` functions which render their respective solid polygon meshes.

The ```glutWire..``` functions render all the shapes above as a wire frame rather than a solid object.
### Transformations in OpenGL
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

Any vertices being drawned will only use the top transformation matrix.

A **parametric curve** is a 2D curve defined by a set of points \(p(t)=(x(t),y(t))^t\) where \(x(t)\) and \(y(t)\) are functions of the parameter \(t\) over an interval \([t_{min},t_{max}]\).

**Drawing a parametric curve** involves drawing a discrete number of vertices using the parametric curve function and connecting them with line strips.

A **parametric surface** is defined as the set of points \(p(s,t)=\begin{cases}x(s,t)\\y(s,t)\\z(s,t)\end{cases}\).

**Drawing a parametric surface** involves drawing a discrete number of vertices using the parametric curve function and connecting them with quad strips.

A **surface of revolution** is a surface defined by a parametric curve rotating around an axis.

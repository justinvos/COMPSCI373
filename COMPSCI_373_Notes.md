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

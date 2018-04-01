### Parallelism paradigm shift
Because modern CPUs have multiple cores, and therefore can execute instructions in parallel, nowadays it is more favourable to write code that uses more cycles but has to access memory less because accessing memory is much slower.

Accessing RAM takes thousands of CPU cycles

### Cache optimization
To decrease D-cache misses organise data in contiguous blocks that are as small as possible and access them sequentially (no jumping around within the contiguous memory block).
To decrease I-cache misses keep high performance loops as small as possible and avoid calling functions within innermost loops.

### Dot product
#### Dot product tests
- collinear
- collinear but opposite
- perpendicular
- same direction
- opposite direction

#### Dot product applications
- Enemy in front or behind.
- Height of a point above or below a plane.
  - plane defined by some point q and a normal vector n.
  - p as position of the player.
  - v = p _ q, or the vector pointing from the plane towards the player.
  - v.n projects the position onto the normal vector, giving us the height of the player from the plane.
  - h = (p-q).n 

### Cross product
#### Cross product applications
- Finding a vector perpendicular to two other vectors.
- Finding a matrix representing the object's orientation given the object's local basis vectors.
  - assuming only the object's k_local vector (direction in which it is facing), and assuming the object has no roll about the k_local vector.
  - i_local = normalize(j_world x k_local) *(j_world being the up vector [0,1,0])*.
  - j_local = k_local x i_local.
- Finding a normal to the surface of a triangle/plane.
  - n = normalize((P2 - P1) x (P3 - P1)).
- Physics simulations (torque)
  - Given a force F and a vector r from the centre of mass to the point where the force is applied, torque N = r x F
  
### Linear interpolation (LERP)
L = LERP(A, B, b) = (1 - b)A + bB  where b ranges from 0 to 1

L is the position vector of a point that lies b * 100 perfect of the way along the line from A to B.

### Matrices
#### Transpose
<img src="https://latex.codecogs.com/png.latex?\begin{bmatrix}&space;a&space;&&space;b&space;&&space;c\\&space;d&space;&&space;e&space;&&space;f\\&space;g&space;&&space;h&space;&&space;i&space;\end{bmatrix}^T&space;=&space;\begin{bmatrix}&space;a&space;&&space;d&space;&&space;g\\&space;b&space;&&space;e&space;&&space;h\\&space;c&space;&&space;f&space;&&space;i&space;\end{bmatrix}" title="\begin{bmatrix} a & b & c\\ d & e & f\\ g & h & i \end{bmatrix}^T = \begin{bmatrix} a & d & g\\ b & e & h\\ c & f & i \end{bmatrix}" />

The inverse of an orthonormal (Pure rotation) matrix is it's transpose.

#### Translate
3x3 Matrices do not allow for translations. Instead, 4x4 matrices are used.
To translate a point **r** by a translation **t** we can use the matrix below.
<img src="https://latex.codecogs.com/png.latex?r&space;&plus;&space;t&space;=&space;\begin{bmatrix}&space;r_x&space;&&space;r_y&space;&&space;r_z&space;&&space;1&space;\end{bmatrix}\begin{bmatrix}&space;1&space;&&space;0&space;&&space;0&space;&&space;0\\&space;0&space;&&space;1&space;&&space;0&space;&&space;0\\&space;0&space;&&space;0&space;&&space;1&space;&&space;0\\&space;t_x&space;&&space;t_y&space;&&space;t_z&space;&&space;1&space;\end{bmatrix}" title="r + t = \begin{bmatrix} r_x & r_y & r_z & 1 \end{bmatrix}\begin{bmatrix} 1 & 0 & 0 & 0\\ 0 & 1 & 0 & 0\\ 0 & 0 & 1 & 0\\ t_x & t_y & t_z & 1 \end{bmatrix}" />

When a point or vector is extended from 3 dimensions to 4 dimensions, the w component must be 1 to be written in *homogeneous coordinates*.

#### Transforming direction vectors
Translating a direction vector would alter it's magnitude.
In homogeneous coordinates, we define points to have their w components equal to 1, while direction vectors to have their w components set to 0 to avoid translations.

#### Pure matrices
- Pure translation: <img src="https://latex.codecogs.com/png.latex?r&space;&plus;&space;t&space;=&space;\begin{bmatrix}&space;r_x&space;&&space;r_y&space;&&space;r_z&space;&&space;1&space;\end{bmatrix}\begin{bmatrix}&space;1&space;&&space;0&space;&&space;0&space;&&space;0\\&space;0&space;&&space;1&space;&&space;0&space;&&space;0\\&space;0&space;&&space;0&space;&&space;1&space;&&space;0\\&space;t_x&space;&&space;t_y&space;&&space;t_z&space;&&space;1&space;\end{bmatrix}" title="r + t = \begin{bmatrix} r_x & r_y & r_z & 1 \end{bmatrix}\begin{bmatrix} 1 & 0 & 0 & 0\\ 0 & 1 & 0 & 0\\ 0 & 0 & 1 & 0\\ t_x & t_y & t_z & 1 \end{bmatrix}" />.

- Pure rotations:
  - x rotation: <img src="https://latex.codecogs.com/png.latex?rotate_x(r,\phi)&space;=&space;\begin{bmatrix}&space;r_x&space;&&space;r_y&space;&&space;r_z&space;&&space;1&space;\end{bmatrix}\begin{bmatrix}&space;1&space;&&space;0&space;&&space;0&space;&&space;0\\&space;0&space;&&space;cos\&space;\phi&space;&&space;sin\&space;\phi&space;&&space;0\\&space;0&space;&&space;-sin\&space;\phi&space;&&space;cos\&space;\phi&space;&&space;0\\&space;0&space;&&space;0&space;&&space;0&space;&&space;1&space;\end{bmatrix}" title="rotate_x(r,\phi) = \begin{bmatrix} r_x & r_y & r_z & 1 \end{bmatrix}\begin{bmatrix} 1 & 0 & 0 & 0\\ 0 & cos\ \phi & sin\ \phi & 0\\ 0 & -sin\ \phi & cos\ \phi & 0\\ 0 & 0 & 0 & 1 \end{bmatrix}" />.
  - y rotation: <img src="https://latex.codecogs.com/png.latex?rotate_y(r,\theta)&space;=&space;\begin{bmatrix}&space;r_x&space;&&space;r_y&space;&&space;r_z&space;&&space;1&space;\end{bmatrix}\begin{bmatrix}&space;cos\&space;\theta&space;&&space;0&space;&&space;-sin\&space;\theta&space;&&space;0\\&space;0&space;&&space;1&space;&&space;0&space;&&space;0\\&space;sin\&space;\theta&space;&&space;0&space;&&space;cos\&space;\theta&space;&&space;0\\&space;0&space;&&space;0&space;&&space;0&space;&&space;1&space;\end{bmatrix}" title="rotate_y(r,\theta) = \begin{bmatrix} r_x & r_y & r_z & 1 \end{bmatrix}\begin{bmatrix} cos\ \theta & 0 & -sin\ \theta & 0\\ 0 & 1 & 0 & 0\\ sin\ \theta & 0 & cos\ \theta & 0\\ 0 & 0 & 0 & 1 \end{bmatrix}" />.
  - z rotation: <img src="https://latex.codecogs.com/png.latex?rotate_z(r,\gamma)&space;=&space;\begin{bmatrix}&space;r_x&space;&&space;r_y&space;&&space;r_z&space;&&space;1&space;\end{bmatrix}\begin{bmatrix}&space;cos\&space;\gamma&space;&&space;sin\&space;\gamma&space;&&space;0&space;&&space;0\\&space;-sin\&space;\gamma&space;&&space;cos\&space;\gamma&space;&&space;0&space;&&space;0\\&space;0&space;&&space;0&space;&&space;1&space;&&space;0\\&space;0&space;&&space;0&space;&&space;0&space;&&space;1&space;\end{bmatrix}" title="rotate_z(r,\gamma) = \begin{bmatrix} r_x & r_y & r_z & 1 \end{bmatrix}\begin{bmatrix} cos\ \gamma & sin\ \gamma & 0 & 0\\ -sin\ \gamma & cos\ \gamma & 0 & 0\\ 0 & 0 & 1 & 0\\ 0 & 0 & 0 & 1 \end{bmatrix}" />.

- Scale: <img src="https://latex.codecogs.com/png.latex?rS&space;=&space;\begin{bmatrix}&space;r_x&space;&&space;r_y&space;&&space;r_z&space;&&space;1&space;\end{bmatrix}\begin{bmatrix}&space;s_x&space;&&space;0&space;&&space;0&space;&&space;0\\&space;0&space;&&space;s_y&space;&&space;0&space;&&space;0\\&space;0&space;&&space;0&space;&&space;s_z&space;&&space;0\\&space;0&space;&&space;0&space;&&space;0&space;&&space;1&space;\end{bmatrix}" title="rS = \begin{bmatrix} r_x & r_y & r_z & 1 \end{bmatrix}\begin{bmatrix} s_x & 0 & 0 & 0\\ 0 & s_y & 0 & 0\\ 0 & 0 & s_z & 0\\ 0 & 0 & 0 & 1 \end{bmatrix}" />.
  - To invert a scaling matrix, substitute s_x, s_y, s_z with their reciprocals (1/s_x, 1/s_y, 1/s_z).
  
#### 4x3 Matrices
Since the righmost column of a 4x4 matrix is always [0, 0, 0, 1], the column is often omitted to save memory.

#### Change of basis matrix
A child space position vector P_c can be transformed into a parent-space position vector P_p as follows:

<img src="https://latex.codecogs.com/png.latex?\\P_p&space;=&space;P_cM_{c\rightarrow&space;p}&space;\\\\M_{c\rightarrow&space;p}&space;=&space;\begin{bmatrix}&space;i_C_x&space;&&space;i_C_y&space;&&space;i_C_z&space;&&space;0\\&space;j_C_x&space;&&space;j_C_y&space;&&space;j_C_z&space;&&space;0\\&space;k_C_x&space;&&space;k_C_y&space;&&space;k_C_z&space;&&space;0\\&space;t_C_x&space;&&space;t_C_y&space;&&space;t_C_z&space;&&space;1\\&space;\end{bmatrix}" title="\\P_p = P_cM_{c\rightarrow p} \\\\M_{c\rightarrow p} = \begin{bmatrix} i_C_x & i_C_y & i_C_z & 0\\ j_C_x & j_C_y & j_C_z & 0\\ k_C_x & k_C_y & k_C_z & 0\\ t_C_x & t_C_y & t_C_z & 1\\ \end{bmatrix}" />

- i_c, j_c, k_c are the unit basis vectors along the child space x, y, z axes, in parent space.
- t_c is the translation of the child coordinate system relative to parent space.

Scaling of the child coordinate system is acomplished by scaling the basis vectors i_c, j_c, k_c.

#### Extracting basis vectors from a matrix
Given a model-to-world tranformation matrix, to find a unit vector representing the direction an object is facing (assuming the z-axis points in the direction the object is facing), we can simply extract k_c directly from the model-to-world matrix.

#### Transforming normal vectors
Special care must be taken in order to ensure that the length and perpendicularity properties of normal vectors are maintained.
If a point can be rotated from space A to space B via a 3x3 matrix <img src="https://latex.codecogs.com/png.latex?M_{A\rightarrow&space;B}" title="M_{A\rightarrow B}" />, then a normal vector n will be transformed via the *inverse transpose* of that matrix, <img src="https://latex.codecogs.com/png.latex?(M^{-1}_{A\rightarrow&space;B})^T" title="(M^{-1}_{A\rightarrow B})^T" />. 
However, if the matrix <img src="https://latex.codecogs.com/png.latex?M_{A\rightarrow&space;B}" title="M_{A\rightarrow B}" /> contains only uniform scale and no shear, then the matrix <img src="https://latex.codecogs.com/png.latex?M_{A\rightarrow&space;B}" title="M_{A\rightarrow B}" /> will actually work just fine for any vector including normal.

#### Storing matrices in memory
We have two choices when it comes to storing a matrix in a two-dimensional array. We can either

1. store the vectors (i_c, j_c, k_c, t_c) contiguously in memory (each row contains a single vector) or

2. store the vectors strided in memory (each column contains one vector)

The befinits of approach 1 is that any vector can be addresed simply by indexing into the matrix and interpreting the 4 contiguous values as a 4 element vector.
Approach 2 is sometimes necessary when doing fast matrix-vector multiplies using a vector-enabled SIMD processor.
In most game engines, matrices are stored using approach 1.

```c++
M[0][0]=ix; M[0][1]=iy; M[0][2]=iz; M[0][3]=0.0f;
M[1][0]=jx; M[1][1]=jy; M[1][2]=jz; M[1][3]=0.0f;
M[2][0]=kx; M[2][1]=ky; M[2][2]=kz; M[2][3]=0.0f;
M[3][0]=tx; M[3][1]=ty; M[3][2]=tz; M[3][3]=1.0f;
```

### Quaternions
A matrix is not always ideal to represent a rotation.
1. Requires 9 floats to represent a rotation, which is excessive considering that there are only 3 degrees of freedom.
2. Rotating a vector requires 3 dot products, or a total of 9 multiplications and 6 additions.
3. It's often important to be able to find a rotation that is some % of the way between two known rotations.

A quaternion looks like a 4D vector but behaves differently.
A quaternion can be interpreted as a 4D complex number with a single real axis, written in the form <img src="https://latex.codecogs.com/png.latex?i_{q_x}&plus;j_{q_y}&space;&plus;&space;k_{q_z}&space;&plus;&space;q_w" title="i_{q_x}+j_{q_y} + k_{q_z} + q_w" />.
Or a+bi+cj+dk.
i^2 = j^2 = k^2 = ijk = -1
Unit length quaternions represent 3D rotations.

#### Unit quaternions as rotations
A unit quaternion can be visualized as a 3D vector + scalar coordinate. The vector part is scaled by the sine of the half-angle of the rotation. The scalar part is the cosine of the half-angle. The unit quaternion *q* can be written as follows:

<img src="https://latex.codecogs.com/png.latex?q&space;=&space;[qv&space;\&space;qs]&space;=&space;[a\&space;sin&space;\frac{\theta}{2}&space;\&space;cos&space;\frac{\theta}{2}]" title="q = [qv \ qs] = [a\ sin \frac{\theta}{2} \ cos \frac{\theta}{2}]" />

where *a* is a unit vector along the axis of rotation, and theta is the angle of rotation.

<img src="https://latex.codecogs.com/png.latex?q&space;=&space;[a_x\&space;sin&space;\frac{\theta}{2}&space;\&space;\&space;a_y\&space;sin&space;\frac{\theta}{2}&space;\&space;\&space;a_z\&space;sin&space;\frac{\theta}{2}&space;\&space;\&space;cos&space;\frac{\theta}{2}]" title="q = [a_x\ sin \frac{\theta}{2} \ \ a_y\ sin \frac{\theta}{2} \ \ a_z\ sin \frac{\theta}{2} \ \ cos \frac{\theta}{2}]" />

#### Quaternion multiplication
Given two quaternions *p* and *q*, the product *pq* represents the composite rotation. The product *pq* is refined as follows:

<img src="https://latex.codecogs.com/png.latex?pq&space;=&space;\begin{bmatrix}&space;(p_sq_v&space;&plus;&space;q_sp_v&space;&plus;&space;p_v\&space;X\&space;q_v)&space;&&space;(p_sq_s&space;-&space;p_v&space;.&space;q_v)&space;\end{bmatrix}" title="pq = \begin{bmatrix} (p_sq_v + q_sp_v + p_v\ X\ q_v) & (p_sq_s - p_v . q_v) \end{bmatrix}" />

where p_s, q_s represent the scalar component and p_v, q_v represent the vector component of the quaternion.

#### Quaternion inverse
In order to calculate the inverse of a quaternion we must first defire a quantity known as the *conjugate* (usually denoted q*).

<img src="https://latex.codecogs.com/png.latex?q*&space;=&space;\begin{bmatrix}&space;-q_v&space;&&space;q_s&space;\end{bmatrix}" title="q* = \begin{bmatrix} -q_v & q_s \end{bmatrix}" />

Given this, the inverse quaternion is defined as follows:

<img src="https://latex.codecogs.com/png.latex?q^{-1}&space;=&space;\frac{q*}{\left&space;|&space;q&space;\right&space;|^2}" title="q^{-1} = \frac{q*}{\left | q \right |^2}" />

Since our quaternions are always of unit length (|q| = 1), the inverse and conjugate are identical.
This means that inverting a quaternion is much faster than inverting a 3x3 matrix.

#### Rotating vectors with quaternions

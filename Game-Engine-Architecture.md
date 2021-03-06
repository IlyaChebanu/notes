## Software engineering fundamentals
### Parallelism paradigm shift
Because modern CPUs have multiple cores, and therefore can execute instructions in parallel, nowadays it is more favourable to write code that uses more cycles but has to access memory less because accessing memory is much slower.

Accessing RAM takes thousands of CPU cycles

### Cache optimization
To decrease D-cache misses organise data in contiguous blocks that are as small as possible and access them sequentially (no jumping around within the contiguous memory block).
To decrease I-cache misses keep high performance loops as small as possible and avoid calling functions within innermost loops.

## 3D Math
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
1. Rewrite the vector in quaternion form <img src="https://latex.codecogs.com/png.latex?v&space;=&space;\begin{bmatrix}&space;v_x&space;&v_y&space;&v_z&space;&0&space;\end{bmatrix}" title="v = \begin{bmatrix} v_x &v_y &v_z &0 \end{bmatrix}" />.
2. To rotate a vector *v* by a quaternion *q*
   1. Premultiply the vector by q
   2. Post-multiply by the inverse quaternion (conjugate in this case).
Therefore, the rotated vector <img src="https://latex.codecogs.com/png.latex?v'&space;=&space;rotate(q,&space;v)&space;=&space;qvq^*" title="v' = rotate(q, v) = qvq^*" />.

#### Quaternion multiplication application
To find a unit vector describing the direction an object is traveling, assuming the positive z-axis points toward the front of an object. The forward unit vector of an object in model space is <img src="https://latex.codecogs.com/png.latex?F_M&space;=&space;[0\&space;0\&space;1]" title="F_M = [0\ 0\ 1]" /> by definition. To transform this into world space, take the object's orientation quaternion q and use it with the equation. 
<img src="https://latex.codecogs.com/png.latex?F_W&space;=&space;qF_Mq^*&space;=&space;q[0\&space;0\&space;1\&space;0]q^*" title="F_W = qF_Mq^* = q[0\ 0\ 1\ 0]q^*" />.

#### Quaternion concatenation
Done the same way as matrix concatenation.
<img src="https://latex.codecogs.com/png.latex?v'&space;=&space;q_3\&space;q_2\&space;q_1\&space;v\&space;q_1^*\&space;q_2^*\&space;q_3^*" title="v' = q_3\ q_2\ q_1\ v\ q_1^*\ q_2^*\ q_3^*" />

#### Converting quaternion to a matrix
If <img src="https://latex.codecogs.com/png.latex?q&space;=&space;[qv_x\&space;qv_y\&space;qv_z\&space;qs]&space;=&space;[x\&space;y\&space;z\&space;w]" title="q = [qv_x\ qv_y\ qv_z\ qs] = [x\ y\ z\ w]" />, then we can find *R* as follows:

<img src="https://latex.codecogs.com/png.latex?R&space;=&space;\begin{bmatrix}&space;1-2y^2-2z^2&space;&2xy&plus;2zw&space;&2xz-2yw&space;\\&space;2xy-2zw&space;&&space;1-2x^2-2z^2&space;&2yz&plus;2xw&space;\\&space;2xz&plus;2yw&space;&2yz-2xw&space;&1-2x^2-2y^2&space;\end{bmatrix}" title="R = \begin{bmatrix} 1-2y^2-2z^2 &2xy+2zw &2xz-2yw \\ 2xy-2zw & 1-2x^2-2z^2 &2yz+2xw \\ 2xz+2yw &2yz-2xw &1-2x^2-2y^2 \end{bmatrix}" />

Likewise, given *R*, we can find *q* as follows:
```c++
void matrixToQuaternion(const float R[3][3], float q[/*4*/])
{
  float trace = R[0][0] + R[1][1] + R[2][2];
  
  // check the diagonal
  if (trace > 0.0f)
  {
    float s = sqrt(trace + 1.0f);
    q[3] = s * 0.5f;
    
    float t = 0.5f / s;
    q[0] = (R[2][1] - R[1][2]) * t;
    q[1] = (R[0][2] - R[2][0]) * t;
    q[2] = (R[1][0] - R[0][1]) * t;
  }
  else
  {
    // diagonal is negative
    int i = 0;
    if (R[1][1] > R[0][0]) i = 1;
    if (R[2][2] > R[i][i]) i = 2;
    
    static const int NEXT[3] = {1, 2, 0};
    int j = NEXT[i];
    int k = NEXT[j];
    
    float s = sqrt((R[i][j] - (R[j][j] + R[k][k])) + 1.0f);
    q[i] = s * 0.5f;
    
    float t;
    if (s != 0.0) t = 0.5f / s;
    else t = s;
    
    q[3] = (R[k][j] - R[j][k]) * t;
    q[j] = (R[j][i] + R[i][j]) * t;
    q[k] = (R[k][i] + R[i][k]) * t;
  }
}
```
For even faster methods, http://www.euclideanspace.com/maths/geometry/rotations/conversions/matrixToQuaternion/index.html

#### Rotational linear interpolation
Easiest and least computationally intensive approach is to LERP a 4D vector.
<img src="https://latex.codecogs.com/png.latex?LERP(q_A,&space;q_B,&space;\beta)&space;=&space;\frac{(1&space;-&space;\beta)q_A&space;&plus;&space;\beta&space;q_B}{\left&space;|&space;(1-\beta)q_A)&space;&plus;&space;\beta&space;q_B&space;\right&space;|}&space;=&space;normalize\left&space;(&space;\begin{bmatrix}&space;(1-\beta)q_A_x)&space;&plus;&space;\beta&space;q_B_x\\&space;(1-\beta)q_A_y)&space;&plus;&space;\beta&space;q_B_y\\&space;(1-\beta)q_A_z)&space;&plus;&space;\beta&space;q_B_z\\&space;(1-\beta)q_A_w)&space;&plus;&space;\beta&space;q_B_w&space;\end{bmatrix}^T&space;\right&space;)" title="LERP(q_A, q_B, \beta) = \frac{(1 - \beta)q_A + \beta q_B}{\left | (1-\beta)q_A) + \beta q_B \right |} = normalize\left ( \begin{bmatrix} (1-\beta)q_A_x) + \beta q_B_x\\ (1-\beta)q_A_y) + \beta q_B_y\\ (1-\beta)q_A_z) + \beta q_B_z\\ (1-\beta)q_A_w) + \beta q_B_w \end{bmatrix}^T \right )" />

#### Spherical LERP
LERP interpolates along a chord of the 4D hypersphere, rather than along the surface. This leads to rotation animations that do not have consistent angular speed when the *beta* parameter is changing at a constant rate. The rotation appears slower at the start and towards the end of the animation.
To solve this problem, spherical linear interpolation, or **SLERP** can be used.
The formula for SLERP is:

<img src="https://latex.codecogs.com/png.latex?\\SLERP(p,&space;q,&space;\beta)&space;=&space;w_pp&space;&plus;&space;w_qq&space;\\&space;\\where&space;\\&space;\\w_p&space;=&space;\frac{sin(1-\beta)\theta}{sin(\theta)},&space;\\&space;\\w_q&space;=&space;\frac{sin(\beta\theta)}{sin(\theta)}" title="\\SLERP(p, q, \beta) = w_pp + w_qq \\ \\where \\ \\w_p = \frac{sin(1-\beta)\theta}{sin(\theta)}, \\ \\w_q = \frac{sin(\beta\theta)}{sin(\theta)}" />

Cosine of the angle between any unit-length quaternions can be found by taking their 4D dot product. Knowing cos theta, we can calculate theta and the sines.

<img src="https://latex.codecogs.com/png.latex?\\cos(\theta)&space;=&space;p.q&space;=&space;p_xq_x&space;&plus;&space;p_yq_y&space;&plus;&space;p_zq_z&space;&plus;&space;p_wq_w&space;\\\theta&space;=&space;cos^{-1}(p.q)" title="\\cos(\theta) = p.q = p_xq_x + p_yq_y + p_zq_z + p_wq_w \\\theta = cos^{-1}(p.q)" />

SLERP is slower than LERP.

### Comparison of rotational representations
#### Euler angles
Typically represented as a 3D vector (Y, P, R) yaw, pitch, roll.

PROS:

- Simple, small size, intuitive.
- Easily interpolate simple rotations about a single axis.

CONS:

- Cannot be interpolated easily when the rotation is about an arbitrarily oriented axis.
- Prone to gimbal lock.
- Order in which the rotations are performed matters.
- Depend upon the mapping from the x, y, z axes onto the natural front, left, up directions for the object being rotated.

#### 3x3 Matrices
PROS:

- Convenient and effective rotational representation.
- Does not suffer from gimbal lock.
- Represents arbitrary rotations uniquely.
- Rotations can be applied to points and vectors in a straighforward manner through matrix multiplication.
- Most CPUs and GPUs have built-in support for hardware accelerated dot products and matrix multiplication.
- Rotations reversable using the inverse matrix, which for pure rotations is just finding the transpose.
- 4x4 matrices offer a way to represent transformations, rotations and scaling in a consistent way.

CONS:

- Not intuitive.
- Not easily interpolated.
- Takes up a lot of storage.

#### Axis + Angle
Rotations can be represented by defining a unit vector as the axis of rotation, plus a scalar for the angle of rotation.

PROS:

- Intuitive.
- Compact.

CONS:

- Cannot be easily interpolated.
- Cannot be applied to points and vectors in a straighforward way, needs to be converted to a matrix or quaternion first.

#### Quaternions
Analogous to the axis + angle representation. Primary difference between the two is that quaternion's axis of rotation is scaled by the sine of the half-angle of rotation, and instead of storing the angle in the fourth component, the cosine of the half-angle is stored instead.

PROS:

- Permits rotations to be concatenated and applied directly to points and vectors via multiplication.
- Permits rotations to be easily interpolated via LERP or SLERP.
- Small size.

#### SQT Transformations
When a quaternion is combined with a translation vector and a scale factor, then we have a viable alternative to a 4x4 matrix.
SQT = [*s* *q* *t*]
Where s can either be a scalar or a vector for non-uniform scaling.
- Smaller size (8 / 10 floats, as opposed to 12 for a 4x3 matrix).
- Easily interpolated.

#### Dual quaternions
A *rigid transformation* involves a rotation and translation, a "corkscrew" motion. These can be represented using dual quaternions. 
- LERP blending can be performed in constant speed, shortest path, coordinate invariant manner, similar to using LERP for translations and SLERP for rotational quaternions.
- Like an ordinary quuaternion, except the four components are dual numbers instead of real-valued numbers.
  - A dual number can be written as the sum of a non-dual part and a dual part <img src="https://latex.codecogs.com/png.latex?\hat{a}&space;=&space;a&space;&plus;&space;\varepsilon&space;b" title="\hat{a} = a + \varepsilon b" />. <img src="https://latex.codecogs.com/png.latex?\varepsilon" title="\varepsilon" /> is called the dual unit, defined in a way that <img src="https://latex.codecogs.com/png.latex?\varepsilon^2&space;=&space;0" title="\varepsilon^2 = 0" /> without <img src="https://latex.codecogs.com/png.latex?\varepsilon" title="\varepsilon" /> being 0. 
  - Because each dual number can be represented by two real numbers, a dual quaternion can be represented by a 8D vector.
  - It can also be represented as the sum of two ordinary quaternions: <img src="https://latex.codecogs.com/png.latex?\hat{q}&space;=&space;q_a&space;&plus;&space;\varepsilon&space;q_b" title="\hat{q} = q_a + \varepsilon q_b" />.

Dual quaternion paper: https://www.cs.tcd.ie/publications/tech-reports/reports.06/TCD-CS-2006-46.pdf/

### Other useful mathematical objects
#### Lines, rays, segments
An infinite line can be represented by a point *P* plus a unit vector *u* in the direction of the line.
L(t) = P + tu, refer to parametrization in Linear Algebra notes.

A ray is a line that extends to infinity in only one direction. This can be expressed with L(t) and a constraint t >= 0.

A segment is bound at both ends by *P0* and *P1*, and can also be represented using L(t) in two ways:
1. L(t) = P0 + tu, where 0 <= t <= |P1-P0|.
2. L(t) = P0 + t(P1-P0), where 0 <= t <= 1.

Option 2 is more convenient, as we don't have to store |P1-P0| in memory.

#### Spheres
Spheres are described as a point *C* and a radius *r*. This packs nicely into a four-element vector [Cx Cy Cz r].

#### Planes
The equation of a plane is often written as follows:
Ax + By + Cz + D = 0
This equation is only satisfied for the points [x y z] that lie on the plane.
Planes can be represented by a point *P0* and a normal vector *n*.
[A B C] lies in the direction of the normal. If that vector is normalized, we get *n*, and the normalized parameter <img src="https://latex.codecogs.com/png.latex?d&space;=&space;D/\sqrt{A^2&space;&plus;&space;B^2&space;&plus;&space;C^2}" title="d = D/\sqrt{A^2 + B^2 + C^2}" />.

To test whether an arbitrary point *P* lies on the plane, we find the signed distance from point *P* to the origin along the normal *n*, and if this signed distance is equal to the signed distance d = -n.P0 from the plane from the origin, then *P* must lie on the plane. Expanding some terms:

signed distance *P* to origin = signed distance plane to origin

<img src="https://latex.codecogs.com/png.latex?\\n\cdot&space;P&space;=&space;n\cdot&space;P_0&space;\\n\cdot&space;P&space;-&space;n\cdot&space;P_0&space;=&space;0&space;\\ax&space;&plus;&space;by&space;&plus;&space;cz&space;-&space;n\cdot&space;P_0&space;=&space;0&space;\\ax&space;&plus;&space;by&space;&plus;&space;cz&space;&plus;&space;d&space;=&space;0" title="\\n\cdot P = n\cdot P_0 \\n\cdot P - n\cdot P_0 = 0 \\ax + by + cz - n\cdot P_0 = 0 \\ax + by + cz + d = 0" />

To describe a plane we only need the normal vector *n* and the distance from the origin *d*. the four element vector [nx ny nz d] is a compact way to represent a plane in memory.

#### Axis-Aligned bounding boxes
An AABB can be represented by a six-element vector containing the minimum and maximum coordinates along each of the 3 principal axes, <img src="https://latex.codecogs.com/png.latex?\begin{bmatrix}&space;x_{min}&space;&&space;x_{max}&space;&y_{min}&space;&y_{max}&space;&z_{min}&space;&z_{max}&space;\end{bmatrix}" title="\begin{bmatrix} x_{min} & x_{max} &y_{min} &y_{max} &z_{min} &z_{max} \end{bmatrix}" /> or two points P_min and P_max.
To test whether a point *P* is inside or outside any given AABB we simply test if all of the following are true:

<img src="https://latex.codecogs.com/png.latex?\\&space;P_x&space;\geq&space;x_{min}\&space;and\&space;P_x&space;\leq&space;x_{max}\&space;and&space;\\&space;P_y&space;\geq&space;y_{min}\&space;and\&space;P_y&space;\leq&space;y_{max}\&space;and&space;\\&space;P_z&space;\geq&space;z_{min}\&space;and\&space;P_z&space;\leq&space;z_{max}" title="\\ P_x \geq x_{min}\ and\ P_x \leq x_{max}\ and \\ P_y \geq y_{min}\ and\ P_y \leq y_{max}\ and \\ P_z \geq z_{min}\ and\ P_z \leq z_{max}" />

Because these tests are inexpensive, AABBs are often used as an "early out" collision check. if the AABBs of two objects do not intersect, then there is no need to do a more detailed collision test.

#### Oriented bounding boxes
An OBB is a cuboid that has been oriented so it aligns in some way with the object it bounds.
Usually aligns with the local axes of the object.
A technique to test for collision is to transform a point into the OBB's aligned coordinate system and then use the AABB intersection test.

#### Frusta
A frustum is a group of 6 planes that define a truncated pyramid shape.
Conveniently defines the viewable region.
Testing whether a point lies inside a frustum involves using the dot products to determine whether the point lies on the front or back side of each plane. If it lies inside all six planes, it is inside the frustum.
A helpful trick is to transform the world-space point by applying the camera's perspective projection. In this space (homogeneous clip space), the frustum is just an AABB.

#### Convex polyhedral regions
A convex polyhedral region is defined by an arbitrary set of planes, all with normals pointing inward or outward. Tests are similar to a frustum test, but with more planes. Convex regions are useful for arbitrarily shaped trigger regions.

### Hardware-Accelerated SIMD math
(S)ingle (I)nstruction (M)ultiple (D)ata.
Allows common vector operations such as dot products and matrix multiplication to be performed extremely quickly.
Streaming SIMD Extentions, or SSE instructions, utilize 128-bit registers that can contain integer or IEEE floats.
The SSE mode most commonly used by game engines is the packed 32-bit floating-point mode. In this mode, four 32-bit values are packed into a single 128-bit register.

```
addps xmm0, xmm1
```
adds four floats in xmm0 register to the four floats in xmm1 and stores the results back into xmm0.
```
xmm0.x = xmm0.x + xmm1.x;
xmm0.y = xmm0.y + xmm1.y;
xmm0.z = xmm0.z + xmm1.z;
xmm0.w = xmm0.w + xmm1.w;
```

Moving data between x87 FPU registers and SSE registers is slow. To minimize the costs of going back and forth between memory, x87 FPU registers and SSE registers, most SIMD math libraries do their best to leave data in the SSE registers for as long as possible. Even scalar values are left in the SSE registers. For example, after a dot product between two vectors produces a scalar, we leave the result in an SSE register as it can be used later in other vector calculations without incurring a transfer cost. Scalars are represented by duplicating the single floating-point value across all four slots.

#### \_\_m128 data type
Visual studio provides a data type called \_\_m128. In many cases, variables of this type will be stored in RAM. But when used in calculations, the vaules are manipulated directly in the SSE regiters.
Declaring local variables and function arguments of type \_\_m128 often results in the compiler storing the values directly in SSE registers, rather than on the stack.

Initializing an \_\_m128 is done as follows:
```
__m128 v = _mm_set_ps(-1.0f, 2.0f, 0.5f, 1.0f);
```

#### SSE Intrinsics
In order to use \_\_m128 and SSE intrinsics, the .cpp file must `#include <xmmintrin.h>`.

To add two \_\_m128 values:
```c++
__m128 addWithIntrinsics(const __m128 a, const __m128 b) 
{
  return _mm_add_ps(a, b);
}
```

Testing the function:
```c++
#include <xmmintrin.h>

__m128 addWithIntrinsics(const __m128 a, const __m128 b) 
{
  return _mm_add_ps(a, b);
}

void testSSE()
{
  // float arrays must be 16-byte aligned to avoid crashes or performance hits.
  __declspec(align(16)) float A[4];
  __declspec(align(16)) float B[4] = {8.0f, 6.0f, 4.0f, 2.0f};
  __declspec(align(16)) float C[4];
  
  // set a = (1, 2, 3, 4) from literals
  // load b = (2, 4, 6, 8) from float array
  // Float array backwards due to Intel CPUs being little-endian
  __m128 a = _mm_set_ps(1.0f, 2.0f, 3.0f, 4.0f);
  __m128 b = _mm_load_ps(&B[0]);
  
  __m128 c = addWithIntrinsics(a, b);
  
  // store the original values back for printing
  _mm_store_ps(&A[0], a);
  _mm_store_ps(&B[0], b);
  
  // store result into float array
  _mm_store_ps(&C[0], c);
  
  // inspect the results
  // results backwards due to little-endian
  printf("a = %g %g %g %g\n", A[0], A[1], A[2], A[3]);
  printf("b = %g %g %g %g\n", B[0], B[1], B[2], B[3]);
  printf("c = %g %g %g %g\n", C[0], C[1], C[2], C[3]);
}
```

#### Vector-Matrix multiplication with SSE
Multiplication involves taking the dot product of the row vector *v* with the columns of matrix *M*. However this is inefficient using SSE registers and instead we multiply the components of *v* (vx, vy, vz, vw) with the rows of the matrix *M*.
Since we're multiplying each individual component, we need to replicate the values of vx, vy, vz and vw across an SSE register [vx vx vx vx] to be able to multiply by a row.
The code below defines macros to replicate the components using the `_mm_shuffle_ps()` intrinsic.

```c++
#define SHUFFLE_PARAM(x, y, z, w) ((x) | ((y) << 2) | ((z) << 4) | ((w) << 6))
#define _mm_replicate_x_ps(v) _mm_shuffle_ps((v), (v), SHUFFLE_PARAM(0, 0, 0, 0))
#define _mm_replicate_y_ps(v) _mm_shuffle_ps((v), (v), SHUFFLE_PARAM(1, 1, 1, 1))
#define _mm_replicate_z_ps(v) _mm_shuffle_ps((v), (v), SHUFFLE_PARAM(2, 2, 2, 2))
#define _mm_replicate_w_ps(v) _mm_shuffle_ps((v), (v), SHUFFLE_PARAM(3, 3, 3, 3))
```

Given these, vector-matrix multiplication can be performed as follows:

```c++
__m128 mulVectorMatrix(
  const __m128& v,
  const __m128& Mrow0,
  const __m128& Mrow1,
  const __m128& Mrow2,
  const __m128& Mrow3)
{
  const __m128 xxxx = _mm_replicate_x_ps(v);
  const __m128 yyyy = _mm_replicate_y_ps(v);
  const __m128 zzzz = _mm_replicate_z_ps(v);
  const __m128 wwww = _mm_replicate_w_ps(v);
  
  const __m128 xMrow0 = _mm_mul_ps(xxxx, Mrow0);
  const __m128 yMrow1 = _mm_mul_ps(yyyy, Mrow1);
  const __m128 zMrow2 = _mm_mul_ps(zzzz, Mrow2);
  const __m128 wMrow3 = _mm_mul_ps(wwww, Mrow3);
  
  __m128 result = _mm_add_ps(xMrow0, yMrow1);
  result        = _mm_add_ps(result, zMrow2);
  result        = _mm_add_ps(result, wMrow3);
  
  return result;
}
```

On some CPUs the code above can be optimized further by using multiply-and-add instruction `madd`. SSE doesn't support a `madd` instruction. However it can be faked with a macro.

```c++
#define _mm_madd_ps(a, b, c) _mm_add_ps(_mm_mul_ps((a), (b)), (c))

__m128 mulVectorMatrix(const __m128 v, const __m128 Mrow[4])
{
  __m128 result;
  
  result = _mm_mul_ps(_mm_replicate_x_ps(v), Mrow[0]);
  result = _mm_madd_ps(_mm_replicate_y_ps(v), Mrow[1], result);
  result = _mm_madd_ps(_mm_replicate_z_ps(v), Mrow[2], result);
  result = _mm_madd_ps(_mm_replicate_w_ps(v), Mrow[3], result);
  
  return result
}
```

4x4 Matrix-Matrix multiplication can be performed using a similar approach. When calculating P = AB, treat each row of A as a vector and multiply it with the rows of B as done in `mulVectorMatrix()`, adding the results of each dot product to produce the corresponding row in the product P.

### Random number generation
#### Mersenne Twister
SFMT (SIMD-oriented fast Mersenne Twister)

#### Mother-of-All
Faster than Mersenne Twister with a period of 2^250.

#### Xorshift
Between Mother-of-All and Mersenne Twister in terms of randomness, but runs faster than Mother-of-All.


## Engine support systems
### Subsystem start-up and shut-down
#### C++ static initialization order
In c++, global and static objects are constructed before the program's entry point (main()) is called in an unpredictable order. Same goes for the destructors after main() returns.
#### Construct on demand
A static variable declared within a function will not be constructed before main(), but rather on the first invocation of the function. so if our global singleton is function-static, we can control the order of construction for our global singletons.

```c++
class RenderManager
{
  public:
    // get the one and only instance
    static RenderManager& get()
    {
      static RenderManager sSingleton;
      return sSingleton;
    }
    
    RenderManager()
    {
      // starting up other managers we depend on by calling their get() functions first
      VideoManager::get();
      TextureManager::get();
      
      // now start up the render manager
      // ...
    }
    
    ~RenderManager()
    {
      // shut down the render manager
      // ...
    }
};
```

Many software engineering textbooks suggest this design or a variant involving dynamic allocation of the singleton as shown below:

```c++
static RenderManager& get()
{
  static RenderManager* gpSingleton = NULL;
  if (gpSingleton == NULL) gpSingleton = new RenderManager;
  ASSERT(gpSingleton);
  return *gpSingleton;
}
```

However, this still gives us no way to control the destruction order.

#### A simple approach that works
If we want to stick with the idea of singleton managers for our subsystems, one approach is to define explicit start-up and shut-down functions for each singleton manager class like so:

```c++
class RenderManager
{
  public:
    RenderManager()
    {
      // nothing
    }
    
    ~RenderManager()
    {
      // nothing
    }
    
    void startUp()
    {
      // start up the manager ...
    }
    
    void shutDown()
    {
      // shut down the manager ...
    }
    //...
};

class PhysicsManager { /* similar */ };
class MemoryManager { /* similar */ };
// ...

RenderManager     gRenderManager;
PhysicsManager    gPhysicsManager;
MemoryManager     gMemoryManager;
// ...

int main(int argc, const char* argv)
{
  // Start up engine systems in the correct order
  gMemoryManager.startUp();
  gRenderManager.startUp();
  gPhysicsManager.startUp();
  // ...
  
  // Run the game
  gSimulationManager.run();
  
  // Shut down everything, in reverse order
  // ...
  gPhysicsManager.shutDown();
  gRenderManager.shutDown();
  gMemoryManager.shutDown();
  
  return 0;
}
```

Other "more elegant" ways to accomplish this include having each manager register itself into a global priority queue and then walk the queue to start up all the managers in the proper order. But, the brute-force approach always wins out because:

- It's simple and easy to implement.
- It's explicit.
- It's easy to debug and maintain.

Refer to page 236 for OGRE example.

### Memory management
Memory affects performance in 2 ways:
1. Dynamic memory allocation via `malloc()` or `new` is a very slow operation. Performance can be improved by avoiding dynamic allocation or by making use of custom memory allocators.
2. Performance is often dominated by a CPU's memory access patterns. data that is located in small, contiguous blocks can be operated on much more efficiently by the CPU.

#### Optimizing dynamic memory allocation
On most operating systems a call to malloc() or free() must context-switch from user mode into mernel mode, process the request and then switch back. These context switches can be expensive.
A rule of thumb for game development is:
- Keep heap allocation to a minimum, and never allocate from the heap within a tight loop.

A custom allocator can satisfy requests from a preallocated memory block (using `malloc()` or `new`, or declared as a global variable). This avoids context switching.
By making assumptions about its usage patterns, a custom allocated can be much more efficient than a general-purpose heap allocator.

#### Stack-based allocators
Many games allocate in a stack-like fashion. Whenever a new game level is loaded, memory is allocated for it. Once the level has been loaded, little or no allocation occurs. At the conclusion of the level, its data is unloaded and all of its memory can be freed.
A stack allocator is easy to implement. Simply allocate a large contiguous block of memory using `malloc()` or `new`, or by declaring a global array of bytes. A pointer to the top of the stack is maintained. Each allocation request simply moves the pointer up by the requested number of bytes. The most recently allocated block can be freed by simply moving the top pointer back down.

```c++
class StackAllocator
{
  public:
    // Stack marker represents the current top of the stack. You can only roll back to a marker.
    typedef U32 Marker;
    
    // Constructs a stack allocated with the given total size
    explicit StackAllocator(U32 stackSize_bytes);
    
    // Allocates a new block from stack top
    void* alloc(U32 size_bytes);
    
    Marker getMarker();
    
    void freeToMarker(Marker marker);
    
    void clear();
  private:
    // ...
};
```

#### Double-ended stack allocators
A single memory block can contain two stack allocators, one that allocates up from the bottom of the block and one that allocates down from the top of the block.
In midway's Hydro Thunder arcade game, the bottom of the stack is used for loading and unloading levels, while the top stack is used for temporary memory bolcks that are allocated and freed every frame.

#### Pool allocators
It's quite common in game engine programming to allocate lots of small blocks of memory, each of which the same size. For example:
- Allocate/free matrices.
- Iterators.
- Links in a linked list.
- Renderable mesh instances.

A pool allocator works by preallocating a large block of memory whose size is an exact multiple of the size of the elements that will be allocated.
A pool of 4x4 matrices would be a multiple of 64 bytes.
Each element within the pool is added to a linked list of free elements. When the pool is initialized, the free list contains all of the elements. Whenever an allocation request is made, we grab the next free element off the free list and return it. When an element is freed, we tack it back onto the free list. 

#### Aligned allocations
To align blocks, allocate extra memory than was requested and adjust the address of the memory block upward.
- Determine the amount by which the block's address must be adjusted by masking off the least-significant bits of the original block's memory address.
- AND the original address with the mask to get the amount by which the block is misaligned.
- Subtract alignment bytes size from that result, and add it to the original address.

```c++
void* allocateAligned(size_t size_bytes, size_t alignment)
{
  ASSERT((alignment & (alignment - 1)) == 0); // power of 2
  
  // Determine total amount of memory to allocate
  size_t expandedSize_bytes = size_bytes + alignment;
  
  uintptr_t rawAddress - reinterpret_cast<uintptr_t>(allocateUnaligned(expandedSize_bytes));
  
  size_t mask = (alignment - 1);
  uintptr_t misalignment = (rawAddress & mask);
  ptrdiff_t adjustment = alignment - misalignment;
  
  uintptr_t alignedAddress = rawAddress + adjustment;
  
  U8* pAlignedMem = reinterpret_cast<U8*>(alignedAddress);
  pAlignedMem[-1] = static_cast<U8>(adjustment);
  
  return static_cast<void*>pAlignedMem);
}
```

```c++
void freeAligned(void* pMem)
{
  const U8* pAlignedMem = reinterpret_cast<const U8*>(pMem);
  uintptr_t alignedAddress = reinterpret_cast<uintptr_t>(pMem);
  ptrdiff_t adjustment = static_cast<ptrdiff_t>(pAlignedMem[-1);
  uintptr_t rawAddress = alignedAddress - adjustment;
  void* pRawMem = reinterpret_cast<void*>(rawAddress);
  
  freeUnaligned(pRawMem);
}
```

#### Single frame allocators
A single-frame allocator is implemented by allocating a block of memory and managing it with a stack allocator. At the beginning of each frame the stack's top pointer is cleared to the bottom of the block.

#### Double buffered allocators
Create two single-frame allocators and swap back and forth between them on each frame. Similar to OpenGL's swap buffers.
Useful for caching results of asynchronous processing.

#### Memory fragmentation
Detrimental effects of memory fragmentation can be avoided by using stack and/or pool allocators.
- Stack allocations are always contiguous.
- Pool allocators do bbecome fragmented, but requests can never fail as all blocks are the exact same size.

#### Defragmentation
When differently sized objects are being allocated and freed in random order, neither stack-based or pool-based allocators can be used. In this case, fragmentation can be avoided by periodically defragmenting the heap.
Defragmentation involves shifting allocated blocks from higher memory addresses down to lower addresses.
The tricky part is that allocated blocks of memory are being moved around. If anyone has a pointer into one of the blocks, then moving the block will invalidate the pointer. The solution is to patch any and all pointers into a shifted memoru block so that they point to the correct new address. This is known as pointer relocation. In order to support memory defragmentation, smart pointers or handles should be used.

Defragmentation can be a slow operation, however it can be amortized over many frames by allowing up to N allocated blocks to be shifted each frame, for some small value N like 8 or 16. As long as allocations and deallocations aren't happening at a faster rate than defragmentation shifts, the heap will remain mostly defragmented at all times.

### Containers
Common container data types include:

- Array. `int a[5]`
- Dynamic array. `std::vector`
- Linked list. `std::list`
- Stack. `std::stack`
- Queue. `std::queue`
- Deque. Double ended queue `std::deque`
- Tree. 
- Binary search tree.
- Binary heap.
- Priority queue. `std::priority_queue`
- Dictionary. `std::map, std::hash_map`
- Set.
- Graph.
- Directed acyclic graph.

Container operations:

- Insert.
- Remove.
- Sequential access (iteration).
- Random access.
- Find.
- Sort.

#### Iterators
```c++
void processArray(int container[], int numElements)
{
  int* pBegin = &container[0];
  int* pEnd = &container[numElements];
  
  for (int* p = pBegin; p != pEnd; p++)
  {
    int element = *p;
    // do stuff ...
  }
}

void processList(std::list<int>& container)
{
  std::list<int>::iterator pBegin = container.begin();
  std::list<int>::iterator pEnd = container.end();
  std::list<int>::iterator p;
  
  for (p = pBegin; p != pEnd; p++)
  {
    int element = *p;
    // do stuff ...
  }
}
```

### Strings
#### Unicode under windows
`wchar_t` is used exclusively for UTF-16.
`char` is used for ANSI/UTF-8 strings.

### Resources and file system
#### Synchronous file I/O
Both of the standard C file I/O libraries are synchronous. The following code snippet demonstrates how the entire contents of a file might be read into an in-memory buffer using the synchronous I/O function fread().
```c++
bool syncReadFile(const char* filePath, U8* buffer, size_t bufferSizze, size_t& rBytesRead)
{
  FILE* handle = fopen(filePath, "rb");
  if (handle)
  {
    // Block occurs here until all the data has been read.
    size_t bytesRead = fread(buffer, 1, bufferSize, handle);
    int err = ferror(handle); // get the error if one occurred.
    fclose(handle);
    
    if (err == 0)
    {
      rBytesRead = bytesRead;
      return true;
    }
  }
  rBytesRead = 0
  return false;
}

void main(int argc, const char* argv[])
{
  U8 testBuffer[512];
  size_t bytesRead = 0;
  
  if (syncReadFile("C:\\testfile.bin", testBuffer, sizeof(testBuffer), bytesRead))
    printf("success: read %u bytes\n", bytesRead);
}
```

#### Asynchronous file I/O
Streaming refers to the act of loading data in the background while the main program continues to run. A load screen free experience can be provided by streaming the next level in the background while the game is being played. Audio and texture data are the most commonly streamed types of data.
To support streaming, asynchronous file I/O is used.
In the following example, the function `asyncReadFile()` returns immediately, and the data is not present in the buffer until the callback function `asyncReadComplete()` has been called by the I/O library.
```c++
 AsyncRequestHandle g_hRequest;
 U8 g_asyncBuffer[512];
 
 static void asyncReadComplete(AsyncRequestHandle hRequest);
 
 void main(int argc, const char* argv[])
 {
  AsyncFileHandle hFile = asyncOpen("C:\\testfile.bin");
  
  if (hfile)
  {
    g_hRequest = asyncReadFile(
      hFile,
      g_asyncBuffer,
      sizeof(g_asyncBuffer),
      asyncReadComplete);
  }
  // simulate doing real work
  for (;;)
  {
    OutputDebugString("zzz...\n");
    Sleep(50);
  }
 }
 
 // Will be called when the data has been read
 static void asyncReadComplete(AsyncRequestHandle hRequest)
 {
  if (hRequest == g_hRequest && asyncWasSuccessful(hRequest))
  {
    size_t bytes = asyncGetBytesReadOrWritten(hRequest);
  
    char msg[256];
    snprintf(msg, sizeof(msg), "async success, read %u bytes\n", bytes);
    OutputDebugString(msg);
  }
 }
```

Most async I/O libraries permit the program to fait for an I/O operation to complete after the request was made. This is useful in some situations where only a limited amount of work can be done before the results are needed to proceed.
```c++
U8 g_asyncBuffer[512];
 
void main(int argc, const char* argv[])
{
  AsyncRequestHandle hRequest = ASYNC_INVALID_HANDLE;
  AsyncFileHandle hFile = asyncOpen("C:\\testfile.bin");
  
  if (hfile)
    hRequest = asyncReadFile(hFile, g_asyncBuffer, sizzeof(g_asyncBuffer), NULL); // no callback
  
  for (int i = 0; i < 10; i++)
  {
    OutputDebugString("zzz...\n");
    Sleep(50);
  }
  
  asyncWait(hRequest); // Can't do anything futher until we have  the data.
  
  if (asyncWasSuccessful(hRequest))
  {
    size_t bytes = asyncGetBytesReadOrWritten(hRequest);
    
    char msg[256];
    snprintf(msg, sizeof(msg), "async success, read %u bytes\n", bytes);
    OutputDebugString(msg);
  }
}
```

Some async libraries allow you to set deadlines on a request and specify what happens when a request misses its deadline.

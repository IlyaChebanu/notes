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


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

## Length of vector

<img src="https://latex.codecogs.com/png.latex?\left&space;\|&space;x&space;\right&space;\|" title="\left \| x \right \|" /> denotes the **Length of x**

<img src="https://latex.codecogs.com/png.latex?\left&space;\|&space;x&space;\right&space;\|&space;=&space;\sqrt{x_{1}^{2}&space;&plus;&space;x_{2}^{2}&space;&plus;&space;...&space;&plus;&space;x_{n}^{2}}" title="\left \| x \right \| = \sqrt{x_{1}^{2} + x_{2}^{2} + ... + x_{n}^{2}}" />

## Distance between vectors

Distance from x to y = <img src="https://latex.codecogs.com/png.latex?\left&space;\|&space;x&space;-&space;y&space;\right&space;\|" title="\left \| x - y \right \|" />

## Inner product

<img src="https://latex.codecogs.com/png.latex?\left&space;\langle&space;x,&space;y&space;\right&space;\rangle&space;=&space;x_{1}y_{1}&space;&plus;&space;x_{2}y_{2}&space;&plus;&space;...&space;&plus;&space;x_{n}y_{n}" title="\left \langle x, y \right \rangle = x_{1}y_{1} + x_{2}y_{2} + ... + x_{n}y_{n}" />

### Properties of the inner product
1. <img src="https://latex.codecogs.com/png.latex?\left&space;\langle&space;x,&space;y&space;\right&space;\rangle&space;\in&space;\mathbb{R}" title="\left \langle x, y \right \rangle \in \mathbb{R}" />
2. <img src="https://latex.codecogs.com/png.latex?\left&space;\langle&space;x,&space;y&space;\right&space;\rangle&space;=&space;\left&space;\langle&space;y,&space;x&space;\right&space;\rangle" title="\left \langle x, y \right \rangle = \left \langle y, x \right \rangle" />
3. <img src="https://latex.codecogs.com/png.latex?\left&space;\langle&space;ax&plus;by,z&space;\right&space;\rangle&space;=&space;a\left&space;\langle&space;x,z&space;\right&space;\rangle&space;&plus;&space;b\left&space;\langle&space;y,z&space;\right&space;\rangle" title="\left \langle ax+by,z \right \rangle = a\left \langle x,z \right \rangle + b\left \langle y,z \right \rangle" />
4. <img src="https://latex.codecogs.com/png.latex?\left&space;\langle&space;x,x&space;\right&space;\rangle&space;=&space;\left&space;\|&space;x&space;\right&space;\|^{2}&space;\geq&space;0" title="\left \langle x,x \right \rangle = \left \| x \right \|^{2} \geq 0" />

### Angle between vectors

<img src="https://latex.codecogs.com/png.latex?cos&space;\theta&space;=&space;\frac{\left&space;\langle&space;x,y&space;\right&space;\rangle}{\left&space;\|&space;x&space;\right&space;\|\left&space;\|&space;y&space;\right&space;\|}" title="cos \Theta = \frac{\left \langle x,y \right \rangle}{\left \| x \right \|\left \| y \right \|}" />

#### Dot product

<img src="https://latex.codecogs.com/png.latex?\left&space;\|&space;x&space;\right&space;\|\left&space;\|&space;y&space;\right&space;\|cos\theta&space;=&space;\left&space;\langle&space;x,y&space;\right&space;\rangle" title="\left \| x \right \|\left \| y \right \|cos\theta = \left \langle x,y \right \rangle" />

#### Application

Find the angle between the vectors
<img src="https://latex.codecogs.com/png.latex?x&space;=&space;\begin{bmatrix}&space;1\\&space;2\\&space;-1&space;\end{bmatrix}&space;,y&space;=&space;\begin{bmatrix}&space;2\\&space;1\\&space;1&space;\end{bmatrix}" title="x = \begin{bmatrix} 1\\ 2\\ -1 \end{bmatrix} ,y = \begin{bmatrix} 2\\ 1\\ 1 \end{bmatrix}" />

<img src="https://latex.codecogs.com/png.latex?\left&space;\|&space;x&space;\right&space;\|&space;=&space;\sqrt{6}" title="\left \| x \right \| = \sqrt{6}" />
<img src="https://latex.codecogs.com/png.latex?\left&space;\|&space;y&space;\right&space;\|&space;=&space;\sqrt{6}" title="\left \| y \right \| = \sqrt{6}" />
<img src="https://latex.codecogs.com/png.latex?\left&space;\langle&space;x,y&space;\right&space;\rangle&space;=&space;3" title="\left \langle x,y \right \rangle = 3" />


<img src="https://latex.codecogs.com/png.latex?cos\theta&space;=&space;\frac{\left&space;\langle&space;x,y&space;\right&space;\rangle}{\left&space;\|&space;x&space;\right&space;\|\left&space;\|&space;y&space;\right&space;\|}&space;=&space;\frac{1}{2}" title="cos\theta = \frac{\left \langle x,y \right \rangle}{\left \| x \right \|\left \| y \right \|} = \frac{1}{2}" />
<img src="https://latex.codecogs.com/png.latex?=>&space;\theta&space;=&space;cos^-1\left&space;(\frac{1}{2}\right&space;)" title="=> \theta = cos^-1\left (\frac{1}{2}\right )" />
<img src="https://latex.codecogs.com/png.latex?=>&space;\theta&space;=&space;\frac{\pi}{3}" title="=> \theta = \frac{\pi}{3}" />

### Finding vector perpendicular to unit vector

To find the constant <img src="https://latex.codecogs.com/png.latex?\alpha&space;\in&space;\mathbb{R}" title="\alpha \in \mathbb{R}" /> and the vector <img src="https://latex.codecogs.com/png.latex?x^\perp" title="x^\perp" /> which is perpendicular to the unit vector u such that <img src="https://latex.codecogs.com/png.latex?x&space;=&space;au&space;&plus;&space;x^\perp" title="x = au + x^\perp" />

=> <img src="https://latex.codecogs.com/png.latex?\left&space;\langle&space;x,&space;u&space;\right&space;\rangle&space;=&space;a\left&space;\langle&space;u,&space;u&space;\right&space;\rangle&space;&plus;&space;\left&space;\langle&space;x^\perp&space;,u\right&space;\rangle" title="\left \langle x, u \right \rangle = a\left \langle u, u \right \rangle + \left \langle x^\perp ,u\right \rangle" />

=> <img src="https://latex.codecogs.com/png.latex?a&space;=&space;\left&space;\langle&space;x,u&space;\right&space;\rangle" title="a = \left \langle x,u \right \rangle" />

To find <img src="https://latex.codecogs.com/png.latex?x^\perp" title="x^\perp" />, 

<img src="https://latex.codecogs.com/png.latex?x&space;=&space;au&space;&plus;&space;x^\perp" title="x = au + x^\perp" />
<img src="https://latex.codecogs.com/png.latex?x^\perp&space;=&space;x&space;-&space;au" title="x^\perp = x - au" />

## Class test stuff

### 2016 Question 1
Parametrize the line in <img src="https://latex.codecogs.com/png.latex?\mathbb{R}^2" title="\mathbb{R}^2" /> given by the equation <img src="https://latex.codecogs.com/png.latex?2x&space;-&space;8y&space;=&space;4" title="2x - 8y = 4" />

Solution:

<img src="https://latex.codecogs.com/png.latex?2x&space;-&space;8y&space;=&space;4" title="2x - 8y = 4" />
<=>
<img src="https://latex.codecogs.com/png.latex?&space;2x&space;=&space;8y&space;&plus;&space;4" title="2x = 8y + 4" />
<=>
<img src="https://latex.codecogs.com/png.latex?\\x&space;=&space;4y&space;&plus;&space;4\\&space;y&space;=&space;0&space;&plus;&space;1y" title="\\x = 4y + 4\\ y = 0 + 1y" />
<=>
<img src="https://latex.codecogs.com/png.latex?\begin{bmatrix}&space;x\\&space;y&space;\end{bmatrix}&space;=&space;\begin{bmatrix}&space;4\\&space;0&space;\end{bmatrix}&space;&plus;&space;y\begin{bmatrix}&space;4\\&space;1&space;\end{bmatrix}" title="\begin{bmatrix} x\\ y \end{bmatrix} = \begin{bmatrix} 4\\ 0 \end{bmatrix} + y\begin{bmatrix} 4\\ 1 \end{bmatrix}" />

That is, the line <img src="https://latex.codecogs.com/png.latex?2x&space;-&space;8y&space;=&space;4" title="2x - 8y = 4" /> is parametrized by the map

<img src="https://latex.codecogs.com/png.latex?\gamma&space;:\mathbb{R}&space;\rightarrow&space;\mathbb{R}^2:y&space;\mapsto&space;\gamma(y)&space;=&space;\begin{bmatrix}&space;4\\&space;0&space;\end{bmatrix}&space;&plus;&space;y&space;\begin{bmatrix}&space;4\\&space;1&space;\end{bmatrix}" title="\gamma :\mathbb{R} \rightarrow \mathbb{R}^2:y \mapsto \gamma(y) = \begin{bmatrix} 4\\ 0 \end{bmatrix} + y \begin{bmatrix} 4\\ 1 \end{bmatrix}" />


Parametrize the line in <img src="https://latex.codecogs.com/png.latex?\mathbb{R}^3" title="\mathbb{R}^3" /> that passes through the points

<img src="https://latex.codecogs.com/png.latex?p&space;=&space;\begin{bmatrix}&space;1\\&space;0\\&space;-2&space;\end{bmatrix},&space;q&space;=&space;\begin{bmatrix}&space;3\\&space;-1\\&space;5&space;\end{bmatrix}" title="p = \begin{bmatrix} 1\\ 0\\ -2 \end{bmatrix}, q = \begin{bmatrix} 3\\ -1\\ 5 \end{bmatrix}" />

<img src="https://latex.codecogs.com/png.latex?\\\gamma:\mathbb{R}\rightarrow\mathbb{R}^3:t\mapsto\gamma(t)&space;=&space;p&space;&plus;&space;t(q-p)\\\\=\begin{bmatrix}&space;1\\&space;0\\&space;-2&space;\end{bmatrix}&space;&plus;&space;t\begin{bmatrix}&space;3-1\\&space;-1-0\\&space;5&plus;2&space;\end{bmatrix}\\\\\\&space;=\begin{bmatrix}&space;1\\&space;0\\&space;-2&space;\end{bmatrix}&plus;t\begin{bmatrix}&space;2\\&space;-1\\&space;7&space;\end{bmatrix}" title="\\\gamma:\mathbb{R}\rightarrow\mathbb{R}^3:t\mapsto\gamma(t) = p + t(q-p)\\\\=\begin{bmatrix} 1\\ 0\\ -2 \end{bmatrix} + t\begin{bmatrix} 3-1\\ -1-0\\ 5+2 \end{bmatrix}\\\\\\ =\begin{bmatrix} 1\\ 0\\ -2 \end{bmatrix}+t\begin{bmatrix} 2\\ -1\\ 7 \end{bmatrix}" />


### 2016 Question 2

**(a)**
Parametrize the plane in <img src="https://latex.codecogs.com/png.latex?\mathbb{R}^3" title="\mathbb{R}^3" /> given by the equation: <img src="https://latex.codecogs.com/png.latex?x&plus;2y-3z=4" title="x+2y-3z=4" />

Solution:

<img src="https://latex.codecogs.com/png.latex?x&plus;2y-3z=4" title="x+2y-3z=4" />

<=>

<img src="https://latex.codecogs.com/png.latex?\\x=-2y&plus;3z&plus;4&space;\\y&space;=&space;1y&space;&plus;&space;0z&space;&plus;&space;0&space;\\z&space;=&space;0y&space;&plus;&space;1z&space;&plus;&space;0&space;\\&space;\\\Rightarrow&space;\begin{bmatrix}&space;x\\&space;y\\&space;z&space;\end{bmatrix}&space;=&space;\begin{bmatrix}&space;4\\&space;0\\&space;0&space;\end{bmatrix}&space;&plus;&space;y\begin{bmatrix}&space;-2\\&space;1\\&space;0&space;\end{bmatrix}&space;&plus;&space;z\begin{bmatrix}&space;3\\&space;0\\&space;1&space;\end{bmatrix}" title="\\x=-2y+3z+4 \\y = 1y + 0z + 0 \\z = 0y + 1z + 0 \\ \\\Rightarrow \begin{bmatrix} x\\ y\\ z \end{bmatrix} = \begin{bmatrix} 4\\ 0\\ 0 \end{bmatrix} + y\begin{bmatrix} -2\\ 1\\ 0 \end{bmatrix} + z\begin{bmatrix} 3\\ 0\\ 1 \end{bmatrix}" />

**(b)**

<img src="https://latex.codecogs.com/png.latex?l:\mathbb{R}\rightarrow\mathbb{R}^3:t\mapsto&space;l(t)&space;=&space;\begin{bmatrix}&space;x(t)\\&space;y(t)\\&space;z(t)&space;\end{bmatrix}&space;=&space;\begin{bmatrix}&space;1\\&space;1\\&space;-2&space;\end{bmatrix}&space;&plus;&space;t\begin{bmatrix}&space;1\\&space;2\\&space;-3&space;\end{bmatrix}" title="l:\mathbb{R}\rightarrow\mathbb{R}^3:t\mapsto l(t) = \begin{bmatrix} x(t)\\ y(t)\\ z(t) \end{bmatrix} = \begin{bmatrix} 1\\ 1\\ -2 \end{bmatrix} + t\begin{bmatrix} 1\\ 2\\ -3 \end{bmatrix}" />

parametrizes a line in <img src="https://latex.codecogs.com/png.latex?\mathbb{R}^3" title="\mathbb{R}^3" />. Explain why this line intersects **orthogonally** the plane given in part (a) and find the point of intersection.

Solution:

The direction of the line <img src="https://latex.codecogs.com/png.latex?\begin{bmatrix}&space;1\\&space;2\\&space;-3&space;\end{bmatrix}" title="\begin{bmatrix} 1\\ 2\\ -3 \end{bmatrix}" /> is the direction of the normal to the plane.

**Note**: To get the normal of a plane construct a vector using the coefficients of the line's equation. for <img src="https://latex.codecogs.com/png.latex?\\x&plus;2y-3z=4,&space;normal&space;=&space;\begin{bmatrix}&space;1\\&space;2\\&space;-3&space;\end{bmatrix}" title="\\x+2y-3z=4, normal = \begin{bmatrix} 1\\ 2\\ -3 \end{bmatrix}" />

To get the point of intersection we sub in x(t), y(t), z(t) for x, y, z in the line's equation. Therefore;

<img src="https://latex.codecogs.com/png.latex?\\line&space;\&space;intersects&space;\&space;plane&space;\iff&space;(1&plus;t)&space;&plus;&space;2(1&plus;2t)-3(-2-3t)&space;=&space;4&space;\\\iff&space;t&space;=&space;-\frac{5}{14}&space;\\&space;so&space;\&space;the&space;\&space;point&space;\&space;of&space;\&space;intersection&space;=&space;l(-\frac{5}{14})&space;=&space;\begin{bmatrix}&space;1\\&space;1\\&space;-2&space;\end{bmatrix}&space;-&space;\frac{5}{14}\begin{bmatrix}&space;1\\&space;2\\&space;-3&space;\end{bmatrix}" title="\\line \ intersects \ plane \iff (1+t) + 2(1+2t)-3(-2-3t) = 4 \\\iff t = -\frac{5}{14} \\ so \ the \ point \ of \ intersection = l(-\frac{5}{14}) = \begin{bmatrix} 1\\ 1\\ -2 \end{bmatrix} - \frac{5}{14}\begin{bmatrix} 1\\ 2\\ -3 \end{bmatrix}" />


### 2016 Question 

<img src="https://latex.codecogs.com/png.latex?u_1&space;=&space;\frac{1}{\sqrt{2}}\begin{bmatrix}&space;0\\&space;1\\&space;1&space;\end{bmatrix},&space;\&space;u_2&space;=&space;\frac{1}{3}\begin{bmatrix}&space;1\\&space;-2\\&space;2&space;\end{bmatrix},&space;\&space;and&space;\&space;v&space;=&space;\begin{bmatrix}&space;3\\&space;2\\&space;1&space;\end{bmatrix}" title="u_1 = \frac{1}{\sqrt{2}}\begin{bmatrix} 0\\ 1\\ 1 \end{bmatrix}, \ u_2 = \frac{1}{3}\begin{bmatrix} 1\\ -2\\ 2 \end{bmatrix}, \ and \ v = \begin{bmatrix} 3\\ 2\\ 1 \end{bmatrix}" />

**(a)** Show that the set of vectors <img src="https://latex.codecogs.com/png.latex?\{u_1,&space;u_2\}" title="\{u_1, u_2\}" /> is an orthonormal set.

A set of vectors is orthonormal if they are orthogonal and unit vectors.

<img src="https://latex.codecogs.com/png.latex?\\\left&space;\langle&space;u_1,&space;u_2&space;\right&space;\rangle&space;=&space;0&space;\\\left&space;\|&space;u_1&space;\right&space;\|^2&space;=&space;1&space;\\\left&space;\|&space;u_2&space;\right&space;\|&space;=&space;1" title="\\\left \langle u_1, u_2 \right \rangle = 0 \\\left \| u_1 \right \|^2 = 1 \\\left \| u_2 \right \| = 1" />

**(b)**
If <img src="https://latex.codecogs.com/png.latex?P" title="P" /> is the plane in <img src="https://latex.codecogs.com/png.latex?\mathbb{R}^3" title="\mathbb{R}^3" /> which passes through the origin and contains the set of vectors <img src="https://latex.codecogs.com/png.latex?\{u_1,&space;u_2\}" title="\{u_1, u_2\}" />, find the point on <img src="https://latex.codecogs.com/png.latex?P" title="P" /> that is nearest to <img src="https://latex.codecogs.com/png.latex?v" title="v" />

The point on the plane nearest to v is v' given by

<img src="https://latex.codecogs.com/png.latex?v'&space;=&space;\left&space;\langle&space;v,&space;u_1&space;\right&space;\rangle&space;u_1&space;&plus;&space;\left&space;\langle&space;v,&space;u_2&space;\right&space;\rangle&space;u_2" title="v' = \left \langle v, u_1 \right \rangle u_1 + \left \langle v, u_2 \right \rangle u_2" />

### 2017 Question 1

**(a)** Write down the equation of the plane in <img src="https://latex.codecogs.com/png.latex?\mathbb{R}^3" title="\mathbb{R}^3" /> that passes through the point p and is normal to the vector n, where:

<img src="https://latex.codecogs.com/png.latex?p&space;=&space;\begin{bmatrix}&space;1\\&space;3\\&space;-2&space;\end{bmatrix}&space;\&space;and&space;\&space;n&space;=&space;\begin{bmatrix}&space;2\\&space;-1\\&space;5\\&space;\end{bmatrix}" title="p = \begin{bmatrix} 1\\ 3\\ -2 \end{bmatrix} \ and \ n = \begin{bmatrix} 2\\ -1\\ 5\\ \end{bmatrix}" />

The equation for a plane is in the form <img src="https://latex.codecogs.com/png.latex?ax&space;&plus;&space;by&space;&plus;&space;cz&space;&plus;&space;d&space;=&space;0" title="ax + by + cz + d = 0" />

The formula to solve this question is:

<img src="https://latex.codecogs.com/png.latex?a(x-x_0)&space;&plus;&space;b(y-y_0)&space;&plus;&space;c(z-z_0)&space;=&space;0" title="a(x-x_0) + b(y-y_0) + c(z-z_0) = 0" />

x0, y0, z0 correspond to the x,y,z of the point p
a, b, c correspond to the x,y,z of the normal n

Inputting the values into the formula we get

<img src="https://latex.codecogs.com/png.latex?\\2(x-1)&space;-1(y-3)&space;&plus;&space;5(z&plus;2)&space;=&space;0&space;\\\iff&space;2x-2-y-3&plus;5z&plus;10=0&space;\\\iff&space;2x-y&plus;5z&plus;5=0" title="\\2(x-1) -1(y-3) + 5(z+2) = 0 \\\iff 2x-2-y-3+5z+10=0 \\\iff 2x-y+5z+5=0" />


### Matrix multiplication

#### Matrix * vector

<img src="https://latex.codecogs.com/png.latex?\\\begin{bmatrix}&space;x_1&space;&&space;y_1&space;&&space;z_1\\&space;x_2&space;&&space;y_2&space;&&space;z_2\\&space;x_3&space;&&space;y_3&space;&&space;z_3&space;\end{bmatrix}\begin{bmatrix}&space;i\\&space;j\\&space;k&space;\end{bmatrix}&space;\iff&space;\begin{bmatrix}&space;ix_1&space;&plus;&space;iy_1&space;&plus;&space;iz_1\\&space;jx_2&space;&plus;&space;jy_2&space;&plus;&space;jz_2\\&space;kx_3&space;&plus;&space;ky_3&space;&plus;&space;kz_3&space;\end{bmatrix}&space;\\\\&space;\\&space;the\&space;same\&space;as\&space;flipping\&space;the\&space;vector\&space;on\&space;it's\&space;side\&space;\\&space;and\&space;multiplying\&space;it's\&space;columns\&space;by\&space;the\&space;columns\&space;in\&space;\\&space;the\&space;matrix\\&space;\\\begin{bmatrix}&space;\&space;i&space;&&space;\&space;j&space;&&space;\&space;k&space;\&space;\&space;\end{bmatrix}\\&space;\\&space;\begin{bmatrix}&space;x_1&space;&&space;y_1&space;&&space;z_1\\&space;x_2&space;&&space;y_2&space;&&space;z_2\\&space;x_3&space;&&space;y_3&space;&&space;z_3&space;\end{bmatrix}" title="\\\begin{bmatrix} x_1 & y_1 & z_1\\ x_2 & y_2 & z_2\\ x_3 & y_3 & z_3 \end{bmatrix}\begin{bmatrix} i\\ j\\ k \end{bmatrix} \iff \begin{bmatrix} ix_1 + iy_1 + iz_1\\ jx_2 + jy_2 + jz_2\\ kx_3 + ky_3 + kz_3 \end{bmatrix} \\\\ \\ the\ same\ as\ flipping\ the\ vector\ on\ it's\ side\ \\ and\ multiplying\ it's\ columns\ by\ the\ columns\ in\ \\ the\ matrix\\ \\\begin{bmatrix} \ i & \ j & \ k \ \ \end{bmatrix}\\ \\ \begin{bmatrix} x_1 & y_1 & z_1\\ x_2 & y_2 & z_2\\ x_3 & y_3 & z_3 \end{bmatrix}" />

### Gaussian elimination

#### Row echelon form

<img src="https://latex.codecogs.com/png.latex?\left&space;[\begin{matrix}&space;1&&space;5&space;&&space;3&space;&&space;2\\&space;0&&space;1&space;&&space;7&space;&&space;4\\&space;0&&space;0&space;&&space;0&space;&&space;1&space;\end{matrix}\mid&space;\begin{matrix}&space;2\\&space;5\\&space;7\\&space;\end{matrix}&space;\right&space;]" title="\left [\begin{matrix} 1& 5 & 3 & 2\\ 0& 1 & 7 & 4\\ 0& 0 & 0 & 1 \end{matrix}\mid \begin{matrix} 2\\ 5\\ 7\\ \end{matrix} \right ]" />


## Things needed for final exam
### Q1
- [x] Vector addition + Scaling
- [x] Calculating vector length
- [x] Calculating angle between vectors
- [x] Finding *a* and *v^perp* satisfying *v = au + v^perp*
### Q2
- [x] Explain orthonormal set
- [x] Explain subspace
- [x] Explain why *w = v - <v,u1>u1 - <v,u2>u2* is non-zero and perpendicular to u1 and u2
- [x] Use formula above to determine perpendicular vector
- [x] Calculate orthogonal projection of a vector onto the subspace spanned by 2 other vectors
### Q3
- [x] Parametrize plane given by equation
- [x] Parametrize line given by equation
- [x] Parametrize line passing through point p in the direction of v
- [x] Find distance from a point to a plane
- [x] Finding normal vector from equation
- [ ] Finding vectors parallel to a plane that do not lie on the same line through the origin
- [ ] Find point at which a line intersects a plane
### Q4
- [x] Matrix-vector multiplication
- [x] Matrix-matrix multiplication
- [x] Matrix transpose
- [x] Explain eigenvector, eigenvalue
- [ ] Show that *(CD)^-1 = D^-1C^-1*
### Q5
- [x] Writing augmented matrix for a system of equations
- [x] Parametrize augmented matrix
- [x] Determine basis for the kernel
- [x] Determine basis for the image
- [x] Determine matrix E such that [EA|Eb] is the rref of [A|b]
### Q6
- [x] Check if vectors are linearly independent
- [x] Is vector in kernel?
- [x] Is vector in image?
- [x] What's the dimension of the kernel?
### Q7 
- [x] Rotation matrices about an axis {e1, e2, e3} in R^3
- [x] Calculate the composition of rotation matrices
- [ ] Find the axis of rotation for the composition
### Q8
- [x] Calculate the characteristic polynomial of a matrix
- [ ] Find all eigenvalues
- [x] Parametrize the eigenspace of a matrix corresponding to some eigenvalue
### Q9
- [x] Finding diagonal matrix
- [ ] Matrix traces
- [x] Find a basis for R^n consisting of eigenvectors of a matrix
### Q10
- [x] Elementary matrix for row operation
- [x] GJ elimination to find inverse of a matrix

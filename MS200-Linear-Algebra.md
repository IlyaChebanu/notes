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
### Parametrizing lines

**2016 Question 1**
Parametrize the line in <img src="https://latex.codecogs.com/png.latex?\mathbb{R}^2" title="\mathbb{R}^2" /> given by the equation <img src="https://latex.codecogs.com/png.latex?2x&space;-&space;8y&space;=&space;4" title="2x - 8y = 4" />

Solution:

<img src="https://latex.codecogs.com/png.latex?2x&space;-&space;8y&space;=&space;4" title="2x - 8y = 4" />
<=>
<img src="https://latex.codecogs.com/png.latex?&space;2x&space;=&space;8y&space;&plus;&space;4" title="2x = 8y + 4" />
<=>
<img src="https://latex.codecogs.com/png.latex?\\x&space;=&space;4y&space;&plus;&space;4\\&space;y&space;=&space;0&space;&plus;&space;1y" title="\\x = 4y + 4\\ y = 0 + 1y" />
<=>
<img src="https://latex.codecogs.com/png.latex?\begin{bmatrix}&space;x\\&space;y&space;\end{bmatrix}&space;=&space;\begin{bmatrix}&space;4\\&space;0&space;\end{bmatrix}&space;&plus;&space;y\begin{bmatrix}&space;3\\&space;1&space;\end{bmatrix}" title="\begin{bmatrix} x\\ y \end{bmatrix} = \begin{bmatrix} 4\\ 0 \end{bmatrix} + y\begin{bmatrix} 3\\ 1 \end{bmatrix}" />

That is, the line <img src="https://latex.codecogs.com/png.latex?2x&space;-&space;8y&space;=&space;4" title="2x - 8y = 4" /> is parametrized by the map

<img src="https://latex.codecogs.com/png.latex?\gamma&space;:\mathbb{R}&space;\rightarrow&space;\mathbb{R}^2:y&space;\mapsto&space;\gamma(y)&space;=&space;\begin{bmatrix}&space;4\\&space;0&space;\end{bmatrix}&space;&plus;&space;y&space;\begin{bmatrix}&space;3\\&space;1&space;\end{bmatrix}" title="\gamma :\mathbb{R} \rightarrow \mathbb{R}^2:y \mapsto \gamma(y) = \begin{bmatrix} 4\\ 0 \end{bmatrix} + y \begin{bmatrix} 3\\ 1 \end{bmatrix}" />

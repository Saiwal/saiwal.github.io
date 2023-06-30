---
title: "Having fun with Deformation Gradients"
categories: ["mechanics"]
math: "true"
---

In this article I plotted various deformation gradient on a 2-D grid to show how the displacement field would look like. Visualizing a deformation gradient greatly helps in understanding how a body deforms and how we calculate the various deformation measures.
share_post: facebook, google-plus, email, twitter

## What is the Deformation Gradient?
Deformation Gradient is a measure of how different fibres of a body stretch when subjected to a deformation. We can try to understand it physically by taking an example of a 2D surface where each point is at its original location denoted by its coordinate $ (x,y) $ and which is mapped to a final position $ (X,Y) $ according to a deformation gradient **[F]**. Here, **[F]** is defined as follows: \\[ F_{ij} = \frac{\partial{x_i}}{\partial{X_j}} \\]

Let's see with an example:

Suppose there is deformation described as follows:
\\[ x = aX + bY \\]
and
\\[ y = cX + dY \\]

then the deformation gradient is given by:
\\[ \textbf{[F]} = \begin{bmatrix}a & b\\\c & d\end{bmatrix} \\]

and the deformation field is given as:

\\[ u = x - X = (a-1)X + bY \\]
\\[ v = y - Y = cX - (d-1)Y \\]

The matrix **F** gives the stretch of a fibre from the initial state to the deformed state. So, a fibre lying along x axis gets stretched by 'a' amount in the same direction but by 'b' in the perpendicular direction.

##Plots of some typical deformation gradients.

### Case I

\\[ x = 1 + X \\]
and
\\[ y = Y \\]
the displacements are:
\\[ u = 1 \\]
\\[ v = 0 \\]
then the deformation gradient is given by:
\\[ \textbf{[F]} = \begin{bmatrix}1 & 0\\\0 & 1\end{bmatrix} \\]

The following code is used to plot the resulting displacement field
```python
    from pylab import *
    from numpy import ma

    X,Y = meshgrid( arange(0,10,0.5),arange(0,6,0.5) )
    U = 1 + 0*X
    V = 0

    figure()
    Q = quiver( U, V)
    xlabel('x')
    ylabel('y')
    title('Displacement Field')
```
which looks like

![uniform](/assets/img/posts/def-grad1.png)

Note that there is no stretching but merely a uniform displacement of 1 unit along the x-axis.


### Case II

\\[ x = 1.2X \\]
and
\\[ y = Y \\]
the displacements are:
\\[ u = 0.2X \\]
\\[ v = 0 \\]
then the deformation gradient is given by:
\\[ \textbf{[F]} = \begin{bmatrix}1.2 & 0\\\0 & 1\end{bmatrix} \\]

The following code is used to plot the resulting displacement field
```python
    from pylab import *
    from numpy import ma

    X,Y = meshgrid( arange(0,10,0.5),arange(0,6,0.5) )
    U = 0.2*X
    V = 0

    figure()
    Q = quiver( U, V)
    xlabel('x')
    ylabel('y')
    title('Displacement Field')
```
which looks like

![linear](/assets/img/posts/def-grad2.png)

Note that now there is a linear variation in the stretching along the x-axis.

### Case III

\\[ x = X + Y \\]
and
\\[ y = Y \\]
the displacements are:
\\[ u = Y \\]
\\[ v = 0 \\]
then the deformation gradient is given by:
\\[ \textbf{[F]} = \begin{bmatrix}1 & 1\\\0 & 1\end{bmatrix} \\]

The following code is used to plot the resulting displacement field
```python
    from pylab import *
    from numpy import ma

    X,Y = meshgrid( arange(0,10,0.5),arange(0,6,0.5) )
    U = Y
    V = 0

    figure()
    Q = quiver( U, V)
    xlabel('x')
    ylabel('y')
    title('Displacement Field')
```
which looks like

![shear](/assets/img/posts/def-grad3.png)

This is a case of simple shear where the solid is sheared along the x-axis. Note the **F** in this case and the significance of its values.

### Case IV

\\[ x = X + Y \\]
and
\\[ y = 1.2X + 0.3Y \\]
the displacements are:
\\[ u = Y \\]

\\[ v = 1.2X - 0.7Y \\]
then the deformation gradient is given by:
\\[ \textbf{[F]} = \begin{bmatrix}1 & 1\\\1.2 & 0.3\end{bmatrix} \\]

The following code is used to plot the resulting displacement field
```python
    from pylab import *
    from numpy import ma

    X,Y = meshgrid( arange(0,10,0.5),arange(0,6,0.5) )
    U = Y
    V = 1.2*X - 0.7*Y

    figure()
    Q = quiver( U, V)
    xlabel('x')
    ylabel('y')
    title('Displacement Field')
```
which looks like

![mix](/assets/img/posts/def-grad4.png)


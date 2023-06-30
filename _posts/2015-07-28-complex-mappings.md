---
title: "Complex function as mappings"
categories: ["mechanics"]
math: true
---

I have plotted various complex functions as a mapping showing how the complex plane is transformed when subjected to a complex function.


## Introduction
Complex Analysis is a topic which is not very easy to grasp. While the mathematics behind it is straight forward with simple rules, it is often difficult to visualize how the various operations take place.

## A Complex function
A complex function is usually written as $ w = f(z) $, here w is referred to as the image of z and f is the transformation function which maps the complex plane z to w. The image of z (w) is plotted on another plane which is obtained after the transformation f. A sample is shown below where the z-plane is translated by adding another complex number to it.
 \\[ w = z + (2 + 3j) \\]

![mapping1]({attach}mapping1.jpg)

It is clearly visible that the indicated region has translated by 2 units along the real axis and 3 units along the imaginary axis.

## Some more Examples
I have plotted some more examples of complex functions using python. The code is also provided if you feel like experimenting.

### Example I (Simple multiplication by a complex number)

When $ w = z*(a + jb) $ the effect is that of stretching and subsequent rotation of the plane. The stretch amount is equal to the magnitude $ \sqrt{(a^2 + b^2)} $  and the rotation is by the amount $ tan^{-1} (b/a) $. Lets consider multiplication by 2 + 3j. In this case the points should stretch $ sqrt(13) $ times and rotate by 56.3 degrees.

```python
    # -*- coding: utf-8 -*-
    """
    Created on Tue Jul 28 09:00:40 2015

    @author: saiwal
    """

    from numpy import *
    import matplotlib.pyplot as plt

    u = linspace(01, 3, 80)
    v = linspace(01, 3, 80)
    uu, vv = meshgrid(u, v)
    z0 = uu + 1j * vv
    m = 2+3j
    z = z0*m
    T = np.arctan2(uu,vv)

    plt.figure(figsize=(14,6))
    plt.subplot(1,2,1)
    plt.scatter(uu, vv, c=T, s=10, lw = 0)
    plt.title('real points')
    plt.xlabel('Re(z)')
    plt.ylabel('Im(z)')
    plt.grid(True)

    plt.subplot(1,2,2)
    plt.scatter(real(z), imag(z),c=T, s=10, lw = 0)
    plt.title('mapped points')
    plt.xlabel('Re(z)')
    plt.ylabel('Im(z)')
    plt.grid(True)
    plt.gray
```

The plot is shown below, note that the rotation and stretching do not depend on the sequence in which it is done.

![mapping2]({attach}mapping2.jpg)

### Example II (Inverse of z)

Now we try to see how $ 1/z $ looks when plotted. This mapping has a singularity at the origin so we should be careful while choosing the domain to plot.

```python
    # -*- coding: utf-8 -*-
    """
    Created on Tue Jul 28 09:00:40 2015

    @author: saiwal
    """

    from numpy import *
    import matplotlib.pyplot as plt

    u = linspace(01, 3, 80)
    v = linspace(01, 3, 80)
    uu, vv = meshgrid(u, v)
    z0 = uu + 1j * vv
    z = 1/z0
    T = np.arctan2(uu,vv)

    plt.figure(figsize=(14,6))
    plt.subplot(1,2,1)
    plt.scatter(uu, vv, c=T, s=10, lw = 0)
    plt.title('real points')
    plt.xlabel('Re(z)')
    plt.ylabel('Im(z)')
    plt.grid(True)

    plt.subplot(1,2,2)
    plt.scatter(real(z), imag(z),c=T, s=10, lw = 0)
    plt.title('mapped points')
    plt.xlabel('Re(z)')
    plt.ylabel('Im(z)')
    plt.grid(True)
    plt.gray
```

The plot is shown below, note the inversion that happens. Also the mapping may be verified manually by computing the maps of the four corner points.

![mapping3](/assets/img/posts/mapping3.png)

Another plot showing the whole plane,

![mapping7](/assets/img/posts/mapping7.jpg)

### Example III (Simple rotation without stretching)

For a simple rotation the multiplying complex number should have a modulus equal to 1. The argument would be the angle of rotation.

lets see the effect of multiplying by different comlplex numbers.

#### Multiplying by j
This results in rotation by $ \pi/2 $

![mapping4](/assets/img/posts/mapping4.jpg)

#### Multiplying by 0.6 + 0.8j
Again the modulus is 1,
Argument = 64.6 deg

![mapping5](/assets/img/posts/mapping5.jpg)

#### Multiplying by 0.98 + 0.2j
Modulus = 1
Argument = 11.53 deg

![mapping6](/assets/img/posts/mapping6.jpg)

### Example III (rasing z to a power)
$ z^n $ can be interpreted as raising the modulus to power n and multiplying the argument $ \theta $ by $ n $.

**Plot of $ z^2 $**

I plotted the domain from Re(0,3) and Im(0,3) to $ z^2 $ and the result is shown. It is clearly visible that the argument is multiplied by 2 and the modulus is squared.

![mapping8](/assets/img/posts/mapping8.jpg)

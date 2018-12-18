---
layout: page
title: 1-D Numerical Integrals
---

# One-Dimensional Numerical Integration

Up to now, your primary experience has probably been integrals of functions with known anti-deriatives -- that is, analytical integrals. However, the concept of integration as accumulation suggests that we not need a known anti-derivative to compute an integral. We have to develop a strategy to calculate the accumulation. Think of the idea of calculating the area under a curve. We don't need to know the function the describes the area under the curve to measure it. In fact, many well-known functions do not have such an anti-derivative.

For our purposes, we will restrict ourselves at the moment to one-dimensional integrals of a known function $f(x)$, which may or may not have an analytical anti-derivative. In that case, we will say that the integral of $f(x)$ from $a$ to $b$ is given by some value, which depends on $a$ and $b$,

$$I(a,b) = \int_a^b f(x) dx$$

[[FIGURE OF CURVE AND AREA UNDER IT]]

If we are unable to compute this value because the function $f(x)$ does not have a known anti-derivative, we can still estimate the value of $I(a,b)$. In fact, this value can be estimated for a function with a known anti-derivative as well, which is a useful check of the quality of our methods of estimation prior to applying them to functions with unknown anti-derivatives.

## Riemann Sum

Perhaps the simplest approach, and one you have already thought of, is to use equally-spaced small rectangles to estimate the area under the curve and, thus, obtain a value for $I(a,b)$. Here, we cut the interval from $a$ to $b$ into $n$ equal-width rectangles with a width of:

$$w = \dfrac{b-a}{n}$$

Each rectangle has a height that is an estimate of the height of the function $f(x)$ at the location of the rectangle. This is typically done in one of three ways:

1. The Left Riemann Sum - the height of the function coincides with the left corner of the rectangle.
2. The Right Riemann Sum -  the height of the function coincides with the right corner of the rectangle.
3. The Midpoint Rule - the height of the function coincides with the middle of the rectangle.

We will focus on the Midpoint Rule so that the area of the i-th (where $i$ runs from 0 to $n-1$) rectangle is:

$$A_i = w\left[f\left(a+\left(i+\dfrac{1}{2}\right)w\right)\right]$$

To estimate $I(a,b)$, we add up the contribution by each rectangle -- summing the areas,

$$I(a,b) \approx \sum_{i=0}^{n-1} A_i = w\sum_{i=0}^{n-1}\left[f\left(a+\left(i+\dfrac{1}{2}\right)w\right)\right]$$

### Numerically computing the Riemann sum

This last form the Riemann sum is a form that is ready for numerical calculations. The pseudocode can be extracted from the process described above:

```
Set the total computed area to zero
Set the values of a,b
Set the number of bins, n
Compute the width of the rectangles, w

For each rectangle from 0 to n-1

  Compute the area of the rectangle
  Add that rectangle area to the total computed area

Return the total computed area

```

### An Example

Let's use the Riemann sum to compute the integral of function with a known anti-derivative, $f(x) = x^2$ from $a=0$ to $b=1$.

$$ \int_0^1 x^2 dx = \dfrac{1}{3}{x^3}\bigg\vert_0^1 = 0.333...$$

From the pseudocode above, we can craft the following Python code,

```python

def f(x):

  return x**2;

def rectangle(i,w,a):

  return w*f(a+(i+1/2)*w);

def riemann(a,b,n):

  w = (b-a)/n;
  I = 0;

  for i in range(0,n):

    I += rectangle(i,w,a);

  return I;


a,b = 0,1
n = 10

print(riemann(a,b,n))
```







## Trapezoidal Rule

## Simpson's Rule

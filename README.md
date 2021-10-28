# The Chaos kata

*Goal: introduction to matplotlib and numpy with a classic example*

# Introduction

We are going to study the suite produced by the iteration of the
function `f`, defined on the real numbers and parameterized by k:

```
f(x) = k * x (1-x)
```

Where

* k is a number between 0 and 4
* x is a float between 0 and 1

The suites we'll study will start at `0.5` and then apply `f`, like this:

```
index term
  0    0.5
  1    f(0.5)
  2    f(f(0.5)
  3    f(f(f(0.y)
```

More specifically, we'll study what happens to the suites when the `k`
value changes.


# Instructions

## Set up

Create a virtual environment containing the `matplotlib` and `numpy` packages

## Step 1 - exploring singular `k` values

Specification: write a command line program that, given the `k` value as argument,
plots the 1000 first values of the suite. Use 0.5 for the initial value.

Here are a few hints to help you get started:

## Generating the suite

```python
import numpy

def suite(initial, k, iterations):
    """
    :param initial: the initial value (x0)
    :param k: the `k` parameter
    :param iterations: how many iterations to compute
    :return: a numpy array contains exactly `iterations` values
    """
    x = initial
    res = []
    for i in range(0, iterations):
        res.append(x)
        x = x * k * (1 - x)
    return numpy.array(res)
```

### Parsing command line options

```python
import sys
def main_single():
    k = float(sys.argv[1])
    # If run with `python main.py 3.2`, now `k` equals 3.2
```

### Generating a numpy array going from `start` to  `end` in `iterations` steps:

```python
ts = numpy.linspace(start, end, iterations)
```

### Plotting graphs

```python
from matplotlib import pyplot

xs = ...
ys = ...
# Plot the graph using the xs array as X axis,
# and the ys array as Y axis
pyplot.plot(xs, ys)
# Show the graph: must be called once, at the end
# of the script
pyplot.show()
```

## Instructions

Run the main script with the following values for `k`: 2, 2, 2.8, 3,
3.5, 3.8, 3.86, 4

# Step 2 - sensibility to initial conditions

In the step above, you may have found that the value 3.86 had a "strange" behavior.

In the same graph, draw to lines. One for the series starting at `0.5` with `k=3.86` and
an other one starting at `0.44449` with k still set to `k=3.86`.

# Step 3 - bifurcation diagram

The idea is to show *in a single* graph the behavior of the series where `k` changes.

This time you will need a *scatter* plot, where `k` is on the `X` axis, and the `Y` axis
contains *all the different values of the series*, starting at 1000 iterations.

For instance, if after 1000 iterations when k = 3.53 the possible values are 0.36, 0.47, 0.80 and 0.88, then
the scatter plot should contain:

| x    | y    |
|------|------|
| 3.53 | 0.36 |
| 3.53 | 0.47 |
| 3.53 | 0.80 |
| 3.53 | 0.88 |


# Going further

The suite is actually called "The Logistic Map". See the corresponding Wikipedia page for more info.

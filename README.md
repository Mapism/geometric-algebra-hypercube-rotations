# Geometric Algebra Hypercube Rotations

Python implementation for visualising higher-dimensional rotations of hypercubes

## Overview

This repository contains a Python script that constructs an N-dimensional hypercube, rotates it in a higher-dimensional plane and projects the results into 3-dimensional space using geometric algebra.

This code was developed as part of a mathematical research project on applications of geometric algebra in R^N

### 1. Hypercube construction

The code generates all vertices as binary coordinate tuples using:

```python
product((0, 1), repeat=N)
```

These coordinate tuples are then converted into geometric algebra vectors.

### 2. Rotation

The code defines a rotor corresponding to rotation in the given plane

```python
R = exp((plane)*angle*math.pi/180/2)
```

The vertices of the hypercube are rotated using the rotor

```python
R.reverse() * v * R
```

### 3. Projection into 3D

After rotation, the vertices are projected into 3-dimensional space and converted into coordinates.

```python
(Rot[i].lc(I))*e3*e2*e1
```

### 4. Visualisation
The script uses 3-dimensional projective geometric algebra to plot:
- the original hypercube projection
- the rotated hypercube projection

## Dependencies

The script currently imports:

- `kingdon`
- `numpy`
- `sympy`

## Usage

After running, script will ask for:

- the dimension of the hypercube
- the rotation angle in degrees

Example:

```text
Enter dimension: 4
Enter angle: 30
```

After this, the script constructs and displays the initial and rotated hypercube.

## Current Rotation Plane

In the current version of the code, the plane of rotation is hard-coded as:

```python
plane = e1*e2 + e2*e4 + e4*e3 + 2*e2*e4
```

To get meaningful results in dimensions greater than 4, editing the plane of rotation is recommended.


## Author

Mapism

## Repository Purpose

This repository is intended to document and showcase my geometric algebra research project.

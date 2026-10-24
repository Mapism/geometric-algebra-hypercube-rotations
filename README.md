# Geometric Algebra Hypercube Rotations

Python implementation for visualising higher-dimensional rotations of hypercubes

## Overview

This repository contains a Python script that constructs an N-dimensional hypercube, rotates it in a higher-dimensional plane and projects the results into 3-dimensional space using geometric algebra.

This code was developed as part of a mathematical research project on applications of geometric algebra in R^$^{superscript}$

### 1. Hypercube construction
An \(N\)-dimensional hypercube has:
- \(2^N\) vertices
- \(N \cdot 2^{N-1}\) edges

The code generates all vertices as binary coordinate tuples using:

```python
product((0, 1), repeat=N)
```

These coordinate tuples are then converted into geometric algebra vectors.

### 2. Rotor-based rotation
The code defines a bivector plane of rotation and constructs a rotor using an exponential map:

```python
R = exp((plane)*angle*math.pi/180/2)
```

The hypercube vertices are then rotated via:

```python
R.reverse() * v * R
```

This is the geometric algebra analogue of applying a rotation transformation.

### 3. Projection into 3D
After rotation, the vertices are projected into 3-dimensional space and converted into coordinates suitable for visualisation.

### 4. Visualisation
The script uses projective geometric algebra in 3D to represent points and edges, and then plots:
- the original hypercube projection
- the rotated hypercube projection

## Dependencies

The script currently imports:

- `kingdon`
- `numpy`
- `sympy`

Install them with:

```bash
pip install kingdon numpy sympy
```

## Usage

Run the script with Python:

```bash
python your_script_name.py
```

The script will ask for:

1. the dimension of the hypercube
2. the rotation angle in degrees

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

This means the script is most naturally suited to dimensions where these basis elements exist (in particular, \(N \ge 4\)).

## Notes and Limitations

- The rotation plane is currently fixed manually rather than chosen dynamically.
- The script is interactive and expects user input from the terminal.
- Some imported modules/functions are not used in the current version.
- The script is primarily intended as a mathematical exploration rather than a polished software package.

## Research Context

This implementation was developed as part of a research project on applications of geometric algebra in higher-dimensional geometry.

The project studies how geometric algebra can be used to represent rotations and visualise projections of \(N\)-dimensional hypercubes.

## Possible Extensions

Some natural extensions of the project would be:

- allowing the user to choose the rotation plane dynamically
- supporting random rotors
- improving the projection method
- exporting figures automatically
- generalising the visualisation pipeline
- refactoring the code into reusable functions/classes

## Author

Taner Erdem Akyıldız

## Repository Purpose

This repository is intended to document and showcase the computational side of my geometric algebra research project.

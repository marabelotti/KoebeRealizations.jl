# Koebe Realizations

This code computes the realization of a 3-dimensional polytope following [Variational principles for circle patterns and Koebe's theorem](https://arxiv.org/abs/math/0203250), which we call a Koebe realization. 
This implementation is motivated by the paper [Algebraic Degrees of 3-Dimensional Polytopes](https://link.springer.com/article/10.1007/s10013-022-00559-2), of which Mara Belotti is one of the authors.

## Installation

```julia
using Pkg
pkg"add https://github.com/marabelotti/KoebeRealizations.jl.git"
```


## Example 1: The Cube
```julia
using KoebeRealizations

cube = Bool[
    1 1 1 1 0 0 0 0
    1 1 0 0 1 1 0 0
    0 1 1 0 0 1 1 0
    0 0 1 1 0 0 1 1
    1 0 0 1 1 0 0 1
    0 0 0 0 1 1 1 1
]
koebe_realization(cube)
```

```
8×3 Matrix{Float64}:
  0.316228  -0.707107   0.948683
 -0.948684  -0.707106   0.316228
 -0.316228  -0.707107  -0.948683
  0.948683  -0.707107  -0.316228
  0.316228   0.707107   0.948683
 -0.948683   0.707107   0.316228
 -0.316228   0.707107  -0.948683
  0.948683   0.707107  -0.316228
```

## Example 2: The Icosahedron

The input can also be a polytope from `Polymake.jl`. In this case the function also returns a polymake polytope.

```julia
using KoebeRealizations, Polymake

ico = polytope.icosahedron()
Q = koebe_realization(ico)
Polymake.visual(Q)
```

## Example 3: The Circle Packing

Underneath, the algorithm to compute a Koebe realization computes a particular circle packing. This can be visualized as follows:

```julia
using KoebeRealizations
cube = Bool[
    1 1 1 1 0 0 0 0
    1 1 0 0 1 1 0 0
    0 1 1 0 0 1 1 0
    0 0 1 1 0 0 1 1
    1 0 0 1 1 0 0 1
    0 0 0 0 1 1 1 1
]
plot_circle_packing(cube)
```
### Authors

Mara Belotti and Sascha Timme


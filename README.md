# Healpix

[![Build Status](https://travis-ci.org/ziotom78/Healpix.jl.svg?branch=master)](https://travis-ci.org/ziotom78/Healpix.jl)
[![Coverage Status](https://coveralls.io/repos/ziotom78/Healpix.jl/badge.png?branch=master)](https://coveralls.io/r/ziotom78/Healpix.jl?branch=master)

A set of Julia functions that implement the Healpix spherical
projection.

## Installation

From the Julia REPL, run

````julia
Pkg.add("https://github.com/ziotom78/Healpix.jl")
````

## Usage examples

Here are some code snippets that show how to use `Healpix.jl`. It is
interesting to have a look at
[test/runtests.jl](https://github.com/ziotom78/Healpix.jl/blob/master/test/runtests.jl)
as well.

### Dealing with resolutions

The resolution of a Healpix map is uniquely determined by the `NSIDE`
parameter. Healpix.jl precalculates a number of values from `NSIDE` to
save time during computations; such values are saved in a
`Healpix.Resolution` object:

`````
import Healpix
res = Healpix.Resolution(256)
print("The pixel index is $(Healpix.ang2pixNest(res, 0.1, 0.2))\n")
`````

### Reading a map from a FITS file

This snippet loads a map named `planck_70GHz.fits` into an array of
64-bit floating-point numbers:

`````julia
import Healpix

m = Healpix.map("planck_70GHz.fits", 1, Float64)
print("average: $(mean(m.pixels))\n")
`````

## License

Healpix.jl is released under a BSD license. This is possible because it
does not link to the [Healpix library](http://healpix.jpl.nasa.gov/)
(which is covered by the GPL library) but instead implements all its
functions in pure Julia.

> Copyright (c) 2014 Maurizio Tomasi.
>
> Permission is hereby granted, free of charge, to any person obtaining
> a copy of this software and associated documentation files (the
> "Software"), to deal in the Software without restriction, including
> without limitation the rights to use, copy, modify, merge, publish,
> distribute, sublicense, and/or sell copies of the Software, and to
> permit persons to whom the Software is furnished to do so, subject to
> the following conditions:
>
> The above copyright notice and this permission notice shall be
> included in all copies or substantial portions of the Software.
>
> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
> EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
> MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
> IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
> CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
> TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
> SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


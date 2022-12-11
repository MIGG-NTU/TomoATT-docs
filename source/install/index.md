# Installation

TomoATT is a C++ library, developed for working efficiently with parallel computing. For achieving a good IO performance, installing HDF5 with parallel IO option is highly recomended. TomoATT can also run in ASCII IO mode, but all the IO processes are run independently in this case rather than collectively, which causes a slowdown in IO performance.

## Dependencies
- [CMake](https://cmake.org/) (version 3.10 or higher)
- C++ compiler which supports C++17 (version 7.0 or higher for GNU compiler. version 19.0 or higher for Intel compiler.)
- MPI v3.0 or higher  

## Optinal:
- [HDF5](https://www.hdfgroup.org/solutions/hdf5/) (parallel IO needs to be enabled)
- [h5py](https://www.h5py.org/) (used in pre/post processes examples)


```{toctree}
:hidden:

Use_on_local_computers
Use_on_HPCs
```


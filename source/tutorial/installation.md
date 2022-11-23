# Installation

## dependency
- MPI v3.0 or higher  

optinal:
- HDF5 (parallel IO needs to be enabled)
- h5py (used in pre/post processes examples)

## to clone
``` bash
git clone --recursive https://github.com/mnagaso/TomoATT.git
```

## to compile
``` bash
mkdir build && cd build
cmake .. && make -j 8
```

compile with cuda support
``` bash
cmake .. -DUSE_CUDA=True && make -j 8
``` 
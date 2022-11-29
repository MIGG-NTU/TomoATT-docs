# Installation

## dependency
- MPI v3.0 or higher  

optinal:
- HDF5 (parallel IO needs to be enabled)
- h5py (used in pre/post processes examples)


### Install dependence from Conda

#### Create a conda environment

```
conda create --name tomoatt --channel conda-forge
```

Then activate the virtual environment

```
conda activate tomoatt
```

#### Install dependence

```
conda install openmpi "hdf5=*=mpi_openmpi*" -c conda-forge
```

## Clone the source codes

``` bash
git clone --recursive https://github.com/mnagaso/TomoATT.git
```

## Compile source codes

``` bash
mkdir build && cd build
cmake .. && make -j
```

compile with cuda support
``` bash
cmake .. -DUSE_CUDA=True && make -j
``` 

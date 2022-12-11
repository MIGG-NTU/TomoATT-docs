# Use on local computers

This page explains how to prepare the environment and compile TomoATT on local computers.

## Install dependencies

There are freedom to choose the way to install the dependencies. We provide two ways to install the dependencies, using [Conda](https://docs.conda.io/en/latest/) and compiling from source codes.

### Using Conda

[Conda](https://docs.conda.io/en/latest/) provides us a convenient way to install the dependencies, which is easier and faster than installing them from source codes.

#### Create a conda environment

```
conda create --name tomoatt --channel conda-forge
```

Then activate the virtual environment

```
conda activate tomoatt
```

#### Install the required libraries in the created virtual environment

```
conda install openmpi "hdf5=*=mpi_openmpi*" -c conda-forge
```

### Compile and instal the dependencies from source code 
It is often necessary to compile and install the dependencies from source codes, for example, compiling TomoATT on HPCs where the required libraries are not installed in the system.

#### Install MPI and HDF5
The terminal commands below shows an example to download and build openmpi and hdf5 from source codes. The commands are tested on Ubuntu 22.04. The commands may vary on different operating systems.

``` bash
# compile and install hdf5 parallel on linux (tested only on ubuntu 22.04)

# every file will be placed in external_libs
cd ./external_libs

# make a local install pass
mkdir local_mpi_hdf5

# install openmpi

# download source
#wget https://download.open-mpi.org/release/open-mpi/v4.1/openmpi-4.1.3.tar.gz

# Extract it
tar -xvf openmpi-4.1.3.tar.gz
cd openmpi-4.1.3

# configure

# without cuda extension
./configure --prefix=$(pwd)/../local_mpi_hdf5

# make
make -j16 && make install

#
cd ../

# download hdf5 source
wget https://support.hdfgroup.org/ftp/HDF5/releases/hdf5-1.13/hdf5-1.13.3/src/hdf5-1.13.3.tar.gz

#Extract the downloaded directory
tar -xvf hdf5-1.13.3.tar.gz
cd hdf5-1.13.3/

# Configure the code. (the pathes to mpicc, mpicxx should vary on the environment)
CC=$(pwd)/../local_mpi_hdf5/bin/mpicc CXX=$(pwd)/../local_mpi_hdf5/bin/mpicxx ./configure --enable-parallel --enable-unsupported --enable-shared --enable-cxx --prefix=$(pwd)/../local_mpi_hdf5

# make
make -j16 && make install

# now openmpi and hdf5 executables are in external_libs/local_mpi_hdf5/bin
```

#### On HPCs
[Here](./Use_on_HPCs.md) we show some workarounds for compiling the dependencies on a few HPCs which we have been using.

## Download and compile TomoATT

### Clone the source codes

``` bash
git clone --recursive https://github.com/mnagaso/TomoATT.git
```

### Compile source codes with cmake

``` bash
mkdir build && cd build
cmake .. && make -j4
```

or if you have installed your Openmpi and HDF5 in a specific directory (for example ../external_libs/local_mpi_hdf5), you can specify the path to the libraries by adding the following options to the cmake command:


``` bash
cmake .. -DCMAKE_PREFIX_PATH=$(pwd)/../external_libs/local_mpi_hdf5 && make -j4
```

After compiling, the executable file `TOMOATT` will be generated in the `build` directory.

<!-- open it after finishing the cuda support
compile with cuda support
``` bash
cmake .. -DUSE_CUDA=True && make -j
``` 
 -->


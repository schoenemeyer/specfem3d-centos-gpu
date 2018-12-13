# specfem3d-centos-gpu

## Install OpenMPI
```
./configure --prefix=/opt/lib/openmpi/1.10.7
make
sudo make install
sudo make check
```
Add the the Path /opt/lib/openmpi/1.10.7/bin

Download Source Code

## Read Installation Guide

The Installation Guide is available here:
https://specfem3d.readthedocs.io/en/latest/02_getting_started/#getting-started

## Download SPECFEM3D_GLOBE_V7.0.0.tar.gz
from
https://geodynamics.org/cig/software/specfem3d_globe/

## Installation

```
tar xvf SPECFEM3D_GLOBE_V7.0.0.tar.gz
./configure FC=gfortran CC=gcc MPIFC=mpif90 --with-mpi
make

# Run the Meshing Tool
mpirun -np 4 bin/xmeshfem3D
# Run the main program
mpirun -np 4 bin/xspecfem3D

```

## Download Example



## Run the model with GPUs  : Details:
https://www.nvidia.com/en-us/data-center/gpu-accelerated-applications/specfem3d-globe/


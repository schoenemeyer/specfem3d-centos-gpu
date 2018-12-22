# Run SPECFEM3D on CentOS 7.4 with CPU and NVIDIA GPU machines 

For the basics of SPECFEM3D read this website
https://specfem3d.readthedocs.io/en/latest/


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
Typically this example will run on a 6 core Workstation with 16GB RAM in less in 850 secs using 4 cores.
The example needs about 8 GB RAM.

```
 Time step #         1500
 Time:    2.67369890      minutes

 Max norm displacement vector U in solid in all slices for forward prop. (m) =    4038.91577
 Max non-dimensional potential Ufluid in fluid in all slices for forward prop. =    1.39181993E-24

 Elapsed time in seconds =    848.92900201100019
 Elapsed time in hh:mm:ss =      0 h 14 m 08 s
 Mean elapsed time per time step in seconds =   0.56595266800733346

 Time steps done =         1500  out of         1500
 Time steps remaining =            0
 Estimated remaining time in seconds =    0.0000000000000000
 Estimated remaining time in hh:mm:ss =      0 h 00 m 00 s

 Estimated total run time in seconds =    848.92900201100019
 Estimated total run time in hh:mm:ss =      0 h 14 m 08 s
 We have done    100.000000     % of that

```

## Download Example



## Run the model with GPUs:

one can find some basic remarks here, 
https://www.nvidia.com/en-us/data-center/gpu-accelerated-applications/specfem3d-globe/

However the fast way is to issue the follwoing command (assuming using OpenMPI)

./configure FC=gfortran CC=gcc MPIFC=mpif90 --with-cuda-architecture=cuda8  CUDA_LIB=/usr/local/cuda-9.0/lib64 MPI_INC=/opt/lib/openmpi/1.10.7/include

make

For running the Benchmarks download the SPECFEM3D_Cartesian_GPU_READY_FILES_v2.tgz from

https://www.nvidia.com/en-us/data-center/gpu-accelerated-applications/specfem3d-cartesian/

and copy the input_cartesian_v4.tar to your root specfem3d installation folder




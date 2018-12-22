# Run SPECFEM3D on CentOS 7.4 with CPU and NVIDIA GPU machines 

For the basics of SPECFEM3D read this website
https://specfem3d.readthedocs.io/en/latest/

<img src="https://specfem3d.readthedocs.io/en/latest/figures/specfem3d.jpg" width "350">


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

## Run a very simple Testcase to verify that the installation went fine.
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

## Run a very simple Example with 4 cores on a desktop machine

cd EXAMPLES

cd regional_Greece_small

./run_this_example.sh


This  contains an example for a small regional simulation and an event located in southern Greece; the example can be run as a small test on a single desktop machine
  (4 CPUs, forward simulation lasts ~5min, kernel simulation lasts ~10min) 
You will need at least 4GB free memory.



## Run the model with GPUs

Recompile the binaries.

one can find some basic remarks here, 
https://www.nvidia.com/en-us/data-center/gpu-accelerated-applications/specfem3d-globe/

However the fast way is to issue the follwoing command (assuming using OpenMPI)

./configure FC=gfortran CC=gcc MPIFC=mpif90 --with-cuda-architecture=cuda8  CUDA_LIB=/usr/local/cuda-9.0/lib64 MPI_INC=/opt/lib/openmpi/1.10.7/include

make

Rerun the above example , but change the File  Par_file in the DATA directory 
Look for GPU_MODE and change the value to .true.
```
# set to true to use GPUs
GPU_MODE                        = .false.
# Only used if GPU_MODE = .true. :
GPU_RUNTIME                     = 1
# 2 (OpenCL), 1 (Cuda) ou 0 (Compile-time -- does not work if configured with --with-cuda *AND* --with-opencl)
GPU_PLATFORM                    = NVIDIA
GPU_DEVICE                      = Tesla
```

## More Examples

For running the Benchmarks download the SPECFEM3D_Cartesian_GPU_READY_FILES_v2.tgz from

https://www.nvidia.com/en-us/data-center/gpu-accelerated-applications/specfem3d-cartesian/

and copy the input_cartesian_v4.tar to your root specfem3d installation folder




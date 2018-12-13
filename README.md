# specfem3d-centos-gpu

# Install OpenMPI
```
./configure --prefix=/opt/lib/openmpi/1.10.7
make
sudo make install
sudo make check
```
Add the the Path /opt/lib/openmpi/1.10.7/bin

Download Source Code

# Read Installation Guide
https://specfem3d.readthedocs.io/en/latest/02_getting_started/#getting-started

# Download SPECFEM3D_GLOBE_V7.0.0.tar.gz

https://geodynamics.org/cig/software/specfem3d_globe/

```
./configure FC=gfortran CC=gcc MPIFC=mpif90 --with-mpi

```


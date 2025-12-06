# Obtaining the code

The plugin is hosted [on Github](https://github.com/andysim/MPIDOpenMMPlugin) and can be checked out with
``` bash
git clone git@github.com:andysim/MPIDOpenMMPlugin
```

# Dependencies

The code needs OpenMM version 8.0 or later, which can be installed as follows.

## Installation of Dependencies via Conda

Conda is *strongly* recommended for managing the environment and dependencies;
after [downloading](https://conda.io/docs/download.html) anaconda (make sure
you use `bash` or `zsh`).

To install OpenMM 8.0+ into its own Conda environment called `mpid`, run
``` bash
conda create -n mpid openmm>=8.0 cuda-toolkit=11.8 swig cmake -c conda-forge
```
Make sure you request the version of the CUDA toolkit supported on your
cluster (CUDA 11.2 or later is recommended for OpenMM 8.0+). You can adjust the
cuda-toolkit version (e.g., cuda-toolkit=12.0) based on your GPU and driver
compatibility. OpenMM 8.0+ requires CMake 3.17 or later and uses modern CMake
CUDA support instead of the deprecated FindCUDA module. This example uses GCC
to build; the speed of the C++ compiler is irrelevant, because the CUDA code is
the only fast code available in this plugin.  Although the reference platform
will run, it is very slow and designed for correctness.

## Building the plugin

The plugin uses CMake (version 3.17 or later) for building, which should be
installed locally; it can be obtained from Conda if you do not have it
available. Once CMake is installed, you can build the code using commands
similar to the following (the exact type of modules and mechanisms to load
them will vary from system to system)::

``` bash
conda activate mpid

export OPENMM_INSTALL_DIR=~/anaconda3/envs/mpid

# From the MPIDOpenMMPlugin top level directory
mkdir build
cd build
cmake .. -DCMAKE_INSTALL_PREFIX=$OPENMM_INSTALL_DIR -DPYTHON_EXECUTABLE=`which python` -DOPENMM_DIR=$OPENMM_INSTALL_DIR
make -j 4
make test
make install
make PythonInstall
```
Note that the C++ and CUDA standards are now automatically set to C++14 by
CMake, which is required for OpenMM 8.0+. The nature of the C++ compiler is not
critical, as the faster kernels are implemented in CUDA and only the slow
reference implementation is available on regular CPUs.

Before running the code, make sure you load the conda environment and all
modules used for building when using the plugin.
``` bash
conda activate mpid
```

# Installation Guide

This guide provides instructions for installing the MPIDOpenMMPlugin for use with OpenMM 8.0 or later.

## Requirements

- OpenMM version 8.0 or later
- CMake version 3.17 or later
- C++14 compatible compiler
- CUDA toolkit (optional, for GPU acceleration)
- Python 3.7 or later
- SWIG (for Python bindings)

## Quick Installation

### 1. Install OpenMM via Conda (Recommended)

We strongly recommend using Conda to manage dependencies:

```bash
conda create -n mpid openmm>=8.0 cuda-toolkit swig cmake -c conda-forge
conda activate mpid
```

### 2. Clone the Repository

```bash
git clone https://github.com/andysim/MPIDOpenMMPlugin
cd MPIDOpenMMPlugin
```

### 3. Build and Install the Plugin

```bash
export OPENMM_INSTALL_DIR=~/anaconda3/envs/mpid

mkdir build
cd build
cmake .. -DCMAKE_INSTALL_PREFIX=$OPENMM_INSTALL_DIR \
         -DPYTHON_EXECUTABLE=`which python` \
         -DOPENMM_DIR=$OPENMM_INSTALL_DIR
make -j 4
make test
make install
make PythonInstall
```

### 4. Verify Installation

```bash
python -c "import openmm; import mpidplugin; print('Installation successful!')"
```

## Important Notes

- **OpenMM 8.0+ Compatibility**: This version of the plugin is specifically updated to work with OpenMM 8.0 and later versions, which require:
  - CMake 3.17 or later
  - C++14 standard (automatically set)
  - Modern CMake CUDA support (no longer using deprecated FindCUDA)

- **Python Compatibility**: The plugin now uses setuptools instead of distutils for better compatibility with Python 3.12+

- **CUDA Support**: The plugin will automatically detect and enable CUDA if available. The CUDA platform is much faster than the reference platform.

## Detailed Documentation

For more detailed build instructions, troubleshooting, and usage information, please refer to:
- [Building Documentation](docs/source/building.md)
- [User Manual](https://andysim.github.io/MPIDOpenMMPlugin/)

## Support

For issues and questions, please visit the [GitHub repository](https://github.com/andysim/MPIDOpenMMPlugin).

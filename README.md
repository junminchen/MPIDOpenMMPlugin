# About

This plugin implements polarizable multipole electrostatics, primarily aimed at
supporting the [MPID](https://doi.org/10.1063/1.4984113) formulation of the
CHARMM Drude force field.  The code supports multipoles up to octopoles, as
well as induced dipoles that may be either isotropic or anisotropic.

**OpenMM 8.0+ Compatible**: This plugin has been updated to work with OpenMM
version 8.0 and later, using modern CMake (3.17+) and C++14 standard.

# Installation

For installation instructions, see [INSTALLATION.md](INSTALLATION.md) or the
detailed [building documentation](docs/source/building.md).

# Documentation

The user manual describing usage and technical aspects of the code can be found
[here](https://andysim.github.io/MPIDOpenMMPlugin/).

# License

The code is distributed freely under the terms of the BSD 3 clause license,
which can be found in the top level directory of this repository.

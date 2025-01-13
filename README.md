# A meaningful title

This is the github repository containing the little coding exercise for the applicants for the PhD position in the group of Sera Markoff. For questions reach out to any of Marc Klinger-Plaisier, Dimitris Kantzas, Aylecia Lattimer or Laura Olivera-Nieto.

## Table of contents

- Installation advice
- Background information and exercise for applicants

## Installation advice

The simplest way to get the code running is via a conda environment. If you don't have conda/anaconda/miniconda/microconda/mamba/.. or anything similar yet, get [micromamba](https://mamba.readthedocs.io/en/latest/installation/micromamba-installation.html). Micromamba is the small version of mamba, which is a faster implementation of conda, which is a package manager that allows you to install packages/libraries inside an environment. Otherwise use what you have already installed.

The next step is to create a new environment for this project and install all the packages:

`micromamba create -n jetexample python numpy matpotlib jupyterlab pybind11 gcc make cmake gsl -c conda-forge`

Since part of the code is written in C++ and needs to be compiled using `cmake` and `make`, it is important to have a compiler installed. Depending on your operating system you can exchange the `gcc` flag with a different compiler (e.g., `gxx` or `clang`).

In order to use the environment, it must be activated:

`micromamba activate jetexample`

Next, the C++ code has to be compiled. Go into the root directory of the repository and run:

`cmake .`

This will create a `Makefile`, which can be executed to perform the compilation:

`make` 

Now a shared library file ending on `*.so` has been created. This can be imported in python as described in `example_notebook.ipynb`.

Of course the code can also be used in `C++`. For this the `BhJetClass` in `bhject_class.hh` and `bhject_class.cpp` can be used. The method/attribute names are mapped with identical names.



## Background information and exercise for applicants

The idea of this is to ...

Please look into this before the interview days and don't overdo it..

The data comes from ... Background information on the model can be found at ...
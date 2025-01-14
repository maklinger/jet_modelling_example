# Exemplary BHJet application to the X-Ray binary GX 339-4

This is the github repository containing the little coding exercise for the applicants for the PhD position in the group of Sera Markoff. For questions reach out to any of Marc Klinger-Plaisier, Dimitrios Kantzas, Aylecia Lattimer, Laura Olivera-Nieto, or Sera Markoff.

## Table of contents

- Background information and exercise for applicants
- Installation advice


## Background information and exercise for applicants

The idea of this is to provide you with a simple coding exercise that involves modeling with the grops BHJet code and prepares you for the PhD position. Please have a look at this before the interview days.

The goal is to use the BHJet model to reproduce the data of the prototype X-ray binary GX 339-4. The data consists of a spectral energy distribution in the file `Data/gx339-4_mw.csv`. The BHJet model is described in detail in [this paper](http://arxiv.org/abs/2108.12011), and involves many free parameters. Familiarise yourself with the general setup of the model and focus on the most important parameters in Table 2 (You can ignore the additional absorption/reflection components which are not part of BHJet and handled via the parameters `rel_refl, line_norm, line_E, line_sigma, nH`). Play around with them and try to reproduce these different scenarios, and understand their physical differences.

The BHJet model is implemented in `C++`. It can either be used directly in `C++` or in `python` using `pybind11` in the pyBHJet code. It needs to be compiled to a library first, as discussed below. Then it can be included and used as in the exemplary Jupyter notebook `example_notebook.ipynb`.


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



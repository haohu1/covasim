# Covasim

Covasim is a stochastic COVID-19 agent-based simulator that can be used for
COVID-19 (novel coronavirus, SARS-CoV-2) epidemic projections, scenario
interventions, etc. It can also be adapted to different contexts (for example,
the Diamond Princess cruise ship, cities, countries).


## Requirements

Python >=3.6 (64-bit).

We also recommend, but do not require, using Python virtual environments. For
more information, see documentation for [venv](https://docs.python.org/3/tutorial/venv.html) or [Anaconda](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html).

## Installation

1.  Clone a copy of the repository. If you intend to make changes to the code,
    we recommend that you fork it first.

2.  (Optional) Create and activate a virtual environment.

3.  Navigate to the root of the repository and install the Covasim Python package
    using one of the following options:

    *   To install with webapp support (recommended):

        `python setup.py develop`

    *   To install as a standalone Python model without webapp support:

        `python setup.py develop nowebapp`

    *   To install Covasim and optional dependencies (be aware this may fail
        since it relies on private packages), enter:

        `python setup.py develop full`

    The module should then be importable as `import covasim`.


## Usage

There are several examples under the `examples` directory. Run them using the following syntax:

`python examples/simple.py`

The example above creates a figure and other examples run Covasim simulations.


## Structure

All core model code is located in the `covasim` subfolder; standard usage is
`import covasim as cv`. The other subfolders, `cruise_ship` and `webapp`, are
also described below.


### covasim

The model consists of two core classes: the `Person` class (which contains
information on health state), and the `Sim` class (which contains methods for
running, calculating results, plotting, etc.).

The structure of the `covasim` folder is as follows:

* `base.py`: The `ParsObj` class, plus basic methods of the `BaseSim` class, and associated functions.
* `interventions.py`: The classes for adding interventions and dynamically modifying parameters.
* `parameters.py`: Functions for creating the parameters dictionary and populating correct attributes for people.
* `people.py`: Class for people and functions to create a population of people.
* `README.md`: Detailed information on the model parameters.
* `requirements.py`: Check that imports succeeded, and turn off features if they didn't.
* `run.py`: Functions for running simulations (e.g. parallel runs and scenarios).
* `sim.py`: The core class defining the model, namely `Sim`, which initializes the model, runs, and plots.
* `utils.py`: Numeric utilities, mostly based on Numba, for choosing random numbers (plus other helper functions).
* `version.py`: Version and version date information.


### cruise_ship

A version of the Covasim model specifically adapted for modeling the Diamond
Princess cruise ship. It uses its own parameters file (`parameters.py`) and has
slight variations to the model (`model.py`).


### webapp

For running the interactive web application: please see the `README.md` in that
folder for more information, including information on Docker deployment.


## Disclaimer

The code in this repository was developed by IDM to support our research in
disease transmission and managing epidemics. We’ve made it publicly available
under the Creative Commons Attribution-Noncommercial-ShareAlike 4.0 License to
provide others with a better understanding of our research and an opportunity to
build upon it for their own work. We make no representations that the code works
as intended or that we will provide support, address issues that are found, or
accept pull requests. You are welcome to create your own fork and modify the
code to suit your own modeling needs as contemplated under the Creative Commons
Attribution-Noncommercial-ShareAlike 4.0 License.

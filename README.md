[![Anaconda-Server Badge](https://anaconda.org/haasad/eidl/badges/version.svg)](https://anaconda.org/haasad/eidl) [![Anaconda-Server Badge](https://anaconda.org/haasad/eidl/badges/latest_release_date.svg)](https://anaconda.org/haasad/eidl) [![Anaconda-Server Badge](https://anaconda.org/haasad/eidl/badges/downloads.svg)](https://anaconda.org/haasad/eidl) [![Build Status](https://travis-ci.org/haasad/EcoInventDownLoader.svg?branch=master)](https://travis-ci.org/haasad/EcoInventDownLoader)
# EcoInventDownLoader (eidl)

The EcoInventDownLoader (eidl) is a small python package that automates the somewhat tedious process of adding an ecoinvent database to your [brightway2](https://brightway.dev/) project. Without `eidl` the following steps are required:

- Login to the ecoinvent homepage
- Choose and download the required database
- Unpack the 7z-archive on your computer (which will take up close to 2GB of disk space)
- Import the ecospold2 files with the `bw2io.SingleOutputEcospoldImporter`

With `eidl`, the above steps can all be carried out with a single command from a jupyter notebook or any python shell:
```
eidl.get_ecoinvent()
```
You will be asked to enter your ecoinvent username and password, and which version and system model you require. The database will then be added to your brightway2 project. Download and extraction are carried out in the background in a temporary directory, which is cleared after the import and therefore doesn't use up your disk space.

## Prerequisites

- Valid [ecoinvent](https://www.ecoinvent.org) login credentials

## Installation

- Add the required conda channels to your conda config file, if you haven't done so already (ie. for the installation of brightway2):
```
conda config --append channels conda-forge
conda config --append channels cmutel
conda config --append channels haasad
```
- Simply install with conda:
```
conda install eidl
```
- ___Alternatively___ you can install `eidl` without adding the channels permanently:
```
conda install -c defaults -c conda-forge -c cmutel -c haasad eidl
```

## Usage

```python
import eidl
import brightway2 as bw

bw.projects.set_current('eidl_demo')

bw.bw2setup()
eidl.get_ecoinvent()
```

See also the [example notebook](./example_usage.ipynb) for more details.

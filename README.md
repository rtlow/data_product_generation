# data_product_generation

AREPO post-processing scripts

These notebooks (whose functionality could be easily translated into scripts) are used for calculating
statistics from `Subfind` catalogs and consolidating general parameters from simulation output.

Data products are dumped into the [`data_products`](https://github.com/rtlow/data_products) submodule, which needs to be checked out through
```
git submodule update --init
```

After cloning this repo,
the easiest way to initialize the python environment is to use the `uv` environment manager
```
cd parameter_building
uv sync
```

# Usage
Individual `jupyter` notebooks perform certain calculations.
All notebooks search for folders containing simulation snapshots and `Subfind` catalogs within the
top level search path `data_dir`.
Following my internal naming convention, this is all subdirectories prefixed with `run_`.
Data products are output into the simulation's corresponding subdirectory within `data_products`.

These data products are easily loaded and interacted with using the [`cosmoSim`](https://github.com/rtlow/cosmoSim)
module.

## get-profiles
Calculates cumulative distributions of halo mass and maximum circular velocity for `Subfind` subhalos.

## get-pyliansPK
Calculates matter power spectra using [`pylians`](https://github.com/franciscovillaescusa/Pylians).

## get-RDP-profile
Calculates the cumulative distribution of distances between subhalos according to halo mass and
Vmax cuts from [Todoroki 2019](https://ui.adsabs.harvard.edu/abs/2019MNRAS.483.3983T/abstract).

## get-SFR-profile
Calculates the cumulative distribution of star formation rates in subhalos.

## get-snapshot-info
Parses simulation information from snapshot files and the simulation run name and
compiles them into a `run_info.json`.
Use with [`cosmoSim`](https://github.com/rtlow/cosmoSim) for easy access
and analysis.

## get-genPK-info
Calculates matter power spectra using [`GenPK`](https://github.com/sbird/GenPK).
**Deprecated**. Use `get-pyliansPK` instead.

## get-group-profiles
Calculates cumulative distributions of halo mass and maximum circular velocity for FoF groups.
**Deprecated** Typically, statistics of `Subfind` subhalos are desired, so `get-profiles` should be used instead.

## get-spectra-mocks
Uses [`fake_spectra`](https://github.com/sbird/fake_spectra) to calculate mock Lyman-alpha spectra
from simulation snapshots.
**Deprecated**. These calculations are more efficiently performed and parallelized on a supercomputing cluster.
Final files are also too heavy for github.
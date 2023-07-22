# Geospatial Time Series Analysis
Methods to stack geospatial rasters and make memory-efficient computations along the time axis. 

## Installation

Download and install [Miniconda](https://docs.conda.io/en/latest/miniconda.html)  

After installing Miniconda set up [Mamba](https://mamba.readthedocs.io/en/latest/installation.html) (optional but recommended)
```
$ conda install mamba -n base -c conda-forge
```
Clone the repo and set up the conda environment  

```
$ git clone https://github.com/friedrichknuth/gtsa.git
$ cd ./gtsa
$ mamba env create -f environment.yml
$ conda activate gtsa
$ pip install -e .
```

## Examples
Below are various command line utilities and corresponding Jupyter notebooks with Python examples.  
See `--help` flag for more information about each command.

### Processing

#### Stack single band rasters and chunk along the time dimension for efficient data retrieval
- notebooks/processing/01_create_stacks.py
- scripts/processing/01_create_stacks.py

#### Run memory-efficient time series analysis methods using dask
- notebooks/processing/02_time_series_computations.ipynb
- scripts/processing/02_time_series_computations.py

### Visualization


#### Convert single band rasters to Cloud Optimized GeoTIFFs (COGs)

```
create_cogs -datadir data \
            -outdir data/cogs
```

Python examples in `notebooks/visualization/01_create_cogs.ipynb`

#### Create interactive folium map for efficient visualization
- notebooks/visualization/02_create_cog_map.ipynb
- scripts/visualization/02_create_cog_map.py

## Download sample data

```
download_data --help

  Downloads historical orthoimage and digital elevation model data from
  https://doi.org/10.5281/zenodo.7297154

Options:
  --site TEXT            Use 'mount-baker' or 'south-cascade' (without quotes).
  --outdir TEXT          Your desired output directory path.
  --product TEXT         Use 'dem' or 'ortho' (without quotes).
  --include_refdem       Set to download reference DEM for site.
  --max_workers INTEGER  Number of workers (cores) to be used.
  --overwrite            Set to overwrite existing outputs.
  --silent               Set to silence information printed to stdout.
  --help                 Show this message and exit.
```

Example

```
download_data --site south-cascade \
              --outdir data \
              --product dem \
              --include_refdem \
              --max_workers 8 \
              --verbose \
              --overwrite
```

## Data citations

Knuth. F. and D. Shean. (2022). Historical digital elevation models (DEMs) and orthoimage mosaics for North American Glacier Aerial Photography (NAGAP) program, version 1.0 [Data set]. Zenodo. https://doi.org/10.5281/zenodo.7297154 

Knuth, F., Shean, D., Bhushan, S., Schwat, E., Alexandrov, O., McNeil, C., Dehecq, A., Florentine, C. and O’Neel, S., 2023. Historical Structure from Motion (HSfM): Automated processing of historical aerial photographs for long-term topographic change analysis. Remote Sensing of Environment, 285, p.113379. https://doi.org/10.1016/j.rse.2022.113379 


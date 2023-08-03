# Pangeo is joining the OSGeo Community Sprint 2023 at the BiDS conference in Vienna, Nov 6-9

BiDS event page: https://www.bigdatafromspace2023.org/code-sprint

Osgeo wiki page: https://wiki.osgeo.org/wiki/OSGeo_Community_Sprint_2023#Participants

This is our info repository for the joint OSGEO and Pangeo code sprint at ESA BIDS in November 2023

## Pangeo projects and activities planned

(fork and submit pull requests if you wish to suggest Pangeo-related projects for the code sprint)

A series of ideas are posed around Discrete Global Grid Systems (DGGS). It would be great to enable data-cube type analysis operations around xarray that use DGGS. For more info read this [discourse thread](https://discourse.pangeo.io/t/discrete-global-grid-systems-dggs-use-with-pangeo/2274).

Learn a bit more about DGGS from this info page: https://dggs-info.web.app/#/

### Python bindings for DGGRID

Alexander Kmoch 

[DGGRID](https://github.com/sahrk/DGGRID) is currently a command-line tool written in C++ to construct and work with various DGGS. It would be great to have Python bindings to be able to utilise the high-performance functions directly in Python.

Various ways are possible to link Python to C++, such as [PyBind11](https://pybind11.readthedocs.io) or [cppyy](https://cppyy.readthedocs.io/), or classic Python ctypes.

Akin to https://github.com/allixender/dggrid4py (a Python wrapper that makes a syscall to execute DGGRID) or https://github.com/am2222/pydggrid (abandoned, PyBind11).


### H3 or rHEALPIx + Xoak + Xarray

Alexander Kmoch

Explore Xarray data cube integration but with data loaded from DGGS encoded data (e.g. in a Zarr or Parquet source) or load GeoTiff/NetCDF and resample into DGGS encoded data.

For that some base workflows of data conversion methods can be provided as guidance and and rough xoak demo is also rather quickly possible. But there are no best practices or performance tests yet and no deeper integration in Xarray so DGGS would be more transparent.

Develop an integration to explore, query and analyse data in Xarray, such as .sel (where parent cell IDs are XYZ, DGGS query semantics are often cell ID and topology based).

- https://xoak.readthedocs.io
- https://github.com/manaakiwhenua/rhealpixdggs-py
- https://h3geo.org/

### H3 or rHEALPIx + Xoak + Xarray + Xvec?

Same as above, but vector data cubes and Xvec (via GeoPandas), with DGGS geometries (explicit or implicit).

- https://xvec.readthedocs.io

### Unstructured grids and DGGS conversion

Unstructured grids are widely used in the ocean and climate sciences, e.g. Global Circulation Models (GCM) - [xgcm](https://github.com/xgcm/xgcm), [ICON](https://www.dwd.de/EN/research/weatherforecasting/num_modelling/01_num_weather_prediction_modells/icon_description.html) (Icosahedral Nonhydrostatic) Model, or [MPAS](https://mpas-dev.github.io/) (Model for Prediction Across Scales).

Some developments are on-going that work well with Xarray and unstructured grids, for example:

- https://raijin.ucar.edu/
- https://github.com/UXARRAY/uxarray

How much of the functionality needed for DGGS is similar / the same as required for icosahedral GCM grids?

If there is a lot of overlap, maybe we can leverage many of the same software elements.


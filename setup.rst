.. _section_download:

**MODEL DOWNLOAD AND SETUP**
=============================

**********************
Download source code 
**********************

`Version beta: not fully tested. click here to download/clone from GitHub <https://github.com/fengyanshi/FUNWAVE-TVD>`_

`Version 3.3 Released July 19 2018: click here to download from GitHub <https://github.com/fengyanshi/FUNWAVE-TVD/releases>`_

`Version 3.2 Released Jan 27 2018: click here to download from GitHub <https://github.com/fengyanshi/FUNWAVE-TVD/releases>`_

Version 3.1 Released Sep 2017: Used for FUNWAVE-TVD Workshop 2017 `click here to download <https://github.com/fengyanshi/FUNWAVE-TVD/releases>`_

Version 3.0: Released Apr 2017 :download:`download here <versions/funwave_tvd_30.zip>`

Versions 1.0, 1.1, 2.0, 2.1: Please contact fyshi@udel.edu

*************************
Download simple examples
*************************

Simple examples are included in the package of Version 3.1 and higher (`click here to download from GitHub <https://github.com/fengyanshi/FUNWAVE-TVD>`_) . They are located in the directory /simple_cases/. 
The simple examples serve as baseline cases for testing your system. You can also choose a simple case similar to your modeling scenario to set up your case. The following simple cases available. The simple examples are also used during the FUNWAVE training workshop. 

* `Waves on 1D slope <slope.html>`_

* `Waves on 2D beach <beach_2d.html>`_

* `Waves and rip currents on 2D beach <rip_2d.html>`_

* `Sediment transport in 2D rip channels <sediment_rip.html>`_

* `Surface waves at an inlet-beach-shoal system <inlet_shoal.html>`_

* `Japanese Tohoku tsunami (Ocean-basin scale) <tohoku.html>`_

* `ship-wakes <vessel.html>`_

* `ship-wakes + sediment transport <vessel_morpho.html>`_

* `Meteotsunami <meteo.html>`_

***************************
Download benchmark tests
***************************

Benchmark tests are validation and verification (V & V) cases with model comparisons with lab or field experiment data. `Available benchmarks: click here to download from GitHub <https://github.com/fengyanshi/BENCHMARK_FUNWAVE>`_


*************************
Compile and setup
*************************

1. uncompress the code from the package downloaded
2. modify *Makefile* if needed. There are several necessary flags in Makefile needed to specify below. 

* --DDOUBLE_PRECISION: use double precision, default is single precision.
* --DPARALLEL: use parallel mode, default is serial mode.
* --DCARTESIAN: Cartesian version, otherwise Spherical version
* --DINTEL: if INTEL compiler is used, this option can make use of FPORT for the RAND() function
* --DCRAY: for CRAY RAND() and system commands
* --DCOUPLING: nesting mode.
* --DSPHERICAL_IJ_STATION: in spherical mode, if you want your station locations defined by grid point (I,J). Otherwise, station locations should be defined by (lat lon).  
* --DVESSLE: include shipwake module
* --DSEDIMENT: include sediment and morphological module
* --DWIND: include wind effect
* --DMETEO: include meteo tsunami module
* --DMANNING: use Manning formula for bottom friction
* --DCHECK_MASS_CONSERVATION: correct mass conservation problem caused by wetting/drying
* --DTRACKING: include Lagrangian tracking module
* CPP: path to CPP directory.
* FC: Fortran compiler. 

3. compile the code

in command line type

> make clean

> make

The executable file such as 'funwave' or 'mytvd' (specified in *Makefile*) will be generated.   **Note: always use 'make clean' after modifying Makefile**.  

4. run the model

Modify input.txt if needed and run. 




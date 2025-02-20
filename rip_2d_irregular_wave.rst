Irregular wave normal incidence
########################################

.. figure:: images/simple_cases/rip_vort.jpg
    :width: 500px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center

Figure: (left) snapshot of surface elevation, (middle) vorticity field, (right) mean current field 

**input.txt:**

|  **Parallel(if applicable)**
|   PX = 4
|   PY = 4

|  **Depth**  
|   DEPTH_TYPE = DATA 
|   DEPTH_FILE = ../bathy/depth_a15.txt 

|  **Output folder** 
|   RESULT_FOLDER = output/ 
 
|  **Dimensions**
|   Mglob = 512
|   Nglob = 250 

|  **Time**
|   TOTAL_TIME = 1200.0 
|   PLOT_INTV = 50.0 
|   PLOT_INTV_STATION = 0.5 
|   SCREEN_INTV = 50.0 

|  **Wave averaging property** 
|   T_INTV_mean = 50.0 
|   STEADY_TIME= 100.0 


|  **Grid sizes**
|   DX = 1.0 
|   DY = 2.0 

|  **Wavemaker** 
|   WAVEMAKER = WK_IRR
|   DEP_WK = 13.0 
|   Xc_WK = 425.0 
|   Yc_WK = 0.0 
|   FreqPeak = 0.1 
|   FreqMin = 0.03
|   FreqMax = 0.5 
|   Hmo = 1.0 
|   GammaTMA = 5.0 
|   ThetaPeak = 0.0 
|   Sigma_Theta = 10.0 

|  **Sponge layer** 
|   FRICTION_SPONGE = T 
|   DIRECT_SPONGE = T 
|   Csp = 0.0 
|   CDsponge = 1.0 
|   Sponge_west_width =  0.0 
|   Sponge_east_width =  60.0 
|   Sponge_south_width = 0.0 
|   Sponge_north_width = 0.0 

|  **Lateral boundary condition** 
|   PERIODIC = T 

|  **Wetting and drying** 
|   MinDepth=0.01 

|  **Physics** 
|   Cd = 0.002

|  **Breaking scheme**
|   VISCOSITY_BREAKING = F  

|  **Output** 
|   ETA = T 
|   U = T
|   V = T
|   Umean = T 
|   Vmean = T   
|   MASK = T 
|   WaveHeight = T 

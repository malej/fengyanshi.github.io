Single vessel + sediment 
###################################

* Model setup

.. figure:: images/simple_cases/layout_single_vessel.jpg
    :width: 500px
    :align: center
    :height: 120px
    :alt: alternate text
    :figclass: align-center


* input.txt
  is in the folder /simple_cases/single_vessel_morphology/

**In input.txt:**

|  **Parallel Info (if use parallel)**  
|   PX = 4 
|   PY = 1

|  **Depth**
|   DEPTH_TYPE = DATA

  DEPTH_FILE = depth.txt

|  **Dimensions**
|   Mglob = 2400
|   Nglob = 60

|  **Grid sizes**
|   DX = 1.0
|   DY = 1.0

|  **Set up time**
|   TOTAL_TIME = 2000.0
|   PLOT_INTV = 5.0
|   PLOT_INTV_STATION = 50000.0
|   SCREEN_INTV = 5.0

|  **Sediment**
|   Bed_Change = T
|   BedLoad = T
|   D50 = 0.0005
|   Sdensity = 2.68
|   n_porosity = 0.47
|   WS = 0.0125
|   Shields_cr = 0.055
|   Shields_cr_bedload = 0.047
|   Tan_phi = 0.7
|   Kappa1 = 0.3333
|   Kappa2 = 1.0
|   MinDepthPickup = 0.1 

|  **Add vessels**
|   VESSEL_FOLDER = ./
|   NumVessel = 1
| 
|   You need a vessel file: vessel_00001 in the current folder. 
|   In vessel_00001, specify:
|   Title: Vessel # 1
|   Blue_Star_I
|   Length(m), Width(m), Alpha(0.5), Beta(0.5), P(draft,m)
|   10.0  5.0, 0.5, 0.5, 1.5
|   Time, X(m), Y(m)  (relative to the orgin of the coordinates)
|   0.0   40.0   60.0
|   25523.0  180040.0  60.0

|  **Output**
|   RESULT_FOLDER = output
|   ETA = T

|  **post-processing**
|   matlab scripts in /simple_cases/single_vessel_morphology/

.. figure:: images/simple_cases/single_wave_conc.jpg
    :width: 400px
    :align: center
    :height: 600px
    :alt: alternate text
    :figclass: align-center

    Shipwakes and sediment concentration at different times.



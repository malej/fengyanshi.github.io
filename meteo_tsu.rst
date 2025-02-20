Wind and Pressure Field
************************

**SPECIFICATION OF WIND EFFECT**

 *  WindForce: logical parameter representing if wind effect is taken into account. T or F. 

 * AirPressure: logical parameter representing if pressure effect is taken into account. T or F. 

 * WindWaveInteraction: logical parameter representing if wave-wind interaction (Chen et al. 2003) based on the formula presented in 'METEO module' in INTRODUCTION section. The parameter WindCrestPercent will be used.  

 *  Cdw: wind stress coefficient for the quadratic formula if WindForce = T. Default: 0.002.

 *  WindCrestPercent: ratio of the forced wave crest height to the maximum surface elevation, if WindForce = T. Default: 100\% (for storm surges). 


 * WindConstantField: logical parameter for constant wind field. T or F.
    
 *  WIND\_FILE: file name for the constant wind field. The following is an example of data format.

  wind data

  100  - number of data

  0.0 ,    10.0 0.0   ---  time(s), wu, wv (m/s)

  2000.0,   10.0,  0.0

  8000.0,  10.0,   0.0
 
  ... 


 * WindHollandModel: logical parameter for Holland model. T or F. 

 * STORM\_FILE: name of file contains paramters used for Holland hurricane model

  A sample: 

    STORM FILE (model does not read)

    Sandy - storm name

    time(s),     x(m), y(m),    pn(mb),   pc(mb),   A,    B (model does not read)

    0.0,  800000.0, 400000.0,   1005.0, 950.0, 23.0, 1.50 - time, x,y, pn, pc, A, B

    120000.0,  800000.0, 1500000.0,  1005.0, 950.0, 23.0, 1.50 



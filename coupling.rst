Coupling (Manually)
**********************************

The present version has a capability for one-way coupling with other models such as NHWAVE or FUNWAVE-TVD itself. The nesting scheme passes surface elevation and velocity components calculated from other models or FUNWAVE-TVD in a large domain to a nested small domain through ghost cells at nesting boundaries. To run a nested model, the following procedures should be performed.

1. The coupling option in Makefile should be defined as '-Dcoupling''. The program should be re--compiled.

2. Prepare nesting data using the output of a large-domain model. The following is an example of the data format.

 coupling data

 boundary info: num of points (negative means no point), start point 

 EAST 

          -1,           1   (no data on east side)

 WEST 

           5,           1   (5 points at west boundary, start from  1) 

 SOUTH 

          -1,         0   ( no data on south side) 

 NORTH 

          -1,        0   (no data on north side)

 TIME SERIES 

   68.443001    (*first step, NOTE: model clock will be initialized as this time*)

 EAST SIDE  (*no nesting on east side*)

 WEST SIDE 

    0.141220E-02    0.141220E-02    0.141220E-02   0.141220E-02    0.141220E-02 (*u*) 

   -0.119260E-10    -0.119260E-10   -0.667390E-10  -0.667390E-10   -0.219240E-10 (*v*) 

    0.141890E-02    0.141890E-02   0.141890E-02  0.141890E-02   0.141890E-02   (*z*) 

 SOUTH SIDE (*no nesting on south side*) 

 NORTH SIDE (*no nesting on north side*) 

   68.641998    (*next time step*) 

   ...
           
 The example above is a case that a model nesting  takes place at the WEST (left) boundary of a small domain.   Boundaries are defined with the order: EAST, WEST, SOUTH, and NORTH. If the num of points of a boundary is larger than zero, the program will read a time series of (u, v, eta) below 'XXXX SIDE'. The read format is

             READ(11,*) TIME\_COUPLING\_2 

             READ(11,119)(U\_COUPLING\_EAST(I,2),I=1,N\_COUPLING\_EAST)

             READ(11,119)(V\_COUPLING\_EAST(I,2),I=1,N\_COUPLING\_EAST)

             READ(11,119)(Z\_COUPLING\_EAST(I,2),I=1,N\_COUPLING\_EAST)

           ENDDO 

 119      FORMAT(5E16.6) 
           
where N\_COUPLING\_EAST is Num of points at the EAST boundary.
       
 
3.Specify the file of coupling data in input.txt

  ! ----------------- COUPLING -------------------------

  ! if do coupling, have to set -DCOUPLING in Makefile 

 COUPLING\_FILE = coupling.txt 

 where 'coupling.txt' is the file saved in procedure 2. 


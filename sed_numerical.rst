.. _section_sed_numerical:

Numerical Scheme for Sediment Transport
****************************************

.. figure:: images/grid.jpg
    :width: 300px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center

Following Shi et al. (2012), the finite-volume approach is used for solving the advection-diffusion equation.  A modified interface construction method is proposed for the sediment concentration. For time-integration, the third-order Stability-Preserving (SSP) Runge-Kutta scheme. The bed evolution equation is solved directly using the forward differencing. The numerical schemes for solving the Boussinesq equations are kept unchanged. The grid arrangement of variables for solving advection-diffusion is shown in Figure above. 


* Space-differencing

The spacing scheme is based on the conservative form of the advection-diffusion equation  can be written as,

.. math:: \frac{\partial \Psi}{\partial t} + \nabla \cdot F (\Psi) = S
  
where :math:`\Psi` and :math:`F(\Psi)` represent the conserved variable and the sediment flux function, given by

.. math:: \Psi = \bar{c} H

and

.. math:: F = \bar{c} ({\bf M} ) - k H \nabla_h \bar{c}

The source term :math:`S = P-D`. :math:`\Psi` and :math:`S` are evaluated at the cell center as the major variables defined in FUNWAVE-TVD. :math:`k` is calculated at the cell faces as

.. math:: k_{i+1/2,j} = 5.93 \left( \frac{u_{*c i+1,j} + u_{*c i,j}}{2} \right)
 \left( \frac{H_{i+1,j} + H_{i,j}}{2} \right)

.. math:: k_{i-1/2,j} = 5.93 \left( \frac{u_{*c i-1,j} + u_{*c i,j}}{2} \right)
 \left( \frac{H_{i-1,j} + H_{i,j}}{2} \right)

The same algorithm is used for :math:`k` at (:math:`i,j+1/2`) and (:math:`i,j-1/2`) points. The shear velocity :math:`u_{*c}` is evaluated as

.. math:: u_{*c i,j} = \frac{k U_{c i,j}}{-1 + \ln (30H_{i,j}/k_s)}

:math:`U_{c i,j}` is the total velocity, 

.. math:: U_{c i,j}= \sqrt{U_{i,j}^2 + V_{i,j}^2}

in which (:math:`U_{i,j}, V_{i,j}`) are directly from the Boussinesq solution,

.. math:: U_{i,j} = U_{\alpha i,j} + U_{2 i,j}

.. math:: V_{i,j} = V_{\alpha i,j} + V_{2 i,j}

corresponding to the reference velocity :math:`{\bf u}_\alpha` and depth averaged velocity correction :math:`\bar{{\bf u}}_2` described in Shi et al. (2012). 

:math:`\nabla_h \bar{c}` is also evaluated at the cell face as

.. math:: \Delta_x \bar{c}_{i+1/2,j} = \frac{\bar{c}_{i+1,j} - \bar{c}_{i,j}}{\Delta x} 

.. math:: \Delta_x \bar{c}_{i-1/2,j} = \frac{\bar{c}_{i,j} - \bar{c}_{i-1,j}}{\Delta x} 

The same scheme is used for the :math:`y` direction. 

The source term in (\ref{psi}) includes the pickup rate :math:`P` and the deposition rate :math:`D`. :math:`P` is 
 calculated at the cell center using van Rijn's (1984) formula as mentioned above. Similarly, the deposition rate, :math:`D`, is calculated at the cell center based on Cao et al.'s  (1999) formula. 

* Time stepping

Time stepping is the same as in FUNWAVE-TVD solver.
The third-order Strong Stability-Preserving (SSP) Runge-Kutta scheme for nonlinear spatial discretization (Gottlieb et al., 2001) is adopted for time stepping. The scheme is given by

.. math:: {\Psi}^{(1)} = {\Psi}^{n}  + \Delta t (- \nabla \cdot F ({\Psi}^n) + {S}^{(1)} )  {\Psi}^{(2)} = \frac{3}{4}{\Psi}^{n}  + \frac{1}{4} \left[   {\Psi}^{(1)} +  \Delta t \left (- \nabla \cdot F ({\Psi}^{(1)} ) + {S}^{(2)} \right) \right]  {\Psi}^{n+1}

.. math:: = \frac{1}{3}{\Psi}^{n}  + \frac{2}{3} \left[   {\Psi}^{(2)} +  \Delta t \left (- \nabla \cdot F ({\Psi}^{(2)} ) + { S}^{n+1} \right) \right]

in which :math:`{\Psi}^{n}` denotes :math:`{\Psi}`  at time level :math:`n`.  :math:`{\Psi}^{(1)}` and :math:`{\Psi}^{(2)}` are values at intermediate stages in the Runge-Kutta integration. As :math:`{\Psi}` is obtained at each intermediate step,  the source term :math:`S` needs to be updates using the intermediate value of concentration.   

Time steps are the same as the Boussinesq solver, which uses adaptive values based on the Courant-Friedrichs-Lewy (CFL) criterion to ensure model stability. 

* Boundary conditions

Boundary conditions used in the sediment module have two types. One is the closed boundary condition which is applied at the cell face, for example, 

.. math:: F_{i+1/2,j} = 0 \hspace{1cm} 

The other is the open boundary condition with zero-gradient condition implemented at ghost cells. 

# INT--E--NSE
## Introduction
INT(E)NSE is (an intended pun and) acronym for IN-terpolated Two-D(E)-Navier-Stokes-Equations. This is an unsteady Navier-Stokes solver I developed during my free time. Interpolations for the face-velocities are done using a blended second-order and first-order accurate scheme to be able to capture the vortices. Pressure-velocity coupling is achieved using SIMPLE algorithm and the time-stepping is first order accurate following backward finite differencing discretization. I am looking for someone who can help me modularize this code and break it down into smaller files. Currently everything is organized using comments(!). Will soon be adding mesh-clustering for the wall and include the energy equation. If you are interested to upgrade/contribute to this solver either by:
1. Modularizing this code into smaller files to make it easy to perform bug-fixes
2. Extend to 3-D 
3. Higher-order interpolations
4. Higher-order time stepping schemes
5. Alternative pressure-velocity coupling schemes 
6. Add turbulence model 
7. Accelerate code performance using suitable paralellization 
Please contact me through mail/submit a pull request. Curerntly the code is written entirely in MATLAB. The test cases for which I have got results are shown below
# Why INTENSE
So the motive behind developing INTENSE is contained in its name-to grasp the concepts of CFD in the most intense way! Ok jokes apart, it is intended as a code to help people starting CFD to better understand what happens inside the black-box when they push a button in any commerical software.To better gain insights into the development of a CFD code. The entire code is thoroughly commented and includes relavant one-liner explanations wherever required. Now I know I could have done a better job using a Jupyter notebook, but I started out coding this as a hobby and before I knew it had over 300 lines! Plus this does away lesser memory. But with solver getting upgraded with new features like mesh-clustering, energy equation, and maybe turbulence, I might like extending this to a more generic CFD code written in MATLAB. However, the intent remains the same-INTENSE-ly understand CFD!
# How to use INTENSE
You can either use this for your direct simulation by tweaking the mesh-parameters and flow-variables in the beginning and hit run in MATLAB (which is highly unlikely as there are standard solvers out there that do a better job!) or you can use this to understand how CFD codes are built by going thru the code and the comments. I advise you to tweak some parameters in the code like the blending factor or the number of iterations for the various sub-solvers to understand the importance of each loop and their effect on the convergence. Oh yea, this has a residual monitor too. so that will show you if your results have converged.Comment or uncomment some lines and look at how they effect the solution. 
# Some geeky details 
INTENSE solves the unsteady version of the incompressible Navier stokes equations together with the continuity equation using the numerical Finite Volume Method (FVM). I have enabled three major problems as benchmarks/test cases. The first being the the standard fully-developed channel flow, the second a pressure-driven channel flow (with pressure boundary conditions) and the lid-driven cavity. The Semi-Implicit method for Pressure-Linked Equation (SIMPLE) is used to couple the pressure and velocity terms. The solver uses a staggered mesh with ghost-cells in the boundary and a blended first and second-order accurate interpolation scheme is used to obtain face-velocities on the staggered-mesh. Time-stepping is done using a first-order accurate finite difference scheme. In addition there's a provision to block cells out-giving us results for the flows around bluff bodies.   

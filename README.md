# EnKF_Analysis
EnKF analysis routines in Fortran 90.  Stochastic and SQRT formulations with subspace inversion. 

lib:     The EnKF analysis routines and a makefile for compiling a library libenkfanalysis.a
The analysis library contains the basic update algorithm using a variety of inversion
schemes. We currently include stochastic and SQRT formulation with different ways of computing the
inverse of (SS'+(N-1)R). Using ensemble subspace inversion with representation of R in terms of 
measurement perturbations provides for very efficient (linear in measurements) update computations
even with correlated measurement errors.  An efficient "exact inversion scheme" is also provided
for the case with diagonal R.  The library also contains support for multiplicative inflation
including an adaptive variant where the inflation factor is computed to minimize variance reduction
due to spurious correlations.

It is recommended that the analysis routine is called from the enkf routine located in the test
directory.  This routine includes support for distance based and adaptive localization, it scales
matrices for stable computations in the case with variables of varying magnitudes.


support: Some additional routines for defining a model state and reading/writing it to file.

test:    A test or example program used to verify the analysis scheme with different options.
These routines are used to verify some basic properties of the different analysis schemes as 
well as studying their numerical behaviour.

Installation: 
    cd lib; make
    cd test; make
    cd build; testEnKF


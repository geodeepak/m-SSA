# m-SSA
Multivariate Singular Spectrum Analysis
M-SSA tutorial with Python
This Python tutorial demonstrates step-by-step the multivariate singular spectrum analysis. The steps are almost identical to those of singular spectrum analysis.

Copyright (c) 2013-2016, Andreas Groth, University of California, Los Angeles.
All rights reserved. Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:
- Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
- - Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

Step 1
Set general Parameters
and import the time-series data 

M = 10     window length of SSA
N = len(data)   length of generated time series
T = 10     period length of sine function
stdnoise = 0.1  noise-to-signal ratio

Create time series X1
First of all, we generate one time series, a sine function
of length N and the same function to the power of 3, both
with observational white noise.

X1 = sin(2*pi*t/T);     % sine function



First 
Calculate covariance matrix C (Toeplitz approach) (cf. Vautard & Ghil)
Next, we calculate the covariance matrix. There are several numerical approaches to estimating C. Here, we calculate the covariance function with CORR and build C with the function TOEPLITZ.

Second 
Calculate covariance matrix (trajectory approach) (cf. Broomhead & King)
An alternative approach is to determine C directly from the scalar product of Y, the time-delayed embedding of X. Although this estimation of C does not give a Toeplitz structure, with the eigenvectors not being symmetric or antisymmetric, it ensures a positive semi-definite covariance matrix.


Choose covariance estimation

Calculate eigenvalues LAMBDA and eigenvectors RHO
In order to determine the eigenvalues and eigenvectors of C we use the function EIG. This function returns two matrices, the matrix RHO with eigenvectors arranged in columns, and the matrix LAMBDA with eigenvalues on the diagonal.


We further use two different approaches to determine the Principal components 

Calculate the principal components (PC)
The principal components are given as the scalar product between Y, the time-delayed embedding of X1 and X2, and the eigenvectors RHO.

Calculate reconstructed components RC
In order to determine the reconstructed components RC, we have to invert the projecting PC = Y*RHO; i.e. RC = Y*RHO*RHO'=PC*RHO'. Averaging along anti-diagonals gives the RCs for the original input X.

and finally 
Compare reconstruction and original time series
Note that the original time series X can be completely reconstructed by the sum of all reconstructed components RC (upper panels). The sine function (lower left panel) can be reconstructed with the first pair of RCs, where more components are required for the nonlinear oscillation (lower right panel).

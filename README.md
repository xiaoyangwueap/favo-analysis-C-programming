Software update of frequency-dependent AVO inversion toolbox.
Four programmes have been adapted from matlab code to C or C++ code which
can be run under Linux or Seismic Unix environment.
(1) ppcoef.cpp
This is a C++ program that uses the Chapman squirt-flow model (2002) to calculate
the frequency-dependent reflection coefficient at the interface of a two-layer model.
The upper layer is an isotropic medium, and the lower layer is an isotropic medium
saturated with fluid. Users can change the parameters to design their own rock
physics model. The input parameters are defined in the par_ppcoef.txt file. The 11
parameters are as follows:
Vp Vs rho Vp0 Vs0 f0 rho0 por0 cd0 tau f1
The parameters are separated by space. Vp, Vs, rho are the P-wave velocity, S-
wave velocity, and density of the upper medium. Vp0, Vs0, rho0 are the P-wave
velocity, S-wave velocity and density of the lower fluid-saturated medium at
frequency f0. por0 and cd0 The porosity and fracture density of the underlying
medium. tau is the time scale parameter. f1 is the frequency at which the reflection
coeﬃcient is to be calculated.
（2）Animod.cpp
This is a c++ program for calculating the frequency-dependent anisotropic moduli
of fluid-saturated media with mesoscale fractures using the rock physics model
developed by Mark Chapman (2003). This program calculates and outputs five
independent elastic moduli for specific fluid-saturated media with vertical
fractures. The input model parameters are defined in the par_animod.txt file. The 9
parameters are as follows,
Vp0 Vs0 r0 f0 por0 cd0 tau0 fd f1
Vp0, Vs0, r0 are the P-wave velocity, S-wave velocity and density of the fluid-
saturated medium at the initial frequency f0. por0 and cd0 are the porosity crack
density of the medium. tau0 is the time scale parameter. fd is the crack density. f1
is the frequency at which the elastic tensor to be calculated.
（3）Suspwv2d.c
This is a spectral decomposition program of 2D seismic data using the smooth
pseudo Wigner-Ville method. The program is developed under the CWP Seismic
Unix software package. Copy the 'spwv2d' file to the SU directory. Then make the
suspwv2d.c file and install the method into the SU system. The following
command is an example of calculating 20Hz equal frequency profile for data.sgy:
$ segyread tape=data.sgy verbose=1 endian=0 | segyclean >data.su
$ suspwv2d frout=20.0 <data.su>data20.su
（4）Sufavoinv.c
This function uses the smooth pseudo Wigner-Ville spectral decomposition
method to calculate the frequency-dependent AVO inversion attributes. Users
need to prepare the seismic amplitude data and its corresponding spectral
decomposition data of 5 diﬀerent frequencies, plus p-wave velocity. An example of
using this code is as follows:
$ sufavoinv inSD0=IL1605.su inSD1=IL1605_30Hz.su inSD2=IL1605_10Hz.su inSD3=
IL1605_20Hz.su inSD4=IL1605_40Hz.su inSD5= IL1605_50Hz.su inVP=IL1605_vp.dat >
data.su

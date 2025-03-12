## Galactic Data Challenges
The tools needed to complete the Galactic challenges are demonstrated in the [Crab spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/crab), [Crab imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/Crab/ScAttBinning), [GRB localization](https://github.com/cositools/cosipy/tree/main/docs/tutorials/ts_map), [Polarization (ASAD method)](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/polarization/ASAD_method.ipynb), and [511 spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/extended_source_fit) (for extended source analysis) notebooks.

**All challenges should use the same detector response file:** <br />
ResponseContinuum.o3.e100_10000.b10log.s10396905069491.m2284.filtered.nonsparse.binnedimaging.imagingresponse_nside8.area.h5.gz <br />
ResponseContinuum.o3.pol.e200_10000.b4.p12.s10396905069491.m441.filtered.nonsparse.binnedpolarization.11D_nside8.area.h5.gz (polarized sources) <br />
extended_source_response_continuum_merged.h5.gz (precomputed extended source response file) <br />

### Galactic diffuse continuum

**Data Files:** <br />
GalTotal_SA100_F98_3months_unbinned_data_filtered_with_SAAcut.fits.gz

**Input Models:**  <br />
The Galactic diffuse continuum emission is modeled using the v57 release of the GALPROP cosmic ray (CR) propagation and interstellar emissions framework [(Porter+22)](https://iopscience.iop.org/article/10.3847/1538-4365/ac80f6). GALPROP self-consistently calculates spectra and abundances of Galactic CR species and associated diffuse emissions (gamma rays, X-rays, and radio) in 2D and 3D. The v57 release includes a set of steady-state emission model examples that reproduce the latest CR data. There are six models in total, categorized according to the CR source and interstellar radioation field (ISRF) model used for the prediction. There are 3 CR source models (SA0, SA50, SA100) and two ISRF models (R12, F98). The CR source density models are based on the distribution of injected CR power, with SA0 describing an axisymmetric disk (following the radial distribution of pulsars), SA50 describing a 50/50% split of the injected CR luminosity between disk-like and spiral arms, and SA100 describing pure spiral arms. All models have the same exponential scale height of 200 pc. The two ISRF models employ different spatial densities for both the stars and the dust but produce intensities very similar to those of the data for near- to far-infrared wavelengths at the location of the solar system (see [Porter+17](https://iopscience.iop.org/article/10.3847/1538-4357/aa844d) and references therein). For the neutral gas distributions (atomic and molecular), a 3D model from [Johannesson+18](https://iopscience.iop.org/article/10.3847/1538-4357/aab26e) is employed. These GALPROP models include the total emission, which is dominated by inverse Compton radiation, but also has a small contribution from Bremsstrahlung towards the upper energy bound. As our representative case, for DC3 we simulate the SA100-F98 model. 

This is the first data challenge to include the Galactic diffuse continuum, and our corresponding goals this year are straight forward. Future data challenges will look more into the different model variations and key parameters. 

**Note that the Galactic diffuse continuum emission is also part of the standard background model for COSI, which will be employed for most analyses.**

**Goals:** <br />
1. Measure the spectrum of the Galactic diffuse continuum emission, extracting it from the rest of the background
2. Image the Galactic diffuse continuum emission in the COSI energy band
3. Characterize how the the Galactic diffuse continuum emission impacts the sensitivity for point sources in the Galactic plane
   
### Gamma-ray Binary PSR B1259-63

**Data Files:** <br /> 
PSRB1259_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
PSRB1259_10x_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

**Input Models:**  <br />
PSR B1259-63 is a binary gamma-ray system consisting of a radio pulsar and a massive Be-type star. The system has a highly eccentric orbit, with an orbital period of 3.4 years. Gamma-ray emission occurs during its periastron passage, as interactions between the outflows of the two objects trigger particle acceleration. The next periastron passage will be November 19th, 2027, making this a prime target for COSI. The model for DC3 is based on the work in [Abdo+11](https://doi.org/10.1088%2F2041-8205%2F736%2F1%2Fl11) (see model 1 in the bottom of Figure 5). For the DC3 simulations, the following features are assumed: 1) Constant emission for 30 days. 2) Two flux scenarios: the nominal value from Abdo+11, as well as a 10x enhanced flux. Note that in general the flux and duration vary for each periastron passage, and in COSI's energy band they are not well understood.

**Goals:** <br />
1. Measure MeV gamma-ray flux during the flare event.
2. Determine the duration of flare periods.

### GRS 1758-258

**Data Files:** <br />
GRS175_3months_unbinned_data_filtered_with_SAAcut.fits.gz

**Input Models:**  <br />
Best fit comptonization model of epoch2 of [Pottschmidt+06](https://arxiv.org/pdf/astro-ph/0509006.pdf).

**Goals:** <br />
1. A simple test of spectral measurement for this galactic center source.
   
### Cygnus X1
   
**Data Files:** <br />
cygX1_soft_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
cygX1_hard_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

**Input Models:**  <br />
The two spectral models for Cyg X1 are best fit eqpair  models of time averaged INTEGRAL data [Cangemi+21]( https://ui.adsabs.harvard.edu/abs/2021A%26A...650A..93C/abstract) given for hard and soft states respectively. Polarization is also included. The hard state model is based on the measurements of [Rodriguez+2015](https://ui.adsabs.harvard.edu/abs/2015ApJ...807...17R/abstract). At low energy (0.1 - 0.4 MeV) the polarization fraction is 5% with an angle of 40 degrees (IAU convention). At high energy (0.4 - 10 MeV) the polarization fraction is 75% with the same angle. The soft spectral state assumes an energy-independent polarization of 20% (same angle).  

**Goals:** <br />
1. Check detection sensitivty in soft state
2. Test how well COSI can monitor for spectral transitions

### 1E1740.7-2942
   
**Data Files:** <br />
1E1740_compow_3months_unbinned_data_filtered_with_SAAcut.fits.gz
1E1740_twocompt_3months_unbinned_data_filtered_with_SAAcut.fits.gz

**Input Models:**  <br />
The 2 spectral models for 1E1740.7-2942 (also know as great annihilator) are the best fit models
 of INTEGRAL data obtained by [Bouchet+09](https://iopscience.iop.org/article/10.1088/0004-637X/693/2/1871/pdf):
 - compow: thermal comptonization + power law
 - twocompt: two components of thermal comptonization with different temperatures
Both models represent the INTEGRAL data well but strongly differ at the highest energies. 

**Goals:** <br />
1. Test whether COSI would be able to distinguish between the two models.

### MAXI J1820+070 and MAXI J1348-630
   
**Data Files:** <br />
MAXI1820_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
MAXI1348_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

**Input Models:**  <br />
The spectral models for MAXI J1820+070 and MAXI J1348-630 are scans of published INTEGRAL data shown in Fig 3 of [Cangemi+23](https://ui.adsabs.harvard.edu/abs/2023A%26A...669A..65C/abstract), in the hard state. The polarimetric models corresponds to the measurements shown in table 3 of the same paper. The input polarization models are divided into a low energy component (0.1 - 0.4 MeV) and a high energy component (0.4 - 10 MeV). MAXIJ1820+070 and  MAXI J1348-630 remained in the hard state for 60 days and 7 days, respectively, and for DC3 we have the sources 'on' for these respective times and off for the rest of the time. 

**Goals:** <br />
1. Test COSI's ability to measure spectra and polarization of transient sources.

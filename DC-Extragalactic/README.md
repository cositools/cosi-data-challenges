## Extragalactic
The tools needed to complete the Extragalactic challenges are demonstrated in the [Crab spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/crab) and [Polarization (ASAD method)](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/polarization/ASAD_method.ipynb) notebooks.

**All challenges should use the same detector response file:** <br />
ResponseContinuum.o3.e100_10000.b10log.s10396905069491.m2284.filtered.nonsparse.binnedimaging.imagingresponse_nside8.area.h5.gz <br />
ResponseContinuum.o3.pol.e200_10000.b4.p12.s10396905069491.m441.filtered.nonsparse.binnedpolarization.11D_nside8.area.h5.gz (polarized sources) <br />
extended_source_response_continuum_merged.h5.gz (precomputed extended source response)  <br />

### NGC 1068
⚠️ Internal ToDo (Lea):
1. Proofread/check content
2. Provide links to cited papers

**Data Files:** <br /> 
NGC_1068_3months_unbinned_data_filtered_with_SAAcut.fits.gz

**Input Models:**  <br />
The baseline model is a powerlaw with exponential cut-off from Bauer+2015: <br />
Gamma=1.92, Ecut=200 keV; intrinsic flux 2-10 keV = 8.9e-10 erg/cm2/s

**Goals:** <br />
1. Determine flux in the COSI band, and coronal cut-off energy

### NGC 4151
⚠️ Internal ToDo (Lea):
1. Proofread/check content
2. Provide links to cited papers

**Data Files:** <br />
NGC_4151_bright_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
NGC_4151_EC200_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
NGC_4151_EC1000_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
NGC_4151_faint_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

**Input Models:**  <br />
The baseline model is a powerlaw with exponential cut-off. <br />

flux in the 20-30 keV calibrated from NuSTAR observations: <br />
NGC_4151_ec200: Gamma=1.75, Ecut=200 keV <br />
NGC_4151_ec1000: Gamma=1.75, Ecut=1000 keV <br />

flux calibrated from INTEGRAL observation of Lubinski+2010: <br />
NGC_4151_bright: Gamma=1.71, Ecut=264 keV <br />
NGC_4151_faint: Gamma=1.81, Ecut=1000 keV <br />

**Goals:** <br />
1. Determine flux in the COSI band, and coronal cut-off energy <br />

### 4C+21.35
⚠️ Internal ToDo (Michela):
1. Give gaol of challenge
2. Provide description of model
3. Proofread/check content

**Data Files:** <br />
4C21p35_noflare_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
4C21p35_flare_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

**Input Models:**  <br />
We present a lightcurve showing 2 states: a flaring state and a quiescent state. The Flaring state is defined every time in which the average flux is 3 times greater than the 16-years average flux (given by Fermi).

The two states come with two different spectra: both powerlaws with different indices:
1. noflare = 1.6
2. flare = 2.5

The normalization is derived from the integrated flux in COSI energy band derived from the extrapolation of the Fermi-LAT log parabola function. 

**Goals:** <br />
1. What are the goals of this challenge? <br />

### 3C 279

**Data Files:** <br />
3C279_3months_unbinned_data_filtered_with_SAAcut.fits.gz

**Input Models:**  <br />
The spectral data is for 3C 279 high, which represent the high state of the source, and the flux is increased by 100x its nominal value. The source is polarized with a polarization fraction of 19.62%, and a randomly chosen polarization angle of 45 degrees (in IAU convention). 

**Goals:** <br />
1. Measure the polarization fraction and angle.

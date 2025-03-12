## Nucleosynthesis Data Challenges
The tools needed to complete these challenges are demonstrated in the [511 imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/511keV/ScAttBinning) and [511 spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/extended_source_fit) notebooks. 

### Al26 Cygnus Region
   
**Data Files:** <br /> 
Response26Al.o4.e1805_1812.s10036231691364.m1045.filtered.nonsparse.binnedimaging.imagingresponse_nside16.area.h5.gz <br />
extended_source_response_Al26_merged.h5.gz (precomputed extended source response file) <br />
26Al_Cyg_Region_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

**Input Models:**  <br />
The characteristics of the emission were obtained from the analyses of INTEGRAL/SPI observations
described in [Martin+09](https://ui.adsabs.harvard.edu/abs/2009A%26A...506..703M/abstract). The source is modeled with a $3^\circ$ width (standard deviation) Gaussian shape emission centered
at $l = 81^\circ, b = 1^\circ$. The line flux is $3.9 \times 10^{-5} \ \mathrm{ph \ cm^{-2} \ s^{-1}}$. It is centered at 1808.8 keV and its width is 1.6 keV (FWHM)
due to the interstellar turbulence.

**Goals:** <br />
1. Make detection taking into account the Galactic diffuse continuum background at 1809 keV emission
2. Measure width of the gamma-ray line
3. Recover 60Fe/26Al ratio (see 60Fe_Cyg_Region)

### Al26 NE2001

**Data Files:** <br /> 
Response26Al.o4.e1805_1812.s10036231691364.m1045.filtered.nonsparse.binnedimaging.imagingresponse_nside16.area.h5.gz <br />
extended_source_response_Al26_merged.h5.gz (precomputed extended source response file) <br />
26Al_NE2001_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

**Input Models:**  <br />
This is the description of the model of the 1809 keV line diffuse emission due decay of 26Al in our Galaxy. The spatial distribution is derived from the model NE2001 of [Cordes & Lazio 2002](https://arxiv.org/abs/astro-ph/0207156) that fits
the distribution of massive stars in our Galaxy. The fraction of 26Al in the bulge is 2%. This value is a compromise between SPI observations and results of studies of star formation rate in this region.
The shape of the line in each spatial bin takes into account the turbulence of the interstellar medium and the Galactic rotation using the model of [Fich, Blitz and Stark 1989](https://ui.adsabs.harvard.edu/abs/1989ApJ...342..272F/abstract) for R > 3 kpc and a solid rotation model for R < 3 kpc.

**Goals:** <br />
1. Detection of the diffuse emission
2. Detection of the Doppler shift in the disk
3. Detection of the spectral shape
4. Correlation with the emission of the Galactic positron annihilations
5. Extract F(26Al)/F(60Fe) ratio and its uncertainty
   
### Ti44
The tools needed to complete these challenges are demonstrated in the [Crab spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/crab) and [GRB localization](https://github.com/cositools/cosipy/tree/main/docs/tutorials/ts_map) notebooks.
   
**Data Files:** <br /> 
Response44Ti.o4.e1154_1160.s9607532021290.m1215.filtered.nonsparse.binnedimaging.imagingresponse_nside16.area.h5.gz <br />
extended_source_response_Ti44_merged.h5.gz (precomputed extended source response) <br />
CasApartiallyresolved_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
CasAfullyresolved_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
CasAG16distribution_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
CasAunresolved_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
CasAsymmetric_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

**Input Models:**  <br />
In all 4 scenarios, bulk center of motion is at rest. Doppler broadening is limited to 1000 km/s, as otherwise, when combined with the Doppler shifts of clumps, the signal will fall quite outside the DC2 simulated response region of 1143-1171 keV.

In asymmetric scenarios, Clump 1: Contains 2/3 of total 44Ti yield Doppler shifted towards from the observer (blueshifted). Has peak energy higher than 1157 keV. Clump 2: Contains 1/3 of total 44Ti yield Doppler shifted away from the observer (redshifted). Has peak energy lower than 1157 keV.

All spectra follow simple Gaussian distributions. The flux is taken as the value between $2.1 \times 10^{-5} \ \mathrm{ph \ cm^{-2} \ s^{-1}}$ in Grefenstette et al 2015 and $3.5 \times 10^{-5} \ \mathrm{ph \ cm^{-2} \ s^{-1}}$  in Siegert et al 2015.

**Goals:** <br />
1. What are the goals?

### Fe60 Cygnus Region

**Data Files:** <br /> 
Response60FeHigh.o4.e1329_1336.s10201526728102.m1287.filtered.nonsparse.binnedimaging.imagingresponse_nside16.area.h5.gz <br /> 
Response60FeLow.o4.e1170_1176.s9552269354945.m1188.filtered.nonsparse.binnedimaging.imagingresponse_nside16.area.h5.gz <br /> 
extended_source_response_Fe60_low_merged.h5.gz (precomputed extended source response) <br />
extended_source_response_Fe60_high_merged.h5.gz (precomputed extended source response) <br />
60Fe_Cyg_Region_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br /> 

**Input Models:**  <br />
The flux of the 60Fe lines is derived from the calculation of [Martin+10](https://ui.adsabs.harvard.edu/abs/2010A%26A...511A..86M/abstract). The spatial extent of this diffuse emission is the same as the one of the 1809 keV line emission that were obtained from the analyses of SPI/INTEGRAL observations
described in [Martin+09](https://ui.adsabs.harvard.edu/abs/2009A%26A...506..703M/abstract). The source is modeled with a 3deg width (standard deviation) Gaussian shape emission centered at $l = 81^\circ, b = 1^\circ$. The line fluxes are $2.7 \times 10^{-6} \ \mathrm{ph \ cm^{-2} \ s^{-1}}$ for the both line. The line energies are 1173.3 keV and 1332.6 keV and their width are 1.04 keV and 1.18 keV (FWHM), respectively (broadening due to the interstellar turbulence).

**Goals:** <br />
1. Make detection taking into account the Galactic diffuse continuum background at 1173 keV and 1332 keV
2. Measure width of the gamma-ray line
3. Recover 60Fe/26Al ratio (see 26Al_Cyg_Region)

 ### Fe60 NE2001

**Data Files:** <br /> 
Response60FeHigh.o4.e1329_1336.s10201526728102.m1287.filtered.nonsparse.binnedimaging.imagingresponse_nside16.area.h5.gz <br /> 
Response60FeLow.o4.e1170_1176.s9552269354945.m1188.filtered.nonsparse.binnedimaging.imagingresponse_nside16.area.h5.gz <br /> 
extended_source_response_Fe60_low_merged.h5.gz (precomputed extended source response) <br />
extended_source_response_Fe60_high_merged.h5.gz (precomputed extended source response) <br />
60Fe_NE2001_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

**Input Models:**  <br />
This is the description of the model of the diffuse emission of the 1173 keV and 1332 keV lines due decay of 60Fe in our Galaxy. The spatial distribution is derived from the model NE2001 of [Cordes & Lazio 2002](https://arxiv.org/abs/astro-ph/0207156) that fits the distribution of massive stars in our Galaxy. The fraction of 60Fe in the bulge is 2%. This value is the same as the one of the 26Al, which is a compromise between SPI observations and results of studies of star formation rate in this region. The flux is computed assuming a total mass of 60Fe of 3.5 M_sol in our Galaxy (see [Wang+20](https://ui.adsabs.harvard.edu/abs/2020ApJ...889..169W/abstract) and [Siegert+23](https://ui.adsabs.harvard.edu/abs/2023A%26A...672A..54S/abstract)). The shape of the line in each spatial bin takes into account the turbulence of the interstellar medium and the Galactic rotation using the model of [Fich, Blitz and Stark 1989](https://ui.adsabs.harvard.edu/abs/1989ApJ...342..272F/abstract) for R > 3 kpc and a solid rotation model for R < 3 kpc.

**Goals:** <br />
1. Detection of the diffuse emission.
2. Extraction of the F(26Al)/F(60Fe) ratio and its uncertainty.

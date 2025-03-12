## Positrons
The tools needed to complete these challenges are demonstrated in the [511 imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/511keV/ScAttBinning) and [511 spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/extended_source_fit) notebooks. 

**All challenges should use the same detector response files:** 
Response511.o4.e509_513.s20881894470591.m2555.filtered.nonsparse.binnedimaging.imagingresponse_nside16.area.h5.gz <br />
ResponseContinuum.o3.e100_10000.b10log.s10396905069491.m2284.filtered.nonsparse.binnedimaging.imagingresponse_nside8.area.h5.gz <br />
extended_source_response_511_merged.h5.gz (precomputed 511 extended source response file)
extended_source_response_continuum_merged.h5.gz (precomputed continuum extended source response file)

The line response is for analyzing the 511 keV line emission, and the continuum response is for analyzing the orthopositronium continuum. Currently, these two components cannot be analyzed simultaneously, as desribed in the [Known Caveats and Limitations](#known-caveats-and-limitations) section. 

### Extragalactic Sources (LMC, M31, Virgo)

**Data Files:** <br />
LMC_Gaussian_511_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
LMC_Gaussian_511_x100_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
M31_Gaussian_511_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
M31_Gaussian_511_x100_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
Virgo_Gaussian_511_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br /> 
Virgo_Gaussian_511_x100_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

**Input Models:**  <br />
Fluxes are estimated by assuming that the 511 keV photon flux is proportional to the stellar mass of a source. Using a Milky Way 511 keV flux of $2.8 \times 10^{-3} \  \mathrm{ph \ cm^{-2} \ s^{-1}}$ ([Siegert+16](https://www.aanda.org/articles/aa/full_html/2016/02/aa27510-15/aa27510-15.html)) and total stellar mass of $5.4 \times 10^{10} \  M_\odot$ ([McMillan+16](https://academic.oup.com/mnras/article/465/1/76/2417479)), we scale the 511 keV flux of each extragalactic source based on the 511 keV flux assumed to be associated with the stellar mass in the Milky Way.

The stellar masses are: <br />
LMC: $1 \times 10^{10} \ M_\odot\$ ([Erkal+19](https://academic.oup.com/mnras/article/487/2/2685/5491315)) <br />
M31: $1.25 \times 10^{11} \ M_\odot\$ ([Tamm+12](https://www.aanda.org/articles/aa/full_html/2012/10/aa20065-12/aa20065-12.html)) <br />
Virgo: $1.2 \times 10^{14} \ M_\odot\$ ([Fouque+01](https://www.aanda.org/articles/aa/abs/2001/33/aa1326/aa1326.html)) <br />

We also include each source at 100x the nominal flux, in order to ensure that they are above COSI's 511 keV line sensitivity.

**Goals:**
1. Determine COSI's sensitivity for detecting these potential extragalactic 511 keV sources. 

### Globular Clusters (Tuc 47, Omega_Cen, NGC 6121, NGC_6397)

**Data Files:** <br />
Globular_Cluster_Tuc_47_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
Globular_Cluster_Omega_Cen_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
Globular_Cluster_NGC_6397_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
Globular_Cluster_NGC_6121_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

**Input Models:**  <br />
The 511 keV photon flux for the brightest 4 globular clusters is presented here. The flux is estimated based on the 0.1 - 100 GeV luminosity from the Globular clusters, nuclear bulge emission, and boxy bulge emission in the Milky Way [Bartels et al 2018a](https://ui.adsabs.harvard.edu/abs/2018NatAs...2..819B/abstract). The GeV luminosity of the Bulge is compared to the 511 keV luminosity of the bulge [Bartels et al 2018b](https://ui.adsabs.harvard.edu/abs/2018MNRAS.480.3826B/abstract). This GeV luminosity vs 511 keV luminosity correlation is applied to the GeV excess observed from globular clusters [Zhang et al 2016](https://ui.adsabs.harvard.edu/abs/2016MNRAS.459...99Z/abstract) in the Galaxy to estimate the 511 keV flux of the globular clusters. The flux values shown here are 3x the values estimated from the correlation in order to make them within COSI's sensitivity limit.

**Goals:** <br />
1. Determine COSI's sensitivity for detecting 511 keV emission from Globular clusters.

### Positrons from 26Al
⚠️ Internal ToDo (Pierre):
1. Proofread/check content

**Data Files:** <br />
Positrons_from_26Al_line_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
Positrons_from_26Al_cont_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

**Input Models:**  <br />
This is the description of the model of the diffuse emission due to the steady state annihilation of positrons produced by 26Al decay in our Galaxy. The spatial distribution is derived from the calculation of the propagation of positrons in our Galaxy. The initial positions of positrons follow the model NE2001 of [Cordes & Lazio 2002](https://arxiv.org/abs/astro-ph/0207156) that fits the distribution of massive stars in our Galaxy, with a fraction of 26Al in the bulge of 2%. The positron propagation method is described in [Alexis et al. 2014](https://ui.adsabs.harvard.edu/abs/2014A%26A...564A.108A/abstract). The spectral distribution takes into account the annihilation line and the orthopositronium continuum. It was obtained from the model of [Guessoum et al 2005](https://ui.adsabs.harvard.edu/abs/2005A%26A...436..171G/abstract) that compute a spectrum for each phase of the interstellar medium. The spectral model was corrected by the Galactic rotation using the model of [Fich, Blitz and Stark 1989](https://ui.adsabs.harvard.edu/abs/1989ApJ...342..272F/abstract) for R > 3 kpc and a solid rotation model for R < 3 kpc.

**Goals:** <br />
1. Detection of the diffuse line and continuum emissions
2. Detection of the Doppler shift in the disk
3. Detection of the spectral shape
4. Correlation with the 26Al map (1809 keV emission)

### Positrons from 44Ti
⚠️ Internal ToDo (Pierre):
1. Proofread/check content

**Data Files:** <br />
Positrons_from_44Ti_line_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
Positrons_from_44Ti_cont_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

**Input Models:**  <br />
This is the description of the model of the diffuse emission due to the steady state annihilation of positrons produced by 44Ti decay in our Galaxy. The spatial distribution is derived from the calculation of the propagation of positrons in our Galaxy. The initial positions of positrons follow the model NE2001 of [Cordes & Lazio 2002](https://arxiv.org/abs/astro-ph/0207156) that fits the distribution of massive stars in our Galaxy, with a fraction of 44Ti in the bulge of 2%, which corresponds to the fraction of massive stars also used for the 26Al. The positron propagation method is described in [Alexis et al. 2014](https://ui.adsabs.harvard.edu/abs/2014A%26A...564A.108A/abstract). The positron rate due to 44Ti decay is $\sim 3 \times 10^{42}$ e+/s (see section 2.3 of Alexis et al. 2014).
The spectral distribution takes into account the annihilation line and the orthopositronium continuum. It was obtained from the model of [Guessoum et al 2005](https://ui.adsabs.harvard.edu/abs/2005A%26A...436..171G/abstract) that compute a spectrum for each phase of the interstellar medium. The spectral model was corrected by the Galactic rotation using the model of [Fich, Blitz and Stark 1989](https://ui.adsabs.harvard.edu/abs/1989ApJ...342..272F/abstract) for R > 3 kpc and a solid rotation model for R < 3 kpc.

**Goals:** <br />
1. Detection of the diffuse line and continuum emissions
2. Detection of the Doppler shift in the disk
3. Detection of the spectral shape

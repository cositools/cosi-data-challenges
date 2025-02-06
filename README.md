<div align="center">
  
# Welcome to COSI Data Challenge 3!

<p align="center">
<img width="325"  src="static/logo.png">
</p>

<div align="left">

## Table of Contents

- [Introduction](#introduction)
- [Getting Started](#getting-started)
- [System Requirements](#system-requirements)
- [Getting Help](#getting-help)
- [Backgrounds](#backgrounds)
- [Earth Occultation](#earth-occultation)
- [Polarization](#polarization)
- [Releases](#releases)
- [Computing Resources](#computing-resources)
- [Simulation Tools](#simulation-tools)
- [Summary of Current and Past Challenges](#summary-of-current-and-past-challenges)
- [Useful Reference Guides](#useful-reference-guides)
- [Data Challenges](#data-challenges)
  - [GRBs](#grbs)
  - [Positrons](#positrons)
  - [Nucleosynthesis](#nucleosynthesis)
  - [Galactic](#galactic)
  - [Extragalactic](#extragalactic)
  - [Dark Matter](#dark-matter)
  - [Extra Challenges](#extra-challenges)
- [Known Caveats](#known-caveats)
- [Citing](#citing)

## Introduction
Welcome to the third COSI data challenge (DC3)! The COSI data challenges are released on a yearly basis in preparation for the launch of the COSI Small Explorer (SMEX) class mission in 2027 ([Tomsick+23](https://ui.adsabs.harvard.edu/abs/2023arXiv230812362T/abstract)). They are based on simulated data, which is intended to closely mimic the real flight data. Every year the data challenges have increasingly more realistic source and background models, and they are analyzed with increasingly complete and matured analysis tools. In general there are two main goals of the data challenges:

1. Facilitate development of the COSI data pipeline and analysis tools.
   - With routine feedback from scientists. 
   - Alongside development of the expected source models by the science team. 
2. Provide resources to the astrophysics community to become familiar with COSI data.
   - Excellent training for science team in preparation for first analyses after launch.
   - Public releases help with community building before COSI data is released. 

## Getting Started 
The only software requirement for DC3 is [cosipy](https://github.com/cositools/cosipy). A general introduction into cosipy, including installation instructions, can be found in the [cosipy-intro](cosipy-intro) directory. For a general introduction into analyzing data from Compton telescopes see [Compton-telescope-data-analysis-intro](Compton-telescope-data-analysis-intro). Note that cosipy is part of the larger COSITools, which is a broad collection of COSI data analysis tools, documentation, and verification data sets. COSITools can be installed by following the installation instructions [here](https://github.com/cositools/cosi-setup). This also includes MEGAlib, which is the main software program used for running simulations. However, unless you need MEGAlib and/or COSITools for other reasons, it's highly recommended to just install cosipy.    

This year's data challenge is based on 3 months of exposure time, for an equatorial orbit at an altitude of 530 km, with a pointing that rocks between $\pm 20^\circ$ from the Earth zenith. The simulated data products are provided in fits file format, and are hosted on wasabi. Details of the simulations, simulated data, and information for accessing the data products can be found in the [data-products](data-products) directory. 

The input models and challenges for DC3 were provided by the COSI science teams. There are challenges for the different science groups: GRBs, Positrons, Nucleosynthesis, Galactic, Extragalactic, Solar, and Dark Matter. These are described in detail in the [Data Challenges](#data-challenges) section below.  

In summary, to get started with DC3, install cosipy, familiarize yourself with the [data-products](data-products), and then start working through the [Data Challenges](#data-challenges), as described below. 

## System Requirements
One of our goals in developing cosipy is to make it easily accesible to all users. **All of the data challenges starting with DC2 should be doable on a laptop with at least 16 GB of RAM**. We are still working on optimizing the code, and so please let us know if you are running into memory issues.

## Getting Help
Please submit a new issue in the [cosipy](https://github.com/cositools/cosipy) git repository if you have issues with the code. If you have general feedback, or need further assistance, please reach out to the COSI Data Challenge team lead, Chris Karwin ([christopher.m.karwin@nasa.gov](mailto:christopher.m.karwin@nasa.gov)), the cosipy implementation lead, Israel Martinez-Castellanos ([israel.martinezcastellanos@nasa.gov](israel.martinezcastellanos@nasa.gov)), and the pipeline development lead Carolyn Kierans ([carolyn.a.kierans@nasa.gov](carolyn.a.kierans@nasa.gov)).

## Backgrounds
In general, observations in the MeV band are hindered by high backgrounds (both instrumental and astrophysical). In order to ensure that COSI accomplishes its main science goals, it is therefore crucial to have a firm understanding of these backgrounds. DC3 includes all of the background components. Compared to the background estimates from DC2, we have now included the full SAA passage, as well as the Galacic diffuse continuum emission. Further details can be found in the [backgrounds](backgrounds) directory. 

For analyzing data in DC3, the starting point is to model the backgrounds using the actual injected backgrounds themselves. This is the ideal case, where the backgrounds are perfectly known, which of course is not very realistic. The next step is to estimate the backgrounds. **With DC3 we have new methods to estimate the background for both line and continuum sources**. The background estimation tool for line emission can be used for both point sources and extended sources. An example tutorial can be found in the [line background estimation](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/background_estimation/line_background/line_background_estimation_example_notebook.ipynb) notebook. The background estimation tool for continuum emission is currently only available for point sources. An example tutorial is available in the [continuum background estimation](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/background_estimation/continuum_estimation/BG_estimation_example.ipynb) notebook. We stress that both of these background estimation algorithms are first versions, and further development and testing is still needed. More details are provided in the respective example tutorials. 

The available background files are listed in the [data-products](data-products) directory. We provide a file with the total background, as well as separate files for the individual background components (as details in the [backgrounds](backgrounds) directory). 

## Earth Occultation
The Earth blocks a significant portion of the sky for satellites in low-Earth orbit, referred to as Earth occultation. It is important to account for this when simulating observations and performing data analysis. In order to implement this for the DC3 simulations we added new functionality to MEGAlib (*develop-cosi* branch), as detailed in the [earth-occultation](earth-occultation) directory. **These new methods now allow for simulating instruments with non-zenith pointings.** We also added new methods in cosipy to account for Earth occultation in the data analysis. 

## Polarization

## Releases

- Data challenge 1, March 2023: [cosi-data-challenge-1](https://github.com/cositools/cosi-data-challenge-1)
- Data challenge 2, March 2024: [cosi-data-challenge-2](https://github.com/cositools/cosi-data-challenges/tree/data_challenge_2.0)
- Data challenge 3, April 2025: **cosi-data-challenge-3 (latest release)**
- Data challenge 4: Planned for March 2026
- Data challenge 5: Planned for March 2027 (final challenge before launch :rocket:!)

## Computing Resources
<div align="center">
<img width="1050"  src="static/clusters.png">
<div align="left">
  
The simulations for the COSI data challenges are ran on high performance computing clusters. Most notably, we have made extensive use of NASA's [Discover cluster](https://www.nccs.nasa.gov/systems/discover), the [MOGON](https://mogonwiki.zdv.uni-mainz.de/docs/introduction/what_is_mogon) cluster in Mainz, and Clemson University's [Palmetto](https://docs.rcd.clemson.edu/palmetto/) cluster. 

## Simulation Tools
The simulations employ [MEGAlib](https://github.com/zoglauer/megalib) via the Python-based COSI simulation pipepline, [cosi-sim](https://github.com/cositools/cosi-sim). Details regarding the specific MEGAlib versions and configuration files can be found in each respective data challenge directory. Model inputs for the simulations and the corresponding data challenges come from the COSI science team. All of the models used for past data challenges can be found in the source library of the cosi-sim tools ([link](https://github.com/cositools/cosi-sim/tree/main/cosi_sim/Source_Library)).   

## Summary of Current and Past Challenges 
- **[Data Challenge 1](https://github.com/cositools/cosi-data-challenge-1):**
  - Focused on the 2016 COSI Balloon flight.
  - Release includes real flight data for the Crab.
  - Main goal is to learn the fundamentals of analyzing Compton data with COSI.
  - The analysis tools used for DC1 are only preliminary (referred to as cosipy classic).
    - Developed by Thomas Siegert for analysis of the 2016 balloon data. 
  - Contains 3 straightforward examples of COSI’s science goals:
    - Extracting energy spectra from the Crab, Cen A, Cygnus X-1, and Vela.
    - Imaging bright point sources, such as the Crab and Cygnus X-1.
    - Imaging diffuse emission from the positron-electron annihilation 511 keV and Al-26 1.8 MeV gamma-ray lines.
- **[Data Challenge 2](https://github.com/cositools/cosi-data-challenges/tree/data_challenge_2.0):**
  - Focused on COSI SMEX mission.
  - First (alpha) release of cosipy. 
  - Data challenges for all the main science groups (none for dark matter and solar).
  - All models and challenges provided by respective COSI science teams.
  - Uses 3 months of observations, for an equatorial orbit at 550 km, with a zenith pointing. 
  - All BG components are included, except for SAA passage (i.e. trapped cosmic rays).
    - BG also includes time variability from changing geomagnetic cutoff.
  - We simulated 12 background components, and 30 unique sources, running 49 different source simulations in total (using multiple models for some of the sources).
  - Contains 7 main tutorials demonstrating all the tools/methods needed for completing the challenges, included as part of the cosipy release:
    - dataIO
    - GRB localization
    - GRB spectral fit
    - Crab spectral fit
    - 511 spectral fit
    - Crab imaging
    - 511 imaging
- **Data Challenge 3**
  - Focused on COSI SMEX mission.
  - Data challenges for all the main science groups (including dark matter and solar), covering all of COSI's primary science objectives. 
  - All models and challenges provided by respective COSI science teams.
  - Used 3 months of observations, for an equatorial orbit at 530 km.
  - Simulations include rocking of instrument:
    - Pointing changes between +/- 22 degrees every 12 hrs, with 8 minute transition time. 
  - Used detailed COSI SMEX mass model.
  - Simulated all background components in low-Earth orbit, including variability from geomagnetic cutoff, long-term buildup, and full SAA passage.
    - Background includes the Galactic diffuse continuum for the first time. 
  - New methods in both MEGAlib and cosipy to account for Earth occultation with a non-zenith pointing. 
  - First time including polarization.
  - Numerous improvements to cosipy:
    - First version of source injector.
    - New implementation of Earth occultation in detector response.
    - First polarization tools.
    - New methods to estimate the background for continuum sources, line sources, and transient sources.
    - Refinements and further developments of imaging class.
    - New Extended source response class.
## Useful Reference Guides
- **[Introduction to Compton telescope data analysis](Compton-telescope-data-analysis-intro)**
- **[Introduction to cosipy](cosipy-intro)** 
- **[Summary of background simulations](backgrounds)**
- **[Dealing with Earth Occultation](earth-occultation)** 
- **[Introduction to Polarization](polarization)** 

## Data Challenges
We have created example jupyter notebooks demonstrating all of the tools that will be needed to complete this year's data challenges. They are available as part of the cosipy release, and listed below: <br /> 

Example 1: [dataIO](https://github.com/cositools/cosipy/tree/main/docs/tutorials/DataIO) <br />
Example 2: [GRB localization](https://github.com/cositools/cosipy/tree/main/docs/tutorials/ts_map) <br />
Example 3: [GRB spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/grb) <br />
Example 4: [Crab spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/crab) <br />
Example 5: [511 spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/extended_source_fit) <br />
Example 6: [Crab imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/Crab/ScAttBinning) <br />
Example 7: [511 imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/511keV/ScAttBinning) <br />

If you haven't worked with Jupyter before, you can find some help [here](https://github.com/cositools/cosi-data-challenge-2/tree/main/cosipy-intro/notebook_help.md)

As a very first step, try working through some of the example notebooks. Specific challenges for the different science topics are described below. You can start with whichever topic you are most interested in. Each challenge will refer you to a specific example notebook that will demonstrate the basic tools needed to complete the respective challenge. If you have completed the main challenges and are interested in further challenges, see the **Extra Challenges** section at the bottom of this page. 

All input models used for the simulations can be found in the DC2 source library of the COSI simulation pipeline, available [here](https://github.com/cositools/cosi-data-challenges/tree/main/cosi_dc/Source_Library/DC2/sources). This includes all the information about the injected sources, and it can be used for checking the results of the data challenges. 

**Orientation and Background Files:** <br />
All challenges use the same files: <br />
orientation file:  <br />
background file: 

## GRBs
 The tools needed to complete these challenges are demonstrated in the [GRB spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/grb) and [GRB localization](https://github.com/cositools/cosipy/tree/main/docs/tutorials/ts_map) examples. 

The burst time for each GRB is specified with the data file. This is the minimum information needed to complete the challenges.   

**Data Files:** <br />


**Input Models:** <br />


**Goals:**


## Positrons
The tools needed to complete these challenges are demonstrated in the [511 imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/511keV/ScAttBinning) and [511 spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/extended_source_fit) notebooks. 

**All challenges should use the same detector response file:** 
Response511.o4.e509_513.s2923345515139.nonsparse.binnedimaging.imagingresponse.rsp.gz

### Extragalactic Sources (LMC, M31, Virgo)
Internal ToDo (Sophie):
1. Proofread/check content
2. Provide links to cited papers

**Data Files:** <br />
LMC_Gaussian_511_3months_unbinned_data.fits.gz <br />
LMC_Gaussian_511_x100_3months_unbinned_data.fits.gz <br />
M31_Gaussian_511_3months_unbinned_data.fits.gz <br />
M31_Gaussian_511_x100_3months_unbinned_data.fits.gz <br />
Virgo_Gaussian_511_3months_unbinned_data.fits.gz <br /> 
Virgo_Gaussian_511_x100_3months_unbinned_data.fits.gz <br />

**Input Models:**  <br />
Fluxes are estimated by assuming that the 511 keV photon flux is proportional to the stellar mass of a source. Using a Milky Way 511 keV flux of $2.8 \times 10^{-3} \  \mathrm{ph \ cm^{-2} \ s^{-1}}$ (Siegert et al 2016) and total stellar mass of $5.4 \times 10^{10} \  M_\odot$ (McMillan et al 2016), we scale the 511 keV flux of each extragalactic source based on the 511 keV flux assumed to be associated with the stellar mass in the Milky Way.

The stellar masses are: <br />
LMC: $1 \times 10^{10} \ M_\odot\$ (Erkal et al 2019) <br />
M31: $1.25 \times 10^{11} \ M_\odot\$ (Tamm et al 2012) <br />
Virgo: $1.2 \times 10^{14} \ M_\odot\$ (Fouque et al 2001) <br />

We also include each source at 100x the nominal flux, in order to ensure that they are above COSI's 511 keV line sensitivity.

**Goals:**
1. Determine COSI's sensitivity for detecting these potential extragalactic 511 keV sources. 

### Globular Clusters (Tuc 47, Omega_Cen, NGC 6121, NGC_6397)
Internal ToDo (Saurabh):
1. Clarify and provide a bit more information regarding how the 511 flux was estimated. 
2. Proofread/check content
3. Provide links to cited papers

**Data Files:** <br />
Globular_Cluster_Tuc_47_3months_unbinned_data.fits.gz <br />
Globular_Cluster_Omega_Cen_3months_unbinned_data.fits.gz <br />
Globular_Cluster_NGC_6397_3months_unbinned_data.fits.gz <br />
Globular_Cluster_NGC_6121_3months_unbinned_data.fits.gz <br />

**Input Models:**  <br />
The 511 keV photon flux for the brightest 4 globular clusters is presented here. The flux is estimated based on the 0.1 - 100 GeV luminosity from the Globular clusters, nuclear bulge emission, and boxy bulge emission in the Milky Way (Bartels+2017). The GeV luminosity of the Bulge is compared to the 511 keV luminosity of the bulge to estimate the 511 keV flux of the globular clusters. The flux values shown here are 3x the values estimated from the correlation in order to make them within COSI's sensitivity limit.

**Goals:** <br />
1. Determine COSI's sensitivity for detecting 511 keV emission from Globular clusters.

### Positrons from 26Al
Internal ToDo (Pierre):
1. Proofread/check content

**Data Files:** <br />
Positrons_from_26Al_line_3months_unbinned_data.fits.gz <br />
Positrons_from_26Al_cont_3months_unbinned_data.fits.gz <br />

**Input Models:**  <br />
This is the description of the model of the diffuse emission due to the steady state annihilation of positrons produced by 26Al decay in our Galaxy. The spatial distribution is derived from the calculation of the propagation of positrons in our Galaxy. The initial positions of positrons follow the model NE2001 of Cordes & Lazio 2002 that fits the distribution of massive stars in our Galaxy, with a fraction of 26Al in the bulge of 2%. The positron propagation method is described in Alexis et al. 2014.The spectral distribution takes into account the annihilation line and the orthopositronium continuum. It was obtained from the model of Guessoum et al 2005 that compute a spectrum for each phase of the interstellar medium. The spectral model was corrected by the Galactic rotation using the model of Fich, Blitz and Stark 1989 for R > 3 kpc and a solid rotation model for R < 3 kpc.

**Goals:** <br />
1. Detection of the diffuse line and continuum emissions
2. Detection of the Doppler shift in the disk
3. Detection of the spectral shape
4. Correlation with the 26Al map (1809 keV emission).

### Positrons from 44Ti
Internal ToDo (Pierre):
1. Proofread/check content

**Data Files:** <br />
Positrons_from_44Ti_line_3months_unbinned_data.fits.gz <br />
Positrons_from_44Ti_cont_3months_unbinned_data.fits.gz <br />

**Input Models:**  <br />
This is the description of the model of the diffuse emission due to the steady state annihilation of positrons produced by 44Ti decay in our Galaxy. The spatial distribution is derived from the calculation of the propagation of positrons in our Galaxy. The initial positions of positrons follow the model NE2001 of Cordes & Lazio 2002 that fits the distribution of massive stars in our Galaxy, with a fraction of 44Ti in the bulge of 2%, which corresponds to the fraction of massive stars also used for the 26Al. The positron propagation method is described in Alexis et al. 2014. The positron rate due to 44Ti decay is ~3 x 10^42 e+/s (see section 2.3 of Alexis et al. 2014).
The spectral distribution takes into account the annihilation line and the orthopositronium continuum. It was obtained from the model of Guessoum et al 2005 that compute a spectrum for each phase of the interstellar medium. The spectral model was corrected by the Galactic rotation using the model of Fich, Blitz and Stark 1989 for R > 3 kpc and a solid rotation model for R < 3 kpc.

**Goals:** <br />
1. Detection of the diffuse line and continuum emissions
2. Detection of the Doppler shift in the disk
3. Detection of the spectral shape
   
## Nucleosynthesis
The tools needed to complete these challenges are demonstrated in the [511 imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/511keV/ScAttBinning) and [511 spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/extended_source_fit) notebooks. 

### Al26 Cygnus Region
Internal ToDo (Pierre):
1. Proofread/check content
2. Provide links to cited papers
   
**Data Files:** <br /> 
26Al_Cyg_Region_3months_unbinned_data.fits.gz

**Input Models:**  <br />
The characteristics of the emission were obtained from the analyses of INTEGRAL/SPI observations
described in Martin+09. The source is modeled with a 3deg width (standard deviation) Gaussian shape emission centered
at l = 81 deg, b = 1 deg. The line flux is 3.9e-5 ph/s/cm2. It is centered at 1808.8 keV and its width is 1.6 keV (FWHM)
due to the interstellar turbulence.

**Goals:** <br />
1. Make detection taking into account the Galactic diffuse continuum background at 1809 keV emission.
2. Measure width of the gamma-ray line.
3. Recover 60Fe/26Al ratio (see 60Fe_Cyg_Region)

### Al26 NE2001
Internal ToDo (Pierre):
1. Proofread/check content
2. Provide links to cited papers
   
**Data Files:** <br /> 
26Al_NE2001_3months_unbinned_data.fits.gz

**Input Models:**  <br />
This is the description of the model of the 1809 keV line diffuse emission due decay of 26Al in our Galaxy. The spatial distribution is derived from the model NE2001 of Cordes & Lazio 2002 that fits
the distribution of massive stars in our Galaxy. The fraction of 26Al in the bulge is 2%. This value is a compromise between SPI observations and results of studies of star formation rate in this region.
The shape of the line in each spatial bin takes into account the turbulence of the interstellar medium and the Galactic rotation using the model of Fich, Blitz and Stark 1989 for R > 3 kpc and a solid rotation model for R < 3 kpc.

**Goals:** <br />
1. Detection of the diffuse emission.
2. Detection of the Doppler shift in the disk.
3. Detection of the spectral shape.
4. Correlation with the emission of the galactic positron annihilations
5. Extract F(26Al)/F(60Fe) ratio and its uncertainty
   
### Ti44
The tools needed to complete these challenges are demonstrated in the [Crab spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/crab) and [GRB localization](https://github.com/cositools/cosipy/tree/main/docs/tutorials/ts_map) notebooks.

Internal ToDo (Anaya):
1. Clarify and provide a bit more information regarding the models.
2. State the goals of the data challenge.
3. Proofread/check content
4. Provide links to cited papers.
   
**Data Files:** <br /> 
CasApartiallyresolved_3months_unbinned_data.fits.gz <br />
CasAfullyresolved_3months_unbinned_data.fits.gz <br />
CasAG16distribution_3months_unbinned_data.fits.gz <br />
CasAunresolved_3months_unbinned_data.fits.gz <br />
CasAsymmetric_3months_unbinned_data.fits.gz <br />

**Input Models:**  <br />
In all 4 scenarios, bulk centre of motion is at rest. Doppler broadening is limited to 1000 km/s, as otherwise, when combined with the Doppler shifts of clumps, the signal will fall quite outside the DC2 simulated response region of 1143-1171 keV.

In asymmetric scenarios, Clump 1: Contains 2/3 of total 44Ti yield Doppler shifted towards from the observer (blueshifted). Has peak energy higher than 1157 keV. Clump 2: Contains 1/3 of total 44Ti yield Doppler shifted away from the observer (redshifted). Has peak energy lower than 1157 keV.

All spectra follow simple Gaussian distributions. The flux is taken as the value between 2.1 x 10^-5 in Grefenstette et al 2015 and 3.5 x 10^-5 ph/cm^2/s in Siegert et al 2015.

**Goals:** <br />
1. What are the goals?

### Fe60 Cygnus Region
Internal ToDo (Pierre):
1. Proofread/check content
2. Provide links to cited papers
   
**Data Files:** <br /> 
60Fe_Cyg_Region_3months_unbinned_data.fits.gz

**Input Models:**  <br />
The flux of the 60Fe lines is derived from the calculation of Martin+10. The spatial extent of this diffuse emission is the same as the one of the 1809 keV line emission that were obtained from the analyses of SPI/INTEGRAL observations
described in Martin+09. The source is modeled with a 3deg width (standard deviation) Gaussian shape emission centered at l = 81 deg, b = 1 deg. The line fluxes are 2.7e-6 ph/s/cm2 for the both line. The line energies are 1173.3 keV and 1332.6 keV and their width are 1.04 keV and 1.18 keV (FWHM), respectively (broadening due to the interstellar turbulence).

**Goals:** <br />
1. Make detection taking into account the Galactic diffuse continuum background at 1173 keV and 1332 keV.
2. Measure width of the gamma-ray line.
3. Recover 60Fe/26Al ratio (see 26Al_Cyg_Region)

 ### Fe60 NE2001
Internal ToDo (Pierre):
1. Proofread/check content
2. Provide links to cited papers
   
**Data Files:** <br /> 
60Fe_NE2001_3months_unbinned_data.fits.gz

**Input Models:**  <br />
This is the description of the model of the diffuse emission of the 1173 keV and 1332 keV lines due decay of 60Fe in our Galaxy. The spatial distribution is derived from the model NE2001 of Cordes & Lazio 2002 that fits the distribution of massive stars in our Galaxy. The fraction of 60Fe in the bulge is 2%. This value is the same as the one of the 26Al, which is a compromise between SPI observations and results of studies of star formation rate in this region. The flux is computed assuming a total mass of 60Fe of 3.5 M_sol in our Galaxy (see Wang et al., 2020 and Siegert et al. 2023). The shape of the line in each spatial bin takes into account the turbulence of the interstellar medium and the Galactic rotation using the model of Fich, Blitz and Stark (1989 for R > 3 kpc and a solid rotation model for R < 3 kpc.

**Goals:** <br />
1. Detection of the diffuse emission.
2. Extraction of the F(26Al)/F(60Fe) ratio and its uncertainty.
   
## Galactic 
The tools needed to complete the Galactic challenges are demonstrated in the [Crab spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/crab), [Crab imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/Crab/ScAttBinning), and [GRB localization](https://github.com/cositools/cosipy/tree/main/docs/tutorials/ts_map) notebooks.

**All challenges should use the same detector response file:**

### Galactic diffuse continuum

**Data Files:** <br />
GalTotal_SA100_F98_3months_unbinned_data.fits.gz

**Input Models:**  <br />
The Galactic diffuse continuum emission is modeled using the v57 release of the GALPROP cosmic ray (CR) propagation and interstellar emissions framework [(Porter+22)](https://iopscience.iop.org/article/10.3847/1538-4365/ac80f6). GALPROP self-consistently calculates spectra and abundances of Galactic CR species and associated diffuse emissions (gamma rays, X-rays, and radio) in 2D and 3D. The v57 release includes a set of steady-state emission model examples that reproduce the latest CR data. There are six models in total, categorized according to the CR source and interstellar radioation field (ISRF) model used for the prediction. There are 3 CR source models (SA0, SA50, SA100) and two ISRF models (R12, F98). The CR source density models are based on the distribution of injected CR power, with SA0 describing an axisymmetric disk (following the radial distribution of pulsars), SA50 describing a 50/50% split of the injected CR luminosity between disk-like and spiral arms, and SA100 describing pure spiral arms. All models have the same exponential scale height of 200 pc. The two ISRF models employ different spatial densities for both the stars and the dust but produce intensities very similar to those of the data for near- to far-infrared wavelengths at the location of the solar system (see [Porter+17](https://iopscience.iop.org/article/10.3847/1538-4357/aa844d) and references therein). For the neutral gas distributions (atomic and molecular), a 3D model from [Johannesson+18](https://iopscience.iop.org/article/10.3847/1538-4357/aab26e) is employed. These GALPROP models include the total emission, which is dominated by inverse Compton radiation, but also has a small contribution from Bremsstrahlung towards the upper energy bound. As our representative case, for DC3 we simulate the SA100-F98 model. 

This is the first data challenge to include the Galactic diffuse continuum, and our corresponding goals this year are straight forward. Future data challenges will look more into the different model variations and key parameters. 

**Note that the Galactic diffuse continuum emission is also part of the standard background model for COSI, which will be employed for most analyses.**

**Goals:** <br />
1. Measure the spectrum of the Galactic diffuse continuum emission, extracting it from the rest of the background. 
2. Image the Galactic diffuse continuum emission in the COSI energy band.
3. Characterize how the the Galactic diffuse continuum emission impacts the sensitivity for point sources in the Galactic plane. 
   
### CygX1

**Data Files:** <br />


**Input Models:**  <br />


**Goals:** <br />

## Extragalactic
The tools needed to complete the Extragalactic challenges are demonstrated in the [Crab spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/crab) notebook.

**All challenges should use the same detector response file:**
ResponseContinuum.o3.e100_10000.b10log.s5383095312085.m1945.nonsparse.binnedimaging.imagingresponse.rsp.gz

### NGC 1068
Internal ToDo (Lea):
1. Proofread/check content
2. Provide links to cited papers

**Data Files:** <br /> 
NGC_1068_3months_unbinned_data.fits.gz

**Input Models:**  <br />
The baseline model is a powerlaw with exponential cut-off from Bauer+2015: <br />
Gamma=1.92, Ecut=200 keV; intrinsic flux 2-10 keV = 8.9e-10 erg/cm2/s

**Goals:** <br />
1. Determine flux in the COSI band, and coronal cut-off energy. 

### NGC 4151
Internal ToDo (Lea):
1. Proofread/check content
2. Provide links to cited papers

**Data Files:** <br />
NGC_4151_bright_3months_unbinned_data.fits.gz <br />
NGC_4151_EC200_3months_unbinned_data.fits.gz <br />
NGC_4151_EC1000_3months_unbinned_data.fits.gz <br />
NGC_4151_faint_3months_unbinned_data.fits.gz <br />

**Input Models:**  <br />
The baseline model is a powerlaw with exponential cut-off. <br />

flux in the 20-30 keV calibrated from NuSTAR observations: <br />
NGC_4151_ec200: Gamma=1.75, Ecut=200 keV <br />
NGC_4151_ec1000: Gamma=1.75, Ecut=1000 keV <br />

flux calibrated from INTEGRAL observation of Lubinski+2010: <br />
NGC_4151_bright: Gamma=1.71, Ecut=264 keV <br />
NGC_4151_faint: Gamma=1.81, Ecut=1000 keV <br />

**Goals:** <br />
1. Determine flux in the COSI band, and coronal cut-off energy. <br />

### 4C+21.35
Internal ToDo (Michela):
1. Give gaol of challenge
2. Provide description of model
3. Proofread/check content

**Data Files:** <br />
4C21p35_noflare_3months_unbinned_data.fits.gz <br />
4C21p35_flare_3months_unbinned_data.fits.gz <br />

**Input Models:**  <br />
We present a lightcurve showing 2 states: a flaring state and a quiescent state. The Flaring state is defined every time in which the average flux is 3 times greater than the 16-years average flux (given by Fermi).

The two states come with two different spectra: both powerlaws with different indices:
1. noflare = 1.6
2. flare = 2.5

The normalization is derived from the integrated flux in COSI energy band derived from the extrapolation of the Fermi-LAT log parabola function. 

**Goals:** <br />
1. What are the goals of this challenge. <br />

## Dark Matter
Internal ToDo (Yu):
1. Provide more info about models.
2. Proofread/check content

The tools needed to complete these challenges are demonstrated in the [511 imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/511keV/ScAttBinning) and [511 spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/extended_source_fit) notebooks.
 
**Data Files:** <br />
eeg_ISO_3months_unbinned_data.fits.gz <br />
eeg_Bur_3months_unbinned_data.fits.gz <br />
eeg_NFW_3months_unbinned_data.fits.gz <br />
gg_ISO_3months_unbinned_data.fits.gz <br />
gg_Bur_3months_unbinned_data.fits.gz <br />
gg_NFW_3months_unbinned_data.fits.gz

**Input Models:**  <br />
Files for DM annihilating into gamma-gamma or e-e-gamma, assuming NFW or Burkert profile. <br />
m_DM = 3 MeV and <sigma v> = 1e-30 cm3/s. Other parameters are detailed in our slides. <br />

**Goals:** <br />
1. Calculate the gamma-ray spectra from the annihilating MeV DM.
2. Compare the spectra from DM and background, and determine COSI’s detectability for attractive DM candidates.
   
## Extra Challenges
Below we provide more advanced data challenges for interested users. The ultimate goal of these challenges would be to eventually integrate the methods and tools into the cosipy source code. 

### Extended 


### Advanced


## Known Caveats 


## Citing 
If you make use of any of the data products from the COSI data challenges in a publication, please provide a link to this page. 

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
In general, observations in the MeV band are hindered by high backgrounds (both instrumental and astrophysical). In order to ensure that COSI accomplishes its main science goals, it is therefore crucial to have a firm understanding of these backgrounds. Although we are still in the early stages of development, with DC2 we have made significant progress in characterizing the background emission for COSI. Further details can be found in the [backgrounds](backgrounds) directory. 

For analyzing data in DC2, the backgrounds are modeled using the actual injected backgrounds themselves. This is the ideal case, where the backgrounds are perfectly known, which of course is not very realistic. In future data challenges we will be developing tools for estimating backgrounds when they are not perfectly known, as will be the case for the actual observations. 

## Earth Occultation
The Earth blocks a significant portion of the sky for satellites in low-Earth orbit, referred to as Earth occultation. It is important to account for this when simulating observations and performing data analysis. In order to implement this for the DC3 simulations we needed  to add new functionality to MEGAlib, as detailed in the [earth-occultation](earth-occultation) directory. **These new methods now allow for simulating instruments with non-zenith pointings.** We also added new methods in cosipy to account for Earth occultation in the data analysis. 

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

Note: binned data products are also available for the 511 components. The file names are the same as listed above, but with "binned" instead of "unbinnned" and ".hdf5" instead of ".fits.gz". The binning matches the detector response, and has a time bin size of 7202.125 seconds. 

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

**Input Models:** 
Fluxes are estimated by assuming that the 511 keV photon flux is proportional to the stellar mass of a source. Using a Milky Way 511 keV flux of $2.8 \times 10^{-3} \  \mathrm{ph \ cm^{-2} \ s^{-1}}$ (Siegert et al 2016) and total stellar mass of $5.4 \times 10^{10} \  M_\odot$ (McMillan et al 2016), we scale the 511 keV flux of each extragalactic source based on the 511 keV flux assumed to be associated with the stellar mass in the Milky Way.

The stellar masses are: <br />
LMC: $1 \times 10^{10} \ M_\odot\$ (Erkal et al 2019) <br />
M31: $1.25 \times 10^{11} \ M_\odot\$ (Tamm et al 2012) <br />
Virgo: $1.2 \times 10^{14} \ M_\odot\$ (Fouque et al 2001) <br />

We also include each source at 100x the nominal flux, in order to ensure that they are above COSI's 511 keV line sensitivity.

**Goals:**
1. Determine COSI's sensitivity for detecting these potential extragalactic 511 keV sources. 

## Nucleosynthesis 

### Al26
The tools needed to complete these challenges are demonstrated in the [511 imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/511keV/ScAttBinning) and [511 spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/extended_source_fit) notebooks. 

**Data Files:** <br /> 


Note: binned data products are also available for the Al26 components. The file names are the same as listed above, but with "binned" instead of "unbinnned" and ".hdf5" instead of ".fits.gz". The binning matches the detector response, and has a time bin size of 7202.125 seconds. 

**Input Models:**  <br />

**Goals:**

### Ti44
The tools needed to complete these challenges are demonstrated in the [Crab spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/crab) and [GRB localization](https://github.com/cositools/cosipy/tree/main/docs/tutorials/ts_map) notebooks.

**Data Files:** <br /> 

Note: There are two different response files with a slightly different width of the energy bin (one being more broad than the other). An additional goal of this data challenge is to determine which response file works better in the analysis.   

**Input Models:**  <br />


**Goals:** <br />


## Galactic 
The tools needed to complete the Galactic challenges are demonstrated in the [Crab spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/crab), [Crab imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/Crab/ScAttBinning), and [GRB localization](https://github.com/cositools/cosipy/tree/main/docs/tutorials/ts_map) notebooks.

**All challenges should use the same detector response file:**


### CygX1

**Data Files:** <br />


**Input Models:**  <br />


**Goals:** <br />


### CygX3

**Data Files:** <br />


**Input Models:**  <br />
 
**Goals:** <br />


### 1E1740.7-2942

**Data Files:** <br />


**Input Models:**  <br />


**Goals:** <br />


### GRS 1758-258

**Data Files:** <br />


**Input Models:**  <br />


**Goals:** <br />
 

### PSR J1513-5908 (B1509-58)

**Data Files:** <br />


**Input Models:**  <br />


**Goals:** <br />


### PSR J1846-0258

**Data Files:** <br />


**Input Models:**  <br />


**Goals:** <br />


### Crab DC2

**Data Files:** <br />


**Input Models:**  <br />


**Goals:** <br />

### Crab DC1

**Data Files:** <br />


**Input Models:**  <br />


**Goals:** <br />


## Extragalactic
The tools needed to complete the Extragalactic challenges are demonstrated in the [Crab spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/crab) notebook.

**All challenges should use the same detector response file:**
SMEXv12.Continuum.HEALPixO3_10bins_log_flat.binnedimaging.imagingresponse.nonsparse_nside8.area.good_chunks_unzip.h5

### 3C 273

**Data Files:** <br /> 


**Input Models:**  <br />


**Goals:** <br />


### 3C 279

**Data Files:** <br />


**Input Models:**  <br />


**Goals:** <br />


### 4C+21.35

**Data Files:** <br />


**Input Models:**  <br />


**Goals:** <br />


## Extra Challenges
Below we provide more advanced data challenges for interested users. The ultimate goal of these challenges would be to eventually integrate the methods and tools into the cosipy source code. 

### Extended 


### Advanced


## Known Caveats 


## Citing 
If you make use of any of the data products from the COSI data challenges in a publication, please provide a link to this page. 

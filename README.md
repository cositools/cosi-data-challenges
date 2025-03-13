<div align="center">
  
# Welcome to COSI Data Challenge 3!

<p align="center">
<img width="325"  src="static/COSI-SMEX Emblem_2E.png">
</p>

<div align="left">

![Countdown](https://img.shields.io/badge/%20Anticipated%20Launch%20Date%20-871%20days%20left-blue)

## Table of Contents

- [Introduction](#introduction)
- [Getting Started](#getting-started)
- [System Requirements](#system-requirements)
- [Getting Help](#getting-help)
- [Computing Resources](#computing-resources)
- [Simulation Tools](#simulation-tools)
- [Releases](#releases)
- [Summary of Current and Past Challenges](#summary-of-current-and-past-challenges)
- [Backgrounds](#backgrounds)
- [Earth Occultation](#earth-occultation)
- [Polarization](#polarization)
- [Available Reference Guides](#available-reference-guides)
- [Data Challenges](#data-challenges)
- [Known Caveats and Limitations](#known-caveats-and-limitations)
- [Citing](#citing)

## Introduction
Welcome to the third COSI Data Challenge (DC3)! The COSI Data Challenges are released on a yearly basis in preparation for the launch of the COSI Small Explorer (SMEX) class mission in 2027 ([Tomsick+23](https://ui.adsabs.harvard.edu/abs/2023arXiv230812362T/abstract)). They are based on simulated data, which is intended to closely mimic the real flight data. Every year the Data Challenges have increasingly more realistic source and background models, and they are analyzed with increasingly complete and matured analysis tools. In general there are two main goals of the Data Challenges:

1. Facilitate development of the COSI data pipeline and analysis tools
   - With routine feedback from scientists
   - Alongside development of the expected source models by the science team 
2. Provide resources to the astrophysics community to become familiar with COSI data
   - Excellent training for science team in preparation for first analyses after launch
   - Public releases help with community building before COSI data is released

## Getting Started 
The only software requirement for DC3 is [cosipy](https://github.com/cositools/cosipy). A general introduction into cosipy, including installation instructions, can be found in the [cosipy-intro](cosipy-intro) directory. For a general introduction into analyzing data from Compton telescopes see [Compton-telescope-data-analysis-intro](Compton-telescope-data-analysis-intro). Note that cosipy is part of the larger COSITools, which is a broad collection of COSI data analysis tools, documentation, and verification data sets. COSITools can be installed by following the installation instructions [here](https://github.com/cositools/cosi-setup). This also includes MEGAlib, which is the main software program used for running simulations. However, unless you need MEGAlib and/or COSITools for other reasons, it's highly recommended to just install cosipy.    

This year's Data Challenge is based on 3 months of exposure time, for an equatorial orbit at an altitude of 530 km, with a pointing that rocks between $\pm 20^\circ$ from the Earth zenith. The simulated data products are provided in Fits file format, and are hosted on Wasabi. Details of the simulations, simulated data, and information for accessing the data products can be found in the [data-products](data-products) directory. 

The input models and challenges for DC3 were provided by the COSI science teams. There are challenges for the different science groups: GRBs, Positrons, Nucleosynthesis, Galactic, Extragalactic, and Dark Matter. These are described in detail in the [Data Challenges](#data-challenges) section below.  

Users are encouraged to post feedback on the [Discussions](https://github.com/cositools/cosi-data-challenges/discussions) page. This can include solutions to specific challenges, questions, issues, etc.

In summary, to get started with DC3, install cosipy, familiarize yourself with the [data-products](data-products), and then start working through the [Data Challenges](#data-challenges), as described below. 

## System Requirements
One of our goals in developing cosipy is to make it easily accesible to all users. **All of the Data Challenges should be doable on a laptop with at least 16 GB of RAM**. We are still working on optimizing the code, and so please let us know if you are running into memory issues.

## Getting Help
Please submit a new issue in the [cosipy](https://github.com/cositools/cosipy) git repository if you have issues with the code. If you have general feedback, or need further assistance, please reach out to the COSI Data Challenge team lead, Chris Karwin ([christopher.m.karwin@nasa.gov](mailto:christopher.m.karwin@nasa.gov)), the cosipy implementation lead, Israel Martinez-Castellanos ([israel.martinezcastellanos@nasa.gov](israel.martinezcastellanos@nasa.gov)), and the pipeline development lead Carolyn Kierans ([carolyn.a.kierans@nasa.gov](carolyn.a.kierans@nasa.gov)).

## Computing Resources
<div align="center">
<img width="1050"  src="static/clusters.png">
<div align="left">
  
The simulations for the COSI Data Challenges are run on high performance computing clusters. Most notably, we have made extensive use of NASA's [Discover cluster](https://www.nccs.nasa.gov/systems/discover), the [MOGON](https://mogonwiki.zdv.uni-mainz.de/docs/introduction/what_is_mogon) cluster in Mainz, and Clemson University's [Palmetto](https://docs.rcd.clemson.edu/palmetto/) cluster. We used 1000 parallel cores for most of the source simulations, which allowed us to simulate them in a fairly short time (typically less than ~10 minutes of total wall time per source). The background simulations are generally much more computationally intensive, with the extreme case being the SAA component, which required roughly 2 million core hours to simulate. 

## Simulation Tools
The simulations employ [MEGAlib](https://github.com/zoglauer/megalib) via the Python-based COSI simulation pipepline, [cosi-sim](https://github.com/cositools/cosi-sim). Details regarding the specific MEGAlib versions and configuration files can be found in each respective Data Challenge release. Model inputs for the simulations and the corresponding Data Challenges come from the COSI science team. All of the models used for past Data Challenges can be found in the source library of the cosi-sim tools ([link](https://github.com/cositools/cosi-sim/tree/main/cosi_sim/Source_Library)).   

## Releases
- [Data Challenge 1](https://github.com/cositools/cosi-data-challenge-1): March 2023
- [Data Challenge 2](https://github.com/cositools/cosi-data-challenges/tree/data_challenge_2.0): March 2024
- Data Challenge 3: April 2025 **(latest release)**
- Data Challenge 4: Planned for March 2026
- Data Challenge 5: Planned for March 2027 (final release before launch :rocket:!)

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
  - Data challenges for all the main science groups (including dark matter), covering all of COSI's primary science objectives. 
  - All models and challenges provided by respective COSI science teams.
  - Used 3 months of observations, for an equatorial orbit at 530 km.
  - Simulations include rocking of instrument:
    - Pointing changes between +/- 22 degrees every 12 hrs, with 8 minute transition time. 
  - Used detailed COSI SMEX mass model.
  - Simulated all background components in low-Earth orbit, including variability from geomagnetic cutoff, long-term buildup, and full SAA passage.
    - Background also includes the Galactic diffuse continuum for the first time. 
  - New methods in both MEGAlib and cosipy to account for Earth occultation with a non-zenith pointing. 
  - First time including polarization.
  - Numerous improvements to cosipy:
    - First version of source injector.
    - New implementation of Earth occultation in point source response.
    - First polarization tools.
    - New methods to estimate the background for continuum sources and line sources.
    - Refinements and further developments of imaging class.
    - New extended source response class.
      
## Backgrounds
In general, observations in the MeV band are hindered by high backgrounds (both instrumental and astrophysical). In order to ensure that COSI accomplishes its main science goals, it is therefore crucial to have a firm understanding of these backgrounds. DC3 includes all of the background components. Compared to the background estimates from DC2, we have now included the full SAA passage, as well as the Galacic diffuse continuum emission. Further details can be found in the [backgrounds](backgrounds) directory. 

For analyzing data in DC3, the starting point is to model the backgrounds using the actual simulated backgrounds themselves. This is the ideal case, where the backgrounds are perfectly known, which of course is not very realistic. The next step is to estimate the backgrounds. **With DC3 we have new methods to estimate the background for both line and continuum sources**. The background estimation tool for line emission can be used for both point sources and extended sources. An example tutorial can be found in the [line background estimation](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/background_estimation/line_background/line_background_estimation_example_notebook.ipynb) notebook. The background estimation tool for continuum emission is currently only available for point sources. An example tutorial is available in the [continuum background estimation](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/background_estimation/continuum_estimation/BG_estimation_example.ipynb) notebook. We stress that both of these background estimation algorithms are only first versions, and further development and testing is still needed. More details are provided in the respective example tutorials. 

The available background files are listed in the [data-products](data-products) directory. We provide a file with the total background, as well as separate files for the individual background components (as details in the [backgrounds](backgrounds) directory). 

## Earth Occultation
The Earth blocks a significant portion of the sky for satellites in low-Earth orbit, referred to as Earth occultation. It is important to account for this when simulating observations and performing data analysis. In order to implement this for the DC3 simulations we added new functionality to MEGAlib (*develop-cosi* branch), as detailed in the [earth-occultation](earth-occultation) directory. **These new methods now allow for simulating instruments with non-zenith pointings.** We also added new methods in cosipy to account for Earth occultation in the data analysis. 

## Polarization
Polarimetry is a key aspect of COSI's primary science goals. With DC3 we release the first version of our polarization tools in cosipy. We also added new functionality in MEGAlib to define polarization in Galactic coordinates. This allows for simulating polarized sources together with the instrument's orbit. A general introduction into Compton polarimetry can be found in the [polarization](polarization) directory.

## Available Reference Guides
- **[Introduction to Compton telescope data analysis](Compton-telescope-data-analysis-intro)**
- **[Introduction to cosipy](cosipy-intro)** 
- **[Summary of background simulations](backgrounds)**
- **[Dealing with Earth occultation](earth-occultation)** 
- **[Introduction to polarization](polarization)** 

## Data Challenges
We have created example Jupyter notebooks demonstrating all of the tools that will be needed to complete this year's data challenges. They are available as part of the cosipy release, and listed below: <br /> 

Example 1: [dataIO](https://github.com/cositools/cosipy/tree/main/docs/tutorials/DataIO) <br />
Example 2: [GRB localization](https://github.com/cositools/cosipy/tree/main/docs/tutorials/ts_map) <br />
Example 3: [GRB spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/grb) <br />
Example 4: [Crab spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/crab) <br />
Example 5: [511 spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/extended_source_fit) <br />
Example 6: [Crab imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/Crab/ScAttBinning) <br />
Example 7: [511 imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/511keV/ScAttBinning) <br />
Example 8: [Source injector](https://github.com/cositools/cosipy/tree/develop/docs/tutorials/source_injector) <br />
Example 9: [TS maps](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/ts_map/Parallel_TS_map_computation_DC2.ipynb) <br />
Example 10: [Polarization (ASAD method)](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/polarization/ASAD_method.ipynb) <br />
Example 11: [Continuum background estimation](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/background_estimation/continuum_estimation/BG_estimation_example.ipynb) <br />
Example 12: [Line background estimation](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/background_estimation/line_background/line_background_estimation_example_notebook.ipynb) <br />

If you haven't worked with Jupyter before, you can find some help [here](https://github.com/cositools/cosi-data-challenge-2/tree/main/cosipy-intro/notebook_help.md).

As a very first step, try working through some of the example notebooks. It is highly recommended to start with the dataIO notebook, as this describes the general handling of COSI data, and it is needed for almost all other notebooks. Specific challenges for the different science topics are described in the links below. You can start with whichever topic you are most interested in. Each challenge will refer you to a specific example notebook that will demonstrate the basic tools needed to complete the respective challenge. If you have completed the main challenges and are interested in exploring other models, you can employ the source injector (see the [Source injector](https://github.com/cositools/cosipy/tree/develop/docs/tutorials/source_injector) example). If you are interested in getting more involved in the cosipy development, see the [Known Caveats and Limitations](#known-caveats-and-limitations) section at the bottom of this page, as well as the bottom of the [cosipy-intro](cosipy-intro), which outlines some of the priority areas for the next stages of development. 

All input models used for the simulations can be found in the DC3 source library of the COSI simulation pipeline, available [here](https://github.com/cositools/cosi-sim/tree/main/cosi_sim/Source_Library/DC3). This includes all the information about the injected sources, and it can be used for checking the results of the data challenges. 

**Orientation Files:** <br />
Two orientation files are available: <br />
DC3_final_530km_3_month_with_slew_15sbins_GalacticEarth_SAA.ori  <br />
DC3_final_530km_3_month_with_slew_1sbins_GalacticEarth_SAA.ori  <br />
The 1 second binning may be optimal for analyzing transients on short time scales, but generally the 15 second binning should be sufficient and is considered the default. 

**Background Files:** <br />
There are a few different options for modeling the background. The staring point is to use the ideal case, where the background model in the analysis is the same as the simulated background. We have provided a file with the total background, as well as files for the individual background components. To simplify the analysis, it is sometimes helpful to start with just a single background component (e.g. albedo photons), and then move on to the total background after everything is working. A more realistic estimate of the uncertainty on the background modeling can be achieved by using one of the background estimation tools (see the [Continuum background estimation](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/background_estimation/continuum_estimation/BG_estimation_example.ipynb) and [Line background estimation](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/background_estimation/line_background/line_background_estimation_example_notebook.ipynb) examples). However, we caution that these tools are in thier very early stages, and they still require further testing and development.  

**Data Challenges for the different science topics can be found in the links below:**
- [GRBs](DC-GRBs)
- [Positrons](DC-Positrons)
- [Nucleosynthesis](DC-Nucleosynthesis)
- [Galactic](DC-Galactic)
- [Extragalactic](DC-Extragalactic)
- [Dark Matter](DC-DarkMatter)
  
## Known Caveats and Limitations
The items listed here are some of the priorities for DC4 development. These can be considered as extra/advanced challenges, and anybody is welcomed to work on them, with the ultimate goal of implementing the software solutions into cosipy. Also see the bottom of the [cosipy-intro](cosipy-intro) for a related discussion on the next steps of development.

- **It is not currently possible to simultaneously fit continuum and line components.** We have separate response files for different emission components (i.e. continuum, 511 keV, Aluminum-26, etc.), and with the current binned analysis setup in cosipy, the data binning needs to match the response binning, and thus only a single component can be analyzed at a time. Possible solutions to this include:
  - Creating a single response for all components
  - Creating a class that automatically matches an input model with the corresponding response
  - Reparameterizing the response in such a way that prevents this issue 
- **Methods need to be developed to determine the response for broadened and offset line emission.** These methods should utilize the baseline response files (e.g. 511 keV, Aluminum-26, Iron-60, etc.), and allow for analyzing any arbitrary line emission.
- **The background estimation tools need to be further tested and developed.** With DC3 we have provided first versions for estimating continuum and line backgrounds. These methods need to be tested, stressed, and further developed. Additionally, we still need background estimation tools for transient sources.
- **The way in which parameters are configured needs to be refined, and callable scripts need to be added.** By callable scripts we are referring to command-line options that will perform common task, such as producing light curves and spectra.  
- **The tools still need to be stressed to find limitations.** The COSI pipeline team has been rapidly developing the cosipy library in preparation for the satellite mission. Our aim is to make this library robust, sustainable, and highly user-friendly. Through more and more user interactions and feedback, we can better learn where the code is working well, and where it breaks down.
  
## Citing 
If you make use of any of the data products from the COSI Data Challenges in a publication, please provide a link to this page and cite [Zoglauer+23](https://arxiv.org/abs/2102.13158) and [Martinez-Castellanos+23](https://pos.sissa.it/444/858). 

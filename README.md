<div align="center">
  
# Welcome to the COSI Data Challenges!

<p align="center">
<img width="325"  src="static/logo.png">
</p>

### latest release: [cosi-data-challenge-3](cosi-data-challenge-3)

<div align="left">

## Table of Contents

- [Introduction](#introduction)
- [Getting Started](#getting-started)
- [System Requirements](#system-requirements)
- [Getting Help](#getting-help)
- [Releases](#releases)
- [Computing Resources](#computing-resources)
- [Simulation Tools](#simulation-tools)
- [Executive Summary of Current and Past Challenges](#executive-summary-of-current-and-past-challenges)
- [Useful Reference Guides](#useful-reference-guides)
- [Citing](#citing)

## Introduction
The COSI data challenges are released on a yearly basis in preparation for the launch of the COSI Small Explorer (SMEX) class mission. They are based on simulated data, which is intended to closely mimic the real flight data. Every year the data challenges have increasingly more realistic source and background models, and they are analyzed with increasingly complete and matured analysis tools. In general there are two main goals of the data challenges:

1. Facilitate development of the COSI data pipeline and analysis tools.
   - With routine feedback from scientists. 
   - Alongside development of the expected source models by the science team. 
2. Provide resources to the astrophysics community to become familiar with COSI data.
   - Excellent training for science team in preparation for first analyses after launch.
   - Public releases help with community building before COSI data is released. 

## Getting Started
For new users, copy the COSI Data Challenges repository as follows:
```
git clone https://github.com/cositools/cosi-data-challenges.git
```
If you've already cloned the repository in the past, then simply update it to get the latest release:
```
cd your/path/cosi-data-challenges
git pull
```
As specified at the top of the page, the most recent release is [cosi-data-challenge-2](cosi-data-challenge-2). Everything you need for this data challenge is contained in the linked directory. Head there to get started!

Alternatively, this repository also contains all past data challenges, as specified in the [Releases](#releases) section below. Each released data challenge is self-contained, and you will find everything you need to get started in the respective directory. 

## System Requirements
One of our goals in developing cosipy is to make it easily accesible to all users. **All of the data challenges starting with DC2 should be doable on a laptop with at least 16 GB of RAM**. We are still working on optimizing the code, and so please let us know if you are running into memory issues. 

## Getting Help
Please submit a new issue in the [cosipy](https://github.com/cositools/cosipy) git repository if you have issues with cosipy. If you have general feedback, or need further assistance, please reach out to the COSI Data Challenge team lead, Chris Karwin ([christopher.m.karwin@nasa.gov](mailto:christopher.m.karwin@nasa.gov)), the cosipy implementation lead, Israel Martinez-Castellanos ([israel.martinezcastellanos@nasa.gov](israel.martinezcastellanos@nasa.gov)), and the pipeline development lead Carolyn Kierans ([carolyn.a.kierans@nasa.gov](carolyn.a.kierans@nasa.gov)).

## Releases

- Data challenge 1, March 2023: [cosi-data-challenge-1](cosi-data-challenge-1)
- Data challenge 2, March 2024: [cosi-data-challenge-2](cosi-data-challenge-2)
- Data challenge 3, March 2025: [cosi-data-challenge-3](cosi-data-challenge-3)
- Data challenge 4: Planned for March 2026
- Data challenge 5: Planned for March 2027 (final challenge before launch :rocket:!)

## Computing Resources
<div align="center">
<img width="1050"  src="static/clusters2.png">
<div align="left">
  
The simulations for the COSI data challenges are ran on high performance computing clusters. Most notably, we have made extensive use of NASA's [Discover cluster](https://www.nccs.nasa.gov/systems/discover), the [MOGON](https://mogonwiki.zdv.uni-mainz.de/docs/introduction/what_is_mogon) cluster in Mainz, and Clemson University's [Palmetto](https://docs.rcd.clemson.edu/palmetto/) cluster. 

## Simulation Tools
The simulations employ [MEGAlib](https://github.com/zoglauer/megalib) via the Python-based COSI simulation pipepline, [cosi-sim](https://github.com/cositools/cosi-sim). Details regarding the specific MEGAlib versions and configuration files can be found in each respective data challenge directory. Model inputs for the simulations and the corresponding data challenges come from the COSI science team. All of the models used for past data challenges can be found in the source library of the cosi-sim tools ([link](https://github.com/cositools/cosi-sim)).   

## Executive Summary of Current and Past Challenges 
- **[Data Challenge 1](cosi-data-challenge-1):**
  - Focused on the 2016 COSI Balloon flight.
  - Release includes real flight data for the Crab.
  - Main goal is to learn the fundamentals of analyzing Compton data with COSI.
  - The analysis tools used for DC1 are only preliminary (referred to as cosipy classic).
    - Developed by Thomas Siegert for analysis of the 2016 balloon data. 
  - Contains 3 straightforward examples of COSI’s science goals:
    - Extracting energy spectra from the Crab, Cen A, Cygnus X-1, and Vela.
    - Imaging bright point sources, such as the Crab and Cygnus X-1.
    - Imaging diffuse emission from the positron-electron annihilation 511 keV and Al-26 1.8 MeV gamma-ray lines.
- **[Data Challenge 2](cosi-data-challenge-2):**
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
- **[Data Challenge 3](cosi-data-challenge-3):**
  - Focused on COSI SMEX mission.
  - Data challenges for all the main science groups (including dark matter and solar), covering all of COSI's primary science objectives. 
  - All models and challenges provided by respective COSI science teams.
  - Used 3 months of observations, for an equatorial orbit at 530 km.
  - Simulations include rocking of instruement:
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
- **General Introduction to analyzing data from a Compton telescopes and the Compton data space:**
  - See main README from [cosi-data-challenge-1](cosi-data-challenge-1)
- **Analysis of data from the 2016 COSI balloon flight:**
  - [cosi-data-challenge-1/cosi_2016_balloon_data](cosi-data-challenge-1/cosi_2016_balloon_data)
- **General Introduction to cosipy:**
  - [cosi-data-challenge-2/cosipy-intro](cosi-data-challenge-2/cosipy-intro)
 - **Summary of the background simulations from data challenge 2:**
   - [cosi-data-challenge-2/backgrounds](cosi-data-challenge-2/backgrounds) 

## Citing 
If you make use of any of the data products from the COSI data challenges in a publication, please provide a link to this page. 

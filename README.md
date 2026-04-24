<div align="center">
  
# Welcome to COSI Data Challenge 4!

<p align="center">
<img width="325"  src="static/COSI-SMEX Emblem_2E.png">
</p>

<div align="left">

![Countdown](https://img.shields.io/badge/%20Anticipated%20Launch%20-464%20days-blue)

## Table of Contents

- [Introduction](#introduction)
- [Getting Started](#getting-started)
- [System Requirements](#system-requirements)
- [Getting Help](#getting-help)
- [Reference Guides](#reference-guides)
- [Data Challenges](#data-challenges)
- [Known Caveats and Limitations](#known-caveats-and-limitations)
- [Releases](#releases)
- [Citing](#citing)

## Introduction
Welcome to the fourth COSI Data Challenge (DC4)! The COSI Data Challenges are released on a yearly basis in preparation for the launch of the COSI Small Explorer (SMEX) class mission in 2027 ([Tomsick+23](https://ui.adsabs.harvard.edu/abs/2023arXiv230812362T/abstract)). They are based on simulated data, which is intended to closely mimic the real flight data. Every year the Data Challenges have increasingly more realistic source and background models, and they are analyzed with increasingly complete and matured analysis tools. In general there are two main goals of the Data Challenges:

1. Facilitate development of the COSI data pipeline and analysis tools
   - With routine feedback from scientists
   - Alongside development of the expected source models by the science team 
2. Provide resources to the astrophysics community to become familiar with COSI data
   - Excellent training for science team in preparation for first analyses after launch
   - Public releases help with community building before COSI data is released

## Getting Started 
The only software requirement for DC4 is [cosipy](https://github.com/cositools/cosipy). A general introduction into cosipy, including installation instructions, can be found in the [cosipy-intro](cosipy-intro/README.md) directory. For a general introduction into analyzing data from Compton telescopes see [Compton-telescope-data-analysis-intro](Compton-telescope-data-analysis-intro/README.md). Note that cosipy is part of the larger COSITools, which is a broad collection of COSI data analysis tools, documentation, and verification data sets. COSITools can be installed by following the installation instructions [here](https://github.com/cositools/cosi-setup). This also includes MEGAlib, which is the main software program used for running simulations. However, unless you need MEGAlib and/or COSITools for other reasons, it's highly recommended to just install cosipy.    

This year's Data Challenge is based on a single mock dataset intended to mimic the real flight data. The mock dataset is simulated using 3 months of exposure time, for an equatorial orbit at an altitude of 530 km, with a pointing that rocks between $\pm 22^\circ$ from the Earth zenith. The simulated data products are provided in FITS file format, and are hosted on Wasabi. Details of the simulations, simulated data, and information for accessing the data products can be found in the [data-products](data-products/README.md) directory. 

The input models and challenges for DC4 were provided by the COSI science teams. There are challenges for the different science groups: GRBs, Positrons, Nucleosynthesis, Galactic, Extragalactic, and Dark Matter. These are described in detail in the [Data Challenges](#data-challenges) section below.  

Users are encouraged to post feedback on the [Discussions](https://github.com/cositools/cosi-data-challenges/discussions) page. This can include solutions to specific challenges, questions, issues, etc.

In summary, to get started with DC4, install cosipy, familiarize yourself with the [data-products](data-products/README.md), and then start working through the [Data Challenges](#data-challenges), as described below. 

## System Requirements
We have made substantial efforts to optimize cosipy for accessibility and performance. However, due to the high-dimensional instrument response and computational demands of full analyses, running the complete data challenge workflows and achieving COSI’s full analysis potential will typically require access to a computing cluster or a high-performance workstation.

That said, many components of the data challenges can be run on a personal laptop with at least 16 GB of RAM. Users working on laptops may encounter limitations in runtime or memory for more advanced or large-scale analyses.

If you experience performance or memory issues, please let us know — we are continuously working to improve efficiency and usability.

## Getting Help
Please submit a new issue in the [cosipy](https://github.com/cositools/cosipy) git repository if you have issues with the code. If you have general feedback, or need further assistance, please reach out to the COSI Data Challenges team lead, Chris Karwin ([ckarwin@clemson.edu](mailto:ckarwin@clemson.edu)), the cosipy implementation lead, Israel Martinez-Castellanos ([israel.martinezcastellanos@nasa.gov](israel.martinezcastellanos@nasa.gov)), and the pipeline development lead Carolyn Kierans ([carolyn.a.kierans@nasa.gov](carolyn.a.kierans@nasa.gov)).

## Reference Guides
- **[Introduction to Compton telescope data analysis](Compton-telescope-data-analysis-intro/README.md)**
- **[Introduction to cosipy](cosipy-intro/README.md)**
- **[Simplified 2D tutorials](https://github.com/israelmcmc/gammaraytoys/tree/main/docs/tutorials)** (from the **[Gamma-ray Toys](https://github.com/israelmcmc/gammaraytoys/tree/main)** repository)
- **[Summary of background simulations](backgrounds/README.md)**
- **[Dealing with Earth occultation](earth-occultation/README.md)** 
- **[Introduction to polarization](polarization/README.md)** 
- **[Introduction to image deconvolution](image_deconvolution/README.md)** 

## Data Challenges
For DC4, we have produced a single mock dataset that mimics three months of real flight observations. It includes 64 sources along with the total background. Detailed information is available in the [data-products](data-products/README.md) directory. All simulation input models are provided in the source library of the COSI simulation pipeline (available [here](https://github.com/cositools/cosi-sim/tree/main/cosi_sim/Source_Library)), which can be used to verify data challenge results. 

We have created example Jupyter notebooks demonstrating some of the basic tools that will be needed to complete this year's data challenges. They are available as part of the cosipy release, and listed below. If you haven't worked with Jupyter before, you can find some help [here](https://github.com/cositools/cosi-data-challenge-2/tree/main/cosipy-intro/notebook_help.md). <br /> 

Example 1: [dataIO](https://github.com/cositools/cosipy/tree/main/docs/tutorials/DataIO/DataIO_example.ipynb) <br />
Example 2: [detector response](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/response/DetectorResponse.ipynb) <br />
Example 3: [GRB localization (TS maps)](https://github.com/cositools/cosipy/tree/main/docs/tutorials/ts_map/TS_map_fitting.ipynb) <br />
Example 4: [GRB spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/grb/SpectralFit_GRB.ipynb) <br />
Example 5: [Crab spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/crab/SpectralFit_Crab.ipynb) <br />
Example 6: [511 spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/extended_source_fit/diffuse_511_spectral_fit.ipynb) <br />
Example 7: [511 imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/511keV-Galactic-ImageDeconvolution.ipynb) <br />
Example 8: [Point Source injector](https://github.com/cositools/cosipy/tree/develop/docs/tutorials/source_injector/Point_source_injector.ipynb) <br />
Example 9: [Extended Source injector](https://github.com/cositools/cosipy/tree/develop/docs/tutorials/source_injector/Extended_source_injector.ipynb) <br />
Example 10: [Polarization (ASAD method)](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/polarization/ASAD_method.ipynb) <br />
Example 11: [Polarization (Stockes method)](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/polarization/Stokes_method.ipynb) <br />
Example 12: [Polarization (Maximum likelihood method)](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/polarization/maximum_likelihood_method.ipynb) <br />
Example 13: [Light curves](https://github.com/cositools/cosipy/tree/main/docs/tutorials/light_curves/speclc_grbdc3.ipynb) <br />
Example 14: [Continuum background estimation](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/background_estimation/continuum_estimation/BG_estimationNN_example.ipynb) <br />
Example 15: [Line background estimation](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/background_estimation/line_background/line_background_estimation_example_notebook.ipynb) <br />
Example 16: [Transient background estimation](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/background_estimation//transient_background/Transient_background_example.ipynb) <br />

As a very first step, try working through some of the example notebooks. It is highly recommended to start with the [dataIO](https://github.com/cositools/cosipy/tree/main/docs/tutorials/DataIO) notebook, as this describes the general handling of COSI data, and it is needed for almost all other notebooks. Specific challenges for the different science topics are described below. You can start with whichever topic you are most interested in. The example notebooks will demonstrate the basic tools needed to start on the respective challenges; however, new code and procedures may need to be implented to achieve all goals with the DC4 data. 

If you  and are interested in exploring other science models, you can employ the source injector (see the source injector examples). If you are interested in getting more involved in the cosipy development, see the [Known Caveats and Limitations](#known-caveats-and-limitations) section at the bottom of this page, as well as the bottom of the [cosipy-intro](cosipy-intro/README.md), which outlines some of the priority areas for the next stages of development. 

**Binned vs. Unbinned Analyses:** <br />
DC4 now allows for both binned and unbinned analyses. The choice of which type of analysis to perform will depend on the scientific objectives of the data challenge, and we leave this decision to the user. However, the required memory and compute need for these analyses will differ and may be a limitation for some users.

**Configuration Files:** <br />
For binned analyses, the configuration for the data binning is specified via yaml files, as demonstrated in the [dataIO](https://github.com/cositools/cosipy/tree/main/docs/tutorials/DataIO) tutorial (and others). **The data binning must match the response binning, and so the yaml configuration files must be updated accordingly when working with DC4 data.** The [detector response](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/response/DetectorResponse.ipynb) tutorial shows how to determine the response binning. The main difference with the DC4 response files is that the phi binning is now 6 degrees compared to 5 degrees for older tutorials. We are currently working on refining how paramaters are configured in cosipy, and this will be updated starting with DC5.  

**Orientation Files:** <br />
Two orientation files are available: <br />
DC4_final_530km_3_month_with_slew_15sbins_GalacticEarth_SAA.ori  <br />
DC4_final_530km_3_month_with_slew_1sbins_GalacticEarth_SAA.ori  <br />
The 1 second binning may be optimal for analyzing transients on short time scales, but generally the 15 second binning should be sufficient and is considered the default. 

**Background Modeling:** <br />
The DC4 mock dataset includes all of the background components. Details of the background models and simulations can be found in the [backgrounds](backgrounds/README.md) directory. The individual background files are listed in the [data-products](data-products/README.md) directory. 

A major challenge in DC4 will be handling the backgrounds. We have methods to estimate the background for transient, line, and continuum sources. Example notebooks for all three cases are provided above. We stress that these background estimation algorithms are still early versions, and further development and testing is still needed. More details are provided in the respective example tutorials. In addition to the background estimation algorithms provided, a major challenge for DC4 is to develop new background modeling methods/techniques, likely involving a combination of template fitting with other estimation approaches. This is particularly true for the continuum sources, but also relevant for line sources that are contaminated by instrumental backgrounds (e.g. 511 keV line).  

**Data Challenges for the different science topics can be found below (click to expand):**

<details>
  <summary>GRBs</summary>
  
## GRB Data Challenges
 
The Key Objectives for GRB science with COSI are:
1. Detect short GRBs following neutron star mergers, which are a known source of gravitational waves
2. Constrain geometries and emission processes with polarization

### DC4 Goals:
- Localize GRBs and fit the spectra
- Measure polarization (fraction and angle) of GRBs
- Localize MGFs and fit the spectra
- Measure the polarization (fraction and angle) of MGFs
- Check if the magnetar short burst is detectable, and if detectable, localize and fit the spectrum

The DC4 mock dataset includes 12 GRBs, 6 Magnetar Giant Flares (MGFs), and 1 magnetar short burst within the 3 months of observation time. Information for how to access the mock dataset and all other needed files is provided in the [data-products](data-products/README.md) page.  

**The binned analysis will require the following detector response files:** 
- ResponseContinuum.o3.e100_10000.b10log.s10396905069491.m2284.filtered.nonsparse.binnedimaging.imagingresponse.h5 <br />
- ResponseContinuum.o3.pol.e200_10000.b4.p12.relx.s10396905069491.m420.filtered.binnedpolarization.11D.h5 <br />
  
Note: the second response file is used for polarization analysis and has fewer energy bins.

 **Data Files:** <br />
 For reference, below is a list of the individual source simulation files that are included in the mock dataset:
 GRB_bn081207680_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_bn090424592_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_bn100612726_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_bn110605183_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_bn131122490_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_bn140329295_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_bn161004964_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_bn170405777_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_bn180504136_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_bn180703876_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_bn080802386_flux150_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_MGF051103_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_MGF070201_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_MGF070222_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_MGF180128A_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_MGF200415A_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_MGF231115A_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 MgtBurst_bright_complex_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 
 **Input Models:** <br />
 All input models can be found [here](https://github.com/cositools/cosi-sim/tree/main/cosi_sim/Source_Library/DC3/sources/GRBs).
 
The simulated GRBs occur randomly within the 3-month orientation file, with their positions chosen such that they have incidence angles under $60^\circ$. The spectra are described with Band functions, and the parameters are based on fits to GBM data. Likewise, the lightcurves are also from GBM data. The fluxes were chosen such that some GRBs have a minimum detectable polarization (MDP) below their polarization fraction, and some have a MDP above. The models are specified below, including the polarization fraction (PF), and the polarization angle (PA) given in IAU convention. We also provide burst times, which is needed for the analysis:
 - bn081207680: PF = 0, PA = $0^\circ$, t = 1836496300.0 s
 - bn090424592: PF = 0.1, PA = $110^\circ$, t = 1837507002.0 s
 - bn100612726: PF = 0.2, PA = $35^\circ$, t = 1839617230.0 s
 - bn110605183: PF = 0.3, PA = $50^\circ$, t = 1841896404.0 s
 - bn131122490: PF = 0.4, PA = $175^\circ$, t = 1842123855.0 s
 - bn140329295: PF = 0.5, PA = $95^\circ$, t = 1837652924.0 s
 - bn161004964: PF = 0.6, PA = $10^\circ$, t = 1842948485.0 s
 - bn170405777: PF = 0.7, PA = $160^\circ$, t = 1841915858.0 s
 - bn180504136: PF = 0.8, PA = $45^\circ$, t = 1836985181.0 s
 - bn180703876: PF = 0.9, PA = $25^\circ$, t = 1838652949.0 s
 - bn080802386: PF = 0.8, PA = $90^\circ$, t = 1835493492.2 s <br />
 
 Information for the MGFs, including reference papers (PF = 1, PA = $90^\circ$ for all sources):
 - MGF051103 ([Svinkin+21](https://www.nature.com/articles/s41586-020-03076-9)): t = 1835533723.498 s
 - MGF070201 ([Ofek+08](https://www.nature.com/articles/s41586-020-03076-9)): t = 1835537496.0 s
 - MGF070222 ([Svinkin+16](https://www.nature.com/articles/s41586-020-03076-9)): t = 1835491681.0 s
 - MGF180128A ([Trigg+24](https://www.nature.com/articles/s41586-020-03076-9)): t = 1835488380.0 s
 - MGF200415A ([Svinkin+21](https://www.nature.com/articles/s41586-020-03076-9)): t = 1835488530.0 s
 - MGF231115A ([Trigg+25](https://www.nature.com/articles/s41586-020-03076-9)): t = 1835533696.0 s
 
 Information for magnetar short burst:
 - MgtBurst_bright_complex: no polarization, t = 1835640345.022513 s
   - SGR 1935+2154 ([Li+21](https://www.nature.com/articles/s41550-021-01302-6)) - a bright burst with a complex light curve.   


</details>

<details>
  <summary>Positrons</summary>
  
## Positron Data Challenges
The Key Objectives for the COSI positron science goal are:
1. Identify potential individual positron sources in the Galaxy
2. Determine the scale-height of the Galactic disk
3. Study the annihilation mechanism and the differences between the Galactic disk and the Galactic bulge
4. Investigate the energy at which positrons are created

### DC4 Goals:
- Identify individual positron sources
- Determine the scale height of the 511 keV disk, and cross-correlate the measured distribution with 26Al map (1809 keV emission) to constrain propagation distances
- Determine line width and relative flux of oPs and 511 keV line for different regions of the Galaxy 
- Find detection significance of in-flight annihilation
  
**⚠️ Pending:** Need to update info about included sources and models. <br />
We have developed models for the 511 keV and ortho-positronium emission from <sup>26</sup>Al and <sup>44</sup>Ti $\beta$+ decay in our Galaxy, which includes the propagation of positrons and Galactic rotation to give a spatially-dependent annihilation spectrum, with three different bulge models that agree with INTEGRAL/SPI measurements. We have also simulated 3 extragalactic sources, 4 globular clusters, and the Vela supernova remnant, as detailed below. Note, these individual sources only have the 511 keV line emission and no contribution from the ortho-positronium continuum. Information for how to access the mock dataset and all other needed files is provided in the [data-products](data-products/README.md) page.

**The challenges will use the following detector response files:** 
- Response511.o4.e509_513.s20881894470591.m2555.filtered.nonsparse.binnedimaging.imagingresponse.h5 <br />
- ResponseContinuum.o3.e100_10000.b10log.s10396905069491.m2284.filtered.nonsparse.binnedimaging.imagingresponse.h5 <br />
- extended_source_response_511_merged.h5.gz (precomputed 511 extended source response file)
- extended_source_response_continuum_merged.h5.gz (precomputed continuum extended source response file)

The line response is for analyzing the 511 keV line emission, and the continuum response is for analyzing the orthopositronium continuum. Currently, these two components cannot be analyzed simultaneously, as desribed in the [Known Caveats and Limitations](#known-caveats-and-limitations) section. The pre-computed extended source responses should be used for imaging in Galactic coordinates and the 511 spectral fit notebook when analyzing extended sources (i.e. positrons from <sup>26</sup>Al or <sup>44</sup>Ti).

### Positrons from <sup>26</sup>Al and <sup>44</sup>Ti

**Data Files:** <br />
Positrons_from_26Al_line_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
Positrons_from_26Al_cont_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
Positrons_from_44Ti_line_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
Positrons_from_44Ti_cont_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
Vela_SNR_511_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

**Galactic Input Models:**  <br />
The spatial distribution of positrons from <sup>26</sup>Al and <sup>44</sup>Ti decay is derived from the propagation of positrons in our Galaxy, where the initial positions of positrons follows the NE2001 model from [Cordes & Lazio 2002](https://arxiv.org/abs/astro-ph/0207156). The model fits the distribution of massive stars in our Galaxy, with an assumed fraction of 2% for both <sup>26</sup>Al and <sup>44</sup>Ti in the bulge. The positron propagation method is described in [Alexis et al. 2014](https://ui.adsabs.harvard.edu/abs/2014A%26A...564A.108A/abstract). The positron rate due to <sup>26</sup>Al is set to $2.6 \times 10^{42}$ e+/s based on INTEGRAL/SPI measurements at 1809 keV [Diehl et al. 2006](https://ui.adsabs.harvard.edu/abs/2006Natur.439...45D/abstract),  and the rate from <sup>44</sup>Ti decay is assumed to be $3\times 10^{42}$ e+/s (see section 2.3 of [Alexis et al. 2014](https://ui.adsabs.harvard.edu/abs/2014A%26A...564A.108A/abstract)).

The spectrum for these diffuse models have two separate components: the 511 keV annihilation line and the ortho-positronium continuum (i.e. files containing “cont”). These were obtained from the model of [Guessoum et al 2005](https://ui.adsabs.harvard.edu/abs/2005A%26A...436..171G/abstract) with a computed spectrum for each phase of the interstellar medium, based on the spatial distribution described above. The spectral model was corrected by the Galactic rotation using the model of [Fich, Blitz and Stark 1989](https://ui.adsabs.harvard.edu/abs/1989ApJ...342..272F/abstract) for R > 3 kpc and a solid rotation model for R < 3 kpc.

The imaged spatial distribution should resemble the initial model, shown here for the 511 keV emission from <sup>26</sup>Al decays, and the resulting measured full-Galaxy 511 keV flux should be $3.2 \times 10^{-4}\ \mathrm{ph \ cm^{-2} \ s^{-1}}$ for <sup>26</sup>Al, and $3.7 \times 10^{-4}\ \mathrm{ph \ cm^{-2} \ s^{-1}}$ for <sup>44</sup>Ti. The flux in the inner Galactic region ($\pm$ 30 deg) should be $1.3 \times 10^{-4}\ \mathrm{ph \ cm^{-2} \ s^{-1}}$ for <sup>26</sup>Al, and $1.4 \times 10^{-4}\ \mathrm{ph \ cm^{-2} \ s^{-1}}$ for <sup>44</sup>Ti. 

<p align="center">
<img width="700"  src="static/PositronsDC3_Al-26_511emission.png">
</p>

<div align="left">

**Vela Input Models:**  <br />
The 511 keV photon flux from the Vela SNR is estimated assuming that all positrons from $1 \times 10^{-4}$ $M_\odot\$ of <sup>44</sup>Ti decay are trapped within the remnant by magnetic fields. We assume a 511 keV flux of $3.5 \times 10^{-4} \mathrm{ph \ cm^{-2} \ s^{-1}}$ and a spatial distribution the follows total ROSAT all-sky survey X-ray emission. This is NOT a point source, but ~8 deg in extent.

### Bulge Emission
**Data Files:** <br />
Narrow_Bulge_511_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
Broad_Bulge_511_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
NFW_511_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

We've simulated 3 bulge models seperate from the disk but recommend you add either the NFW or narrow + broad bulge to the disk simulations above for a representative all-sky distribution. The broad bulge and narrow bulge spatial models are based on the Boxy bulge ([Freudenreich 1998](https://ui.adsabs.harvard.edu/abs/1998ApJ...492..495F/abstract)) and nuclear bulge ([Launhardt et al. 2002](https://ui.adsabs.harvard.edu/abs/2002A%26A...384..112L/abstract)). These are consistent with the INTEGRAL/SPI spatial model components referred to as the broad and narrow bulge in ([Skinner et al. 2014](https://pos.sissa.it/228/054/) and [Siegert et al. 2016](https://ui.adsabs.harvard.edu/abs/2016A%26A...586A..84S/abstract)). The NFW<sup>2</sup> model is derived from dark matter models and is based on the spatial distribution presented in ([Siegert et al. 2024](https://ui.adsabs.harvard.edu/abs/2024MNRAS.528.3433S/abstract)). Each bulge model has a 511 keV component and ortho-Ps continuum, as expected from low-energy positron annihilation ($f_{Ps}$ ~ 1). Images of the narrow, broad, and NFW<sup>2</sup> models are shown below. 

<p float="left">
  <img src="static/PositronDC3_NarrowBulge.png" width="300" />
  <img src="static/PositronDC3_BroadBulge.png" width="300" /> 
  <img src="static/PositronDC3_NFWBulge.png" width="300" />
</p>

### Extragalactic Sources

**Data Files:** <br />
LMC_Gaussian_511_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
LMC_Gaussian_511_x100_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
M31_Gaussian_511_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
M31_Gaussian_511_x100_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
Virgo_Gaussian_511_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br /> 
Virgo_Gaussian_511_x100_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

**Input Models:**  <br />
The fluxes for extragalactic sources (LMC, M31, Virgo) are estimated by assuming that the 511 keV photon flux is proportional to the stellar mass of the source. Using a Milky Way 511 keV flux of $2.8 \times 10^{-3} \  \mathrm{ph \ cm^{-2} \ s^{-1}}$ ([Siegert+16](https://www.aanda.org/articles/aa/full_html/2016/02/aa27510-15/aa27510-15.html)) and total stellar mass of $5.4 \times 10^{10} \  M_\odot$ ([McMillan+16](https://academic.oup.com/mnras/article/465/1/76/2417479)), we assume the 511 keV flux of each extragalactic source follows the same ratio. The stellar masses are:

The stellar masses are: <br />
LMC: $1 \times 10^{10} \ M_\odot\$ ([Erkal+19](https://academic.oup.com/mnras/article/487/2/2685/5491315)) <br />
M31: $1.25 \times 10^{11} \ M_\odot\$ ([Tamm+12](https://www.aanda.org/articles/aa/full_html/2012/10/aa20065-12/aa20065-12.html)) <br />
Virgo: $1.2 \times 10^{14} \ M_\odot\$ ([Fouque+01](https://www.aanda.org/articles/aa/abs/2001/33/aa1326/aa1326.html)) <br />

We also include each source at 100x the nominal flux, in order to ensure that they are above COSI's 511 keV line sensitivity.

### Globular Clusters

**Data Files:** <br />
Globular_Cluster_Tuc_47_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
Globular_Cluster_Omega_Cen_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
Globular_Cluster_NGC_6397_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
Globular_Cluster_NGC_6121_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

**Input Models:**  <br />
The 511 keV photon flux for the brightest 4 globular clusters is estimated based on the 0.1 - 100 GeV luminosity from the Globular clusters, and the nuclear bulge and boxy bulge emission in the Milky Way [Bartels et al 2018a](https://ui.adsabs.harvard.edu/abs/2018NatAs...2..819B/abstract). The GeV luminosity of the Bulge is compared to the 511 keV luminosity of the bulge [Bartels et al 2018b](https://ui.adsabs.harvard.edu/abs/2018MNRAS.480.3826B/abstract). This GeV luminosity vs 511 keV luminosity correlation is applied to the GeV excess observed from globular clusters [Zhang et al 2016](https://ui.adsabs.harvard.edu/abs/2016MNRAS.459...99Z/abstract) in the Galaxy to estimate the 511 keV flux of the globular clusters. The flux values shown here are 3x the values estimated from the correlation in order to make them within COSI's sensitivity limit within the 3 month observation period.

The simulated 511 keV flux for the GCs are: <br />
$4.17 \times 10^{-5} \  \mathrm{ph \ cm^{-2} \ s^{-1}}$ for Tuc 47 <br />
$5.01 \times 10^{-5} \  \mathrm{ph \ cm^{-2} \ s^{-1}}$ for Omega Cen <br />
$4.02 \times 10^{-5} \  \mathrm{ph \ cm^{-2} \ s^{-1}}$ for NGC 6397 <br />
$6.96 \times 10^{-5} \  \mathrm{ph \ cm^{-2} \ s^{-1}}$ for NGC 6121 <br />

<p align="center">
<img width="700"  src="static/PositronsDC3_GCsources.png">
</p>

<div align="left">
  
</details>

<details>
  <summary>Nucleosynthesis</summary>
  
## Nucleosynthesis Data Challenges
The Key Objectives for the COSI nucleosynthesis science goal are:
1. Reveal the history of core collapse supernova activity in the Galaxy
2. Determine the role of the evolution of massive stars in creating the elements
3. Detect nuclear line emission from young supernova remnants in the Galaxy
4. Probe explosion physics in the core of supernovae

### DC4 Goals:
- Estimate the Galactic 60Fe/26Al ratio
- Determine the mass of 26Al in three massive star groups
- Sky survey of 44Ti point sources
- Spectral analysis of 44Ti in Cas A

We have modeled the diffuse emission from <sup>26</sup>Al and <sup>60</sup>Fe in our Galaxy assuming they follow the distribution of massive stars and are in agreement with INTEGRAL/SPI observations. We have also included a model for the <sup>26</sup>Al and <sup>60</sup>Fe emission from the Cygnus region. Additionally, we simulated extended <sup>26</sup>Al and <sup>60</sup>Fe emissions from the Orion Eridanus superbubble and the Upper Scorpius part of the Scorpius-Centaurus association. Finally, we simulated <sup>44</sup>Ti decay from Tycho, SN1987A, Kepler, G1903, Vela Jr., and Cassiopeia A. Information for how to access the mock dataset and all other needed files is provided in the [data-products](data-products/README.md) page.

**The challenges will use the following detector response files:** 
- Response26Al.o4.e1805_1812.s10036231691364.m1045.filtered.nonsparse.binnedimaging.imagingresponse.h5
- extended_source_response_Al26_merged.h5.gz
- Response60FeHigh.o4.e1329_1336.s10201526728102.m1287.filtered.nonsparse.binnedimaging.imagingresponse.h5
- Response60FeLow.o4.e1170_1176.s9552269354945.m1188.filtered.nonsparse.binnedimaging.imagingresponse.h5
- extended_source_response_Fe60_low_merged.h5.gz
- extended_source_response_Fe60_high_merged.h5.gz
- Response44Ti.o4.e1154_1160.s9607532021290.m1215.filtered.nonsparse.binnedimaging.imagingresponse.h5
- extended_source_response_Ti44_merged.h5.gz 

Each gamma-ray line has a different response, and the response files are labeled with each isotope. Note that <sup>60</sup>Fe has two separate response files for the two decay lines at 1173 keV and 1332 keV. Currently, these two line components cannot be analyzed simultaneously using a binned analysis, as desribed in the [Known Caveats and Limitations](#known-caveats-and-limitations) section. However, an unbinned analysis might be suitable. The pre-computed extended source responses should be used for imaging in Galactic coordinates and the spectral fit notebook when analyzing extended sources (i.e. <sup>26</sup>Al or <sup>60</sup>Fe).

### Input Models

**<sup>26</sup>Al and <sup>60</sup>Fe diffuse emission:**  <br />
The spatial distribution of the 1809 keV line from <sup>26</sup>Al decay and the 1173 keV and 1332 keV lines from <sup>60</sup>Fe decay in our Galaxy follow the NE2001 model from [Cordes & Lazio 2002](https://arxiv.org/abs/astro-ph/0207156). The model fits the distribution of massive stars in our Galaxy, with an assumed fraction of 2% for both <sup>26</sup>Al and <sup>60</sup>Fe in the Galactic bulge. This value is a compromise between SPI observations and results of studies of star formation rate in this region. The flux of <sup>26</sup>Al is consistent with measurements from SPI with a total mass of 2.7 $M_\odot\$ in our Galaxy ([Diehl et al. 2006](https://ui.adsabs.harvard.edu/abs/2006Natur.439...45D/abstract)). The flux of <sup>60</sup>Fe is computed assuming a total mass of 3.5 $M_\odot\$ (see [Wang+20](https://ui.adsabs.harvard.edu/abs/2020ApJ...889..169W/abstract) and [Siegert+23](https://ui.adsabs.harvard.edu/abs/2023A%26A...672A..54S/abstract)). The shape of the line in each spatial bin takes into account the turbulence of the interstellar medium and the Galactic rotation using the model of [Fich, Blitz and Stark 1989](https://ui.adsabs.harvard.edu/abs/1989ApJ...342..272F/abstract) for R > 3 kpc and a solid rotation model for R < 3 kpc.
   
**Cygnus Region:**  <br />
The characteristics of the <sup>26</sup>Al emission from the Cygnus region are obtained from INTEGRAL/SPI observations described in [Martin+09](https://ui.adsabs.harvard.edu/abs/2009A%26A...506..703M/abstract), while predictions for the <sup>60</sup>Fe lines are derived from the calculation of [Martin+10](https://ui.adsabs.harvard.edu/abs/2010A%26A...511A..86M/abstract). The spatial distribution, for both <sup>26</sup>Al and <sup>60</sup>Fe, is modeled with a $3^\circ$ Gaussian shape centered at $l = 81^\circ, b = 1^\circ$. The 1.8 MeV line flux is $3.9 \times 10^{-5} \ \mathrm{ph \ cm^{-2} \ s^{-1}}$, and it is centered at 1808.8 keV with a width of 1.6 keV FWHM due to the interstellar turbulence. The flux of <sup>60</sup>Fe is $2.7 \times 10^{−6}\ \mathrm{ph \ cm^{-2} \ s^{-1}}$ for both lines, and centroids are 1173.3 keV and 1332.6 keV with a width of 1.04 keV and 1.18 keV FWHM, respectively.
   
**Orion Eridanus superbubble:**  <br />
Extended 26Al and 60Fe source emissions from the Orion Eridanus superbubble. Flux and diffusion on the Myr timescale have been estimated using the age and launch velocities. The distribution is modeled as a FarFieldAssymetricGaussian (2D elliptical projections on the sky) with 0 degree rotation with respect to latitude. The spectra are modeled as Gaussians with 200 km/s broadening.

**Scorpius-Centaurus association:**  <br />
Extended 26Al and 60Fe source emissions from the Upper Scorpius part of the Scorpius-Centaurus association. Flux and diffusion on the Myr timescale have been estimated using the age and launch velocities. The distribution is modeled as a FarFieldAssymetricGaussian (2D elliptical projections on the sky) with 0 degree rotation with respect to latitude. The spectra are modeled as Gaussians with 200 km/s broadening.

**Cas A:**  <br />
Based on Grefenstette et al. 2017. NuSTAR observed the Cassiopeia A supernova remnant for 2.4 Ms. This model simulates the spectral structure that will be observable by COSI after spatially-integrating the NuSTAR observations. The photopeak and Doppler-shifts have been shifted from 68 keV to 1157 keV. As spatial-spectral mixing effects were not accounted for, the sum of clump fluxes does not match the total flux from the source. The total flux has been scaled to $3 \times 10^{−4}\ \mathrm{ph \ cm^{-2} \ s^{-1}}$ (10x the value reported in Weinberger et al. 2020). The minimum clump broadening is set to 5 keV (1-sigma), or equivalently 1300 km/s to match NuSTAR’s spectral resolving power. 

**Kepler:** <br />
Point-like 44Ti emissions from a moderate-latitude source. Doppler broadening is set to 4000 km/s or 15.4 keV (1-sigma). Flux is set to 1.6x of the upper limit in Weinberger et al. 2020. The source is located at $l = 4.5^{\circ}, b=6.8^{\circ}$.

**G1903:** <br />
Point-like 44Ti emissions from the Galactic center. Doppler broadening is set to 4000 km/s or 15.4 keV (1-sigma). Flux is set to 1.6x of the upper limit in Zoglauer et al. 2015. The source is located at $l = 1.9^{\circ}, b=0.3^{\circ}$.

**SN1987A:** <br />
Point-like 44Ti emissions from a high-latitude source. Doppler broadening is set to 4000 km/s or 15.4 keV (1-sigma). Flux is set to 2x of the upper limit in Boggs et al. 2015. The source is located at $l = 279.7^{\circ}, b=-31.9^{\circ}$.

**Tycho:** <br />
Point-like 44Ti emissions from an equatorial source away from dust obscuration. Doppler broadening is set to 4000 km/s or 15.4 keV (1-sigma). Flux is set to 1.6x of the upper limit in Lopez et al. 2015. The source is located at $l = 120.1^{\circ}, b=1.4^{\circ}$. 

**Vela Jr.:** <br />
Point-like 44Ti emissions from an equatorial source away from dust obscuration. Doppler broadening is set to 4000 km/s or 15.4 keV (1-sigma). Flux is set to 1.6x of the upper limit in Weinberger et al. 2020. The source is located at $l = 266.3^{\circ}, b=-1.2^{\circ}$.
</details>

<details>
  <summary>Galactic</summary>
  
## Galactic Data Challenges
There is one Key Objective for Galactic science with COSI:
1. Constrain geometries and emission processes in Galactic black holes <br />

While the main science goals for COSI are not directly related to many Galactic sources, there is no doubt that COSI’s unique energy range will bring compelling new observations. 

### DC4 Goals:
- Constrain geometries and emission processes in Galactic black holes through polarization and spectral analyses
- Perform phase resolved analysis of variable Galactic sources
- Perform imaging and spectral analysis of Galactic point sources
- Make measurement of Galactic diffuse continuum

The DC4 mock dataset includes 12 Galactic point sources: 2 steady-state sources (GRS 1758-258, 1E1740.7-2942) for spectral analysis, 5 transient/variable sources (Crab, PSR B1259-63, PSR J1846−0258, Cyg X3, and LS 5039), and 5 sources with polarization (Cyg-X1, MAXI J1820+070, MAXI J1348-630, 1RXS J170849.0-400901, and a genaric magnetar). Note that all of the polarized sources are variable as well, and the Crab is polarized (in addition to being a periodic source). The DC4 mock dataset also includes the Galactic diffuse continuum emission. Information for how to access the mock dataset and all other needed files is provided in the [data-products](data-products/README.md) page.

**The challenges will use the following detector response files:** <br />
- ResponseContinuum.o3.e100_10000.b10log.s10396905069491.m2284.filtered.nonsparse.binnedimaging.imagingresponse.h5 <br />
- ResponseContinuum.o3.pol.e200_10000.b4.p12.relx.s10396905069491.m420.filtered.binnedpolarization.11D.h5 <br />
- extended_source_response_continuum_merged.h5.gz <br />

Note: the second response file is used for polarization analysis and the extended source response should be used to analyze the Galactic diffuse continuum when imaging or performing the spectral fit.

### Steady-state sources

**GRS 1758-258 Input Models:**  <br />
The spectral model for the microquasar GRS 1758-258 near the Galactic center is based on the best fit comptonization model of epoch2 from [Pottschmidt+06](https://arxiv.org/pdf/astro-ph/0509006.pdf). This is the same model as used in DC2 and DC3. The source is located at $l = 4.51^{\circ}, b=-1.36^{\circ}$, with a flux of $3.495 \times 10^{-3}\ \mathrm{ph \ cm^{-2} \ s^{-1}}$. 

**1E1740.7-2942 Input Models:**  <br />
The spectral model for microquasar 1E1740.7-2942 (also known as the Great Annihilator) is one of the best fit models of INTEGRAL data obtained by [Bouchet+09](https://iopscience.iop.org/article/10.1088/0004-637X/693/2/1871/pdf). Specifically, we use the "compow" model, which is a thermal comptonization + powerlaw model. The source is located close to the Galactic center at $l = 359.1^{\circ}, b = -0.1^{\circ}$ with a total integrated flux of $4.23 \times 10^{-3}\ \mathrm{ph \ cm^{-2} s^{-1}}$.

### Transient/Variable sources 

**Crab Input Model:**  <br />
For DC4 we simulated a simplified Crab model with 4 key components: nebula, peak 1, peak 2, and bridge. The nebula is simulated with a steady state and has polarization degree and angle (Galactic coordinates) of 0.40 and 160 deg, respectively. The remaining components are for the pulsar (peak 1, peak 2, and bridge), and they share the same polarization fraction and degree: 0.2 and 145 deg.

**PSR B1259-63 Input Model:**  <br />
PSR B1259-63 is a binary gamma-ray system consisting of a radio pulsar and a massive Be-type star. The next periastron passage will be November 19th, 2027, making this a prime target for COSI. The model for DC3 is based on the work in [Abdo+11](https://doi.org/10.1088%2F2041-8205%2F736%2F1%2Fl11) (see Model 1 in the bottom of Figure 5). The flare is simulated as a constant emission for 30 days (T > 1839487305.0). We use the nominal flux value from [Abdo+11](https://doi.org/10.1088%2F2041-8205%2F736%2F1%2Fl11), which is $6.13 \times 10^{-4} \ \mathrm{ph \ cm^{-2} s^{-1}}$. The source is located at $l = 304.2^{\circ}, b = -0.99^{\circ}$.

**PSR J1846−0258 Input Model:**  <br />
PSR J1846-0258 is a bright pulsar with strong magnetic field, located at (l, b)= (29.71195, -0.24012). This pulsar has a rotation period of 0.327 s. The pulse profile and spectrum are taken from [Kuiper+18](https://doi.org/10.1093/mnras/stx3128) (Fig. 3 and Sec. 4.2.2).  

**Cyg X3 Input Models:**  <br />
For DC4, Cyg X-3 ($l = 79.8^{\circ}, b = 0.7^{\circ}$) is modeled using a single transition-state spectrum based on the best-fit eqpair model from INTEGRAL data from [Cangemi+21](https://www.aanda.org/articles/aa/pdf/2021/01/aa37951-20.pdf). The source is simulated at its nominal flux in the transition state for the full 3-month exposure.

**LS 5039 Input Models:**  <br />
LS 5039 is a TeV gamma-ray binary system with an orbital period of about 3.9 days. MeV gamma-ray emission was reported by COMPTEL ([Collmar+14](http://adsabs.harvard.edu/abs/2014A%26A...565A..38C)). The input spectrum was generated by interpolating the X-ray spectrum ([Yoneda+21](https://iopscience.iop.org/article/10.3847/1538-4357/ac0ae1/meta)) and MeV spectrum ([Collmar+14](http://adsabs.harvard.edu/abs/2014A%26A...565A..38C)), averaged over the orbital period. Orbital modulation is based on the orbital light curve from [Collmar+14](http://adsabs.harvard.edu/abs/2014A%26A...565A..38C). 

### Polarized Sources

**Cyg X1 Input Models:**  <br />
The spectral model for Cyg X1 ($l = 71.3^{\circ}, b = 3.1^{\circ}$) is based on the best-fit eqpair model of time averaged INTEGRAL data ([Cangemi+21]( https://ui.adsabs.harvard.edu/abs/2021A%26A...650A..93C/abstract)). We assume that the source is in the hard state for the 3 months of exposure. The hard state polarization model is based on the measurements of [Rodriguez+2015](https://ui.adsabs.harvard.edu/abs/2015ApJ...807...17R/abstract). At low energy (0.1 - 0.4 MeV) the polarization fraction is 5% with an angle of 40 degrees (IAU convention). At high energy (0.4 - 10 MeV) the polarization fraction is 75% with the same angle. 

**MAXI J1820+070 and J1348-630 Input Models:**  <br />
The spectral models for two black hole X-ray binaries, MAXI J1820+070 and MAXI J1348-630, are based on INTEGRAL data (Fig 3 of [Cangemi+23](https://ui.adsabs.harvard.edu/abs/2023A%26A...669A..65C/abstract)), in the hard state. The polarimetric models corresponds to the measurements shown in Table 3 of the same paper. The input polarization models are divided into a low energy component (0.1 - 0.4 MeV) and a high energy component (0.4 - 10 MeV). MAXI J1820+070 and  MAXI J1348-630 remained in the hard state for 60 days and 7 days, respectively, and for DC4 we have the sources 'on' for these respective times and off for the rest of the time. Therefore, MAXI J1820+070 has a nominal flux of $1.4 \times 10^{-1}\ \mathrm{ph \ cm^{-2} \ s^{-1}}$ (0.1 - 0.4 MeV) and $6.0 \times 10^{-3}\ \mathrm{ph \ cm^{-2} \ s^{-1}}$ (0.4 - 10 MeV) until T = 1840671300, and then drops to zero. MAXI J1348-630 has a flux of $8.6 \times 10^{-2}\ \mathrm{ph \ cm^{-2} \ s^{-1}}$ (0.1 - 0.4 MeV) and $2.3 \times 10^{-3}\ \mathrm{ph \ cm^{-2} \ s^{-1}}$ (0.4 - 10 MeV) until T = 1836092100.

**1RXS J170849.0-400901 and a genaric magnetar:**  <br />
DC4 features two magnetars:
1. 1RXS J170849.0-400901 
    * GLON, GLAT: 346.47938142, 0.03838608
2. A generic magnetar with slightly different parameters than 1RXS J1780849.0-400901
    * GLON, GLAT: 250, 0.03838608
    
The models that we use are based on [Hartog+08](https://www.aanda.org/articles/aa/abs/2008/37/aa09772-08/aa09772-08.html).

The spectrum is a log parabola in the MeV energy range:

```
spec = norm * var**(-alpha-beta*np.log(var)),
where var = x/pivot
```

The assumed parameters for 1RXS are:
* alpha = 1.637
* beta = 0.261
* norm = 1.68e-6 $\mathrm{ph \ cm^{-2} \ s^{-1} \ keV^{-1}}$
* pivot = 143.276 keV

The assumed parameters for the generic magnetar are the same, except for beta which is multiplied by 2.

The polarization is assumed energy independent in the COSI band with a phase-integrated polarization degree of 80% (PA = 30 degrees) for 1RXS and 40% (PA = 75 degrees) for the genaric magnetar.

The Lightcurves for both 1RXS and the genearic magnetar are periodic with the following parameters:
* Period: P = 11.00502461 s
* Period derivative: Pdot = 1.95E-11 s/s
* Pulsed Fraction: PF = 0.5

The Pulsed fraction is defined as (Fmax - Fmin)/(Fmax + Fmin), with F being the flux.

### Galactic diffuse continuum

**Input Models:**  <br />
The Galactic diffuse continuum emission is modeled using the v57 release of the GALPROP cosmic ray (CR) propagation and interstellar emissions framework [(Porter+22)](https://iopscience.iop.org/article/10.3847/1538-4365/ac80f6). GALPROP self-consistently calculates spectra and abundances of Galactic CR species and associated diffuse emissions (gamma rays, X-rays, and radio) in 2D and 3D. The v57 release includes a set of steady-state emission model examples that reproduce the latest CR data. There are six models in total, categorized according to the CR source and interstellar radiation field (ISRF) model used for the prediction. There are 3 CR source models (SA0, SA50, SA100) and two ISRF models (R12, F98). The CR source density models are based on the distribution of injected CR power, with SA0 describing an axisymmetric disk (following the radial distribution of pulsars), SA50 describing a 50/50% split of the injected CR luminosity between disk-like and spiral arms, and SA100 describing pure spiral arms. All models have the same exponential scale height of 200 pc. The two ISRF models employ different spatial densities for both the stars and the dust but produce intensities very similar to those of the data for near- to far-infrared wavelengths at the location of the solar system (see [Porter+17](https://iopscience.iop.org/article/10.3847/1538-4357/aa844d) and references therein). For the neutral gas distributions (atomic and molecular), a 3D model from [Johannesson+18](https://iopscience.iop.org/article/10.3847/1538-4357/aab26e) is employed. These GALPROP models include the total emission, which is dominated by inverse Compton radiation, but also has a small contribution from Bremsstrahlung towards the upper energy bound. As our representative case, for DC3 we simulate the SA100-F98 model. 

</details>

<details>
  <summary>Extragalactic</summary>
  
## Extragalactic Data Challenges
There is one key objective for extragalactic science with COSI:
1. Constrain geometries and emission processes in Active Galactic Nuclei (AGN) <br />

While the main science goals for COSI are not directly related to many extragalactic sources, there is no doubt that COSI’s unique energy range will bring compelling new observations. 

### DC4 Goals:
- Constrain geometries and emission processes in Active Galactic Nuclei (AGN)
- Spectral, time-resolved analysis of blazar flares
- Spectral analysis of radio-quiet AGN to constrain the properties of the corona
- Detection and Characterization of the MeV background

We have simulated 6 extragalactic sources: Cen A (steady state, polarized), NGC 1068 (steady state), NGC 4151 (steady state), 4C+21.35 (flare), 4C 71.07 (polarized), and 3C 454.3 (variable, polarized). In addition, we also simulated the extragalactic MeV background, which is part of the standard background model. Information for how to access the mock dataset and all other needed files is provided in the [data-products](data-products/README.md) page.

**All challenges should use the same detector response files:** <br />
- ResponseContinuum.o3.e100_10000.b10log.s10396905069491.m2284.filtered.nonsparse.binnedimaging.imagingresponse.h5 <br />
- ResponseContinuum.o3.pol.e200_10000.b4.p12.relx.s10396905069491.m420.filtered.binnedpolarization.11D.h5 <br />

Note: the second response file is used for polarization analysis.

### Steady state sources

**NGC 1068 Input Models:**  <br />
NGC 1068 is a nearby, bright Seyfert 2 AGN. In DC4, the source is described using a composite spectral model consisting of a thermal cutoff power law and an additional non-thermal power-law tail. The thermal component, representing Comptonization by hot coronal electrons, is based on the spectral analysis of [Bauer+2015](https://ui.adsabs.harvard.edu/abs/2015ApJ...812..116B/abstract), while the non-thermal component follows the treatment of Inoue et al. (2008) and accounts for a possible high-energy tail. The source is located at Galactic coordinates $(l,b) = (172.10^\circ, -51.93^\circ)$, with an integrated photon flux of $1.61 \times 10^{-3}\ \mathrm{ph\ cm^{-2}\ s^{-1}}$ over the 100 keV–10 MeV energy range. The adopted parameters for the thermal component are a photon index $\Gamma = 1.92$, a high-energy cutoff $E_{\mathrm{cut}} = 200\ \mathrm{keV}$, and a normalization of $0.308\ \mathrm{keV^{-1}\ s^{-1}\ cm^{-2}}$ at 1 keV. The non-thermal component is characterized by a photon index $\Gamma = 3.8$ and a normalization of $91.18\ \mathrm{keV^{-1}\ s^{-1}\ cm^{-2}}$ at 1 keV. 

**NGC 4151 Input Models:**  <br />
NGC 4151 is one of the brightest and most extensively studied Seyfert galaxies. In DC4, the source is described using a composite spectral model consisting of a thermal cutoff power law and a non-thermal power-law tail. The thermal component, representing Comptonization by hot coronal electrons, is based on the spectral analysis of Lubinski et al. (2010), while the non-thermal component follows Inoue et al. (2008) and accounts for a possible high-energy tail. The source is located at Galactic coordinates $(l,b) = (155.08^\circ, 75.06^\circ)$, with an integrated photon flux of $1.88 \times 10^{-3}\ \mathrm{ph\ cm^{-2}\ s^{-1}}$ over the 100 keV–10 MeV energy range. The adopted parameters for the thermal component are a photon index $\Gamma = 1.75$, a high-energy cutoff $E_{\mathrm{cut}} = 200\ \mathrm{keV}$, and a normalization of $0.149\ \mathrm{keV^{-1}\ s^{-1}\ cm^{-2}}$ at 1 keV. The non-thermal component is characterized by a photon index $\Gamma = 3.8$ and a normalization of $142.8\ \mathrm{keV^{-1}\ s^{-1}\ cm^{-2}}$ at 1 keV. 

### Transient source

**4C+21.35 Input Models:**  <br />
We have included a simulation of quasar 4C+21.35 which has both a quiescent state simulation (noflare) and a flaring state in separate files. The lightcurve describing the quiescent flux and the flare is based on Fermi-LAT data, where the flaring state is initiated when the reported flux is 3x greater than the 16-years average flux. The normalization is derived from the integrated flux in the COSI energy band, based on an extrapolation of the Fermi-LAT log parabola function. The two states come with two different spectra: both powerlaws with different indices, where the non-flaring state has and index of 1.6, and the flaring state has an index of 2.5. The flaring state has variable flux between 1838089680 < T < 1840422465, and is zero elsewhere, and the non-flaring state is the opposite, as seen in the light curve below. Combine these files to represent a 4C+21.35 flare with a different spectral model in the flaring state.

<p align="center">
<img width="500"  src="static/ExtragalacticDC3_4C_LC.png">
</p>

<div align="left">


### Polarized sources

**Cen A:**  <br />
Centaurus A is the nearest radio-loud active galaxy (distance of about 3.8 Mpc) and a well-studied misaligned AGN with prominent jets and lobes. The spectrum is modeled as a power law with photon index $\Gamma = 1.732$. The total integrated flux between 100 keV and 10 MeV is $1.97 \times 10^{-3} \ \mathrm{ph \ cm^{-2} \ s^{-1}}$. A polarization fraction of 20% is assumed, with a polarization angle of $150^\circ$ (Galactic coordinates). The source position is $(l, b) = (309.516^\circ, 19.417^\circ)$.

**4C 71.07:**  <br />
4C +71.07 is a high-redshift ($z \sim 2.2$) flat-spectrum radio quasar (FSRQ), characterized by strong jet emission aligned close to the line of sight. The spectral model is taken from Model A of [Tavecchio et al. 2025](https://ui.adsabs.harvard.edu/abs/2025A%26A...694L...3T/abstract). The integrated flux between 100 keV and 10 MeV is
$1.19 \times 10^{-3} \ \mathrm{ph \ cm^{-2} \ s^{-1}}$. A polarization fraction of 75% is assumed, with a polarization angle of $60^\circ$ (Galactic coordinates). The source position is $(l, b) = (143.54^\circ, 34.43^\circ)$.

**3C 454.3:**  <br />
3C 454.3 is one of the brightest and most variable gamma-ray blazars, known for dramatic flaring activity. The spectral model is based on [Bonnoli et al. 2011](https://ui.adsabs.harvard.edu/abs/2011MNRAS.410..368B/abstract) and includes both low and high emission states. The low state is assumed to be unpolarized. In the high state, a polarization fraction of 50% is adopted with a polarization angle of $45^\circ$ (Galactic coordinates). The source is located at $(l, b) = (86.11^\circ, -38.18^\circ)$.

</details>

<details>
  <summary>Dark Matter</summary>
  
## Dark Matter Data Challenges

While the main science goals for COSI are not directly related to dark matter, there is no doubt that COSI’s unique energy range will bring compelling new observations.  

### DC4 Goals:
- Set upper limits on DM signals in the absence of a signal.
- Extract signal from background in the case of a signal.
  
**Data Files:** <br />
Annihilation_eeg_NFW_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
Decay_gg_NFW_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

**Input Models:**  <br />
We consider two cases: (i) a dark matter (DM) particle decaying into two photons (gg), and (ii) two DM particles annihilating into an $e^+e^-$ pair with a final-state radiation (FSR) photon (eeg). We adopt NFW profile parameters from [Cirelli+10](https://arxiv.org/abs/1012.4515), and the fragmentation function for the eeg case is from [Coogan+19](https://arxiv.org/abs/1907.11846), assuming a scalar mediator. For these models, we take a DM mass of 3 MeV with a lifetime of $10^{28},\mathrm{s}$ for the decay scenario, and a DM mass of 30 MeV with an annihilation cross section of $10^{-25},\mathrm{cm^{3},s^{-1}}$ for the annihilation scenario.
  
</details>

## Known Caveats and Limitations
The items listed here are some of the priorities for DC5 development. These can be considered as extra/advanced challenges, and anybody is welcomed to work on them, with the ultimate goal of implementing the software solutions into cosipy. Also see the bottom of the [cosipy-intro](cosipy-intro) for a related discussion on the next steps of development.
 
- **It is not currently possible to simultaneously fit continuum and line components in binned analyses.** We have separate response files for different emission components (i.e. continuum, 511 keV, Aluminum-26, etc.), and with the current binned analysis setup in cosipy, the data binning needs to match the response binning, and thus only a single component can be analyzed at a time. Possible solutions to this include:
  - Creating a single response that combines multiple components
  - Creating a class that automatically matches an input model with the corresponding response
  - Reparameterizing the response in such a way that prevents this issue 
- **Methods need to be developed to determine the response for broadened and offset line emission in binned analyses.** These methods should utilize the baseline binned response files (e.g. 511 keV, Aluminum-26, Iron-60, etc.), and allow for analyzing any arbitrary line emission.
- **The background estimation tools need to be further tested and developed.** With DC4 we have methods for estimating continuum, line, and transient backgrounds. These methods need to be tested, stressed, and further developed. 
- **The way in which parameters are configured needs to be refined, and more callable scripts need to be added.** By callable scripts we are referring to command-line options that will perform common task, such as producing light curves and spectra.  
- **The tools still need to be further stressed to find limitations.** The COSI pipeline team has been rapidly developing the cosipy library in preparation for the satellite mission. Our aim is to make this library robust, sustainable, and highly user-friendly. Through more and more user interactions and feedback, we can better learn where the code is working well, and where it breaks down.

## Releases
Previous, current, and planned releases are summarized below (click to expand):

<details>
  <summary>Data Challenge 1 (<a href="https://github.com/cositools/cosi-data-challenge-1">link</a>): March 2023</summary>

  - Focused on the 2016 COSI Balloon flight.
  - Release includes real flight data for the Crab.
  - Main goal is to learn the fundamentals of analyzing Compton data with COSI.
  - The analysis tools used for DC1 are only preliminary (referred to as cosipy classic).
    - Developed by Thomas Siegert for analysis of the 2016 balloon data. 
  - Contains 3 straightforward examples of COSI’s science goals:
    - Extracting energy spectra from the Crab, Cen A, Cygnus X-1, and Vela.
    - Imaging bright point sources, such as the Crab and Cygnus X-1.
    - Imaging diffuse emission from the positron-electron annihilation 511 keV and Al-26 1.8 MeV gamma-ray lines.  
</details>

<details>
  <summary>Data Challenge 2 (<a href="https://github.com/cositools/cosi-data-challenges/tree/data_challenge_2.0">link</a>): March 2024</summary>
  
  - Focused on COSI SMEX mission.
  - First (alpha) release of cosipy. 
  - Data challenges for all the main science groups (none for dark matter and solar).
  - All models and challenges provided by respective COSI science teams.
  - Uses 3 months of observations, for an equatorial orbit at 550 km, with a zenith pointing. 
  - All background components are included, except for SAA passage (i.e. trapped cosmic rays).
    - Background also includes time variability from changing geomagnetic cutoff.
  - We simulated 12 background components, and 30 unique sources, running 49 different source simulations in total (using multiple models for some of the sources).
  - Contains 8 main tutorials demonstrating all the tools/methods needed for completing the challenges, included as part of the cosipy release:
    - dataIO
    - detector response
    - GRB localization (TS maps)
    - GRB spectral fit
    - Crab spectral fit
    - 511 spectral fit
    - Crab imaging
    - 511 imaging  
</details>

<details>
  <summary>Data Challenge 3 (<a href="https://github.com/cositools/cosi-data-challenges/tree/data_challenge_3.2">link</a>): April 2025</summary>
  
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
  - Restructuring and refinement of the cosi-data-challenges repository.
  - Simulated 45 unique sources, running 75 different source simulations in total (using multiple models for some of the sources).
  - Numerous improvements to cosipy:
    - First version of source injector.
    - New implementation of Earth occultation in point source response.
    - First polarization tools.
    - New methods to estimate the background for continuum sources and line sources.
    - Refinements and further developments of imaging class.
    - New extended source response class.
  - Contains 4 new tutorials (in addition to the ones released with DC2) demonstrating the tools/methods needed for completing the challenges, included as part of the cosipy release:
    - Source injector
    - Polarization (ASAD method)
    - Continuum background estimation
    - Line background estimation  
</details>

<details>
  <summary>Data Challenge 4 (current release): May 2026</summary>
 
  - Fist time using a realistic mock dataset:
    - Includes 64 sources plus total background, distributed in weekly data files.
    - The DC4 mock dataset is comprised of a combination of simulations from DC3 and new simulations for DC4.
    - For DC4 we produced 24 new source simulations plus updated simulations for most background components. 
    - DC4 uses same inputs as DC3, i.e., same mass model, orientation file, detector effects engine, etc.
    - Response files are also the same, but the formatting has been optimized.
  - Substantial changes to cosipy, including:
    - Refactored the entire library to improve modularity by implementing an interface-based design. As the codebase continues to grow in complexity, this was necessary to ensure long-term maintainability and sustainability.
    - Optimized many components of the code to improve performance and reduce memory usage. 
    - Introduced unbinned analysis for the first time, employing a neural network–based response approximation and background estimation. 
    - Improvements to all background estimation tools (continuum, line, transient).
    - Added the ability to fit multiple background components.
    - Introduced more data selection methods.
    - Introduced initial tools enabling phase-resolved analysis. 
    - Expanded and enhanced the available toolset.        

</details>

<details>
  <summary>Data Challenge 5: Planned for January 2027</summary>
  
  - Final release before launch :rocket:!
  - This data challenge will be blind to the general scientific community and most of the COSI science team. 

</details>

## Citing 
If you make use of any of the data products from the COSI Data Challenges in a publication, please provide a link to this page and cite [Zoglauer+23](https://arxiv.org/abs/2102.13158), [Martinez-Castellanos+23](https://pos.sissa.it/444/858), and the zenodo release: https://doi.org/10.5281/zenodo.15126188. 

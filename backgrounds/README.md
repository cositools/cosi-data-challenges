# Backgrounds

### Executive Summary
We employed MEGAlib to simululate 3 months of instrumental and astrophysical backgrounds (BGs), using an equatorial orbit at 530 km with a rocking of 22 degree every 12h. The astrophysical BGs include albedo emission and cosmic photons (i.e. the extragalactic gamma-ray background). The instrumental backgrounds arise from cosmic rays bombarding the instrument, and there is both a prompt component and a delayed component. The former is due to cosmic ray particles directly triggering the instrument. The latter is due to activation of the irradiated materials, which subsequently decay and emit photons that contribute to the BG emission. The instrumental BGs arise mainly from primary protons, primary alpha particles, atmospheric neutrons, primary electrons, primary positrons, and secondary protons electrons and positrons, all of which are included in DC3. In order to simulate the activation, MEGAlib keeps in memory each isotope created during the simulation until it decays (the expected decay time is computed according to the isotope lifetime and the event is rejected if this time is longer than the simulation time). This method accurately simulates the build-up of the activation during the 3 months of orbit. Our background simulations account for the time-dependent flux variation due to the changing geomagnetic cutoff along the orbit. Another important BG for COSI will be due to passage through the Southern Atlantic Anomoly (SAA). The SAA component is include in DC3 and will be describe below. Spectra and lightcurves for the DC3 BG components are shown below. Further details about the BG simulations are provided in the sections that follow. 

<p align="center">
<img width="600"  src="images/">
</p>

## Input Models

### Spectra and Source Files 
The input spectra are generated using the model from [Cumani](https://link.springer.com/article/10.1007/s10686-019-09624-0). This is implemented using the code **CreateBackgroundSpectrumMEGAlib.py**, available in the **DC3** branch of the [cosi-background](https://github.com/cositools/cosi-background/tree/DC3) repository. The user can choose the main parameters, including altitude, inclination, geomagnetic cutoff, etc. For DC3 we simulated an equatorial orbit at 530 km. Correspondingly, for the BGs we used the average rigidity cutoff for this orbit (10 GV) as the nominal value. Solar modulation is accounted for using the force field approximation, for which we use 520 MV, extrapolation of the expected solar activity in 2027. The resulting spectra are shown below. All of the input files used for the DC3 simulations can be found [here](https://github.com/cositools/cosi-sim/tree/main/cosi_sim/Source_Library/DC3). 

<p align="center">
<img width="550"  src="images/DC3inputflux.png">
</p>




### South Atlantic Anomaly (SAA)
The spectrum and light curve of the trapped protons are generated using the model [IRENE AP9 v1.57.004](https://www.vdl.afrl.af.mil/programs/ae9ap9/) . The expected differential flux is computed for every 15s of DC3 orbit and then integrated over the energy to get the light curve. Since COSI will not take data during SAA passages, we did not simulate the trapped electrons component. In order to improve the simulation time, the spectrum is troncated at 4 Mev. This is motivated by the fact we are only interested into activation induced by the trapped protons during a SAA passage. As shown in the figures below, the proton cross-section with commun materials found in the spacecraft are negligible below 4 MeV. A 24h orbit test has been done for a cut at 2 MeV, showing no significant variation with a cut at 4 MeV.      

<p align="center">
<img width="1000"  src="images/SAAspectrum.png">
</p>

The corresponding light curve for a few days of orbit is shown in the figure below: 

<p align="center">
<img width="550"  src="images/SAALC.png">
</p>

### Geomagnetic Cutoff Dependencies
The spacecraft coordinates have been generated with [SPENVIS](https://www.spenvis.oma.be/intro.php), as shown below. In addition, we added 12 hours observing North sky, then 8 minute slewing time 
on average, then 12 hours observing south sky and so on in order to take into account the +-22° rocking. An example of 4 days of observation is shown in the plot below.

<p align="center">
<img width="550"  src="images/DC3orientation.png">
</p>

Based on these coordinates, the average geomagnetic cutoff (in GV) is calculated as in [Smart and Shea (2005)](https://www.sciencedirect.com/science/article/pii/S0273117705001997?via%3Dihub):

$$ R_{\mathrm{cutoff}} = \frac{g^1_0\cdot R_{\mathrm{Earth}}}{4}\cdot \left( 1+\frac{h}{R_{\mathrm{Earth}}}\right)^{-2}\cos^4({\lambda}), $$

with $h$ the altitude in km, $R_{\mathrm{Earth}}$ the radius of Earth, $\lambda$ the geomagnetic latitude, and $g^1_0$ a coefficient computed by the International Geomagnetic Reference Field [IGRF](https://www.ncei.noaa.gov/products/international-geomagnetic-reference-field). The geomagnetic latitude for each orbit is computed with the python package [aacgmv2](https://pypi.org/project/aacgmv2/). The IGRF results are released every 5 years. For the DC3 simulations we used the extrapolated value for the year 2027: $g^1_0 =$ 29147.79 nT.        

We calculate the geomagnetic cutoff for 15 second time intervals of the 3 month orientation file, and use this to obtain the integrated spectrum for each BG component. The geomagnetic cutoff dependencies are described in [Cumani+19](https://link.springer.com/article/10.1007/s10686-019-09624-0). This results in a light curve for each component, which is used as input for the simulation, in order to take into account the geomagnetic cutoff dependencies in the expected BG flux. Note that cosima only takes the light curve shape into account, and the overall flux normalization is set by the spectrum. We make the simplifying approximation that the spectral shape is constant with time. This is a reasonable assumption, considering that the geomagnetic cutoff only varies from 9-11.5 GV, and correspondingly, the change in spectral shape is minor.

## Simulations

The BG simulations have been ran on the [MOGON](https://mogonwiki.zdv.uni-mainz.de/docs/introduction/what_is_mogon) cluster in Mainz. They employ [MEGAlib](https://github.com/zoglauer/megalib) (*develop-cosi* branch) via the COSI simulation pipepline ([cosi-data-challenges](https://github.com/cositools/cosi-data-challenges)), using [DC3 COSI-SMEX mass model](https://github.com/cositools/massmodel-cosi-dc3). More specifically, for the source simulations (with *cosima*) we use the COSISMEX.sim.geo.setup version of the mass model. This has a high strip pitch for charge sharing. For the event reconstruction (with *revan*) we use the COSISMEX.analysis.geo.setup version of the mass model. This implements the new detector effects engine. 

### Cosima
The first step of the simulations is done with *cosima*. The *develop-cosi* branch is used with the mass model file **COSISMEX.sim.geo.setup**. In order to use multiple CPUs, the initial flux is divided by 1000. The full 3 months orbit is then run on 1000 CPUs in parallel. 

### Revan 

The second step is the event reconstruction done by *revan*. This part still use the *develop-cosi* branch of MEGAlib with the mass-model file **COSISMEX.analysis.geo.setup** and the configuration file **SMEXv12.Continuum.HEALPixO3.binnedimaging.revan.cfg**. 

### Mimrec

The last step is the event selection done by *mimrec* using the configuration file **SMEXv12.Continuum.HEALPixO3.binnedimaging.mimrec.cfg**. Here, all the tra files from the individual simulation are collected into a single extracted file that is then converted into a fits file (using cosipy).  

### Computation Time
The simulations are very computationally intensive. **put a number of CPU h**

## Results

### Spectra and Light Curves 
The resulting spectra for each component are shown in the left figure at the top of this page. Note that here we are only considering the reconstructed Compton events, using the DC3 event selection. We can observe a dominance of the cosmic photons up to ~1 MeV,  The rates for each component are shown in the right figure at the top of the page. As expected, the rate is dominated by the cosmic photons and the proton/alpha delayed components. The total rates for the energy bands corresponding to the 0.511 MeV and Al26 emission lines are given below:
* 508 - 512 keV: 0.1848 Hz
* 1805 - 1812 keV: 0.0112 Hz

### Time Variation

On a daily scale, it is difficult to see the variation due to the geomagnetic cutoff. However, on the minute scale we can observe the rate variation which is opposite to the geomagnetic variation, as shown below. 

<p align="center">
<img width="650"  src="images/rate_geomagnetic_cutoff_comparison.png">
</p>

This validates the light curve models we used as input for the simulations. The total BG rate (without cosmic photons) as a function of the spacecraft geographic coordinates is shown in the left figure below and as function of the geographic longitude in the right figure below. 

<p align="center">
<img width="900"  src="images/geomagnetic_cutoff_location_comparison.png">
</p>

### Activation Backgrounds

We can observe several lines in the delayed components due to the activation of materials present in the mass model. The fact that a majority of the lines are common for all components suggests that these isotopes are produced by spallation reactions at high energy, where the type of particle does not matter. As a first approach, the line energies in the total spectrum are determined manually using matplotlib. A more robust method for the future will be to fit each line with a Gaussian, with its width constrained at the instrumental resolution. Almost all the lines are identified also thanks to the identification of SPI/INTEGRAL BG lines in [Weidenspointner+03](https://hal.in2p3.fr/in2p3-00022236v1/file/in2p3-00022236.pdf) and [Diehl+18](https://ui.adsabs.harvard.edu/abs/2018A%26A...611A..12D/abstract). The table below summarizes most of the lines we can identify in the total spectrum. 

<p align="center">
<img width="550"  src="images/table_of_identified_lines.png">
</p>

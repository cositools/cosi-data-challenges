# Earth Occultation  

Satellites in low-Earth orbit are occulted by Earth. This must be accounted for when simulating observations and performing data analysis. For zenith pointing observations—as was simulated for DC2—the Earth occultation is simply a function of the off-axis angle, and it can determined geometrically, as depicted in the schematic below:

<p align="center">
<img width="450"  src="images/earth_occ_dc2.png">
</p>

This can be implemented in the MEGAlib simulations in two different ways. For simulating astrophysical sources, a binary transmission probability file can be used, where the transmission probability is 1 for angles less than $\theta_{\text{max}}$ or 0 otherwise. Examples of this can be found in the *.source* files for the DC2 sources ([here](https://github.com/cositools/cosi-sim/tree/main/cosi_sim/Source_Library/DC2/sources)). The other option is to use a beam function, as is used for simulating backgrounds. Examples of this can be found in the *.source* files for the DC2 backgrounds ([here](https://github.com/cositools/cosi-sim/tree/main/cosi_sim/Source_Library/DC2/backgrounds)).

For the case above, the off-axis angle in detector coordinates is equivalent to the Earth zenith angle, and this makes it easy to account for Earth occultation. However, for DC3 we implemented the instrument rocking angle, where COSI rocks between $\pm 22^\circ$ from the Earth zenith. In detector coordinates, the Earth occultation now has an azimuthal dependence, in addition to the off-axis angle. In order to accommodate this in the simulations, we needed to add new functionalities to MEGAlib.

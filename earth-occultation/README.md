# Earth Occultation  

Satellites in low-Earth orbit are occulted by Earth. This must be accounted for when simulating observations and performing data analysis. For zenith pointing observations—as was simulated for DC2—the Earth occultation is simply a function of the off-axis angle, and it can determined geometrically, as depicted in the schematic below:

<p align="center">
<img width="450"  src="images/earth_occ_dc2.png">
</p>

For the case above, the off-axis angle in detector coordinates is equivalent to the Earth zenith angle, and this makes it easy to account for Earth occultation. However, for DC3 we implemented the instrument rocking angle, where COSI rocks between $\pm 22^\circ$ from the Earth zenith. In detector coordinates, the Earth occultation now has an azimuthal dependence, in addition to the off-axis angle. In order to accommodate this in the simulations, we needed to add new functionalities to MEGAlib.

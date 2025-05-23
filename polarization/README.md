# Polarization       

Polarization, which describes the alignment of photons' electric field vectors, can be used to probe the emission processes of astrophysical sources. As a Compton telescope, *COSI* is inherently sensitive to gamma-ray linear polarization. Data Challenge 3 includes a first version of *COSI*'s polarization analysis software, including two approaches: the azimuthal scattering angle distribution (ASAD) method and the Stokes parameters method.        

The polarization analysis tools will be made more sensitive and comprehensive in future Data Challenges, including a maximum likelihood method using forward-folding. See [Tomsick et al. 2022](https://ui.adsabs.harvard.edu/abs/2022hxga.book...73T/abstract) for a more in-depth overview of polarimetry with *COSI*.        

## Compton Polarimetry       

Compton telescopes are inherently sensitive to polarization because photons are more likely to Compton scatter in a direction perpendicular to their electric field vector. Therefore, measuring the scattering direction of photons probes the orientation of their electric field vectors. The Klein-Nishina equation, which describes the differential cross-section, or likelihood, of photons scattering with free electrons demonstrates this               
$$\large \frac{d\sigma}{d\Omega} = \frac{r_0^2}{2} \left( \frac{E^\prime}{E_\gamma} \right)^2 \left( \frac{E_\gamma}{E^\prime} + \frac{E^\prime}{E_\gamma} - 2\sin^2{\phi}cos^2{\eta} \right)$$,        
where $\large r_0$ is the classical electron radius, $\large E_\gamma$ is the energy of the incoming photon, $\large E^\prime$ is the energy of the Compton-scattered photon, $\large \phi$ is the Compton scattering angle, and $\large \eta$ is the azimuthal scattering angle, or the angle at which the photon scatters measured with respect to the incoming photon's electric field vector. The cross-section is maximized when the azimuthal scattering angle is perpendicular to the photon's electric field vector ($\large \eta=90^\circ$) and minimized when the azimuthal scattering angle is parallel to the electric field vector ($\large \eta=0^\circ$).   

<img src="images/scattering-angles.png" alt="Compton and azimuthal scattering angles" width="500"/>

***Figure 1:** The Compton scattering angle, ϕ, is the angle between the incoming and scattered photon directions. The azimuthal scattering angle, η, is measured with respect to a reference axis, ξ, in a plane perpendicular to the incoming photon direction. In the Klein-Nishina equation, the reference axis is the direction of the photon's electric field vector.*          

This makes it possible to determine the polarization using the measured distribution of azimuthal scattering angles. The probability distribution function that follows from the Klein-Nishina equation is of the form       
$$\large f(x) = A - B \cos{(2 (\eta - C))}$$         
where $\large \frac{B}{A}$ is proportional to the polarization fraction and $\large C$ is the polarization angle. When a source is polarized, the distribution of azimuthal scattering angles is expected to be sinusoidal, with the peaks corresponding to directions perpendicular to the incoming photon's electric field vector. For an unpolarized source, the azimuthal scattering directions are random, producing a uniform distribution. This allows the polarization to be determined by fitting $\large A$, $\large B$, and $\large C$ to the distribution of azimuthal scattering angles. However, a realistic detector is not perfectly symmetric, and some scattering directions are suppressed or enhanced due to the instrument geometry. Therefore, the distributions of azimuthal scattering angle for polarized and unpolarized sources will not be perfectly sinusoidal and uniform, respectively. This makes it important to have a very good understanding of the instrument response in order to accurately measure polarization.        

A polarization measurement is defined by the polarization fraction, which is sometimes called polarization level or polarization degree, and the polarization angle. The polarization fraction is the fraction of photons from a source that are polarized, where 100% polarization corresponds to all photons having their electric field vectors aligned in the same direction. The polarization angle describes the direction of the photons' electric field vector, and we typically use the standard [IAU convention](https://lambda.gsfc.nasa.gov/product/about/pol_convention.html) to define this angle. *cosipy*'s polarization tools include [methods for transforming between different conventions](https://cositools.github.io/cosipy/api/polarization.html), including the spacecraft frame conventions used in MEGAlib.         

The minimum detectable polarization (MDP) describes the minimum polarization fraction for which significant detection can be made by a particular instrument for a given source. The 99% confidence MDP is given by       
$$\large \text{MDP} = \frac{4.29}{\mu_{100}} \frac{\sqrt{N_s + N_b}}{N_s}$$      
where 4.29 is the coefficient corresponding to 99% confidence, and $\large N_s$ and $\large N_b$ are the number of source and background counts, respectively. A source with a fitted polarization fraction greater than its MDP has measurable polarization. However, only an upper limit can be placed on the polarization of a source with a fitted polarization fraction smaller than its MDP, and its polarization angle cannot be constrained. 

## Azimuthal Scattering Angle Distribution Method       

The simplest, and most intuitive, way to measure polarization is directly through the distribution of azimuthal scattering angles. *COSI* measures the scattered photon direction of each photon it detects. Because the direction of the incoming photon's electric field vector isn't known, a reference axis that is perpendicular to the incoming photon direction from the source location is chosen, which is in the plane of the photon's electric field vector. The angle between the scattered photon direction and reference axis is calculated for each photon. This measured azimuthal scattering angle ($\large \eta'$) relates to the azmimuthal scattering angle in the Klein-Nishina equation above via $\large \eta' = \eta + D$, where $\large D$, which is unknown, is the angle between the chosen reference axis and the photon's electric field vector. The azimuthal scattering angles of the data are binned to produce a raw azimuthal scattering angle distribution (ASAD).      

To find the polarization fraction and angle, the effects of the background and detector geometry need to be taken into account, and we rely heavily on simulations to do this. We create a background-subtracted ASAD, and then scale the distribution with a simulation of an unpolarized source to correct for detector effects. Then, this corrected ASAD is fit with the probability distribution function above to determine the polarization.           

To produce the background-subtracted ASAD, an ASAD for a model of the background is created, and subtracted from the total measured ASAD.       

<img src="images/source-asad.png" alt="Source ASAD" width="500"/>

***Figure 2:** The raw background-subtracted ASAD doesn’t obviously show the expected sinusoidal response of a polarized source since we haven’t accounted for the effects of the detector geometry.*        

Using the detector response, ASADs are then created for simulations of unpolarized and 100% polarized versions of the source being analyzed, with the same flux, sky position, and spectrum. These are used to account for instrumental effects and characterize the instrument's sensitivity to the source's polarization.         

<img src="images/unpolarized-asad.png" alt="Unpolarized ASAD" width="500"/>

***Figure 3:** A simulation of an unpolarized source, with the same spectrum and location, is used to account for instrumental effects.*       

<img src="images/100-percent-polarized-asad.png" alt="100% polarized ASAD" width="500"/>
       
***Figure 4:** A simulation of a 100% polarized source, with the same spectrum and location, is used to understand the polarization sensitivity of the instrument for this particular observation.*       

The measured source ASAD and simulated 100% polarized ASAD are both divided by the simulated unpolarized ASAD to correct for effects of the detector geometry.        

<img src="images/corrected-source-asad.png" alt="Corrected source ASAD" width="500"/>

***Figure 5:** The background-subtracted measured ASAD is divided by the ASAD of the simulated unpolarized source to get the final corrected ASAD for the observation. The ASAD is fit with a sinusoid (the probability distribution function above) to determine the polarization angle and fraction.*       

<img src="images/corrected-100-percent-polarized-asad.png" alt="Corrected 100% polarized ASAD" width="500"/>

***Figure 6:** The ASAD of the simulated 100% polarized source is divided by ASAD of the simulated unpolarized source and fit with a sinusoid in order to determine the modulation of the 100% polarized source.*          

Both corrected ASADs are fit with the above probability distribution function. The modulation of the 100% polarized ASAD, which is used to convert the amplitude of the sinusoidal fit of the source's ASAD to a polarization fraction, is given by        
$$\large \mu_{100} = \frac{\hat{B_{100}}}{\hat{A_{100}}}$$               
where $\large \hat{A_{100}}$ and $\large \hat{B_{100}}$ are the fitted values of the parameters for the 100% polarized ASAD. Then, the polarization fraction of the source is        
$$\large \Pi = \frac{1}{\mu_{100}} \frac{\hat{B}}{\hat{A}}$$        
and the polarization angle is         
$$\large \eta_0 = \hat{C}$$       
where $\large \hat{A}$, $\large \hat{B}$, and $\large \hat{C}$ are the fitted values of the parameters for the measured source ASAD.     

The sensitivity of the ASAD method is limited because only the scattered photon direction is used, and it is projected down onto only one axis, the azimuthal scattering angle. However, *COSI* also measures the energy and Compton scattering angle of each photon, and the scattered photon direction is described by two parameters, making up the Compton data space. As can be seen in the Klein-Nishina equation above, the scattering direction is dependent on the photon's energy and Compton scattering angle, not only the azimuthal scattering angle. By only fitting the azimuthal scattering angle, we are losing information, making the fit less sensitive than *COSI*'s measurements allow. The analysis can be made more sensitive by performing a maximum likelihood polarization fit in the Compton data space ([Krawczynski, 2011](https://ui.adsabs.harvard.edu/abs/2011APh....34..784K/abstract), [Lowell et al., 2017](https://ui.adsabs.harvard.edu/abs/2017ApJ...848..120L/abstract)). In Data Challenge 4, *cosipy* will include a forward-folding polarization fitting method, using *threeML*. 

## Stokes Parameters Method      

The Stokes parameters are a convenient and powerful way to characterize the polarization state of electromagnetic radiation, particularly for linear polarization. By definition, they describe the intensity and polarization of a beam through four quantities: $\large I$, $\large Q$, $\large U$, and $\large V$. For linear polarization, the parameters $\large Q$ and $\large U$ contain the essential information about the polarization direction and fraction, while $\large V$ captures the circular polarization component (which is often negligible in many astrophysical scenarios).

### Linear Polarization in Terms of Stokes Parameters

The Stokes parameters ($\large I$, $\large Q$, $\large U$, $\large V$) offer a convenient way to describe the polarization state of electromagnetic radiation:

- $\large I$ is the total intensity (i.e., the sum of the intensities over all polarization states).
- $\large Q$ and $\large U$ describe linear polarization.
- $\large V$ describes circular polarization (often negligible in many astrophysical scenarios).

A 100% linearly polarized beam can be visualized as the sum of electric field vectors oscillating in a single plane, and the relevant Stokes parameters for such a beam are $\large I$, $\large Q$, and $\large U$. The polarization fraction ($\large \Pi$) and polarization angle ($\large \eta_0$) (with respect to some reference axis) can be extracted from $\large Q$ and $\large U$ by:

$$\large \Pi = \frac{\sqrt{Q^2 + U^2}}{I}, \quad \eta_0 = \frac{1}{2} \tan_2^{-1}\left(\frac{U}{Q}\right)$$

Here, $\large \eta_0$ may be defined according to the [IAU convention](https://lambda.gsfc.nasa.gov/product/about/pol_convention.html) or another specified reference system; $\large tan_2^{-1}$ is the arctan2 is the angle (in radians), with $\large -\pi <\eta \leq \pi$, defined from the the positive x-axis ($\large Q>0$).

### Superposition principle 
The superposition principle states that when multiple waves overlap, the resulting wave is the sum of the individual contributions. In the context of linear polarization, this principle applies to the Stokes parameters $\large I$, $\large Q$, and $\large U$. When studying a polarized source over an unpolarized background, the superposition principle allows us to separate the polarized signal from the unpolarized contributions, as the background adds only to $\large I$, and not to $\large Q$ or $\large U$.

This principle is particularly important when addressing spurious polarization introduced by instrumental effects. Instruments can induce false polarization signals, even when observing unpolarized sources. To correct for this, we can simulate the detector’s response to an unpolarized source under identical exposure conditions as the real observation. By applying the superposition principle, the simulated spurious Q and U components can be subtracted from the observed data, effectively isolating the true polarization of the astrophysical source. This correction is critical for ensuring the accuracy of polarization measurements, particularly when considering short exposure which are more affected by the orientation of the spacecraft at that time.

$$\large Q_{src} = Q_{obs} - Q_{sim}, ~~~~ U_{src} = U_{obs} - Q_{sim},$$

### Photon-based pseudo-Stokes parameters
In implementing this pipeline, we adopt the formalism outlined in [Kislat et al., 2015](https://arxiv.org/abs/1409.6214) and follow the computational framework provided by the _ixpeobssim_ software, as described in ([Baldini et al., 2023](https://arxiv.org/abs/2203.06384)).

The Stokes parameters $\large I$, $\large Q$, and $\large U$ are derived from the measured azimuthal scattering angles $\large \eta'$ of incoming photons. The modulation curve, representing the distribution of these angles, is described by
$$\large N(\eta') = A[1+\mu cos(2(\eta'-\eta_0))]$$
where $\large A$ is the mean count rate and $\large \mu$ is the modulation factor. The Stokes parameters are computed as:

$$\large Q = \sum_{i=1}^N q_i ~~~~~~ U = \sum_{i=1}^N u_i$$

where N is the total number of photons, and $q_i$ and $u_i$ are the pseudo Stokes parameters defined photon-by-photon as:

$$\large q_i = 2 cos(2\phi_i) ~~~~~~ u_i = 2 sin(2\phi_i)$$

### Visualizing Polarization with Q-U Charts

A useful way to **visualize** the linear polarization state is to plot $\large U$ versus $\large Q$. In such a **Q-U chart**, each point represents a measurement of the Stokes parameters $\large Q/I$ and $\large U/I$ (with $\large -1 \leq Q, U \leq 1$). The distance of the point from the origin gives an indication of the **polarization degree**, while the **angle** it makes with the $\large Q$-axis corresponds to the polarization angle (ranging between 0 and 180 degrees).

- **Radius and Polarization Fraction**  
  The distance from the origin in the $\large Q-U$ plane is $\large \sqrt{\frac{Q}{I}^2 + \frac{U}{I}^2}$. This quantity yields the polarization fraction $\large \Pi$.
  
- **Quadrant location and Polarization Angle**  
  The position angle of the point in $\large Q-U$ space is defined relative to the $\large Q>0$ axis and  chosen reference axis (e.g., the IAU convention).

- **Uncertainties and Confidence Regions**  
  When uncertainties in $\large Q$ and $\large U$ are accounted for, they can be displayed as **error ellipses** (specifically circles since $\large Q/I$ and $\large U/I$ uncertainties are equal and Gaussian distributed). The size and shape of these ellipses provide a visual sense of the confidence level for the measured polarization state. 

- **Physical Interpretation**  
  - A measurement lying far from the origin indicates a high linear polarization fraction.
  - A point lying close to the origin indicates weak (or zero) linear polarization.
  - To consider a measurement a detection, a 99% C.L. (a ($\large Q/I$, $\large U/I$) point ~2.575 sigma distance from (0,0)) is required.

In practice, $\large Q-U$ charts are especially helpful for rapidly assessing the **direction** and **degree** of polarization in an observation, and for comparing different datasets (e.g., source vs. background, or different energy bands) in a straightforward 2D representation.       

<img src="images/qu-chart.png" alt="Q-U chart" width="500"/>

***Figure 7:** Polarization analysis in the Q/I - U/I plane: The red dot represents the measured polarization, while the red contours indicate confidence intervals around the measurement. The green marker and contours correspond to the simulated polarization values. The shaded pink region represents the 99% Minimum Detectable Polarization.*          

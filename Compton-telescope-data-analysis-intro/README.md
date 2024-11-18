## General Compton Telescope Analysis Procedure

Analysis of MeV data is challenging due to high backgrounds and the complicated instrument responses of Compton telescopes like COSI. Thus, here we provide a basic description of Compton telescope data analysis as an introduction for new users before diving into the Data Challenge analysis. For those who are new to Compton telescopes, we encourage you to read the review: [Kierans, Takahashi & Kanbach 2022](https://ui.adsabs.harvard.edu/abs/2022arXiv220807819K/abstract). 

Compton telescopes perform single-photon detection, a technique whereby each photon is measured as a number of energy deposits in the detector volume (shown in blue in the figure below). The order of interactions must first be sequenced in time to reconstruct the scattering path and determine the original direction of the photon. This photon origin is constrained to a circle on the sky (a so-called Compton event circle) defined by an opening angle equal to the Compton scattering angle $(\phi)$ of the first interaction. A typical event in a Compton telescope is shown in the figure below: a photon Compton scatters twice in the detector volume and undergoes a photoelectric absorption as its third and final interaction. The position of each interaction is recorded and the incident energy of the photon is fully contained in the active detector volume. The event sequencing and reconstruction are performed in the MEGAlib tool; we will start our analysis with events that are already defined by their total energy deposit in the detector $(E_0)$, and the Compton scattering angle.

<img width="760" alt="Screen Shot 2022-10-16 at 11 00 42 PM" src="https://user-images.githubusercontent.com/33991471/196080097-d3fdde9c-e7ae-494b-af02-1ffb846dbc33.png">

As shown in the figure above, a Compton telescope can image a source distribution by finding the overlap of event circles from multiple source photons. A point-source image can be recovered by performing deconvolution techniques. This List-mode imaging approach ([Zoglauer 2005](https://megalibtoolkit.com/documents/Zoglauer_PhD.pdf)) is implemented in MEGAlib and can be used for strong point sources, for example in laboratory measurements. However, this approach assumes a simplified detector response and cannot be used for the most sensitive analyses.

When performing analyses of astrophysical sources with high backgrounds, a more sophisticated description of the data space is required. This data space, along with the fundamentals of modern Compton telescope analysis techniques, was pioneered by the COMPTEL mission ([Schönfelder et al. 1993](https://ui.adsabs.harvard.edu/abs/1993ApJS...86..657S/abstract) & [Diehl et al. 1992](https://ui.adsabs.harvard.edu/abs/1992NASCP3137...95D/abstract)) and is sometimes referred to as the COMPTEL Data Space, or simply the Compton Data Space (CDS). In the CDS, each event is defined by a minimum of 5 parameters. Three parameters describe the geometry of each event: the Compton scatter angle $(\phi)$ of the first interaction, and the polar and azimuthal angles of the scattered photon direction $(\chi, \psi)$. These angles as defined in instrument coordinates are shown in the figure below. The other two parameters in the CDS are the total photon energy $(E_0)$ and the event time $(t)$, but these are not always explicitly written. 

<img width="722" alt="Screen Shot 2022-10-16 at 11 02 38 PM" src="https://user-images.githubusercontent.com/33991471/196080315-86545b58-7104-4ba1-b68d-e3a634e69fa5.png">

The scattering angles $(\phi, \chi, \psi)$ span the three orthogonal axes of the CDS. As photons from a point source at location $(\chi_0, \psi_0)$ scatter in the detector, the CDS is populated in the shape of a cone whose apex lies at the source location, as shown in the figure on the right. This is the point spread function of a Compton telescope. The opening angle of the CDS cone is 90º since the Compton scatter angle is equal (within measurement error) to the deviation of the scattered photon direction. An extended source will appear as a broadened cone. The more familiar Angular Resolution Measure (ARM) for Compton telescopes is a 1-dimensional projection of the width of the CDS cone walls, representing the angular resolution. 

All analyses with COSIpy start with reconstructed events defined in a photon list (MEGAlib’s .tra files). After reading in the data from the .tra file, the first step of any analysis is to bin the data into the CDS. For this Data Challenge, we are using 6º bin sizes for each of the scattering angles. This is because the angular resolution of the COSI Balloon instrument is ~6º at best, and smaller bins would be more computationally demanding. We are also using 10 energy bins for the continuum analyses, 2 hour time bins for the spectral analysis, and 30 minute time bins for the imaging analyses. For the narrow-line sources, such as 511 keV and Al-26, we use only 1 energy bin centered on the gamma-ray line of interest.

As a visual representation of the data (D) in the CDS, see the figure below. The three axes are the 3 scatter angles $(\phi, \chi, \psi)$. Each $(\phi, \chi, \psi)$ bin contains the number of events, or counts, with that geometry. These counts are illustrated with the red color fill (this is just a random distribution and not representative of what real data looks like in the CDS). The CDS is filled in this way for each energy and time bin, represented by the subscript $E,t$ in the figure. In COSIpy-classic, $\chi$ and $\psi$ are binned into in 1145 FISBEL bins. FISBEL stands for Fixed Integral Square Bins in Equi-Longitude, and is MEGAlib’s spherical axis binning that has approximately equal solid angle for each pixel.

<img width="400" alt="Screen Shot 2022-10-16 at 11 03 38 PM" src="https://user-images.githubusercontent.com/33991471/196080461-6e97c2c2-4d36-4cfb-b13c-935f438616c1.png">

Now that we have a better understanding of the Compton telescope data space and have binned our data in the CDS, we’re ready to perform spectral analysis and imaging with COSI. There are 3 key pieces needed: 
1. Response Matrix
2. Sky Model
3. Background Model

We will describe these components here and explain how they are used for general fitting procedures with COSI data. When running through the analysis notebooks, pay attention to when these are initialized.

### Response Matrix

The response matrix (R) for Compton telescopes represents the probability that a photon with energy $E_0$ originating from Galactic coordinates $(l,b)$ interacts in the detector and is recorded as an event with measured energy E’ and scattering angles $(\phi,\chi,\psi)$. The probability distribution is normalized to match the total effective area of the instrument, defining the conversion from counts to physical parameters. The matrix that encodes this information is 2 dimensions larger $(l,b)$ than the CDS and describes the transformation between image space and the CDS, taking into account the accurate response of the instrument. We build the response matrix through extensive MEGAlib simulations: the instrument is situated at the center of an isotropically-emitting source and thus records photons from all surrounding source locations. With a sufficiently large number of incident photons, we can populate the entire CDS of possible scattering angles and thereby obtain a representation of each incident photon in the CDS.

<img width="965" alt="Screen Shot 2022-10-16 at 11 05 26 PM" src="https://user-images.githubusercontent.com/33991471/196080645-6f1eecb9-a34a-489f-ae7c-79f43224ae32.png">

### Sky Model

For forward-folding analysis methods, we assume a source sky distribution, referred to as the sky (or signal) model (S). The sky model in image space can be, for example, a simple point source or a complicated diffuse model. The sky model also contains spectral and polarization assumptions about the source. This model is convolved with the instrument response matrix and knowledge of the instrument aspect pointing during observations to determine the representation of the sky model in the CDS. Below, we show this for a simple point source and regain the expected cone-shape in the CDS.

<img width="1065" alt="Screen Shot 2022-10-16 at 11 06 10 PM" src="https://user-images.githubusercontent.com/33991471/196080720-dc1db3c5-0bee-4843-b8d5-ddb936745bb1.png">

### Background Model

We require an accurate estimate of the backgrounds during observations. This background model (B) can be achieved in a number of ways. One approach is to use the measured flight data from source-starved regions. Alternatively, one can perform full bottom-up simulations of the gamma-ray background at balloon-flight altitudes, including atmospheric contamination and instrumental activation. For this first Data Challenge, we use the latter approach. The simulation is further described in [data_products](data_products); in future Data Challenges, we will employ multiple background-model approaches.

With the background model generated from simulations, we subsequently bin it in the same CDS that we used for the data and the source model. We have already performed this step for you, and have provided a .npz file, which is a zipped numpy array of the background simulation in the CDS.

<img width="1053" alt="Screen Shot 2022-10-16 at 11 06 45 PM" src="https://user-images.githubusercontent.com/33991471/196080812-bb591627-3127-454d-af92-1d859313774b.png">

### Fitting General Principle

Finally, we have all of our components and can perform the analysis. When model fitting, we can optionally free multiple spectral, polarization, and location parameters. For simplicity, in this Data Challenge we will only fit for the amplitudes of the source and background models ($\alpha$ and $\beta$, respectively) that best describe the measured data: **D = $\alpha$ S + $\beta$ B**. This fit is shown schematically in the figure below and is performed for each energy bin and time bin independently. This procedure for spectral fitting and spatial model fitting is maximizing the likelihood in the CDS.

<img width="1074" alt="Screen Shot 2022-10-16 at 11 07 20 PM" src="https://user-images.githubusercontent.com/33991471/196080880-83937b0d-15b0-4a93-b0dc-09368d3423ae.png">

If we don’t know what the source should look like, instead of providing a sky model we can remain agnostic to an assumed source distribution and perform image deconvolution. The data is represented as the sum of the response convolved with the source sky distribution (which we want to find) and the background:

<img width="482" alt="Screen Shot 2022-10-16 at 11 08 00 PM" src="https://user-images.githubusercontent.com/33991471/196080950-0a042af0-0bd8-4360-9f7f-898edcd81ee1.png">

Since the response is non-invertible, we must use iterative deconvolutions to reveal the sky distribution. In COSIpy-classic, we introduce you to a modified Richardson-Lucy algorithm, which is a special case of the expectation maximization algorithm developed for COMPTEL’s images of diffuse gamma-ray emission ([Knödlseder et al. 1999](https://ui.adsabs.harvard.edu/abs/1999A%26A...345..813K/abstract)). The Richardson-Lucy algorithm starts from an initial isotropic (i.e. unbiased) image, and iteratively compares the data in the CDS to the sky distribution convolved with the transpose of the response matrix R:

<img width="257" alt="Screen Shot 2022-10-16 at 11 08 28 PM" src="https://user-images.githubusercontent.com/33991471/196080993-a258bd27-9df9-4996-924c-ec3bc7222aa8.png">

This will evolve into the maximum likelihood solution. There are other image deconvolution techniques that will be used for COSI imaging, and those will be introduced in subsequent Data Challenges.

In order to gain intuition for how to interpret this equation, consider that we are trying to find the number of photons in an image pixel given our model expectation $M = R \cdot S + B$. Here, $M$ are the model counts, calculated from a linear combination of the instrumental background $B$ and the sky morphology $S$, to which the image response function $R$ is applied to convert from image space to data space.<br>
In such a counting experiment, the measured data $D$ given the model expectation $M$ follows a Poisson distribution, so that the likelihood of measuring $D$ photons is given by $P(D|M) = \prod \frac{\exp(-M)M^D}{D!}$. The product here is taken over all sky pixels.<br>
Taking the logarithm of the likelihood and plugging in the model expectation results in $L \equiv \ln P(D|S,B) = \sum \left(-(R \cdot S + B) + D \ln(R \cdot B) \right)$.<br>
Assuming, for the moment, that the background is known, we can optimise the likelihood with respect to the wanted sky signal $S$, such that<br>
$0 = \nabla_S L = -I \cdot R^T + \frac{D \cdot R^T}{R \cdot S + B} = \left(1 - \frac{D}{R \cdot S + B} \right) \cdot R^T$.<br>
Finally, this equation can be solved iteratively, (for each pixel simultaneously) by assuming a starting sky distribution (map) for $S$, similar to Newton's method for example, which will result in the RL equation above.

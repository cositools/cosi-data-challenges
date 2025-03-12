## GRBs
 The tools needed to complete these challenges are demonstrated in the [GRB spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/grb), [GRB localization](https://github.com/cositools/cosipy/tree/main/docs/tutorials/ts_map), and [Polarization (ASAD method)](https://github.com/cositools/cosipy/blob/develop/docs/tutorials/polarization/ASAD_method.ipynb) examples. 
 
 **Data Files:** <br />
 ResponseContinuum.o3.e100_10000.b10log.s10396905069491.m2284.filtered.nonsparse.binnedimaging.imagingresponse_nside8.area.h5.gz <br />
 ResponseContinuum.o3.pol.e200_10000.b4.p12.s10396905069491.m441.filtered.nonsparse.binnedpolarization.11D_nside8.area.h5.gz (for polarization) <br />
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
 GRB_bn080802386_flux300_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_MGF051103_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_MGF070201_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_MGF070222_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_MGF180128A_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_MGF200415A_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 GRB_MGF231115A_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 MgtBurst_bright_complex_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 MgtBurst_bright_simple_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
 
 **Input Models:** <br />
 All input models can be found [here](https://github.com/cositools/cosi-sim/tree/main/cosi_sim/Source_Library/DC3/sources/GRBs).
 
 The GRBs occur randomly within the orientation file, with their positions chosen such that they have incidence angles under $60^\circ$. The spectra are described with Band functions, and the parameters are based on fits to GBM data. Likewise, the lightcurves are also from GBM data. The fluxes were chosen such that some GRBs have a minimum detectable polarization (MDP) below their polarization fraction, and some have a MDP above. The models are specified below, including the polarization fraction (PF), and the polarization angle (PA) given in IAU convention. We also provide burst times, which is needed for the analysis:
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
 - bn080802386: PF = 0.8, PA = $90^\circ$, t = 1835493492.2 s
 
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
 - MgtBurst_bright_simple: no polarization, t = 1837365120.031250 s
   - A bright burst with simple light curve: spectrum of SGR 1935+2154 burst + light curve of 1E 1048.1-5937 ([Gavriil+02](https://www.nature.com/articles/nature01011)) burst.
 
 **GRB and MGF Goals:**
 1. Localize GRB
 2. Fit spectrum
 3. Measure polarization (fraction and angle)
 4. Classify: GRB or MGF
 
 **Magnetar Short Burst Goals:**
 1. Check if they are detectable
 2. If detectable, localize and fit spectrum (and polarization when applicable)

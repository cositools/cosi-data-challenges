## Dark Matter
The tools needed to complete these challenges are demonstrated in the [511 imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/511keV/ScAttBinning) and [511 spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/extended_source_fit) notebooks.
 
**Data Files:** <br />
eeg_ISO_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
eeg_Bur_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
eeg_NFW_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
gg_ISO_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
gg_Bur_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />
gg_NFW_3months_unbinned_data_filtered_with_SAAcut.fits.gz <br />

**Input Models:**  <br />
Photon spectra from annihilating dark matter (DM) in our galaxy. We consider cases where two DM particles annihilate into either two photons (gg) or an e+e− pair with a FSR photon (eeg), assuming DM follows an NFW or Burkert profile. The profile parameters are taken from [Cirelli+10](https://arxiv.org/abs/1012.4515), and the fragmentation function for the eeg case is from [Coogan+19](https://arxiv.org/abs/1907.11846), assuming a scalar mediator. We assume a DM mass of 3 MeV and an annihilation cross section of 1e-29 cm3/s.

**Goals:** <br />
1. Obtaining energy spectra
2. Obtaining signal morphologies
3. Estimating COSI’s detectability for annihilating WIMPs

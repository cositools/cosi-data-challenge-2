# COSI Data Challenge 2 (2024)

Welcome to the second COSI data challenge (DC2)! These data challenges are released on a yearly basis in preparation for the upcoming launch of the COSI Small Explorer mission in 2027 ([Tomsick+23](https://ui.adsabs.harvard.edu/abs/2023arXiv230812362T/abstract)). The main goals of the data challenges are to facilitate the development of the COSI data pipeline and analysis tools, and to provide resources to the astrophysics community to become familiar with COSI data. The first data challenge ([DC1](https://github.com/cositools/cosi-data-challenge-1)) was released in March 2023, and it was focused on data from the 2016 COSI balloon flight ([Kierans+17](https://ui.adsabs.harvard.edu/abs/2017arXiv170105558K/abstract)). The focus of DC2 is the satellite mission. With this data challenge we also make the first (alpha) release of our official high-level analysis tools, cosipy. 

## Getting Started 
The only software requirement for DC2 is [cosipy](https://github.com/cositools/cosipy). A general introduction into cosipy, including installation instructions, can be found in the [cosipy-intro](https://github.com/cositools/cosi-data-challenge-2/tree/main/cosipy-intro) directory. Note that cosipy is part of the larger COSITools, which is a broad collection of COSI data analysis tools, documentation, and verification data sets. COSITools can be installed by following the installation instructions [here](https://github.com/cositools/cosi-setup). This also includes MEGAlib, which is the main software program used for running simulations. However, unless you need MEGAlib and/or COSITools for other reasons, it's highly recommended to just install cosipy.    

This year's data challenge is based on 3 months of exposure time, for an equatorial orbit at an altitude of 550 km, with a zenith pointing. The simulated data products are provided in fits file format, and are hosted on wasabi. Details of the simulations, simulated data, and information for accessing the data products can be found in the [data-products](https://github.com/cositools/cosi-data-challenge-2/tree/main/data-products) directory. 

The input models and challenges for DC2 were provided by the COSI science teams. There are challenges for the different science groups: GRBs, Positrons, Nucleosynthesis, Galactic, and Extragalactic. These are described in detail in the **Data Challenges** section below.  

In summary, to get started with DC2, install cosipy, familiarize yourself with the data products, and then start working through the data challenges, as described below. 

## System Requirements
One of our goals in developing cosipy is to make it easily accesible to all users. **All of the data challenges in DC2 should be doable on a laptop with at least 16 GB of RAM**. The biggest memory limitation will likely come from combining and binning the data. We are still working on optimizing the code, and so please let us know if you are running into memory issues. 

## Getting Help
Please submit a new issue in the [cosipy](https://github.com/cositools/cosipy) git repository if you have issues with the code. If you have general feedback, or need further assistance, please reach out to the COSI Data Challenge team lead, Chris Karwin ([christopher.m.karwin@nasa.gov](mailto:christopher.m.karwin@nasa.gov)), the cosipy implementation lead, Israel Martinez-Castellanos ([israel.martinezcastellanos@nasa.gov](israel.martinezcastellanos@nasa.gov)), and the pipeline development lead Carolyn Kierans ([carolyn.a.kierans@nasa.gov](carolyn.a.kierans@nasa.gov)).

## Backgrounds
In general, observations in the MeV band are hindered by high backgrounds (both instrumental and astrophysical). In order to ensure that COSI accomplishes its main science goals, it is therefore crucial to have a firm understanding of these backgrounds. Although we are still in the early stages of development, with DC2 we have made significant progress in characterizing the background emission for COSI. Further details can be found in the [backgrounds](https://github.com/cositools/cosi-data-challenge-2/tree/main/backgrounds) directory. 

For analyzing data in DC2, the backgrounds are modeled using the actual injected backgrounds themselves. This is the ideal case, where the backgrounds are perfectly known, which of course is not very realistic. In future data challenges we will be developing tools for estimating backgrounds when they are not perfectly known, as will be the case for the actual observations.    

## Data Challanges
We have created example jupyter notebooks demonstrating all of the tools that will be needed to complete this year's data challenges. They are available as part of the cosipy release, and listed below: <br /> 

Example 1: [dataIO](https://github.com/cositools/cosipy/tree/main/docs/tutorials/DataIO) <br />
Example 2: [GRB localization](https://github.com/cositools/cosipy/tree/main/docs/tutorials/ts_map) <br />
Example 3: [GRB spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/grb) <br />
Example 4: [Crab spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/crab) <br />
Example 5: [511 spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/extended_source_fit) <br />
Example 6: [Crab imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/Crab/ScAttBinning) <br />
Example 7: [511 imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/511keV/ScAttBinning) <br />

If you haven't worked with Jupyter before, you can find some help [here](https://github.com/cositools/cosi-data-challenge-2/tree/main/cosipy-intro/notebook_help.md)

As a very first step, try working through some of the example notebooks. Specific challenges for the different science topics are described below. You can start with whichever topic you are most interested in. Each challenge will refer you to a specific example notebook that will demonstrate the basic tools needed to complete the respective challenge. If you have completed the main challenges and are interested in further challenges, see the **Extra Challenges** section at the bottom of this page. 

All input models used for the simulations can be found in the DC2 source library of the COSI simulation pipeline, available [here](https://github.com/cositools/cosi-data-challenges/tree/main/cosi_dc/Source_Library/DC2/sources). This includes all the information about the injected sources, and it can be used for checking the results of the data challenges. 

**Orientation and Background Files:** <br />
All challenges use the same files: <br />
orientation file: 20280301_3_month.ori <br />
background file: total_bg_3months_unbinned_data.fits.gz

## GRBs
 The tools needed to complete these challenges are demonstrated in the [GRB spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/grb) and [GRB localization](https://github.com/cositools/cosipy/tree/main/docs/tutorials/ts_map) examples. 

The burst time for each GRB is specified with the data file. This is the minimum information needed to complete the challenges.   

**Data Files:** <br />
SMEXv12.Continuum.HEALPixO3_10bins_log_flat.binnedimaging.imagingresponse.nonsparse_nside8.area.good_chunks_unzip.h5 <br />
GRB080723557_unbinned_data.fits.gz (t = 1836758310.0 s)  <br />
GRB090206620_unbinned_data.fits.gz (t = 1842597410.0 s) <br />
GRB130425327_unbinned_data.fits.gz (t = 1842417609.0 s) <br />
GRB090227772_unbinned_data.fits.gz (t = 1840166979.0 s) <br />
GRB090228204_unbinned_data.fits.gz (t = 1841042855.0 s) <br />
GRB101216721_unbinned_data.fits.gz (t = 1841710622.0 s) <br />
GRB080725541_unbinned_data.fits.gz (t = 1837379302.0 s) <br />
GRB081101491_unbinned_data.fits.gz (t = 1837992600.0 s) <br />
GRB081122614_unbinned_data.fits.gz (t = 1838665305.0 s) <br />
GRB081223419_unbinned_data.fits.gz (t = 1839467340.0 s) <br />
GRB180128215_unbinned_data.fits.gz (t = 1835487315.119 s) <br />
GRB200415A_unbinned_data.fits.gz (t = 1835487385.0265 s) <br />

**Input Models:** <br />
Spectra are either Band function or Comptonized spectrum fits from GBM. Long GRB lightcurves are downloaded directly from GBM. Short GRB realistic lightcurves are downloaded from GBM & binned using Bayesian blocks. Short GRB constant lightcurves are constant over the duration of the GRB. Magnetar giant flare lightcurves are downloaded from GBM & binned using Bayesian blocks. GRBs occur randomly in time throughout the duration of the 3 month exposure. GRB positions were chosen to have incidence angles between 0 and 30 degrees with a range of azimuthal angles.

**Goals:**
1) Determine source locations.
2) Determine time interval of each event and create lightcurve.
3) Fit spectra.
4) Identify event type (GRB vs MGF).

## Positrons
The tools needed to complete these challenges are demonstrated in the [511 imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/511keV/ScAttBinning) and [511 spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/extended_source_fit) notebooks. 

**Data Files:** <br />
SMEXv12.511keV.HEALPixO4.binnedimaging.imagingresponse.nonsparse_nside16.area.h5 <br />
psr_gal_511_DC2.h5 <br />
511_thick_disk_3months_unbinned_data.fits.gz <br />
511_thick_disk10x_3months_unbinned_data.fits.gz <br />
511_thin_disk_3months_unbinned_data.fits.gz <br />
511_thin_diskx10_3months_unbinned_data.fits.gz <br />

Note: binned data products are also available for the 511 components. The file names are the same as listed above, but with "binned" instead of "unbinnned" and ".hdf5" instead of ".fits.gz". The binning matches the detector response, and has a time bin size of 7202.125 seconds. 

**Input Models:** 

Spatial: <br />
Simple Gaussian spatial models with a thin or thick disk. The bulge is based off of the model in Skinner et al. 2014 (and used in Siegert et al. 2016) and includes a narrow and broad buldge, and a central point source. The disk descriptions follow Skinner for the thin disk (3 deg scale height) and Siegert for the thick disk (10.5 deg scale height).

Spectral: <br /> 
Each spatial component has two spectral components: 1) A line at 511 keV. This has a 2 keV FWHM width for the bulge components, and 3 keV FWHM for the disk emission. 2) the ortho-positronium (OPs) continuum emission (as described by Ore 1949). The relative fluxes of the OPs and 511 are scaled such that the positronium fraction for the disk is 85% and the fraction for the bulge is 95%.

Both models are included at 1x and 10x nominal flux.

Note: For the DC2 analysis we will only consider the line emission. The ortho-positronium continuum will be included starting with DC3. 

**Goals:**
1) Make full sky image of 511 keV. 
2) Determine scale height of disk emission.
3) Extract the line spectra of the bulge and disk emissions.

## Nucleosynthesis 

### Al26
The tools needed to complete these challenges are demonstrated in the [511 imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/511keV/ScAttBinning) and [511 spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/extended_source_fit) notebooks. 

**Data Files:** <br /> 
SMEXv12.1809keV.HEALPixO4.binnedimaging.imagingresponse.nonsparse_nside16.area.h5 <br />
psr_gal_Al26_DC2.h5 <br />
Al26_R5000_z1000_M60_3months_unbinned_data.fits.gz <br /> 
Al26_R5000_z1000_M60_3months_10xflux_unbinned_data.fits.gz <br />
Al26_R5000_z0200_M30_3months_unbinned_data.fits.gz <br />
Al26_R5000_z0200_M30_10xflux_3months_unbinned_data.fits.gz <br />

Note: binned data products are also available for the Al26 components. The file names are the same as listed above, but with "binned" instead of "unbinnned" and ".hdf5" instead of ".fits.gz". The binning matches the detector response, and has a time bin size of 7202.125 seconds. 

**Input Models:**  <br />

There are two realisations from the same doubly exponential disk model for Al26 line emission (1808.63 keV) in the Galaxy. The three-dimensional model is

$$&rho;(R,z,&phi;) = L / (4 &pi; R_s^2  z_s) \times \mathrm{exp}(-R/R_s) \times \mathrm{exp}(-|z|/z_s)$$
where L is the total luminosity of Al26 in the Galaxy, i.e. $L = M/m \times p/&tau;$, with $m = 26 u$ the atomic mass of Al26 nuclei, $p = 0.9976$ is the branching ratio to emit a photon, and $&tau; = 1.05$ Myr is the lifetime of Al26. This gives a quasi-persistent luminosity for a "living" Al26 mass $M$. The values $R_s$ and $z_s$ are the scale radius and scale height, respectively. The radial coordinate is given by $R$, i.e. $R = \sqrt{(x-x_0)^2 + (y-y_0)^2}$, and $z$ is the vertical coordinate, $z = z' - z_0$, where $x_0 = 8.178$, $y_0 = 0$, and $z_0 = -0.019$ are the coordinates of the Galactic center seen from Earth. All distance and size units are in kpc. The line of sight integration is performed so that the flux per pixel (here: cartesian pixel grid with 3 deg resolution) is in units of ph/cm2/s/sr.

Model 1: Al26_R5000_z0200_M30  <br />
$M = 3$ $M_\odot\$ $\implies L = 4.162 \times 10^{42}$ ph/s $\implies F = 1.278 \times 10^{-3}$ ph/cm2/s <br />
$R_s = 5.0$  <br />
$z_s = 0.2$  <br />

Model 2: R5000_z1000_M60 <br />
$M = 6$ $M_\odot\$ $\implies L = 8.324 \times 10^{42}$ ph/s $\implies F = 1.800 \times 10^{-3}$ ph/cm2/s <br />
$R_s = 5.0$ <br />
$z_s = 1.0$ <br />

The two models with 10 times the ejecta mass (i.e. $M \implies 10 \times M$) result in 10 times the flux.

**Goals:**
1) Distinction between the two models of roughly equal flux. Can we measure the scale height and radius in projected (Galactic) coordinates,
and can we do a profile likelihood with different 3D models to recover the input scale dimensions?
2) What does the reconstructed image look like, and can we determine the scale dimensions from a fit to the reconstructed image?

### Ti44
The tools needed to complete these challenges are demonstrated in the [Crab spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/crab) and [GRB localization](https://github.com/cositools/cosipy/tree/main/docs/tutorials/ts_map) notebooks.

**Data Files:** <br /> 
SMEXv12.44Ti.HEALPix04.E_1150_1164keV.binnedimaging.imagingresponse.nonsparse_nside16.area.h5
psr_gal_Ti44_E_1143_1171keV_DC2.h5 <br />
psr_gal_Ti44_E_1150_1164keV_DC2.h5 <br />
Ti44_CasA_3months_unbinned_data.fits.gz <br />
Ti44_CasA_x50_3months_unbinned_data.fits.gz <br />
Ti44_G1903_3months_unbinned_data.fits.gz <br />
Ti44_G1903_x10_3months_unbinned_data.fits.gz <br />
Ti44_SN1987A_3months_unbinned_data.fits.gz <br />
Ti44_SN1987A_x50_3months_unbinned_data.fits.gz <br />
Ti44_SNsurprise_3months_unbinned_data.fits.gz <br />
Ti44_SNsurprise_x50_3months_unbinned_data.fits.gz <br />

Note: There are two different response files with a slightly different width of the energy bin (one being more broad than the other). An additional goal of this data challenge is to determine which response file works better in the analysis.   

**Input Models:**  <br />
There are four models of supernova remnants with only the Ti44 line emission (1157.02 keV) included. The line is a broadened Gaussian with a Doppler broadening of 5000 km/s, corresponding to roughly 8.2 keV (1 sigma value). For this data challange, only the fluxes are important, so that we see if we detect the sources. The sources are: Cas A, SN1987A, G1.9+0.3, and SNsurprise.

**Goals:** <br />
1) Identification of Ti44 sources in the Milky Way.
2) Creating TS maps in only the Ti44 line.
3) Fitting the spectrum of a Gaussian line at inferred positions.
4) Identifty the SN surprise. 

## Galactic 
The tools needed to complete the Galactic challenges are demonstrated in the [Crab spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/crab), [Crab imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/Crab/ScAttBinning), and [GRB localization](https://github.com/cositools/cosipy/tree/main/docs/tutorials/ts_map) notebooks.

**All challenges should use the same detector response file:**
SMEXv12.Continuum.HEALPixO3_10bins_log_flat.binnedimaging.imagingresponse.nonsparse_nside8.area.good_chunks_unzip.h5

### CygX1

**Data Files:** <br />
cygX1_soft_3months_unbinned_data.fits.gz <br />
cygX1_hard_3months_unbinned_data.fits.gz <br />
cygX1_hard-soft_3months_unbinned_data.fits.gz <br />

**Input Models:**  <br />
The two spectral models for Cyg X1 are best fit models of time averaged INTEGRAL data 
([Cangemi et al 2021](https://ui.adsabs.harvard.edu/abs/2021A%26A...650A..93C/abstract)), 
given for hard and soft states.

**Goals:** <br />
1) Check how well COSI can detect the source in the hard/soft state.
2) Test how well COSI can be used as a monitor to detect a spectral transition between states.

### CygX3

**Data Files:** <br />
cygX3_FSXR_3months_unbinned_data.fits.gz <br />
cygX3_transition_3months_unbinned_data.fits.gz <br />
cygX3_FSXR_54percent-transition_46percent_3months_unbinned_data.fits.gz <br />

**Input Models:**  <br />
There are 6 different spectral models for Cyg X3 based on time averaged INTEGRAL data 
in [Cangemi+21](https://www.aanda.org/articles/aa/pdf/2021/01/aa37951-20.pdf), and the average time spent in each state is summarized below:

Quiescent:  6% <br />
Transition  46% <br />
FHXR:       10% <br />
FIM:        22% <br />
FSXR:       54%  <br /> 
Hypersoft:  12% <br />

In DC2 we consider that the time is split between the Transition (46%) and FSXR (54%) states. 
 
**Goals:** <br />
1) Check if COSI can achieve a decent measurement of the average spectrum over its lifetime, 
and if so, check if we can detect the spectral changes on shorter time scales. 

### 1E1740.7-2942

**Data Files:** <br />
1E1740_compton-powerlaw_3months_unbinned_data.fits.gz <br />
1E1740_two_components_3months_unbinned_data.fits.gz <br />

**Input Models:**  <br />
The 2 spectral models for 1E1740.7-2942 (also know as great annihilator) are the best fit models
 of INTEGRAL data obtained by [Bouchet+09](https://iopscience.iop.org/article/10.1088/0004-637X/693/2/1871/pdf):
 - compton-powerlaw: thermal comptonization + powerlaw
 - two components: two components of thermal comptonization with different temperatures
Both models represent the INTEGRAL data well but strongly differ at the highest energies.

**Goals:** <br />
1) Test if COSI can distinguish between the two models.

### GRS 1758-258

**Data Files:** <br />
GRS1758_3months_unbinned_data.fits.gz

**Input Models:**  <br />
Best fit comptonization model of epoch2 from [Pottschmidt+06](https://arxiv.org/pdf/astro-ph/0509006.pdf).

**Goals:** <br />
1) Measure spectrum. 

### PSR J1513-5908 (B1509-58)

**Data Files:** <br />
PSRB1509_3months_unbinned_data.fits.gz

**Input Models:**  <br />
Pulse profile and spectrum from [Kuiper+15](https://doi.org/10.1093/mnras/stv426). The source is divided into 3 energy bands: <br />
Band1: 100-250 keV <br />
Band2: 250-750 keV <br />
Band3: 0.75-10 MeV <br />

**Goals:** <br />
1) Detection and measurement of phase-integrated spectrum.

### PSR J1846-0258

**Data Files:** <br />
PSRJ1846_3months_unbinned_data.fits.gz

**Input Models:**  <br />
Pulse profile and spectrum from [Kuiper+18](https://doi.org/10.1093/mnras/stx3128).

**Goals:** <br />
1) Detection and measurement of phase-integrated spectrum.

### Crab DC2

**Data Files:** <br />
Crab_DC2_3months_unbinned_data.fits.gz

**Input Models:**  <br />
The pulse profile is from [Kuiper+01](https://doi.org/10.1051/0004-6361:20011256). The spectrum(pulsar + nebula) is from [Petry+09](https://doi.org/10.1051/0004-6361/200912844). The source is divided into 5 energy bands: <br />
Band1: 100-315 keV <br />
Band2: 315-750 keV <br />
Band3: 0.75-1 MeV <br />
Band4: 1-3 MeV <br />
Band5: 3-10 MeV <br />

**Goals:** <br />
1) Detection and measurement of phase-integrated spectrum.

### Crab DC1

**Data Files:** <br />
crab_3months_unbinned_data.fits.gz

**Input Models:**  <br />
This is the same input model that was used for DC1. 

**Goals:** <br />
1) Localize source.
2) Measure spectrum.
3) Image source.

## Extragalactic
The tools needed to complete the Extragalactic challenges are demonstrated in the [Crab spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/crab) notebook.

**All challenges should use the same detector response file:**
SMEXv12.Continuum.HEALPixO3_10bins_log_flat.binnedimaging.imagingresponse.nonsparse_nside8.area.good_chunks_unzip.h5

### 3C 273

**Data Files:** <br /> 
3C273_3months_unbinned_data.fits.gz <br />
3C273_10xFlux_3months_unbinned_data.fits.gz <br />

**Input Models:**  <br />
The baseline model can be found in Madsen et al 2015.

**Goals:** <br />
1) Determine flux and spectral index in the COSI band.

### 3C 279

**Data Files:** <br />
3C279_low100_3months_unbinned_data.fits.gz <br />
3C279_high100_3months_unbinned_data.fits.gz <br />

**Input Models:**  <br />
The spectral data are 3C279 low and high, which represent the low and high states of the source, and the flux is increased by 100x its nominal value.

**Goals:** <br />
1) Determine if COSI can identify spectral curvature and changes during flares. The low state has two spectral components due to synchrotron self-Compton and external Compton, while the high state is dominated by synchrotron self-Compton.

### 4C+21.35

**Data Files:** <br />
4C21p35_3months_unbinned_data.fits.gz

**Input Models:**  <br />
Need more info.

**Goals:** <br />
1) Detect flaring continuum source. 
2) Measure spectrum and lightcurve. 

## Extra Challenges
Below we provide more advanced data challenges for interested users. The ultimate goal of these challenges would be to eventually integrate the methods and tools into the cosipy source code. 

### Extended 
These challenges will require using the tools already available in cosipy to develop new functionality. 
1) Develop method for calculating light curves.
2) Develop method for calculating SEDs.
3) Example notebook demonstrating simultaneous fit of multiple point sources.
4) Develop source injector.
5) Test construction of TS map with multiple sources (of varying relative intensities). 

### Advanced
These challenges will require developing new fundamental tools, which should fit into the cosipy framework.
1) Allow for time-dependent spectral fits.
2) Develop tools for time-resolved analysis.
3) Implement parallel computing.
4) Implement GPU computing.
5) Minimize memory usage. 

## Known Caveats 
1) As can be seen in the spectral fit tutorials, we are not able to perfectly recover the input models (e.g. the Crab spectrum), although the results are very close. This is the case even though we are using an ideal background. We think that this may be due to the fact that our response currently uses a coarse pixelation. Another possibility is that it may be related to a poorly characterized response for high off-axis angles. This is something that still needs to be investigated further. **NB: Our current response only uses 0.5% of the statistics that will be used for the actual analysis with the satellite data**. 

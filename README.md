# COSI Data Challenge 2 (2024)

Welcome to the second COSI data challenge (DC2)! These data challenges are released on a yearly basis in preparation for the upcoming launch of the COSI Small Explorer mission in 2027 ([Tomsick+23](https://ui.adsabs.harvard.edu/abs/2023arXiv230812362T/abstract)). The main goals of the data challenges are to facilitate the development of the COSI data pipeline and analysis tools, and to provide resources to the astrophysics community to become familiar with COSI data. The first data challenge ([DC1](https://github.com/cositools/cosi-data-challenge-1)) was released in March 2023, and it was focused on data from the 2016 COSI balloon flight ([Kierans+17](https://ui.adsabs.harvard.edu/abs/2017arXiv170105558K/abstract)). The focus of DC2 is the satallite mission. With this data challenge we also make the first (alpha) release of our official high-level analysis tools, cosipy. 

## Getting Started 
The only software requirement for DC2 is [cosipy](https://github.com/cositools/cosipy). A general introduction into cosipy, including installation instructions, can be found in the [cosipy-intro](https://github.com/cositools/cosi-data-challenge-2/tree/main/cosipy-intro) directory. Note that cosipy is part of the larger COSITools, which is a broad collection of COSI data analysis tools, documentation, and verification data sets. COSITools can be installed by following the installation instructions [here](https://github.com/cositools/cosi-setup). This also includes MEGAlib, which is the main software program used for running simulations. However, unless you need MEGAlib and/or COSITools for other reasons, it's highly recommended to just install cosipy.    

This year's data challenge is based on 3 months of exposure time, for an equatorial orbit at an altitude of 550 km, with a zenith pointing. The simulated data products are provided in fits file format, and are hosted on wasabi. Details of the simulations, simulated data, and information for accessing the data products can be found in the [data-products](https://github.com/cositools/cosi-data-challenge-2/tree/main/data-products) directory. 

The input models and challenges for DC2 were provided by the COSI science teams. There are challenges for the different science groups: GRBs, Positrons, Nucleosynthesis, Galactic, and Extragalactic. These are described in detail in the **Data Challenges** section below.  

In summary, to get started with DC2, install cosipy, familiarize yourself with the data products, and then start working through the data challenges, as described below. 

## Getting Help
Please submit a New Issue in the [cosipy](https://github.com/cositools/cosipy) git repository if you have issues with the code. If you have general feedback, or need further assistance, please reach out to the COSI Data Challenge team lead, Chris Karwin ([christopher.m.karwin@nasa.gov](mailto:christopher.m.karwin@nasa.gov)), the cosipy implementation lead, Israel Martinez-Castellanos ([israel.martinezcastellanos@nasa.gov](israel.martinezcastellanos@nasa.gov)), and the pipeline development lead Carolyn Kierans ([carolyn.a.kierans@nasa.gov](carolyn.a.kierans@nasa.gov)).

## Backgrounds
In general, observations in the MeV band are hindered by high backgrounds (both instrumental and astrophysical). In order to ensure that COSI accomplishes it's main science goals, it is therefore crucial to have a firm understanding of these backgrounds. Although we are still in the early stages of development, with DC2 we have made significant progress in characterizing the background emission for COSI. Further details can be found in the [backgrounds](https://github.com/cositools/cosi-data-challenge-2/tree/main/backgrounds) directory. 

For analyzing data in DC2, the backgrounds are modeled using the actual injected backgrounds themselves. This is the ideal case, where the backgrounds are perfectly known, which of course is not very realistic. In future data challenges we will be developing tools for estimating backgrounds when they are not perfectly known, as will be the case for the actual observations.    

## Data Challanges
We have created example jupyter notebooks demonstrating all of the tools that will be needed to complete this year's data challenges. They are available as part of the cosipy release, and listed below: <br /> 

Example 1: GRB localization <br />
Example 2: [GRB spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/grb) <br />
Example 3: [Crab spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/crab) <br />
Example 4: 511 spectral fit <br />
Example 5: [Crab imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/Crab/ScAttBinning) <br />
Example 6: [511 imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/511keV/ScAttBinning) <br />

As a very first step, try working through some of the example notebooks. Specific challenges for the different science topics are described below. You can start with whichever topic you are most interested in. Each challenge will refer you to a specific example notebook that will demonstrate the basic tools needed to complete the respective challenge. If you have completed the main challenges and are interested in further challenges, see the **Extra Challenges** section at the bottom of this page. 

All input models used for the simulation can be found in the DC2 source library of the COSI simulation pipeline, available [here](https://github.com/cositools/cosi-data-challenges/tree/main/cosi_dc/Source_Library/DC2/sources). This includes all the information about the injected sources, and it can be used for checking 

## GRBs
 The tools needed to complete these challenges are demonstrated in the [GRB spectral fit](https://github.com/cositools/cosipy/tree/main/docs/tutorials/spectral_fits/continuum_fit/grb) and GRB localization examples. 

**Data Files:** <br />
3 long GRBs with realistic lightcurves: <br /> 
GRB080723557_unbinned_data.fits.gz  <br />
GRB090206620_unbinned_data.fits.gz <br />
GRB130425327_unbinned_data.fits.gz <br />

3 short GRBs with realistic lightcurves: <br />
GRB090227772_unbinned_data.fits.gz <br />
GRB090228204_unbinned_data.fits.gz <br />
GRB101216721_unbinned_data.fits.gz <br />

4 short GRBs with constant lightcurves: <br />
GRB080725541_unbinned_data.fits.gz <br />
GRB081101491_unbinned_data.fits.gz <br />
GRB081122614_unbinned_data.fits.gz <br />
GRB081223419_unbinned_data.fits.gz <br />

2 magnetar giant flares (MGFs): <br /> 
GRB180128215_unbinned_data.fits.gz <br />
GRB200415A_unbinned_data.fits.gz <br />

**Input Models:** <br />
Spectra are either Band function or Comptonized spectrum fits from GBM. Long GRB lightcurves are downloaded directly from GBM. Short GRB realistic lightcurves are downloaded from GBM & binned using Bayesian blocks. Short GRB constant lightcurves are constant over the duration of the GRB. Magnetar giant flare lightcurves are downloaded from GBM & binned using Bayesian blocks. GRBs occur randomly in time throughout the duration of the 3 month exposure. GRB positions were chosen to have incidence angles between 0 and 30 degrees with a range of azimuthal angles.

**Goals:**
1) Determine time of each event and create lightcurve
2) Determine source locations
3) Fit spectra
4) Identify event type (GRB vs MGF)

## Positrons
The tools needed to complete these challenges are demonstrated in the [511 imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/511keV/ScAttBinning) and 511 spectral fit notebooks. 

**Data Files:** <br />
511_thick_disk_3months_unbinned_data.fits.gz <br />
511_thick_disk10x_3months_unbinned_data.fits.gz <br />
511_thin_disk_3months_unbinned_data.fits.gz <br />
511_thin_diskx10_3months_unbinned_data.fits.gz <br />

**Input Models:** 

Spatial: <br />
Simple Gaussian spatial models with a thin or thick disk. The bulge is based off of the model in Skinner et al. 2014 (and used in Siegert et al. 2016) and includes a narrow and broad buldge, and a central point source. The disk descriptions follow Skinner for the thin disk (3 deg scale height) and Siegert for the thick disk (10.5 deg scale height).

Spectral: <br /> 
Each spatial component has two spectral components: 1) A line at 511 keV. This has a 2 keV FWHM width for the bulge components, and 3 keV FWHM for the disk emission. 2) the orthopositrium (OPs) continuum emission (as described by Ore 1949). The spectral shape of the OPs continuum is included in the OPsSpectrum.dat file and shown in ops_spectrum.pdf. The relative fluxes of the OPs and 511 are scale such that the positronium fraction for the disk is 85% and the fraction for the bulge is 95%.

Both models are included at 1x and 10x nominal flux.

**Goals:**
1) Make full sky image of 511 keV (image deconvolution)
2) Determine scale height of disk emission (model fitting)
3) Extract the spectra of the bulge emission

## Nucleosynthesis 

### Al26
The tools needed to complete these challenges are demonstrated in the [511 imaging](https://github.com/cositools/cosipy/tree/main/docs/tutorials/image_deconvolution/511keV/ScAttBinning) and 511 spectral fit notebooks. 

**Data Files:** <br /> 
Al26_R5000_z1000_M60_3months_unbinned_data.fits.gz <br /> 
Al26_R5000_z1000_M60_3months_10xflux_unbinned_data.fits.gz <br />
Al26_R5000_z0200_M30_3months_unbinned_data.fits.gz <br />
Al26_R5000_z0200_M30_10xflux_3months_unbinned_data.fits.gz <br />

**Input Models:**  <br />

There are two realisations from the same doubly exponential disk model. The three-dimensional model is

$$&rho;(R,z,&phi;) = L / (4 &pi; R_s^2  z_s) * exp(-R/R_s) * exp(-|z|/z_s)$$
where L is the total luminosity of Al26 in the Galaxy, i.e. $L = M/m * p/&tau;$, with $m = 26 u$ the atomic mass of Al26 nuclei, $p = 0.9976$ is the branching ratio to emit a photon, and $&tau; = 1.05$ Myr is the lifetime of Al26. This gives a quasi-persistent luminosity for a "living" Al26 mass $M$. The values $R_s$ and $z_s$ are the scale radius and scale height, respectively. The radial coordinate is given by $R$, i.e. $R = \sqrt{(x-x_0)^2 + (y-y_0)^2}$, and $z$ is the vertical coordinate, $z = z' - z_0$, where $x_0 = 8.178$, $y_0 = 0$, and $z_0 = -0.019$ are the coordinates of the Galactic centre seen from Earth. All distance and size units are in kpc. The line of sight integration is performed so that the flux per pixel (here: cartesian pixel grid with 3 deg resolution) is in units of ph / cm2 / s / sr.

Model 1: Al26_R5000_z0200_M30  <br />
$M = 3$ Msol $\implies L = 4.162e42$ ph/s $\implies F = 1.278e-3$ ph / cm2 / s <br />
$R_s = 5.0$  <br />
$z_s = 0.2$  <br />

Model 2:
M = 6 Msol -> L = 8.324e42 ph/s -> F = 1.800e-3 ph / cm2 / s
Re = 5.0
ze = 1.0
filenames: COSI_DC2_26Al_R5000_z1000_M60_3deg

The two model with 10 times the ejecta mass, which will result in 10 times the flux:
Model 1x10:
M = 30 Msol -> L = 4.162e43 ph/s -> F = 1.278e-2 ph / cm2 / s
Re = 5.0
ze = 0.2
filenames: COSI_DC2_26Al_R5000_z0200_M30_3deg_10xflux

Model 2x10:
M = 60 Msol -> L = 8.324e43 ph/s -> F = 1.800e-2 ph / cm2 / s
Re = 5.0
ze = 1.0
filenames: COSI_DC2_26Al_R5000_z1000_M60_3deg_10xflux

**Goals:**
1) Distinction between the two models of roughly equal flux. Can we measure the scale heigt and radius in projected (Galactic) coordinates,
and can we do a profile likelihood with different 3D models to recover the input scale dimensions?
2) What does the reconstructed image look like, and can we determine the scale dimensions from a fit to the reconstructed image?

### Ti44
2023/May/16 Thomas Siegert
This is the description of the source models for point like 44Ti line emission in the Galaxy at 1157.02 keV

There are four models of supernova remnants with the 44Ti line emission only included.

The line is a broadened Gaussian with a Doppler broadening of 5000 km/s, corresponding to roughly 8.2 keV (1 sigma value).

For this data challange, only the fluxes are important, so that we see if we detect the sources.

The sources are:
Cas A
SN1987A
G1.9+0.3
Betelgeuse (SNsurprise)

The .source files provided are for the actually expected flux, and 50 times the expected flux for these sources to check
for us how many photons to expect in the broadened line, and for the data challange to "count" the supernova remnants.


Goals: Identification of 44Ti sources in the Milky Way.
Creating TS maps in only the 44Ti line (probably with an approximated line response).
Fitting the spectrum of a Gaussian line only at inferred positions.


Files:
The .source files are copied from a template and the names, coordinates, and fluxes are changed accordingly.

## Galactic 
## Extragalactic
## Extra Challenges
### Extended 
### Advanced


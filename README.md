# COSI Data Challenge 2 (2024)

Welcome to the second COSI data challenge (DC2)! These data challenges are released on a yearly basis in preparation for the upcoming launch of the COSI Small Explorer mission in 2027 ([Tomsick+23](https://ui.adsabs.harvard.edu/abs/2023arXiv230812362T/abstract)). The main goals of the data challenges are to facilitate the development of the COSI data pipeline and analysis tools, and to provide resources to the astrophysics community to become familiar with COSI data. The first data challenge ([DC1](https://github.com/cositools/cosi-data-challenge-1)) was released in March 2023, and it was focused on data from the 2016 COSI balloon flight ([Kierans+17](https://ui.adsabs.harvard.edu/abs/2017arXiv170105558K/abstract)). The focus of DC2 is the satallite mission. With this data challenge we also make the first (alpha) release of our official high-level analysis tools, cosipy. 

## Getting Started 
The only software requirement for DC2 is [cosipy](https://github.com/cositools/cosipy). A general introduction into cosipy, including installation instructions, can be found in the [cosipy-intro](https://github.com/cositools/cosi-data-challenge-2/tree/main/cosipy-intro) directory. Note that cosipy is part of the larger COSITools, which is a broad collection of COSI data analysis tools, documentation, and verification data sets. COSITools can be installed by following the installation instructions [here](https://github.com/cositools/cosi-setup). This also includes MEGAlib, which is the main software program used for running simulations. However, unless you need MEGAlib and/or COSITools for other reasons, it's highly recommended to just install cosipy.    

The input models and challenges for DC2 were provided by the COSI science teams. There are challenges for the different science groups: GRBs, Positrons, Nucleosynthesis, Galactic, and Extragalactic. These are described in detail in the **Data Challenges** section below. We have created example jupyter notebooks demonstrating the basic tools that you'll need to complete each challenge. In addition to the main data challenges, we have given some extra challenges, which entails developing new functionality using the available tools in cosipy, e.g. methods for calculating light curves, SEDs, etc. Finally, we have also given some advanced challenges, which entails developing new tools. 

In summary, to get started with DC2, install cosipy, familiarize yourself with the (simulated) data products, and then start working through the data challenges, as described below. 

## Getting Help
Please submit a New Issue in the [cosipy](https://github.com/cositools/cosipy) git repository if you have issues with the code. If you have general feedback, or need further assistance, please reach out to the COSI Data Challenge team lead, Chris Karwin ([christopher.m.karwin@nasa.gov](mailto:christopher.m.karwin@nasa.gov)), the cosipy implementation lead, Israel Martinez-Castellanos ([israel.martinezcastellanos@nasa.gov](israel.martinezcastellanos@nasa.gov)), and/or the pipeline development lead Carolyn Kierans ([carolyn.a.kierans@nasa.gov](carolyn.a.kierans@nasa.gov)).

## Data Products
This year's data challenge is based on 3 months of exposure time, for an equatorial orbit at an altitude of 550 km, with a zenith pointing. Details of the simulations, simulated data, and information for accessing the data products can be found in the [data-products](https://github.com/cositools/cosi-data-challenge-2/tree/main/data-products) directory. 

## Backgrounds
In general, observations in the MeV band are hindered by high backgrounds (both instrumental and astrophysical). In order to ensure that COSI accomplishes it's main science goals, it is therefore crucial to have a firm understanding of these backgrounds. Although we are still in the early stages of development, with DC2 we have made significant progress in characterizing the background emission for COSI. Further details can be found in the [backgrounds](https://github.com/cositools/cosi-data-challenge-2/tree/main/backgrounds) directory. 

For analyzing data in DC2, the backgrounds are modeled using the actual simulated backgrounds themselves. This is the ideal case, where the backgrounds are perfectly known, which is not realistic. In future data challenges we will be developing tools for estimating backgrounds when they are not perfectly known, as will be the case for the actual observations.    

## Data Challanges
We have created example jupyter notebooks demonstrating all of the tools that will be needed to complete this year's data challenges. They are available as part of the cosipy release, and listed below: <br /> 

Example 1: GRB localization <br />
Example 2: GRB spectral fit <br />
Example 3: Crab spectral fit <br />
Example 4: 511 spectral fit <br />
Example 5: Crab imaging <br />
Example 6: 511 imaging <br />

As a very first step, try working through some of the example notebooks. Specific challenges for the different science topics are described below. You can start with whatever topic you are most interested in. Each challenge will refer you to a specific example notebook that will demonstrate the basic tools needed to complete the respective challenge. If you have completed the main challenges and are interested in further challenges, see the **Extra Challenges** section at the bottom of this page. 

## GRBs
Included are:
3 long GRBs with realistic lightcurves - GRB080723557.source, GRB090206620.source, GRB130425327.source
3 short GRBs with realistic lightcurves - GRB090227772.source, GRB090228204.source, GRB101216721.source
4 short GRBs with constant lightcurves - GRB080725541.source, GRB081101491.source, GRB081122614.source, GRB081223419.source
2 magnetar giant flares (MGFs) - GRB180128215.source, GRB200415A.source

Spectra are either Band function or Comptonized spectrum fits from GBM.
Long GRB lightcurves are downloaded directly from GBM.
Short GRB realistic lightcurves are downloaded from GBM & binned using Bayesian blocks.
Short GRB constant lightcurves are constant over the duration of the GRB.
Magnetar giant flare lightcurves are downloaded from GBM & binned using Bayesian blocks.

GRBs occur randomly in time throughout the duration of the orientation file (20280301_3_month_edited.ori), and 1835487300.0 s needs to be added to the .sim files to match the Data Challenge 2 orientation file. 
GRB positions were chosen to have incidence angles between 0 and 30 degrees with a range of azimuthal angles.

Goals:
Determine time of each event and create lightcurve
Determine source locations
Fit spectra
Identify event type (GRB vs MGF)

## Positrons
May 17th, 2023 - Carolyn Kierans

This is the description of the source model for the 511 keV positron annihilation emission in the Galaxy for DC2

Spatial: Simple Gaussian spatial models with a thin or thick disk. The bulge is based off of the model in Skinner et al. 2014 (and used in Siegert et al. 2016) and includes a narrow and broad buldge, and a central point source. The disk descriptions follow Skinner for the thin disk (3 deg scale height) and Siegert for the thick disk (10.5 deg scale height)

Spectral: Each spatial component has two spectral components. 

1) A line at 511 keV. This has a 2 keV FWHM width for the bulge components, and 3 keV FWHM for the disk emission.

2) the orthopositrium (OPs) continuum emission (as described by Ore 1949). The spectral shape of the OPs continuum is included in the OPsSpectrum.dat file and shown in ops_spectrum.pdf.

The relative fluxes of the OPs and 511 are scale such that the positronium fraction for the disk is 85% and the fraction for the bulge is 95%

Both models are included at 1x and 10x nominal flux 

Goals: 
1) Make full sky image of 511 keV (image deconvolution)
2) Determine scale height of disk emission (model fitting)
3) Extract the spectra of the bulge emission

## Nucleosynthesis 

### Al26
2023/May/16 Thomas Siegert
This is the description of the source model for diffuse 26Al line emission in the Galaxy at 1808.63 keV

There are two realisations from the same doubly exponential disk model.

The three-dimensional model is

rho(R,z,phi) = L / (4 * pi * Re^2 * ze) * exp(-R/Re) * exp(-|z|/ze),

where L is the total luminosity of 26Al in the Galaxy, i.e. L = M/m * p/tau with

m = 26 u as the atomic mass of 26Al nuclei, p = 0.9976 is the branching ratio to emit a photon, and
tau = 1.05 Myr is the lifetime of 26Al. This gives a quasi-persistent luminosity for a "living"
26Al mass M.

Re and ze are the scale radius and scale height, respectively.

R is the radial coordinate, i.e. R = sqrt((x-x0)^2 + (y-y0)^2), and z is the vertical coordinate, z = z' - z0.
x0 = 8.178, y0 = 0, and z0 = -0.019 are the coordinates of the Galactic centre seen from Earth.

All distance / size units are in kpc.

The line of sight integration is performed so that the flux per pixel (here: cartesian pixel grid with 3 deg
resolution) is in units of ph / cm2 / s / sr.


The two models are
Model 1:
M = 3 Msol -> L = 4.162e42 ph/s -> F = 1.278e-3 ph / cm2 / s
Re = 5.0
ze = 0.2
filenames: COSI_DC2_26Al_R5000_z0200_M30_3deg

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



Goals: Distinction between the two models of roughly equal flux.
Can we measure the scale heigt and radius in projected (Galactic) coordinates,
and can we do a profile likelihood with different 3D models to recover the input scale dimensions?
What does the reconstructed image look like, and can we determine the scale dimensions from a fit to the reconstructed image?


Files:
The .dat files for the input with cosima are created from the corresponding fits files, which also include information about
the images in the fits header.
PDF files are also created to check what the actual image should look like.

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


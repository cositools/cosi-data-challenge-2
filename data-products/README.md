# Data Products

### Simulated Data

We simulated 3 months of exposure time for an equatorial orbit at 550 km with a zenith pointing. The figure below shows the pointing of the telescope's z-axis as a function of time, in Galactic coordinates. 

<p align="center">
<img width="400"  src="images/telescope_pointing.png">
</p>

The simulations employ [MEGAlib](https://github.com/zoglauer/megalib) (*main* and *feature/dee2022* branches) via the COSI simulation pipepline ([cosi-data-challenges](https://github.com/cositools/cosi-data-challenges)), using version 12 of the COSI-SMEX mass model. This is a simplified version of the mass model, and we are currently working on a more detailed one which will be implemented in future data challenges. The far left image below shows the mass model from MEGAlib's geomega. For comparison, we also show a schematic of the mass model (middle) and the actual germanium detectors (right) from [Tomsick+23](https://ui.adsabs.harvard.edu/abs/2023arXiv230812362T/abstract).

<p align="center">
<img width="1000"  src="images/mass_model.png">
</p>

More specifically, for the source simulations (with *cosima*) we use the *main* branch of MEGAlib, together with the COSISMEX.Geo.setup version of the mass model. This has a high strip pitch for charge sharing. For the event reconstruction (with *revan*) we use the *feature/dee2022* branch, together with the COSISMEX.O64.geo.setup version of the mass model. This implements the new detector effects engine (i.e. dee2022). We simulate energies between 100 keV - 10 MeV. Note that COSI's nominal energy range is 200 keV - 5 MeV. Earth occultation is accounted for in the simulations by blocking all photons with arrival directions beyond $113^\circ$. We only select photons corresponding to Compton events. The full configuration files used for the event reconstruction (with *revan*) and extracting the data (with *mimrec*) can be found [here](https://github.com/cositools/cosi-data-challenges/tree/main/cosi_dc/Input_Files/Configuration_Files/Data_Challenges/Data_Challenge_2/DC2).

### Data Format
The data is provided in fits file format, which contains all of the photon information. If you are unfamiliar with analysis of Compton data, we highly recommend reading the [DC1](https://github.com/cositools/cosi-data-challenge-1) introduction page, which covers some of the key topics. In short, each photon event is decribed in terms of four axes: energy, time, compton scattering angle (&phi;), and event circle axis (&Psi; &Chi;). For Compton data, photons occupy what is known as the Compton data space, which is the 3-dimensional space defined by the axes &phi;, &psi;, and &chi;. For the actual analysis, &psi; and &chi; are defined using a healpix grid, allowing us to reduce this to a single dimenion (&Psi; &Chi;), i.e. the healpix pixel number.  

There are fits files for each individual component, for both sources and backgrounds. Each data challenge specifies the specific source files that you'll need. In order to create the dataset for a given data challenge, you will need to combine the source data with the background data. Instructions on how to do this are provided in the example jupyter notebooks, as well as the DataIO example in cosipy. There are 12 individual background components, so these will also need to be combined in order to obtain the total background. A file with the total background is also available. As a simplification, you can also use just the most dominant components.   

### Computing Resources 

<img  align="right" width="250"  src="images/clusters.png">

The source simulations were ran on NASA's [Discover cluster](https://www.nccs.nasa.gov/systems/discover). We used 1000 parallel CPUs for most of the source simulations, which allowed us to simulate them in a short time (typically less than ~10 minutes of total compute time per source). The source models were provided by the COSI science teams, and more information about them can be found in the respective **Data Challenges** section on the main page. The Background simulations were ran on the super cluster [MOGON](https://mogonwiki.zdv.uni-mainz.de/docs/introduction/what_is_mogon) in Mainz and Clemson University's [Palmetto](https://docs.rcd.clemson.edu/palmetto/) cluster. Simulations of the backgrounds were highly computationally intensive. The most time consuming simulations were the primary protons, which required 57.5 years of CPU time! This was accomplished using 6045 parallel cores. More details can be found in the [backgrounds](https://github.com/cositools/cosi-data-challenge-2/tree/main/backgrounds) directory.

### Accessing the Data

The data is hosted on wasabi. Files can be downloaded as follows:

**Orientation file:** <br />
wasabi path: COSI-SMEX/DC2/Data/Orientation/20280301_3_month.ori <br />

Copy from command line:
<pre>
os.system("AWS_ACCESS_KEY_ID=GBAL6XATQZNRV3GFH9Y4 AWS_SECRET_ACCESS_KEY=GToOczY5hGX3sketNO2fUwiq4DJoewzIgvTCHoOv aws s3api get-object  --bucket cosi-pipeline-public --key COSI-SMEX/DC2/Data/Orientation/20280301_3_month.ori --endpoint-url=https://s3.us-west-1.wasabisys.com 20280301_3_month.ori")
</pre>

**Background Files:** <br />

wasabi path: COSI-SMEX/DC2/Data/Backgrounds <br />

Components: <br />
total_bg_3months_unbinned_data.fits.gz <br />
cosmic_photons_3months_unbinned_data.fits.gz <br />
albedo_photons_3months_unbinned_data.fits.gz <br />
primary_protons_prompt_3months_unbinned_data.fits.gz <br />
primary_protons_decay_3months_unbinned_data.fits.gz <br />
primary_alphas_prompt_3months_unbinned_data.fits.gz <br />
primary_alpha_delayed_3months_unbinned_data.fits.gz <br />
primary_electrons_3months_unbinned_data.fits.gz <br />
primary_positrons_3months_unbinned_data.fits.gz <br />
NeutronAtm_prompt_3months_unbinned_data.fits.gz <br />
NeutronAtm_decay_3months_unbinned_data.fits.gz <br />
secondary_protons_prompt_3months_unbinned_data.fits.gz <br />
secondary_protons_delayed_3months_unbinned_data.fits.gz <br />

Copy from command line: <br />
Note: This particular example is for cosmic photons. For other components you'll need to change the file name accordingly. 
<pre>
os.system("AWS_ACCESS_KEY_ID=GBAL6XATQZNRV3GFH9Y4 AWS_SECRET_ACCESS_KEY=GToOczY5hGX3sketNO2fUwiq4DJoewzIgvTCHoOv aws s3api get-object  --bucket cosi-pipeline-public --key COSI-SMEX/DC2/Data/Backgrounds/cosmic_photons_3months_unbinned_data.fits.gz --endpoint-url=https://s3.us-west-1.wasabisys.com cosmic_photons_3months_unbinned_data.fits.gz")
</pre>

**Source Files:** <br />

wasabi path: COSI-SMEX/DC2/Data/Sources <br />

Sources:
For DC2 we simulated 30 different sources, running 49 different simulations in total (using multiple models for some of the sources). The source files needed for each respective data challenge are specified in the **Data Challenges** section on the main page.  

Copy from command line: <br />
Note: This particular example is for on of the 511 models. For other components you'll need to change the file name accordingly.
<pre>
os.system("AWS_ACCESS_KEY_ID=GBAL6XATQZNRV3GFH9Y4 AWS_SECRET_ACCESS_KEY=GToOczY5hGX3sketNO2fUwiq4DJoewzIgvTCHoOv aws s3api get-object  --bucket cosi-pipeline-public --key COSI-SMEX/DC2/Data/Sources/511_thin_diskx10_3months_unbinned_data.fits.gz --endpoint-url=https://s3.us-west-1.wasabisys.com 511_thin_diskx10_3months_unbinned_data.fits.gz")
</pre>

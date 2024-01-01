# Data Products

## Simulated Data

We simulated 3 months of exposure time for an equatorial orbit at 550 km with a zenith pointing. 


The simulations employ [MEGAlib](https://github.com/zoglauer/megalib) (*main* and *feature/dee2022* branches) via the COSI simulation pipepline ([cosi-data-challenges](https://github.com/cositools/cosi-data-challenges)), using version 12 of the COSI-SMEX mass model. Note that this is a simplified version of the COSI SMEX mass model. We are currently working on more detailed mass models which will be implemented in future data challenges. The far left image below shows the mass model from MEGAlib's goemega. For comparison, we also show a schematic of the mass model (middle) and the actual germanium detectors (right) from [Tomsick+23](https://ui.adsabs.harvard.edu/abs/2023arXiv230812362T/abstract).

<p align="center">
<img width="1000"  src="images/mass_model.png">
</p>

More specifically, for the source simulations (with *cosima*) we use the *main* branch, together with the COSISMEX.Geo.setup version of the mass model. This has a high strip pitch for charge sharing. For the event reconstruction (with *revan*) we use the *feature/dee2022* branch, together with the COSISMEX.O64.geo.setup version of the mass model. This implements the new detector effects engine (i.e. dee2022). We simulate energies between 100 keV - 10 MeV. Note that COSI's nominal energy range is 200 keV - 5 MeV. Earth occultation is accounted for in the simulations by blocking all photons with arrival directions beyond $113^\circ$. We only select photons corresponding to Compton events. The full configuration files used for extracting the data can be found [here](https://github.com/cositools/cosi-data-challenges/tree/main/cosi_dc/Input_Files/Configuration_Files/Data_Challenges/Data_Challenge_2/DC2).

<img  align="right" width="225"  src="images/clusters.png">

The source simulations were ran on NASA's [Discover cluster](https://www.nccs.nasa.gov/systems/discover). We used 1000 parallel CPUs for most of the source simulations, which allowed us to simulate them in a short time (typically less than ~10 minutes of total compute time per source). The Background simulations were ran on the super cluster [MOGON](https://mogonwiki.zdv.uni-mainz.de/docs/introduction/what_is_mogon) in Mainz and Clemson University's [Palmetto](https://docs.rcd.clemson.edu/palmetto/) cluster. More details about the background simulations can be found in the [backgrounds](https://github.com/cositools/cosi-data-challenge-2/tree/main/backgrounds) directory.








## Accessing Data

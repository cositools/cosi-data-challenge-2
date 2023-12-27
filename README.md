# COSI Data Challenge 2 (2024)

Welcome to the second COSI data challenge (DC2)! These data challenges are released on a yearly basis in preparation for the upcoming launch of the COSI Small Explorer mission in 2027 ([Tomsick+23](https://ui.adsabs.harvard.edu/abs/2023arXiv230812362T/abstract)). The main goals of the data challenges are to facilitate the development of the COSI data pipeline and analysis tools, and to provide resources to the astrophysics community to become familiar with COSI data. The first data challenge ([DC1](https://github.com/cositools/cosi-data-challenge-1)) was released in March 2023, and it was focused on data from the 2016 COSI balloon flight ([Kierans+17](https://ui.adsabs.harvard.edu/abs/2017arXiv170105558K/abstract)). The focus of DC2 is the satallite mission. With this data challenge we also make the first (alpha) release of our official high-level analysis tools, cosipy. 

## Getting Started 
The only software requirement for DC2 is [cosipy](https://github.com/cositools/cosipy). A general introduction into cosipy, including installation instructions, can be found in the [cosipy-intro](https://github.com/cositools/cosi-data-challenge-2/tree/main/cosipy-intro) directory. Note that cosipy is part of the larger COSITools, which is a broad collection of COSI data analysis tools, documentation, and verification data sets. COSITools can be installed by following the installation instructions [here](https://github.com/cositools/cosi-setup). This also includes MEGAlib, which is the main software program used for running simulations. However, unless you need MEGAlib and/or COSITools for other reasons, it's highly recommended to just install cosipy.    

The input models and challenges for DC2 were provided by the COSI science team. There are challenges for the different groups: Nucleosynthesis, Positron, GRB, Galactic, and Extragalactic. These are described in detail in the **Data Challenges** section below. We have created example jupyter notebooks demonstrating the basic tools that you'll need to complete each challenge. In addition to the main data challenges, we have given some extra challenges, which entails developing new functionality using the available tools in cosipy, e.g. methods for calculating light curves, SEDs, etc. Finally, we have also given some advanced challenges, which requires developing new tools. 

## Getting Help
Please submit a New Issue in the [cosipy](https://github.com/cositools/cosipy) git repository if you have issues with the code. If you have general feedback, or need further assistance, please reach out to the COSI Data Challenge team lead, Chris Karwin ([christopher.m.karwin@nasa.gov](mailto:christopher.m.karwin@nasa.gov)), the cosipy implementation lead, Israel Martinez-Castellanos ([israel.martinezcastellanos@nasa.gov](israel.martinezcastellanos@nasa.gov)), and/or the pipeline development lead Carolyn Kierans ([carolyn.a.kierans@nasa.gov](carolyn.a.kierans@nasa.gov)).

## Data Products
This year's data challenge is based on 3 months of exposure time, for an equatorial orbit at an altitude of 550 km, with a zenith pointing. Details of the simulations, simulated data, and information for accessing the data products can be found in the [data-products](https://github.com/cositools/cosi-data-challenge-2/tree/main/data-products) directory. 

## Backgrounds
In general, observations in the MeV band are hindered by high backgrounds (both instrumental and astrophysical). In order to ensure that COSI accomplishes it's main science goals, it is therefore crucial to have a firm understanding of these backgrounds. Although we are still in the early stages of development, with DC2 we have made significant progress in characterizing the background emission. Further details can be found in the [backgrounds](https://github.com/cositools/cosi-data-challenge-2/tree/main/backgrounds) directory. 

For analyzing data in DC2, the backgrounds are modeled using the actual backgrounds themselves. This is the ideal case, where the backgrounds are perfectly known, which of course is not realistic. In future data challenges we will be developing tools for estimating backgrounds when they are not perfectly known, as will be the case for the actual observations.    

## Data Challanges




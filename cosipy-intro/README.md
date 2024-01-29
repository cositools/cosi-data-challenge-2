# Introduction to cosipy

The cosipy library is [COSI](https://cosi.ssl.berkeley.edu)'s high-level analysis software. It allows you to extract imaging and spectral information from the data, as well as to perform statistical model comparisons. The cosipy product are meant to be ready for interpretation.

The main repository is hosted in https://github.com/cositools/cosipy

Here we explain how cosipy works internally, including the statistical analysis. We also end with a note on the next steps for cosipy, in the context of the second COSI data challenge release.

For the cosipy installation and usage instructions please refer to the main [cosipy documentation](https://cositools.github.io/cosipy/).

## cosipy and cositools

<img src="figures/cosi-pipelines-diagram.png" alt="the full COSI pipelines" width="500"/>

## The cosipy analysis



### Likelihood analysis

<img src="figures/likelihood.png" alt="Poisson likelihood" width="500"/>

$$\mathcal{L}(\hat{\color{red}s_j }|{\color{PineGreen}n_i}) = \max \mathcal{L}({\color{red}s_j }|{\color{PineGreen}n_i})$$

### The detector response: an introduction

<img src="figures/simple_drm_def.png" alt="" width="500"/>

<img src="figures/drm_convolution.png" alt="" width="500"/>

### The Compton Data Space

<img src="figures/CDS_detector.png" alt="" width="250"/>

<img src="figures/CDS_two_sources.png" alt="" width="500"/>

### The detector response: full version

<img src="figures/full_drm.png" alt="" width="250"/>

<img src="figures/cds_psichi_slices.png" alt="" width="500"/>

## The cosipy modules, inputs and outputs

<img src="figures/cosipy_modules.png" alt="" width="500"/>

## Integration with 3ML

$$\mathcal{L}_{}(\mathrm{model}) = \mathcal{L}_{\mathrm{NuSTAR}}(\mathrm{model}) \cdot \mathcal{L}_{\mathrm{GBM}}(\mathrm{model}) \cdot \mathcal{L}_{\mathrm{COSI}}(\mathrm{model}) \cdot \mathcal{L}_{\mathrm{LAT}}(\mathrm{model}) \cdot \mathcal{L}_{\mathrm{HAWC}}(\mathrm{model})\ldots$$

## Differences with cosipy-classic


## Next steps
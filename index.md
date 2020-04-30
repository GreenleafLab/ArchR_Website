# <img src="man/figures/ArchR_Logo_Integrated.png" alt="" width="200" >

[![Lifecycle: maturing](https://img.shields.io/badge/lifecycle-maturing-blue.svg)](https://www.tidyverse.org/lifecycle/#maturing)

ArchR is a full-featured R package for processing and analyzing single-cell ATAC-seq data. ArchR provides the most extensive suite of scATAC-seq analysis tools of any software available. Additionally, ArchR excels in both speed and resource usage, making it possible to analyze 1 million cells in 8 hours on a MacBook Pro laptop.

To get started, we recommend running through [the brief ArchR tutorial](articles/Articles/tutorial.html). For a detailed description of all of the features of ArchR applied to a test dataset of hematopoietic cells, please see the searchable [full manual](bookdown/index.html). If you havent already done so, we also recommend reading [the publication]() to get a better idea of what ArchR can do.

<hr>

# Installation of ArchR

__ArchR is designed to be run on Unix-based operating systems such as macOS and linux. If you are running Windows, the same installation instructions apply but you may run into unexpected issues.__

ArchR installation currently requires `devtools` and `BiocManager` for installation of GitHub and Bioconductor packages. Run the following commands to install the various dependencies used by ArchR:

```{r}
#First, install devtools (for installing GitHub packages) if it isn't already installed:
if (!requireNamespace("devtools", quietly = TRUE)) install.packages("devtools")

#Then, install BiocManager (for installing bioconductor packages) if it isn't already installed:
if (!requireNamespace("BiocManager", quietly = TRUE)) install.packages("BiocManager")

#Then, install ArchR:
devtools::install_github("GreenleafLab/ArchR", ref="master", repos = BiocManager::repositories())

#Lastly, install all of the ArchR dependencies that arent installed by default:
library(ArchR)
ArchR::installExtraPackages()
```
If any of these steps fails, you should identify the offending package and troubleshoot that individual installation before proceeding. Additionally, check below for some common trouble spots.

It is also highly recommended that you [install MACS2](https://github.com/taoliu/MACS/blob/master/INSTALL.md), which requires python, and have the `macs2` executable in your `PATH` variable. This will allow ArchR to call peaks using MACS2.

### Known trouble spots for installation
__If you are installing on macOS__, you will need a current version of GNU Fortran (gfortran) and XQuartz. For gfortran, you can download and install the `.dmg` file from [the gfortran github page](https://github.com/fxcoudert/gfortran-for-macOS/releases). For XQuartz, you can download and install the `.dmg` file from [the XQuartz project page](https://www.xquartz.org/).

__If you have installed R through Conda__, we have had reports of compile errors when installing ArchR that can be fixed by running `Sys.setenv(CONDA_BUILD_SYSROOT="/")` prior to executing the `devtools::install_github()` command as outlined in [this post](https://stackoverflow.com/questions/53637414/conda-build-r-package-fails-at-c-compiler-issue-on-macos-mojave).

<hr>

# The ArchR Workflow

<img src="man/figures/ArchR_Workflow_Horizontal.png" alt="">

<hr>

# How to cite ArchR?

Granja JM et al., An integrative and scalable software package for single-cell chromatin accessibility analysis. bioRxiv (2020)
[Download an RIS-format citation file here]().

Looking for scripts related to the publication? Check out the [GitHub page for the publication](https://github.com/GreenleafLab/ArchR_2020).

# Issues using ArchR?

ArchR is currently in __beta__. We expect there to be bumps in the road. If you think you have found a bug, please first install the latest version of ArchR via
```{r}
devtools::install_github("GreenleafLab/ArchR", ref="master", repos = BiocManager::repositories())
```
If this does not fix your problem, please report it as an issue on [Github](https://github.com/GreenleafLab/ArchR/issues).

If you think the documentation on this website or in the function annotations is unclear, please submit this as an issue on [Github](https://github.com/GreenleafLab/ArchR/issues) with the __documentation__ tag. If you have questions about ArchR usage, please refer to the [the searchable full user's manual](bookdown/index.html), [the FAQ section](articles/faq.html), and the [publication](https://greenleaf.stanford.edu/assets/pdf/). If none of these options help, [send us an email](mailto:archr.devs@gmail.com). We will do our best to respond to questions that are not otherwise answered in the documentation.



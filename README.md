# REnPortable
A portable R environment for Windows

## Introduction
REnPortable is a portable R x64 environment for Windows. It was put together using the [PortableApps.com](https://portableapps.com) launcher but is not endorsed by and does not comply with PortableApps.com requirements.

Please note that to use REnPortable you need to supply your own copy of [R(base)](https://cloud.r-project.org/), [Rtools](https://cloud.r-project.org/), [RStudio](https://www.rstudio.com/products/rstudio/download/) (Open Source Edition). REnPortable was tested with R v3.5.1, Rtools v3.4, and RStudio Desktop Open Source v1.1.453 on a Windows 10 (x64) machine. No support is offered for any of these programs. Please use the relevant support pages.

The reason for putting together REnPortablewas to have a complete, portable R environment to learn R and [RStan](http://mc-stan.org/). Therefore, all the prliminary work is complete to install the [RStan for Windows](https://github.com/stan-dev/rstan/wiki/Installing-RStan-on-Windows) packages into REnPortable.

## Getting started
You can download the REnPortable zip file and unzip to any place on a Windows x64 machine. If you have installled versions of R(base), Rtools, or RStudio, you can copy the files into the appropriate folders in the Apps directory. If you do not have installed versions of R and Rtools you will need to install them (Choose to install the x64 verions only), copy the files to the correct folders and then remove the installed programs. RStudio Desktop can be downloaded as a zip file.

Packages for R are added to the folder Data\RLibrary.

The working directory, R_USER, HOME, and R_LIBS_USER are in Data\RData

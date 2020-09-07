# REnPortable
A portable R environment for Windows

## Introduction
REnPortable is a portable 64-bit R environment for Windows. It was put together using the [PortableApps.com](https://portableapps.com) launcher but is not endorsed by and does not comply with PortableApps.com requirements.

Please note that to use REnPortable you need to supply your own 64-bit copy of [R(base)](https://cloud.r-project.org/), [Rtools](https://cloud.r-project.org/), [RStudio](https://www.rstudio.com/products/rstudio/download/) (Open Source Edition). REnPortable was tested with R v4.0, Rtools v4.0, and RStudio Desktop Open Source v1.3 on a Windows 10 (x64) machine. No support is offered for any of these programs -- please use the relevant support pages.

The reason for putting together REnPortable was to have a complete, portable R environment to learn R and [RStan](http://mc-stan.org/). Therefore, all the preliminary work is complete to install the [RStan for Windows](https://github.com/stan-dev/rstan/wiki/Installing-RStan-on-Windows) packages into REnPortable.

## Getting started
1. The size of the 64-bit versions of R, RStudio, and Rtools together is approximately 1.1 GB. If you want to add other R packages you will need room for these too. For example, RStan plus dependencies adds another 350 MB (total ~1.8 GB on disk). You could save ~700 MB by excluding Rtools but REnPortable has not been tested without Rtools and RStan will not work without Rtools.
1. You can download the REnPortable zip file and unzip to any place on a Windows 64-bit machine, USB, or external drive. 
1. If you have installed 64-bit versions of R, Rtools, or RStudio, you can copy the program files for each into the appropriate folders in the Apps directory (see Folder structure below).
1. If you have not installed 64-bit versions of R and Rtools you will need to install them (choose to install the 64-bit versions only), copy the program files to the correct folders in REnPortable and then uninstall R and Rtools. RStudio Desktop can be downloaded as a zip file and unzipped into the appropriate RStudio folder.
1. Launch REnPortable.exe

**Note:** Every time you start REnPortable, RStudio will ask you for the version of R you wish to use. Please select the version of R that is in `...\REnPortable\App\Rbase` (see below); if you do not have R installed, this should be the only version listed. This is a behaviour of RStudio and cannot be change (AFAIK).

**Note:** When it is time to update R(base), Rtools, and RStudio program files, it is usually best to delete the old files first and then copy/paste the new ones to prevent old, unused files or versions of files from causing problems.

## Folder structure
### App
1. **AppInfo** – files for portability of REnPortable, there is no reason to edit these unless you know what you are doing.
1. **CmdStan** - unpack [CmdStan](https://mc-stan.org/users/interfaces/cmdstan.html) here before building.
1. **Rbase** – where to put the R(base) program files (and updated versions of R). Updated R base packages are saved here.
1. **RStudio** – where to put the RStudio program files (and updated versions of RStudio).
1. **Rtools** – where to put the Rtools program files (and updated versions of Rtools).
1. **TinyTex** - for [TinyTex](https://yihui.org/tinytex/) files.

### Data
1. **RData** – the working directory\folder for R and RStudio, e.g. `R_USER` and `HOME`.
1. **RLibrary** – Contributed R packages are saved to this folder (i.e. `R_LIBS_USER`) to separate them from the R program. If you install RStan, this is where the files will be saved rather than under `\App\Rbase`. It means that R(base) can be updated independently of any contributed packages you add.
1. **Settings** - You probably do not need to change anything in this folder unless something goes wrong.
   1. **Local**
       - **R** – R crash-handler files. Copied to your profile under `\Users\[username]\AppData\Local\R` when REnPortable starts and then copied back when close REnPortable closes.
       - **RStudio** – Contains `rstudio-desktop.json` file. Copied to your profile under `\Users\[username]\AppData\Local\RStudio` when REnPortable starts and then copied back when close REnPortable closes.
       - **RStudio-Desktop** – RStudio Desktop files. Are copied to your profile under `\Users\[username]\AppData\Local\RStudio-Desktop` when REnPortable starts and then copied back when close REnPortable closes.
   1. **Rbase** - Contains `Renviron.site` file. The file has settings for R such as the location of `HOME`, `R_HISTFILE`, `R_USER`, and `R_LIBS_USER`. This file is copied to `App\Rbase\etc` when REnPortable starts and then copied back when close REnPortable closes.
   1. **Roaming**
       - **R** - For rsconnect. Copied to your profile under `\Users\[username]\AppData\Roaming\R` when REnPortable starts and then copied back when close REnPortable closes.
       - **RStudio** - RStudio preferences. Copied to your profile under `\Users\[username]\AppData\Roaming\R` when REnPortable starts and then copied back when close REnPortable closes. The file `rstudio-prefs.json` includes the initial working directory for RStudio which is set to `\Data\RData\` in REnPortable.
   1. **Temp** – temporary files for R/RStudio (I haven't seen anything saved there yet but who knows?).

### Other
Various files for portability, there is no reason to edit these unless you know what you are doing.

## Install RStan
If you have copied the program files for R, Rtools, and RStudio into the correct folders, then follow the instructions for getting [RStan](https://mc-stan.org/users/interfaces/rstan.html) up and running. You do not needed to
1. [Configure of the C++ toolchain](https://github.com/stan-dev/rstan/wiki/RStan-Getting-Started#configuration-of-the-c-toolchain) because it has already been done for you.
1. You can [verify that Rtools can be used in R](https://github.com/stan-dev/rstan/wiki/Installing-RStan-on-Windows#verify-that-rtools-can-be-used-in-r).

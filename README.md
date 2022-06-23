# REnPortable

A portable R environment for Windows.

## Introduction

REnPortable is a portable **64-bit only** R environment for Windows. It was put together using the [PortableApps.com](https://portableapps.com) launcher but is not endorsed by and does not fully comply with all PortableApps.com requirements.

At a minimum, REnPortable 4.2 needs extracted copies of [R (base) 4.2+](https://cloud.r-project.org/) and [RStudio Desktop 2021.09.0+](https://www.rstudio.com/). Optionally, you can include your own copies of [TinyTex](https://yihui.org/tinytex/), [Rtools 4.2](https://cloud.r-project.org/), and [CmdStan 2.29+](https://mc-stan.org/). REnPortable was tested on Windows 10 Pro (x64) and Windows 11. No support is offered for any of these programs; please use the relevant support pages. 

## Getting started

1. The extracted size of R and RStudio is approximately 800 MB. When you include Rtools (~3.9 GB), CmdStan (~1.0 GB), and TinyYex (~270 to 525 MB) altogether this is approximately 6.2 GB. You will want to add R packages and you will need room for these too. For example, my R packages library is currently ~900 MB.
1. You can download the [REnPortable zip file](https://github.com/conchra/REnPortable/releases/) and unzip to any place on a Windows machine, USB, or external drive.
1. If you have installed current versions of the various programs, you can copy the files for each into the appropriate folders in the Apps directory (see Folder structure below).
1. If you have not installed the programs, you will need to install them, copy the program files to the correct folders in REnPortable and then uninstall the programs. RStudio Desktop can be downloaded as a zip file and unzipped into the appropriate RStudio folder.
1. Run `REnPortable42.exe`.

**Note** - When you start REnPortable, RStudio may ask you for the version of R you wish to use. Please select the version of R that is in `\App\Rbase42` (see folder structure below); if you do not have R installed, this should be the only version listed.

**Note** - When it is time to update R, Rtools, RStudio, and other program files, it is usually best to delete the old files first and then copy/paste the new ones. This prevents old, unused files or versions of files from causing problems.

## Folder structure

### `REnPortable\App` folder

1. **AppInfo** – Files for portability of REnPortable, there is no reason to edit these unless you know what you are doing.
1. **CmdStan** - (Optional) Unpack [CmdStan](https://mc-stan.org/users/interfaces/cmdstan.html) here before building. You can comment out all the lines in `\CmdStan\install-tbb.bat` because the path is already set for you.
1. **Rbase42** – Where to put the [R(base)](https://cloud.r-project.org/) program files (and updated versions of R). Updated R base packages are also saved here.
1. **RStudio** – Where to put the [RStudio](https://www.rstudio.com) program files (and updated versions of RStudio).
1. **Rtools42** – (Optional) Where to put the [Rtools](https://cloud.r-project.org/) program files (and updated versions of Rtools).
1. **TinyTex** – (Optional) For [TinyTex](https://yihui.org/tinytex/) files. If you install TinyTex from R/RStudio (`install_tinytex(force = TRUE, dir = tinytex_root(), add_path = FALSE)`) the main application files will go here.

### `REnPortable\Data` folder

1. **RData** – The working directory\folder for R and RStudio, e.g. `R_USER` and `HOME`.
1. **RLibrary42** – Contributed R packages are saved to this folder (i.e. `R_LIBS_USER`) to separate them from the R program.
1. **Settings** - You probably do not need to change anything in this folder unless something goes wrong. Most of the settings files and folders are copied to the user profile when REnPortable starts. When REnPortable closes, the folders and files are moved back to their original locations. This means that start and close times may be slower than for installed programs.
   1. **Local** - Copied to `...\Users\[username]\AppData\Local\...`
       - **R** – R crash-handler files.
       - **RStudio** – General RStudio files.
       - **RStudio-Desktop** – RStudio Desktop files.
   1. **Profile** - Contains the `.bash_history` file.
   1. **Rbase42** - Contains `Renviron.site` file. The file has settings for R such as the location of `HOME`, `R_HISTFILE`, `R_USER`, and `R_LIBS_USER`. This file is copied to `App\Rbase\etc` when REnPortable starts and then moved back when close REnPortable closes.
   1. **Roaming** - Copied to `...\Users\[username]\AppData\Roaming\...`
       - **R** - For rsconnect.
       - **RStudio** - RStudio preferences. The file `rstudio-prefs.json` includes the initial working directory for RStudio which is set to `\Data\RData\` in REnPortable.
1. **Temp** – Required for temporary files for R/RStudio (I haven't seen anything saved there yet but who knows?).

### `REnPortable\Other` folder

Various files for portability, there is no reason to edit these unless you know what you are doing.

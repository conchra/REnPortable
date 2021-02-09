# REnPortable

A portable R environment for Windows

## Introduction

REnPortable is a portable 64-bit only R environment for Windows. It was put together using the [PortableApps.com](https://portableapps.com) launcher but is not endorsed by and does not fully comply with all PortableApps.com requirements.

To use REnPortable you need to supply your own 64-bit copy of [R(base)](https://cloud.r-project.org/), [Rtools](https://cloud.r-project.org/), [RStudio Desktop](https://www.rstudio.com/) (Open Source Edition). REnPortable was tested with R v4.0+, Rtools v4.0, and RStudio Desktop v1.3.+ on Windows 10 Pro (x64). No support is offered for any of these programs; please use the relevant support pages.

The reason for putting together REnPortable was to have a complete, portable R environment to learn R and [RStan](https://mc-stan.org/users/interfaces/rstan.html). Therefore, all the preliminary work is complete to install the RStan package and dependencies in REnPortable. If you copy the program files for R, Rtools, and RStudio into the correct folders, then the following instructions for getting RStan up and running can be skipped:
   1. [Checking the C++ toolchain](https://github.com/stan-dev/rstan/wiki/RStan-Getting-Started#checking-the-c-toolchain), should work but you can always double check.
   1. [Configure of the C++ toolchain](https://github.com/stan-dev/rstan/wiki/RStan-Getting-Started#configuration-of-the-c-toolchain) because it has already been done for you (see `\Data\RData\.R\Makevars.win`).

I have also added support for [CmdStan](https://mc-stan.org/users/interfaces/cmdstan.html), [TinyTex](https://yihui.org/tinytex/), and [Portable Git](https://github.com/git-for-windows/git/releases).

## Getting started

1. The size of the 64-bit versions of R, RStudio, and Rtools together is approximately 1.8 GB. If you want to add other R packages you will need room for these too. For example, RStan plus dependencies adds another ~350 MB. You could save ~700 MB by excluding Rtools but REnPortable has not been tested without Rtools and RStan will not work without Rtools.
1. You can download the [REnPortable zip file](https://github.com/conchra/REnPortable/releases/) and unzip to any place on a Windows 64-bit machine, USB, or external drive.
1. If you have installed 64-bit versions of R, Rtools, or RStudio, you can copy the program files for each into the appropriate folders in the Apps directory (see Folder structure below).
1. If you have not installed 64-bit versions of R and Rtools you will need to install them (choose to install the 64-bit versions only), copy the program files to the correct folders in REnPortable and then uninstall R and Rtools. RStudio Desktop can be downloaded as a zip file and unzipped into the appropriate RStudio folder.
1. Run `REnPortable.exe`.

**Note** - When you start REnPortable, RStudio may ask you for the version of R you wish to use. Please select the version of R that is in `\App\Rbase` (see folder structure below); if you do not have R installed, this should be the only version listed.

**Note** - When it is time to update R(base), Rtools, RStudio, and other program files, it is usually best to delete the old files first and then copy/paste the new ones. This prevents old, unused files or versions of files from causing problems.

## Folder structure

### `REnPortable\App` folder

1. **AppInfo** – Files for portability of REnPortable, there is no reason to edit these unless you know what you are doing.
1. **CmdStan** - (Optional) Unpack [CmdStan](https://mc-stan.org/users/interfaces/cmdstan.html) here before building. You can comment out all the lines in `\CmdStan\install-tbb.bat` because the path is already set for you.
1. **PortableGit** - (Optional) [Portable Git for Windows](https://github.com/git-for-windows/git/releases) (64-bit) can be extracted here if you use git with R. The path to `\PortableGit\bin` and `\PortableGit\cmd` is already set for you.
1. **Rbase** – Where to put the [R(base)](https://cloud.r-project.org/) program files (and updated versions of R). Updated R base packages are also saved here.
1. **RStudio** – Where to put the [RStudio](https://www.rstudio.com) program files (and updated versions of RStudio).
1. **Rtools** – Where to put the [Rtools](https://cloud.r-project.org/) program files (and updated versions of Rtools). The empty folders `home`, `opt`, and `tmp` are required for Rtools to work properly.
1. **TinyTex** - (Optional) For [TinyTex](https://yihui.org/tinytex/) files. If you install TinyTex from R/RStudio (`install_tinytex(force = TRUE, dir = tinytex_root(), add_path = FALSE)`) the main application files go here.

### `REnPortable\Data` folder

1. **RData** – The working directory\folder for R and RStudio, e.g. `R_USER` and `HOME`.
1. **RLibrary** – Contributed R packages are saved to this folder (i.e. `R_LIBS_USER`) to separate them from the R program. If you install RStan, this is where the files will be saved rather than under `\App\Rbase`. It means that R(base) can be updated independently of any contributed packages you add.
1. **Settings** - You probably do not need to change anything in this folder unless something goes wrong. Most of the settings files and folders are copied to the user profile when REnPortable starts. When REnPortable closes, the folders and files are moved back to their original locations. This means that start and close times may be slower than for installed programs.
   1. **Local** - Copied to `...\Users\[username]\AppData\Local\...`
       - **R** – R crash-handler files.
       - **RStudio** – Contains `rstudio-desktop.json` file.
       - **RStudio-Desktop** – RStudio Desktop files.
   1. **Profile** - Contains the `.bash_history` file.
   1. **Roaming** - Copied to `...\Users\[username]\AppData\Roaming\...`
       - **R** - For rsconnect.
       - **RStudio** - RStudio preferences. The file `rstudio-prefs.json` includes the initial working directory for RStudio which is set to `\Data\RData\` in REnPortable.
1. **Temp** – Required for temporary files for R/RStudio (I haven't seen anything saved there yet but who knows?).

### `REnPortable\Other` folder

Various files for portability, there is no reason to edit these unless you know what you are doing.

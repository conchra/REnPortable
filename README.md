# REnPortable

A portable R environment for Windows.

## Introduction

REnPortable is a portable **64-bit only** R environment for Windows. It was put together using the [PortableApps.com](https://portableapps.com) launcher but is not endorsed by and does not fully comply with all PortableApps.com requirements.

At a minimum, REnPortable 4.5 needs extracted copies of [R (base) 4.5+](https://cloud.r-project.org/) and [RStudio Desktop 2025+](https://www.rstudio.com/). Optionally, you can include copies of [TinyTex](https://yihui.org/tinytex/), [Rtools45](https://cloud.r-project.org/), [CmdStan 2.36+](https://mc-stan.org/), and [PortableGit](https://github.com/git-for-windows/git). REnPortable was tested on Windows 11 Pro (x64). No support is offered for any of these programs; please use the relevant program's support pages. 

## Getting started

1. The extracted size of R and RStudio is approximately 1.25 GB. When you include Rtools45 (~3.0 GB), CmdStan (~1.1 GB), and TinyTex (~270 to 620 MB) altogether this is approximately 6.5 GB. You will want to add R packages and you will need room for these too. For example, my R packages library is currently ~1.3 GB.
1. You can download the [REnPortable zip file](https://github.com/conchra/REnPortable/releases/) and unzip to any place on a Windows machine, USB, or external drive.
1. If you have installed current versions of the various programs, you can copy the files for each into the appropriate folders in the Apps directory (see Folder structure below).
1. If you have not installed the programs, you will need to install them, copy the program files to the correct folders in REnPortable and then uninstall the programs. RStudio Desktop can be downloaded as a zip file and unzipped into the appropriate RStudio folder.
1. Run `REnPortable42.exe`.

**Note** - When you start REnPortable, RStudio may ask you for the version of R you wish to use. Please select the version of R that is in `\App\Rbase45` (see folder structure below); if you do not have R installed, this should be the only version listed.

**Note** - When it is time to update R, Rtools, RStudio, and other program files, it is usually best to delete the old files first and then copy/paste the new ones. This prevents old, unused files or versions of files from causing problems.

## Folder structure

The R, Rtools, and RLibrary folders are named with R's major and minor version number (e.g. `45` for version 4.5) appended because sometimes you may want to have access to and be able to run more than one version of R, Rtools, and associated packages in the library.

### `REnPortable\App` folder

1. **AppInfo** – Files for portability of REnPortable, there is no reason to edit these unless you know what you are doing.
1. **CmdStan** – (Optional) Unpack [CmdStan](https://mc-stan.org/users/interfaces/cmdstan.html) here before building. You can comment out all the lines in `\CmdStan\install-tbb.bat` because the path is already set for you.
1. **PortableGit** – (Optional) Where to put the [PortableGit](https://github.com/git-for-windows/git) files.
1. **Rbase45** – Where to put the [R(base)](https://cloud.r-project.org/) program files (and updated versions of R). Updated R base packages are also saved here.
1. **RStudio** – Where to put the [RStudio](https://www.rstudio.com) program files (and updated versions of RStudio).
1. **Rtools45** – (Optional) Where to put the [Rtools45](https://cloud.r-project.org/) program files (and updated versions of Rtools42).
1. **TinyTex** – (Optional) For [TinyTex](https://yihui.org/tinytex/) files. If you install TinyTex from the `tinytex` package in R/RStudio (`install_tinytex(force = TRUE, dir = tinytex_root(), add_path = FALSE)`) the main application files will go here.

### `REnPortable\Data` folder

1. **RData** – The working directory\folder for R and RStudio, e.g. `R_USER` and `HOME`.
1. **RLibrary45** – Contributed R packages are saved to this folder (i.e. `R_LIBS_USER`) to separate them from the R program.
1. **Settings** – You probably do not need to change anything in this folder unless something goes wrong. Most of the settings files and folders are copied to the user profile when REnPortable starts. When REnPortable closes, the folders and files are moved back to their original locations. This means that start and close times may be slower than for installed programs.
   1. **Bash** – Contains the `.bash_history` file.
   1. **Local** – Copied to `.\Users\[username]\AppData\Local\`
       - **R** – R crash-handler files.
       - **RStudio** – General RStudio files.
       - **RStudio-Desktop** – RStudio Desktop files.
   1. **Rbase** – Contains `Renviron.site` file. The file has settings for R such as the location of `HOME`, `R_HISTFILE`, `R_USER`, and `R_LIBS_USER`. This file is copied to `App\Rbase\etc` when REnPortable starts and then moved back when REnPortable closes.
   1. **Roaming** – Copied to `.\Users\[username]\AppData\Roaming\`
       - **R** - For rsconnect.
       - **RStudio** – RStudio preferences. The file `rstudio-prefs.json` includes the initial working directory for RStudio which is set to `\Data\RData\` in REnPortable.
   1. **RStudioProfile** – RStudio uses Electron and this is the profile folder. The file `config.json` has the path to `R.exe`, the main R executable.
   1. **TinyTex** – Contains the `texmf.cnf` file.
1. **Temp** – Required for temporary files for R/RStudio (I haven't seen anything saved there yet but who knows?).

### `REnPortable\Other` folder

Various help and license files.

# Dyssol
Dyssol is a tool for dynamic flowsheet simulation of complex production processes with advanced treatment of granular materials.

For more information, please check the [documentation](https://github.com/FlowsheetSimulation/Dyssol-open/tree/master/Documentation). 

Video intruductions: [Basics](https://youtu.be/IHzr0NVYW6M) and [Simulation of granulation process](https://youtu.be/ni54JwvCVDc)

For new versions and updates, please visit our [github page](https://github.com/FlowsheetSimulation/Dyssol-open/releases).

To cite Dyssol please use the following: 
Skorych, V., Dosta, M., & Heinrich, S. (2020). Dyssol — An open-source flowsheet simulation framework for particulate materials. SoftwareX, 12, 100572. [doi.org/10.1016/j.softx.2020.100572](https://doi.org/10.1016/j.softx.2020.100572).

# Installation requirements 
Dyssol should install and work on all latest versions of Windows.
Requires Visual C++ Redistributable for Visual Studio 2019 to run.

# Installation
Run the provided installer and follow the instructions.

# Compilation
A fully functional version can be compiled and built with Microsoft Visual Studio 2019. A command-line version can also be built for Linux.

## Windows
### Compilation requirements on Windows
- [Microsoft Visual Studio 2019](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=16), Desktop development with C++ workload.
- [Qt 5.15.2](https://www.qt.io/download-qt-installer) msvc2019 / msvc2019_64
- [Qt Visual Studio Tools](https://marketplace.visualstudio.com/items?itemName=TheQtCompany.QtVisualStudioTools2019) for Visual Studio 2019
- [CMake](https://cmake.org/download/) 3.14 or higher
- [Git](https://git-scm.com/downloads)
- PowerShell 5.0 (usually shipped with Windows)

### Compilation procedure on Windows
- Make sure all programs and tools from the [list](#Compilation-requirements) are installed.
- Setup Qt Visual Studio Tools extension to point to the installed Qt libraries. In Visual Studio 2019, go to Extensions → Qt VS Tools → Qt Options → Add → ... → Navigate in the Qt installation directory to `Qt/5.15.0/msvc2019` → OK. Repeat for `Qt/5.15.0/msvc2019_64`.
- Compile and build external statically linked libraries: zlib, HDF5, SUNDIALS. To do this, navigate to `Dyssol/ExternalLibraries/` and execute file `RunAll.bat`. It will start building all the required libraries by executing files `CompileZLib.ps1`, `CompileHDF5.ps1`, `CompileSundials.ps1`. To use the scripts, the following requirements apply: Visual Studio 16 2019, CMake, PowerShell 5.0.
- Open `Dyssol/Dyssol.sln` with Visual Studio and build the solution.

Also, other versions of Microsoft Visual Studio can be used, but additional preparations are required:
- Install build tools for the corresponding Visual Studio.
- Configure all *.ps1 scripts to use the required version of Visual Studio build tools before running `Dyssol/ExternalLibraries/RunAll.bat`.
- If the Models Creator tool is required, files associated with it may need to be updated. They to be found in `Dyssol/DyssolInstallers/Data/VCProject/`.

## Linux
### Compilation requirements on Linux
- gcc-9, g++-9
- CMake 3.14 or higher

### Compilation procedure on Linux
- Navigate to `Dyssol/DyssolLinux/`
- Install the required build tools manually or run
```sh
$ sudo ./install_gcc.sh
$ sudo ./install_cmake.sh
```
- Build and install all required third-party libraries.
```sh
$ ./install_hdf5.sh
$ ./install_sundials.sh
```
- Gather all source files.
```sh
$ ./copy_files.sh
```
- Build Dyssol.
```sh
$ ./make_dyssol.sh
```
- The compiled executable file and all the units libraries will appear in `Dyssol/DyssolLinux/compiled/`

# Code organization
- BaseSolvers - interfaces for equation solvers
- CahceHandlers - dynamic data caching
- Documentation - manuals
- DyssolConsole - main project for command-line version of Dyssol
- DyssolInstallers - scripts and data needed to build installers for Windows
- DyssolLinux - scripts for compilation on Linux
- DyssolMainWindow - main project for GUI version of Dyssol
- EquationSolvers - built-in equation solvers based on SUNDIALS library
- ExternalLibraries - all third-party libraries and scripts to build them
- GUIDialogs - main GUI components
- GUIWidgets - auxiliary GUI components and tools
- HDF5Handler - wrapper for HDF5 library
- MaterialsDatabase - database of materials
- ModelsAPI - part of the core components needed to develop units
- Modules - additional modules
- PropertySheets - projects settings for Visual Studio
- SimulatorCore - core components
- Solvers - all solvers and templates for them
- Units - all units and temp0lates for them
- Utilities - auxiliary program components
- Dyssol.sln - main file of the Visual Studio solution
- LICENSE - license agreement
- Materials.dmdb - exemplary database of materials 
- README - this file

# Installation directory organization 
- Example flowsheets – flowsheet examples 
- Example units – source code of units (C++)
- Example solvers – source code of solvers (C++)
- Help – documentation files (pdf)
- Licenses – information about licenses 
- platforms - Qt libraries to support GUI
- Solvers – libraries of developed solvers
- styles - Qt libraries to support GUI
- Units – libraries of developed units
- VCProject – Models Creator tool: template project for Microsoft Visual Studio 
- Dyssol.exe – main executable of Dyssol
- DyssolC.exe – command-line utility
- ExampleConfigFile.txt – example configuration file for command-line utility
- LICENSE - license agreement
- Materials.dmdb – default materials database
- Qt5*.dll - Qt libraries to support GUI
- unins000.exe – Dyssol uninstaller

# Third-party tools and libraries
- [Qt 5.15.2](https://www.qt.io/) – The Qt Company - [LGPL v3](https://doc.qt.io/qt-5/lgpl.html)
- [HDF5 v1.12.0](https://www.hdfgroup.org/downloads/hdf5/) – HDF Group - [HDF license](https://support.hdfgroup.org/ftp/HDF5/releases/COPYING)
- [zlib v1.2.11](https://www.zlib.net/) – Jean-loup Gailly and Mark Adler - [zlib license](https://www.zlib.net/zlib_license.html)
- [SUNDIALS v5.6.1](https://computing.llnl.gov/projects/sundials/) – Lawrence Livermore National Security and Southern Methodist University - [BSD-3-Clause license](https://computing.llnl.gov/projects/sundials/license)
- [Inno Setup v6.0.5](https://jrsoftware.org/isinfo.php) – Jordan Russell - [Inno Setup license](http://www.jrsoftware.org/files/is/license.txt)
- [KISS FFT v131](https://github.com/mborgerding/kissfft) – Mark Borgerding - [BSD-3-Clause license](https://github.com/mborgerding/kissfft/blob/master/COPYING)

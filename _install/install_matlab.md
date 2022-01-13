---
layout: page
sectionid: install_matlab
title: Install MATLAB
permalink: /install/install_matlab/
---

Here we provide details on the configuration of MATLAB for BIODICA. The python implementation of the stabilized-ica package is now used by default but we still provide a MATLAB option only for historical and compatibility reasons.

-----

 1. Run *install.bat* (Windows) or *install.sh* in your local root folder for BIODICA (this will copy the MATLAB RunTime binaries). To do so, open the terminal and run the following command :

    **Windows** 
    ```
    local_path_to_root_folder\install.bat
    ```
    **Other operating systems**
    ```
    local_path_to_root_folder\install.sh
    ```

2. Select the "use MATLAB for ICA computations" option in BIODICA Navigator parameters and press "OK".
     
     <center><img src="../../assets/img/MATLAB_1.png" wide="auto"  height="400"></center>

     You can also directly modify the *config* file located in the local root folder for BIODICA:

     ```
     ICAImplementation = matlab
     ```

3. For the last step of the configuration of MATLAB, you have three options

    * If you can use docker (recommended) for performing Matlab computations (then MATLAB or binaries are not required and no configuration of MATLAB Runtime is needed) then execute first the following command line in your terminal

        ```
        docker pull auranic/biodica
        ```

        and select the "Use docker" option in BIODICA Navigator parameters or directly modify the *config* file with

        ```
        UseDocker = true
        ```
        
        <center><img src="../../assets/img/MATLAB_2.png" height="400" wide="auto"></center>

    * If you already have an installed MATLAB, then you can specify the path to MATLAB bin folder (e.g `C:\Matlab\bin`) in BIODICA Navigator parameters or directly in the *config* file with
        ```
        MATLABFolder = C:\Matlab\bin
        ```

        <center><img src="../../assets/img/MATLAB_3.png" height="400" wide="auto"></center>

    * You can also leave *MATLABfolder* option empty and the "Use docker" option unselected.

        <center><img src="../../assets/img/MATLAB_4.png" height="400" wide="auto"></center>

        You will then have the responsability to download and configure the MATLAB RunTime library, specify if necessary the path to the Runtime library files such that the executables in *bin/doICA/* folder could be run without "library not found" message. Under Windows, the installer will take care of this automatically, while under Linux it can require some setting of the environment variables.

        Windows: <a href="https://fr.mathworks.com/supportfiles/downloads/R2015a/deployment_files/R2015a/installers/win64/MCR_R2015a_win64_installer.exe">Link to the corresponding version of MATLAB Runtime (version 8.5, 64 bit)</a>

        Linux: <a href="https://fr.mathworks.com/supportfiles/MCR_Runtime/R2013a/MCR_R2013a_glnxa64_installer.zip">Link to the corresponding version of MATLAB Runtime (version 8.1, 64 bit)</a>
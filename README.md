# NIOS_II_EDS_on_Ubuntu_20.04
How to install NIOS 2 EDS contained in Quartus Prime Lite 20.1.1 on Ubuntu 20.04

## Install system Prerequisites

taken from https://www.intel.com/content/dam/www/programmable/us/en/pdfs/literature/manual/quartus_install.pdf

```
sudo apt install libc6:i386 libncurses5:i386 libxtst6:i386 libxft2:i386 libstdc++6:i386 libc6-dev-i386 libxft2 lib32z1 lib32ncurses6 libbz2-1.0:i386 libpng16-16
```

Note: some libraries were not available in the version described in the installation manual (lib32ncurses5, lib32bz2-1.0 and libpng12) and therefore substituted with the available pendant (untested wether or not the software would work without them!)

## Download Quartus Prime Lite and Device Support Packages

Go to https://fpgasoftware.intel.com/20.1.1/?edition=lite&platform=linux and select either of:
- Quartus Prime Lite Edition Software (Device support included) (6.4GB!!!)
- Quartus Prime (includes Nios II EDS) + Device Support Package for your target device

## Install Quartus Prime Lite
- 
  ```
  cd <download_dir>
  chmod +x QuartusLiteSetup-20.1.XXXX-linux.run
  ./QuartusLiteSetup-20.1.XXXX-linux.run
  ```
- Follow the steps shown on the graphical installer.

Note: the device package in the same folder was automatically added to the installation during the process

## Install Eclipse needed for NIOS2EDS

originally described in https://www.intel.com/content/www/us/en/programmable/documentation/lro1419794938488.html#zyy1556500180085

- Download:
  ```
  cd <eclipse_download_folder>/
  wget https://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/mars/2/eclipse-cpp-mars-2-linux-gtk-x86_64.tar.gz
  ```
- Installation:
  ```
  cd <your_quartus_installation>/nios2eds/bin
  tar -xzvf <eclipse_download_folder>/eclipse-cpp-mars-2-linux-gtk-x86_64.tar.gz
  mv eclipse eclipse_nios2
  tar -xzvf eclipse_nios2_plugins.tar.gz
  ```
- Installation complete, start NIOS2EDS with:
  ```
  ./eclipse-nios2
  ```

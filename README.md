# NIOS_II_EDS_on_Ubuntu_20.04
How to install NIOS 2 EDS contained in Quartus Prime Lite 20.1.1 on Ubuntu 20.04

## Install system Prerequisites

taken from the [official installation instructions](https://www.intel.com/content/dam/www/programmable/us/en/pdfs/literature/manual/quartus_install.pdf)

```
sudo apt install libc6:i386 libncurses5:i386 libxtst6:i386 libxft2:i386 libstdc++6:i386 libc6-dev-i386 libxft2 lib32z1 lib32ncurses6 libbz2-1.0:i386 libpng16-16
```

Note: some libraries were not available in the version described in the installation manual (lib32ncurses5, lib32bz2-1.0 and libpng12) and therefore substituted with the available pendant (untested wether or not the software would work without them!)

## Download Quartus Prime Lite and Device Support Packages

Go to [official download page](https://fpgasoftware.intel.com/20.1.1/?edition=lite&platform=linux) and select either of:
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

as originally described in the [official documentation](https://www.intel.com/content/www/us/en/programmable/documentation/lro1419794938488.html#zyy1556500180085)

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

## Configure Java version to use

Make sure java is installed on your system:
```
sudo apt install default-jre
```

When I ran ```eclipse-nios``` on my installation, startup failed with error ```free(): invalid pointer```. I used a workaround similar to the solution in [this link](https://community.intel.com/t5/Intel-Quartus-Prime-Software/Nios-Eclipse-crashes-free-invalid-pointer/td-p/1215911) to resolve the issue:
```
cd <your_quartus_installation>/quartus/linux64
mv jre64 jre64_unused
ln -s /usr/lib/jvm/default-java jre64
```
Note: Your java version and installation path may vary, check ```/lib``` for example.

## Install support for Arrow USB BLaster

Choose the right driver version for your Programmer from https://shop.trenz-electronic.de/Download/?path=Trenz_Electronic/Software/Drivers/Arrow_USB_Programmer
, unzip it and install the files according to the instructions in the README file

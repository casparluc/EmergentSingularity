# EmergentSingularity
A simple Singularity configuration file to build a headless (running a TCP server without GUI) version of Emergent 8.1.0 on top of Ubuntu 16.04. 
Bootstrapping this configuration to a Singularity image allows you to run emergent server on any OS.

# Installation
The installation process for Singularity can be found in the Singularity documentation:
- For Mac head over [here](http://singularity.lbl.gov/install-mac)
- For Windows head over [here](http://singularity.lbl.gov/install-windows)
- For Linux head over [here](http://singularity.lbl.gov/install-linux)

# Bootstraping the image
After installation is complete follow the instructions [here](http://singularity.lbl.gov/bootstrap-image) to create and bootstrap the Singularity configuration to an image.
Warning: If you wish to bootstrap the image yourself, you need to create an image of at least 5Go or you will get a `No space left on device` during compilation.

# Downloading the image
A fully build image is readiliy available on [Singularity Hub](https://singularity-hub.org/collections/178/) and will automatically be kept up to date.

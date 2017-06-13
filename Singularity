Bootstrap: docker
From: ubuntu:16.04

%runscript
   echo "Running Emergent with arguments: -nogui -ni $*"
   exec emergent -nogui -ni "$@"

%post
   echo "Installing software and dependencies for the container."
   apt-get update
   apt-get install -y qt5-default qttools5-dev libqt5webkit5-dev qtlocation5-dev libqt5designer5 qtdeclarative5-dev libqt5sensors5-dev qtmultimedia5-dev libqt5svg5-dev libcoin80-dev cmake g++ libreadline6-dev libgsl0-dev zlib1g-dev libpng12-dev libjpeg-dev libncurses5-dev libsvn-dev libsndfile1-dev mercurial python-pip subversion devscripts csh pkg-config libode-dev
   
   echo "Checkout lastest version of emergent."
   svn checkout https://grey.colorado.edu/svn/emergent/emergent/trunk ~/emergent
   if [ $? -gt 0 ]; then exit 1;fi

   echo "Compile and install Quarter library."
   cd ~/emergent/package/
   sed -i 's/sudo //' ubuntu-motu-quarter
   sed -i 's/apt-get /apt-get -y /' ubuntu-motu-quarter
   bash ubuntu-motu-quarter
   dpkg -i /tmp/libquarter0_1.0-51ubuntu1_amd64.deb
   if [ $? -gt 0 ]; then exit 1;fi

   echo "Configure emergent build."
   cd ~/emergent
   ./configure --qt5 --clean --prefix=/usr
   if [ $? -gt 0 ]; then exit 1;fi

   echo "Compile emergent."
   cd build
   make -j 4
   if [ $? -gt 0 ]; then exit 1;fi
   
   echo "Install emergent."
   make install

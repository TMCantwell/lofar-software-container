BootStrap: yum
OSVersion: 7
MirrorURL: http://mirror.centos.org/centos-%{OSVERSION}/%{OSVERSION}/os/$basearch/
Include: yum wget


%post -c /bin/bash

yum -y update
yum -y install yum-utils
yum -y groupinstall development
yum -y install https://centos7.iuscommunity.org/ius-release.rpm
yum -y install nano
yum -y install build-essential curl git man vim autoconf libtool debootstrap squashfs-tools
yum -y install python
yum -y install python-pip
yum -y install python-devel
yum -y install cfitsio
yum -y install wcslib
yum -y install cmake
yum -y install hdf5
yum -y install cmake cmake-gui gcc-gfortran gcc-c++ flex bison \
       blas blas-devel  lapack lapack-devel cfitsio cfitsio-devel \
       wcslib wcslib-devel ncurses ncurses-devel readline readline-devel\
       python-devel fftw fftw-devel hdf5 hdf5-devel\
       numpy

#Install Boost

wget https://dl.bintray.com/boostorg/release/1.67.0/source/boost_1_67_0.tar.bz2
tar --bzip2 -xf boost_1_67_0.tar.bz2
cd boost_1_67_0
./bootstrap.sh
./b2
./b2 install
cd /

#Install casacore

wget ftp://ftp.astron.nl/outgoing/Measures/WSRT_Measures.ztar
mkdir WSRT_Measures
tar -C WSRT_Measures -xzvf WSRT_Measures.ztar
git clone https://github.com/casacore/casacore
cd casacore
mkdir build
cd build
cmake -DDATA_DIR=~/WSRT_Measures -DUSE_FFTW3=ON -DUSE_OPENMP=ON -DUSE_HDF5=ON -DBUILD_PYTHON=ON -DUSE_THREADS=ON ..
make 
make install
cd /

#Install casarest

yum -y install python-setuptools
CFLAGS="-std=gnu++11 -I /usr/include/cfitsio" pip install python-casacore
wget https://github.com/casacore/casarest/archive/1.5.0.tar.gz
tar -xvf 1.5.0.tar.gz 
cd casarest-1.5.0/
mkdir build
cd build
cmake -DCFITSIO_INCLUDE_DIR=/usr/include/cfitsio ..
make
cd /

#Install AOFlagger

yum -y install log4cplus
yum -y install libxml2-devel
yum -y install libpng-devel
yum -y install gtkmm30
yum -y install gtkmm30-devel
wget https://downloads.sourceforge.net/project/aoflagger/aoflagger-2.14.0/aoflagger-2.14.0.tar.bz2
tar -xvf aoflagger-2.14.0.tar.bz2 
cd aoflagger-2.14.0
mkdir build
cd build
cmake ../ -DBUILD_SHARED_LIBS=ON
make -j 4
make install

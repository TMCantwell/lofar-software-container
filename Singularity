BootStrap: docker
From: lofaruser/imaging-pipeline:latest

%post -c /bin/bash
pip install shapely
pip install pyregion
source /lofarsoft/lofarinit.sh
cd /lofarsoft/
rm -rf prefactor-2.0.3/
git clone https://github.com/lofar-astron/prefactor.git
cd /
git clone https://github.com/lofar-astron/factor.git
cd factor
python setup.py install --prefix=/lofarsoft/
cd /
mkdir DDF
cd DDF
git clone https://github.com/mhardcastle/ddf-pipeline.git
cd ddf-pipeline
git checkout DR1
cd ..
./ddf-pipeline/scripts/install.sh

%environment

source /lofarsoft/lofarinit.sh
source /DDF/init.sh 

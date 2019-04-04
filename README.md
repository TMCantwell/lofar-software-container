# lofar-software-container
this repoisitory is a contains a singularity recipe file for the lofar software.

The recipe uses the docker image provided by Astron as a bootstrap. 
See [here](https://support.astron.nl/LOFARImagingCookbook/buildlofar.html) for more information on the docker image.  

The main difference is between the docker image and this container is that the [Factor](https://github.com/lofar-astron/factor) 
and [prefactor](https://github.com/lofar-astron/prefactor) versions have been updated. 
We have also included the [DDF-pipeline](https://github.com/mhardcastle/ddf-pipeline).


## Usage

```bash
singularity pull --name container.simg shub://TMCantwell/lofar-software-container:latest
singularity shell -H $PWD container.simg
source /.singularity.d/env/90-environment.sh
```


# Camelyon CNNs Training Experiments

This repository contains a reproducible RED experiment. This experiment can be reproduced with CC-FAICE or CC-Agency version 7 of the [Curious Containers](https://www.curious-containers.cc/) project.

The experiments train Convolutional Neural Network models on image data from the CAMELYON16 database and do performance measurements. It is therefore crucial to wait until one set of experiments is finished, before starting the next. The database must be stored in a single HDF5 file, which can be created using a preliminary experiement (see https://github.com/deep-projects/camelyon-slide-to-tiles-experiments).


## External resources used for this Experiment

* [camelyon-cnns](https://github.com/deep-projects/camelyon-cnns) release 0.1
* camelyon-cnns appliance (Docker image)
    * [docker.io/deepprojects/camelyon-cnns:0.1](https://cloud.docker.com/u/deepprojects/repository/docker/deepprojects/camelyon-cnns)
    * [Dockerfile](https://github.com/deep-projects/appliances/tree/master/camelyon-cnns/0.1)


## Reproduce at CBMI - HTW Berlin

Running the requires access to compute resources of CBMI - HTW Berlin. If you had access, you could run the original experiment as follows.

```bash
pip3 install --user --upgrade cc-faice==7.*
faice exec camelyon-cnns-batchConcurrencyLimit-1.red.yml

# wait until camelyon-cnns-batchConcurrencyLimit-1 is finished
faice exec camelyon-cnns-batchConcurrencyLimit-3.red.yml

# wait until camelyon-cnns-batchConcurrencyLimit-3 is finished
faice exec camelyon-cnns-batchConcurrencyLimit-9.red.yml
```


## Reproduce without access to CBMI resources

* Create your own HDF5 database using https://github.com/deep-projects/camelyon-slide-to-tiles-experiments.
* Replace `inputs`, `outputs` and `execution` sections in the RED files with references to your own resources.
* Run the adapted RED files via `faice exec`.

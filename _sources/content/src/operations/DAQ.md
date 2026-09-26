# DAQ Operations

ICARUS DAQ operation wiki for experts is hosted over RedMine's [DAQ Experts page](https://cdcvs.fnal.gov/redmine/projects/icarus-operations/wiki/DAQ_Experts). Up-to date guides for almost everything are there.

## Developing DAQ code: `newSPACKDevArea.sh`

Gennady wrote a handy (but clunky) tool to be able to develop the ICARUS DAQ. It is quite useful for setting it up the first time around. Compiling an already set-up DAQ development area can be done following the details [later described](#re-building-a-daq-dev-area). 

> Note: Any DAQ development area should be installed in the `${HOME}/DAQ_SPACK_DevArea/` directory

Setting it up requires little effort. The very first thing to do is to source the correct packages

```bash
SPACK_HOME_DIR=/daq/software/spack_packages/spack/v1.0.1.sbnd; export PATH=${SPACK_HOME_DIR}/sbndaq-spack-tools:${PATH}
```

This way it is possible to ensure that the script is correctly located, 
```bash
$ which newSPACKDevArea.sh
/daq/software/spack_packages/spack/v1.0.1.sbnd/sbndaq-spack-tools/newSPACKDevArea.sh
```

### Usage

## Re-building a DAQ dev. area
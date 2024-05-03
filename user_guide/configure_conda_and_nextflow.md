# Install Nextflow and nf-core within a Conda Environment

This guide describes the process of configuring conda and creating a conda environment with Nextflow and nf-core installed.

These instructions require that you have the miniconda distribution of conda available as a personal software module. Please refer to the relevant section of [Running Nextflow with nf-core Pipelines on SHU Beowulf Cluster](https://github.com/lquayle88/nfcore_on_shu_beowulf#readme) if you have not already setup miniconda as a personal software module.


## Load and Configure Conda

Run the following commands in the order provided and follow any prompts as appropriate:

```shell
# load the miniconda module
module load miniconda

# disable base environment auto-activation
conda config --set auto_activate_base false

# add the bioconda and conda-forge channels to conda configuration
conda config --add channels bioconda
conda config --add channels conda-forge

# set channel_priority to "strict"
conda config --set channel_priority strict

# ensure conda is up-to-date
conda update conda
```


## Create a Conda Analysis Environment with Nextflow and nf-core

This approach works with the most recent versions of nextflow (v23.10.1), nf-core (v2.13.1) and singularity (v3.8.6), along with the specific version of Java shown. Run the following commands in order and follow any prompts as appropriate:

```shell
# make the "nf_env" environment
conda create --name nf_env nextflow nf-core singularity java-1.8.0-openjdk-devel-cos7-s390x

# activate the environment
source activate nf_env
```

You can now test the install has worked by running the following:

```shell
# test the environment is working
nextflow info

# test functionality
nextflow run hello
```

You will notice if you run `ls -al` wherever you executed these commands (e.g., your $HOME directory) that a directory called `work` and a file `nextflow.log` have been created. You can remove these.

Finally, we should create a specific cache for our singularity containers to be pulled to which we can specify later in any pipeline driver job run script. Run the following command:

```shell
mkdir $HOME/.singularity
```

When you are finished, you can deactivate your conda environment using the command `conda deactivate`

Should you wish to unload your personal miniconda module you can do so by running `module unload miniconda`

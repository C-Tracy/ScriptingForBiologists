# Python Virtual Environments and Supercomputers

The goal of this tutorial is to introduce you to creating virtual environments in python. This becomes very useful when working on a supercomputer, and allows you to create your own environment and install packages there, rather than needing supercomputer admin to install packages. 

## Auburn University Easley Supercomputer
Some of you may have access the the Easley computing cluster at Auburn University. If you do, here are a few

##

##

## Create a Python Virtual Environment in Easley
module load python/anaconda
export CONDA_PKGS_DIRS=~/.conda/pkgs
conda create -n genome_env2
source activate genome_env2
conda install -c bioconda bam2fastx
conda deactivate

# Python Virtual Environments and Supercomputers

The goal of this tutorial is to introduce you to creating virtual environments in python. This becomes very useful when working on a supercomputer, as it allows you to create your own environment and install packages there, rather than needing supercomputer admin to install packages. 

## Auburn University Easley Supercomputer
Some of you may have access the the Easley computing cluster at Auburn University. If you do, here are a few helpful resources for Easley users. 

Easley's User Guide: https://hpc.auburn.edu/hpc/docs/hpcdocs/build/html/easley/easley.html

Using Python on Easley: https://hpc.auburn.edu/hpc/docs/hpcdocs/build/html/easley/python.html


### Python Virtual Environments in Easley

#### Anaconda

First, create a python virtual environment using **anaconda**. In this example I create a virtual environment called genome_env2, in which I install useful genomics packages using bioconda. 
```
module load python/anaconda 
export CONDA_PKGS_DIRS=~/.conda/pkgs #this is particular to easley, and it tells it to create a local package directory
conda create -n genome_env2 #first we have to create the virtual environment, giving it whatever name you like
source activate genome_env2 #next we have to actually load that virtual environment using _source activate_
conda install -c bioconda bam2fastx #install the desired package using conda
conda deactivate #this closes the virtual environment
```

#### python3 venv
Create a virtual environment using python3 venv:
```
module load python3
python3 -m venv NAME
```
#### python3 virtualenv with pip
This method uses pip (python package manager) to install virtualenv to a local directory. 


First we will need to use pip to install virtualenv. You will only need to run these commands once to install virtualenv:
```
module load python3
pip3 install --user virtualenv
```

Now we can create the virtual environment:
```
python3 -m virtualenv env1_python
source env1_python/bin/activate
```
Once within the virtual environment you can install all packages desired:
'''
pip3 install <package_name>
'''

And don't forget to exit the virtual env: 
'''
source deactivate

'''

## Alabama Supercomputer
Every graduate student at Auburn should have access to the Alabama Supercomputer (ASC). Here are a few helpful resources for ASC users. 

### 

## Create a Python Virtual Environment in Easley
module load python/anaconda
export CONDA_PKGS_DIRS=~/.conda/pkgs
conda create -n genome_env2
source activate genome_env2
conda install -c bioconda bam2fastx
conda deactivate

# Python Virtual Environments and Supercomputers

The goal of this tutorial is to introduce you to creating virtual environments in python. This becomes very useful in a number of scenarios. First, when working on a supercomputer, it allows you to create your own environment and install packages locally, rather than needing supercomputer admin to install packages. Second, when doing different projects you may need different versions of a package. This will allow you to install multiple versions of a package without having to uninstall and reinstall different versions each time. 

The overview of steps to use a virtual environment, whether on your own machine or a supercomputer, are as follows:
1. load the necessary version of python
2. create a folder for your virtual enviroment, and move into that folder
3. create your virtual environment
4. activate your virtual environment
5. install the desired packages for your project
6. deactivate your virtual environmnet

Once you have created a virtual environment and are coming back to an existing virtual environment, you will skip steps 1-3 above, and just activate your virtual environment to run programs or install additional packages, and then deactivate your virtual environment.  

Below I am going to introduce you to the different methods of creating virtual environments on the Easley supercomputer. 
These will be largely the same as what you will do on your local computer if you are using virtual environments to have mutiple versions of a package, or if you are using a **different** supercomputer. 
If you are using a different supercomputing cluster (such as the ASC), I would recommend you examine their user guide for different applications of these. 

## Auburn University Easley Supercomputer
Some of you may have access the the Easley computing cluster at Auburn University. If you do, here are a few helpful resources for Easley users. 

Easley's User Guide: https://hpc.auburn.edu/hpc/docs/hpcdocs/build/html/easley/easley.html  
Using Python on Easley: https://hpc.auburn.edu/hpc/docs/hpcdocs/build/html/easley/python.html

In general, the process of creating virtual environments will be similar across different computing clusters. Much of the information for the following outline for Easley is pulled from their User Guide provided above. 

### A few helpful commands for Easley

Before we get started creating python virtual environments, I'm going to provide a quick outline of commands that are helpful in Easley if you are just getting started. These will differ slightly between supercomputers, so see the user guide if you are using the ASC.

First, run the following line to see what versions of python are available. You will see that there are some options that are python/version_number, and some that are python/anaconda/version_number. We will use both a version of python installed using anaconda, and a version of python3 in the tutorial below. 
```
module avail python
module av python #this runs the same command
```


You can also run the following command to see what modules you currently have loaded. This can be helpful if you have been coding and need to see what versions of a program are loaded/running. 
```
module list
```

Okay if you are new to supercomputers, you will want to go through documentation provided, however this should be sufficient to explain the differences between virtual environment options provided below. 


## Anaconda Virtual Environments
First, we will create a python virtual environment using **anaconda**. In this example I create a virtual environment called genome_env2, in which I install useful genomics packages using bioconda. 

First load a version of python installed with anaconda, this will be specific to your machine: 
```
module load python/anaconda 
```

This next step will tell the program to create a local package directory rather than the default global setting (which you do not have permissions for in a supercomputer):
```
export CONDA_PKGS_DIRS=~/.conda/pkgs 
```

Now we will create our virtual environment, load it, install packages, and the deactivate:
```
conda create -n genome_env2 #first we have to create the virtual environment, giving it whatever name you like
source activate genome_env2 #next we have to actually load that virtual environment using _source activate_
conda install -c bioconda bam2fastx #install the desired package using conda
conda deactivate #this closes the virtual environment
```
You should notice that when you activate the environment, your environment name appears in parenthese or brackets before your command prompt. 
Once you deactivate the environment you should no longer see this. 

### Managing conda environments

See what environments are available:
```
conda env list
```

See what packages are installed in a specific environment:
```
conda list -n conda_testenv
```

Removing an environment:
```
conda env remove --name conda_testenv
```

## Python3 venv
venv is a module that already exists within python to create virtual environments, and as such we do not need to install anything to create a virtual environment.
In the script below we will simply create a folder for our virtual environment, move into that folder, and then create our virtual environment for out project. 


Create a virtual environment using python3 venv:
```
module load python 
mkdir test_ve
cd test_ve
python -m venv test_venv
ls 
```

You should now see a folder with your virtual environment name (here test_venv), now lets activate that virtual environment, install our packages, and then deactivate it. 
```
source test_venv/bin/activate
#line to install
#you should now see that you have entered your virtual environment
deactivate
```
## python3 virtualenv with pip
This method uses pip (python package manager) to install virtualenv to a local directory. See this helpful guide for more in depth details, and to see different syntax between Unix/macOS and Windows: https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/

First we will need to use pip to install virtualenv. You will only need to run these commands once to install virtualenv:
```
module load python 
pip3 install --user virtualenv
```

Now we can create the virtual environment:
```
python -m virtualenv env1_python
source env1_python/bin/activate
```

Once within the virtual environment you can install all packages desired:
```
pip3 install <package_name>
```

And don't forget to exit the virtual env: 
```
source deactivate
```



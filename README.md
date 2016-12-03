# GFlow
[![DOI](https://zenodo.org/badge/23503/Pbleonard/GFlow.svg)](https://zenodo.org/badge/latestdoi/23503/Pbleonard/GFlow)
[![License (GPL version 3)](https://img.shields.io/badge/license-GNU%20GPL%20version%203-red.svg?style=flat-square)](http://opensource.org/licenses/GPL-3.0)

Software for modeling circuit theory-based connectivity at any scale. We developed GFlow to solve large ecological problems in a High Performance Computing environment. If solving a small problem or if you are willing to sacrifice some performance, it can be deployed on a desktop computer.

## Installation

### [Please download latest release with sample data.] (https://github.com/Pbleonard/GFlow/releases/latest)

### Mac OS X Install Instructions
The easiest way to setup your environment is with the
[Homebrew](http://brew.sh) package manager.
After Homebrew is set up, run the following commands to install
the required packages:

    brew update
    brew install openmpi
    brew install homebrew/science/hypre
    brew install homebrew/science/petsc
    brew install coreutils					# optional

**Note**: Advanced users may build their own versions of PETSc and an MPI library, `gflow` does not require
any specific preconditioner (we recommend `hypre`) nor does it depend on a particular
MPI implementation.

With the required packages installed, `gflow` can be built by running the following command:

     make
     
If you encounter errors related to PETSc, you may have to edit the `Makefile` to change the 
value of the `PETSC_DIR` variable.

Currently, there is no mechanism to automatically copy the `gflow.x` binary to a centrally-located
directory.


### Linux Install Instructions

*Coming soon*...


### Windows

*Not happening*...


## Running 

*Instructions below apply to Mac Desktop Computers only although the software is Linux compatible. Advanced use for cluster computing follows a very similar proceedure after dependencies are installed. Details of cluster scheduling/submission scripts are typically unique to given cyberinfrastructure.*

**Easiest using Terminal** 

1. Navigate to the directory where you downloaded GFlow and extract. 

2. Extract the zipped example input files (`inputs.tar.gz`) into the current GFlow directory. *E.g., using terminal:*
	```
    tar xvf inputs.tar.gz
	```
3. Open the commented example `execute_example.sh` script with your favorite text editor and examine the format, default settings, and save any necessary 
adjustments. Otherwise, the script is ready to submit and solve the example problem.

4. If terminal is not open, open now and navigate to GFlow directory. Execute script:
	```
    sh execute_example.sh
	```
5. To stop execution after any iteration, simply open another Terminal window and navigate to the working directory of GFlow. Enter `touch killswitch`. The simulation will cleanly exit after the current calculation and write the existing current density summation.

	1. To print the existing summation of current density without stopping the execution, simply open another Terminal window and navigate to the working directory of GFlow. We need to get the Process ID (PID). Enter:

		```
		ps aux | grep mpiexec
		``` 

	2. Take note of the retunred PID value and enter this where your value = PID:

		```
		kill -USR1 PID
		```



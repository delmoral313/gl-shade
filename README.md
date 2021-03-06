# GL-SHADE
This source code implements the GL-SHADE algorithm presented in the paper "A SHADE-Based Algorithm for Large Scale Global Optimization" at the PPSN 2020 international conference. Here it´s showed a parallell implementation of GL-SHADE using CUDA + OpenMP and adopting the CEC'13 LSGO Benchmark test suite. Futher, all test functions are implemented in both CUDA and OpenMP; the gpu based implementation of a test problem is used most of the time but in very special cases the OpenMP based implementation is employed.

### GL-SHADE-PYTHON
Public interested in a non parallel python-based implementation, you can visit https://github.com/delmoral313/gl-shade-python.

## Getting Started

### Prerequisites
The implementation was tested using a pc with an Intel(R) Core(TM) i7-3930K @ 3.20GHz CPU, 8 GB of RAM, ubuntu 18.04 as operating system and a GeForce GTX 680 GPU with the CUDA 10.2 version. For running the program you need a GPU enabled to work with CUDA version 7.0 or higher (since syntax c++11 is used) and, if possible, a pc powered by a linux like operating system.  

## Running the program 

The number of threads and blocks when using the GPU as well as the number of CPU cores activated when using OpenMP are predefined at the top of the main program named glshade.cu but we encourage you to modify them according to you GPU and CPU hardware. So, for running the main program just 4 parameters have to be defined: population size 1 (NP1), population size 2 (NP2), random number generator seed (Rseed) and problem (the one to be adopted as the objective function) identifier.  

### Compile

The test suite is composed of 15 problems and you can set any of them, but it must be done at compilation time. In the following example it's showed how to compile the main program adopting f7 as the objective function:    
```
nvcc glshade.cu -O2 -D=f7 -Xcompiler -fopenmp
```
Similarly, we can choose f13 as the objective function as follows:
```
nvcc glshade.cu -O2 -D=f13 -Xcompiler -fopenmp
```

### Run
Once the problem has been set, you can run the a.out program provided 3 input arguments: NP1, NP2 and Reseed. The population size must be a positive number bigger or equal to 4 and the RNG seed must be a real number within the interval [0.0,1.0]. The following example shows an execution where NP1 = 85, NP2 = 54 and Rseed = 0.76:

```
./a.out 85 54 0.76
```

### Compile and run easily

You can use the run.sh file provided as a shortcut for compiling and executing. The following example shows how to run GL-SHADE where NP1 and NP2 are set to 100, Rseed is set to 0.36 and f2 is set as the objective function.   

```
bash run.sh 100 100 0.36 2
```

README for CMT-bone-pca.cu

This file runs the CMT-bone-be skeleton app either on a single CPU core, 
or on a single CPU core + a GPU accelerator for the partial derivative 
compute kernels for dr, ds, dt. 

Typically, CMT-bone-BE would be run across multiple MPI ranks on multiple
CPU cores; however, those MPI calls have been removed in order to measure
performance on a single CPU core. This allows us to compare how a hardware
accelerator (in this case GPU, but could be others, such as FPGA) can 
extract parallelism beyond that of a CPU core, which can then give us 
insight into how many CPU cores worth of performance could be added or 
replaced by the hardware accelerator. The goal is not to replace multicores
in HPC systems, but rather to complement them with hardware accelerators. 


# To run on CPU only:
  -Set USE_GPU flag to 0 (#define USE_GPU 0) 

# To use GPU accelerator for target compute kernels:
  -Set USE_GPU flag to 1 (#define USE_GPU 1) 


# To vary the problem size, change the ELEMENT_SIZE parameter. 
  Typically, this value is in the range of 5 to 25 and defines the size of 
  the NxNxN 3D matrices that CMT-bone-BE operates on. 


# To compile: (NOTE: Use the -O2 compiler flag to use compiler optimizations 
  for both CPU and GPU, in order to have the fairest comparison of devices.) 
  TIP: You can compile multiple executables with different parameter combos
  on the login node in order to save time on the compute nodes. Just use 
  different executable names! 

  $ module load intel cuda ufrc
  $ nvcc -O2 CMT-bone-pca.cu -o <executable_name> 


# To allocate compute resources, including 1 CPU core and 1 GPU, and run:

  $ srun --account=eel6763 --qos=eel6763 -n1 -c1 -p gpu --gres=gpu:tesla:1 --time=01:00:00 --pty -u bash -i
  (on compute node) $ ./<executable_name> 



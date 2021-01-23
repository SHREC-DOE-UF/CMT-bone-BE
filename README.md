# CMT-bone-BE
This is a skeleton-app of a multiphysics code, CMT-nek, being developed at the Center for Compressible Multiphase Turbulence (CCMT) to drive co-design activity. While the objective of CMT-nek is to perform high-fidelity, predictive simulations of particle laden explosively dispersed turbulent flows, the goal of CMT-bone-BE is to mimic the computational behavior of CMT-nek in terms of operation counts, memory access patterns for data and performance characteristics of hardware devices (memory, cache, floating point unit, etc.). CMT-bone-BE, as a skeleton app, is used as an important benchmark to realize tradeoffs in HPC software, hardware, and algorithm design as a part of the co-design process. 

Directory for all things CMTbone or CMT-Nek. This includes the latest CMTbone source codes, profiling codes, tests, documentation, profiling and other results etc. Organization is as follows:

compute-only/		    microkernel benchmarks for compute kernels in cmt-bone-be  
insitu/			    insitu- instrumentation for microbenchmarking of compute kernels in cmt-bone-be  
	/ctime 		    compile-time specification of application input parameters  
	/rtime		    run-time specification of application input parameters  
mpi/			    MPI version of CMT-bone-BE with  
	/ctime		    compile-time specification of application input parameters  
	/rtime		    run-time specification of application input parameters  
cuda/ 			    Cuda version of CMT-bone-BE  

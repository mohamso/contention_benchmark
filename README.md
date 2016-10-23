# An MPI Contention Benchmark

This repository contains a benchmark code that performs MPI communication and computation simultaneously. The computational kernel used in the code is the Triad kernel from the [STREAM Triad benchmark](https://www.cs.virginia.edu/stream/) originally developed by John D. McCalpin.

## Build

In order to compile the system, it is sufficient to write the following on most Unix/Linux systems

    icpc -O3 -openmp -std=c++11 -o main.o -c main.cc
    mpicxx -o mpi_stream_ring main.o -O3 -openmp -std=c++11

## Run

The input to the application is the number of bytes (message size) to communicate between the different MPI processes.
For example, in order to define a message size of 4 MB, the input should be 419430 .

In order to execute the application on four nodes, using one MPI process per node on a system where SLURM is the default resource scheduler, please write:

    srun --ntaks 4 ./mpi_stream_ring 4194304

## License

Please see the LICENSE file.

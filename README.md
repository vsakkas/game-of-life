
# Game of Life

This repo contains six different implementations of Conway's Game of Life: A simple implementation of Game of Life, written in C, a CUDA version, three MPI versions (one using serial I/O, one async I/O and another one using collective I/O) and finally an MPI + OpenMP version (which uses collective I/O). The purpose of writing these six versions was to benchmark their differences in performance.

## Getting Started

To test the six versions of Game of Life on your local machine, simply follow the following instructions.

### Prerequisites


Before you get started, you need ensure that you have a compiler compatible with OpenMP. Use the following command to check the version of `gcc` that you are using (version 4.4 or newer is required):
```
gcc --version
```
You also need to install MPI and CUDA. To do so, you can use the following commands:
```
apt install mpich2
apt install nvidia-cuda-toolkit
```

### Downloading

To download the source code use the following command:

```
git clone https://github.com/vsakkas/game-of-life.git
```

And to enter the directory of the downloaded project, simply type:
```
cd game-of-life
```

### Building

To build one of the versions of Game of Life, type the command below:

```
make <version_name>
```

Where `<version_name>` can be `game`, `cuda`, `mpi`, `async`, `collective` or `openmp`.

### Running

Finally, to run the compiled program, use one the following commands:
```
./a.out <width> <height> <input_file>                 # For the regular and the CUDA version
mpiexec -n <x> ./a.out <width> <height> <input_file>  # For all MPI and MPI + OpenMP versions
```

In the above examples, `<input_file>` must be a text file containing `<height>` rows and `<width>` columns and all values must be `0` and `1`. The script `generate.sh` can be used to create a valid input file of any size.

Once the executable of any version of Game of Life is executed, an output file will be generated which contains the array of the last generation before the program stopped executing.

Each source file contains two constants, `GEN_LIMIT` and `SIMILARITY_FREQUENCY` using preprocessor commands. The default values are 1000 and 3 respectively and their values can be changed (this requires recompilation of the source file). The first value is the maximum amount of generations to be generated and the second one sets how often two generations will be compared (if two generations are the same, then the program exits). You can completely remove the similarity check by removing the `#define CHECK_SIMILARITY` macro and recompiling the source file.

## Authors
* [vsakkas](https://github.com/vsakkas)

* [v-pap](https://github.com/v-pap)

* [mahcloudservers](https://github.com/mahcloudservers)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details


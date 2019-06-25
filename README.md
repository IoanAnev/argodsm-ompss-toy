# Nanos6 benchmarks

Contains benchmarks that are used to evaluate the performance of the Cluster version of Nanos6.

## Installation

The project uses `cmake` version `2.8`. Build the project using the follow steps

```shell
git clone <nanos6-benchmarks>
cd  <nanos6-benchmarks_root>
mkdir build
cd build
CC=mcc CXX=mcxx cmake .. -DCMAKE_INSTALL_PREFIX=<target_installation_dir> -DCMAKE_BUILD_TYPE=Release
make install
```

This assumes you have already installed [mercurium](https://github.com/bsc-pm/mcxx) and [nanos6](https://github.com/epeec/nanos6)
with cluster support enabled. For more info look at the respective projects.

## Benchmarks

### fibonacci

Calculates the nth fibonacci number

#### Usage

```sh
./fibonacci N [CHECK]

where:

N       the fibonacci number to calculate
CHECK   an optional parameter that enables checks to make sure the computation is correct
```

## daxpy

Performs the computation: `y += a * x` where `x`, `y`, are two vectors of `double`,
of size `N` and `a` is a scalar.

### Usage

```sh
./daxpy_strong N TS ITER [CHECK]

where:

N       the size of the vectors x and y
TS      the number of vector elements each leaf task will compute
ITER    number of iterations for each to execute the computation
CHECK   an optional parameter that enables checks to make sure the comptuation is correct
```

## matvec-strong

Calculates the matrix-vector product: `y = A * x`, where `A` is a matrix of `M` rows
and `N` columns. This version uses only strong OmpSs-2 dependencies to parallelize the
problem.

### Usage

```sh
./matvec_strong M N TS ITER [CHECK]

where:

M       the rows of matrix A
N       the columns of matrix A
TS      the number of rows of matrix A each leaf task wil compute
ITER    number of iterations for which to execute the computations
CHECK   an optional parameter that enables checks to make sure the comptuation is correct
```

## matvec-weak

Calculates the matrix-vector product: `y = A * x`, where `A` is a matrix of `M` rows
and `N` columns. This version uses two-level tasks. The first level of tasks is using
weak dependencies. Each of the top-level task creates a number of second-level tasks
with strong dependencies.

### Usage

```sh
./matvec_strong M N TS WS ITER [CHECK]

where:

M       the rows of matrix A
N       the columns of matrix A
TS      the number of rows of matrix A each leaf task will compute
W       The number of rows of matrix A each top-level task will compute
ITER    number of iterations for which to execute the computations
CHECK   an optional parameter that enables checks to make sure the comptuation is correct
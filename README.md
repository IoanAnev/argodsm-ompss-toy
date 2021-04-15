# Toy ArgoDSM@OmpSs benchmarks

Contains toy benchmarks that are used to evaluate the performance of ArgoDSM@OmpSs.

Current benchmarks in C include:
1. [daxpy_strong](./c_bench/daxpy_strong/)
2. [matvec_strong](./c_bench/matvec_strong/)
3. [matvec_weak](./c_bench/matvec_weak/)
4. [fibonacci](./c_bench/fibonacci/)

Current benchmarks in C++ include:
1. [himeno](./cpp_bench/himeno/)

## Building

Build the applications using `cmake` (version `2.8`).

```shell
mkdir build
cd build
CC=mcc CXX=mcxx cmake .. -DCMAKE_INSTALL_PREFIX=<target_installation_dir> -DCMAKE_BUILD_TYPE=Release
make install
```

This assumes you have already installed [mercurium](https://github.com/bsc-pm/mcxx) and [nanos6-cluster](https://github.com/bsc-pm/nanos6-cluster).

## Benchmarks

### **daxpy-strong**

Performs the computation: `y += a * x` where `x`, `y`, are two vectors of `double`, of size `N` and `a` is a scalar.

This version uses only strong dependencies for parallelisation.

#### **[Usage]**

```sh
mpirun $OMPIFLAGS ./daxpy_strong N TS ITER [CHECK]

where:

N       the size of the vectors x and y
TS      the number of vector elements each leaf task will compute
ITER    number of iterations for each to execute the computation
CHECK   an optional parameter that enables checks to make sure the comptuation is correct
```

### **matvec-strong**

Calculates the matrix-vector product: `y = A * x`, where `A` is a matrix of `M` rows and `N` columns.

This version uses only strong dependencies for parallelisation.

#### **[Usage]**

```sh
mpirun $OMPIFLAGS ./matvec_strong M N TS ITER [CHECK]

where:

M       the rows of matrix A
N       the columns of matrix A
TS      the number of rows of matrix A each leaf task wil compute
ITER    number of iterations for which to execute the computations
CHECK   an optional parameter that enables checks to make sure the comptuation is correct
```

### **matvec-weak**

Calculates the matrix-vector product: `y = A * x`, where `A` is a matrix of `M` rows and `N` columns.

This version uses two-level tasks. The first level of tasks is using weak dependencies. Each of the top-level task creates a number of second-level tasks with strong dependencies.

#### **[Usage]**

```sh
mpirun $OMPIFLAGS ./matvec_weak M N TS WS ITER [CHECK]

where:

M       the rows of matrix A
N       the columns of matrix A
TS      the number of rows of matrix A each leaf task will compute
W       The number of rows of matrix A each top-level task will compute
ITER    number of iterations for which to execute the computations
CHECK   an optional parameter that enables checks to make sure the comptuation is correct
```

### **fibonacci**

Calculates the n<sup>th</sup> fibonacci number.

#### **[Usage]**

```sh
mpirun $OMPIFLAGS ./fibonacci N [CHECK]

where:

N       the fibonacci number to calculate
CHECK   an optional parameter that enables checks to make sure the computation is correct
```

### **himeno**

Measures the speed of major loops for solving Poisson’s equation using the Jacobi iteration method.

#### **[Usage]**

```sh
(mpirun $OMPIFLAGS) ./himeno-ompss-2(-cluster) TS (PS) ([CHECK])

where:

TS      task granularity
(PS)    the problem size set through CMakeLists.txt
(CHECK) optional output to a file for verification set through CMakeLists.txt
```

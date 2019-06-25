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

This assumes you have already installed `mercurium` and `nanos6` with cluster support enabled. For more info look at the
respective projects <ADD_URLS>.

After the successful installation, `<target_installation_dir>/bin` contains the following benchmarks
- `daxpy_strong` for scaling a vector
- `matvec_strong` and `matvec_weak` for matrix-vector mulptiplication

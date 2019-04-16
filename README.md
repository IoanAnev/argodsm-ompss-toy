# Nanos6 benchmarks

This is a repo for gathering benchmarks used to evaluate the performance of the
Cluster version of Nanos6.

## How to compile

The project uses `cmake` version `2.8`. Build the project using the follow steps

```shell
bchalios@dellbsc:~/tmp$ git clone git@gitlab.itwm.fraunhofer.de:EPEEC/nanos6-benchmarks.git                                                                                                 
Cloning into 'nanos6-benchmarks'...                                                                                                                                                         
remote: Enumerating objects: 78, done.                                                                                                                                                      
remote: Counting objects: 100% (78/78), done.                                                                                                                                               
remote: Compressing objects: 100% (77/77), done.                                                                                                                                            
remote: Total 78 (delta 36), reused 0 (delta 0)                                                                                                                                             
Receiving objects: 100% (78/78), 10.86 KiB | 5.43 MiB/s, done.                                                                                                                              
Resolving deltas: 100% (36/36), done.                                                                                                                                                       
bchalios@dellbsc:~/tmp$ ls                                                                                                                                                                  
nanos6-benchmarks
bchalios@dellbsc:~/tmp$ mkdir build
bchalios@dellbsc:~/tmp$ cd build/
bchalios@dellbsc:~/tmp/build$ CC=mcc CXX=mcxx cmake -DCMAKE_INSTALL_PREFIX=${HOME}/tmp -DCMAKE_BUILD_TYPE=Release ../nanos6-benchmarks/
bchalios@dellbsc:~/tmp/build$ make install

Compilation log ...

bchalios@dellbsc:~/tmp/build$ ls ~/tmp/bin
daxpy_strong  matvec_strong  matvec_weak
```
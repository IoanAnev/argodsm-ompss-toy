cmake_minimum_required(VERSION 2.8)

project(ompss_cluster_c_benchmarks)

add_executable(daxpy_strong daxpy.c)
target_link_libraries(daxpy_strong common)
target_link_libraries(daxpy_strong rt)

install(TARGETS daxpy_strong DESTINATION bin)

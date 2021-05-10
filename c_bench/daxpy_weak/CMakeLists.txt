cmake_minimum_required(VERSION 2.8)

project(ompss_cluster_c_benchmarks)

add_executable(daxpy_weak daxpy.c)
target_link_libraries(daxpy_weak common)
target_link_libraries(daxpy_weak rt)

install(TARGETS daxpy_weak DESTINATION bin)

cmake_minimum_required(VERSION 3.1)

project(ompss_cluster_benchmarks)

add_executable(matvec_weak matvec.c)
target_link_libraries(matvec_weak PRIVATE common)

install(TARGETS matvec_weak DESTINATION bin)

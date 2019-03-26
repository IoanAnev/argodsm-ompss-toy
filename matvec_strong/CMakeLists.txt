cmake_minimum_required(VERSION 3.1)

project(ompss_cluster_benchmarks)

add_executable(matvec_strong matvec.c)
target_link_libraries(matvec_strong PRIVATE common)

install(TARGETS matvec_strong DESTINATION bin)

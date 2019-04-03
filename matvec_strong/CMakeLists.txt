cmake_minimum_required(VERSION 2.8)

project(ompss_cluster_benchmarks)

add_executable(matvec_strong matvec.c)
target_link_libraries(matvec_strong common)
target_link_libraries(matvec_strong rt)

install(TARGETS matvec_strong DESTINATION bin)

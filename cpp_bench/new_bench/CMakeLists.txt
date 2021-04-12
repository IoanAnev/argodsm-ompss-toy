cmake_minimum_required(VERSION 2.8)

project(ompss_cluster_cpp_benchmarks)

add_executable(new_bench-ompss-2 new_bench-ompss-2.cpp)
target_link_libraries(new_bench-ompss-2 numa)
target_link_libraries(new_bench-ompss-2 rt)

install(TARGETS new_bench-ompss-2 DESTINATION bin)

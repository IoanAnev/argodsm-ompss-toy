cmake_minimum_required(VERSION 2.8)

project(ompss_cluster_c_benchmarks)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} --ompss-2")
	
include_directories(common)
add_subdirectory(common)
add_subdirectory(matvec_strong)
add_subdirectory(matvec_weak)
add_subdirectory(daxpy_strong)
add_subdirectory(fibonacci)

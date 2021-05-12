cmake_minimum_required(VERSION 2.8)

project(ompss_cluster_cpp_benchmarks)

# MATRIX SIZE
add_definitions(-DMATMUL_SIZE=2048)

add_executable(matmul-ompss-2 matmul-ompss-2.cpp)
target_link_libraries(matmul-ompss-2 numa)
target_link_libraries(matmul-ompss-2 rt)

add_executable(matmul-ompss-2-cluster-strong matmul-ompss-2-cluster-strong.cpp)
target_link_libraries(matmul-ompss-2-cluster-strong numa)
target_link_libraries(matmul-ompss-2-cluster-strong rt)

add_executable(matmul-ompss-2-cluster-weak matmul-ompss-2-cluster-weak.cpp)
target_link_libraries(matmul-ompss-2-cluster-weak numa)
target_link_libraries(matmul-ompss-2-cluster-weak rt)

install(TARGETS matmul-ompss-2 matmul-ompss-2-cluster-strong matmul-ompss-2-cluster-weak DESTINATION bin)

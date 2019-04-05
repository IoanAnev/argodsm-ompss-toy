cmake_minimum_required(VERSION 2.8)

project(ompss_cluster_benchmarks)

add_executable(matvec_weak matvec.c)
target_link_libraries(matvec_weak common)
target_link_libraries(matvec_weak rt)

configure_file(json/matvec_weak_strong_scalability.json.in
	json/matvec_weak_strong_scalability.json)
configure_file(json/matvec_weak_single_node.json.in
	json/matvec_weak_single_node.json)

install(TARGETS matvec_weak DESTINATION bin)
install(DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/json/
	DESTINATION share/json)

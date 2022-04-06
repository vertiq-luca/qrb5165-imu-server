cmake_minimum_required(VERSION 3.3)


set(SERVERNAME voxl-imu-server)
file(GLOB all_src_files "src/*.c")
add_executable(${SERVERNAME} ${all_src_files} ../common/cal_file.c)
include_directories(
	include
	../common
)
target_link_libraries(${SERVERNAME}
	m
	pthread
	voxl_io
	modal_pipe
	modal_json
)


install(
	TARGETS ${SERVERNAME}
	LIBRARY			DESTINATION /usr/lib
	RUNTIME			DESTINATION /usr/bin
	PUBLIC_HEADER	DESTINATION /usr/include
)
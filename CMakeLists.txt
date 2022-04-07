cmake_minimum_required(VERSION 3.3)
project(voxl-imu-server)

find_library(LIBMODAL_PIPE_SO NAMES libmodal_pipe.so HINTS /usr/lib64 )
find_library(LIBMODAL_JSON_SO NAMES libmodal_json.so HINTS /usr/lib64 )
find_library(LIBRC_MATH_SO NAMES librc_math.so HINTS /usr/lib64 )
find_library(LIBQRB5165_IO_SO NAMES libvoxl_io.so HINTS /usr/lib )

set(CMAKE_C_FLAGS "-g -std=gnu99 -Wall -Wextra -Wuninitialized \
	-Wunused-variable -Wdouble-promotion -Wmissing-prototypes \
	-Wmissing-declarations -Werror=undef -Wno-unused-function ${CMAKE_C_FLAGS}")

# server and client binaries
add_subdirectory(server)
add_subdirectory(clients)

# also install the headers from common
install(FILES common/voxl_imu_server.h DESTINATION /usr/include)

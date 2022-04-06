cmake_minimum_required(VERSION 3.3)
project(voxl-imu-server)

set(CMAKE_C_FLAGS "-g -std=gnu99 -Wall -Wextra -Wuninitialized \
	-Wunused-variable -Wdouble-promotion -Wmissing-prototypes \
	-Wmissing-declarations -Werror=undef -Wno-unused-function ${CMAKE_C_FLAGS}")


# tell the linker not to worry about missing symbols in libraries
# set(CMAKE_C_FLAGS   "-Wl,--unresolved-symbols=ignore-in-shared-libs ${CMAKE_C_FLAGS}")
# set(CMAKE_CXX_FLAGS "-Wl,--unresolved-symbols=ignore-in-shared-libs ${CMAKE_CXX_FLAGS}")

# server and client binaries
add_subdirectory(server)
add_subdirectory(clients)

# also install the headers from common
install(FILES common/voxl_imu_server.h DESTINATION /usr/include)

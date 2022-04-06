


set(CALNAME voxl-calibrate-imu)
add_executable(${CALNAME} voxl-calibrate-imu.c ../common/cal_file.c)
include_directories(include ../common)
target_link_libraries(${CALNAME} modal_pipe modal_json rc_math)

set(CALTEMPNAME voxl-calibrate-imu-temp)
add_executable(${CALTEMPNAME} voxl-calibrate-imu-temp.c ../common/cal_file.c)
include_directories(include ../common)
target_link_libraries(${CALTEMPNAME} modal_pipe modal_json m rc_math pthread)



# make sure everything is installed where we want
# LIB_INSTALL_DIR comes from the parent cmake file
install(
	TARGETS ${CALNAME} ${CALTEMPNAME}
	LIBRARY			DESTINATION ${LIB_INSTALL_DIR}
	RUNTIME			DESTINATION /usr/bin
	PUBLIC_HEADER	DESTINATION /usr/include
)


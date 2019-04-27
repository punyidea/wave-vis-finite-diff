SET(MACOSX_DEPLOYMENT_TARGET 10.14)
SET(CMAKE_CXX_FLAGS "--sysroot ${CMAKE_OSX_SYSROOT} ${CMAKE_CXX_FLAGS}")
MESSAGE("Setting MACOSX_DEPLOYMENT_TARGET to '${MACOSX_DEPLOYMENT_TARGET}'.")

project(finitediff)
set(FINITEDIFF_Version 0.0.0+devel)
set(PROJECT_NAME finitediff)
cmake_minimum_required(VERSION 3.9.2)
set(CMAKE_INCLUDE_CURRENT_DIR TRUE)
set(CMAKE_MODULE_PATH "CMakeFiles/Modules")


message("system: ${CMAKE_SYSTEM_PREFIX_PATH}")
message("system: ${qwt_DIR}")

set (INCLUDE_DIR "include/")
set (SRC_DIR "src/")

include_directories (${SRC_DIR})
include_directories(${INCLUDE_DIR})

set(CMAKE_CXX_STANDARD 11)

find_package(Armadillo REQUIRED)
include_directories(${ARMADILLO_INCLUDE_DIRS})

find_package(Qwt REQUIRED)
include_directories(${QWT_INCLUDE_DIR})


add_executable(finite_diff_vis "${SRC_DIR}main.cpp")
target_link_libraries(finite_diff_vis ${ARMADILLO_LIBRARIES} ${QWT_LIBRARIES})

install(TARGETS finite_diff_vis DESTINATION bin)




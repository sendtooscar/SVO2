project(rpg_common)
cmake_minimum_required(VERSION 2.8.3)

find_package(catkin_simple REQUIRED)
catkin_simple(ALL_DEPS_REQUIRED)
#FIND_PACKAGE(OpenCV REQUIRED)
find_package(OpenCV 3.4.1 REQUIRED PATHS "/storage_ssd/opencv-3.4.1" NO_DEFAULT_PATH)
message(WARNING "OpenCV_VERSION: ${OpenCV_VERSION}")

add_definitions(-std=c++11)

FILE(GLOB_RECURSE HEADERS "include/*")

list(APPEND SOURCES src/fs.cpp)

cs_add_library(${PROJECT_NAME} ${HEADERS} ${SOURCES})
target_link_libraries(${PROJECT_NAME} ${OpenCV_LIBRARIES})

cs_install()
cs_export()

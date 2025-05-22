project(vikit_ros)
cmake_minimum_required(VERSION 2.8.3)

find_package(catkin_simple REQUIRED)
catkin_simple(ALL_DEPS_REQUIRED)

find_package(OpenCV 3.4.1 REQUIRED PATHS "/storage_ssd/opencv-3.4.1" NO_DEFAULT_PATH)
message(WARNING "OpenCV_VERSION: ${OpenCV_VERSION}")

include(SvoSetup)

set(HEADERS
  include/vikit/img_type_conversion.h
  include/vikit/output_helper.h
  include/vikit/params_helper.h
  )

set(SOURCES
  src/output_helper.cpp
  src/img_type_conversion.cpp
  )

# Create vikit library
cs_add_library(${PROJECT_NAME} ${SOURCES} ${HEADERS})
target_link_libraries(${PROJECT_NAME} ${OpenCV_LIBRARIES})

################################################################################
cs_install()
cs_export()

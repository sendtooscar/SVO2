project(svo_test_utils)
cmake_minimum_required(VERSION 2.8.3)

find_package(catkin_simple REQUIRED)
catkin_simple(ALL_DEPS_REQUIRED)
find_package(OpenCV 3.4.1 REQUIRED PATHS "/storage_ssd/opencv-3.4.1" NO_DEFAULT_PATH)
#target_link_libraries(${PROJECT_NAME} ${OpenCV_LIBRARIES})
include(SvoSetup)

################################################################################
set(HEADERS
  include/svo/test_utils/test_utils.h
  include/svo/test_utils/imu_simulation.h
  include/svo/test_utils/synthetic_dataset.h
  include/svo/test_utils/simple_raytracer.h
  include/svo/test_utils/trajectory_generator.h
  include/svo/test_utils/point_cloud_generator.h
)

set(SOURCES
  src/test_utils.cpp
  src/imu_simulation.cpp
  src/synthetic_dataset.cpp
  src/simple_raytracer.cpp
  src/trajectory_generator.cpp
  src/point_cloud_generator.cpp
)

cs_add_library(${PROJECT_NAME} ${SOURCES} ${HEADERS} )
target_link_libraries(${PROJECT_NAME} ${OpenCV_LIBRARIES})
################################################################################
cs_install()
cs_export()

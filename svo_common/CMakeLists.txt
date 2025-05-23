project(svo_common)
cmake_minimum_required(VERSION 2.8.3)

find_package(catkin_simple REQUIRED)
catkin_simple()

find_package(OpenCV 3.4.1 REQUIRED PATHS "/storage_ssd/opencv-3.4.1" NO_DEFAULT_PATH)
#message(WARNING "OpenCV_VERSION: ${OpenCV_VERSION}")

include(SvoSetup)

set(HEADERS
  include/svo/common/camera.h
  include/svo/common/camera_fwd.h
  include/svo/common/feature_wrapper.h
  include/svo/common/frame.h
  include/svo/common/imu_calibration.h
  include/svo/common/logging.h
  include/svo/common/occupancy_grid_2d.h
  include/svo/common/point.h
  include/svo/common/seed.h
  include/svo/common/transformation.h
  include/svo/common/types.h
  )

set(SOURCES
  src/frame.cpp
  src/point.cpp
  )

cs_add_library(${PROJECT_NAME} ${SOURCES} ${HEADERS})
target_link_libraries(${PROJECT_NAME} ${OpenCV_LIBRARIES})

################################################################################
# TESTS

################################################################################
###
### GTEST
###

catkin_add_gtest(${PROJECT_NAME}-test
  test/test_main.cpp
  test/test_feature_wrapper.cpp
)
target_link_libraries(${PROJECT_NAME}-test ${PROJECT_NAME} pthread  ${OpenCV_LIBRARIES})

catkin_add_gtest(container-helpers-test
  test/test_container_helpers.cpp
)
target_link_libraries(container-helpers-test ${PROJECT_NAME} ${OpenCV_LIBRARIES})

################################################################################
cs_install()
cs_export()

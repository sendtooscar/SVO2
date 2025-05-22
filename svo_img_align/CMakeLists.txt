project(svo_img_align)
cmake_minimum_required(VERSION 2.8.3)

find_package(catkin_simple)
catkin_simple()
find_package(OpenCV 3.4.1 REQUIRED PATHS "/storage_ssd/opencv-3.4.1" NO_DEFAULT_PATH)
#target_link_libraries(${PROJECT_NAME} ${OpenCV_LIBRARIES})

include(SvoSetup)

set(HEADERS_CPU
  include/svo/img_align/sparse_img_align_base.h
  include/svo/img_align/sparse_img_align.h
  )

set(SOURCES_CPU
  src/sparse_img_align_base.cpp
  src/sparse_img_align.cpp
  )

cs_add_library(${PROJECT_NAME} ${SOURCES_CPU} ${HEADERS_CPU})
target_link_libraries(${PROJECT_NAME} ${LINK_LIBS} ${OpenCV_LIBRARIES})

cs_install()
cs_export()

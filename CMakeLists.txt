cmake_minimum_required(VERSION 2.8)
project( sfm )


find_package(OpenCV 3.2 REQUIRED COMPONENTS core calib3d features2d imgproc highgui)
find_package(Boost      REQUIRED COMPONENTS system chrono filesystem unit_test_framework program_options)
find_package(Ceres      REQUIRED)
find_package(OpenGL)


# enable C++11 standard
set(CXX_STANDARD          11)
set(CXX_STANDARD_REQUIRED ON)

include_directories(${Boost_INCLUDE_DIR})
link_directories   (${Boost_LIBRARY_DIR})
include_directories(${BLAS_INCLUDE_DIRS})
link_directories   (${BLAS_LIBRARY_DIRS})
include_directories(${LAPACK_INCLUDE_DIRS})
link_directories   (${LAPACK_LIBRARY_DIRS})


find_package(Eigen3 REQUIRED)
include_directories(${EIGEN3_INCLUDE_DIR})
message("Found Eigen3 in: ${EIGEN3_INCLUDE_DIR}")
find_package( OpenCV REQUIRED )
include_directories( ${opencv_INCLUDE_DIRS} )
add_executable( sfm main.cpp )
target_link_libraries( sfm ${OpenCV_LIBS} )

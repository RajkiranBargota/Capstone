cmake_minimum_required(VERSION 2.8 FATAL_ERROR)
project("My Project")

set(CMAKE_CXX_FLAGS "-std=c++11")
# Set cmake prefix path to enable cmake to find freenect2
set(CMAKE_PREFIX_PATH ${CMAKE_PREFIX_PATH} $ENV{HOME}/freenect2/lib/cmake/freenect2)
find_package(freenect2 REQUIRED)

include_directories("/usr/include/libusb-1.0/")

INCLUDE_DIRECTORIES(
  ${freenect2_INCLUDE_DIR}
)

add_executable(main ./src/kinect/src/main.cpp)

target_link_libraries(main ${freenect2_LIBRARIES})

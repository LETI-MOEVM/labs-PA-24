cmake_minimum_required(VERSION 3.1)

#add_subdirectory(libs)
include_directories(${OPENCL_INCLUDE_DIR})

project(enumDevices)

find_package(OpenCL REQUIRED)

set(CMAKE_CXX_STANDARD 11)

add_executable(${PROJECT_NAME} src/main.cpp)

target_link_libraries(${PROJECT_NAME} PRIVATE OpenCL::OpenCL)

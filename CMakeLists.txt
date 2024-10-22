cmake_minimum_required(VERSION 3.2)
project(forRaylib)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include(CMakeOptions.txt)

if (${BUILD_EXAMPLES})
    MESSAGE(STATUS "Building examples is enabled")
    add_subdirectory(examples)
endif()

enable_testing()


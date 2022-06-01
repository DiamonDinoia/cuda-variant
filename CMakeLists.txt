cmake_minimum_required(VERSION 3.1)
project(cuda-variant)

if(CMAKE_VERSION VERSION_LESS 3.1)
    set(CMAKE_CXX_FLAGS "-std=c++14")
elseif(NOT CMAKE_CXX_STANDARD) # don't override c++ standard if already set
    set(CMAKE_CXX_STANDARD 14)
endif()

option(USE_THRUST "enables cuda thrust compatibility" OFF)
if(USE_THRUST)
    add_definitions(-DUSE_THRUST=ON)
endif()
add_library(variant INTERFACE)


target_include_directories(variant INTERFACE
        ${CMAKE_CURRENT_SOURCE_DIR})

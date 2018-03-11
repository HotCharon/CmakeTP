cmake_minimum_required(VERSION 3.5)
project(libB)

set(CMAKE_CXX_STANDART 11)

set(SOURCE_FILES lib.cpp)

add_library(libB SHARED ${SOURCE_FILES})

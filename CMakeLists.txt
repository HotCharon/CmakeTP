cmake_minimum_required(VERSION 3.5)
project(CmakeTP)

set(SOURCE_FILES 
	A/preparing.py;
	C/main.cpp)

#set(cmake_binary_dir "${PROJECT_SOURCE_DIR}/build")

execute_process(COMMAND python preparing.py WORKING_DIRECTORY A)
execute_process(COMMAND echo "A/preparing.py")
set(CMAKE_CXX_STANDART 11)

include_directories(A)
include_directories(B)

add_executable(CmakeTP ${SOURCE_FILES})

add_subdirectory(B)

target_include_directories(CmakeTP PUBLIC ${PROJECT_SOURCE_DIR})

cmake_minimum_required(VERSION 3.6)
project(CmakeTP)

set(CMAKE_CXX_STANDARD 11)

#set(cmake_binary_dir "${PROJECT_SOURCE_DIR}/build")

add_custom_command(
    COMMAND ${PYTHON_EXECUTABLE} A/preparing.py {index.h}.proto
    DEPENDS generate_protobuf.py ${ProtoName}.proto
    OUTPUTS index.h
    COMMENT "Generating code for index.h."
)

include_directories("${PROJECT_SOURCE_DIR}/A")
include_directories("${PROJECT_SOURCE_DIR}/B")
add_subdirectory("B")

set(SOURCE_FILES 
	A/index.h;
	B/lib.h;
	C/main.cpp)

add_executable(CmakeTP ${SOURCE_FILES})